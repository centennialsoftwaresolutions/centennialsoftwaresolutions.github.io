# How to Create an App in 2019.1 PetaLinux and How that App's Recipe Is Found

![Yocto_project_logo](Yocto_project_logo.png)

This post shows how to create an app using Xilinx's PetaLinux 2019.1 and how to find how the app is found by the underlying Yocto 2.6.1 thud technology that helps build it. It's mainly a reference post.

**<u><span>Create an App and Test It on a ZCU102</span></u>**

```
cd ~/plxprjs/xilinx-zcu102-2019.1
source ~/petalinux/2019.1/settings.sh
petalinux-create -t apps --name my-app --enable # can't use underscores
# Creates:
# /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app
touch start
petalinux-build -c my-app
find . -type f -cnewer start -printf "%T+\t%p\n" | sort
petalinux-build
# In another terminal: screen /dev/ttyUSB0 115200
petalinux-boot --jtag --kernel -v --hw_server-url 10.0.0.2:3121
# Username: root and password: root
root@xilinx-zcu102-2019_1:~# my-app
 Hello World!
root@xilinx-zcu102-2019_1:~# which my-app
/usr/bin/my-app
```

**_Create Console Output_**

```
petalinux-create -t apps --name my-app --enable 
# INFO: Create apps: my-app
# INFO: New apps successfully created in /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app
# INFO: Enabling created component...
# INFO: sourcing bitbake
# INFO: oldconfig rootfs
# INFO: my-app has been enabled 
```

**_File Updates_**

```
demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1$ grep -REns "my-app" *
build/misc/rootfs_config/Kconfig.user:12:config my-app  
build/misc/rootfs_config/Kconfig.user:13:	 bool "my-app"
build/misc/rootfs_config/Kconfig.user:15:	 Simple my-app application
build/tmp/work/zcu102_zynqmp-xilinx-linux/linux-xlnx/4.19-xilinx-v2019.1+gitAUTOINC+9811303824-r0/recipe-sysroot-native/usr/share/gir-1.0/Gio-2.0.gir:65415:gsettings_ENUM_FILES = my-app-enums.h my-app-misc.h
build/tmp/sysroots-components/x86_64/gobject-introspection-native/usr/share/gir-1.0/Gio-2.0.gir:65415:gsettings_ENUM_FILES = my-app-enums.h my-app-misc.h
project-spec/meta-user/recipes-apps/my-app/files/Makefile:1:APP = my-app
project-spec/meta-user/recipes-apps/my-app/files/Makefile:4:APP_OBJS = my-app.o
project-spec/meta-user/recipes-apps/my-app/README:7:file my-app.c.
project-spec/meta-user/recipes-apps/my-app/README:17:To build your application, simply run "petalinux-build -c my-app".
project-spec/meta-user/recipes-apps/my-app/my-app.bb:2:# This file is the my-app recipe.
project-spec/meta-user/recipes-apps/my-app/my-app.bb:5:SUMMARY = "Simple my-app application"
project-spec/meta-user/recipes-apps/my-app/my-app.bb:10:SRC_URI = "file://my-app.c \
project-spec/meta-user/recipes-apps/my-app/my-app.bb:22:	     install -m 0755 my-app ${D}${bindir}
project-spec/meta-user/recipes-core/images/petalinux-image-full.bbappend:6:IMAGE_INSTALL_append = " my-app"
project-spec/meta-plnx-generated/recipes-core/images/petalinux-user-image.bb:30:		my-app \
project-spec/configs/rootfs_config.old:4206:CONFIG_my-app=y
project-spec/configs/rootfs_config:4196:CONFIG_my-app=y
```

**_Directory Created_**

```
/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app
```

**_Files Created_**

```
demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1$ ls /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/*
/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb
/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/README

/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/files:
Makefile  my-app.c
```

**_Build Console Output_**

```
[INFO] building my-app
[INFO] sourcing bitbake
[INFO] generating user layers
INFO: bitbake my-app
Loading cache: 100% |############################################################################################################################| Time: 0:00:02
Loaded 3812 entries from dependency cache.
Parsing recipes: 100% |##########################################################################################################################| Time: 0:00:06
Parsing of 2779 .bb files complete (2774 cached, 5 parsed). 3814 targets, 148 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
Initialising tasks: 100% |#######################################################################################################################| Time: 0:00:00
Checking sstate mirror object availability: 100% |###############################################################################################| Time: 0:00:00
Sstate summary: Wanted 14 Found 0 Missed 28 Current 116 (0% match, 89% complete)
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 557 tasks of which 541 didn't need to be rerun and all succeeded.
INFO: Copying Images from deploy to images
NOTE: Failed to copy built images to tftp dir:  /tftpboot
[INFO] successfully built my-app
```

