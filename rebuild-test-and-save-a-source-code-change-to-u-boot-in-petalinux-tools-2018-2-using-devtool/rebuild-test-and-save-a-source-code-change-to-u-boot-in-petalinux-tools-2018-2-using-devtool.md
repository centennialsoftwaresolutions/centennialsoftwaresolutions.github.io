# Rebuild, Test and Save a Source Code Change to U-Boot in PetaLinux Tools 2018.2 Using devtool

![xilinx_logo_1](xilinx_logo_1.png)

This post shows a way to rebuild, test and save a source code change in U-Boot using PetaLinux Tools 2018.2 using devtool;

**<u><span>Prerequisites</span></u>**

This write up assumes you've:

-   Installed PetaLinux Tools, Vivado, minicom,
    
-   Have done a complete build
    
-   Have programmed that build over JTAG and
    
-   Have viewed the output over minicom
    

See these for help:

<u><span>Install 64bit Ubuntu 16.04.3 on a VirtualBox 5.2.12 Managed Virtual Machine Running on Windows 7 SP1</span></u> at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/install-64bit-ubuntu-16-04-3-on-a-virtualbox-5-2-12-managed-virtual-machine-running-on-windows-7-sp1)\]

<u><span>ZCU102 Development Using 2018.2 on a Linux VM Running on Windows: Part 1</span></u> at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/zcu102-development-using-2018-2-on-a-linux-vm-running-on-windows)\]

<u><span>ZCU102 Development Using 2018.2 on a Linux VM Running on Windows: Part 2</span></u> at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/zcu102-development-using-2018-2-on-a-linux-vm-running-on-windows-part-2)\]

<u><span>Connecting Vivado to Digilent's USB-to-JTAG through VirtualBox</span></u> at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/connecting-vivado-to-digilent-s-usb-to-jtag-through-virtualbox)\]

