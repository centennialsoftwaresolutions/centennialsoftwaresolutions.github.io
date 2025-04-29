# Boot the 2020.1 FSBL in QEMU

![Xilinx_logo](Xilinx_logo.png)

This write-up shows how to boot the 2020.1 FSBL in QEMU. It also shows how to recompile the FSBL from PetaLinux 2020.1.

**<u><span>Install PetaLinux 2020.1</span></u>**

```
# Download petalinux-v2020.1-final-installer.run to ~/Downloads
# Download xilinx-zcu102-v2020.1-final.bsp to ~/Downloads
mkdir -p ~/plxbsps
mkdir -p ~/plxprjs
mkdir -p ~/petalinux
cd ~/Downloads
./petalinux-v2020.1-final-installer.run -d $HOME/petalinux/2020.1 # Takes a bit
```

**<u><span>Create, Build the ZCU102 BSP, and Boot U-Boot</span></u>**

```
mkdir -p ~/plxprjs
cd ~/plxprjs
source ~/petalinux/2020.1/settings.sh
petalinux-create -t project -s ~/Downloads/xilinx-zcu102-v2020.1-final.bsp
cd xilinx-zcu102-2020.1
petalinux-build
# test QEMU
petalinux-boot --qemu --u-boot
... you'll see it pause at (qemu)...then boot U-Boot
# Ctrl-a x to quit
```

**<u><span>Make the Change Needed for the FSBL to Boot in QEMU</span></u>**

...as listed in \[

https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/862421130/Known+Issues#KnownIssues-Firststagebootloader(FSBL)hangsonQEMUFSBLHang] 

\# Get the source and launch the environment

```
petalinux-build -c fsbl -x compile
petalinux-build -c fsbl -x devshell
# A dev shell should launch placing the user in
# root@ubuntu:~/plxprjs/xilinx-zcu102-2020.1/build/tmp/work/zcu102_zynqmp-xilinx-linux/fsbl/2020.1+gitAUTOINC+6cbb920f4d-r0/git#

find ~/plxprjs/xilinx-zcu102-2020.1/build/tmp/work/zcu102_zynqmp-xilinx-linux/fsbl/ -name "xfsbl_initialization.c"
```

\# you'll see 3, choose the one listed here:

```
grep -REns "XFsbl_DdrInit" ~/plxprjs/xilinx-zcu102-2020.1/build/tmp/work/zcu102_zynqmp-xilinx-linux/fsbl/2020.1+gitAUTOINC+6cbb920f4d-r0/build/fsbl/xfsbl_initialization.c
```

\# You should see: \# 753: Status = XFsbl\_DdrInit();

\# Edit

```
vi +753 ~/plxprjs/xilinx-zcu102-2020.1/build/tmp/work/zcu102_zynqmp-xilinx-linux/fsbl/2020.1+gitAUTOINC+6cbb920f4d-r0/build/fsbl/xfsbl_initialization.c
```

\# Comment out:

#

\# // Status = XFsbl\_DdrInit();

\# // if (XFSBL\_SUCCESS != Status) {

\# // XFsbl\_Printf(DEBUG\_GENERAL,"XFSBL\_DDR\_INIT\_FAILED\\n\\r");

\# // goto END;

\# // }

\# Run:

```
~/plxprjs/xilinx-zcu102-2020.1/build/tmp/work/zcu102_zynqmp-xilinx-linux/fsbl/2020.1+gitAUTOINC+6cbb920f4d-r0/temp/run.do_compile
```

\# Note, the exe will be at:

```
ls -l ~/plxprjs/xilinx-zcu102-2020.1/build/tmp/work/zcu102_zynqmp-xilinx-linux/fsbl/2020.1+gitAUTOINC+6cbb920f4d-r0/build/fsbl/executable.elf
```

**<u><span>Test It</span></u>**

\# Open a new terminal (terminal 2)

\# Run once

```
cd ~/plxprjs/xilinx-zcu102-2020.1
 source ~/petalinux/2020.1/settings.sh
PATH=/home/demo/petalinux/2020.1/components/yocto/buildtools/sysroots/x86_64-petalinux-linux/usr/bin/:$PATH
```

\# Then run:

```
rm -rf /tmp/tmp.test
mkdir /tmp/tmp.test 
# Args broken out 
qemu-system-microblazeel \
-M microblaze-fdt \
-display none \
-kernel ./pre-built/linux/images/pmu_rom_qemu_sha3.elf \
-device loader,file=./images/linux/pmufw.elf \
-hw-dtb ./images/linux/zynqmp-qemu-multiarch-pmu.dtb \
-machine-path /tmp/tmp.test \
-device loader,addr=0xfd1a0074,data=0x1011003,data-len=4 \
-device loader,addr=0xfd1a007C,data=0x1010f03,data-len=4
```

\# Open another new terminal (terminal 3)

\# Run once

```
cd ~/plxprjs/xilinx-zcu102-2020.1
 source ~/petalinux/2020.1/settings.sh
PATH=/home/demo/petalinux/2020.1/components/yocto/buildtools/sysroots/x86_64-petalinux-linux/usr/bin/:$PATH
```

\# Then run:

```
qemu-system-aarch64 \
-M arm-generic-fdt \
-m 4G \
-nographic \
-monitor none \
 -hw-dtb ./images/linux/zynqmp-qemu-multiarch-arm.dtb \
-device loader,file=./build/tmp/work/zcu102_zynqmp-xilinx-linux/fsbl/2020.1+gitAUTOINC+6cbb920f4d-r0/build/fsbl/executable.elf,cpu-num=0 \
 -device loader,addr=0xfd1a0104,data=0x8000000e,data-len=4 \
 -machine-path /tmp/tmp.test \
 -global xlnx,zynqmp-boot.cpu-num=0 \
 -global xlnx,zynqmp-boot.use-pmufw=true \
 -serial mon:stdio
```

You should see:

```
PMU Firmware 2020.1	Aug  8 2021   06:05:27
PMU_ROM Version: xpbr-v8.1.0-0
Xilinx Zynq MP First Stage Boot Loader 
Release 2020.1   Aug  8 2021  -  06:16:42
```

Type Ctrl-a x to quit in the 3rd open terminal to quit.

You can launch QEMU again by running the command sequence after the "run once" command in terminal 2 and the command sequence after the "run once" command in terminal 3.

**<u><span>References</span></u>**

-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]