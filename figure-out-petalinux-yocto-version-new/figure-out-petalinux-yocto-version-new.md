# Figure Out PetaLinux Yocto Version (PetaLinux >= 2020.1)

**Note:** This guide is for PetaLinux version 2020.1 and newer. For PetaLinux versions up to and including 2019.2, see [<u><span>this older post</span></u>](https://www.css-techhelp.com/post/figure-out-petalinux-yocto-version).

## Summary

This guide will show you how to find the version of Yocto used by PetaLinux. To do that, you'll need to create a PetaLinux project from a BSP or hardware export, then get the Yocto version from a file in the created project.

## Known Versions

Here are the Yocto versions used by some PetaLinux versions that we've tested:

**2020.1 and 2020.2:** 3.0.1 ("zeus")

**2021.1:** We haven't tested this PetaLinux version.

**2021.2:** 3.2.3 ("gatesgarth")

**2022.1 and 2022.2:** 3.4.1 ("honister")

**2023.1:** 4.1.2 ("langdale")

## HOWTO

First, if you don't already have a PetaLinux BSP or hardware export, download a BSP from the AMD's downloads site:

Pick a PetaLinux version in the left sidebar or from the Archive, then ctrl-f for "ZC702" and download the "ZC702 BSP". It doesn't matter which board BSP you get; ZC702 is one of the smaller downloads.

Next, source the PetaLinux tools and create a PetaLinux project from the BSP:

```
source /tools/Xilinx/PetaLinux/<version>/settings.sh

petalinux-create -t project -s /path/to/bsp/file.bsp
```

This'll create a folder named something like "xilinx-zc702-2022.2" or "xilinx-zcu102-2021.2" or "xilinx-vck190-2023.1"

Cd into that folder and run petalinux-config to fully initialize the created project:

```
cd <new petalinux project folder>

petalinux-config --silentconfig
```

_Note the second line printed by petalinux-config:_

```
[INFO] Extracting yocto SDK to components/yocto. This may take time!
```

_It's extracting the Yocto SDK by running the script at: /tools/Xilinx/PetaLinux/<version>/components/yocto/source/<arch>_

Next, get the Yocto version from poky.conf in the extracted Yocto SDK:

```
head -n5 $(find . -name poky.conf)
```

This will print something like:

```
DISTRO = "poky"
DISTRO_NAME = "Poky (Yocto Project Reference Distro)"
DISTRO_VERSION = "3.2.3"
DISTRO_CODENAME = "gatesgarth"
SDK_VENDOR = "-pokysdk"
```

The bold lines are the Yocto version.

_For reference, this is the path to poky.conf from the PetaLinux project root:_

```
2020.1 thru 2022.2:
components/yocto/layers/core/meta-poky/conf/distro/poky.conf
2023.1:
components/yocto/layers/poky/meta-poky/conf/distro/poky.conf
```