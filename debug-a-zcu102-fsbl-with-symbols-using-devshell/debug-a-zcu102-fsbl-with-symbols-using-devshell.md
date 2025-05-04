# Debug a ZCU102 FSBL with Symbols using devshell

![xilinx_logo](xilinx_logo.png)

This post shows how to use devshell to debug the FSBL on a ZCU102 build. It also includes changes that enable source-level debug and shows how to save changes.

**<u><span>Assumptions</span></u>**

Assumes you have installed PetaLinux Tools and built xilinx-zcu102-2019.1

**<u><span>Note</span></u>**

These steps are meant for people who have worked a little with PetaLinux Tools and Yocto.

**<u><span>Steps</span></u>**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Run devshell

```
cd ~/plxprjs
source ~/petalinux/2019.1/settings.sh
cd xilinx-zcu102-2019.1
petalinux-build -c fsbl -x devshell # calls bitbake fsbl -c devshell
```

Note: you will be placed into:

```
~/plxprjs/xilinx-zcu102-2019.1/build/tmp/work/zcu102_zynqmp-xilinx-linux/fsbl/2019.1+gitAUTOINC+26c14d9861-r0/git
```

...you will run **make** here.

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Make these changes

```
diff --git a/lib/sw_apps/zynqmp_fsbl/misc/makefile b/lib/sw_apps/zynqmp_fsbl/misc/makefile                                                                        [35/1845]
index e8ad2a71e..f7568b173 100755
--- a/lib/sw_apps/zynqmp_fsbl/misc/makefile
+++ b/lib/sw_apps/zynqmp_fsbl/misc/makefile
@@ -9,7 +9,7 @@ endif
 ifeq "${PROC}" "r5"
 PROCESSOR = zynqmp_fsbl_bsp/psu_cortexr5_0
 endif
-LTO_FLAGS = -Wall -Wextra -Os -flto -ffat-lto-objects
+LTO_FLAGS = -g3 -Wall -Wextra -Og
 OTHER_FLAGS = -mfpu=vfpv3 -mfloat-abi=hard
 
 LIBRARIES = ${PROCESSOR}/lib/libxil.a
diff --git a/lib/sw_apps/zynqmp_fsbl/src/Makefile b/lib/sw_apps/zynqmp_fsbl/src/Makefile
index dea27a29d..16279fe49 100644
--- a/lib/sw_apps/zynqmp_fsbl/src/Makefile
+++ b/lib/sw_apps/zynqmp_fsbl/src/Makefile
@@ -73,7 +73,7 @@ CC      :=      $(CROSS)aarch64-none-elf-gcc
 AS      :=      $(CROSS)aarch64-none-elf-gcc
 LINKER  :=      $(CROSS)aarch64-none-elf-gcc
 DUMP    :=      $(CROSS)aarch64-none-elf-objdump -xSD
-ECFLAGS = -march=armv8-a -DARMA53_$(A53_STATE) -Os -flto -ffat-lto-objects
+ECFLAGS = -march=armv8-a -DARMA53_$(A53_STATE) -Og
 LSCRIPT :=     -Tlscript_a53.ld
 LDFLAGS := -Wl,--start-group,-lxil,-lxilffs,-lxilsecure,-lxilpm,-lgcc,-lc,--end-group -L$(LIBPATH) -L./ -Wl,--build-id=none
 else
@@ -81,7 +81,7 @@ CC      :=      $(CROSS)arm-none-eabi-gcc
 AS      :=      $(CROSS)arm-none-eabi-gcc
 LINKER  :=      $(CROSS)arm-none-eabi-gcc
 DUMP    :=      $(CROSS)arm-none-eabi-objdump -xSD
-ECFLAGS :=  -Wextra -march=armv7-a -mfloat-abi=hard -mfpu=vfpv3-d16 -DARMA53_$(A53_STATE) -Os -flto -ffat-lto-objects
+ECFLAGS :=  -Wextra -march=armv7-a -mfloat-abi=hard -mfpu=vfpv3-d16 -DARMA53_$(A53_STATE) -Og
 LSCRIPT :=     -Tlscript.ld
 LDFLAGS :=  -Wl,--start-group,-lxil,-lxilffs,-lxilsecure,-lxilpm,-lgcc,-lc,--end-group -L$(LIBPATH) -L./ -Wl,--build-id=none -march=armv7-a -mfloat-abi=hard -mfpu=vfpv3
 
diff --git a/lib/sw_apps/zynqmp_fsbl/src/xfsbl_config.h b/lib/sw_apps/zynqmp_fsbl/src/xfsbl_config.h
index ecf479511..9fe8b1226 100644
--- a/lib/sw_apps/zynqmp_fsbl/src/xfsbl_config.h
+++ b/lib/sw_apps/zynqmp_fsbl/src/xfsbl_config.h
@@ -131,20 +131,20 @@ extern "C" {
  *     - FSBL_FORCE_ENC_EXCLUDE_VAL Forcing encryption for every partition
  *       when ENC only bit is blown will be excluded.
  */
-#define FSBL_NAND_EXCLUDE_VAL                  (0U)
-#define FSBL_QSPI_EXCLUDE_VAL                  (0U)
-#define FSBL_SD_EXCLUDE_VAL                    (0U)
-#define FSBL_SECURE_EXCLUDE_VAL                        (0U)
-#define FSBL_BS_EXCLUDE_VAL                            (0U)
+#define FSBL_NAND_EXCLUDE_VAL                  (1U)
+#define FSBL_QSPI_EXCLUDE_VAL                  (1U)
+#define FSBL_SD_EXCLUDE_VAL                    (1U)
+#define FSBL_SECURE_EXCLUDE_VAL                        (1U)
+#define FSBL_BS_EXCLUDE_VAL                            (1U)
 #define FSBL_EARLY_HANDOFF_EXCLUDE_VAL (1U)
-#define FSBL_WDT_EXCLUDE_VAL                   (0U)
+#define FSBL_WDT_EXCLUDE_VAL                   (1U)
 #define FSBL_PERF_EXCLUDE_VAL                  (1U)
 #define FSBL_A53_TCM_ECC_EXCLUDE_VAL   (1U)
 #define FSBL_PL_CLEAR_EXCLUDE_VAL              (1U)
 #define FSBL_USB_EXCLUDE_VAL                   (1U)
 #define FSBL_PROT_BYPASS_EXCLUDE_VAL   (1U)
-#define FSBL_PARTITION_LOAD_EXCLUDE_VAL (0U)
-#define FSBL_FORCE_ENC_EXCLUDE_VAL             (0U)
+#define FSBL_PARTITION_LOAD_EXCLUDE_VAL (1U)
+#define FSBL_FORCE_ENC_EXCLUDE_VAL             (1U)
 #define FSBL_DDR_SR_EXCLUDE_VAL                        (1U)
 
 #if FSBL_NAND_EXCLUDE_VAL
```

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Make your changes and build them

```
make
```

Note: To save your changes you could:

```
git add xfsbl_main.c
git commit -m "Test commit"
git format-patch HEAD^
# You should see: 0001-Test-commit.patch
mkdir -p ~/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-bsp/fsbl/files
cp 0001-Test-commit.patch ~/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-bsp/fsbl/files
vi  ~/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-bsp/fsbl/fsbl_%.bbappend
# Add:
FILESEXTRAPATHS_prepend := "${THISDIR}/files:"
SRC_URI += "file://0001-Test-commit.patch"
```

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): Copy the fsbl.elf to image/linux for petalinux-boot

```
cp fsbl.elf ~/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf
```

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): Boot it

```
petalinux-boot --jtag --kernel
```

**<u><span>Reference</span></u>**

The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]