**_build/build.log_**

```
[INFO] building my-app
[INFO] sourcing bitbake
SDK environment now set up; additionally you may now run devtool to perform development tasks.
Run devtool --help for further details.

### Shell environment set up for builds. ###

You can now run 'bitbake <target>'

Common targets are:
    core-image-minimal
    core-image-sato
    meta-toolchain
    meta-ide-support

You can also run generated qemu images with a command like 'runqemu qemux86'
NOTE: Starting bitbake server...
[INFO] generating user layers
NOTE: Starting bitbake server...
NOTE: Resolving any missing task queue dependencies
Sstate summary: Wanted 14 Found 0 Missed 28 Current 116 (0% match, 89% complete)
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Running task 542 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_fetch)
NOTE: recipe my-app-1.0-r0: task do_fetch: Started
NOTE: recipe my-app-1.0-r0: task do_fetch: Succeeded
NOTE: Running task 543 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_prepare_recipe_sysroot)
NOTE: Running task 544 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_unpack)
NOTE: recipe my-app-1.0-r0: task do_unpack: Started
NOTE: recipe my-app-1.0-r0: task do_prepare_recipe_sysroot: Started
NOTE: recipe my-app-1.0-r0: task do_unpack: Succeeded
NOTE: Running task 545 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_patch)
NOTE: recipe my-app-1.0-r0: task do_patch: Started
NOTE: recipe my-app-1.0-r0: task do_prepare_recipe_sysroot: Succeeded
NOTE: recipe my-app-1.0-r0: task do_patch: Succeeded
NOTE: Running task 546 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_populate_lic)
NOTE: Running task 547 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_configure)
NOTE: recipe my-app-1.0-r0: task do_populate_lic: Started
NOTE: recipe my-app-1.0-r0: task do_configure: Started
NOTE: recipe my-app-1.0-r0: task do_configure: Succeeded
NOTE: Running task 548 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_compile)
NOTE: recipe my-app-1.0-r0: task do_populate_lic: Succeeded
NOTE: recipe my-app-1.0-r0: task do_compile: Started
NOTE: recipe my-app-1.0-r0: task do_compile: Succeeded
NOTE: Running task 549 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_install)
NOTE: recipe my-app-1.0-r0: task do_install: Started
NOTE: recipe my-app-1.0-r0: task do_install: Succeeded
NOTE: Running task 550 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_package)
NOTE: Running task 551 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_populate_sysroot)
NOTE: recipe my-app-1.0-r0: task do_populate_sysroot: Started
NOTE: recipe my-app-1.0-r0: task do_package: Started
NOTE: recipe my-app-1.0-r0: task do_populate_sysroot: Succeeded
NOTE: recipe my-app-1.0-r0: task do_package: Succeeded
NOTE: Running task 552 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_packagedata)
NOTE: recipe my-app-1.0-r0: task do_packagedata: Started
NOTE: recipe my-app-1.0-r0: task do_packagedata: Succeeded
NOTE: Running task 553 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_package_qa)
NOTE: Running task 554 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_package_write_rpm)
NOTE: recipe my-app-1.0-r0: task do_package_qa: Started
NOTE: recipe my-app-1.0-r0: task do_package_write_rpm: Started
NOTE: recipe my-app-1.0-r0: task do_package_qa: Succeeded
NOTE: recipe my-app-1.0-r0: task do_package_write_rpm: Succeeded
NOTE: Running task 555 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_rm_work)
NOTE: recipe my-app-1.0-r0: task do_rm_work: Started
NOTE: recipe my-app-1.0-r0: task do_rm_work: Succeeded
NOTE: Running noexec task 556 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_rm_work_all)
NOTE: Running noexec task 557 of 557 (/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app/my-app.bb:do_build)
NOTE: Tasks Summary: Attempted 557 tasks of which 541 didn't need to be rerun and all succeeded.
[INFO] successfully built my-app
```

**<u><span>How PetaLinux (BitBake) Finds the my-app Recipe aka Where Does BBPATH Get Set?</span></u>**

**_Method_**

Using the commands to manually run BitBake commands to figure out when BBPATH gets set by diffing the environment.

