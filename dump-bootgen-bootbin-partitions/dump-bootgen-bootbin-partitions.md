# Dump the partitions from a BOOT.bin built with bootgen

![xilinx_logo](xilinx_logo.png)

This posts shows how to figure out the names and sizes of the partitions of BOOT.bin from bootgen.

Example bootimage.bif:

```
pfefferz@plc2:~/build$ cat out/bootimage.bif 
image : {
        [bootloader,destination_cpu=a53-0]/home/pfefferz/build/out/zynqmp_fsbl.elf
        [pmufw_image]/home/pfefferz/build/out/pmufw.elf
        [destination_cpu=a53-0, exception_level=el-3, trustzone] /home/pfefferz/build/out/bl31.elf
        [destination_cpu=a53-0, exception_level=el-2] /home/pfefferz/build/out/u-boot.elf
        [load=0x03000000]/home/pfefferz/build/out/uImage.bin
        [load=0x1407f000]/home/pfefferz/build/out/system.dtb
        [load=0x01000000]/home/pfefferz/build/out/uramdisk.image.gz
}
```

Get all the partitions by passing **\-log trace** to bootgen:

```
$PATH_TO_XSCT/bootgen -log trace -arch zynqmp -image $PETALINUX_BUILD_OUT/bootimage.bif -w -o $PETALINUX_BUILD_OUT/BOOT.bin
```

