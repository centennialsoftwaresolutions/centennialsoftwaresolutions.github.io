# Use PetaLinux Tools to Add a Script that Will Execute at Boot

![yocto_project](yocto_project.png)

This post lists how to install an initscript into a build using PetaLinux Tools.

*Looking for PetaLinux help? Email* [*inquiries@centennialsoftwaresolutions.com*](mailto:inquiries@centennialsoftwaresolutions.com?subject=I'm+looking+for+a+30-min+consult+on+PetaLinux+Tools+for+$99.00) *today to schedule a 30-min consult for $99.00*

**Notes**

-   This write up was done using PetaLinux Tools 2017.4.
    
-   If you need help installing PetaLinux Tools check out [link](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools).
    
-   The write up follows
    

**Steps**

**1.** cd into your PetaLinux project directory

**2.** Run:

```
petalinux-create -t apps --template install -n bootscript --enable
```

Changes to the PetaLinux project from this command:

```
--- a/project-spec/configs/rootfs_config
+++ b/project-spec/configs/rootfs_config
@@ -4373,6 +4373,7 @@ CONFIG_bridge-utils=y
 #
 # apps 
 #
+CONFIG_bootscript=y
 # CONFIG_gpio-demo is not set
 # CONFIG_peekpoke is not set
 
diff --git a/project-spec/meta-user/recipes-bsp/u-boot/files/platform-top.h b/project-spec/meta-user/recipes-bsp/u-boot/files/platform-top.h
index b195f40..afb45cb 100644
--- a/project-spec/meta-user/recipes-core/images/petalinux-image.bbappend
+++ b/project-spec/meta-user/recipes-core/images/petalinux-image.bbappend
@@ -3,3 +3,4 @@
 IMAGE_INSTALL_append = " peekpoke"
 IMAGE_INSTALL_append = " gpio-demo"
 IMAGE_INSTALL_append = " swupdate"
+IMAGE_INSTALL_append = " bootscript"
```

These files are also created automatically:

_project-spec/meta-user/recipes-apps/bootscript/.gdbinit_

```
# Load the PetaLinux SDK main gdbinit script
source plnx_gdbinit
```

_project-spec/meta-user/recipes-apps/bootscript/README_

```
PetaLinux User Application Template
===================================

This directory contains a PetaLinux user application created from a template.

You can easily import any already built application or script by copying
it into this directory, and editing the automatically generated Makefile 
as described below.

Modify the "install:" target in Makefile to use $(TARGETINST) to install your
prebuilt application or script to the host copy of the target file system
referring to the comments of the "install:" target.

Before building the application, you will need to enable the application
from PetaLinux menuconfig by running:
    "petalinux-config -c rootfs"
You will see your application in the "Applications --->" submenu.

To install your prebuilt application or script to the target file system
copy on the host, simply run the 
    "petalinux-build -c rootfs/bootscript"
command.

You will also need to rebuild PetaLinux bootable images so that the images
is updated with the updated target filesystem copy, run this command:
    "petalinux-build -x package"

You can also run one PetaLinux command to install the application to the
target filesystem host copy and update the bootable images as follows:
    "petalinux-build"
```

_project-spec/meta-user/recipes-apps/bootscript/bootscript.bb_

```
#
# This file is the bootscript recipe.
#

SUMMARY = "Simple bootscript application"
SECTION = "PETALINUX/apps"
LICENSE = "MIT"
LIC_FILES_CHKSUM = "file://${COMMON_LICENSE_DIR}/MIT;md5=0835ade698e0bcf8506ecda2f7b4f302"

SRC_URI = "file://bootscript \
	"

S = "${WORKDIR}"

do_install() {
	     install -d ${D}/${bindir}
	     install -m 0755 ${S}/bootscript ${D}/${bindir}
}
```

Note:

All variables are defined below.

_project-spec/meta-user/recipes-apps/bootscript/files/bootscript_

```
#!/bin/sh

echo "Hello PetaLinux World"
```

**3.** Edit project-spec/meta-user/recipes-apps/bootscript/files/bootscript

Add a :)

```
#!/bin/sh

echo "Hello PetaLinux World :)"
```

**4.** Edit project-spec/meta-user/recipes-apps/bootscript/bootscript.bb

Add the following (listed in diff form, add the lines with '+', remove the lines with '-'):

```
--- a/project-spec/meta-user/recipes-apps/bootscript/bootscript.bb
+++ b/project-spec/meta-user/recipes-apps/bootscript/bootscript.bb
@@ -12,7 +12,12 @@ SRC_URI = "file://bootscript \
 
 S = "${WORKDIR}"
 
+inherit update-rc.d
+
+INITSCRIPT_NAME = "bootscript"
+INITSCRIPT_PARAMS = "start 99 S ."
 do_install() {
-            install -d ${D}/${bindir}
-            install -m 0755 ${S}/bootscript ${D}/${bindir}
+            install -d ${D}${sysconfdir}/init.d
+            install -m 0755 ${S}/bootscript ${D}${sysconfdir}/init.d/bootscript
 }
+FILES_${PN} += "${sysconfdir}/*"
```

