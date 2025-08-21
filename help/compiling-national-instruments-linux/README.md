# Compiling National Instruments Linux

![national_instruments_logo](national_instruments_logo.png)

National Instruments maintains their version of the Linux kernel on GitHub: [<u><span>https://github.com/ni/linux</span></u>](https://github.com/ni/linux). This article covers compiling it from source and then running it on your computer (in place of the normal Linux kernel that ships with your Linux distribution - though the exact same steps should work in a virtual machine).

The master branch of the repository is based on Linux 4.14, which was released in November 2017. If you have a newer computer then chances are it won't work for you, since it will be missing the drivers for your CPU, GPU, WiFi card, etc. They maintain branches rebased on top of newer kernels - in this case, the 'nilrt/master/5.6' and 'nilrt/master/5.10' branches, based on kernels 5.6 and 5.10. Linux 5.10 is fairly recent and thus we'll use that.

## Setup

First, create a folder to do this in, and a folder for the compiled output.

```
$ mkdir -p ~/linux/build/kernel
$ cd ~/linux
$ git clone https://github.com/ni/linux.git
```

This will create a folder 'linux' inside ~/linux containing the repository. Additionally, we'll use ~/linux/build/kernel as the build output directory - the actual folder doesn't matter, but this is what is used in the compiling guide from the kernel source [<u><span>(link)</span></u>](https://github.com/ni/linux/blob/nilrt/master%2F5.10/Documentation/admin-guide/README.rst).

```
$ cd ~/linux/linux
$ git checkout nilrt/master/5.10
```

Getting the kernel built has three steps: creating a configuration file, compiling the kernel, and creating the modules.

## Config file

The kernel includes a few config file editors/generators. The full list is available in the [<u><span>docs</span></u>](https://github.com/ni/linux/blob/nilrt/master%2F5.10/Documentation/admin-guide/README.rst#configuring-the-kernel), but here are a few notable ones:

\- nconfig, xconfig, gconfig are TUI/Qt/GTK based editors

\- defconfig, allyesconfig, tinyconfig create config files for the default/biggest/smallest kernels

\- localmodconfig will use every module that is currently loaded on your system, and nothing else

\- oldconfig will update a config file from an older Linux version

If you're already using a Linux distribution on the target hardware, you would want to base your config file on the same one that your distribution uses to create their normal builds of Linux. Copy their file over to ~/linux/build/kernel/.config (dot config - hidden). The NI 5.10 kernel is actually based on Linux 5.10.17, and so the config file you copy over can't be from a newer version of Linux. Then, if the config file you copied is for an older kernel (<5.10.17), you will need to run the 'oldconfig' editor to update the config file to be compatible with 5.10.17.

To run a config generator/edtior:

```
$ make O=/home/me/linux/build/kernel <EDITOR>
# Where <EDITOR> = xconfig, oldconfig, defconfig, etc., e.g.
$ make O=/home/me/linux/build/kernel xconfig
```

## Compiling the kernel

Simply run make with no target. For me, it defaulted to single-core compilation so I had to specify the number of threads with -j.

Interestingly, the older 4.10 kernel did automatically set j=16, so that's what I used here too. My CPU is 8 core / 16 threads.

```
$ make -j16 O=/home/me/linux/build/kernel
```

## Create modules

Run the modules\_install target with root privileges. Again, this will be very slow if you don't use -j.

```
$ sudo make -j16 O=/home/me/linux/build/kernel modules_install
```

This will put its output into /lib/modules - for me, the exact folder it made was /lib/modules/5.10.17-rt32-gf7a7e9082661.

## Run the kernel

This part is somewhat OS and bootloader-specific. The general steps are:

\- Copy the kernel image into /boot

\- Generate the initial ramdisk

\- Add the new kernel to your bootloader

\- Reboot into it!

The specific instructions below are for Arch Linux with the systemd bootloader on an EFI system, based on the steps from the Arch Wiki [<u><span>(link)</span></u>](https://wiki.archlinux.org/index.php/Kernel/Traditional_compilation#Installation).

Arch Linux has a number of kernels available in the official repositories, named like 'linux', 'linux-lts', 'linux-zen', 'linux-hardened', etc. So we'll name this one linux-ni.

And on my system, I already had a /boot folder containing kernel images and ramdisks such as:

\- /boot/vmlinuz-linux (for the default Arch kernel)

\- /boot/vmlinuz-linux-lts (for the linux-lts kernel from the Arch repositories)

\- /boot/vmlinuz-linux-zen (for the linux-zen kernel from the Arch repositories)

\- /boot/initramfs-linux.img

\- /boot/initramfs-linux-lts.img

\- /boot/initramfs-linux-zen.img

So we'll follow this convention for naming and storing the new kernel image and ramdisk.

First, copy the kernel image to /boot:

```
# cp /home/me/linux/build/kernel/arch/x86_64/boot/bzImage /boot/vmlinuz-linux-ni
```

Then, create the presets file for mkinitcpio so it can generate the initial ramdisk (mkinitcpio is an Arch-specific utility):

```
# cd /etc/mkinitcpio.d
# cp linux.preset linux-ni.preset
# vim linux-ni.preset
> change 'linux' to 'linux-ni' in these three places:
>   vmlinuz-linux
>   initramfs-linux.img
>   initramfs-linux-fallback.img
```

Next, create the ramdisk - this will output /boot/initramfs-linux-ni.img:

```
# mkinitcpio -p linux-ni
```

Finally, add a new bootloader entry for the new kernel:

```
# cd /boot/loader/entries
> copy an existing entry to a new file
> change 'linux' to 'linux-ni' in 'vmlinuz-linux' and 'initramfs-linux.img'
> change the title of the bootloader entry so you can tell which one is which
```

Reboot and choose linux-ni from your bootloader.

## Nvidia graphics

If you're using the proprietary Nvidia graphics driver, it won't work with the new kernel and so your computer won't get past a TTY. The solutions are to either:

a) use the nouveau driver, or,

b) use the DKMS version of the nvidia package instead of the standard nvidia package

I no longer use Nvidia anymore, but do use the virtualbox-host kernel modules to run virtual machines on my computer. In my case, simply reinstalling the virtualbox-host-dkms package through the Arch Linux package manger picked up the new kernel and installed the vboxhost module into it. So chances are that just installing the nvidia-dkms package that your distribution provides would also work for you.

## References

NI logo from \[[<u><span>link</span></u>](https://ni.scene7.com/is/image/ni/logo_2020?fmt=png-alpha)\]