**_Record the Environment Before Bitbake_**

```
demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1/build$ env | sort > env-before-bb.txt
```

**_Pull in BitBake and Record ENV Diffs_**

```
cd ~/plxprjs/xilinx-zcu102-2019.1
mkdir ~/recordenv
env | sort > ~/recordenv/env-orig.txt
source ~/petalinux/2019.1/settings.sh
env | sort > ~/recordenv/env-change-1-petalinux-settings.txt
diff -u ~/recordenv/env-orig.txt ~/recordenv/env-change-1-petalinux-settings.txt > ~/recordenv/diff.orig.1
source ~/petalinux/2019.1/components/yocto/source/aarch64/environment-setup-aarch64-xilinx-linux
env | sort > ~/recordenv/env-change-2-environment-setup-aarch64-xilinx-linux.txt
diff -u ~/recordenv/env-change-1-petalinux-settings.txt ~/recordenv/env-change-2-environment-setup-aarch64-xilinx-linux.txt > ~/recordenv/diff.1.2
source ~/petalinux/2019.1/components/yocto/source/aarch64/layers/core/oe-init-build-env
env | sort > ~/recordenv/env-change-3-oe-init-build-env.txt
diff -u ~/recordenv/env-change-2-environment-setup-aarch64-xilinx-linux.txt ~/recordenv/env-change-3-oe-init-build-env.txt > ~/recordenv/diff.2.3
export PATH=~/petalinux/2019.1/tools/xsct/bin/:$PATH
which xsct
export BB_ENV_EXTRAWHITE="$BB_ENV_EXTRAWHITE PETALINUX" 
env | sort > ~/recordenv/env-change-4-all.txt
diff -u ~/recordenv/env-orig.txt ~/recordenv/env-change-4-all.txt > ~/recordenv/diff.1.4
```

Without the env:

```
cd ~/plxprjs/xilinx-zcu102-2019.1
source ~/petalinux/2019.1/settings.sh
source ~/petalinux/2019.1/components/yocto/source/aarch64/environment-setup-aarch64-xilinx-linux
source ~/petalinux/2019.1/components/yocto/source/aarch64/layers/core/oe-init-build-env
export PATH=~/petalinux/2019.1/tools/xsct/bin/:$PATH
which xsct
export BB_ENV_EXTRAWHITE="$BB_ENV_EXTRAWHITE PETALINUX" 
```

Note: which bitbake

```
demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1/build$ which bitbake
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/layers/core/bitbake/bin/bitbake
```

**_The Environment After source ~/petalinux/2019.1/settings.sh_**

Note: Additional PATH info has been bolded and additional formatting has been inserted to aid readability.

```
PATH=/home/demo/bin:/home/demo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
+PATH=
/home/demo/petalinux/2019.1/tools/xsct/petalinux/bin:
/home/demo/petalinux/2019.1/tools/common/petalinux/bin:
/home/demo/petalinux/2019.1/tools/xsct/bin:
/home/demo/petalinux/2019.1/tools/xsct/gnu/microblaze/lin/bin:
/home/demo/petalinux/2019.1/tools/xsct/gnu/armr5/lin/gcc-arm-none-eabi/bin:
/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch64/lin/aarch64-none/bin:
/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch32/lin/gcc-arm-none-eabi/bin:
/home/demo/bin:/home/demo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
+PETALINUX=/home/demo/petalinux/2019.1
+PETALINUX_VER=2019.1
```

**_The Environment After source ~/petalinux/2019.1/components/yocto/source/aarch64/environment-setup-aarch64-xilinx-linux_**

Note: Additional PATH info has been bolded and additional formatting has been inserted to aid readability.

