# Rebuild PMUFW and load it

![yocto_project_logo](yocto_project_logo.png)

This post describes how to rebuild PMUFW in PetaLinux Tools 2017.4.

**Prerequisites**

-   An installation of PetaLinux Tools 2017.4 - [HOWTO](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools)
    
-   A PetaLinux Tools ZU+ project that's been built - [HOWTO](http://www.zachpfeffer.com/single-post/Create-Build-and-Test-a-PetaLinux-Tools-20174-Project)
    

**Steps**

1\. Access bitbake

```
source $PETALINUX_TOOLS_INSTALL_DIR/components/yocto/source/aarch64/environment-setup-aarch64-xilinx-linux
cd $PETALINUX_PROJS_DIR/$PETALINUX_PROJ_NAME
source $PETALINUX_TOOLS_INSTALL_DIR/components/yocto/source/aarch64/layers/core/oe-init-build-env
export BB_ENV_EXTRAWHITE="$BB_ENV_EXTRAWHITE PETALINUX"
```

Note: I fairly certain you must use bitbake because you can't pass pmufw to petalinux-build via the "-c" option.

2\. Make a change in:

```
$PETALINUX_PROJS_DIR/$PETALINUX_PROJ_NAME/components/plnx_workspace/pmufw/pmu-firmware/src/
```

Note:

The source gets copied from:

```
$PETALINUX/tools/hsm/data/embeddedsw/lib/sw_apps/zynqmp_pmufw/src/
```

...to:

```
$PETALINUX_PROJS_DIR/$PETALINUX_PROJ_NAME/components/plnx_workspace/pmufw/pmu-firmware/src/
```

...when a configure is run:

```
bitbake pmu-firmware -c configure -C configure
```

Warning:

Your changes in:

```
$PETALINUX_PROJS_DIR/$PETALINUX_PROJ_NAME/components/plnx_workspace/pmufw/pmu-firmware/src/
```

...will be overwritten if you do a **configure**

3\. Rebuild PMUFW

```
bitbake pmu-firmware -c compile -C compile
```

4\. Copy the result to the output directory

```
cp ../components/plnx_workspace/pmufw/pmu-firmware/Release/pmu-firmware.elf ../images/linux/pmufw.elf
```

5\. Load it

```
connect -url tcp:localhost:3121

targets -set -nocase -filter {name =~ "*PSU*"}
stop
rst -system
after 2000

targets -set -nocase -filter {name =~ "*PMU*"}
stop
rst -system
after 2000

targets -set -nocase -filter {name =~ "*PSU*"}
stop
rst -system
after 2000

mwr 0xFFCA0038 0x1ff

targets -set -nocase -filter {name =~ "*MicroBlaze PMU*"}
dow pmufw.elf
after 2000
con
```

XSCT Output

```
xsct% targets                                                                   
  2  PS TAP                                                                     
     3  PMU
       14  MicroBlaze PMU (Sleeping. No clock)
```

**References**

-   The Xilinx + Yocto graphic is an amalgamation of [Xilinx](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png) and [Yocto](http://www.yoctoproject.org/docs/2.0/yocto-project-qs/yocto-project-qs.html) icons
    
-   Free Online HTML Escape / Unescape Tool - FreeFormatter.com @ [link](http://www.freeformatter.com/html-escape.html)