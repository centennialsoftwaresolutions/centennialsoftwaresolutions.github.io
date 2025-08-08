# Add GENIVI's DLT to a PetaLinux Tools Managed Build

![genivi_logo](genivi_logo.png)

This post demonstrates how to add GENIVI's Diagnostic Log and Trace Daemon (DLT) to a PetaLinux Tools managed build.

**Versions**

PetaLinux Tools 2017.4 used (2017.4 is based on Morty - see [link](http://www.zachpfeffer.com/single-post/Add-a-Yocto-Layer-to-a-PetaLinux-Project-and-Build-a-Recipe-in-the-Layer-with-PetaLinux-Tools?fb_comment_id=1616244218428935_1618865668166790) for details)

meta-ivi/12.0.0 at [link](http://at.projects.genivi.org/wiki/pages/viewpage.action?pageId=14549492) was used based it is based on the morty Yocto branch

**Prerequisites**

-   Download and Install Xilinx's 2017.4 PetaLinux Tools at [link](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools)
    
-   Read "Add a Yocto Layer to a PetaLinux Project and Build a Recipe in the Layer with PetaLinux Tools" at [link](http://www.zachpfeffer.com/single-post/Add-a-Yocto-Layer-to-a-PetaLinux-Project-and-Build-a-Recipe-in-the-Layer-with-PetaLinux-Tools)
    

**Method**

A way to pull the dlt-daemon into the build is to pull in the meta-ivi Yocto layer and build the dlt-daemon recipe from the layer.

**Steps**

1\. Set up your PetaLinux Tools

```
export PETALINUX_TOOLS_INSTALL_DIR=/home/pfefferz/tools/opt/pkg/petalinux
source $PETALINUX_TOOLS_INSTALL_DIR/settings.sh
```

2\. Change to your PetaLinux project

```
cd ROOT_OF_YOUR_PETALINUX_PROJ
```

3\. Check out the meta-ivi layer

```
cd components/ext_source/
git clone https://github.com/GENIVI/meta-ivi
cd meta-ivi; git checkout 12.0.0
```

4\. Use the following settings:

-   While using the instructions below, the user layer should be:
    
-   While using the instructions below, add the following to **project-spec/meta-user/recipes-core/images/petalinux-image.bbappend**
    
-   Pull in the new layer and build the dlt-daemon recipe with these instructions (**don't petalinux-build yet**):
    

[https://www.zachpfeffer.com/single-post/Add-a-Yocto-Layer-to-a-PetaLinux-Project-and-Build-a-Recipe-in-the-Layer-with-PetaLinux-Tools](http://www.zachpfeffer.com/single-post/Add-a-Yocto-Layer-to-a-PetaLinux-Project-and-Build-a-Recipe-in-the-Layer-with-PetaLinux-Tools)

5\. Create:

```
recipes-extended/dlt-daemon/dlt-daemon_%.bbappend
```

...in:

```
project-spec/meta-user
```

...with:

```
unset EXTRA_OECMAKE
```

6\. Put

```
VIRTUAL-RUNTIME_init_manager = "sysvinit"
```

..in

```
./project-spec/meta-user/conf/petalinuxbsp.conf
```

7\. Run:

```
petlinux-build
```

**Errors and Resolutions**

**petalinux-build** Error

You may get something like this error :

ERROR: /home/pfefferz/plprj3/mtd_board/components/ext_source/meta-ivi/meta-ivi/recipes-yocto-ivi/packagegroups/packagegroup-core-boot-genivi.bb: Please ensure that your setting of VIRTUAL-RUNTIME_init_manager (systemd) matches the entries enabled in DISTRO_FEATURES ERROR: Failed to parse recipe: /home/pfefferz/plprj3/mtd_board/components/ext_source/meta-ivi/meta-ivi/recipes-yocto-ivi/packagegroups/packagegroup-core-boot-genivi.bb

Note: The error will be saved in **build/build.log** and **build/tmp/log/cooker/plnx\_aarch64/console-latest.log**.

Start Investigation

Investigating **components/ext\_source/meta-ivi/meta-ivi/recipes-yocto-ivi/packagegroups/packagegroup-core-boot-genivi.bb** shows:

```
# Distro can override the following VIRTUAL-RUNTIME providers:
VIRTUAL-RUNTIME_dev_manager ?= "udev"
VIRTUAL-RUNTIME_login_manager ?= "busybox"
VIRTUAL-RUNTIME_init_manager ?= "systemd"
VIRTUAL-RUNTIME_initscripts ?= ""
VIRTUAL-RUNTIME_keymaps ?= "keymaps"

RDEPENDS_${PN} = "\
    base-files \
    base-passwd \
    busybox \
    ${@bb.utils.contains("MACHINE_FEATURES", "keyboard", "${VIRTUAL-RUNTIME_keymaps}", "", d)} \
    netbase \
    ${VIRTUAL-RUNTIME_login_manager} \
    ${VIRTUAL-RUNTIME_init_manager} \
    ${VIRTUAL-RUNTIME_initscripts} \
    ${VIRTUAL-RUNTIME_dev_manager} \
    ${VIRTUAL-RUNTIME_update-alternatives} \
    ${MACHINE_ESSENTIAL_EXTRA_RDEPENDS} \
    kmod \
    procps \
    util-linux-mount \
    "
```

Who raises this error?

Grepping for:

```
grep -REns "Please ensure that your setting of" $PETALINUX_TOOLS_INSTALL_DIR
```

Leads to a few results:

pfefferz@plc2:~/plprj3/mtd_board$ grep -REns "Please ensure that your setting of" $PETALINUX_TOOLS_INSTALL_DIR /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/microblaze_lite/layers/core/meta/classes/packagegroup.bbclass:54: bb.fatal("Please ensure that your setting of VIRTUAL-RUNTIME_init_manager (%s) matches the entries enabled in DISTRO_FEATURES" % initman) /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/arm/layers/core/meta/classes/packagegroup.bbclass:54: bb.fatal("Please ensure that your setting of VIRTUAL-RUNTIME_init_manager (%s) matches the entries enabled in DISTRO_FEATURES" % initman) /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/core/meta/classes/packagegroup.bbclass:54: bb.fatal("Please ensure that your setting of VIRTUAL-RUNTIME_init_manager (%s) matches the entries enabled in DISTRO_FEATURES" % initman) /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/microblaze_full/layers/core/meta/classes/packagegroup.bbclass:54: bb.fatal("Please ensure that your setting of VIRTUAL-RUNTIME_init_manager (%s) matches the entries enabled in DISTRO_FEATURES" % initman)

The aarch64 line is the right one, because in this case we're building for the Zynq UltraScale+ MPSoC:

/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/core/meta/classes/packagegroup.bbclass:54: bb.fatal("Please ensure that your setting of VIRTUAL-RUNTIME_init_manager (%s) matches the entries enabled in DISTRO_FEATURES" % initman)

This file lists:

```
# We don't want to look at shared library dependencies for the
# dbg packages
DEPCHAIN_DBGDEFAULTDEPS = "1"

# We only need the packaging tasks - disable the rest
do_fetch[noexec] = "1"
do_unpack[noexec] = "1"
do_patch[noexec] = "1"
do_configure[noexec] = "1"
do_compile[noexec] = "1"
do_install[noexec] = "1"
do_populate_sysroot[noexec] = "1"

python () {
    initman = d.getVar("VIRTUAL-RUNTIME_init_manager", True)
    if initman and initman in ['sysvinit', 'systemd'] and not bb.utils.contains('DISTRO_FEATURES', initman, True, False, d):
        bb.fatal("Please ensure that your setting of VIRTUAL-RUNTIME_init_manager (%s) matches the entries enabled in DISTRO_FEATURES" % initman)
}
```

What is the **distro level** in Yocto?

From version 2.2.3 of the [Yocto Mega Manual](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html) page 15/400:

**Configuration File:** Configuration information in various .conf files provides global definitions of variables. The conf/local.conf configuration file in the [Build Directory](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#build-directory) contains user-defined variables that affect every build. The meta-poky/conf/distro/poky.conf configuration file defines Yocto "distro" configuration variables used only when building with this policy. Machine configuration files, which are located throughout the [Source Directory](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#source-directory), define variables for specific hardware and are only used when building for that target (e.g. the machine/beaglebone.conf configuration file defines variables for the Texas Instruments ARM Cortex-A8 development board). Configuration files end with a .conf filename extension.

From page 74 (with comments pertaining to PetaLinux Tools Yocto interwork):

**5.14. Creating Your Own Distribution**

When you build an image using the Yocto Project and do not alter any distribution [Metadata](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#metadata), you are creating a Poky distribution. If you wish to gain more control over package alternative selections, compile-time options, and other low-level configurations, you can create your own distribution.

To create your own distribution, the basic steps consist of creating your own distribution layer, creating your own distribution configuration file, and then adding any needed code and Metadata to the layer. The following steps provide some more detail:

**Create a layer for your new distro:** Create your distribution layer so that you can keep your Metadata and code for the distribution separate. It is strongly recommended that you create and use your own layer for configuration and code. Using your own layer as compared to just placing configurations in a local.conf configuration file makes it easier to reproduce the same build configuration when using multiple build machines. See the "[Creating a General Layer Using the yocto-layer Script](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#creating-a-general-layer-using-the-yocto-layer-script)" section for information on how to quickly set up a layer.

**Create the distribution configuration file:** The distribution configuration file needs to be created in the conf/distro directory of your layer. You need to name it using your distribution name (e.g. mydistro.conf).

**Note**

The DISTRO variable in your local.conf file determines the name of your distribution.

You can split out parts of your configuration file into include files and then "require" them from within your distribution configuration file. Be sure to place the include files in the conf/distro/include directory of your layer. A common example usage of include files would be to separate out the selection of desired version and revisions for individual recipes.

Your configuration file **needs** to set the following required variables:

DISTRO\_NAME 

DISTRO\_VERSION

As it applies to PetaLinux Tools / Yocto interoperation:

This implies that if we search for "DISTRO\_NAME" we'll find if PetaLinux Tools creates a distro layer.

Grepping in my project directory failed to show any results

```
grep -REns "DISTRO_NAME" *
```

...apart from

components/ext_source/meta-ivi/meta-ivi/conf/distro/poky-ivi-systemd.conf:2:DISTRO_NAME = "Yocto GENIVI Baseline (Poky/meta-ivi)"

Grepping with this command in the PetaLinux Tools install directory

```
grep -REns "DISTRO_NAME *=" $PETALINUX_TOOLS_INSTALL_DIR
```

...gave many results:

```
pfefferz@plc2:~/plprj3/mtd_board$ grep -REns "DISTRO_NAME *=" $PETALINUX_TOOLS_INSTALL_DIR
/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/microblaze_lite/layers/meta-petalinux/conf/distro/petalinux.conf:4:DISTRO_NAME = "PetaLinux"
/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/microblaze_lite/layers/core/meta-poky/conf/distro/poky.conf:2:DISTRO_NAME = "Poky (Yocto Project Reference Distro)"
/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/arm/layers/meta-petalinux/conf/distro/petalinux.conf:4:DISTRO_NAME = "PetaLinux"
/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/arm/layers/core/meta-poky/conf/distro/poky.conf:2:DISTRO_NAME = "Poky (Yocto Project Reference Distro)"
/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-petalinux/conf/distro/petalinux.conf:4:DISTRO_NAME = "PetaLinux"
/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/core/meta-poky/conf/distro/poky.conf:2:DISTRO_NAME = "Poky (Yocto Project Reference Distro)"
/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/microblaze_full/layers/meta-petalinux/conf/distro/petalinux.conf:4:DISTRO_NAME = "PetaLinux"
/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/microblaze_full/layers/core/meta-poky/conf/distro/poky.conf:2:DISTRO_NAME = "Poky (Yocto Project Reference Distro)"
```

The following are relevant because we're using Zynq UltraScale+ MPSoC (aarch64)

/home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/meta-petalinux/conf/distro/petalinux.conf:4:DISTRO_NAME = "PetaLinux" /home/pfefferz/tools/opt/pkg/petalinux/components/yocto/source/aarch64/layers/core/meta-poky/conf/distro/poky.conf:2:DISTRO_NAME = "Poky (Yocto Project Reference Distro)"

In $PETALINUX\_TOOLS\_INSTALL\_DIR/components/yocto/source/aarch64/layers/meta-petalinux/conf/distro/petalinux.conf it requires conf/distro/poky.conf:

```
require conf/distro/poky.conf
```

...and includes:

```
VIRTUAL-RUNTIME_dev_manager_microblaze = "busybox-mdev"
VIRTUAL-RUNTIME_login_manager = "busybox"
VIRTUAL-RUNTIME_initscripts = "initscripts"
```

VIRTUAL-RUNTIME\_init\_manager is missing.

Yocto Documentation Continued...

These following variables are optional and you typically set them from the distribution configuration file:

 [DISTRO_FEATURES](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#var-DISTRO_FEATURES) [DISTRO_EXTRA_RDEPENDS](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#var-DISTRO_EXTRA_RDEPENDS) [DISTRO_EXTRA_RRECOMMENDS](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#var-DISTRO_EXTRA_RRECOMMENDS) [TCLIBC](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#var-TCLIBC)

If you want to base your distribution configuration file on the very basic configuration from OE-Core, you can use conf/distro/defaultsetup.conf as a reference and just include variables that differ as compared to defaultsetup.conf. Alternatively, you can create a distribution configuration file from scratch using the defaultsetup.conf file or configuration files from other distributions such as Poky or Angstrom as references.

**Provide miscellaneous variables:** Be sure to define any other variables for which you want to create a default or enforce as part of the distribution configuration. You can include nearly any variable from the local.conf file. The variables you use are not limited to the list in the previous bulleted item.

**Point to Your distribution configuration file:** In your local.conf file in the Build Directory, set your DISTRO variable to point to your distribution's configuration file. For example, if your distribution's configuration file is named mydistro.conf, then you point to it as follows:

DISTRO = "mydistro"

As it applies to PetaLinux Tools / Yocto interoperation:

$PETALINUX\_TOOLS\_INSTALL\_DIR/components/yocto/source/aarch64/layers/meta-petalinux/conf/distro/petalinux.conf lists:

```
DISTRO = "petalinux"
DISTRO_NAME = "PetaLinux"
DISTRO_VERSION = "2017.4"
DISTRO_CODENAME = "morty"
```

Yocto Documentation Continued...

**Add more to the layer if necessary:** Use your layer to hold other information needed for the distribution:

-   Add recipes for installing distro-specific configuration files that are not already installed by another recipe. If you have distro-specific configuration files that are included by an existing recipe, you should add an append file (.bbappend) for those. For general information and recommendations on how to add recipes to your layer, see the "[Creating Your Own Layer](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#creating-your-own-layer)" and "[Best Practices to Follow When Creating Layers](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#best-practices-to-follow-when-creating-layers)" sections.
    
-   Add any image recipes that are specific to your distribution.
    
-   Add a psplash append file for a branded splash screen. For information on append files, see the "[Using .bbappend Files](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html#using-bbappend-files)" section.
    
-   Add any other append files to make custom changes that are specific to individual recipes.
    

**petalinux-build** Error Continued...

Tried putting ./project-spec/meta-user/conf/petalinuxbsp.conf

```
VIRTUAL-RUNTIME_init_manager = "sysvinit"
```

Then hit this error after typing **petalinux-build**

```
| Package systemd was not found in the pkg-config search path.
| Perhaps you should add the directory containing `systemd.pc'
| to the PKG_CONFIG_PATH environment variable
| No package 'systemd' found
| CMake Error at CMakeLists.txt:167 (string):
|   string sub-command REPLACE requires at least four arguments.
```

Package systemd was not found in the pkg-config search path Error

Is systemd required?

[https://github.com/GENIVI/dlt-daemon/blob/master/INSTALL](http://github.com/GENIVI/dlt-daemon/blob/master/INSTALL) shows that you can use sysvinit. sysvinit is the PetaLinux Tools 2017.4 out-of-the-box default:

```
In order to change these options, you can modify these values
with ccmake, do the appropriate changes in CmakeList.txt or via
the commandline for cmake

- Change a value with: cmake -D<Variable>=<Value>
- Example: cmake -DWITH_SYSTEMD=ON -DWITH_SYSTEMD_JOURNAL=ON -DCMAKE_INSTALL_PREFIX=/usr ..
```

How can we try turning it off?

In:

```
meta-ivi/meta-ivi/recipes-extended/dlt-daemon/dlt-daemon_2.16.0.bb
```

Put a # in front of this to comment it out.

```
EXTRA_OECMAKE = "-DWITH_SYSTEMD=ON"
```

After this I was able to build the dlt-daemon into my image using PetaLinux Tools 2017.4 with:

```
petalinux-build
```

Where should the # go?

It is a little "hacky" to comment out EXTRAX\_OECMAKE on the recipe.

A better way to to leverage the ability to "append" to the recipe using a Yocto (Bit Bake) bbappend file.

Where should it go?

PetaLinux Tools provides a "meta-user" layer which is \_a\_ place to put a bbappend file for the dlt-daemon.

_Steps_

1\. Create:

```
recipes-extended/dlt-daemon/dlt-daemon_%.bbappend
```

...in:

```
project-spec/meta-user
```

...with:

```
unset EXTRA_OECMAKE
```

2\. Put the # back in the recipe:

```
meta-ivi/recipes-extended/dlt-daemon/dlt-daemon_2.16.0.bb
```

3\. Run to clean and rebuild:

```
petalinux-build -c dlt-daemon -x cleansstate
petalinux-build -c dlt-daemon
petalinux-build
```

**Other Info**

meta-ivi/13.0.0 at [link](http://at.projects.genivi.org/wiki/pages/viewpage.action?pageId=14976439) is based on pyro and meta-ivi/14.0.0 at [link](http://at.projects.genivi.org/wiki/pages/viewpage.action?pageId=16027065) is based on rocko

**References**

-   Yocto Project Mega-Manual 2.2.3 @ [link](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html)
    
-   Note: using 2.2.3 because PetaLinux Tools 2017.4 is built on Yocto 2.2.3
    
-   BitBake User Manual 2.2.3 @ [link](http://www.yoctoproject.org/docs/2.2.3/bitbake-user-manual/bitbake-user-manual.html)