```
+AR=aarch64-xilinx-linux-ar
+ARCH=arm64
+AS=aarch64-xilinx-linux-as 
+CC=aarch64-xilinx-linux-gcc  --sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+CFLAGS= -O2 -pipe -g -feliminate-unused-debug-types 
+CONFIG_SITE=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/site-config-aarch64-xilinx-linux
+CONFIGURE_FLAGS=--target=aarch64-xilinx-linux --host=aarch64-xilinx-linux --build=x86_64-linux --with-libtool-sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+CPP=aarch64-xilinx-linux-gcc -E  --sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+CPPFLAGS=
+CROSS_COMPILE=aarch64-xilinx-linux-
+CXX=aarch64-xilinx-linux-g++  --sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+CXXFLAGS= -O2 -pipe -g -feliminate-unused-debug-types 
+DEPLOY_DIR_IMAGE=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/deploy/images/zynqmp-generic
+GDB=aarch64-xilinx-linux-gdb
+GIT_SSL_CAINFO=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux/etc/ssl/certs/ca-certificates.crt
+KCFLAGS=--sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+LD=aarch64-xilinx-linux-ld  --sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+LDFLAGS=-Wl,-O1 -Wl,--hash-style=gnu -Wl,--as-needed
+M4=m4
+NM=aarch64-xilinx-linux-nm
+OBJCOPY=aarch64-xilinx-linux-objcopy
+OBJDUMP=aarch64-xilinx-linux-objdump

+OECORE_ACLOCAL_OPTS=-I /home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/share/aclocal
+OECORE_BASELIB=lib
+OECORE_DISTRO_VERSION=2019.1
+OECORE_NATIVE_SYSROOT=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64
+OECORE_SDK_VERSION=2019.1
+OECORE_TARGET_ARCH=aarch64
+OECORE_TARGET_OS=linux
+OECORE_TARGET_SYSROOT=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+OE_SKIP_SDK_CHECK=1
-PATH=/home/demo/petalinux/2019.1/tools/xsct/petalinux/bin:/home/demo/petalinux/2019.1/tools/common/petalinux/bin:/home/demo/petalinux/2019.1/tools/xsct/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/microblaze/lin/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/armr5/lin/gcc-arm-none-eabi/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch64/lin/aarch64-none/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/home/demo/bin:/home/demo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
+PATH=
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/sysroots/x86_64-petalinux-linux/usr/bin:
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux/usr/bin:
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/sbin:
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/sbin:
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/../x86_64-petalinux-linux/bin:
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/aarch64-xilinx-linux:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/aarch64-xilinx-linux-musl:
/home/demo/petalinux/2019.1/tools/xsct/petalinux/bin:/home/demo/petalinux/2019.1/tools/common/petalinux/bin:/home/demo/petalinux/2019.1/tools/xsct/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/microblaze/lin/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/armr5/lin/gcc-arm-none-eabi/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch64/lin/aarch64-none/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/home/demo/bin:/home/demo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

+PETALINUX_NATIVE_QEMU=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux/usr/bin/qemu-xilinx
+PETALINUX_NATIVE_SYSROOT=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux

+PKG_CONFIG_PATH=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic/usr/lib/pkgconfig:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic/usr/share/pkgconfig
+PKG_CONFIG_SYSROOT_DIR=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic

+RANLIB=aarch64-xilinx-linux-ranlib
+SDKTARGETSYSROOT=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic

+STRIP=aarch64-xilinx-linux-strip
+TARGET_PREFIX=aarch64-xilinx-linux-
```

**_The Complete Environment After source ~/petalinux/2019.1/components/yocto/source/aarch64/layers/core/oe-init-build-env_**

<u>Note: BBPATH comes in here.</u>

```
+BB_ENV_EXTRAWHITE=ALL_PROXY BBPATH_EXTRA BB_NO_NETWORK BB_NUMBER_THREADS BB_SETSCENE_ENFORCE BB_SRCREV_POLICY DISTRO FTPS_PROXY FTP_PROXY GIT_PROXY_COMMAND HTTPS_PROXY HTTP_PROXY MACHINE NO_PROXY PARALLEL_MAKE SCREENDIR SDKMACHINE SOCKS5_PASSWD SOCKS5_USER SSH_AGENT_PID SSH_AUTH_SOCK STAMPS_DIR TCLIBC TCMODE all_proxy ftp_proxy ftps_proxy http_proxy https_proxy no_proxy 
+BBPATH=/home/demo/plxprjs/xilinx-zcu102-2019.1/build
+BUILDDIR=/home/demo/plxprjs/xilinx-zcu102-2019.1/build

-OLDPWD=/home/demo
-PATH=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/sysroots/x86_64-petalinux-linux/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/sbin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/sbin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/../x86_64-petalinux-linux/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/aarch64-xilinx-linux:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/aarch64-xilinx-linux-musl:/home/demo/petalinux/2019.1/tools/xsct/petalinux/bin:/home/demo/petalinux/2019.1/tools/common/petalinux/bin:/home/demo/petalinux/2019.1/tools/xsct/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/microblaze/lin/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/armr5/lin/gcc-arm-none-eabi/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch64/lin/aarch64-none/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/home/demo/bin:/home/demo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
+OLDPWD=/home/demo/plxprjs/xilinx-zcu102-2019.1
+PATH=
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/layers/core/scripts:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/layers/core/bitbake/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/sysroots/x86_64-petalinux-linux/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/sbin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/sbin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/../x86_64-petalinux-linux/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/aarch64-xilinx-linux:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/aarch64-xilinx-linux-musl:/home/demo/petalinux/2019.1/tools/xsct/petalinux/bin:/home/demo/petalinux/2019.1/tools/common/petalinux/bin:/home/demo/petalinux/2019.1/tools/xsct/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/microblaze/lin/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/armr5/lin/gcc-arm-none-eabi/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch64/lin/aarch64-none/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/home/demo/bin:/home/demo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

-PWD=/home/demo/plxprjs/xilinx-zcu102-2019.1
+PWD=/home/demo/plxprjs/xilinx-zcu102-2019.1/build
```

