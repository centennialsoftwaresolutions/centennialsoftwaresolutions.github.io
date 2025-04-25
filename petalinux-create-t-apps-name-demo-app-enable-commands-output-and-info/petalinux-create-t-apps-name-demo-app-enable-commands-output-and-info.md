# petalinux-create -t apps --name demo-app --enable Commands, Output, and Info

![Yocto_project_logo](Yocto_project_logo.png)

This post lists commands, output, and information around **petalinux-create -t apps --name demo-app --enable**. Its meant to be used as a development and debugging reference.

**<u><span># Install, Create, and Build a ZCU102 2019.1 PetaLinux BSP Project</span></u>**

mkdir -p $HOME/petalinux

cd ~/Downloads

./petalinux-v2019.1-final-installer.run $HOME/petalinux/2019.1

mkdir -p ~/plxprjs

cd ~/plxprjs

source ~/petalinux/2019.1/settings.sh

petalinux-create -t project -s ~/plxbsps/xilinx-zcu102-v2019.1-final.bsp

​	INFO: Create project:

​	INFO: Projects:

​	INFO: \* xilinx-zcu102-2019.1

​	INFO: has been successfully installed to /home/demo/plxprjs/

​	INFO: New project successfully created in /home/demo/plxprjs/

cd ~/plxprjs/xilinx-zcu102-2019.1

time petalinux-build

​	real 24m50.272s

​	user 0m54.305s

​	sys 0m7.616s

​	build/build.log at https://drive.google.com/file/d/1Tom4WATrZyOjX1D42KS0MqnJgFRDF7VR/view?usp=sharing

**<u><span># Create a demo-app and Build It</span></u>**

\# In a new terminal

cd ~/plxprjs/xilinx-zcu102-2019.1

source ~/petalinux/2019.1/settings.sh

​	PetaLinux environment set to '/home/demo/petalinux/2019.1'

​	INFO: Checking free disk space

​	INFO: Checking installed tools

​	INFO: Checking installed development libraries

​	INFO: Checking network and other services

​	WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution

petalinux-create -t apps --name demo-app --enable

​	INFO: Create apps: demo-app

​	INFO: New apps successfully created in /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app

​	INFO: Enabling created component...

​	INFO: sourcing bitbake

​	INFO: oldconfig rootfs

​	INFO: demo-app has been enabled

cat project-spec/meta-plnx-generated/recipes-core/images/petalinux-user-image.bb

​	DESCRIPTION = "PETALINUX image definition for Xilinx boards" 

​	LICENSE = "MIT" 

​	require recipes-core/images/petalinux-image-common.inc 

​	inherit extrausers 

​	COMMON\_FEATURES = "\\ 

​		ssh-server-dropbear \\ 

​		hwcodecs \\ 

​		" 

​	IMAGE\_LINGUAS = " " 

​	IMAGE\_INSTALL = "\\ 

​		kernel-modules \\ 

​		mtd-utils \\ 

​		canutils \\ 

​		openssh-sftp-server \\ 

​		pciutils \\ 

​		run-postinsts \\ 

​		udev-extraconf \\ 

​		packagegroup-core-boot \\ 

​		packagegroup-core-ssh-dropbear \\ 

​		tcf-agent \\ 

​		watchdog-init \\ 

​		bridge-utils \\ 

​		hellopm \\ 

​		**demo-app \\** 

​		" 

​	EXTRA\_USERS\_PARAMS = "usermod -P root root;"

cat project-spec/meta-user/recipes-core/images/petalinux-image-full.bbappend

​	[#Note](https://www.centennialsoftwaresolutions.com/blog/hashtags/Note): Mention Each package in individual line 

​	#      cascaded representation with line breaks are not valid in this file.

​	IMAGE_INSTALL_append = " peekpoke"

​	IMAGE_INSTALL_append = " gpio-demo"

​	IMAGE_INSTALL_append = " demo-app"

find project-spec/meta-user/recipes-apps/demo-app/

​	project-spec/meta-user/recipes-apps/demo-app/

​	project-spec/meta-user/recipes-apps/demo-app/.gdbinit

​	project-spec/meta-user/recipes-apps/demo-app/demo-app.bb

​	project-spec/meta-user/recipes-apps/demo-app/files

​	project-spec/meta-user/recipes-apps/demo-app/files/demo-app.c

​	project-spec/meta-user/recipes-apps/demo-app/files/Makefile

​	project-spec/meta-user/recipes-apps/demo-app/README

cat project-spec/meta-user/recipes-apps/demo-app/demo-app.bb

#
# #This file is the demo-app recipe.
#

SUMMARY = "Simple demo-app application"
SECTION = "PETALINUX/apps"
LICENSE = "MIT"
LIC_FILES_CHKSUM = "file://${COMMON_LICENSE_DIR}/MIT;md5=0835ade698e0bcf8506ecda2f7b4f302"

SRC_URI = "file://demo-app.c \
	   file://Makefile \
		  "

S = "${WORKDIR}"

do_compile() {
	     oe_runmake
}

do_install() {
	     install -d ${D}${bindir}
	     install -m 0755 demo-app ${D}${bindir}
}

petalinux-build -c demo-app

cat build/build.log

\[INFO\] building demo-app

\[INFO\] sourcing bitbake

SDK environment now set up; additionally you may now run devtool to perform development tasks.

Run devtool --help for further details.

\### Shell environment set up for builds. ###

You can now run 'bitbake <target>'

Common targets are:

core-image-minimal

core-image-sato

meta-toolchain

meta-ide-support

You can also run generated qemu images with a command like 'runqemu qemux86'

NOTE: Starting bitbake server...

\[INFO\] generating user layers

NOTE: Starting bitbake server...

NOTE: Resolving any missing task queue dependencies

Sstate summary: Wanted 14 Found 0 Missed 28 Current 116 (0% match, 89% complete)

NOTE: Executing SetScene Tasks

NOTE: Executing RunQueue Tasks

NOTE: Running task 542 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_fetch)

