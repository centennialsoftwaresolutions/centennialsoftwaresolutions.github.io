# Unraveling Xilinx UltraScale+ MPSoC Linux Boot Errors: A Deep Dive

![amd_logo](amd_logo.png)

Curious about debugging those elusive Xilinx UltraScale+ MPSoC Linux boot errors? Dive into this post and uncover the secret behind the petalinux-boot "verbose" switch. Discover the nuances of identifying physical load addresses of each component as they're loaded, and the art of pairing it with insights from "readelf -l" and U-Boot's bdinfo. If you've ever been stumped by one component overwriting another, this is your guide to clarity. Equip yourself with the tools to troubleshoot with confidence!

Lets get into "Unraveling Xilinx UltraScale+ MPSoC Linux Boot Errors: A Deep Dive"

Environment

- A PC connected to a ZCU102's USB-to-JTAG port.
- 2023.1 PetaLinux Tools and Vitis (  ) 
- Ubuntu 22.04.01
- PetaLinux Tools ZCU102 BSP xilinx-zcu102-v2023.1-05080224.bsp
- Tools installed to ~/tools/amd/

Using the petalinux-boot --verbose Switch Output in xsct

By using petalinux-boot's "verbose"  switch, saving the result, and running the output of the --verbose switch in xsct you'll see the physical load addresses of each component as those components are loaded. By pairing this with the MemSiz of each Segment listed via "readelf -l" and bdinfo from U-Boot, should boot get that far, a user can understand if one component overwrites another. If the boot fails to get to U-Boot, the script can be adjusted to "bisect the boot flow" running items up to the point of failure.  

Note, you can more easily understand where things are in memory by converting hex addresses to human readable addresses using numfmt:

```
numfmt --to iec $(printf "%d\n" 0x87FFFFFFF)
34G
```

Verbose petalinux-boot

```
petalinux-boot --jtag --fpga --kernel --hw_server-url TCP:localhost:3121 --verbose
```

Verbose petalinux-boot output (save this as **verbose_output.tcl**):

```
connect -url TCP:localhost:3121
for {set i 0} {$i < 20} {incr i} {
	if { [ta] != "" } break;
	after 50
}
puts stderr "INFO: Configuring the FPGA..."
puts stderr "INFO: Downloading bitstream: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.bit to the target."
fpga "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.bit"
targets -set -nocase -filter {name =~ "*PSU*"}
mask_write 0xFFCA0038 0x1C0 0x1C0
targets -set -nocase -filter {name =~ "*MicroBlaze PMU*"}

if { [string first "Stopped" [state]] != 0 } {
stop
}
puts stderr "INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf to the target."
dow  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf"
con
targets -set -nocase -filter {name =~ "*A53*#0"}
rst -processor -clear-registers

source /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/project-spec/hw-description/psu_init.tcl
puts stderr "INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf to the target."
dow  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf"
con

after 4000
stop
psu_ps_pl_isolation_removal; psu_ps_pl_reset_config
puts stderr "INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf to the target."
dow  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf"
puts stderr "INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/Image at 0x00200000"
dow -data  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/Image" 0x00200000
puts stderr "INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.dtb at 0x00100000"
dow -data  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.dtb" 0x00100000
puts stderr "INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/ramdisk.cpio.gz.u-boot at 0x04000000"
dow -data  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/ramdisk.cpio.gz.u-boot" 0x04000000
puts stderr "INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/boot.scr at 0x20000000"
dow -data  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/boot.scr" 0x20000000
dow  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf"
con
exit
```

Start xsct:

```
source ~/tools/amd/Vitis/2023.1/settings64.sh
xsct
```

source verbose_output.tcl in xsct

```
source verbose_output.tcl
```

xsct output:

