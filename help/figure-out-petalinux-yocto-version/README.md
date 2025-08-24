# Figure Out PetaLinux Yocto Version (PetaLinux <= 2019.2)

**Note:** This guide is for PetaLinux version 2019.2 and older. For PetaLinux version 2020.1 and newer, see [<u><span>this newer post</span></u>](/help/figure-out-petalinux-yocto-version-new).

![yocto_project_logo_1](yocto_project_logo_1.png)

This post shows you how to figure out which version of Yocto is being used in a particular version of PetaLinux Tools (PetaLinux Tools 2018.2 is using Rocko 2.4.1).

**<u><span>Versions Used</span></u>**

PetaLinux Tools 2018.2

**<u><span>Steps</span></u>**

1\. Type **cd /opt/pkg/petalinux**

2\. Type **find . -name poky.conf**

You'll see the following output:

```
./components/yocto/source/arm/layers/core/meta-poky/conf/distro/poky.conf
./components/yocto/source/microblaze_lite/layers/core/meta-poky/conf/distro/poky.conf
./components/yocto/source/microblaze_full/layers/core/meta-poky/conf/distro/poky.conf
./components/yocto/source/aarch64/layers/core/meta-poky/conf/distro/poky.conf
```

**Note**: this implies that PetaLinux Tools 2018.2 **ships with 4 copies of Yocto**.

3\. Type **find . -name poky.conf -print0 | xargs --null grep -HEi 'DISTRO\_CODENAME =|DISTRO\_VERSION ='** to list the DISTRO\_VERSION and DISTRO\_CODENAME for all 4 of the Yocto copies shipped with PetaLinux Tools

You'll see the following output:

```
./components/yocto/source/arm/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_VERSION = "2.4.1"
./components/yocto/source/arm/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_CODENAME = "rocko"
./components/yocto/source/microblaze_lite/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_VERSION = "2.4.1"
./components/yocto/source/microblaze_lite/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_CODENAME = "rocko"
./components/yocto/source/microblaze_full/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_VERSION = "2.4.1"
./components/yocto/source/microblaze_full/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_CODENAME = "rocko"
./components/yocto/source/aarch64/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_VERSION = "2.4.1"
./components/yocto/source/aarch64/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_CODENAME = "rocko"
```

This means that PetaLinux Tools 2018.2 is using Rocko 2.4.1.

With this, the specific documentation for the release can be listed at \[[<u><span>link</span></u>](https://www.yoctoproject.org/docs/archived-documents/)\] by selecting **YP CORE - ROCKO 2.4.1**.

**Examples**

Yocto Project Reference Manual for 2.4.1 at \[[<u><span>link</span></u>](https://www.yoctoproject.org/docs/2.4.1/ref-manual/ref-manual.html)\]

Yocto Project Mega-Manual for 2.4.1 at \[[<u><span>link</span></u>](https://www.yoctoproject.org/docs/2.4.1/mega-manual/mega-manual.html)\]

Yocto Project Quick Start for 2.4.1 at \[[<u><span>link</span></u>](https://www.yoctoproject.org/docs/2.4.1/yocto-project-qs/yocto-project-qs.html)\]

**<u><span>References</span></u>**

-   <u><span>[yocto] How to check the version of Yocto</span></u> at \[[<u><span>link</span></u>](https://lists.yoctoproject.org/pipermail/yocto/2015-July/025798.html)\]
    
-   The Xilinx + Yocto graphic is an amalgamation of [<u><span>Xilinx</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png) and [<u><span>Yocto</span></u>](https://www.yoctoproject.org/docs/2.0/yocto-project-qs/yocto-project-qs.html) icons.
