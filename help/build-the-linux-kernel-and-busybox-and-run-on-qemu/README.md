# Build the Linux kernel and Busybox and run them on QEMU

![tux_logo](tux_logo.png)

**Update**

Check out \[[link](http://www.centennialsoftwaresolutions.com/blog/build-the-linux-kernel-and-busybox-and-run-them-on-qemu)\] for more streamlined instructions

**What the Post is About**

This post is a condensed version of Mitchel Humpherys excellent post @ [link](http://mgalgs.github.io/2015/05/16/how-to-build-a-custom-linux-kernel-for-qemu-2015-edition.html). Like Mitchel's post, this post gives step-by-step instructions for building a minimal custom Linux kernel, creating a busybox based userland and booting it on an emulator ([QEMU)](http://www.qemu.org/). This post just builds the allnoconfig + custom config; the smallest config.

**Why is it Useful?**

Of the many reasons, building a minimal Linux kernel and booting it on an emulator allows developers to quickly build additional Linux kernel features.

**Set Up**

Everything was built in an Oracle VM VirtualBox running on Windows 7, Version 5.1.30 r118389 (Qt5.6.2) with 4 GB of RAM and a 64 GB disk (the VM's config) running Ubuntu 16.04.2. VirtualBox was running on a [T460](http://www.zachpfeffer.com/single-post/2017/01/28/New-T460-System-Information). If you need help setting up this environment click [here](http://www.zachpfeffer.com/single-post/2017/02/15/Installing-the-64-bit-PC-AMD64-desktop-image-of-Ubuntu-16041-LTS-Xenial-Xerus-in-Oracle-VM-VirtualBox-5114-running-in-Windows-7-Professional-Service-Pack-1-CurrentBuild-7601-on-a-ThinkPad-T460-model-20FNCTO1WW-with-an-IntelR-CoreTM-i7-6600U-CPU) (just install 16.04.02 instead of 16.04.01).

**Get the Packages**

```
sudo apt-get install curl
sudo apt-get install libncurses5-dev
sudo apt install qemu-system-x86
```

**Steps**

1\. Open a Terminal

2\. Create a workspace

```
STAGE=$HOME/tl
TOP=$STAGE/teeny-linux
mkdir -p $STAGE
```

3\. Download and extract the Linux kernel and BusyBox

```
cd $STAGE
curl https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.10.6.tar.xz | tar xJf -
curl https://busybox.net/downloads/busybox-1.26.2.tar.bz2 | tar xjf -
```

1 min 23 secs for kernel, 2 secs for BusyBox

4\. Create a minimal userland

-   \-pv: p means don't output an error and quit if the directory exist and v means print a message for each created directory.
    
-   0= means put output here
    

5\. Enable static linking in BusyBox

```
make O=$TOP/obj/busybox-x86 menuconfig
```

5.1 Press enter on **Busybox Settings --->**

5.2 Press the down arrow until you hit **Build BusyBox as a static binary (no shared libs)**.

5.3 Press **Y**

5.4 Select **Exit** twice and hit **Enter** to Save (cursor will be on Yes).

6\. Build BusyBox

```
cd $TOP/obj/busybox-x86
make -j2
make install
```

make -j2 took about 2 min, the time to make install was negligible.

7\. Build the directory structure of the initramfs

```
mkdir -pv $TOP/initramfs/x86-busybox
cd $TOP/initramfs/x86-busybox
mkdir -pv {bin,dev,sbin,etc,proc,sys/kernel/debug,usr/{bin,sbin},lib,lib64,mnt/root,root}
cp -av $TOP/obj/busybox-x86/_install/* $TOP/initramfs/x86-busybox
sudo cp -av /dev/{null,console,tty,sda1} $TOP/initramfs/x86-busybox/dev/
```

**\-av**: **a** means **\-dR --preserve=all**, v means **explain what is being done**

**\-dR --preserve=all:**

**d** means **\--no-dereference --preserve=links**

**R** means **copy directories recursively**

**\--preserve=all** means

Note: Need additional info about /dev nodes from [link](http://wiki.gentoo.org/wiki/Custom_Initramfs).

8\. Create init and make it executable

Edit init

```
vi $TOP/initramfs/x86-busybox/init
```

Paste this in

```
#!/bin/sh
 
mount -t proc none /proc
mount -t sysfs none /sys
mount -t debugfs none /sys/kernel/debug
 
echo -e "\nBoot took $(cut -d' ' -f1 /proc/uptime) seconds\n"
 
exec /bin/sh
```

Make the file executable

```
chmod +x $TOP/initramfs/x86-busybox/init
```

9\. Create the initramfs (big thanks to http://jootamam.net/howto-initramfs-image.htm)

```
cd $TOP/initramfs/x86-busybox
find . | cpio -H newc -o > ../initramfs.cpio
cd ..
cat initramfs.cpio | gzip > $TOP/obj/initramfs.igz
```

Warning: you \_have\_ to use **find .** if you use find with a absolute path you'll encode absolute paths and the kernel will not find your init. Scroll down to see the error.

find - search for files in a directory hierarchy

**$TOP**: starts looking for files in $TOP. Since no filter is specified, all the files will be returned

**\-print0**: print the fill filename followed by a NULL instead of a newline

[cpio](http://www.gnu.org/software/cpio/manual) - copy files to and from archives

**\-o**: Create the archive (run in copy-out mode)

**\-v**: Verbosely list the files processed

**\-H newc**: Use given archive FORMAT

**newc**: The new (SVR4) portable format, which supports file systems having more than 65536 i-nodes. (4294967295 bytes)

gzip - compress or expand files

Check it. Run:

```
ls -hl $TOP/obj/initramfs-busybox-x86.cpio.gz
```

You should see something like:

```
-rw-rw-r-- 1 pfefferz pfefferz 8.7M Mar  6 21:06 /home/pfefferz/tl/teeny-linux/obj/initramfs-busybox-x86.cpio.gz
```

To check the contents do:

```
mkdir $STAGE/checkarchive
cd $STAGE/checkarchive
zcat $TOP/obj/initramfs.igz | cpio -idmv --no-absolute-filenames
```

Then to re-create from \_this\_ directory do:

```
cd $STAGE/checkarchive
find . | cpio -H newc -o > ../checked-initramfs.cpio
cd ..
cat checked-initramfs.cpio | gzip > $TOP/obj/checked-initramfs.igz
```

10\. Config the kernel with the minimal config

```
cd $STAGE/linux-4.10.6
make O=$TOP/obj/linux-x86-allnoconfig allnoconfig
```

11\. Re-enable config options for QEMU

```
cd $STAGE/linux-4.10.6
make O=$TOP/obj/linux-x86-allnoconfig nconfig
```

nconfig: Pseudo-graphical menu based on ncurses (doc from [link](http://wiki.gentoo.org/wiki/Kernel/Configuration))

12\. Turn these options on

```
[*] 64-bit kernel

-> General setup
  -> Configure standard kernel features
[*] Enable support for printk

-> General setup
[*] Initial RAM filesystem and RAM disk (initramfs/initrd) support

-> Executable file formats / Emulations
[*] Kernel support for ELF binaries
[*] Kernel support for scripts starting with #!

-> Device Drivers
  -> Character devices
[*] Enable TTY

-> Device Drivers
  -> Character devices
    -> Serial drivers
[*] 8250/16550 and compatible serial support
[*]   Console on 8250/16550 and compatible serial port

-> File systems
  -> Pseudo filesystems
[*] /proc file system support
[*] sysfs file system support

-> Kernel hacking                                                     
    -> Compile-time checks and compiler options 
[*] Debug filesystem

-> Kernel hacking   
[*] Early printk
```

Debug fs is not needed for QEMU. Its included because building a debug interface is a good way to start to work with the kernel.

Early printk is also not required but it helps see the kernel boot up.

13\. Make the Linux kernel

```
cd $STAGE/linux-4.10.6
make O=$TOP/obj/linux-x86-allnoconfig -j2
```

At the end of the log you should see:

```
  AS      arch/x86/boot/header.o
  LD      arch/x86/boot/setup.elf
  OBJCOPY arch/x86/boot/setup.bin
  BUILD   arch/x86/boot/bzImage
Setup is 15804 bytes (padded to 15872 bytes).
System is 550 kB
CRC 57d75ca8
Kernel: arch/x86/boot/bzImage is ready  (#1)
make[1]: Leaving directory '/home/pfefferz/tl/teeny-linux/obj/linux-x86-allnoconfig'
```

14\. Launch the kernel

```
STAGE=$HOME/tl
TOP=$STAGE/teeny-linux
qemu-system-x86_64 \
    -kernel $TOP/obj/linux-x86-allnoconfig/arch/x86/boot/bzImage \
    -initrd $TOP/obj/initramfs.igz \
    -nographic -append "earlyprintk=serial,ttyS0 console=ttyS0"
```

To Exit QEMU (this didn't work for me)

Type Ctl-a c then type “quit” at the qemu monitor shell.

15\. To build the initramfs into the kernel (which I had to do since I kept getting a "can't find init error)

Run a kernel config:

```
cd $STAGE/linux-4.10.6
make O=$TOP/obj/linux-x86-allnoconfig nconfig
```

Set this field to where your initramfs is (note: not using $TOP here):

```
General setup  --->
    (/home/pfefferz/tl/teeny-linux/initramfs/x86-busybox) Initramfs source file(s)
```

Then kick off QEMU with:

```
qemu-system-x86_64 \
    -kernel $TOP/obj/linux-x86-allnoconfig/arch/x86/boot/bzImage \
    -nographic -append "earlyprintk=serial,ttyS0 console=ttyS0"
```

When ever you change the initramfs you need to rebuild the kernel.

Issues

Enabling early printk's allowed me to see:

```
input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input2
Freeing unused kernel memory: 452K
Write protecting the kernel read-only data: 4096k
Freeing unused kernel memory: 776K
Freeing unused kernel memory: 1764K
Kernel panic - not syncing: No working init found.  Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance.
Kernel Offset: disabled
---[ end Kernel panic - not syncing: No working init found.  Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance.
random: crng init done
```

I then add **init=/bin/sh** and called the kernel:

```
qemu-system-x86_64 \
>     -kernel $TOP/obj/linux-x86-allnoconfig/arch/x86/boot/bzImage \
>     -initrd $TOP/obj/initramfs-busybox-x86.cpio.gz \
>     -nographic -append "init=/bin/sh earlyprintk=serial,ttyS0 console=ttyS0"
```

I got:

```
Freeing unused kernel memory: 452K
Write protecting the kernel read-only data: 4096k
Freeing unused kernel memory: 776K
Freeing unused kernel memory: 1764K
Kernel panic - not syncing: Requested init /bin/sh failed (error -2).
Kernel Offset: disabled
---[ end Kernel panic - not syncing: Requested init /bin/sh failed (error -2).
random: fast init done
```

When I extract the cpio built using Mitchel Humphery's cpio creation I noticed that the paths started were absolute!

```
./home
./home/pfefferz
./home/pfefferz/tl
./home/pfefferz/tl/teeny-linux
./home/pfefferz/tl/teeny-linux/initramfs
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/smemcap
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/bzip2
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/renice
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/setuidgid
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/mesg
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/rx
./home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/crontab
```

Gar!

I looked back at Michel's original instructions:

```
cd $TOP/initramfs/x86-busybox
find . -print0 \
    | cpio --null -ov --format=newc \
    | gzip -9 > $TOP/obj/initramfs-busybox-x86.cpio.gz
```

...I had changed to use an absolute path in the find call:

```
find $TOP/initramfs/x86-busybox -print0 \
    | cpio --null -ov --format=newc \
    | gzip -9 > $TOP/obj/initramfs-busybox-x86.cpio.gz
```

Look at the output from:

```
cd $TOP/initramfs/x86-busybox
find . | more
```

```
pfefferz@machine:~/tl/teeny-linux/initramfs/x86-busybox$ find . | more
.
./usr
./usr/bin
./usr/bin/smemcap
./usr/bin/bzip2
./usr/bin/renice
./usr/bin/setuidgid
./usr/bin/mesg
./usr/bin/rx
```

Versus the output from:

```
find $TOP/initramfs/x86-busybox | more
```

Output:

```
pfefferz@machine:~/tl/teeny-linux/initramfs/x86-busybox$ find $TOP/initramfs/x86-busybox | more
/home/pfefferz/tl/teeny-linux/initramfs/x86-busybox
/home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr
/home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin
/home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/smemcap
/home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/bzip2
/home/pfefferz/tl/teeny-linux/initramfs/x86-busybox/usr/bin/renice
```

See the full paths! Garrrh!

So when creating cpio archives for initramfs', cd into the initramfs and use find . otherwise you may see:

```
input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input2
Freeing unused kernel memory: 452K
Write protecting the kernel read-only data: 4096k
Freeing unused kernel memory: 776K
Freeing unused kernel memory: 1764K
Kernel panic - not syncing: No working init found.  Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance.
Kernel Offset: disabled
---[ end Kernel panic - not syncing: No working init found.  Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance.
random: crng init done
```

**Notes**

This write up also forgos the use of '$' before commands so that you can copy and paste the commands directly into your terminal.

Google Internet speed test:

40.2 Mbps download, 5.18 Mbps upload, Latency 32 ms

BusyBox is at [link](http://busybox.net/FAQ.html).

**Reference**

Tux from [link](http://en.wikipedia.org/wiki/Tux_(mascot)) (found via Google image search).