**<u><span>More on BBPATH</span></u>**

**_Look at the OE Build Environment Setup Script_**

~/petalinux/2019.1/components/yocto/source/aarch64/layers/core/oe-init-build-env

shows:

if \[ -n "$BASH\_SOURCE" \]; then

​	THIS\_SCRIPT=$BASH\_SOURCE

elif \[ -n "$ZSH\_NAME" \]; then

​	THIS\_SCRIPT=$0

else

​	**THIS\_SCRIPT="$(pwd)/oe-init-build-env"**

fi

if \[ -n "$BBSERVER" \]; then

​	unset BBSERVER

fi

if \[ -z "$ZSH\_NAME" \] && \[ "$0" = "$THIS\_SCRIPT" \]; then

​	echo "Error: This script needs to be sourced. Please run as '. $THIS\_SCRIPT'"

​	exit 1

fi

if \[ -z "$OEROOT" \]; then

​	**OEROOT=$(dirname "$THIS\_SCRIPT")**

​	**OEROOT=$(readlink -f "$OEROOT") # Gets the full path**

fi

unset THIS\_SCRIPT

export OEROOT

**. $OEROOT/scripts/oe-buildenv-internal && # See below**

​	TEMPLATECONF="$TEMPLATECONF" $OEROOT/scripts/oe-setup-builddir || { **\# Below**

​	unset OEROOT

​	return 1

}

unset OEROOT

\[ -z "$BUILDDIR" \] || cd "$BUILDDIR"

**_Look at the OE-Core Build Environment Setup Script_**

cat ~/petalinux/2019.1/components/yocto/source/aarch64/layers/core/scripts/oe-buildenv-internal

<u>This ^^^ sets BBPATH to the **path/build** where **oe-buildenv-internal** was sourced</u>

**_The Environment After All Bitbake Commands_**