```
~/build/out ~/build
/hdd/opt/Xilinx/SDK/2017.4/bin//bootgen -log trace -arch zynqmp -image /home/pfefferz/build/out/bootimage.bif -w -o /home/pfefferz/build/out/BOOT.bin
[TRACE]  : Command Line parsing started
[TRACE]  : Command: -log trace -arch zynqmp -image /home/pfefferz/build/out/bootimage.bif -w -o /home/pfefferz/build/out/BOOT.bin
[INFO]   : Command line parsing completed successfully
[INFO]   : Bootgen Version - 2017.4, Nov 23, 2017
[TRACE]  : BIF File: /home/pfefferz/build/out/bootimage.bif
[TRACE]  : BIF file parsing started
[TRACE]  : Creating ZYNQ MP Factory
[INFO]   : Filename: /home/pfefferz/build/out/zynqmp_fsbl.elf
[INFO]   : Parsing Partition Data
[INFO]   : Filename: /home/pfefferz/build/out/pmufw.elf
[INFO]   : Filename: /home/pfefferz/build/out/bl31.elf
[INFO]   : Parsing Partition Data
[INFO]   : Filename: /home/pfefferz/build/out/u-boot.elf
[INFO]   : Parsing Partition Data
[INFO]   : Filename: /home/pfefferz/build/out/uImage.bin
[INFO]   :  Load: 3000000
[INFO]   : Parsing Partition Data
[INFO]   : Filename: /home/pfefferz/build/out/system.dtb
[INFO]   :  Load: 1407f000
[INFO]   : Parsing Partition Data
[INFO]   : Filename: /home/pfefferz/build/out/uramdisk.image.gz
[INFO]   :  Load: 1000000
[INFO]   : Parsing Partition Data
[INFO]   : BIF file parsing completed successfully
[INFO]   : Building image - image
[TRACE]  : Setting Core as 2
[INFO]   : Building the Partition Header Table
[TRACE]  : Creating ZYNQ MP Factory
[INFO]   : After build 
           -- Dump of Binary Image ----
           00000000 Len: 000008b8 Res: 00000000 "BootHeader"
           00000000 Len: 00000040 Res: 00000000 "ImageHeaderTable"
           00000000 Len: 00000024 Res: 00000000 "ImageHeader zynqmp_fsbl.elf"
           00000000 Len: 00000020 Res: 00000000 "ImageHeader bl31.elf"
           00000000 Len: 00000020 Res: 00000000 "ImageHeader u-boot.elf"
           00000000 Len: 00000020 Res: 00000000 "ImageHeader uImage.bin"
           00000000 Len: 00000020 Res: 00000000 "ImageHeader system.dtb"
           00000000 Len: 00000028 Res: 000006c0 "ImageHeader uramdisk.image.gz"
           00000000 Len: 00000040 Res: 00000000 "PartitionHeader zynqmp_fsbl.elf.0"
           00000000 Len: 00000040 Res: 00000000 "PartitionHeader bl31.elf.0"
           00000000 Len: 00000040 Res: 00000000 "PartitionHeader bl31.elf.1"
           00000000 Len: 00000040 Res: 00000000 "PartitionHeader u-boot.elf.0"
           00000000 Len: 00000040 Res: 00000000 "PartitionHeader uImage.bin.0"
           00000000 Len: 00000040 Res: 00000000 "PartitionHeader system.dtb.0"
           00000000 Len: 00000040 Res: 00000000 "PartitionHeader uramdisk.image.gz.0"
           00000000 Len: 00000040 Res: 00001540 "PartitionHeader Null"
           00000000 Len: 00036de8 Res: 00000000 "zynqmp_fsbl.elf.0"
           00000000 Len: 00006000 Res: 00000000 "bl31.elf.0"
           00000000 Len: 00000020 Res: 00000000 "bl31.elf.1"
           00000000 Len: 00093e70 Res: 00000000 "u-boot.elf.0"
           00000000 Len: 00cc2a40 Res: 00000000 "uImage.bin.0"
           00000000 Len: 00008764 Res: 00000000 "system.dtb.0"
           00000000 Len: 0079bbcc Res: 00000000 "uramdisk.image.gz.0"
           -- End of Dump
[INFO]   : After align 
           -- Dump of Binary Image ----
           00000000 Len: 000008b8 Res: 00000000 "BootHeader"
           000008c0 Len: 00000040 Res: 00000000 "ImageHeaderTable"
           00000900 Len: 00000024 Res: 00000000 "ImageHeader zynqmp_fsbl.elf"
           00000940 Len: 00000020 Res: 00000000 "ImageHeader bl31.elf"
           00000980 Len: 00000020 Res: 00000000 "ImageHeader u-boot.elf"
           000009c0 Len: 00000020 Res: 00000000 "ImageHeader uImage.bin"
           00000a00 Len: 00000020 Res: 00000000 "ImageHeader system.dtb"
           00000a40 Len: 00000028 Res: 000006c0 "ImageHeader uramdisk.image.gz"
           00001100 Len: 00000040 Res: 00000000 "PartitionHeader zynqmp_fsbl.elf.0"
           00001140 Len: 00000040 Res: 00000000 "PartitionHeader bl31.elf.0"
           00001180 Len: 00000040 Res: 00000000 "PartitionHeader bl31.elf.1"
           000011c0 Len: 00000040 Res: 00000000 "PartitionHeader u-boot.elf.0"
           00001200 Len: 00000040 Res: 00000000 "PartitionHeader uImage.bin.0"
           00001240 Len: 00000040 Res: 00000000 "PartitionHeader system.dtb.0"
           00001280 Len: 00000040 Res: 00000000 "PartitionHeader uramdisk.image.gz.0"
           000012c0 Len: 00000040 Res: 00001540 "PartitionHeader Null"
           00002800 Len: 00036de8 Res: 00000000 "zynqmp_fsbl.elf.0"
           00039600 Len: 00006000 Res: 00000000 "bl31.elf.0"
           0003f600 Len: 00000020 Res: 00000000 "bl31.elf.1"
           0003f640 Len: 00093e70 Res: 00000000 "u-boot.elf.0"
           000d34c0 Len: 00cc2a40 Res: 00000000 "uImage.bin.0"
           00d95f00 Len: 00008764 Res: 00000000 "system.dtb.0"
           00d9e680 Len: 0079bbcc Res: 00000000 "uramdisk.image.gz.0"
           -- End of Dump
[INFO]   : Partition Information: 
[INFO]   : Image: zynqmp_fsbl.elf
[INFO]   :      1. Partition: zynqmp_fsbl.elf.0,  Size: 224744
[INFO]   : Image: bl31.elf
[INFO]   :      2. Partition: bl31.elf.0,  Size: 24576
[INFO]   :      3. Partition: bl31.elf.1,  Size: 32
[INFO]   : Image: u-boot.elf
[INFO]   :      4. Partition: u-boot.elf.0,  Size: 605808
[INFO]   : Image: uImage.bin
[INFO]   :      5. Partition: uImage.bin.0,  Size: 13380160
[INFO]   : Image: system.dtb
[INFO]   :      6. Partition: system.dtb.0,  Size: 34659
[INFO]   : Image: uramdisk.image.gz
[INFO]   :      7. Partition: uramdisk.image.gz.0,  Size: 7977929
[INFO]   : After Link 
           -- Dump of Binary Image ----
           00000000 Len: 000008b8 Res: 00000000 "BootHeader"
           000008c0 Len: 00000040 Res: 00000000 "ImageHeaderTable"
           00000900 Len: 00000024 Res: 00000000 "ImageHeader zynqmp_fsbl.elf"
           00000940 Len: 00000020 Res: 00000000 "ImageHeader bl31.elf"
           00000980 Len: 00000020 Res: 00000000 "ImageHeader u-boot.elf"
           000009c0 Len: 00000020 Res: 00000000 "ImageHeader uImage.bin"
           00000a00 Len: 00000020 Res: 00000000 "ImageHeader system.dtb"
           00000a40 Len: 00000028 Res: 000006c0 "ImageHeader uramdisk.image.gz"
           00001100 Len: 00000040 Res: 00000000 "PartitionHeader zynqmp_fsbl.elf.0"
           00001140 Len: 00000040 Res: 00000000 "PartitionHeader bl31.elf.0"
           00001180 Len: 00000040 Res: 00000000 "PartitionHeader bl31.elf.1"
           000011c0 Len: 00000040 Res: 00000000 "PartitionHeader u-boot.elf.0"
           00001200 Len: 00000040 Res: 00000000 "PartitionHeader uImage.bin.0"
           00001240 Len: 00000040 Res: 00000000 "PartitionHeader system.dtb.0"
           00001280 Len: 00000040 Res: 00000000 "PartitionHeader uramdisk.image.gz.0"
           000012c0 Len: 00000040 Res: 00001540 "PartitionHeader Null"
           00002800 Len: 00036de8 Res: 00000000 "zynqmp_fsbl.elf.0"
           00039600 Len: 00006000 Res: 00000000 "bl31.elf.0"
           0003f600 Len: 00000020 Res: 00000000 "bl31.elf.1"
           0003f640 Len: 00093e70 Res: 00000000 "u-boot.elf.0"
           000d34c0 Len: 00cc2a40 Res: 00000000 "uImage.bin.0"
           00d95f00 Len: 00008764 Res: 00000000 "system.dtb.0"
           00d9e680 Len: 0079bbcc Res: 00000000 "uramdisk.image.gz.0"
           -- End of Dump
~/build
```