<u><span>Arg! Nothing I type shows up in the Minicom console!</span></u> at \[[<u><span>link</span></u>](http://www.zachpfeffer.com/single-post/Arg-Nothing-I-type-shows-up-in-the-Minicom-console)\]

**<u><span>Pull in PetaLinux</span></u>**

Type from PLXPROJ directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/**

```
source /opt/pkg/petalinux/settings.sh
```

**<u><span>Pull in BitBake</span></u>**

Type from PLXPROJ directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/**

```
source /opt/pkg/petalinux/components/yocto/source/arm/environment-setup-cortexa9hf-neon-xilinx-linux-gnueabi
source /opt/pkg/petalinux/components/yocto/source/arm/layers/core/oe-init-build-env 
# this ^^^ puts you into PLXPROJ/build
# stay here to run BitBake commands
export PATH=/opt/pkg/petalinux/tools/hsm/bin:$PATH
export BB_ENV_EXTRAWHITE="$BB_ENV_EXTRAWHITE PETALINUX"
bitbake strace
```

**<u><span>Pull u-boot-xlnx into devtool</span></u>**

Type from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

```
devtool modify u-boot-xlnx
```

Note: this will checkout **u-boot** to **/opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx**

You should see:

```
NOTE: Starting bitbake server...
Loading cache: 100% |############################################| Time: 0:00:03
Loaded 3423 entries from dependency cache.
Parsing recipes: 100% |##########################################| Time: 0:00:14
Parsing of 2552 .bb files complete (2517 cached, 35 parsed). 3425 targets, 147 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
Initialising tasks: 100% |#######################################| Time: 0:00:19
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 3 tasks of which 0 didn't need to be rerun and all succeeded.
NOTE: Adding local source files to srctree...
NOTE: Source tree extracted to /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx
NOTE: Recipe u-boot-xlnx now set up to build from /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx
```

**<u><span>Make a Change</span></u>**

Edit board\_info.c:

```
vi /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/common/board_info.c
```

Make the change:

```
zpfeffer@z:/opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx$ git diff
diff --git a/common/board_info.c b/common/board_info.c
index aa45e24..ca49451 100644
--- a/common/board_info.c
+++ b/common/board_info.c
@@ -26,6 +26,7 @@ int __weak show_board_info(void)
        if (model)
                printf("Model: %s\n", model);
 #endif
+       printf("Hello, World!!\n");
 
        return checkboard();
 }
```

**<u><span>Build it</span></u>**

Type from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

```
bitbake u-boot-xlnx
```

You should see something like:

```
Loading cache: 100% |###################################################################| Time: 0:00:03
Loaded 3422 entries from dependency cache.
Parsing recipes: 100% |#################################################################| Time: 0:00:14
Parsing of 2552 .bb files complete (2516 cached, 36 parsed). 3425 targets, 147 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
Initialising tasks: 100% |##############################################################| Time: 0:00:20
Checking sstate mirror object availability: 100% |######################################| Time: 0:00:19
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: u-boot-xlnx: compiling from external source tree /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx
NOTE: Tasks Summary: Attempted 2379 tasks of which 2365 didn't need to be rerun and all succeeded.
```

Note: you may see different values of tasks and entries

**Check that board\_info.c was rebuilt**

Find the u-boot-xlnx log.do\_compile file

Type from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

```
find . -name "log.do_compile" | grep u-boot-xlnx
```

You'll see:

```
./tmp/work/zc706_zynq7-xilinx-linux-gnueabi/u-boot-xlnx/v2018.01-xilinx-v2018.2+git999-r0/temp/log.do_compile
```

**Grep for** **<u><span>board_info</span></u>**

cat ./tmp/work/zc706_zynq7-xilinx-linux-gnueabi/u-boot-xlnx/v2018.01-xilinx-v2018.2+git999-r0/temp/log.do_compile | grep board_info

You should see

arm-xilinx-linux-gnueabi-gcc --sysroot=/home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/u-boot-xlnx/v2018.01-xilinx-v2018.2+git999-r0/recipe-sysroot -Wp,-MD,common/.board_info.o.d -nostdinc -isystem /home/zpfeffer/plxprjs/xilinx-zc706-2018.2/build/tmp/work/zc706_zynq7-xilinx-linux-gnueabi/u-boot-xlnx/v2018.01-xilinx-v2018.2+git999-r0/recipe-sysroot-native/usr/bin/arm-xilinx-linux-gnueabi/../../lib/arm-xilinx-linux-gnueabi/gcc/arm-xilinx-linux-gnueabi/7.2.0/include -Iinclude -I/opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/include -I/opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/arch/arm/include -include /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/include/linux/kconfig.h -I/opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/common -Icommon -D__KERNEL__ -D__UBOOT__ -Wall -Wstrict-prototypes -Wno-format-security -fno-builtin -ffreestanding -fshort-wchar -Os -fno-stack-protector -fno-delete-null-pointer-checks -g -fstack-usage -Wno-format-nonliteral -Werror=date-time -D__ARM__ -marm -mno-thumb-interwork -mabi=aapcs-linux -mword-relocations -fno-pic -mno-unaligned-access -ffunction-sections -fdata-sections -fno-common -ffixed-r9 -msoft-float -pipe -march=armv7-a -D__LINUX_ARM_ARCH__=7 -I/opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/arch/arm/mach-zynq/include -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(board_info)" -D"KBUILD_MODNAME=KBUILD_STR(board_info)" -c -o common/board_info.o /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/common/board_info.c
from /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/common/board_info.c:5:
from /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/common/board_info.c:5:
from /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx/common/board_info.c:5:
arm-xilinx-linux-gnueabi-ld.bfd -r -o common/built-in.o common/init/built-in.o common/main.o common/exports.o common/hash.o common/cli_hush.o common/autoboot.o common/board_f.o common/board_r.o common/board_info.o common/bootm.o common/bootm_os.o common/fdt_support.o common/miiphyutil.o common/usb.o common/usb_hub.o common/usb_storage.o common/splash.o common/menu.o common/cli_readline.o common/cli_simple.o common/console.o common/dlmalloc.o common/malloc_simple.o common/image.o common/image-fdt.o common/image-fit.o common/image-sig.o common/memsize.o common/stdio.o common/cli.o common/dfu.o common/command.o common/s_record.o common/xyzModem.o

**<u><span>Test it</span></u>**

**Find the ELF file:**

Type from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

```
find . -type f -name "u-boot*.elf" -ls
```

Note: this excludes files that are links

You'll see something like:

zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build$ find . -type f -name "u-boot*.elf" -ls
1285090 4204 -rw-r--r-- 2 zpfeffer zpfeffer 4362712 Sep 22 15:40 ./tmp/deploy/images/zc706-zynq7/u-boot-zc706-zynq7-v2018.01-xilinx-v2018.2+git999-r0.elf
1285302 4264 -rw-r--r-- 2 zpfeffer zpfeffer 4362712 Sep 22 15:40 ./tmp/work/zc706_zynq7-xilinx-linux-gnueabi/u-boot-xlnx/v2018.01-xilinx-v2018.2+git999-r0/package/boot/u-boot-zc706-zynq7-v2018.01-xilinx-v2018.2+git999-r0.elf
1285527 4204 -rw-r--r-- 1 zpfeffer zpfeffer 4362712 Sep 22 15:40 ./tmp/work/zc706_zynq7-xilinx-linux-gnueabi/u-boot-xlnx/v2018.01-xilinx-v2018.2+git999-r0/image/boot/u-boot-zc706-zynq7-v2018.01-xilinx-v2018.2+git999-r0.elf
1285090 4204 -rw-r--r-- 2 zpfeffer zpfeffer 4362712 Sep 22 15:40 ./tmp/work/zc706_zynq7-xilinx-linux-gnueabi/u-boot-xlnx/v2018.01-xilinx-v2018.2+git999-r0/deploy-u-boot-xlnx/u-boot-zc706-zynq7-v2018.01-xilinx-v2018.2+git999-r0.elf
1285302 4264 -rw-r--r-- 2 zpfeffer zpfeffer 4362712 Sep 22 15:40 ./tmp/work/zc706_zynq7-xilinx-linux-gnueabi/u-boot-xlnx/v2018.01-xilinx-v2018.2+git999-r0/packages-split/u-boot-xlnx/boot/u-boot-zc706-zynq7-v2018.01-xilinx-v2018.2+git999-r0.elf

**Copy the ELF:**

Type from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

cp ./tmp/deploy/images/zc706-zynq7/u-boot-zc706-zynq7-v2018.01-xilinx-v2018.2+git999-r0.elf ../images/linux/u-boot.elf

**Start minicom:**

```
minicom -o -w -C minicom.log
```

**Boot:**

Type from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

```
petalinux-boot --jtag --u-boot -v
```

You should see

```
U-Boot 2018.01 (Sep 22 2018 - 09:40:10 -0600) Xilinx Zynq ZC706

Model: Zynq ZC706 Development Board
Hello, World!!!
Bo. 0 
igh Capacity: Yes
Capacity: 7.4 GiB
Bus Width: 4-bit
Erase Group Size: 512 Bytes
** Unable to read file image.ub **
Zynq> 
```

**<u><span>Save Your Changes</span></u>**

Type from **/opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx**

```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
git add common/board_info.c 
git commit -m "My changes"
```

Type from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

```
devtool update-recipe --mode patch --wildcard-version u-boot-xlnx
```

You'll see:

```
NOTE: Starting bitbake server...
Loading cache: 100% |##########################################################################################################| Time: 0:00:03
Loaded 3423 entries from dependency cache.
Parsing recipes: 100% |########################################################################################################| Time: 0:00:15
Parsing of 2552 .bb files complete (2516 cached, 36 parsed). 3425 targets, 147 skipped, 0 masked, 0 errors.
NOTE: There are 1 recipes to be removed from sysroot zc706-zynq7, removing...
NOTE: Adding new patch 0001-My-changes.patch
NOTE: Updating recipe u-boot-xlnx_2018.2.bb
```

The patch is at:

/opt/pkg/petalinux/components/yocto/source/arm/layers/meta-xilinx/meta-xilinx-bsp/recipes-bsp/u-boot/u-boot-xlnx/0001-My-changes.patch

**<u><span>Finish</span></u>**

Type this from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

```
devtool reset --no-clean u-boot-xlnx
```

**You should see**:

zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build$ devtool reset --no-clean u-boot-xlnx
NOTE: Starting bitbake server...
NOTE: Leaving source tree /opt/pkg/petalinux/components/yocto/source/arm/workspace/sources/u-boot-xlnx as-is; if you no longer need it then please delete it manually

**<u><span>Check</span></u>**

To make sure your patches got picked up...

Type these commands from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

**Build U-Boot:**

```
bitbake u-boot-xlnx
```

**Find the ELF file:**

```
find ../ -type f -name "u-boot*.elf" -ls
```

**Copy it to where PetaLinux Tools expects it to be:**

cp ../build/tmp/deploy/images/zc706-zynq7/u-boot-zc706-zynq7-v2018.01-xilinx-v2018.2+gitAUTOINC+21812b5fd3-r0.elf ../images/linux/u-boot.elf

**Boot it:**

```
petalinux-boot --jtag --u-boot -v
```

**<u><span>Edit Code Again</span></u>**

To edit code again with devtool and maintain your existing source tree:

Type from PLXPROJ/**build/** directory, i.e. **zpfeffer@z:~/plxprjs/xilinx-zc706-2018.2/build/**

```
devtool modify --no-extract u-boot-xlnx
```

...then follow the steps from **<u><span>Make a Change</span></u>** above.

**<u><span>References</span></u>**

-   <u><span>TipsAndTricks/Patching the source for a recipe</span></u> at \[[<u><span>link</span></u>](https://wiki.yoctoproject.org/wiki/TipsAndTricks/Patching_the_source_for_a_recipe)\]
    
-   <u><span>Using devtool in Your SDK Workflow</span></u> at \[[<u><span>link</span></u>](https://www.yoctoproject.org/docs/current/sdk-manual/sdk-manual.html#using-devtool-in-your-sdk-workflow)\]
    
-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]