```
INFO: Configuring the FPGA...                                                                                                                                     
INFO: Downloading bitstream: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.bit to the target.
100%    6MB   1.5MB/s  00:04                                                                                                                                      
Info: MicroBlaze PMU (target 13) Stopped at 0xffd02f24 (Stop)                                                                                                     
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf to the target.                                               
Downloading Program -- /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf
	section, .vectors.reset: 0xffdc0000 - 0xffdc0007
	section, .vectors.sw_exception: 0xffdc0008 - 0xffdc000f
	section, .vectors.interrupt: 0xffdc0010 - 0xffdc0017
	section, .vectors.hw_exception: 0xffdc0020 - 0xffdc0027
	section, .text: 0xffdc0050 - 0xffdd196f
	section, .rodata: 0xffdd1970 - 0xffdd2b8b
	section, .data: 0xffdd2b8c - 0xffdd6cab
	section, .sdata2: 0xffdd6cac - 0xffdd6caf
	section, .sdata: 0xffdd6cb0 - 0xffdd6caf
	section, .sbss: 0xffdd6cb0 - 0xffdd6caf
	section, .bss: 0xffdd6cc0 - 0xffdda9df
	section, .srdata: 0xffdda9e0 - 0xffddb2fb
	section, .stack: 0xffddb2fc - 0xffddc2ff
	section, .xpbr_serv_ext_tbl: 0xffddf6e0 - 0xffddfadf
100%    0MB   0.2MB/s  00:00                                                                                                                                      
Setting PC to Program Start Address 0xffdd1188
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf
Info: MicroBlaze PMU (target 13) Running
Info: Cortex-A53 #0 (target 9) Stopped at 0xffff0000 (Reset Catch)                                                                                                
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf to the target.
Downloading Program -- /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf
	section, .text: 0xfffc0000 - 0xfffd6693
	section, .note.gnu.build-id: 0xfffd6694 - 0xfffd66b7
	section, .init: 0xfffd66c0 - 0xfffd66f3
	section, .fini: 0xfffd6700 - 0xfffd6733
	section, .rodata: 0xfffd6740 - 0xfffd6c54
	section, .sys_cfg_data: 0xfffd6c80 - 0xfffd73eb
	section, .mmu_tbl0: 0xfffd8000 - 0xfffd800f
	section, .mmu_tbl1: 0xfffd9000 - 0xfffdafff
	section, .mmu_tbl2: 0xfffdb000 - 0xfffdefff
	section, .data: 0xfffdf000 - 0xfffe02c7
	section, .sbss: 0xfffe02c8 - 0xfffe02ff
	section, .bss: 0xfffe0300 - 0xfffe297f
	section, .heap: 0xfffe2980 - 0xfffe2d7f
	section, .stack: 0xfffe2d80 - 0xfffe4d7f
	section, .dup_data: 0xfffe4d80 - 0xfffe6047
	section, .handoff_params: 0xfffe9e00 - 0xfffe9e87
	section, .bitstream_buffer: 0xffff0040 - 0xfffffc3f
100%    0MB   0.1MB/s  00:01                                                                                                                                      
Setting PC to Program Start Address 0xfffc0000
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf
Info: Cortex-A53 #0 (target 9) Running                                                                                                                            
Info: Cortex-A53 #0 (target 9) Stopped at 0xfffd2cc0 (External Debug Request)                                                                                     
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf to the target.                                              
Downloading Program -- /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf
	section, .text: 0x10080000 - 0x100801e7
	section, .efi_runtime: 0x100801e8 - 0x10080d4f
	section, .text_rest: 0x10081000 - 0x1015aa3b
	section, .rodata: 0x1015aa40 - 0x1018fbe9
	section, .hash: 0x1018fbf0 - 0x1018fc07
	section, .data: 0x1018fc08 - 0x1019eabf
	section, .got: 0x1019eac0 - 0x1019eac7
	section, .got.plt: 0x1019eac8 - 0x1019eadf
	section, __u_boot_list: 0x1019eae0 - 0x101a4a57
	section, .efi_runtime_rel: 0x101a4a58 - 0x101a4c07
	section, .rela.dyn: 0x101a4c08 - 0x101c0147
	section, .bss_start: 0x101c0148 - 0x101c0147
	section, .bss: 0x101c0180 - 0x101d8d8f
	section, .bss_end: 0x101d8d90 - 0x101d8d8f
100%    1MB   0.1MB/s  00:14                                                                                                                                      
Setting PC to Program Start Address 0x10080000
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf
INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/Image at 0x00200000
100%   21MB   0.1MB/s  03:58                                                                                                                                      
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/Image
INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.dtb at 0x00100000
100%    0MB   0.1MB/s  00:00                                                                                                                                      
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.dtb
INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/ramdisk.cpio.gz.u-boot at 0x04000000
100%    5MB   0.1MB/s  00:58                                                                                                                                      
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/ramdisk.cpio.gz.u-boot
INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/boot.scr at 0x20000000
100%    0MB   0.1MB/s  00:00                                                                                                                                      
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/boot.scr
Downloading Program -- /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf
	section, .text: 0xfffea000 - 0xffff1fff
	section, .rodata: 0xffff2000 - 0xffff2fff
	section, .data: 0xffff3000 - 0xffff6091
	section, stacks: 0xffff60c0 - 0xffff71bf
	section, .bss: 0xffff71c0 - 0xffff7fbf
	section, xlat_table: 0xffff8000 - 0xffffcfff
	section, coherent_ram: 0xffffd000 - 0xffffdfff
100%    0MB   0.1MB/s  00:00                                                                                                                                      
Setting PC to Program Start Address 0xfffea000
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf
Info: Cortex-A53 #0 (target 9) Running 
```

