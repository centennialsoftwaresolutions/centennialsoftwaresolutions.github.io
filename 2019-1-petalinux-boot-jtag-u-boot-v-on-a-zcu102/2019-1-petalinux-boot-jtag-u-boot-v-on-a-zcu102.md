# 2019.1 petalinux-boot --jtag --u-boot -v on a ZCU102

![xilinx_logo](xilinx_logo.png)

This post lists a log of petalinux-boot --jtag --u-boot -v on a ZCU102 from a 2019.1 build.

## Source Tools

```
cd ~/plxprjs/
cd xilinx-zcu102-2019.1/
source ~/petalinux/2019.1/settings.sh
```

## petalinux-boot --jtag --u-boot -v

```
demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1$ petalinux-boot --jtag --u-boot -v
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
attempting to launch hw_server                                                                                   

****** Xilinx hw_server v2019.1
  **** Build date : May 11 2019 at 11:28:07
    ** Copyright 1986-2019 Xilinx, Inc. All Rights Reserved.

INFO: hw_server application started
INFO: Use Ctrl-C to exit hw_server application

INFO: To connect to this hw_server instance use url: TCP:127.0.0.1:3121

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
100%    0MB   0.2MB/s  00:00    
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
100%    0MB   0.2MB/s  00:00    
Setting PC to Program Start Address 0xfffc0000
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf
INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf to the target.
Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf
	section, .data: 0x10080000 - 0x1014c7e3
100%    0MB   0.2MB/s  00:04    
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
100%    0MB   0.2MB/s  00:00    
Setting PC to Program Start Address 0xfffea000
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf
```

## Reference

Xilinx logo from \[[<u><span>link</span></u>](https://twitter.com/xilinxinc)\]