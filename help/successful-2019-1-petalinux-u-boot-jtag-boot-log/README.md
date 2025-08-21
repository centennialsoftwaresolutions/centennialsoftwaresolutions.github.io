# Successful 2019.1 PetaLinux U-Boot JTAG Boot Log

![Xilinx_logo](Xilinx_logo.png)

This post lists a successful JTAG boot of U-Boot. This can be useful if a build doesn't boot and a developer is trying to figure out why. The developer can compare the last message printed with the log to get a clue on what isn't working.

**<u><span>Launched With</span></u>**

```
petalinux-boot --jtag --u-boot -v --hw_server-url 10.0.0.2:3121
```

**<u><span>Load and Run Log</span></u>**

```
INFO: sourcing build tools
XSDB Script:

connect -url 10.0.0.2:3121
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
INFO: Launching XSDB for file download and boot.
INFO: This may take a few minutes, depending on the size of your image.
rlwrap: warning: your $TERM is 'xterm-256color' but rlwrap couldn't find it in the terminfo database. Expect some problems.: Inappropriate ioctl for device
INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/pmufw.elf to the target.          
Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/pmufw.elf
	section, .vectors.reset: 0xffdc0000 - 0xffdc0007
	section, .vectors.sw_exception: 0xffdc0008 - 0xffdc000f
	section, .vectors.interrupt: 0xffdc0010 - 0xffdc0017
	section, .vectors.hw_exception: 0xffdc0020 - 0xffdc0027
	section, .text: 0xffdc0050 - 0xffdd0dc7
	section, .rodata: 0xffdd0dc8 - 0xffdd2edf
	section, .data: 0xffdd2ee0 - 0xffdd71d7
	section, .sdata2: 0xffdd71d8 - 0xffdd71d7
	section, .sdata: 0xffdd71d8 - 0xffdd71d7
	section, .sbss: 0xffdd71d8 - 0xffdd71d7
	section, .bss: 0xffdd71e0 - 0xffddb20b
	section, .srdata: 0xffddb20c - 0xffddbb2f
	section, .stack: 0xffddbb30 - 0xffddcb2f
	section, .xpbr_serv_ext_tbl: 0xffddf6e0 - 0xffddfadf
100%    0MB   0.6MB/s  00:00    
Setting PC to Program Start Address 0xffdcffe0
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/pmufw.elf
INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf to the target.
Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf
	section, .text: 0xfffc0000 - 0xfffd410b
	section, .init: 0xfffd4140 - 0xfffd4173
	section, .fini: 0xfffd4180 - 0xfffd41b3
	section, .note.gnu.build-id: 0xfffd41b4 - 0xfffd41d7
	section, .rodata: 0xfffd4200 - 0xfffd474f
	section, .sys_cfg_data: 0xfffd4780 - 0xfffd4f67
	section, .mmu_tbl0: 0xfffd5000 - 0xfffd500f
	section, .mmu_tbl1: 0xfffd6000 - 0xfffd7fff
	section, .mmu_tbl2: 0xfffd8000 - 0xfffdbfff
	section, .data: 0xfffdc000 - 0xfffdd3b7
	section, .sbss: 0xfffdd3b8 - 0xfffdd3bf
	section, .bss: 0xfffdd3c0 - 0xfffdf5bf
	section, .heap: 0xfffdf5c0 - 0xfffdf9bf
	section, .stack: 0xfffdf9c0 - 0xfffe19bf
	section, .dup_data: 0xfffe19c0 - 0xfffe2d77
	section, .handoff_params: 0xfffe9e00 - 0xfffe9e87
	section, .bitstream_buffer: 0xffff0040 - 0xfffffc3f
100%    0MB   0.8MB/s  00:00    
Setting PC to Program Start Address 0xfffc0000
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf
INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf to the target.
Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf
	section, .data: 0x10080000 - 0x1014c52b
100%    0MB   0.8MB/s  00:00    
Setting PC to Program Start Address 0x10080000
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf
INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf to the target.
Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf
	section, .text: 0xfffea000 - 0xffff1fff
	section, .rodata: 0xffff2000 - 0xffff2fff
	section, .data: 0xffff3000 - 0xffff6777
	section, stacks: 0xffff6780 - 0xffff787f
	section, .bss: 0xffff7880 - 0xffff8613
	section, xlat_table: 0xffff9000 - 0xffffdfff
	section, coherent_ram: 0xffffe000 - 0xffffefff
100%    0MB   0.8MB/s  00:00    
Setting PC to Program Start Address 0xfffea000
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf
```

**<u><span>Boot Log</span></u>**

```
xilinx-zcu102-2019_1 login: Xilinx Zynq MP First Stage Boot Loader
Release 2019.1   Jan 28 2021  -  08:16:00
NOTICE:  ATF running on XCZU9EG/silicon v3/RTL5.1 at 0xfffea000
NOTICE:  BL31: Secure code at 0x60000000
NOTICE:  BL31: Non secure code at 0x10080000
NOTICE:  BL31: v2.0(release):xilinx-v2018.3-720-g80d1c790
NOTICE:  BL31: Built : 21:11:59, May 15 2021
PMUFW:  v1.1


U-Boot 2019.01 (May 15 2021 - 21:12:25 +0000)

Model: ZynqMP ZCU102 Rev1.0
Board: Xilinx ZynqMP
DRAM:  4 GiB
EL Level:       EL2
Chip ID:        zu9eg
MMC:   mmc@ff170000: 0
Loading Environment from SPI Flash... SF: Detected n25q512a with page size 512 Bytes, erase size 128 KiB, total 128 M
iB
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

ethernet@ff0e0000 Waiting for PHY auto negotiation to complete............ done
BOOTP broadcast 1
BOOTP broadcast 2
BOOTP broadcast 3
BOOTP broadcast 4
BOOTP broadcast 5
BOOTP broadcast 6
BOOTP broadcast 7
BOOTP broadcast 8
BOOTP broadcast 9
BOOTP broadcast 10
BOOTP broadcast 11
BOOTP broadcast 12
BOOTP broadcast 13
BOOTP broadcast 14
BOOTP broadcast 15
BOOTP broadcast 16
BOOTP broadcast 17

Retry time exceeded; starting again
Hit any key to stop autoboot:  0
Device: mmc@ff170000
Manufacturer ID: 3
OEM: 5344
Name: SL16G
Bus Speed: 50000000
Mode : SD High Speed (50MHz)
Rd Block Len: 512
SD version 3.0
High Capacity: Yes
Capacity: 14.8 GiB
Bus Width: 4-bit
Erase Group Size: 512 Bytes
** Unable to read file image.ub **
ZynqMP>
```

**<u><span>References</span></u>**

-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]