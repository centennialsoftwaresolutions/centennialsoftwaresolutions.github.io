# Booting U-Boot via JTAG with PetaLinux Tools – Commands and Logs for Verifying a Functional System

![amd_logo](amd_logo.png)

For those working with AMD embedded systems, especially those harnessing the power of Zynq UltraScale+ MPSoC, booting your system correctly is crucial. A useful approach? Utilizing JTAG to boot U-Boot via PetaLinux Tools. In this post, I'll show the command for JTAG booting and list its inner workings. Whether you're troubleshooting issues or keen on executing commands step-by-step, this post should help.

## <u><span>Booting U-Boot via JTAG with PetaLinux Tools</span></u>

```
petalinux-boot --jtag --fpga --u-boot --hw_server-url TCP:localhost:3121 --verbose
```

```
[INFO] Sourcing buildtools
INFO: Use bitstream: "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.bit.
INFO: Please use --fpga --bitstream <BITSTREAM> to specify a bitstream if you want to use other bitstream.
XSDB Script:

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
puts stderr "INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.dtb at 0x00100000"
dow -data  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.dtb" 0x00100000
puts stderr "INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf to the target."
dow  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf"
puts stderr "INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf to the target."
dow  "/home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf"
con
exit
INFO: Launching XSDB for file download and boot.
INFO: This may take a few minutes, depending on the size of your image.
rlwrap: warning: your $TERM is 'xterm-256color' but rlwrap couldn't find it in the terminfo database. Expect some problems.: Inappropriate ioctl for device
INFO: Configuring the FPGA...                                                                                                                                       
INFO: Downloading bitstream: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.bit to the target.
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf to the target.
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf to the target.
INFO: Loading image: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/system.dtb at 0x00100000
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf to the target.
INFO: Downloading ELF file: /home/demouser/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf to the target.
```

## <u><span>Other Useful References</span></u>

### Output From 'print'

```
print
```