```
demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1/build$ diff -u ../env-before-bb.txt env-after-bb.txt 
--- ../env-before-bb.txt	2021-11-16 18:27:16.052986856 -0700
+++ env-after-bb.txt	2021-11-16 18:32:06.266997289 -0700
@@ -1,11 +1,29 @@
+AR=aarch64-xilinx-linux-ar
+ARCH=arm64
+AS=aarch64-xilinx-linux-as 
+BB_ENV_EXTRAWHITE=ALL_PROXY BBPATH_EXTRA BB_NO_NETWORK BB_NUMBER_THREADS BB_SETSCENE_ENFORCE BB_SRCREV_POLICY DISTRO FTPS_PROXY FTP_PROXY GIT_PROXY_COMMAND HTTPS_PROXY HTTP_PROXY MACHINE NO_PROXY PARALLEL_MAKE SCREENDIR SDKMACHINE SOCKS5_PASSWD SOCKS5_USER SSH_AGENT_PID SSH_AUTH_SOCK STAMPS_DIR TCLIBC TCMODE all_proxy ftp_proxy ftps_proxy http_proxy https_proxy no_proxy  PETALINUX
+BBPATH=/home/demo/plxprjs/xilinx-zcu102-2019.1/build
+BUILDDIR=/home/demo/plxprjs/xilinx-zcu102-2019.1/build
+CC=aarch64-xilinx-linux-gcc  --sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+CFLAGS= -O2 -pipe -g -feliminate-unused-debug-types 
 CLUTTER_IM_MODULE=xim
 COMPIZ_CONFIG_PROFILE=ubuntu
+CONFIG_SITE=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/site-config-aarch64-xilinx-linux
+CONFIGURE_FLAGS=--target=aarch64-xilinx-linux --host=aarch64-xilinx-linux --build=x86_64-linux --with-libtool-sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+CPP=aarch64-xilinx-linux-gcc -E  --sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+CPPFLAGS=
+CROSS_COMPILE=aarch64-xilinx-linux-
+CXX=aarch64-xilinx-linux-g++  --sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+CXXFLAGS= -O2 -pipe -g -feliminate-unused-debug-types 
 DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-J5FuREy4sE
 DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path
+DEPLOY_DIR_IMAGE=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/deploy/images/zynqmp-generic
 DESKTOP_SESSION=ubuntu
 DISPLAY=:0
+GDB=aarch64-xilinx-linux-gdb
 GDM_LANG=en_US
 GDMSESSION=ubuntu
+GIT_SSL_CAINFO=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux/etc/ssl/certs/ca-certificates.crt
 GNOME_DESKTOP_SESSION_ID=this-is-deprecated
 GNOME_KEYRING_CONTROL=
 GNOME_KEYRING_PID=
@@ -17,26 +35,53 @@
 IM_CONFIG_PHASE=1
 INSTANCE=
 JOB=dbus
+KCFLAGS=--sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
 LANG=en_US.UTF-8
 LANGUAGE=en_US
+LD=aarch64-xilinx-linux-ld  --sysroot=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+LDFLAGS=-Wl,-O1 -Wl,--hash-style=gnu -Wl,--as-needed
 LESSCLOSE=/usr/bin/lesspipe %s %s
 LESSOPEN=| /usr/bin/lesspipe %s
 LOGNAME=demo
 LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
+M4=m4
 MANDATORY_PATH=/usr/share/gconf/ubuntu.mandatory.path
-PATH=/home/demo/bin:/home/demo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
-PWD=/home/demo/plxprjs/xilinx-zcu102-2019.1
+NM=aarch64-xilinx-linux-nm
+OBJCOPY=aarch64-xilinx-linux-objcopy
+OBJDUMP=aarch64-xilinx-linux-objdump
+OECORE_ACLOCAL_OPTS=-I /home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/share/aclocal
+OECORE_BASELIB=lib
+OECORE_DISTRO_VERSION=2019.1
+OECORE_NATIVE_SYSROOT=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64
+OECORE_SDK_VERSION=2019.1
+OECORE_TARGET_ARCH=aarch64
+OECORE_TARGET_OS=linux
+OECORE_TARGET_SYSROOT=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+OE_SKIP_SDK_CHECK=1
+OLDPWD=/home/demo/plxprjs/xilinx-zcu102-2019.1
+PATH=/home/demo/petalinux/2019.1/tools/xsct/bin/:/home/demo/petalinux/2019.1/tools/hsm/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/layers/core/scripts:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/layers/core/bitbake/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/sysroots/x86_64-petalinux-linux/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/sbin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/sbin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/../x86_64-petalinux-linux/bin:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/aarch64-xilinx-linux:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/x86_64/usr/bin/aarch64-xilinx-linux-musl:/home/demo/petalinux/2019.1/tools/xsct/petalinux/bin:/home/demo/petalinux/2019.1/tools/common/petalinux/bin:/home/demo/petalinux/2019.1/tools/xsct/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/microblaze/lin/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/armr5/lin/gcc-arm-none-eabi/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch64/lin/aarch64-none/bin:/home/demo/petalinux/2019.1/tools/xsct/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/home/demo/bin:/home/demo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
+PETALINUX=/home/demo/petalinux/2019.1
+PETALINUX_NATIVE_QEMU=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux/usr/bin/qemu-xilinx
+PETALINUX_NATIVE_SYSROOT=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/buildtools/sysroots/x86_64-petalinux-linux
+PETALINUX_VER=2019.1
+PKG_CONFIG_PATH=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic/usr/lib/pkgconfig:/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic/usr/share/pkgconfig
+PKG_CONFIG_SYSROOT_DIR=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
+PWD=/home/demo/plxprjs/xilinx-zcu102-2019.1/build
 QT4_IM_MODULE=xim
 QT_ACCESSIBILITY=1
 QT_IM_MODULE=ibus
 QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
 QT_QPA_PLATFORMTHEME=appmenu-qt5
+RANLIB=aarch64-xilinx-linux-ranlib
+SDKTARGETSYSROOT=/home/demo/petalinux/2019.1/components/yocto/source/aarch64/tmp/sysroots/zynqmp-generic
 SESSION_MANAGER=local/ubuntu:@/tmp/.ICE-unix/1767,unix/ubuntu:/tmp/.ICE-unix/1767
 SESSIONTYPE=gnome-session
 SESSION=ubuntu
 SHELL=/bin/bash
 SHLVL=1
 SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
+STRIP=aarch64-xilinx-linux-strip
+TARGET_PREFIX=aarch64-xilinx-linux-
 TERM=xterm-256color
 UPSTART_SESSION=unix:abstract=/com/ubuntu/upstart-session/1000/1536
```

