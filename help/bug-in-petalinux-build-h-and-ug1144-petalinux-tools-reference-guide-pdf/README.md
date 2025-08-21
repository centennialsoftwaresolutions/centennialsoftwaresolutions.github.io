# Bug in petalinux-build -h and ug1144-petalinux-tools-reference-guide.pdf

![xilinx_logo_1](xilinx_logo_1.png)

This post lists a bug in the 2018.2 version of PetaLinux Tools **petalinux-build** and **ug1144-petalinux-tools-reference-guide.pdf**

**<u><span>Instance 1</span></u>**

When the user types **petalinux-build -h** to get help the following tip is listed:

```
Compile u-boot ignoring dependencies:
  $ petalinux-build -b u-boot-xlnx_2018.1 -x do_compile
```

When this command is run the user gets the following:

```
zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2$ petalinux-build -b u-boot-xlnx_2018.1 -x do_compile
[INFO] building project
[INFO] sourcing bitbake
INFO: bitbake -b u-boot-xlnx_2018.1 -c do_compile
WARNING: Buildfile specified, dependencies will not be handled. If this is not what you want, do not use -b / --buildfile.
ERROR: Unable to find any recipe file matching 'u-boot-xlnx_2018.1'

Summary: There was 1 WARNING message shown.
Summary: There was 1 ERROR message shown, returning a non-zero exit code.
ERROR: Failed to build project
```

The issue is that **u-boot-xlnx\_2018.1.bb** doesn't exist. **u-boot-xlnx\_2018.2.bb** does exist in the 4 Yocto installations that PetaLinux Tools 2018.2 includes:

```
zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2$ find /opt/pkg/petalinux -name "u-boot-xlnx_2018*"
/opt/pkg/petalinux/components/yocto/source/arm/layers/meta-xilinx/meta-xilinx-bsp/recipes-bsp/u-boot/u-boot-xlnx_2018.2.bb
/opt/pkg/petalinux/components/yocto/source/microblaze_lite/layers/meta-xilinx/meta-xilinx-bsp/recipes-bsp/u-boot/u-boot-xlnx_2018.2.bb
/opt/pkg/petalinux/components/yocto/source/microblaze_full/layers/meta-xilinx/meta-xilinx-bsp/recipes-bsp/u-boot/u-boot-xlnx_2018.2.bb
/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-xilinx/meta-xilinx-bsp/recipes-bsp/u-boot/u-boot-xlnx_2018.2.bb
```

Use: **petalinux-build -b u-boot-xlnx\_2018.2 -x do\_compile**

**<u><span>Instance 2</span></u>**

In the 2018.2 ug1144-petalinux-tools-reference-guide.pdf at \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug1144-petalinux-tools-reference-guide.pdf)\] **petalinux-build -b u-boot-xlnx\_2018.1** is given on page 32.

Use **petalinux-build -b u-boot-xlnx\_2018.2**

**<u><span>Reference</span></u>**

Xilinx logo found via https://twitter.com/xilinxinc at [[link](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)]  