readelf -l pmufw.elf:

```
~/tools/amd/Vitis/2023.1/gnu/aarch64/lin/aarch64-linux/bin/aarch64-linux-gnu-readelf -l /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf

Elf file type is EXEC (Executable file)
Entry point 0xffdd1188
There are 3 program headers, starting at offset 52

Program Headers:
  Type           Offset   VirtAddr   PhysAddr   FileSiz MemSiz  Flg Align
  LOAD           0x0000a0 0xffdc0000 0xffdc0000 0x16cac 0x1a9e0 RWE 0x20
  LOAD           0x016d4c 0xffdda9e0 0xffdda9e0 0x0091c 0x01920 RW  0x4
  LOAD           0x017668 0xffddf6e0 0xffddf6e0 0x00400 0x00400 RW  0x4

 Section to Segment mapping:
  Segment Sections...
   00     .vectors.reset .vectors.sw_exception .vectors.interrupt .vectors.hw_exception .text .rodata .data .sdata2 .bss 
   01     .srdata .stack 
   02     .xpbr_serv_ext_tbl
```

readelf -l zynqmp_fsbl.elf

```
~/tools/amd/Vitis/2023.1/gnu/aarch64/lin/aarch64-linux/bin/aarch64-linux-gnu-readelf -l /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf

Elf file type is EXEC (Executable file)
Entry point 0xfffc0000
There are 4 program headers, starting at offset 64

Program Headers:
  Type           Offset             VirtAddr           PhysAddr
                 FileSiz            MemSiz              Flags  Align
  LOAD           0x0000000000000200 0x00000000fffc0000 0x00000000fffc0000
                 0x00000000000202c8 0x0000000000026048  RWE    0x100
  LOAD           0x0000000000000000 0x00000000fffe9e00 0x00000000fffe9e00
                 0x0000000000000000 0x0000000000000088  RW     0x8
  LOAD           0x0000000000000000 0x00000000ffff0040 0x00000000ffff0040
                 0x0000000000000000 0x000000000000fc00  RW     0x40
  NOTE           0x0000000000016894 0x00000000fffd6694 0x00000000fffd6694
                 0x0000000000000024 0x0000000000000024  R      0x4

 Section to Segment mapping:
  Segment Sections...
   00     .text .note.gnu.build-id .init .fini .rodata .sys_cfg_data .mmu_tbl0 .mmu_tbl1 .mmu_tbl2 .data .sbss .bss .heap .stack .dup_data 
   01     .handoff_params 
   02     .bitstream_buffer 
   03     .note.gnu.build-id
```

readelf -l u-boot.elf