Of note: BB\_ENV\_EXTRAWHITE

```
+BB_ENV_EXTRAWHITE=ALL_PROXY BBPATH_EXTRA BB_NO_NETWORK BB_NUMBER_THREADS BB_SETSCENE_ENFORCE BB_SRCREV_POLICY DISTRO FTPS_PROXY FTP_PROXY GIT_PROXY_COMMAND HTTPS_PROXY HTTP_PROXY MACHINE NO_PROXY PARALLEL_MAKE SCREENDIR SDKMACHINE SOCKS5_PASSWD SOCKS5_USER SSH_AGENT_PID SSH_AUTH_SOCK STAMPS_DIR TCLIBC TCMODE all_proxy ftp_proxy ftps_proxy http_proxy https_proxy no_proxy  PETALINUX
```

More on BB\_ENV\_EXTRAWHITE

```
From https://www.yoctoproject.org/docs/2.6.1/bitbake-user-manual/bitbake-user-manual.html

Specifies an additional set of variables to allow through (whitelist) from the external environment into BitBake's datastore. This list of variables are on top of the internal list set in BB_ENV_WHITELIST.
```

Of note: BBPATH

```
+BBPATH=/home/demo/plxprjs/xilinx-zcu102-2019.1/build
```

More on BBPATH

```
From https://www.yoctoproject.org/docs/2.6.1/bitbake-user-manual/bitbake-user-manual.html

Used by BitBake to locate class (.bbclass) and configuration (.conf) files. This variable is analogous to the PATH variable.

If you run BitBake from a directory outside of the build directory, you must be sure to set BBPATH to point to the build directory. Set the variable as you would any environment variable and then run BitBake:

     $ BBPATH="build_directory"
     $ export BBPATH
     $ bitbake target
```

After launching Bitbake run:

<u>bitbake -e > bitbake.e.out</u>

<u>This ^^^ file has all of the variables.</u>

**<u><span>Completing the story</span></u>**

This gets created above:

```
/home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-apps/my-app
```

conf/bblayers.conf is read, project-spec/meta-user comes in

Tip: Use cat bitbake.e.out | grep TOPDIR to get TOPDIR

```
demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1/build$ cat conf/bblayers.conf 
# WARNING: this configuration has been automatically generated and in
# most cases should not be edited. If you need more flexibility than
# this configuration provides, it is strongly suggested that you set
# up a proper instance of the full build system and use that instead.

LCONF_VERSION = "7"

BBPATH = "${TOPDIR}"
SDKBASEMETAPATH = "/home/demo/petalinux/2019.1/components/yocto/source/aarch64"
BBLAYERS := " \
  ${SDKBASEMETAPATH}/layers/core/meta \
  ${SDKBASEMETAPATH}/layers/core/meta-poky \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-perl \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-python \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-filesystems \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-gnome \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-multimedia \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-networking \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-webserver \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-xfce \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-initramfs \
  ${SDKBASEMETAPATH}/layers/meta-openembedded/meta-oe \
  ${SDKBASEMETAPATH}/layers/meta-browser \
  ${SDKBASEMETAPATH}/layers/meta-qt5 \
  ${SDKBASEMETAPATH}/layers/meta-xilinx/meta-xilinx-bsp \
  ${SDKBASEMETAPATH}/layers/meta-xilinx/meta-xilinx-contrib \
  ${SDKBASEMETAPATH}/layers/meta-xilinx-tools \
  ${SDKBASEMETAPATH}/layers/meta-petalinux \
  ${SDKBASEMETAPATH}/layers/meta-virtualization \
  ${SDKBASEMETAPATH}/layers/meta-openamp \
  ${SDKBASEMETAPATH}/workspace \
  /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-plnx-generated \
  /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user \
  "

```

...and BBFILES is updated from **project-spec/meta-user/conf/layer.conf**