NOTE: recipe demo-app-1.0-r0: task do\_fetch: Started

NOTE: recipe demo-app-1.0-r0: task do\_fetch: Succeeded

NOTE: Running task 543 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_prepare\_recipe\_sysroot)

NOTE: Running task 544 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_unpack)

NOTE: recipe demo-app-1.0-r0: task do\_prepare\_recipe\_sysroot: Started

NOTE: recipe demo-app-1.0-r0: task do\_unpack: Started

NOTE: recipe demo-app-1.0-r0: task do\_unpack: Succeeded

NOTE: Running task 545 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_patch)

NOTE: recipe demo-app-1.0-r0: task do\_patch: Started

NOTE: recipe demo-app-1.0-r0: task do\_prepare\_recipe\_sysroot: Succeeded

NOTE: recipe demo-app-1.0-r0: task do\_patch: Succeeded

NOTE: Running task 546 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_populate\_lic)

NOTE: Running task 547 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_configure)

NOTE: recipe demo-app-1.0-r0: task do\_populate\_lic: Started

NOTE: recipe demo-app-1.0-r0: task do\_configure: Started

NOTE: recipe demo-app-1.0-r0: task do\_configure: Succeeded

NOTE: Running task 548 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_compile)

NOTE: recipe demo-app-1.0-r0: task do\_populate\_lic: Succeeded

NOTE: recipe demo-app-1.0-r0: task do\_compile: Started

NOTE: recipe demo-app-1.0-r0: task do\_compile: Succeeded

NOTE: Running task 549 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_install)

NOTE: recipe demo-app-1.0-r0: task do\_install: Started

NOTE: recipe demo-app-1.0-r0: task do\_install: Succeeded

NOTE: Running task 550 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_package)

NOTE: Running task 551 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_populate\_sysroot)

NOTE: recipe demo-app-1.0-r0: task do\_populate\_sysroot: Started

NOTE: recipe demo-app-1.0-r0: task do\_package: Started

NOTE: recipe demo-app-1.0-r0: task do\_populate\_sysroot: Succeeded

NOTE: recipe demo-app-1.0-r0: task do\_package: Succeeded

NOTE: Running task 552 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_packagedata)

NOTE: recipe demo-app-1.0-r0: task do\_packagedata: Started

NOTE: recipe demo-app-1.0-r0: task do\_packagedata: Succeeded

NOTE: Running task 553 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_package\_qa)

NOTE: Running task 554 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_package\_write\_rpm)

NOTE: recipe demo-app-1.0-r0: task do\_package\_qa: Started

NOTE: recipe demo-app-1.0-r0: task do\_package\_write\_rpm: Started

NOTE: recipe demo-app-1.0-r0: task do\_package\_qa: Succeeded

NOTE: recipe demo-app-1.0-r0: task do\_package\_write\_rpm: Succeeded

NOTE: Running task 555 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_rm\_work)

NOTE: recipe demo-app-1.0-r0: task do\_rm\_work: Started

NOTE: recipe demo-app-1.0-r0: task do\_rm\_work: Succeeded

NOTE: Running noexec task 556 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_rm\_work\_all)

NOTE: Running noexec task 557 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/demo-app/demo-app.bb:do\_build)

NOTE: Tasks Summary: Attempted 557 tasks of which 541 didn't need to be rerun and all succeeded.

\[INFO\] successfully built demo-app

petalinux-build

build/build.log at https://drive.google.com/file/d/1u41OLMf-fAsyQFXkWTh2cFUOfv7EQ2MJ/view?usp=sharing 

**<u><span># How demo-app is Connected to Yocto</span></u>**

cat build/conf/bblayers.conf

\# WARNING: this configuration has been automatically generated and in

\# most cases should not be edited. If you need more flexibility than

\# this configuration provides, it is strongly suggested that you set

\# up a proper instance of the full build system and use that instead.

