# Access PetaLinux Tool Commands, Build Everything and Program U-Boot and the Linux Kernel

![xilinx_logo_1](xilinx_logo_1.png)

This post shows how to get access to PetaLinux Tools commands, build everything and program U-Boot and the Linux kernel onto the ZCU102.

This post is meant to be a quick reference to steps laid out in other, longer posts.

**<u><span>Prerequisites</span></u>**

1\. <u><span>Connecting Vivado to Digilent's USB-to-JTAG through VirtualBox</span></u> at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/connecting-vivado-to-digilent-s-usb-to-jtag-through-virtualbox)\]

2\. <u><span>ZCU102 Development Using 2018.2 on a Linux VM Running on Windows: Part 1</span></u> at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/zcu102-development-using-2018-2-on-a-linux-vm-running-on-windows)\]

3\. <u><span>ZCU102 Development Using 2018.2 on a Linux VM Running on Windows: Part 2</span></u> at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/zcu102-development-using-2018-2-on-a-linux-vm-running-on-windows-part-2)\]

**<u><span>Steps</span></u>**

<u><span>Bring in the Environment</span></u>

Type **cd ~/plxprjs/xilinx-zcu102-2018.2**

Type **source /opt/pkg/petalinux/settings.sh**

<u><span>Build</span></u>

Type **petalinux-build**

<u><span>Boot U-Boot</span></u>

Type **petalinux-boot --jtag --u-boot -v**

Output:

```
XSDB Script:
INFO: Launching XSDB for file download and boot.
INFO: This may take a few minutes, depending on the size of your image.

connect
targets -set -nocase -filter {name =~ "*PSU*"}
mask_write 0xFFCA0038 0x1C0 0x1C0
targets -set -nocase -filter {name =~ "*MicroBlaze PMU*"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/pmufw.elf"
after 2000
con
targets -set -nocase -filter {name =~ "*APU*"}
mwr 0xffff0000 0x14000000
mask_write 0xFD1A0104 0x501 0x0
targets -set -nocase -filter {name =~ "*A53*#0"}

source /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/project-spec/hw-description/psu_init.tcl
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/zynqmp_fsbl.elf"
after 2000
con
after 4000; stop; catch {stop}; psu_ps_pl_isolation_removal; psu_ps_pl_reset_config
targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/u-boot.elf"
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/bl31.elf"
after 2000
con
exit
rlwrap: warning: your $TERM is 'xterm-256color' but rlwrap couldn't find it in the terminfo database. Expect some problems.: Inappropriate ioctl for device
INFO: Downloading ELF file to the target.                                       
Downloading Program -- /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/pmufw.elf
	section, .vectors.reset: 0xffdc0000 - 0xffdc0007
	section, .vectors.sw_exception: 0xffdc0008 - 0xffdc000f
	section, .vectors.interrupt: 0xffdc0010 - 0xffdc0017
	section, .vectors.hw_exception: 0xffdc0020 - 0xffdc0027
	section, .text: 0xffdc0050 - 0xffdce183
	section, .rodata: 0xffdce184 - 0xffdcf456
	section, .data: 0xffdcf458 - 0xffdd2797
	section, .sdata2: 0xffdd2798 - 0xffdd2797
	section, .sdata: 0xffdd2798 - 0xffdd2797
	section, .sbss: 0xffdd2798 - 0xffdd2797
	section, .bss: 0xffdd27a0 - 0xffdd6cff
	section, .srdata: 0xffdd6d00 - 0xffdd79e3
	section, .stack: 0xffdd79e4 - 0xffdd89e7
	section, .xpbr_serv_ext_tbl: 0xffddf6e0 - 0xffddfadf
100%    0MB   0.2MB/s  00:00    
Setting PC to Program Start Address 0xffdc8c68
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/pmufw.elf
INFO: Downloading ELF file to the target.
Downloading Program -- /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/zynqmp_fsbl.elf
	section, .text: 0xfffc0000 - 0xfffcfaef
	section, .init: 0xfffcfb00 - 0xfffcfb33
	section, .fini: 0xfffcfb40 - 0xfffcfb73
	section, .note.gnu.build-id: 0xfffcfb74 - 0xfffcfb97
	section, .rodata: 0xfffcfbc0 - 0xfffd002f
	section, .sys_cfg_data: 0xfffd0040 - 0xfffd0827
	section, .eh_frame: 0xfffd0828 - 0xfffd082b
	section, .mmu_tbl0: 0xfffd1000 - 0xfffd100f
	section, .mmu_tbl1: 0xfffd2000 - 0xfffd3fff
	section, .mmu_tbl2: 0xfffd4000 - 0xfffd7fff
	section, .data: 0xfffd8000 - 0xfffd92df
	section, .init_array: 0xfffd92e0 - 0xfffd92e7
	section, .fini_array: 0xfffd92e8 - 0xfffd92ef
	section, .sbss: 0xfffd92f0 - 0xfffd92ff
	section, .bss: 0xfffd9300 - 0xfffdb37f
	section, .heap: 0xfffdb380 - 0xfffdb77f
	section, .stack: 0xfffdb780 - 0xfffdd77f
	section, .dup_data: 0xfffdd780 - 0xfffdea5f
	section, .handoff_params: 0xfffe9e00 - 0xfffe9e87
	section, .bitstream_buffer: 0xffff0040 - 0xfffffc3f
100%    0MB   0.1MB/s  00:00    
Setting PC to Program Start Address 0xfffc0000
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/zynqmp_fsbl.elf
INFO: Downloading ELF file to the target.
Downloading Program -- /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/u-boot.elf
	section, .data: 0x10080000 - 0x1014ca6f
100%    0MB   0.1MB/s  00:05    
Setting PC to Program Start Address 0x10080000
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/u-boot.elf
INFO: Downloading ELF file to the target.
Downloading Program -- /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/bl31.elf
	section, .text: 0xfffea000 - 0xffff1fff
	section, .rodata: 0xffff2000 - 0xffff2fff
	section, .data: 0xffff3000 - 0xffff67cf
	section, stacks: 0xffff6800 - 0xffff78ff
	section, .bss: 0xffff7900 - 0xffff8613
	section, xlat_table: 0xffff9000 - 0xffffdfff
	section, coherent_ram: 0xffffe000 - 0xffffefff
100%    0MB   0.1MB/s  00:00    
Setting PC to Program Start Address 0xfffea000
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/bl31.elf
```