```
cd ~/plxprjs/xilinx-zcu102-2019.1/build
cat /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/conf/layer.conf 
# We have a conf and classes directory, add to BBPATH
BBPATH .= ":${LAYERDIR}"

# We have recipes-* directories, add to BBFILES
BBFILES += "${LAYERDIR}/recipes-*/*/*.bb \ # < Here's where are files get picked up
	${LAYERDIR}/recipes-*/*/*.bbappend" 

BBFILE_COLLECTIONS += "meta-user"
BBFILE_PATTERN_meta-user = "^${LAYERDIR}/"
BBFILE_PRIORITY_meta-user = "6"
LAYERSERIES_COMPAT_meta-user = "thud"
```

**<u><span>Open Questions</span></u>**

Q1: Why does **conf/bblayers.conf** set BBPATH when ~/petalinux/2019.1/components/yocto/source/aarch64/layers/core/scripts/oe-buildenv-internal sets BBPATH?

Note: you can comment the BBPATH assignment in **conf/bblayers.conf** out and everything still works.

Q2: Why doesn't **conf/bblayers.conf** use BBPATH := "${TOPDIR}" instead of BBPATH = "${TOPDIR}"?

Q2.1: What is the impact of this?

Q2.2: Is this a bug?

**<u><span>References</span></u>**

-   [<u><span>https://www.yoctoproject.org/docs/2.6.1/bitbake-user-manual/bitbake-user-manual.html</span></u>](https://www.yoctoproject.org/docs/2.6.1/bitbake-user-manual/bitbake-user-manual.html)
    
-   Xilinx logo from [<u><span>https://www.xilinx.com/etc.clientlibs/site/clientlibs/xilinx/site-all/resources/imgs/header/xilinx-header-logo.svg</span></u>](https://www.xilinx.com/etc.clientlibs/site/clientlibs/xilinx/site-all/resources/imgs/header/xilinx-header-logo.svg)
    
-   Yocto icon from [<u><span>https://www.linuxfoundation.org/wp-content/uploads/yocto.svg</span></u>](https://www.linuxfoundation.org/wp-content/uploads/yocto.svg)
    
-   [<u><span>https://a4z.gitlab.io/docs/BitBake/guide.html</span></u>](https://a4z.gitlab.io/docs/BitBake/guide.html)
    
-   A good guide: [<u><span>https://a4z.gitlab.io/docs/BitBake/guide.html</span></u>](https://a4z.gitlab.io/docs/BitBake/guide.html)
    

**_Extra: Find the Version of Yocto that Ships with PetaLinux 2019.1_**

```
demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1$ find ~/petalinux -name *.conf -print0 | xargs --null grep -HEi 'DISTRO_CODENAME =|DISTRO_VERSION ='
```

_Output:_

```
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/layers/meta-petalinux/conf/distro/petalinux.conf:DISTRO_VERSION = "${XILINX_VER_MAIN}"
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_VERSION = "2.6.1"
/home/demo/petalinux/2019.1/components/yocto/source/aarch64/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_CODENAME = "thud"
/home/demo/petalinux/2019.1/components/yocto/source/microblaze_full/layers/meta-petalinux/conf/distro/petalinux.conf:DISTRO_VERSION = "${XILINX_VER_MAIN}"
/home/demo/petalinux/2019.1/components/yocto/source/microblaze_full/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_VERSION = "2.6.1"
/home/demo/petalinux/2019.1/components/yocto/source/microblaze_full/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_CODENAME = "thud"
/home/demo/petalinux/2019.1/components/yocto/source/microblaze_lite/layers/meta-petalinux/conf/distro/petalinux.conf:DISTRO_VERSION = "${XILINX_VER_MAIN}"
/home/demo/petalinux/2019.1/components/yocto/source/microblaze_lite/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_VERSION = "2.6.1"
/home/demo/petalinux/2019.1/components/yocto/source/microblaze_lite/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_CODENAME = "thud"
/home/demo/petalinux/2019.1/components/yocto/source/arm/layers/meta-petalinux/conf/distro/petalinux.conf:DISTRO_VERSION = "${XILINX_VER_MAIN}"
/home/demo/petalinux/2019.1/components/yocto/source/arm/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_VERSION = "2.6.1"
/home/demo/petalinux/2019.1/components/yocto/source/arm/layers/core/meta-poky/conf/distro/poky.conf:DISTRO_CODENAME = "thud"
```