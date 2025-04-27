# Finding the Linux kernel version / commit used by Petalinux, and acquiring the kernel source

This post shows how you can find the kernel version used in a Petalinux build - not just the numeric version like 4.19, but the exact git commit. It also shows how to download the kernel source for that version.

## Kernel version

Execute \`uname -a\` on a running Petalinux image on the FPGA. Here, the output indicates that the kernel version is 4.19 and that this Petalinux image was built on Thursday October 21 2021, at 22:04:57 UTC.

```
# uname -a 
Linux 4.19.0-xilinx-v2019.1 #1 SMP Thu Oct 21 22:04:57 UTC 2021 aarch64 aarch64 aarch64 GNU/Linux
```

## Kernel commit

cd to your Petalinux installation directory - this is the directory containing the settings.sh file you source to activate the Petalinux tools.

From here, cd into components/yocto/source/_arch_/layers

Replace the italic _arch_ with the CPU architecture that your Petalinux build is running on:

\- 'arm' for 32-bit ARM cores, like on the XC7S PS

\- 'aarch64' for 64-bit ARM cores, like on the Ultrascale/+ PS

\- 'microblaze\_full' and 'microblaze\_lite' for Microblaze softcores

From here, open the file meta-xilinx/meta-xilinx-bsp/recipes-kernel/linux/linux-xlnx\_2019.1.bb in a text editor. Replace 2019.1 with the Petalinux version you're using.

This file will contain:

```
LINUX_VERSION = "4.19"
SRCREV ?= "9811303824b66a8db9a8ec61b570879336a9fde5"
```

Indicating that Petalinux 2019.1 uses kernel 4.19, and that specific git commit in the linux-xlnx repository.

This file may have moved around in newer Petalinux versions. If you can't find it at the path described above, you can cd to components/yocto/source/_arch_/layers and run a search for the commit:

```
grep -rIFe SRCREV | grep linux-xlnx
```

This does a recursive search for all occurrences of 'SRCREV', then narrows it down to just matches in files that had 'linux-xlnx' in their name.

## Acquiring kernel sources

Download the linux-xlnx repository, and then checkout the commit that you want:

```
git clone https://github.com/Xilinx/linux-xlnx.git
cd linux-xlnx
git checkout 9811303824b66a8db9a8ec61b570879336a9fde5
```

## References:

\- The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]