LCONF\_VERSION = "7"

BBPATH = "${TOPDIR}"

SDKBASEMETAPATH = "/home/demo/petalinux/2019.1/components/yocto/source/aarch64"

BBLAYERS := " \\

${SDKBASEMETAPATH}/layers/core/meta \\

${SDKBASEMETAPATH}/layers/core/meta-poky \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-perl \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-python \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-filesystems \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-gnome \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-multimedia \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-networking \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-webserver \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-xfce \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-initramfs \\

${SDKBASEMETAPATH}/layers/meta-openembedded/meta-oe \\

${SDKBASEMETAPATH}/layers/meta-browser \\

${SDKBASEMETAPATH}/layers/meta-qt5 \\

${SDKBASEMETAPATH}/layers/meta-xilinx/meta-xilinx-bsp \\

${SDKBASEMETAPATH}/layers/meta-xilinx/meta-xilinx-contrib \\

${SDKBASEMETAPATH}/layers/meta-xilinx-tools \\

${SDKBASEMETAPATH}/layers/meta-petalinux \\

${SDKBASEMETAPATH}/layers/meta-virtualization \\

${SDKBASEMETAPATH}/layers/meta-openamp \\

${SDKBASEMETAPATH}/workspace \\

/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-plnx-generated \\

/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user \\

"

cat /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-plnx-generated/conf/layer.conf

\# We have a conf and classes directory, add to BBPATH

BBPATH .= ":${LAYERDIR}"

\# We have recipes-\* directories, add to BBFILES

BBFILES += "${LAYERDIR}/recipes-\*/\*/\*.bb \\

${LAYERDIR}/recipes-\*/\*/\*.bbappend"

BBFILE\_COLLECTIONS += "meta-plnx-generated"

BBFILE\_PATTERN\_meta-plnx-generated = "^${LAYERDIR}/"

BBFILE\_PRIORITY\_meta-plnx-generated = "6"

LAYERDEPENDS\_meta-plnx-generated = "core"

LAYERSERIES\_COMPAT\_meta-plnx-generated = "thud"

cat /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/conf/layer.conf

\# We have a conf and classes directory, add to BBPATH

BBPATH .= ":${LAYERDIR}"

\# We have recipes-\* directories, add to BBFILES

BBFILES += "${LAYERDIR}/recipes-\*/\*/\*.bb \\

${LAYERDIR}/recipes-\*/\*/\*.bbappend"

BBFILE\_COLLECTIONS += "meta-user"

BBFILE\_PATTERN\_meta-user = "^${LAYERDIR}/"

BBFILE\_PRIORITY\_meta-user = "6"

LAYERSERIES\_COMPAT\_meta-user = "thud"

**<u><span># Work Directly With BitBake</span></u>**

\# Open a new terminal

cd ~/plxprjs/xilinx-zcu102-2019.1

source ~/petalinux/2019.1/settings.sh

source ~/petalinux/2019.1/components/yocto/source/aarch64/environment-setup-aarch64-xilinx-linux

source ~/petalinux/2019.1/components/yocto/source/aarch64/layers/core/oe-init-build-env

\# At this point BBPATH is set:

\# env | grep BBPATH

\# BBPATH=/home/demo/plxprjs/xilinx-zcu102-2019.1/build

export PATH=~/petalinux/2019.1/tools/xsct/bin:$PATH

which xsct

export BB\_ENV\_EXTRAWHITE="$BB\_ENV\_EXTRAWHITE PETALINUX"

bitbake -e demo-app > bitbake.e.demo-app

Get all the BB variables:

grep -v "^#" bitbake.e.demo-app | grep "^BB"

**<u><span># References</span></u>**

-   BitBake @ 2019.1 (thud): [<u><span>https://www.yoctoproject.org/docs/2.6.1/bitbake-user-manual/bitbake-user-manual.html</span></u>](https://www.yoctoproject.org/docs/2.6.1/bitbake-user-manual/bitbake-user-manual.html)
    
-   Yocto @ 2019.1 (thud): [<u><span>https://docs.yoctoproject.org/2.6.1/mega-manual/mega-manual.html</span></u>](https://docs.yoctoproject.org/2.6.1/mega-manual/mega-manual.html)
    
-   Xilinx logo from [<u><span>https://www.xilinx.com/etc.clientlibs/site/clientlibs/xilinx/site-all/resources/imgs/header/xilinx-header-logo.svg</span></u>](https://www.xilinx.com/etc.clientlibs/site/clientlibs/xilinx/site-all/resources/imgs/header/xilinx-header-logo.svg)
    
-   Yocto icon from [<u><span>https://www.linuxfoundation.org/wp-content/uploads/yocto.svg</span></u>](https://www.linuxfoundation.org/wp-content/uploads/yocto.svg)
    
-   [<u><span>https://a4z.gitlab.io/docs/BitBake/guide.html</span></u>](https://a4z.gitlab.io/docs/BitBake/guide.html)