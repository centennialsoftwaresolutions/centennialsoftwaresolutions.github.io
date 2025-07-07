# linux-xlnx won't build in devtool

![xilinx_logo](xilinx_logo.png)

This post is a summary of an error that I hit when trying to use devtool to rebuild the Linux kernel using PetaLinux 2018.2 from Xilinx: "could not find kconf openamp.cfg, included from /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx/oe-local-files/openamp.scc."

**<u><span>Steps to Reproduce</span></u>**

**1 BUILD THE LINUX KERNEL FROM SOURCE AND SAVE CHANGES**

**1.1 PULL IN PETALINUX TOOLS**

**1.1.1 Steps**

1\. Open a new terminal.

2\. Type **cd ~/plxprjs/xilinx-zc706-2018.2/**

3\. Type **source /opt/pkg/petalinux/settings.sh**

I see:

```
PetaLinux environment set to '/opt/pkg/petalinux'
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution
```

**1.2 PULL IN BITBAKE**

**1.2.1 Note**

I'm placed into ~/plxprjs/xilinx-zc706-2018.2/build/ after this sequence.

**1.2.2 Steps**

1\. Type **cd ~/plxprjs/xilinx-zc706-2018.2/**

2\. Type the following:

**source /opt/pkg/petalinux/components/yocto/source/arm/environment-setup-cortexa9hf-neon-xilinx-linux-gnueabi**

I see:

```
SDK environment now set up; additionally you may now run devtool to perform development tasks.
Run devtool --help for further details.
```

**source /opt/pkg/petalinux/components/yocto/source/arm/layers/core/oe-init-build-env**

I see:

```
### Shell environment set up for builds. ###

You can now run 'bitbake '

Common targets are:
    core-image-minimal
    core-image-sato
    meta-toolchain
    meta-ide-support

You can also run generated qemu images with a command like 'runqemu qemux86'
```

\# this ^^^ puts you into PLXPROJ/build

\# stay here to run BitBake commands

**export PATH=/opt/pkg/petalinux/tools/hsm/bin:$PATH**

**export BB\_ENV\_EXTRAWHITE="$BB\_ENV\_EXTRAWHITE PETALINUX"**

**1.3 PULL U-BOOT-XLNX INTO DEVTOOL**

**1.3.1 Steps**

1\. Type **cd ~/plxprjs/xilinx-zc706-2018.2/build/**

2\. Type **devtool modify linux-xlnx**

I see:

```
NOTE: Starting bitbake server...
Loading cache: 100% |############################################| Time: 0:00:03
Loaded 3423 entries from dependency cache.
Parsing recipes: 100% |##########################################| Time: 0:00:14
Parsing of 2552 .bb files complete (2517 cached, 35 parsed). 3425 targets, 147 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
Initialising tasks: 100% |#######################################| Time: 0:00:16
Checking sstate mirror object availability: 100% |###############| Time: 0:00:02
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 343 tasks of which 334 didn't need to be rerun and all succeeded.
NOTE: Adding local source files to srctree...
NOTE: Copying kernel config to srctree
NOTE: Source tree extracted to /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx
NOTE: Recipe linux-xlnx now set up to build from /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx

Note: this will checkout the Linux kernel to /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx
```

**1.4 MAKE A CHANGE**

**1.4.1 Steps**

1\. Type **cd /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx**

2\. Type **vi init/main.c**

3\. Make this change:

```
diff --git a/init/main.c b/init/main.c
index 0ee9c686..fdc5c1a 100644
--- a/init/main.c
+++ b/init/main.c
@@ -707,6 +707,7 @@ asmlinkage __visible void __init start_kernel(void)
        }
 
        /* Do the rest non-__init'ed, we're now alive */
+       printk(KERN_ERR "######## Finished %s ########\n", __func__);
        rest_init();
 }
