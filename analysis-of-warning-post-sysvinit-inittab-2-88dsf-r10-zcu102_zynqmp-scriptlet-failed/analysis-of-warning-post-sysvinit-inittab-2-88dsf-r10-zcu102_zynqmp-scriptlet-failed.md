# Analysis of warning: %post(sysvinit-inittab-2.88dsf-r10.zcu102_zynqmp) scriptlet failed

![xilinx_logo_1](xilinx_logo_1.png)

This post analyzes the warning message seen when running petalinux-build on a ZCU102 on release 2018.2 it comes to a conclusion that differs from Xilinx's.

**<u><span>Warning</span></u>**

WARNING: petalinux-user-image-1.0-r0 do\_rootfs: \[log\_check\] petalinux-user-image: found 1 warning message in the logfile:

\[log\_check\] warning: %post(sysvinit-inittab-2.88dsf-r10.zcu102\_zynqmp) scriptlet failed, exit status 1

**<u><span>Xilinx's Answer Record</span></u>**

Xilinx lists the following info in an Answer Record (AR) at \[[<u><span>link</span></u>](https://www.xilinx.com/support/answers/71110.html)\]:

_The post install scripts are deferred for the first run on target. These warnings can be ignored._

**<u><span>Further investigation</span></u>**

1\. Get the **recipe** (petalinux-user-image-1.0-r0) and **task** (do\_rootfs) from the message above or from typing **grep warning ./build/build.log**

2\. Find log.task\_order by typing **find . -name "log.task\_order" | grep petalinux-user-image** to get all the tasks run:

```
zpfeffer@z:~/plxprjs/xilinx-zcu102-2018.2$ find . -name "log.task_order" | grep petalinux-user-image
./build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/temp/log.task_order
```

3\. Look at the file to get the specific log by typing **cat build/tmp/work/zcu102\_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/temp/log.task\_order**

```
zpfeffer@z:~/plxprjs/xilinx-zcu102-2018.2$ cat build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/temp/log.task_order 
do_prepare_recipe_sysroot (20449): log.do_prepare_recipe_sysroot.20449
do_populate_lic (29532): log.do_populate_lic.29532
do_rootfs (21453): log.do_rootfs.21453
do_image_qa (27096): log.do_image_qa.27096
do_image (2248): log.do_image.2248
do_image_ext3 (8958): log.do_image_ext3.8958
do_image_ext4 (20981): log.do_image_ext4.20981
do_image_cpio (10318): log.do_image_cpio.10318
do_image_tar (7954): log.do_image_tar.7954
do_image_jffs2 (4299): log.do_image_jffs2.4299
do_image_complete (27999): log.do_image_complete.27999
do_rm_work (16259): log.do_rm_work.16259
```

4\. Open the file and search for "warning" you'll see:

```
  Installing       : sysvinit-inittab-2.88dsf-r10.zcu102_zynqmp          95/147
  Running scriptlet: sysvinit-inittab-2.88dsf-r10.zcu102_zynqmp          95/147
warning: %post(sysvinit-inittab-2.88dsf-r10.zcu102_zynqmp) scriptlet failed, exit status 1
```

This is an error related to installing an RPM package. Type **find . -name "sysvinit-inittab-2.88dsf-r10\*"** to find the RPM: **./build/tmp/deploy/rpm/zcu102\_zynqmp/sysvinit-inittab-2.88dsf-r10.zcu102\_zynqmp.rpm**

5\. Type **sudo apt install rpm**

6\. Type **rpm -qp --scripts ./build/tmp/deploy/rpm/zcu102\_zynqmp/sysvinit-inittab-2.88dsf-r10.zcu102\_zynqmp.rpm**

You'll see:

```
zpfeffer@z:~/plxprjs/xilinx-zcu102-2018.2$ rpm -qp --scripts ./build/tmp/deploy/rpm/zcu102_zynqmp/sysvinit-inittab-2.88dsf-r10.zcu102_zynqmp.rpm
postinstall scriptlet (using /bin/sh):
# sysvinit-inittab - postinst
# run this on the target
if [ "x$D" = "x" ] && [ -e /proc/consoles ]; then
	tmp="115200;ttyPS0 115200;hvc0"
	for i in $tmp
	do
		j=`echo ${i} | sed -e s/^.*\;//g -e s/\:.*//g`
		k=`echo ${i} | sed s/^.*\://g`
		if [ -z "`grep ${j} /proc/consoles`" ]; then
			if [ -z "${k}" ] || [ -z "`grep ${k} /proc/consoles`" ] || [ ! -e /dev/${j} ]; then
				sed -i -e /^.*${j}\ /d -e /^.*${j}$/d /etc/inittab
			fi
		fi
	done
	kill -HUP 1
else
	if [ "115200;ttyPS0 115200;hvc0" = "" ]; then
		exit 0
	else
		exit 1
	fi
fi
```

7\. Type **find . -name "petalinux-user-image\*.bb"** to locate the [petalinux-user-image-1.0-r0.bb](http://petalinux-user-image-1.0-r0.bb/) recipe:

```
zpfeffer@z:~/plxprjs/xilinx-zcu102-2018.2$ find . -name "petalinux-user-image*.bb"
./project-spec/meta-plnx-generated/recipes-core/images/petalinux-user-image.bb
```

8\. The file contains:

```
DESCRIPTION = "PETALINUX image definition for Xilinx boards"
LICENSE = "MIT"

require recipes-core/images/petalinux-image-common.inc

inherit extrausers
IMAGE_LINGUAS = " "

IMAGE_INSTALL = "\
                kernel-modules \
                mtd-utils \
                canutils \
                openssh-sftp-server \
                pciutils \
                run-postinsts \
                udev-extraconf \
                packagegroup-core-boot \
                packagegroup-core-ssh-dropbear \
                tcf-agent \
                bridge-utils \
                hellopm \
                "
EXTRA_USERS_PARAMS = "usermod -P root root;"
```

Which roughly corresponds to lines like this in **build/tmp/work/zcu102\_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/temp/log.do\_rootfs**

```
update-alternatives: Linking /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/rootfs/sbin/nologin to /sbin/nologin.shadow
  Installing       : packagegroup-core-boot-1.0-r17.zcu102_zynqmp       101/147
  Running scriptlet: tcf-agent-1.7.0+git0+23bd5a2c8b-r0.aarch64         102/147
 Removing any system startup links for tcf-agent ...
  Installing       : tcf-agent-1.7.0+git0+23bd5a2c8b-r0.aarch64         102/147
  Running scriptlet: tcf-agent-1.7.0+git0+23bd5a2c8b-r0.aarch64         102/147
 Adding system startup for /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/rootfs/etc/init.d/tcf-agent.
  Installing       : canutils-4.0.6-r0.aarch64                          103/147
  Installing       : kernel-modules-4.14+xilinx+v2018.2+git0+ad4cd988   104/147
  Installing       : packagegroup-core-ssh-dropbear-1.0-r1.noarch       105/147
  Installing       : udev-extraconf-1.1-r0.aarch64                      106/147
  Installing       : bridge-utils-1.5-r0.aarch64                        107/147
  Running scriptlet: bridge-utils-1.5-r0.aarch64                        107/147
update-alternatives: Linking /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/rootfs/usr/sbin/brctl to /usr/sbin/brctl.bridge-utils
  Installing       : mtd-utils-2.0.0-r0.aarch64                         108/147
  Installing       : openssh-sftp-server-7.5p1-r0.aarch64               109/147
  Running scriptlet: run-postinsts-1.0-r9.noarch                        110/147
 Removing any system startup links for run-postinsts ...
  Installing       : run-postinsts-1.0-r9.noarch                        110/147
  Running scriptlet: run-postinsts-1.0-r9.noarch                        110/147
 Adding system startup for /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/rootfs/etc/init.d/run-postinsts.
  Installing       : hellopm-0.1-r0.zynqmp                              111/147
  Installing       : update-rc.d-0.7-r5.noarch                          112/147
  Running scriptlet: busybox-inetd-1.24.1-r0.aarch64                    113/147
update-rc.d: /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/rootfs/etc/init.d/inetd.busybox exists during rc.d purge (continuing)
```

9\. **recipes-core/images/petalinux-image-common.inc** is located in the PetaLinux Tools install directory: **/opt/pkg/petalinux**

```
zpfeffer@z:/opt/pkg/petalinux$ find . -name "petalinux-image-common.inc"
./components/yocto/source/arm/layers/meta-petalinux/recipes-core/images/petalinux-image-common.inc
./components/yocto/source/microblaze_lite/layers/meta-petalinux/recipes-core/images/petalinux-image-common.inc
./components/yocto/source/microblaze_full/layers/meta-petalinux/recipes-core/images/petalinux-image-common.inc
./components/yocto/source/aarch64/layers/meta-petalinux/recipes-core/images/petalinux-image-common.inc
```

Note 1: all of these files are the same

Note 2: this may be an indication of inefficiencies in the build system

10\. In **petalinux-image-common.inc** the **core-image** class is inherited:

```
inherit core-image autologin

COMMON_FEATURES = " \
    ssh-server-dropbear \
    hwcodecs \
    "
IMAGE_FEATURES += "${COMMON_FEATURES}"

COMMON_INSTALL = " \
    openssh-sftp-server \
...
```

11\. Back to **build/tmp/work/zcu102\_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/temp/log.do\_rootfs**:

At the top of the file is **DEBUG: Executing python function extend\_recipe\_sysroot**

The **DEBUG: Executing python** before the warning is **do\_rootfs**. This implies that the environment that the scriptlet executes in may be built by the **do\_sysroot** Python function:

```
DEBUG: Executing python function do_rootfs
NOTE: ###### Generate rootfs #######
NOTE: Executing '/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/recipe-sysroot-native/usr/bin/createrepo_c --update -q /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/oe-rootfs-repo' ...
NOTE: Added oe-repo repo from /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/oe-rootfs-repo
oe-repo                                          26 MB/s | 1.0 MB     00:00
Last metadata expiration check: 0:00:01 ago on Fri 07 Sep 2018 01:19:46 PM UTC.
Metadata cache created.

NOTE: Added oe-repo repo from /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/tmp/work/zcu102_zynqmp-xilinx-linux/petalinux-user-image/1.0-r0/oe-rootfs-repo
Last metadata expiration check: 0:00:04 ago on Fri 07 Sep 2018 01:19:46 PM UTC.
Dependencies resolved.
================================================================================
 Package                            Arch          Version         Repository
                                                                           Size
================================================================================
Installing:
 base-passwd                        aarch64       3.5.29-r0       oe-repo 7.0 k
 bridge-utils                       aarch64       1.5-r0          oe-repo  16 k
...
Installing dependencies:
 base-files                         zcu102_zynqmp 3.0.14-r89      oe-repo  12 k
 bash                               aarch64       4.4-r0          oe-repo 358 k
 busybox                            aarch64       1.24.1-r0       oe-repo 346 k
...
 sysvinit                           aarch64       2.88dsf-r14     oe-repo  53 k
 sysvinit-inittab                   zcu102_zynqmp 2.88dsf-r10     oe-repo 7.5 k
 sysvinit-pidof                     aarch64       2.88dsf-r14     oe-repo  13 k
```

12\. Back to **rpm -qp --scripts ./build/tmp/deploy/rpm/zcu102\_zynqmp/sysvinit-inittab-2.88dsf-r10.zcu102\_zynqmp.rpm**

```
zpfeffer@z:~/plxprjs/xilinx-zcu102-2018.2$ rpm -qp --scripts ./build/tmp/deploy/rpm/zcu102_zynqmp/sysvinit-inittab-2.88dsf-r10.zcu102_zynqmp.rpm
postinstall scriptlet (using /bin/sh):
# sysvinit-inittab - postinst
# run this on the target
if [ "x$D" = "x" ] && [ -e /proc/consoles ]; then
	tmp="115200;ttyPS0 115200;hvc0"
	for i in $tmp
	do
		j=`echo ${i} | sed -e s/^.*\;//g -e s/\:.*//g`
		k=`echo ${i} | sed s/^.*\://g`
		if [ -z "`grep ${j} /proc/consoles`" ]; then
			if [ -z "${k}" ] || [ -z "`grep ${k} /proc/consoles`" ] || [ ! -e /dev/${j} ]; then
				sed -i -e /^.*${j}\ /d -e /^.*${j}$/d /etc/inittab
			fi
		fi
	done
	kill -HUP 1
else
	if [ "115200;ttyPS0 115200;hvc0" = "" ]; then
		exit 0
	else
		exit 1
	fi
fi
```

A break down of this script:

Path 1

if $D is empty and /proc/consoles exists then

for 115200;ttyPS0 and 11520;hvc0

set j to ttyPS0 for 115200;ttyPS0 then set j to hvc0 for 11520;hvc0 on the next iteration

set k to 115200;ttyPS0 then set k to11520;hvc0 on the next iteration

if ttyPS0 (or hvc0) isn't in /proc/consoles then

if k is null or k isn't in /proc/consoles or there doesn't exist /dev/ttyPS0 or /dev/hvc0

then edit /etc/inittab in place and delete ttyPS0 or hv0 if it exists at all

**i.e. if the console device doesn't exist in the system, don't use it in /etc/inittab**

if $D is empty and /proc/consoles exists then restart init and re-read /etc/inittab

Path 2

if /proc/consoles doesn't exist then return 1, **which is what we see.**

13\. What inittab is installed into the rootfs?

There are 8 inittab files:

```
zpfeffer@z:/opt/pkg/petalinux$ find . -name "inittab"
./components/yocto/source/arm/layers/core/meta/recipes-core/sysvinit/sysvinit-inittab/inittab
./components/yocto/source/arm/layers/core/meta/recipes-core/busybox/files/inittab
./components/yocto/source/microblaze_lite/layers/core/meta/recipes-core/sysvinit/sysvinit-inittab/inittab
./components/yocto/source/microblaze_lite/layers/core/meta/recipes-core/busybox/files/inittab
./components/yocto/source/microblaze_full/layers/core/meta/recipes-core/sysvinit/sysvinit-inittab/inittab
./components/yocto/source/microblaze_full/layers/core/meta/recipes-core/busybox/files/inittab
./components/yocto/source/aarch64/layers/core/meta/recipes-core/sysvinit/sysvinit-inittab/inittab
./components/yocto/source/aarch64/layers/core/meta/recipes-core/busybox/files/inittab
```

Note 1: all of the sysvinit-inittab/inittab files are the same

Note 2: all of the files/inittab are the same

In both sysvinit-inittab/inittab and files/inittab there is no console mentioned.

**<u><span>Conclusion</span></u>**

Xilinx listed: _The post install scripts are deferred for the first run on target. These warnings can be ignored._

_._..but based on my analysis, this is not accurate. The scriptlet appears to only run at the point the RPM is installed; this means that the scriptlet is not "deferred" for the first run of the target, its never run.

Assuming the analysis is correct, the warning can still be ignored in this case because the inittabs in the 2018.2 PetaLinux Tools release doesn't contains any consoles.

**<u><span>References</span></u>**

-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]
    
-   **Show RPM packages** at \[[<u><span>link</span></u>](https://www.commandlinefu.com/commands/view/7555/show-rpm-packages-scriptlets)\]
    
-   Sysvinit-2.88dsf described at \[[<u><span>link</span></u>](http://www.linuxfromscratch.org/lfs/view/6.8/chapter06/sysvinit.html)\]
    
-   **Unix How To: The Linux /etc/inittab file** at \[[<u><span>link</span></u>](https://www.networkworld.com/article/2693438/operating-systems/unix-how-to-the-linux-etc-inittab-file.html)\]
    
-   SIGHUP Wiki at \[[<u><span>link</span></u>](https://en.wikipedia.org/wiki/SIGHUP)\]
    
-   **What kill -HUP 1 does** at \[[<u><span>link</span></u>](https://www.cyberciti.biz/faq/linux-unix-kill-hup-1-reread-etcinittab-file/)\]