```
~/tools/amd/Vitis/2023.1/gnu/aarch64/lin/aarch64-linux/bin/aarch64-linux-gnu-readelf -l /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf

Elf file type is EXEC (Executable file)
Entry point 0x10080000
There are 2 program headers, starting at offset 64

Program Headers:
  Type           Offset             VirtAddr           PhysAddr
                 FileSiz            MemSiz              Flags  Align
  LOAD           0x0000000000010000 0x0000000010080000 0x0000000010080000
                 0x0000000000158d90 0x0000000000158d90  RWE    0x10000
  GNU_STACK      0x0000000000000000 0x0000000000000000 0x0000000000000000
                 0x0000000000000000 0x0000000000000000  RW     0x10

 Section to Segment mapping:
  Segment Sections...
   00     .text .efi_runtime .text_rest .rodata .hash .data .got .got.plt __u_boot_list .efi_runtime_rel .rela.dyn .bss_start .bss 
   01     
```

readelf -l bl31.elf (Trust Zone)

```
~/tools/amd/Vitis/2023.1/gnu/aarch64/lin/aarch64-linux/bin/aarch64-linux-gnu-readelf -l ~/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf

Elf file type is EXEC (Executable file)
Entry point 0xfffea000
There are 2 program headers, starting at offset 64

Program Headers:
  Type           Offset             VirtAddr           PhysAddr
                 FileSiz            MemSiz              Flags  Align
  LOAD           0x0000000000000000 0x00000000fffe0000 0x00000000fffe0000
                 0x0000000000016092 0x000000000001e000  RWE    0x10000
  GNU_STACK      0x0000000000000000 0x0000000000000000 0x0000000000000000
                 0x0000000000000000 0x0000000000000000  RW     0x10

 Section to Segment mapping:
  Segment Sections...
   00     .text .rodata .data stacks .bss xlat_table coherent_ram 
   01     
```

bdinfo

```
ZynqMP> bdinfo
boot_params = 0x0000000000000000
DRAM bank   = 0x0000000000000000
-> start    = 0x0000000000000000
-> size     = 0x000000007ff00000
DRAM bank   = 0x0000000000000001
-> start    = 0x0000000800000000
-> size     = 0x0000000080000000
flashstart  = 0x0000000000000000
flashsize   = 0x0000000000000000
flashoffset = 0x0000000000000000
baudrate    = 115200 bps
relocaddr   = 0x000000007fc87000
reloc off   = 0x000000006fc07000
Build       = 64-bit
current eth = ethernet@ff0e0000
ethaddr     = 00:0a:35:07:8f:88
IP addr     = <NULL>
fdt_blob    = 0x000000007bbf8ce0
new_fdt     = 0x000000007bbf8ce0
fdt_size    = 0x000000000000e0a0
lmb_dump_all:
 memory.cnt  = 0x2
 memory[0]      [0x0-0x7fefffff], 0x7ff00000 bytes flags: 0
 memory[1]      [0x800000000-0x87fffffff], 0x80000000 bytes flags: 0
 reserved.cnt  = 0x2
 reserved[0]    [0x0-0x7ffffff], 0x08000000 bytes flags: 4
 reserved[1]    [0x7bbf4850-0x7fdfffff], 0x0420b7b0 bytes flags: 0
devicetree  = board
arch_number = 0x0000000000000000
TLB addr    = 0x000000007fde0000
irq_sp      = 0x000000007bbf8cd0
sp start    = 0x000000007bbf8cd0
ARM frequency = 99 MHz
DSP frequency = 0 MHz
DDR frequency = 0 MHz
Early malloc usage: 16a0 / 8000
```

This awk script transforms hex to human readable inline:

```
 awk '{
    for (i = 1; i <= NF; i++) {
        if ($i ~ /^0x[a-fA-F0-9]+$/) {
            $i = strtonum($i);
            cmd = "numfmt --to iec " $i;
            cmd | getline human_readable
            close(cmd)
            $i = human_readable
        }
    }
    print $0
}' load_kernel.out
```