```

**1.5 BUILD THE CHANGE**

**1.5.1 Steps**

1\. Type **cd ~/plxprjs/xilinx-zc706-2018.2/build/**

2\. Type **bitbake linux-xlnx**

I see:

```
Loading cache: 100% |############################################| Time: 0:00:03
Loaded 3423 entries from dependency cache.
Parsing recipes: 100% |##########################################| Time: 0:00:15
Parsing of 2552 .bb files complete (2516 cached, 36 parsed). 3425 targets, 147 skipped, 0 masked, 0 errors.
NOTE: There are 1 recipes to be removed from sysroot zc706-zynq7, removing...
NOTE: Resolving any missing task queue dependencies
Initialising tasks: 100% |#######################################| Time: 0:00:20
Checking sstate mirror object availability: 100% |###############| Time: 0:00:23
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
ERROR: linux-xlnx-4.14-xilinx-v2018.2+git999-r0 do_kernel_metadata: Could not generate configuration queue for zc706-zynq7.
ERROR: linux-xlnx-4.14-xilinx-v2018.2+git999-r0 do_kernel_metadata: Function failed: do_kernel_metadata (log file is located at /home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/temp/log.do_kernel_metadata.1117)
ERROR: Logfile of failure stored in: /home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/temp/log.do_kernel_metadata.1117
Log data follows:
| DEBUG: Executing python function extend_recipe_sysroot
| NOTE: Direct dependencies are ['/opt/pkg/petalinux/components/yocto/source/arm/layers/core/meta/recipes-kernel/kern-tools/kern-tools-native_git.bb:do_populate_sysroot']
| NOTE: Installed into sysroot: ['kern-tools-native', 'quilt-native']
| NOTE: Skipping as already exists in sysroot: []
| DEBUG: sed -e 's:^[^/]*/:/home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/recipe-sysroot-native/:g' /home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/sysroots-components/x86_64/quilt-native/fixmepath | xargs sed -i -e 's:FIXMESTAGINGDIRTARGET:/home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/recipe-sysroot:g; s:FIXMESTAGINGDIRHOST:/home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/recipe-sysroot-native:g' -e 's:FIXME_COMPONENTS_DIR:/home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/sysroots-components:g' -e 's:FIXME_HOSTTOOLS_DIR:/home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/hosttools:g' -e 's:FIXME_PKGDATA_DIR:/home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/pkgdata/zc706-zynq7:g' -e 's:FIXME_PSEUDO_LOCALSTATEDIR:/home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/pseudo/:g' -e 's:FIXME_LOGFIFO:/home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/temp/fifo.1117:g'
| DEBUG: Python function extend_recipe_sysroot finished
| DEBUG: Executing shell function do_kernel_metadata
| ERROR: could not find kconf openamp.cfg, included from /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx/oe-local-files/openamp.scc
| ERROR: Could not generate configuration queue for zc706-zynq7.
| ERROR: could not process input files: /home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/defconfig /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx/oe-local-files/openamp.scc /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx/oe-local-files/plnx_kernel.cfg /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx/oe-local-files/bsp.cfg
|        See /tmp/tmp.ql3ECphvxz for details
| WARNING: /home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/temp/run.do_kernel_metadata.1117:1 exit 1 from 'exit 1'
| ERROR: Function failed: do_kernel_metadata (log file is located at /home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/linux-xlnx/4.14-xilinx-v2018.2+git999-r0/temp/log.do_kernel_metadata.1117)
ERROR: Task (/opt/pkg/petalinux/components/yocto/source/arm/layers/meta-xilinx/meta-xilinx-bsp/recipes-kernel/linux/linux-xlnx_2018.2.bb:do_kernel_metadata) failed with exit code '1'
NOTE: Tasks Summary: Attempted 1325 tasks of which 1321 didn't need to be rerun and 1 failed.

Summary: 1 task failed:
  /opt/pkg/petalinux/components/yocto/source/arm/layers/meta-xilinx/meta-xilinx-bsp/recipes-kernel/linux/linux-xlnx_2018.2.bb:do_kernel_metadata
Summary: There were 2 ERROR messages shown, returning a non-zero exit code.
```

**1.6 EXIT DEVTOOL**

**1.6.1 Steps**

1\. Type **cd ~/plxprjs/xilinx-zc706-2018.2/build/**

2\. Type **devtool reset --no-clean linux-xlnx**

I see:

```
NOTE: Starting bitbake server...
NOTE: Leaving source tree /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/linux-xlnx as-is; if you no longer need it then please delete it manually
```

3\. Type **cd /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources**

4\. Type **rm-rf linux-xlnx**

**<u><span>Reference</span></u>**

Xilinx logo clipped from [xilinx.com](http://xilinx.com/)