```
arch=arm
baudrate=115200
board=zynqmp
board_name=zcu102
board_rev=1.0
board_serial=881461172208-66530
boot_a_script=load ${devtype} ${devnum}:${distro_bootpart} ${scriptaddr} ${prefix}${script}; source ${scriptaddr}
boot_efi_binary=load ${devtype} ${devnum}:${distro_bootpart} ${kernel_addr_r} efi/boot/bootaa64.efi; if fdt addr -q ${fdt_addr_r}; then bootefi ${kernel_addr_r} $
{fdt_addr_r};else bootefi ${kernel_addr_r} ${fdtcontroladdr};fi
boot_efi_bootmgr=if fdt addr -q ${fdt_addr_r}; then bootefi bootmgr ${fdt_addr_r};else bootefi bootmgr;fi
boot_extlinux=sysboot ${devtype} ${devnum}:${distro_bootpart} any ${scriptaddr} ${prefix}${boot_syslinux_conf}
boot_net_usb_start=usb start
boot_prefixes=/ /boot/
boot_script_dhcp=boot.scr.uimg
boot_scripts=boot.scr.uimg boot.scr
boot_syslinux_conf=extlinux/extlinux.conf
boot_targets=jtag pxe dhcp jtag mmc0 mmc1 qspi0 nand0 usb0 usb1 scsi0 pxe dhcp
bootcmd=run distro_bootcmd
bootcmd_dhcp=devtype=dhcp; run boot_net_usb_start; if dhcp ${scriptaddr} ${boot_script_dhcp}; then source ${scriptaddr}; fi;setenv efi_fdtfile ${fdtfile}; setenv 
efi_old_vci ${bootp_vci};setenv efi_old_arch ${bootp_arch};setenv bootp_vci PXEClient:Arch:00011:UNDI:003000;setenv bootp_arch 0xb;if dhcp ${kernel_addr_r}; then 
tftpboot ${fdt_addr_r} dtb/${efi_fdtfile};if fdt addr -q ${fdt_addr_r}; then bootefi ${kernel_addr_r} ${fdt_addr_r}; else bootefi ${kernel_addr_r} ${fdtcontroladd
r};fi;fi;setenv bootp_vci ${efi_old_vci};setenv bootp_arch ${efi_old_arch};setenv efi_fdtfile;setenv efi_old_arch;setenv efi_old_vci;
bootcmd_jtag=echo JTAG: Trying to boot script at ${scriptaddr} && source ${scriptaddr}; echo JTAG: SCRIPT FAILED: continuing...;
bootcmd_mmc0=devnum=0; run mmc_boot
bootcmd_mmc1=devnum=1; run mmc_boot
bootcmd_nand0= nand info && nand read $scriptaddr $script_offset_f $script_size_f && echo NAND: Trying to boot script at ${scriptaddr} && source ${scriptaddr}; ec
ho NAND: SCRIPT FAILED: continuing...;
bootcmd_pxe=run boot_net_usb_start; dhcp; if pxe get; then pxe boot; fi
bootcmd_qspi0=sf probe 0 0 0 && sf read $scriptaddr $script_offset_f $script_size_f && echo QSPI: Trying to boot script at ${scriptaddr} && source ${scriptaddr}; 
echo QSPI: SCRIPT FAILED: continuing...;
bootcmd_scsi0=devnum=0; run scsi_boot
bootcmd_usb0=devnum=0; run usb_boot
bootcmd_usb1=devnum=1; run usb_boot
bootcmd_usb_dfu0=setenv dfu_alt_info boot.scr ram $scriptaddr $script_size_f && dfu 0 ram 0 60 && echo DFU0: Trying to boot script at ${scriptaddr} && source ${sc
riptaddr}; echo DFU0: SCRIPT FAILED: continuing...;
bootcmd_usb_dfu1=setenv dfu_alt_info boot.scr ram $scriptaddr $script_size_f && dfu 1 ram 1 60 && echo DFU1: Trying to boot script at ${scriptaddr} && source ${sc
riptaddr}; echo DFU1: SCRIPT FAILED: continuing...;
bootcmd_usb_thor0=setenv dfu_alt_info boot.scr ram $scriptaddr $script_size_f && thordown 0 ram 0 && echo THOR0: Trying to boot script at ${scriptaddr} && source 
${scriptaddr}; echo THOR0: SCRIPT FAILED: continuing...;
bootcmd_usb_thor1=setenv dfu_alt_info boot.scr ram $scriptaddr $script_size_f && thordown 1 ram 1 && echo THOR1: Trying to boot script at ${scriptaddr} && source 
${scriptaddr}; echo THOR1: SCRIPT FAILED: continuing...;
bootdelay=2
bootm_low=0
bootm_size=7fe00000
cpu=armv8
distro_bootcmd=scsi_need_init=; for target in ${boot_targets}; do run bootcmd_${target}; done
efi_dtb_prefixes=/ /dtb/ /dtb/current/
ethaddr=00:0a:35:07:8f:88
fdt_addr_r=0x40000000
fdt_size_r=0x400000
fdtcontroladdr=7bbf8dc0
fdtfile=xilinx/zynqmp-zcu102-rev1.0.dtb
kernel_addr_r=0x18000000
kernel_comp_addr_r=0x30000000
kernel_comp_size=0x3C00000
kernel_size_r=0x10000000
load_efi_dtb=load ${devtype} ${devnum}:${distro_bootpart} ${fdt_addr_r} ${prefix}${efi_fdtfile}
loadaddr=0x8000000
mmc_boot=if mmc dev ${devnum}; then devtype=mmc; run scan_dev_for_boot_part; fi
modeboot=jtagboot
multiboot=0
preboot=run scsi_init;usb start
pxefile_addr_r=0x10000000
ramdisk_addr_r=0x02100000
reset_reason=EXTERNAL
sata_boot=if sata dev ${devnum}; then devtype=sata; run scan_dev_for_boot_part; fi
scan_dev_for_boot=echo Scanning ${devtype} ${devnum}:${distro_bootpart}...; for prefix in ${boot_prefixes}; do run scan_dev_for_extlinux; run scan_dev_for_scripts; done;run scan_dev_for_efi;
scan_dev_for_boot_part=part list ${devtype} ${devnum} -bootable devplist; env exists devplist || setenv devplist 1; for distro_bootpart in ${devplist}; do if fstype ${devtype} ${devnum}:${distro_bootpart} bootfstype; then run scan_dev_for_boot; fi; done; setenv devplist
scan_dev_for_efi=setenv efi_fdtfile ${fdtfile}; for prefix in ${efi_dtb_prefixes}; do if test -e ${devtype} ${devnum}:${distro_bootpart} ${prefix}${efi_fdtfile}; then run load_efi_dtb; fi;done;run boot_efi_bootmgr;if test -e ${devtype} ${devnum}:${distro_bootpart} efi/boot/bootaa64.efi; then echo Found EFI removable media binary efi/boot/bootaa64.efi; run boot_efi_binary; echo EFI LOAD FAILED: continuing...; fi; setenv efi_fdtfile
scan_dev_for_extlinux=if test -e ${devtype} ${devnum}:${distro_bootpart} ${prefix}${boot_syslinux_conf}; then echo Found ${prefix}${boot_syslinux_conf}; run boot_extlinux; echo EXTLINUX FAILED: continuing...; fi
scan_dev_for_scripts=for script in ${boot_scripts}; do if test -e ${devtype} ${devnum}:${distro_bootpart} ${prefix}${script}; then echo Found U-Boot script ${prefix}${script}; run boot_a_script; echo SCRIPT FAILED: continuing...; fi; done
script_offset_f=3e80000
script_size_f=0x80000
scriptaddr=20000000
scsi_boot=run scsi_init; if scsi dev ${devnum}; then devtype=scsi; run scan_dev_for_boot_part; fi
scsi_init=if ${scsi_need_init}; then scsi_need_init=false; scsi scan; fi
soc=zynqmp
stderr=serial,vidconsole
stdin=serial
stdout=serial,vidconsole
ubifs_boot=if ubi part ${bootubipart} ${bootubioff} && ubifsmount ubi0:${bootubivol}; then devtype=ubi; devnum=ubi0; bootfstype=ubifs; distro_bootpart=${bootubivol}; run scan_dev_for_boot; ubifsumount; fi
usb_boot=usb start; if usb dev ${devnum}; then devtype=usb; run scan_dev_for_boot_part; fi
vendor=xilinx

Environment size: 6010/262139 bytes
```