Giving you:

```
INFO: Configuring the FPGA...                                                                                                                                     

INFO: Downloading bitstream: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.bit to the target.
100%    6MB   1.5MB/s  00:04                                                                                                                                      

Info: MicroBlaze PMU (target 13) Stopped at 4.0G (Stop)
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf to the target.                                               

Downloading Program -- /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf
section, .vectors.reset: 4.0G - 4.0G
section, .vectors.sw_exception: 4.0G - 4.0G
section, .vectors.interrupt: 4.0G - 4.0G
section, .vectors.hw_exception: 4.0G - 4.0G
section, .text: 4.0G - 4.0G
section, .rodata: 4.0G - 4.0G
section, .data: 4.0G - 4.0G
section, .sdata2: 4.0G - 4.0G
section, .sdata: 4.0G - 4.0G
section, .sbss: 4.0G - 4.0G
section, .bss: 4.0G - 4.0G
section, .srdata: 4.0G - 4.0G
section, .stack: 4.0G - 4.0G
section, .xpbr_serv_ext_tbl: 4.0G - 4.0G
100%    0MB   0.2MB/s  00:00                                                                                                                                      

Setting PC to Program Start Address 4.0G
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf
Info: MicroBlaze PMU (target 13) Running
Info: Cortex-A53 #0 (target 9) Stopped at 4.0G (Reset Catch)
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf to the target.
Downloading Program -- /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf
section, .text: 4.0G - 4.0G
section, .note.gnu.build-id: 4.0G - 4.0G
section, .init: 4.0G - 4.0G
section, .fini: 4.0G - 4.0G
section, .rodata: 4.0G - 4.0G
section, .sys_cfg_data: 4.0G - 4.0G
section, .mmu_tbl0: 4.0G - 4.0G
section, .mmu_tbl1: 4.0G - 4.0G
section, .mmu_tbl2: 4.0G - 4.0G
section, .data: 4.0G - 4.0G
section, .sbss: 4.0G - 4.0G
section, .bss: 4.0G - 4.0G
section, .heap: 4.0G - 4.0G
section, .stack: 4.0G - 4.0G
section, .dup_data: 4.0G - 4.0G
section, .handoff_params: 4.0G - 4.0G
section, .bitstream_buffer: 4.0G - 4.0G
100%    0MB   0.1MB/s  00:01                                                                                                                                      

Setting PC to Program Start Address 4.0G
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf
Info: Cortex-A53 #0 (target 9) Running                                                                                                                            

Info: Cortex-A53 #0 (target 9) Stopped at 4.0G (External Debug Request)
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf to the target.                                              

Downloading Program -- /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf
section, .text: 257M - 257M
section, .efi_runtime: 257M - 257M
section, .text_rest: 257M - 258M
section, .rodata: 258M - 258M
section, .hash: 258M - 258M
section, .data: 258M - 258M
section, .got: 258M - 258M
section, .got.plt: 258M - 258M
section, __u_boot_list: 258M - 258M
section, .efi_runtime_rel: 258M - 258M
section, .rela.dyn: 258M - 258M
section, .bss_start: 258M - 258M
section, .bss: 258M - 258M
section, .bss_end: 258M - 258M
100%    1MB   0.1MB/s  00:14                                                                                                                                      

Setting PC to Program Start Address 257M
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf
INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/Image at 2.0M
100%   21MB   0.1MB/s  03:58                                                                                                                                      

Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/Image
INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.dtb at 1.0M
100%    0MB   0.1MB/s  00:00                                                                                                                                      

Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.dtb
INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/ramdisk.cpio.gz.u-boot at 64M
100%    5MB   0.1MB/s  00:58                                                                                                                                      

Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/ramdisk.cpio.gz.u-boot
INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/boot.scr at 512M
100%    0MB   0.1MB/s  00:00                                                                                                                                      

Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/boot.scr
Downloading Program -- /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf
section, .text: 4.0G - 4.0G
section, .rodata: 4.0G - 4.0G
section, .data: 4.0G - 4.0G
section, stacks: 4.0G - 4.0G
section, .bss: 4.0G - 4.0G
section, xlat_table: 4.0G - 4.0G
section, coherent_ram: 4.0G - 4.0G
100%    0MB   0.1MB/s  00:00                                                                                                                                      

Setting PC to Program Start Address 4.0G
Successfully downloaded /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf
Info: Cortex-A53 #0 (target 9) Running 
```

