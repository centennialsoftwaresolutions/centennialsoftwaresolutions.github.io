# How to Figure out Which Yocto Recipe is Getting Built by PetaLinux Tools 2017.4

![yocto_project](yocto_project.png)

This post shows how to figure out which Yocto recipe is getting built by PetaLinux Tools 2017.4.

**TL;DR**

Run the following and grep for the recipe you're interested in **from inside the PetaLinux project, just above the build directory**:

```
export PETALINUX_TOOLS_INSTALL_DIR=/home/pfefferz/tools/opt/pkg/petalinux
source $PETALINUX_TOOLS_INSTALL_DIR/components/yocto/source/aarch64/environment-setup-aarch64-xilinx-linux
source $PETALINUX_TOOLS_INSTALL_DIR/components/yocto/source/aarch64/layers/core/oe-init-build-env
export BB_ENV_EXTRAWHITE="$BB_ENV_EXTRAWHITE PETALINUX"
which bitbake
```

This should drop you into the build directory. If it does, type the following to show the current and preferred versions of all recipes:

```
bitbake -s
```

Grep this to filter for the recipe you're interested in.

_This has been adapted from "Accessing BitBake in a Project" on page 80 of the PetaLinux Tools Reference Guide (link to doc below)._

**Motivation**

[Add a Yocto Layer to a PetaLinux Project and Build a Recipe in the Layer with PetaLinux Tools](http://www.zachpfeffer.com/single-post/Add-a-Yocto-Layer-to-a-PetaLinux-Project-and-Build-a-Recipe-in-the-Layer-with-PetaLinux-Tools) listed the steps to add a new Yocto layer to a PetaLinux Tools managed build.

Some layers contain multiple recipe versions.

**Figuring out the Version without bitbake -s**

This example uses SWUpdate.

The morty branch of the SWUpdate layer @ [link](http://github.com/sbabic/meta-swupdate.git) contains three **release** recipes and a tip recipe:

```
./recipes-support/swupdate/swupdate_git.bb
./recipes-support/swupdate/swupdate_2016.10.bb
./recipes-support/swupdate/swupdate_2016.07.bb
./recipes-support/swupdate/swupdate_2017.01.bb
```

Which one gets used and why?

**Which one is Used and Why?**

BitBake defaults to the highest version of a provider. PREFERRED\_VERSION can be used to specify a particular version.

DEFAULT\_PREFERENCE can influence the default:

-   By default, files have a preference of "0"
    
-   Setting DEFAULT\_PREFERENCE to "-1" makes the recipe unlikely to be used unless it is explicitly referenced
    
-   Setting DEFAULT\_PREFERENCE to "1" makes it likely the recipe will be used
    

PREFERRED\_VERSION overrides any DEFAULT\_PREFERENCE setting.

To figure out which version of SWUpdate will be pulled in grep with:

```
pfefferz@plc2:~/plprjs5/mtd_board/components/ext_source/meta-swupdate$ grep -REns "PREFERRED_VERSION|DEFAULT_PREFERENCE" *
recipes-support/swupdate/swupdate_git.bb:4:DEFAULT_PREFERENCE = "-1"
```

By the rules above, BitBake will choose the highest version: 2017.1. Running bitbake -s confirms it.

_This has been adapted from sections_ **_2.3 Providers_** _and_ **_2.4 Preferences_** _in version 2.2.3 of the BitBake User Manual(link to doc below)._

**References**

-   Bitbake User Manual 2.2.3 @ [link](http://www.yoctoproject.org/docs/2.2.3/bitbake-user-manual/bitbake-user-manual.html)
    
-   PetaLinux Tools Reference Guide UG1144 (v2017.3) October 4, 2017 @ [link](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_4/ug1144-petalinux-tools-reference-guide.pdf)
    
-   The Xilinx + Yocto graphic is an amalgamation of [Xilinx](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png) and [Yocto](http://www.yoctoproject.org/docs/2.0/yocto-project-qs/yocto-project-qs.html) icons.
    

**Get SWUpdate**

Get SWUpdate layer and checkout morty with:

```
git clone https://github.com/sbabic/meta-swupdate.git 
cd meta-swupdate
git checkout morty
```