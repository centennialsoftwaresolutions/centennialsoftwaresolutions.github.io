# The files updated and created by: petalinux-create -t apps --template install --name mylib --enable

![xilinx_logo](xilinx_logo.png)

- This post lists the file updated and created by running petalinux-create -t apps --template install --name mylib --enable

  The listing is meant as a reference.

  **File List** generated with:

  source $PETALINUX_TOOLS_INSTALL/settings.sh

  cd ~/plxprjs/xilinx-zcu102-2019.1

  touch start

  petalinux-create -t apps --template install --name mylib --enable

  find . -cnewer start -printf "%T+\t%p\n" | sort | awk '{print $2}'

  **Content of Files** generated with:

  echo "# petalinux-create files" > all_changes.txt

  for file in $(find . -type f -cnewer start -printf "%T+\t%p\n" | sort | awk '{print $2}'); do

  ​    if [ $file != ./all_changes.txt ]; then

  ​        echo "#FILE: $file" >> all_changes.txt

  ​        cat $file >> all_changes.txt

  ​    fi

  done

  **File List**

  Generated with:

  cat **all_changes.txt** | grep \#FILE:

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./project-spec/meta-user/recipes-core/images/petalinux-image-full.bbappend

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./project-spec/meta-user/recipes-apps/mylib/files/mylib

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./project-spec/meta-user/recipes-apps/mylib/.gdbinit

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./project-spec/meta-user/recipes-apps/mylib/README

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./project-spec/meta-user/recipes-apps/mylib/mylib.bb

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./build/pyshtables.py

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./build/cache/bb_persist_data.sqlite3

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./build/conf/bblayers.conf

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./project-spec/configs/rootfs_config.old

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./build/bitbake-cookerdaemon.log

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./build/misc/rootfs_config/Kconfig.user

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./build/misc/rootfs_config/Kconfig

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./project-spec/configs/rootfs_config

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./project-spec/meta-plnx-generated/recipes-core/images/petalinux-user-image.bb

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./.petalinux/metadata

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./.petalinux/usage_statistics_copy

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./.petalinux/usage_statistics_token

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./.petalinux/usage_statistics

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./all_changes.txt

  **Content of Files**

  Generated with: 

  cat all_changes.txt | grep \#FILE: -A10

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./project-spec/meta-user/recipes-core/images/petalinux-image-full.bbappend**

  [#Note](https://www.centennialsoftwaresolutions.com/blog/hashtags/Note): Mention Each package in individual line

  \#      cascaded representation with line breaks are not valid in this file.

  IMAGE_INSTALL_append = " peekpoke"

  IMAGE_INSTALL_append = " gpio-demo"

  IMAGE_INSTALL_append = " **mylib**"

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./project-spec/meta-user/recipes-apps/mylib/files/mylib**

  \#!/bin/sh

  echo "Hello PetaLinux World"

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./project-spec/meta-user/recipes-apps/mylib/.gdbinit**

  \# Load the PetaLinux SDK main gdbinit script

  source plnx_gdbinit

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./project-spec/meta-user/recipes-apps/mylib/README**

  PetaLinux User Application Template

  ===================================

  This directory contains a PetaLinux user application created from a template.

  You can easily import any already built application or script by copying

  it into this directory, and editing the automatically generated Makefile 

  as described below.

  Modify the "install:" target in Makefile to use $(TARGETINST) to install your

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./project-spec/meta-user/recipes-apps/mylib/mylib.bb**

  \#

  \# This file is the mylib recipe.

  \#

  SUMMARY = "Simple mylib application"

  SECTION = "PETALINUX/apps"

  LICENSE = "MIT"

  LIC_FILES_CHKSUM = "file://${COMMON_LICENSE_DIR}/MIT;md5=0835ade698e0bcf8506ecda2f7b4f302"

  SRC_URI = "file://mylib \

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): ./build/pyshtables.py

  \# pyshtables.py

  \# This file is automatically generated. Do not edit.

  _tabversion = '3.2'

  _lr_method = 'LALR'

  _lr_signature = b'\xc40\xcf\x03\xc2w\xa3h\xbe\x88\x1a\xc1\xdf\xa8U\xba'

  ​    

  _lr_action_items = {'If':([0,1,3,4,5,6,7,8,9,10,11,12,15,16,17,18,20,21,22,24,25,26,27,29,31,33,35,37,38,40,41,42,43,44,45,46,47,49,51,52,53,55,56,57,58,59,60,61,62,63,64,65,66,67,68,71,74,75,78,79,80,81,82,83,84,85,86,87,88,89,90,91,92,93,94,95,97,99,100,102,103,104,105,109,110,111,112,113,114,115,116,117,118,119,120,121,122,124,125,126,127,128,129,130,131,132,133,134,135,136,137,138,139,140,141,142,144,145,147,148,149,150,152,154,159,160,161,162,163,164,165,166,168,175,177,185,190,191,193,196,198,199,201,202,],[1,-59,-144,-7,-11,-21,-143,-67,1,-113,-87,-5,1,-82,1,-8,-127,-126,1,-84,-85,-142,1,1,1,-25,-34,-79,1,-2,-14,-138,-19,-16,-26,-1,-17,-24,-22,-12,-23,-20,-111,-119,-122,-147,-147,-3,-134,-132,-131,1,-4,-116,-118,1,-120,-128,-107,-101,-74,-60,-93,-145,1,-146,-105,-97,-103,-89,-99,-95,-91,-75,-115,-13,-123,-124,-121,-88,1,-86,-83,-18,-109,-117,-147,-114,-112,-129,-130,1,1,-6,-133,-147,1,-27,1,-66,-141,-68,-147,-108,-102,-94,-106,-98,-104,-90,-100,-96,-92,-125,1,-139,1,-73,-110,1,-9,-10,1,1,-35,-15,-140,-76,-70,-69,-62,1,1,-71,-61,-44,-36,1,1,-42,-43,-37,1,1,]),'$end':**<clipped>**

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./build/cache/bb_persist_data.sqlite3**

  <binary>

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./build/conf/bblayers.conf**

  \# WARNING: this configuration has been automatically generated and in

  \# most cases should not be edited. If you need more flexibility than

  \# this configuration provides, it is strongly suggested that you set

  \# up a proper instance of the full build system and use that instead.

  LCONF_VERSION = "7"

  BBPATH = "${TOPDIR}"

  SDKBASEMETAPATH = "/net/10.4.1.1/mnt/datastore1/tools/xilinx/petalinux-v2019.1-final/components/yocto/source/aarch64"

  BBLAYERS := " \

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./project-spec/configs/rootfs_config.old**

  \#

  \# Automatically generated file; DO NOT EDIT.

  \# Configuration

  \#

  CONFIG_system-zynqmp=y

  \#

  \# Filesystem Packages 

  \#

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./build/bitbake-cookerdaemon.log**

  --- Starting bitbake server pid 128315 at 2020-10-26 05:32:25.164646 ---

  Started bitbake server pid 128315

  Entering server connection loop

  Accepting [<socket.socket fd=7, family=AddressFamily.AF_UNIX, type=SocketKind.SOCK_STREAM, proto=0, laddr=bitbake.sock>]

  Connecting Client

  Running command ['setFeatures', [2, 1]]

  **<clipped>**

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./build/misc/rootfs_config/Kconfig.user**

  menu "apps " 

  config gpio-demo  

  ​	 bool "gpio-demo"

  ​	 help

  ​	 gpio-demo application

  ​	

  config mylib  

  ​	 bool "mylib"

  ​	 help

  ​	 Simple mylib application

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./build/misc/rootfs_config/Kconfig**

  config system-zynqmp

  ​        bool

  ​        default y

  menu "Filesystem Packages " 

  menu "admin " 

  menu "sudo " 

  config sudo  

  ​	 bool "sudo"

  ​	 help

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./project-spec/configs/rootfs_config**

  \#

  \# Automatically generated file; DO NOT EDIT.

  \# Configuration

  \#

  CONFIG_system-zynqmp=y

  \#

  \# Filesystem Packages 

  \#

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./project-spec/meta-plnx-generated/recipes-core/images/petalinux-user-image.bb**

  DESCRIPTION = "PETALINUX image definition for Xilinx boards"

  LICENSE = "MIT"

  require recipes-core/images/petalinux-image-common.inc 

  inherit extrausers 

  COMMON_FEATURES = "\

  ​		ssh-server-dropbear \

  ​		hwcodecs \

  ​		"

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./.petalinux/metadata**

  PETALINUX_VER=2019.1

  project_id=be3f335be66804710444d1488a679684

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./.petalinux/usage_statistics_copy**

  1724593236

  notsent

  command_total_run_petalinux-boot=7

  command_failures_petalinux-boot=0

  command_option_petalinux-boot=--qemu

  command_option_petalinux-boot=--kernel

  command_total_run_petalinux-config=6

  command_failures_petalinux-config=0

  command_option_petalinux-config=-c

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./.petalinux/usage_statistics_token**

  24333

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./.petalinux/usage_statistics**

  627410986

  command_total_run_petalinux-create=1

  command_failures_petalinux-create=0

  command_option_petalinux-create=-t

  command_option_value_petalinux-create=<USER_DEFINED>

  command_option_petalinux-create=--template

  command_option_value_petalinux-create=<USER_DEFINED>

  command_option_petalinux-create=--name

  command_option_value_petalinux-create=<USER_DEFINED>

  \--

  [#FILE](https://www.centennialsoftwaresolutions.com/blog/hashtags/FILE): **./all_changes.txt**

  **List Resultant CPIO Contents**

  cpio -itv < ./images/linux/rootfs.cpio | grep mylib

  drwxr-xr-x   2 root     root            0 Oct 30 19:05 usr/share/licenses/mylib

  -rw-r--r--   1 root     root         1080 Oct 30 19:05 usr/share/licenses/mylib/MIT

  -rw-r--r--   1 root     root         1080 Oct 30 19:05 usr/share/licenses/mylib/generic_MIT

  -rwxr-xr-x   1 root     root           41 Oct 30 19:05 usr/bin/mylib

  **Reference** 

  - CPIO method found at [[link](http://osr507doc.xinuos.com/en/OSUserG/_contents_of_cpio_archive.html)]
  - Xilinx logo found via https://twitter.com/xilinxinc at [[link](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)]  