You could also use HERE syntax:

```
awk '{
    for (i = 1; i <= NF; i++) {
        if ($i ~ /^0x[a-fA-F0-9]+$/) {
            $i = strtonum($i);
            cmd = "numfmt --to iec --format=\"%0.4f\" " $i;
            cmd | getline human_readable
            close(cmd)
            $i = human_readable
        }
    }
    print $0
}' <<EOF
ZynqMP> bdinfo
boot_params = 0x0000000000000000
DRAM bank   = 0x0000000000000000
-> start    = 0x0000000000000000
-> size     = 0x000000007ff00000
DRAM bank   = 0x0000000000000001
-> start    = 0x0000000800000000
-> size     = 0x0000000080000000
flashstart  = 0x0000000000000000
flashsize   = 0x0000000000000000
flashoffset = 0x0000000000000000
baudrate    = 115200 bps
relocaddr   = 0x000000007fc87000
reloc off   = 0x000000006fc07000
Build       = 64-bit
current eth = ethernet@ff0e0000
ethaddr     = 00:0a:35:07:8f:88
IP addr     = <NULL>
fdt_blob    = 0x000000007bbf8ce0
new_fdt     = 0x000000007bbf8ce0
fdt_size    = 0x000000000000e0a0
lmb_dump_all:
 memory.cnt  = 0x2
 memory[0]      [0x0-0x7fefffff], 0x7ff00000 bytes flags: 0
 memory[1]      [0x800000000-0x87fffffff], 0x80000000 bytes flags: 0
 reserved.cnt  = 0x2
 reserved[0]    [0x0-0x7ffffff], 0x08000000 bytes flags: 4
 reserved[1]    [0x7bbf4850-0x7fdfffff], 0x0420b7b0 bytes flags: 0
devicetree  = board
arch_number = 0x0000000000000000
TLB addr    = 0x000000007fde0000
irq_sp      = 0x000000007bbf8cd0
sp start    = 0x000000007bbf8cd0
ARM frequency = 99 MHz
DSP frequency = 0 MHz
DDR frequency = 0 MHz
Early malloc usage: 16a0 / 8000
EOF
```

...and get:

```
ZynqMP> bdinfo
boot_params = 0.0000
DRAM bank = 0.0000
-> start = 0.0000
-> size = 1.9991G
DRAM bank = 1.0000
-> start = 32.0000G
-> size = 2.0000G
flashstart = 0.0000
flashsize = 0.0000
flashoffset = 0.0000
baudrate    = 115200 bps
relocaddr = 1.9967G
reloc off = 1.7462G
Build       = 64-bit
current eth = ethernet@ff0e0000
ethaddr     = 00:0a:35:07:8f:88
IP addr     = <NULL>
fdt_blob = 1.9336G
new_fdt = 1.9336G
fdt_size = 56.1570K
lmb_dump_all:
memory.cnt = 2.0000
memory[0] [0x0-0x7fefffff], 1.9991G bytes flags: 0
memory[1] [0x800000000-0x87fffffff], 2.0000G bytes flags: 0
reserved.cnt = 2.0000
reserved[0] [0x0-0x7ffffff], 128.0000M bytes flags: 4
reserved[1] [0x7bbf4850-0x7fdfffff], 66.0449M bytes flags: 0
devicetree  = board
arch_number = 0.0000
TLB addr = 1.9980G
irq_sp = 1.9336G
sp start = 1.9336G
ARM frequency = 99 MHz
DSP frequency = 0 MHz
DDR frequency = 0 MHz
Early malloc usage: 16a0 / 8000
```

## References

Logo from https://library.amd.com/media/ (requires a password)