<u><span>Boot the Linux Kernel</span></u>

Type **petalinux-boot --jtag --kernel -v**

Output:

```
XSDB Script:
INFO: Launching XSDB for file download and boot.
INFO: This may take a few minutes, depending on the size of your image.

connect
targets -set -nocase -filter {name =~ "*PSU*"}
mask_write 0xFFCA0038 0x1C0 0x1C0
targets -set -nocase -filter {name =~ "*MicroBlaze PMU*"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/pmufw.elf"
after 2000
con
targets -set -nocase -filter {name =~ "*APU*"}
mwr 0xffff0000 0x14000000
mask_write 0xFD1A0104 0x501 0x0
targets -set -nocase -filter {name =~ "*A53*#0"}

source /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/project-spec/hw-description/psu_init.tcl
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/zynqmp_fsbl.elf"
after 2000
con
after 4000; stop; catch {stop}; psu_ps_pl_isolation_removal; psu_ps_pl_reset_config
targets -set -nocase -filter {name =~ "*A53*#0"}
dow -data "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/Image" 0x00080000
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
dow -data "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/system.dtb" 0x1407f000
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/misc/linux-boot/linux-boot.elf"
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/bl31.elf"
after 2000
con
exit
rlwrap: warning: your $TERM is 'xterm-256color' but rlwrap couldn't find it in the terminfo database. Expect some problems.: Inappropriate ioctl for device
INFO: Downloading ELF file to the target.                                       
Downloading Program -- /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/pmufw.elf
	section, .vectors.reset: 0xffdc0000 - 0xffdc0007
	section, .vectors.sw_exception: 0xffdc0008 - 0xffdc000f
	section, .vectors.interrupt: 0xffdc0010 - 0xffdc0017
	section, .vectors.hw_exception: 0xffdc0020 - 0xffdc0027
	section, .text: 0xffdc0050 - 0xffdce183
	section, .rodata: 0xffdce184 - 0xffdcf456
	section, .data: 0xffdcf458 - 0xffdd2797
	section, .sdata2: 0xffdd2798 - 0xffdd2797
	section, .sdata: 0xffdd2798 - 0xffdd2797
	section, .sbss: 0xffdd2798 - 0xffdd2797
	section, .bss: 0xffdd27a0 - 0xffdd6cff
	section, .srdata: 0xffdd6d00 - 0xffdd79e3
	section, .stack: 0xffdd79e4 - 0xffdd89e7
	section, .xpbr_serv_ext_tbl: 0xffddf6e0 - 0xffddfadf
100%    0MB   0.2MB/s  00:00    
Setting PC to Program Start Address 0xffdc8c68
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/pmufw.elf
INFO: Downloading ELF file to the target.
Downloading Program -- /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/zynqmp_fsbl.elf
	section, .text: 0xfffc0000 - 0xfffcfaef
	section, .init: 0xfffcfb00 - 0xfffcfb33
	section, .fini: 0xfffcfb40 - 0xfffcfb73
	section, .note.gnu.build-id: 0xfffcfb74 - 0xfffcfb97
	section, .rodata: 0xfffcfbc0 - 0xfffd002f
	section, .sys_cfg_data: 0xfffd0040 - 0xfffd0827
	section, .eh_frame: 0xfffd0828 - 0xfffd082b
	section, .mmu_tbl0: 0xfffd1000 - 0xfffd100f
	section, .mmu_tbl1: 0xfffd2000 - 0xfffd3fff
	section, .mmu_tbl2: 0xfffd4000 - 0xfffd7fff
	section, .data: 0xfffd8000 - 0xfffd92df
	section, .init_array: 0xfffd92e0 - 0xfffd92e7
	section, .fini_array: 0xfffd92e8 - 0xfffd92ef
	section, .sbss: 0xfffd92f0 - 0xfffd92ff
	section, .bss: 0xfffd9300 - 0xfffdb37f
	section, .heap: 0xfffdb380 - 0xfffdb77f
	section, .stack: 0xfffdb780 - 0xfffdd77f
	section, .dup_data: 0xfffdd780 - 0xfffdea5f
	section, .handoff_params: 0xfffe9e00 - 0xfffe9e87
	section, .bitstream_buffer: 0xffff0040 - 0xfffffc3f
100%    0MB   0.1MB/s  00:00    
Setting PC to Program Start Address 0xfffc0000
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/zynqmp_fsbl.elf
100%   28MB   0.1MB/s  03:23    
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/Image
100%    0MB   0.1MB/s  00:00    
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/system.dtb
INFO: Downloading ELF file to the target.
Downloading Program -- /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/misc/linux-boot/linux-boot.elf
	section, .text: 0x10080000 - 0x10080027
100%    0MB   0.0MB/s  00:00    
Setting PC to Program Start Address 0x10080000
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/build/misc/linux-boot/linux-boot.elf
INFO: Downloading ELF file to the target.
Downloading Program -- /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/bl31.elf
	section, .text: 0xfffea000 - 0xffff1fff
	section, .rodata: 0xffff2000 - 0xffff2fff
	section, .data: 0xffff3000 - 0xffff67cf
	section, stacks: 0xffff6800 - 0xffff78ff
	section, .bss: 0xffff7900 - 0xffff8613
	section, xlat_table: 0xffff9000 - 0xffffdfff
	section, coherent_ram: 0xffffe000 - 0xffffefff
100%    0MB   0.1MB/s  00:00    
Setting PC to Program Start Address 0xfffea000
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zcu102-2018.2/images/linux/bl31.elf
```

**Reference**

The Xilinx graphic is from \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]