### readelf -l Of Each ELF

#### pmufw.elf

```
~/tools/amd/Vitis/2023.1/gnu/aarch64/lin/aarch64-linux/bin/aarch64-linux-gnu-readelf -l ~/work/baseaddr/xilinx-zcu102-2023.1/images/linux/pmufw.elf
```

```
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

The ELF file is an executable that will start executing at 0xffdd1188. It has 3 segments 00, 01, 02.

Segment 00 starts at file offset 0x0000a0 and is loaded at memory address 0xffdc0000. This segment has permissions to read, write, and execute. The segment contains the actual code (.text), read-only data (.rodata), and some initialized data (.data).

Segment 01 starts at file offset 0x016d4c and is loaded at memory address 0xffdda9e0. This segment has permissions to read and write. The segment contains the stack (.stack).

Etc.

#### zynqmp\_fsbl.elf

```
~/tools/amd/Vitis/2023.1/gnu/aarch64/lin/aarch64-linux/bin/aarch64-linux-gnu-readelf -l ~ /work/baseaddr/xilinx-zcu102-2023.1/images/linux/zynqmp_fsbl.elf
```

```
<span><span>Elf file type is EXEC (Executable file)
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

#### u-boot.elf

```
~/tools/amd/Vitis/2023.1/gnu/aarch64/lin/aarch64-linux/bin/aarch64-linux-gnu-readelf -l ~/work/baseaddr/xilinx-zcu102-2023.1/images/linux/u-boot.elf
```

```
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

#### bl31.elf

```
~/tools/amd/Vitis/2023.1/gnu/aarch64/lin/aarch64-linux/bin/aarch64-linux-gnu-readelf -l ~/work/baseaddr/xilinx-zcu102-2023.1/images/linux/bl31.elf
```

```
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

## <u><span>References</span></u>

Logo from https://library.amd.com/media/ (requires a password)