**5.** Run:

```
petalinux-build -c bootscript -x do_install -f
petalinux-build -c rootfs
petalinux-build
```

Note: I had to run all three of these commands, in this order, to have **bootscript** installed into the **rootfs**.

**6.** Boot the rootfs:

```
Populating dev cache                                                                                
Starting internet superserver: inetd.                                                               
Hello PetaLinux World :)                                                                            
Running postinst /etc/rpm-postinsts/100-sysvinit-inittab... 
```

**References**

-   The Xilinx + Yocto graphic is an amalgamation of [Xilinx](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png) and [Yocto](http://www.yoctoproject.org/docs/2.0/yocto-project-qs/yocto-project-qs.html) icons
    
-   Free Online HTML Escape / Unescape @ [link](http://www.freeformatter.com/html-escape.html)
    
-   PetaLinux Tools 2017.4 Reference Guide UG1144 (v2017.4) December 20, 2017 @ [link](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_4/ug1144-petalinux-tools-reference-guide.pdf)
    
-   Yocto Project Mega-Manual 2.2.3 @ [link](http://www.yoctoproject.org/docs/2.2.3/mega-manual/mega-manual.html)
    
-   Note: using 2.2.3 because PetaLinux Tools 2017.4 is built on Yocto 2.2.3
    

**Additional Info**

All definitions listed from the Yocto Mega Manual.

${WORKDIR}

The pathname of the work directory in which the OpenEmbedded build system builds a recipe. This directory is located within the TMPDIR directory structure and is specific to the recipe being built and the system for which it is being built.

The WORKDIR directory is defined as follows: ${TMPDIR}/work/${MULTIMACH\_TARGET\_SYS}/${PN}/${EXTENDPE}${PV}-${PR}

The actual directory depends on several things:

• TMPDIR: The top-level build output directory

• MULTIMACH\_TARGET\_SYS: The target system identifier

• PN: The recipe name

• EXTENDPE: The epoch - (if PE is not specified, which is usually the case for most recipes, then EXTENDPE is blank)

• PV: The recipe version

• PR: The recipe revision

As an example, assume a Source Directory top-level folder name **poky**, a default Build Directory at **poky/build**, and a **qemux86-poky-linux** machine target system. Furthermore, suppose your recipe is **named foo\_1.3.0-r0.bb**. In this case, the work directory the build system uses to build the package would be as follows:

poky/build/tmp/work/qemux86-poky-linux/foo/1.3.0-r0

inherit update-rc.d

The OpenEmbedded build system provides support for starting services two different ways:

**SysVinit:** SysVinit is a system and service manager that manages the init system used to control the very basic functions of your system. The init program is the first program started by the Linux kernel when the system boots. Init then controls the startup, running and shutdown of all other programs.

To enable a service using SysVinit, your recipe needs to **inherit the update-rc.d** class. The class helps facilitate safely installing the package on the target.

You will need to set the INITSCRIPT\_PACKAGES, INITSCRIPT\_NAME, and INITSCRIPT\_PARAMS variables within your recipe.

**systemd:** System Management Daemon (systemd) was designed to replace SysVinit and to provide enhanced management of services. For more information on systemd, see the systemd homepage at http://freedesktop.org/wiki/Software/systemd/.

To enable a service using systemd, your recipe needs to inherit the systemd class. See the systemd.bbclass file located in your Source Directory. section for more information.

INITSCRIPT\_NAME

The filename of the initialization script as installed to ${sysconfdir}/init.d.

This variable is used in recipes when using update-rc.d.bbclass. The variable is mandatory.

INITSCRIPT\_PARAMS

Specifies the options to pass to update-rc.d. Here is an example:

INITSCRIPT\_PARAMS = "start 99 5 2 . stop 20 0 1 6 ." In this example, the script has a runlevel of 99, starts the script in initlevels 2 and 5, and stops the script in levels 0, 1 and 6.

The variable's default value is "defaults", which is set in the update-rc.d class.

The value in INITSCRIPT\_PARAMS is passed through to the update-rc.d command. For more information on valid parameters, please see the update-rc.d manual page at http://www.tin.org/bin/man.cgi?section=8&topic=update-rc.d.

${D}

The destination directory. The location in the Build Directory where components are installed by the do\_install task. This location defaults to: ${WORKDIR}/image

Caution Tasks that read from or write to this directory should run under fakeroot.

${bindir}

/usr/bin

${sysconfdir}

/etc

${PN}

This variable can have two separate functions depending on the context: a recipe name or a resulting package name.

PN refers to a recipe name in the context of a file used by the OpenEmbedded build system as input to create a package. The name is normally extracted from the recipe file name. For example, if the recipe is named expat\_2.0.1.bb, then the default value of PN will be "expat".

The variable refers to a package name in the context of a file created or produced by the OpenEmbedded build system.

If applicable, the PN variable also contains any special suffix or prefix. For example, using bash to build packages for the native machine, PN is bash-native. Using bash to build packages for the target and for Multilib, PN would be bash and lib64-bash, respectively.