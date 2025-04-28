# Quickly Try devicetree and Root Filesystem Changes from a Xilinx PetaLinux Built image.ub

![Xilinx_logo](Xilinx_logo.png)

- This post shows how to get the Linux kernel, Flattened Device Tree blob, petalinux-user-image from an image.ub built by PetaLinux. Then it shows how to convert the Flattened Device Tree blob (DTB) into a DTS so that it can be edited and how to convert it back to a DTB. It then details how to extract the rootfilesystem and rebuild the rootfilesystem. It finishes by showing how to rebuild and use an image.ub with the updated components. This method is useful to try out quick changes to a device tree and a root filesystem. 

  **Setup**

  Ubuntu 16.04.5

  PetaLinux 2019.1 installed to **~/petalinux/2019.1/** using:

  **sudo apt-get update** **sudo apt-get -y install python3 dos2unix iproute2 gawk xvfb git make net-tools libncurses5-dev tftpd lib32z1 libssl-dev flex bison libselinux1 gnupg wget diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib build-essential libsdl1.2-dev libglib2.0-dev libsdl-dev build-essential gcc-multilib glib2.0 automake screen pax gzip libtool-bin zlib1g:i386** **mkdir -p $HOME/petalinux** **cd ~/Downloads** **./petalinux-v2019.1-final-installer.run $HOME/petalinux/2019.1**

  ZCU102 BSP was built using:

  \# Download the 2019.1 ZCU102 BSP from:

  https://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-zcu102-v2019.1-final.bsp to ~/Downloads

  \# Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): 

  **mkdir ~/plxbsps**

  **cd ~/plxbsps**

  **cp ~/Downloads/xilinx-zcu102-v2019.1-final.bsp .**

  **md5sum xilinx-zcu102-v2019.1-final.bsp**

  **# You should see:**

  **# 2189911c4ac9c33f170cdced96472ba7  xilinx-zcu102-v2019.1-final.bsp**

  **rm ~/Downloads/xilinx-zcu102-v2019.1-final.bsp**

  \# Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3):

  **mkdir ~/plxprjs**

  **cd ~/plxprjs/**

  **source ~/petalinux/2019.1/settings.sh**

  \# You should see:

  \# PetaLinux environment set to '/home/demo/petalinux/2019.1'

  \# INFO: Checking free disk space

  \# INFO: Checking installed tools

  \# INFO: Checking installed development libraries

  \# INFO: Checking network and other services

  \# WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution

  **petalinux-create -t project -s ~/plxbsps/xilinx-zcu102-v2019.1-final.bsp** **cd xilinx-zcu102-2019.1/**

  **petalinux-build**

  **Steps**

  \# Get the Tools: dtc, dumpimage, mkimage

  **sudo apt-get install u-boot-tools**

  \# Get the version of dtc

  **dtc -v**

  \# Example output:

  \# Version: DTC 1.4.0

  \# Get the Version of dumpimage with

  **dumpimage -V**

  \# Example output:

  \# dumpimage version 2016.01+dfsg1-2ubuntu5

  \# Get the Version of mkimage with:

  **mkimage -V**

  \# Example output:

  \# mkimage version 2016.01+dfsg1-2ubuntu5

  \# List Contents of the FIT Image (aka list the contents of images/linux/image.ub)

  **cd ~/plxprjs/xilinx-zcu102-2019.1/**

  **mkimage -l images/linux/image.ub** 

  \# Example output:

  FIT description: U-Boot fitImage for PetaLinux/4.19-xilinx-v2019.1+gitAUTOINC+9811303824/zcu102-zynqmp

  Created:         Tue Oct  5 10:29:19 2021

   Image 0 (kernel@1)

    Description:  Linux kernel

    Created:      Tue Oct  5 10:29:19 2021

    Type:         Kernel Image

    Compression:  uncompressed

    Data Size:    18149888 Bytes = 17724.50 kB = 17.31 MB

    Architecture: AArch64

    OS:           Linux

    Load Address: 0x00080000

    Entry Point:  0x00080000

    Hash algo:    sha1

    Hash value:   e4d410bcdce2a6869cb553b054d5fb31988a0cb1

   Image 1 (fdt@system-top.dtb)

    Description:  Flattened Device Tree blob

    Created:      Tue Oct  5 10:29:19 2021

    Type:         Flat Device Tree

    Compression:  uncompressed

    Data Size:    41288 Bytes = 40.32 kB = 0.04 MB

    Architecture: AArch64

    Hash algo:    sha1

    Hash value:   2062c3ae51659cc8ac7ab76bf3ae0dc311ca4b08

   Image 2 (ramdisk@1)

    Description:  petalinux-user-image

    Created:      Tue Oct  5 10:29:19 2021

    Type:         RAMDisk Image

    Compression:  gzip compressed

    Data Size:    6625387 Bytes = 6470.10 kB = 6.32 MB

    Architecture: AArch64

    OS:           Linux

    Load Address: unavailable

    Entry Point:  unavailable

    Hash algo:    sha1

    Hash value:   74c7a71f25ef5f2ed8e74d0ccdc93e31306fb567

   Default Configuration: 'conf@system-top.dtb'

   Configuration 0 (conf@system-top.dtb)

    Description:  1 Linux kernel, FDT blob, ramdisk

    Kernel:       kernel@1

    Init Ramdisk: ramdisk@1

    FDT:          fdt@system-top.dtb

  \# Split Out the dtb from a FIT Image (aka extract the dtb from an image.ub)

  **cd ~/plxprjs/xilinx-zcu102-2019.1/**

  **dumpimage -i images/linux/image.ub -T flat_dt -p 1 mysystems.dtb**

  \# Example output:

  Extracted:

   Image 1 (fdt@system-top.dtb)

    Description:  Flattened Device Tree blob

    Created:      Tue Oct  5 10:29:19 2021

    Type:         Flat Device Tree

    Compression:  uncompressed

    Data Size:    41288 Bytes = 40.32 kB = 0.04 MB

    Architecture: AArch64

    Hash algo:    sha1

    Hash value:   2062c3ae51659cc8ac7ab76bf3ae0dc311ca4b08

  \# Convert a DTB to a DTS (aka see what's in the DTB we're going boot)

  **dtc -I dtb -O dts mysystems.dtb > mysystems.dts**

  **# Make the changes to mysystems.dts you want to try** 

  **# ...like disable power management:**

  **vi mysystems.dts**

  bootargs = "earlycon console=ttyPS0,115200 clk_ignore_unused cpuidle.off=1";

  \# Convert a DTS to a DTB (aka get a DTB ready for a FIT image, aka put a new DTB in an image.ub)

  **dtc -I dts -O dtb mysystems.dts > new-mysystem.dtb**

  \#..and back (to check):

  **dtc -I dtb -O dts new-mysystem.dtb > new-mysystem.dts**	

  \# Split Out the kernel from a FIT Image (aka extract the kernel from an image.ub)

  **dumpimage -i images/linux/image.ub -T flat_dt -p 0 myImage**

  \# Example output:

  Extracted:

   Image 0 (kernel@1)

    Description:  Linux kernel

    Created:      Tue Oct  5 10:29:19 2021

    Type:         Kernel Image

    Compression:  uncompressed

    Data Size:    18149888 Bytes = 17724.50 kB = 17.31 MB

    Architecture: AArch64

    OS:           Linux

    Load Address: 0x00080000

    Entry Point:  0x00080000

    Hash algo:    sha1

    Hash value:   e4d410bcdce2a6869cb553b054d5fb31988a0cb1

  \# Split Out the rootfs from a FIT Image (aka get the rootfs from an image.ub)

  **dumpimage -i images/linux/image.ub -T flat_dt -p 2 myrootfs.cpio.gz**

  \# Example output

  Extracted:

   Image 2 (ramdisk@1)

    Description:  petalinux-user-image

    Created:      Tue Oct  5 10:29:19 2021

    Type:         RAMDisk Image

    Compression:  gzip compressed

    Data Size:    6625387 Bytes = 6470.10 kB = 6.32 MB

    Architecture: AArch64

    OS:           Linux

    Load Address: unavailable

    Entry Point:  unavailable

    Hash algo:    sha1

    Hash value:   74c7a71f25ef5f2ed8e74d0ccdc93e31306fb567

  \# Expand, Get The Biggest Items, Make an Update, and Repack a rootfs (aka extract a rootfs.cpio.gz )

  **mkdir debugrootfs**

  **pushd debugrootfs**

  **gzip -cd ../myrootfs.cpio.gz | cpio -imd --quiet**

  **du -a . | sort -n -r | head -n 20**

  **touch test.txt**

  **find . | cpio -H newc -o -R root:root > ../newmyrootfs.cpio**

  **popd**

  **cat newmyrootfs.cpio | gzip > newmyrootfs.cpio.gz**

  \# Example output

  demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1/debugrootfs$ gzip -cd ../myrootfs.cpio.gz | cpio -imd --quiet

  demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1/debugrootfs$ du -a . | sort -n -r | head -n 20

  18308	.

  7548	./usr

  5972	./lib

  3056	./usr/sbin

  2072	./usr/share

  2000	./bin

  1920	./sbin

  1756	./usr/share/licenses

  1692	./lib/modules

  1688	./lib/modules/4.19.0-xilinx-v2019.1

  1584	./lib/modules/4.19.0-xilinx-v2019.1/kernel

  1380	./lib/libc-2.28.so

  1300	./usr/lib

  1124	./bin/bash.bash

  1008	./lib/modules/4.19.0-xilinx-v2019.1/kernel/drivers

  996	./usr/bin

  892	./usr/lib/opkg

  888	./usr/lib/opkg/alternatives

  876	./usr/sbin/tcf-agent

  772	./etc

  demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1/debugrootfs$ touch test.txt

  demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1/debugrootfs$ find . | cpio -H newc -o -R root:root > ../newmyrootfs.cpio

  31340 blocks

  demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1/debugrootfs$ popd

  ~/plxprjs/xilinx-zcu102-2019.1

  demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1$ cat newmyrootfs.cpio | gzip > newmyrootfs.cpio.gz

  \# Create an image.ub (aka repack a FIT image)

  \# Note: uses the new files created above: 

  \# myImage, new-mysystem.dtb, newmyrootfs.cpio.gz

  \# Note: select everything from the "c" in cat to the "S" in IMAGEITS

  \# Note2: you can also create image.its with the contents starting with /dts-v1/; and ending with the }; before IMAGEITS

  **cat << "IMAGEITS" > image.its**

  **/dts-v1/;**

    

  **/ {**

  ​    **description = "U-Boot fitImage for plnx_aarch64 kernel";**

  ​    **[#address](https://www.centennialsoftwaresolutions.com/blog/hashtags/address)-cells = <1>;**

    

  ​    **images {**

  ​        **kernel@0 {**

  ​            **description = "Linux Kernel";**

  ​            **data = /incbin/("./myImage");**

  ​            **type = "kernel";**

  ​            **arch = "arm64";**

  ​            **os = "linux";**

  ​            **compression = "none";**

  ​            **load = <0x80000>;**

  ​            **entry = <0x80000>;**

  ​            **hash@1 {**

  ​                **algo = "sha1";**

  ​            **};**

  ​        **};**

  ​        **fdt@0 {**

  ​            **description = "Flattened Device Tree blob";**

  ​            **data = /incbin/("./new-mysystem.dtb");**

  ​            **type = "flat_dt";**

  ​            **arch = "arm64";**

  ​            **compression = "none";**

  ​            **hash@1 {**

  ​                **algo = "sha1";**

  ​            **};**

  ​        **};**

  ​        **ramdisk@0 {**

  ​            **description = "ramdisk";**

  ​            **data = /incbin/("./newmyrootfs.cpio.gz");**

  ​            **type = "ramdisk";**

  ​            **arch = "arm64";**

  ​            **os = "linux";**

  ​            **compression = "gzip";**

  ​            **hash@1 {**

  ​                **algo = "sha1";**

  ​            **};**

  ​        **};**

  ​    **};**

  ​    **configurations {**

  ​        **default = "conf@1";**

  ​        **conf@1 {**

  ​            **description = "Boot Linux kernel with FDT blob + ramdisk";**

  ​            **kernel = "kernel@0";**

  ​            **fdt = "fdt@0";**

  ​            **ramdisk = "ramdisk@0";**

  ​            **hash@1 {**

  ​                **algo = "sha1";**

  ​            **};**

  ​        **};**

  ​    **};**

  **};**

  **IMAGEITS**

  **mkimage -f image.its image.itb**

  \# Example output:

  FIT description: U-Boot fitImage for plnx_aarch64 kernel

  Created:         Sun Oct 10 11:15:23 2021

   Image 0 (kernel@0)

    Description:  Linux Kernel

    Created:      Sun Oct 10 11:15:23 2021

    Type:         Kernel Image

    Compression:  uncompressed

    Data Size:    18149888 Bytes = 17724.50 kB = 17.31 MB

    Architecture: AArch64

    OS:           Linux

    Load Address: 0x00080000

    Entry Point:  0x00080000

    Hash algo:    sha1

    Hash value:   e4d410bcdce2a6869cb553b054d5fb31988a0cb1

   Image 1 (fdt@0)

    Description:  Flattened Device Tree blob

    Created:      Sun Oct 10 11:15:23 2021

    Type:         Flat Device Tree

    Compression:  uncompressed

    Data Size:    37064 Bytes = 36.20 kB = 0.04 MB

    Architecture: AArch64

    Hash algo:    sha1

    Hash value:   6acc0c305ed9b3c820ed981ed421e617d86f5d7b

   Image 2 (ramdisk@0)

    Description:  ramdisk

    Created:      Sun Oct 10 11:15:23 2021

    Type:         RAMDisk Image

    Compression:  gzip compressed

    Data Size:    6653833 Bytes = 6497.88 kB = 6.35 MB

    Architecture: AArch64

    OS:           Linux

    Load Address: unavailable

    Entry Point:  unavailable

    Hash algo:    sha1

    Hash value:   f59fd56ab1974d2e684131e86b447b0ec46f01fe

   Default Configuration: 'conf@1'

   Configuration 0 (conf@1)

    Description:  Boot Linux kernel with FDT blob + ramdisk

    Kernel:       kernel@0

    Init Ramdisk: ramdisk@0

    FDT:          fdt@0

  **Test**

  \# Switch the ZCU102 to PS JTAG mode

  \# See all the modes here:

  https://www.centennialsoftwaresolutions.com/post/pictures-of-sw6-for-every-zcu102-zynq-ultrascale-mpsoc-boot-mode 

  \# Turn on the ZCU102

  \# In one terminal

  screen /dev/ttyUSB0 115200

  \# Use Ctrl-a x to scroll

  \# In another terminal

  **cd ~/plxprjs/xilinx-zcu102-2019.1**

  **source ~/petalinux/2019.1/settings.sh**

  **petalinux-boot --jtag --u-boot -v**

  \# Stop U-Boot at: "Hit any key to stop autoboot:  " ...in the other terminal

  \# In a third terminal

  **~/petalinux/2019.1/tools/xsct/bin/xsct**

  \# In xsct

  **connect**

  **# You should see: tcfchan#0**

  **targets**

  targets -set -nocase -filter {name =~ "*A53*#0"} ;# or targets 10

  **dow -data ~/plxprjs/xilinx-zcu102-2019.1/image.itb 0x20000000**

  **disco**

  \# You should see:

  \# 100%   23MB   0.3MB/s  01:11                                                                                                                      

  \#  Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/image.itb

  \# In the U-Boot terminal 

  **bootm 0x20000000**

  \# After boot:

  **ls /**

  \# You'll see test.txt

  \# Example output from boot:

  INIT: version 2.88 booting

  PMU Firmware 2019.1     Sep  5 2021   21:05:51

  PMU_ROM Version: xpbr-v7.2.0-1

  Xilinx Zynq MP First Stage Boot Loader

  Release 2019.1   Sep  5 2021  -  21:05:09

  NOTICE:  ATF running on XCZU9EG/silicon v3/RTL5.1 at 0xfffea000

  NOTICE:  BL31: Secure code at 0x60000000

  NOTICE:  BL31: Non secure code at 0x10080000

  NOTICE:  BL31: v2.0(release):xilinx-v2018.3-720-g80d1c790

  NOTICE:  BL31: Built : 16:26:05, Oct  5 2021

  PMUFW:  v1.1

  U-Boot 2019.01 (Oct 05 2021 - 16:26:46 +0000)

  Model: ZynqMP ZCU102 Rev1.0

  Board: Xilinx ZynqMP

  DRAM:  4 GiB

  EL Level:       EL2

  Chip ID:        zu9eg

  MMC:   mmc@ff170000: 0

  Loading Environment from SPI Flash... SF: Detected n25q512a with page size 512 Bytes, erase size 128 KiB, total 128 MiB

  *** Warning - bad CRC, using default environment

  In:    serial@ff000000

  Out:   serial@ff000000

  Err:   serial@ff000000

  Model: ZynqMP ZCU102 Rev1.0

  Board: Xilinx ZynqMP

  Bootmode: JTAG_MODE

  Reset reason:   EXTERNAL

  Net:   ZYNQ GEM: ff0e0000, phyaddr c, interface rgmii-id

  Warning: ethernet@ff0e0000 MAC addresses don't match:

  Address in ROM is          ff:ff:ff:ff:ff:ff

  Address in environment is  00:0a:35:00:22:01

  eth0: ethernet@ff0e0000

  U-BOOT for xilinx-zcu102-2019_1

  ethernet@ff0e0000 Waiting for PHY auto negotiation to complete......................................... TIMEOUT !

  Hit any key to stop autoboot:  0

  \# Example output from **petalinux-boot --jtag --u-boot -v**

  INFO: sourcing build tools

  XSDB Script:

  INFO: Launching XSDB for file download and boot.

  INFO: This may take a few minutes, depending on the size of your image.

  connect

  targets -set -nocase -filter {name =~ "*PSU*"}

  mask_write 0xFFCA0038 0x1C0 0x1C0

  targets -set -nocase -filter {name =~ "*MicroBlaze PMU*"}

  puts stderr "INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/pmufw.elf to the target."

  dow "/home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/pmufw.elf"

  after 2000

  con

  targets -set -nocase -filter {name =~ "*APU*"}

  mwr 0xffff0000 0x14000000

  mask_write 0xFD1A0104 0x501 0x0

  targets -set -nocase -filter {name =~ "*A53*#0"}

  source /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/hw-description/psu_init.tcl

  puts stderr "INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf to the target."

  dow "/home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf"

  after 2000

  con

  after 4000; stop; catch {stop}; psu_ps_pl_isolation_removal; psu_ps_pl_reset_config

  targets -set -nocase -filter {name =~ "*A53*#0"}

  puts stderr "INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf to the target."

  dow "/home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf"

  after 2000

  targets -set -nocase -filter {name =~ "*A53*#0"}

  puts stderr "INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf to the target."

  dow "/home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf"

  after 2000

  con

  exit

  rlwrap: warning: your $TERM is 'xterm-256color' but rlwrap couldn't find it in the terminfo database. Expect some problems.: Inappropriate ioctl for device

  INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/pmufw.elf to the target.     

  Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/pmufw.elf

  ​	section, .vectors.reset: 0xffdc0000 - 0xffdc0007

  ​	section, .vectors.sw_exception: 0xffdc0008 - 0xffdc000f

  ​	section, .vectors.interrupt: 0xffdc0010 - 0xffdc0017

  ​	section, .vectors.hw_exception: 0xffdc0020 - 0xffdc0027

  ​	section, .text: 0xffdc0050 - 0xffdd0dc7

  ​	section, .rodata: 0xffdd0dc8 - 0xffdd2edf

  ​	section, .data: 0xffdd2ee0 - 0xffdd71d7

  ​	section, .sdata2: 0xffdd71d8 - 0xffdd71d7

  ​	section, .sdata: 0xffdd71d8 - 0xffdd71d7

  ​	section, .sbss: 0xffdd71d8 - 0xffdd71d7

  ​	section, .bss: 0xffdd71e0 - 0xffddb20b

  ​	section, .srdata: 0xffddb20c - 0xffddbb2f

  ​	section, .stack: 0xffddbb30 - 0xffddcb2f

  ​	section, .xpbr_serv_ext_tbl: 0xffddf6e0 - 0xffddfadf

  100%    0MB   0.2MB/s  00:00    

  Setting PC to Program Start Address 0xffdcffe0

  Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/pmufw.elf

  INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf to the target.

  Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf

  ​	section, .text: 0xfffc0000 - 0xfffd410b

  ​	section, .init: 0xfffd4140 - 0xfffd4173

  ​	section, .fini: 0xfffd4180 - 0xfffd41b3

  ​	section, .note.gnu.build-id: 0xfffd41b4 - 0xfffd41d7

  ​	section, .rodata: 0xfffd4200 - 0xfffd474f

  ​	section, .sys_cfg_data: 0xfffd4780 - 0xfffd4f67

  ​	section, .mmu_tbl0: 0xfffd5000 - 0xfffd500f

  ​	section, .mmu_tbl1: 0xfffd6000 - 0xfffd7fff

  ​	section, .mmu_tbl2: 0xfffd8000 - 0xfffdbfff

  ​	section, .data: 0xfffdc000 - 0xfffdd3b7

  ​	section, .sbss: 0xfffdd3b8 - 0xfffdd3bf

  ​	section, .bss: 0xfffdd3c0 - 0xfffdf5bf

  ​	section, .heap: 0xfffdf5c0 - 0xfffdf9bf

  ​	section, .stack: 0xfffdf9c0 - 0xfffe19bf

  ​	section, .dup_data: 0xfffe19c0 - 0xfffe2d77

  ​	section, .handoff_params: 0xfffe9e00 - 0xfffe9e87

  ​	section, .bitstream_buffer: 0xffff0040 - 0xfffffc3f

  100%    0MB   0.2MB/s  00:00    

  Setting PC to Program Start Address 0xfffc0000

  Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf

  INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf to the target.

  Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf

  ​	section, .data: 0x10080000 - 0x1014c51f

  100%    0MB   0.2MB/s  00:04    

  Setting PC to Program Start Address 0x10080000

  Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf

  INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf to the target.

  Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf

  ​	section, .text: 0xfffea000 - 0xffff1fff

  ​	section, .rodata: 0xffff2000 - 0xffff2fff

  ​	section, .data: 0xffff3000 - 0xffff6777

  ​	section, stacks: 0xffff6780 - 0xffff787f

  ​	section, .bss: 0xffff7880 - 0xffff8613

  ​	section, xlat_table: 0xffff9000 - 0xffffdfff

  ​	section, coherent_ram: 0xffffe000 - 0xffffefff

  100%    0MB   0.1MB/s  00:00    

  Setting PC to Program Start Address 0xfffea000

  Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf

  **References**

  - https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/18842374/U-Boot+Images 
  - The Xilinx graphic is from [[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)]