**References**

-   Xilinx logo from [https://twitter.com/xilinxinc](http://twitter.com/xilinxinc) at [link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)
    

**Other Info**

bootgen -help

```
pfefferz@plc2:~/build$ $PATH_TO_XSCT/bootgen -help
```

```
Xilinx BootGen
Build-2017.4, Date-Nov 23, 2017
Copyright (c) 1995-2017 Xilinx, Inc. All rights reserved.

------------------------------------------------------------------------------+
                       COMMAND LINE OPTIONS                                   |
-------------------------------+----------------------------------------------+
 -arch              [options]  | Xilinx Architecture                          |
                               | options: [zynq, zynqmp, fpga]                |
-------------------------------+----------------------------------------------+
 -image              | Input Boot Image File (.bif)                 |
-------------------------------+----------------------------------------------+
 -o                  | Output filename in MCS/BIN format            |
-------------------------------+----------------------------------------------+
 -w                 [options]  | Overwrite mode                               |
                               | options: [on, off]                           |
-------------------------------+----------------------------------------------+
 -encrypt           [options]  | AES Key storage in chip (Zynq only)          |
                               | options: [bbram, efuse]                      |
-------------------------------+----------------------------------------------+
 -p                    | Part name                                    |
-------------------------------+----------------------------------------------+
 -efuseppkbits       | Generate PPK hash for e-fuse                 |
-------------------------------+----------------------------------------------+
 -generate_hashes              | Generate SHA hashes (PKCS#1v1.5)             |
-------------------------------+----------------------------------------------+
 -spksignature       | Generate SPK signature file                  |
-------------------------------+----------------------------------------------+
 -fill               | Fill byte for padding                        |
-------------------------------+----------------------------------------------+
 -split             [options]  | Split partitions to diff files               |
                               | options: [bin, mcs]                          |
-------------------------------+----------------------------------------------+
 -padimageheader    [options]  | Pad header tables                            |
                               | options: [0, 1]                              |
-------------------------------+----------------------------------------------+
 -process_bitstream [options]  | Outputs bitstream in bin/mcs format          |
                               | options: [bin, mcs]                          |
-------------------------------+----------------------------------------------+
 -generate_keys auth [options] | Generate Authentication Keys                 |
                               | options: [pem, rsa]                          |
-------------------------------+----------------------------------------------+
 -dual_qspi_mode    [options]  | Generate 2 output files for Dual QSPI        |
                               | options: [parallel, stacked ]          |
-------------------------------+----------------------------------------------+
 -log               [options]  | Generate log file                            |
                               | options: [error, warning, info, debug, trace]|
-------------------------------+----------------------------------------------+
 -zynqmpes1                    | Generate boot image for (1.0)ES1             |
-------------------------------+----------------------------------------------+
 -h | -help                    | Print the help summary                       |
-------------------------------+----------------------------------------------+
 -bif_help                     | Print the BIF help summary                   |
-------------------------------+----------------------------------------------+
 Note     : For more info on bootgen options, use the command                 |
            bootgen -help 
```