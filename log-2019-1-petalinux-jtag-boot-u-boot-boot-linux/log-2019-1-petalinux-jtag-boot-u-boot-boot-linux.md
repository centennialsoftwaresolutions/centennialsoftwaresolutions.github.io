# Log: 2019.1 PetaLinux JTAG Boot U-Boot & Boot Linux

![Xilinx_logo](Xilinx_logo.png)

This post lists the output from a successful verbose PetaLinux Tools 2019.1 JTAG boot & subsequent Linux kernel boot from an image.ub on an SD Card on a ZCU102. It also list the output from the U-Boot 'bdinfo' command and the 'printenv' command.

**<u><span>JTAG Load</span></u>**

```
demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1$ petalinux-boot --jtag --u-boot -v --hw_server-url 10.0.0.2:3121
INFO: sourcing build tools
XSDB Script:
INFO: Launching XSDB for file download and boot.
INFO: This may take a few minutes, depending on the size of your image.

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
100%    0MB   0.6MB/s  00:00    
Setting PC to Program Start Address 0xfffc0000
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf
INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf to the target.
Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/u-boot.elf
	section, .data: 0x10080000 - 0x1014c51f
100%    0MB   0.8MB/s  00:01    
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

**<u><span>U-Boot bdinfo</span></u>**

```
ZynqMP> bdinfo
arch_number = 0x0000000000000000
boot_params = 0x0000000000000000
DRAM bank   = 0x0000000000000000
-> start    = 0x0000000000000000
-> size     = 0x000000007ff00000
DRAM bank   = 0x0000000000000001
-> start    = 0x0000000800000000
-> size     = 0x0000000080000000
baudrate    = 115200 bps
TLB addr    = 0x000000007fee0000
relocaddr   = 0x000000007fdea000
reloc off   = 0x000000006fd6a000
irq_sp      = 0x000000007dd9ec70
sp start    = 0x000000007dd9ec70
ARM frequency = 99 MHz
DSP frequency = 0 MHz
DDR frequency = 0 MHz
Early malloc usage: eb0 / 8000
fdt_blob    = 0x000000007dd9ec88
```

**<u><span>U-Boot printenv</span></u>**

```
ZynqMP> printenv
arch=arm
autoload=no
baudrate=115200
board=zynqmp
board_name=zynqmp
boot_img=BOOT.BIN
boot_targets=pxe dhcp
bootcmd=run default_bootcmd
bootdelay=4
bootenv=uEnv.txt
bootenvsize=0x40000
bootenvstart=0x1e00000
clobstart=0x10000000
console=console=ttyPS0,115200
cp_kernel2ram=mmcinfo && fatload mmc ${sdbootdev} ${netstart} ${kernel_img}
cpu=armv8
default_bootcmd=run uenvboot; run cp_kernel2ram && bootm ${netstart}
dfu_mmc_info=set dfu_alt_info ${kernel_image} fat 0 1\\;dfu_mmc=run dfu_mmc_info && dfu 0 mmc 0
dfu_ram=run dfu_ram_info && dfu 0 ram 0
dfu_ram_info=setenv dfu_alt_info image.ub ram $netstart 0x1e00000
dtb_img=system.dtb
dtbnetstart=0x23fff000
eraseenv=sf probe 0 && sf erase ${bootenvstart} ${bootenvsize}
eth1addr=11:0a:35:00:22:01
ethact=ethernet@ff0e0000
ethaddr=00:0a:35:00:22:01
fault=echo ${img} image size is greater than allocated place - partition ${img} is NOT UPDATED
fdtcontroladdr=7dd9ec88
fdtfile=xilinx/zynqmp-zcu102-rev1.0.dtb
importbootenv=echo "Importing environment from SD ..."; env import -t ${loadbootenv_addr} $filesize
install_boot=mmcinfo && fatwrite mmc ${sdbootdev} ${clobstart} ${boot_img} ${filesize}
install_jffs2=sf probe 0 && sf erase ${jffs2start} ${jffs2size} && sf write ${clobstart} ${jffs2start} ${filesize}
install_kernel=mmcinfo && fatwrite mmc ${sdbootdev} ${clobstart} ${kernel_img} ${filesize}
jffs2_img=rootfs.jffs2
kernel_img=image.ub
load_boot=tftpboot ${clobstart} ${boot_img}
load_dtb=tftpboot ${clobstart} ${dtb_img}
load_jffs2=tftpboot ${clobstart} ${jffs2_img}
load_kernel=tftpboot ${clobstart} ${kernel_img}
loadaddr=0x10000000
loadbootenv=load mmc $sdbootdev:$partid ${loadbootenv_addr} ${bootenv}
loadbootenv_addr=0x00100000
modeboot=jtagboot
nc=setenv stdout nc;setenv stdin nc;
netboot=tftpboot ${netstart} ${kernel_img} && bootm
netstart=0x10000000
psserial0=setenv stdout ttyPS0;setenv stdin ttyPS0
reset_reason=EXTERNAL
sd_uEnvtxt_existence_test=test -e mmc $sdbootdev:$partid /uEnv.txt
sd_update_dtb=echo Updating dtb from SD; mmcinfo && fatload mmc ${sdbootdev}:1 ${clobstart} ${dtb_img} && run install_dtb
sd_update_jffs2=echo Updating jffs2 from SD; mmcinfo && fatload mmc ${sdbootdev}:1 ${clobstart} ${jffs2_img} && run install_jffs2
sdbootdev=0
serial=setenv stdout serial;setenv stdin serial
serverip=192.168.239.133
soc=zynqmp
stderr=serial@ff000000
stdin=serial@ff000000
stdout=serial@ff000000
test_crc=if imi ${clobstart}; then run test_img; else echo ${img} Bad CRC - ${img} is NOT UPDATED; fi
test_img=setenv var "if test ${filesize} -gt ${psize}; then run fault; else run ${installcmd}; fi"; run var; setenv var
thor_mmc=run dfu_mmc_info && thordown 0 mmc 0
thor_ram=run dfu_ram_info && thordown 0 ram 0
uenvboot=if run sd_uEnvtxt_existence_test; then run loadbootenv; echo Loaded environment from ${bootenv}; run importbootenv; fi; if test -n $uenvcmd;
 then echo Running uenvcmd ...; run uenvcmd; fi
update_boot=setenv img boot; setenv psize ${bootsize}; setenv installcmd "install_boot"; run load_boot ${installcmd}; setenv img; setenv psize; setenv installcmd
update_dtb=setenv img dtb; setenv psize ${dtbsize}; setenv installcmd "install_dtb"; run load_dtb test_img; setenv img; setenv psize; setenv installcmd
update_jffs2=setenv img jffs2; setenv psize ${jffs2size}; setenv installcmd "install_jffs2"; run load_jffs2 test_img; setenv img; setenv psize; setenv installcmd
update_kernel=setenv img kernel; setenv psize ${kernelsize}; setenv installcmd "install_kernel"; run load_kernel ${installcmd}; setenv img; setenv psize; setenv installcmd
vendor=xilinx

Environment size: 3551/262140 bytes
ZynqMP>
```

**<u><span>Boot Log</span></u>**

```
Xilinx Zynq MP First Stage Boot Loader
Release 2019.1   Jul 19 2021  -  02:27:45
NOTICE:  ATF running on XCZU9EG/silicon v3/RTL5.1 at 0xfffea000
NOTICE:  BL31: Secure code at 0x60000000
NOTICE:  BL31: Non secure code at 0x10080000
NOTICE:  BL31: v2.0(release):xilinx-v2018.3-720-g80d1c790
NOTICE:  BL31: Built : 02:25:10, Jul 19 2021
PMUFW:  v1.1


U-Boot 2019.01 (Jul 19 2021 - 02:26:23 +0000)

Model: ZynqMP ZCU102 Rev1.0
Board: Xilinx ZynqMP
DRAM:  4 GiB
EL Level:       EL2
Chip ID:        zu9eg
MMC:   mmc@ff170000: 0
Loading Environment from SPI Flash... SF: Detected n25q512a with page size 512 Bytes, erase size 128 KiB, total 128 MiB
OK
In:    serial@ff000000
Out:   serial@ff000000
Err:   serial@ff000000
Model: ZynqMP ZCU102 Rev1.0
Board: Xilinx ZynqMP
Net:   ZYNQ GEM: ff0e0000, phyaddr c, interface rgmii-id

Warning: ethernet@ff0e0000 MAC addresses don't match:
Address in ROM is          ff:ff:ff:ff:ff:ff
Address in environment is  00:0a:35:00:22:01
eth0: ethernet@ff0e0000
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
24818960 bytes read in 1620 ms (14.6 MiB/s)
## Loading kernel from FIT Image at 10000000 ...
   Using 'conf@system-top.dtb' configuration
   Trying 'kernel@1' kernel subimage
     Description:  Linux kernel
     Type:         Kernel Image
     Compression:  uncompressed
     Data Start:   0x10000108
     Data Size:    18149888 Bytes = 17.3 MiB
     Architecture: AArch64
     OS:           Linux
     Load Address: 0x00080000
     Entry Point:  0x00080000
     Hash algo:    sha1
     Hash value:   bd76f4120cf683f15ca8c92ca3c2bf3af8601a37
   Verifying Hash Integrity ... sha1+ OK
## Loading ramdisk from FIT Image at 10000000 ...
   Using 'conf@system-top.dtb' configuration
   Trying 'ramdisk@1' ramdisk subimage
     Description:  petalinux-user-image
     Type:         RAMDisk Image
     Compression:  gzip compressed
     Data Start:   0x11159618
     Data Size:    6625640 Bytes = 6.3 MiB
     Architecture: AArch64
     OS:           Linux
     Load Address: unavailable
     Entry Point:  unavailable
     Hash algo:    sha1
     Hash value:   c1e81735e2881bac098a6b5faf7bce7e75aa4d78
   Verifying Hash Integrity ... sha1+ OK
## Loading fdt from FIT Image at 10000000 ...
   Using 'conf@system-top.dtb' configuration
   Trying 'fdt@system-top.dtb' fdt subimage
     Description:  Flattened Device Tree blob
     Type:         Flat Device Tree
     Compression:  uncompressed
     Data Start:   0x1114f40c
     Data Size:    41288 Bytes = 40.3 KiB
     Architecture: AArch64
     Hash algo:    sha1
     Hash value:   2062c3ae51659cc8ac7ab76bf3ae0dc311ca4b08
   Verifying Hash Integrity ... sha1+ OK
   Booting using the fdt blob at 0x1114f40c
   Loading Kernel Image ... OK
   Loading Ramdisk to 079ae000, end 07fff968 ... OK
   Loading Device Tree to 00000000079a0000, end 00000000079ad147 ... OK

Starting kernel ...

[    0.000000] Booting Linux on physical CPU 0x0000000000 [0x410fd034]
[    0.000000] Linux version 4.19.0-xilinx-v2019.1 (oe-user@oe-host) (gcc version 8.2.0 (GCC)) #1 SMP Mon Jul 19 02:26:41 UTC 2021
[    0.000000] Machine model: ZynqMP ZCU102 Rev1.0
[    0.000000] earlycon: cdns0 at MMIO 0x00000000ff000000 (options '115200n8')
[    0.000000] bootconsole [cdns0] enabled
[    0.000000] efi: Getting EFI parameters from FDT:
[    0.000000] efi: UEFI not found.
[    0.000000] cma: Reserved 256 MiB at 0x000000006fc00000
[    0.000000] psci: probing for conduit method from DT.
[    0.000000] psci: PSCIv1.1 detected in firmware.
[    0.000000] psci: Using standard PSCI v0.2 function IDs
[    0.000000] psci: MIGRATE_INFO_TYPE not supported.
[    0.000000] psci: SMC Calling Convention v1.1
[    0.000000] random: get_random_bytes called from start_kernel+0x94/0x3f8 with crng_init=0
[    0.000000] percpu: Embedded 23 pages/cpu @(____ptrval____) s53656 r8192 d32360 u94208
[    0.000000] Detected VIPT I-cache on CPU0
[    0.000000] CPU features: enabling workaround for ARM erratum 845719
[    0.000000] Speculative Store Bypass Disable mitigation not required
[    0.000000] CPU features: detected: Kernel page table isolation (KPTI)
[    0.000000] Built 1 zonelists, mobility grouping on.  Total pages: 1033987
[    0.000000] Kernel command line: earlycon console=ttyPS0,115200 clk_ignore_unused
[    0.000000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.000000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000000] software IO TLB: mapped [mem 0x6bc00000-0x6fc00000] (64MB)
[    0.000000] Memory: 3776224K/4193280K available (10812K kernel code, 636K rwdata, 5428K rodata, 832K init, 316K bss, 154912K reserved, 262144K cma
-reserved)
[    0.000000] rcu: Hierarchical RCU implementation.
[    0.000000] rcu:     RCU event tracing is enabled.
[    0.000000] rcu:     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS: 64, nr_irqs: 64, preallocated irqs: 0
[    0.000000] GIC: Adjusting CPU interface base to 0x00000000f902f000
[    0.000000] GIC: Using split EOI/Deactivate mode
[    0.000000] arch_timer: cp15 timer(s) running at 99.99MHz (phys).
[    0.000000] clocksource: arch_sys_counter: mask: 0xffffffffffffff max_cycles: 0x170f8de2d3, max_idle_ns: 440795206112 ns
[    0.000003] sched_clock: 56 bits at 99MHz, resolution 10ns, wraps every 4398046511101ns
[    0.008238] Console: colour dummy device 80x25
[    0.012392] Calibrating delay loop (skipped), value calculated using timer frequency.. 199.98 BogoMIPS (lpj=399960)
[    0.022757] pid_max: default: 32768 minimum: 301
[    0.027445] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.034012] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.041783] ASID allocator initialised with 32768 entries
[    0.046509] rcu: Hierarchical SRCU implementation.
[    0.051531] EFI services will not be available.
[    0.055826] smp: Bringing up secondary CPUs ...
[    0.060486] Detected VIPT I-cache on CPU1
[    0.060514] CPU1: Booted secondary processor 0x0000000001 [0x410fd034]
[    0.060816] Detected VIPT I-cache on CPU2
[    0.060835] CPU2: Booted secondary processor 0x0000000002 [0x410fd034]
[    0.061119] Detected VIPT I-cache on CPU3
[    0.061138] CPU3: Booted secondary processor 0x0000000003 [0x410fd034]
[    0.061182] smp: Brought up 1 node, 4 CPUs
[    0.095682] SMP: Total of 4 processors activated.
[    0.100355] CPU features: detected: 32-bit EL0 Support
[    0.106979] CPU: All CPU(s) started at EL2
[    0.109535] alternatives: patching kernel code
[    0.114777] devtmpfs: initialized
[    0.121745] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.126923] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.138494] xor: measuring software checksum speed
[    0.177123]    8regs     :  2375.000 MB/sec
[    0.217149]    8regs_prefetch:  2051.000 MB/sec
[    0.257179]    32regs    :  2724.000 MB/sec
[    0.297208]    32regs_prefetch:  2308.000 MB/sec
[    0.297237] xor: using function: 32regs (2724.000 MB/sec)
[    0.301553] pinctrl core: initialized pinctrl subsystem
[    0.307319] NET: Registered protocol family 16
[    0.311388] audit: initializing netlink subsys (disabled)
[    0.316586] audit: type=2000 audit(0.264:1): state=initialized audit_enabled=0 res=1
[    0.324234] cpuidle: using governor menu
[    0.328207] vdso: 2 pages (1 code @ (____ptrval____), 1 data @ (____ptrval____))
[    0.335461] hw-breakpoint: found 6 breakpoint and 4 watchpoint registers.
[    0.342879] DMA: preallocated 256 KiB pool for atomic allocations
[    0.362121] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
[    0.430909] raid6: int64x1  gen()   446 MB/s
[    0.498982] raid6: int64x1  xor()   454 MB/s
[    0.566971] raid6: int64x2  gen()   680 MB/s
[    0.635012] raid6: int64x2  xor()   600 MB/s
[    0.703096] raid6: int64x4  gen()   981 MB/s
[    0.771140] raid6: int64x4  xor()   737 MB/s
[    0.839152] raid6: int64x8  gen()  1163 MB/s
[    0.907208] raid6: int64x8  xor()   759 MB/s
[    0.975252] raid6: neonx1   gen()   734 MB/s
[    1.043286] raid6: neonx1   xor()   879 MB/s
[    1.111350] raid6: neonx2   gen()  1127 MB/s
[    1.179381] raid6: neonx2   xor()  1173 MB/s
[    1.247443] raid6: neonx4   gen()  1482 MB/s
[    1.315493] raid6: neonx4   xor()  1418 MB/s
[    1.383532] raid6: neonx8   gen()  1541 MB/s
[    1.451580] raid6: neonx8   xor()  1460 MB/s
[    1.451606] raid6: using algorithm neonx8 gen() 1541 MB/s
[    1.455571] raid6: .... xor() 1460 MB/s, rmw enabled
[    1.460503] raid6: using neon recovery algorithm
[    1.465813] SCSI subsystem initialized
[    1.468983] usbcore: registered new interface driver usbfs
[    1.474295] usbcore: registered new interface driver hub
[    1.479564] usbcore: registered new device driver usb
[    1.484608] media: Linux media interface: v0.10
[    1.489072] videodev: Linux video capture interface: v2.00
[    1.494522] pps_core: LinuxPPS API ver. 1 registered
[    1.499432] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.508525] PTP clock support registered
[    1.512423] EDAC MC: Ver: 3.0.0
[    1.515920] zynqmp-ipi-mbox mailbox@ff990400: Probed ZynqMP IPI Mailbox driver.
[    1.523047] FPGA manager framework
[    1.526330] Advanced Linux Sound Architecture Driver Initialized.
[    1.532485] Bluetooth: Core ver 2.22
[    1.535781] NET: Registered protocol family 31
[    1.540178] Bluetooth: HCI device and connection manager initialized
[    1.546495] Bluetooth: HCI socket layer initialized
[    1.551338] Bluetooth: L2CAP socket layer initialized
[    1.556369] Bluetooth: SCO socket layer initialized
[    1.561542] clocksource: Switched to clocksource arch_sys_counter
[    1.567340] VFS: Disk quotas dquot_6.6.0
[    1.571186] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.582186] NET: Registered protocol family 2
[    1.582638] tcp_listen_portaddr_hash hash table entries: 2048 (order: 3, 32768 bytes)
[    1.590137] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    1.597473] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    1.604227] TCP: Hash tables configured (established 32768 bind 32768)
[    1.610395] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.616376] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.622850] NET: Registered protocol family 1
[    1.627242] RPC: Registered named UNIX socket transport module.
[    1.632920] RPC: Registered udp transport module.
[    1.637586] RPC: Registered tcp transport module.
[    1.642259] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    1.648991] Trying to unpack rootfs image as initramfs...
[    1.925415] Freeing initrd memory: 6468K
[    1.925819] hw perfevents: no interrupt-affinity property for /pmu, guessing.
[    1.930958] hw perfevents: enabled with armv8_pmuv3 PMU driver, 7 counters available
[    1.939422] Initialise system trusted keyrings
[    1.942980] workingset: timestamp_bits=62 max_order=20 bucket_order=0
[    1.950073] NFS: Registering the id_resolver key type
[    1.954351] Key type id_resolver registered
[    1.958482] Key type id_legacy registered
[    1.962468] nfs4filelayout_init: NFSv4 File Layout Driver Registering...
[    1.969136] jffs2: version 2.2. (NAND) \A9 2001-2006 Red Hat, Inc.
[    3.062928] NET: Registered protocol family 38
[    3.125276] Key type asymmetric registered
[    3.125304] Asymmetric key parser 'x509' registered
[    3.128636] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 247)
[    3.135938] io scheduler noop registered
[    3.139827] io scheduler deadline registered
[    3.144095] io scheduler cfq registered (default)
[    3.148738] io scheduler mq-deadline registered
[    3.153235] io scheduler kyber registered
[    3.184940] Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled
[    3.189117] cacheinfo: Unable to detect cache hierarchy for CPU 0
[    3.196136] brd: module loaded
[    3.199944] loop: module loaded
[    3.200770] mtdoops: mtd device (mtddev=name/number) must be supplied
[    3.205563] libphy: Fixed MDIO Bus: probed
[    3.209612] tun: Universal TUN/TAP device driver, 1.6
[    3.213433] CAN device driver interface
[    3.218104] usbcore: registered new interface driver asix
[    3.222534] usbcore: registered new interface driver ax88179_178a
[    3.228585] usbcore: registered new interface driver cdc_ether
[    3.234380] usbcore: registered new interface driver net1080
[    3.240000] usbcore: registered new interface driver cdc_subset
[    3.245883] usbcore: registered new interface driver zaurus
[    3.251430] usbcore: registered new interface driver cdc_ncm
[    3.257522] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.263510] ehci-pci: EHCI PCI platform driver
[    3.268206] usbcore: registered new interface driver uas
[    3.273229] usbcore: registered new interface driver usb-storage
[    3.279677] rtc_zynqmp ffa60000.rtc: rtc core: registered ffa60000.rtc as rtc0
[    3.286401] i2c /dev entries driver
[    3.291417] usbcore: registered new interface driver uvcvideo
[    3.295517] USB Video Class driver (1.1.1)
[    3.300125] Bluetooth: HCI UART driver ver 2.3
[    3.304000] Bluetooth: HCI UART protocol H4 registered
[    3.309099] Bluetooth: HCI UART protocol BCSP registered
[    3.314394] Bluetooth: HCI UART protocol LL registered
[    3.319479] Bluetooth: HCI UART protocol ATH3K registered
[    3.324859] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.331109] Bluetooth: HCI UART protocol Intel registered
[    3.336452] Bluetooth: HCI UART protocol QCA registered
[    3.341658] usbcore: registered new interface driver bcm203x
[    3.347274] usbcore: registered new interface driver bpa10x
[    3.352812] usbcore: registered new interface driver bfusb
[    3.358262] usbcore: registered new interface driver btusb
[    3.363685] Bluetooth: Generic Bluetooth SDIO driver ver 0.1
[    3.369353] usbcore: registered new interface driver ath3k
[    3.374880] EDAC MC: ECC not enabled
[    3.378507] EDAC DEVICE0: Giving out device to module zynqmp-ocm-edac controller zynqmp_ocm: DEV ff960000.memory-controller (INTERRUPT)
[    3.391095] sdhci: Secure Digital Host Controller Interface driver
[    3.396559] sdhci: Copyright(c) Pierre Ossman
[    3.400883] sdhci-pltfm: SDHCI platform and OF driver helper
[    3.406824] ledtrig-cpu: registered to indicate activity on CPUs
[    3.412520] zynqmp_firmware_probe Platform Management API v1.1
[    3.418277] zynqmp_firmware_probe Trustzone version v1.0
[    3.426139] zynqmp-pinctrl firmware:zynqmp-firmware:pinctrl: zynqmp pinctrl initialized
[    3.452897] zynqmp_clk_mux_get_parent() getparent failed for clock: lpd_wdt, ret = -22
[    3.455599] alg: No test for xilinx-zynqmp-aes (zynqmp-aes)
[    3.460721] zynqmp_aes zynqmp_aes: AES Successfully Registered
[    3.460721]
[    3.468225] alg: No test for xilinx-keccak-384 (zynqmp-keccak-384)
[    3.474373] alg: No test for xilinx-zynqmp-rsa (zynqmp-rsa)
[    3.479994] usbcore: registered new interface driver usbhid
[    3.485267] usbhid: USB HID core driver
[    3.491348] fpga_manager fpga0: Xilinx ZynqMP FPGA Manager registered
[    3.495850] usbcore: registered new interface driver snd-usb-audio
[    3.502489] pktgen: Packet Generator for packet performance testing. Version: 2.75
[    3.509511] Initializing XFRM netlink socket
[    3.513455] NET: Registered protocol family 10
[    3.518143] Segment Routing with IPv6
[    3.521503] sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
[    3.527637] NET: Registered protocol family 17
[    3.531732] NET: Registered protocol family 15
[    3.536143] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.
[    3.549056] can: controller area network core (rev 20170425 abi 9)
[    3.555190] NET: Registered protocol family 29
[    3.559577] can: raw protocol (rev 20170425)
[    3.563814] can: broadcast manager protocol (rev 20170425 t)
[    3.569439] can: netlink gateway (rev 20170425) max_hops=1
[    3.575101] Bluetooth: RFCOMM TTY layer initialized
[    3.579739] Bluetooth: RFCOMM socket layer initialized
[    3.584848] Bluetooth: RFCOMM ver 1.11
[    3.588560] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.593832] Bluetooth: BNEP filters: protocol multicast
[    3.599024] Bluetooth: BNEP socket layer initialized
[    3.603953] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[    3.609842] Bluetooth: HIDP socket layer initialized
[    3.614879] 9pnet: Installing 9P2000 support
[    3.619020] Key type dns_resolver registered
[    3.623628] registered taskstats version 1
[    3.627316] Loading compiled-in X.509 certificates
[    3.632386] Btrfs loaded, crc32c=crc32c-generic
[    3.642754] ff000000.serial: ttyPS0 at MMIO 0xff000000 (irq = 47, base_baud =   3.651695] console [ttyPS0] enabled
[    3.651695] console [ttyPS0] enabled
[    3.655277] bootconsole [cdns0] disabled
[    3.655277] bootconsole [cdns0] disabled
[    3.663400] ff010000.serial: ttyPS1 at MMIO 0xff010000 (irq = 48, base_baud = 6249375) is a xuartps
[    3.676804] of-fpga-region fpga-full: FPGA Region probed
[    3.682631] nwl-pcie fd0e0000.pcie: Link is DOWN
[    3.687276] nwl-pcie fd0e0000.pcie: host bridge /amba/pcie@fd0e0000 ranges:
[    3.694243] nwl-pcie fd0e0000.pcie:   MEM 0xe0000000..0xefffffff -> 0xe0000000
[    3.701465] nwl-pcie fd0e0000.pcie:   MEM 0x600000000..0x7ffffffff -> 0x600000000
[    3.709047] nwl-pcie fd0e0000.pcie: PCI host bridge to bus 0000:00
[    3.715222] pci_bus 0000:00: root bus resource [bus 00-ff]
[    3.720697] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xefffffff]
[    3.727566] pci_bus 0000:00: root bus resource [mem 0x600000000-0x7ffffffff pref]
[    3.739252] pci 0000:00:00.0: PCI bridge to [bus 01-0c]
[    3.744948] xilinx-dpdma fd4c0000.dma: Xilinx DPDMA engine is probed
[    3.751524] xilinx-zynqmp-dma fd500000.dma: ZynqMP DMA driver Probe success
[    3.758626] xilinx-zynqmp-dma fd510000.dma: ZynqMP DMA driver Probe success
[    3.765723] xilinx-zynqmp-dma fd520000.dma: ZynqMP DMA driver Probe success
[    3.772826] xilinx-zynqmp-dma fd530000.dma: ZynqMP DMA driver Probe success
[    3.779922] xilinx-zynqmp-dma fd540000.dma: ZynqMP DMA driver Probe success
[    3.787029] xilinx-zynqmp-dma fd550000.dma: ZynqMP DMA driver Probe success
[    3.794129] xilinx-zynqmp-dma fd560000.dma: ZynqMP DMA driver Probe success
[    3.801230] xilinx-zynqmp-dma fd570000.dma: ZynqMP DMA driver Probe success
[    3.808401] xilinx-zynqmp-dma ffa80000.dma: ZynqMP DMA driver Probe success
[    3.815501] xilinx-zynqmp-dma ffa90000.dma: ZynqMP DMA driver Probe success
[    3.822602] xilinx-zynqmp-dma ffaa0000.dma: ZynqMP DMA driver Probe success
[    3.829702] xilinx-zynqmp-dma ffab0000.dma: ZynqMP DMA driver Probe success
[    3.836807] xilinx-zynqmp-dma ffac0000.dma: ZynqMP DMA driver Probe success
[    3.843912] xilinx-zynqmp-dma ffad0000.dma: ZynqMP DMA driver Probe success
[    3.851017] xilinx-zynqmp-dma ffae0000.dma: ZynqMP DMA driver Probe success
[    3.858125] xilinx-zynqmp-dma ffaf0000.dma: ZynqMP DMA driver Probe success
[    3.865368] xilinx-psgtr fd400000.zynqmp_phy: Lane:1 type:8 protocol:4 pll_locked:yes
[    3.875338] xilinx-dp-snd-codec fd4a0000.zynqmp-display:zynqmp_dp_snd_codec0: Xilinx DisplayPort Sound Codec probed
[    3.886010] xilinx-dp-snd-pcm zynqmp_dp_snd_pcm0: Xilinx DisplayPort Sound PCM probed
[    3.894052] xilinx-dp-snd-pcm zynqmp_dp_snd_pcm1: Xilinx DisplayPort Sound PCM probed
[    3.902724] xilinx-dp-snd-card fd4a0000.zynqmp-display:zynqmp_dp_snd_card: xilinx-dp-snd-codec-dai <-> xilinx-dp-snd-codec-dai mapping ok
[    3.915165] xilinx-dp-snd-card fd4a0000.zynqmp-display:zynqmp_dp_snd_card: xilinx-dp-snd-codec-dai <-> xilinx-dp-snd-codec-dai mapping ok
[    3.927840] xilinx-dp-snd-card fd4a0000.zynqmp-display:zynqmp_dp_snd_card: Xilinx DisplayPort Sound Card probed
[    3.938025] OF: graph: no port node found in /amba/zynqmp-display@fd4a0000
[    3.945044] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.951651] [drm] No driver support for vblank timestamp query.
[    3.957623] xlnx-drm xlnx-drm.0: bound fd4a0000.zynqmp-display (ops 0xffffff8008bcf5e0)
[    5.045556] [drm] Cannot find any crtc or sizes
[    5.050358] [drm] Initialized xlnx 1.0.0 20130509 for fd4a0000.zynqmp-display on minor 0
[    5.058463] zynqmp-display fd4a0000.zynqmp-display: ZynqMP DisplayPort Subsystem driver probed
[    5.067429] xilinx-psgtr fd400000.zynqmp_phy: Lane:3 type:3 protocol:2 pll_locked:yes
[    5.075310] ahci-ceva fd0c0000.ahci: AHCI 0001.0301 32 slots 2 ports 6 Gbps 0x3 impl platform mode
[    5.084265] ahci-ceva fd0c0000.ahci: flags: 64bit ncq sntf pm clo only pmp fbs pio slum part ccc sds apst
[    5.094678] scsi host0: ahci-ceva
[    5.098241] scsi host1: ahci-ceva
[    5.101696] ata1: SATA max UDMA/133 mmio [mem 0xfd0c0000-0xfd0c1fff] port 0x100 irq 45
[    5.109611] ata2: SATA max UDMA/133 mmio [mem 0xfd0c0000-0xfd0c1fff] port 0x180 irq 45
[    5.118660] m25p80 spi0.0: n25q512a (131072 Kbytes)
[    5.123553] 3 fixed-partitions partitions found on MTD device spi0.0
[    5.129895] Creating 3 MTD partitions on "spi0.0":
[    5.134680] 0x000000000000-0x000001e00000 : "boot"
[    5.139933] 0x000001e00000-0x000001e40000 : "bootenv"
[    5.145384] 0x000001e40000-0x000004240000 : "kernel"
[    5.152737] macb ff0e0000.ethernet: Not enabling partial store and forward
[    5.160098] libphy: MACB_mii_bus: probed
[    5.168453] TI DP83867 ff0e0000.ethernet-ffffffff:0c: attached PHY driver [TI DP83867] (mii_bus:phy_addr=ff0e0000.ethernet-ffffffff:0c, irq=POLL)
[    5.181497] macb ff0e0000.ethernet eth0: Cadence GEM rev 0x50070106 at 0xff0e0000 irq 30 (00:0a:35:00:22:01)
[    5.191682] xilinx-axipmon ffa00000.perf-monitor: Probed Xilinx APM
[    5.198235] xilinx-axipmon fd0b0000.perf-monitor: Probed Xilinx APM
[    5.204720] xilinx-axipmon fd490000.perf-monitor: Probed Xilinx APM
[    5.211213] xilinx-axipmon ffa10000.perf-monitor: Probed Xilinx APM
[    5.219022] dwc3 fe200000.dwc3: Failed to get clk 'ref': -2
[    5.224873] xilinx-psgtr fd400000.zynqmp_phy: Lane:2 type:0 protocol:3 pll_locked:yes
[    5.232940] xhci-hcd xhci-hcd.0.auto: xHCI Host Controller
[    5.238429] xhci-hcd xhci-hcd.0.auto: new USB bus registered, assigned bus number 1
[    5.246410] xhci-hcd xhci-hcd.0.auto: hcc params 0x0238f625 hci version 0x100 quirks 0x0000000202010810
[    5.255816] xhci-hcd xhci-hcd.0.auto: irq 54, io mem 0xfe200000
[    5.261927] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.19
[    5.270197] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.277412] usb usb1: Product: xHCI Host Controller
[    5.282280] usb usb1: Manufacturer: Linux 4.19.0-xilinx-v2019.1 xhci-hcd
[    5.288973] usb usb1: SerialNumber: xhci-hcd.0.auto
[    5.294195] hub 1-0:1.0: USB hub found
[    5.297960] hub 1-0:1.0: 1 port detected
[    5.302056] xhci-hcd xhci-hcd.0.auto: xHCI Host Controller
[    5.307541] xhci-hcd xhci-hcd.0.auto: new USB bus registered, assigned bus number 2
[    5.315197] xhci-hcd xhci-hcd.0.auto: Host supports USB 3.0  SuperSpeed
[    5.321919] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 4.19
[    5.330179] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.337396] usb usb2: Product: xHCI Host Controller
[    5.342265] usb usb2: Manufacturer: Linux 4.19.0-xilinx-v2019.1 xhci-hcd
[    5.348957] usb usb2: SerialNumber: xhci-hcd.0.auto
[    5.354066] hub 2-0:1.0: USB hub found
[    5.357823] hub 2-0:1.0: 1 port detected
[    5.362888] pca953x 0-0020: 0-0020 supply vcc not found, using dummy regulator
[    5.370140] pca953x 0-0020: Linked as a consumer to regulator.0
[    5.376723] pca953x 0-0021: 0-0021 supply vcc not found, using dummy regulator
[    5.383971] pca953x 0-0021: Linked as a consumer to regulator.0
[    5.391271] ina2xx 3-0040: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.398057] ina2xx 3-0041: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.404843] ina2xx 3-0042: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.411633] ina2xx 3-0043: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.418414] ina2xx 3-0044: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.425200] ina2xx 3-0045: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.431745] ata2: SATA link down (SStatus 0 SControl 330)
[    5.431986] ina2xx 3-0046: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.437162] ata1: SATA link down (SStatus 0 SControl 330)
[    5.449060] ina2xx 3-0047: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.455843] ina2xx 3-004a: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.462636] ina2xx 3-004b: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.469012] i2c i2c-0: Added multiplexed i2c bus 3
[    5.474430] ina2xx 4-0040: power monitor ina226 (Rshunt = 2000 uOhm)
[    5.481216] ina2xx 4-0041: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.488007] ina2xx 4-0042: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.494792] ina2xx 4-0043: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.501594] ina2xx 4-0044: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.508381] ina2xx 4-0045: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.515170] ina2xx 4-0046: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.521963] ina2xx 4-0047: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.528344] i2c i2c-0: Added multiplexed i2c bus 4
[    5.551365] random: fast init done
[    5.569797] i2c i2c-0: Added multiplexed i2c bus 5
[    5.574718] i2c i2c-0: Added multiplexed i2c bus 6
[    5.579509] pca954x 0-0075: registered 4 multiplexed busses for I2C mux pca9544
[    5.586840] cdns-i2c ff020000.i2c: 400 kHz mmio ff020000 irq 32
[    5.594521] at24 7-0054: 1024 byte 24c08 EEPROM, writable, 1 bytes/write
[    5.601246] i2c i2c-1: Added multiplexed i2c bus 7
[    5.606241] i2c i2c-1: Added multiplexed i2c bus 8
[    5.613094] si570 9-005d: registered, current frequency 300000000 Hz
[    5.619468] i2c i2c-1: Added multiplexed i2c bus 9
[    5.637550] si570 10-005d: registered, current frequency 148500000 Hz
[    5.644017] i2c i2c-1: Added multiplexed i2c bus 10
[    5.649095] si5324 11-0069: si5328 probed
[    5.714905] si5324 11-0069: si5328 probe successful
[    5.719811] i2c i2c-1: Added multiplexed i2c bus 11
[    5.724825] i2c i2c-1: Added multiplexed i2c bus 12
[    5.729825] i2c i2c-1: Added multiplexed i2c bus 13
[    5.734818] i2c i2c-1: Added multiplexed i2c bus 14
[    5.739698] pca954x 1-0074: registered 8 multiplexed busses for I2C switch pca9548
[    5.747609] i2c i2c-1: Added multiplexed i2c bus 15
[    5.752614] i2c i2c-1: Added multiplexed i2c bus 16
[    5.757634] i2c i2c-1: Added multiplexed i2c bus 17
[    5.763024] i2c i2c-1: Added multiplexed i2c bus 18
[    5.768031] i2c i2c-1: Added multiplexed i2c bus 19
[    5.773041] i2c i2c-1: Added multiplexed i2c bus 20
[    5.778051] i2c i2c-1: Added multiplexed i2c bus 21
[    5.783059] i2c i2c-1: Added multiplexed i2c bus 22
[    5.787937] pca954x 1-0075: registered 8 multiplexed busses for I2C switch pca9548
[    5.795528] cdns-i2c ff030000.i2c: 400 kHz mmio ff030000 irq 33
[    5.802048] cdns-wdt fd4d0000.watchdog: Xilinx Watchdog Timer at (____ptrval____) with timeout 60s
[    5.811278] cdns-wdt ff150000.watchdog: Xilinx Watchdog Timer at (____ptrval____) with timeout 10s
[    5.820519] cpufreq: cpufreq_online: CPU0: Running at unlisted freq: 1199880 KHz
[    5.827959] cpufreq: cpufreq_online: CPU0: Unlisted initial frequency changed to: 1199999 KHz
[    5.868648] mmc0: SDHCI controller on ff170000.mmc [ff170000.mmc] using ADMA 64-bit
[    5.884269] input: gpio-keys as /devices/platform/gpio-keys/input/input0
[    5.891206] rtc_zynqmp ffa60000.rtc: setting system clock to 2021-07-19 02:28:44 UTC (1626661724)
[    5.900079] of_cfs_init
[    5.902548] of_cfs_init: OK
[    5.905450] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    5.925327] mmc0: new high speed SDHC card at address e624
[    5.931339] mmcblk0: mmc0:e624 SL16G 14.8 GiB
[    5.941198]  mmcblk0: p1
[    6.049721] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[    6.056246] clk: Not disabling unused clocks
[    6.060513] ALSA device list:
[    6.063469]   #0: DisplayPort monitor
[    6.067374] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[    6.075987] cfg80211: failed to load regulatory.db
[    6.080967] Freeing unused kernel memory: 832K
[    6.101567] Run /init as init process
INIT: version 2.88 booting
[    6.161576] [drm] Cannot find any crtc or sizes
Starting udev
[    6.223477] udevd[1986]: starting version 3.2.5
[    6.228294] random: udevd: uninitialized urandom read (16 bytes read)
[    6.234787] random: udevd: uninitialized urandom read (16 bytes read)
[    6.241279] random: udevd: uninitialized urandom read (16 bytes read)
[    6.251803] udevd[1987]: starting eudev-3.2.5
[    6.711624] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Mon Jul 19 02:32:37 UTC 2021
Configuring packages on first boot....
 (This may take several minutes. Please do not power off the machine.)
Running postinst /etc/rpm-postinsts/100-sysvinit-inittab...
update-rc.d: /etc/init.d/run-postinsts exists during rc.d purge (continuing)
INIT: Entering runlevel: 5
Configuring network interfaces... [    7.124019] pps pps0: new PPS source ptp0
[    7.128042] macb ff0e0000.ethernet: gem-ptp-timer ptp clock registered.
[    7.134748] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
udhcpc: started, v1.29.2
udhcpc: sending discover
udhcpc: sending discover
udhcpc: sending discover
udhcpc: no lease, forking to background
done.
Starting Dropbear SSH server: [   16.328425] urandom_read: 5 callbacks suppressed
[   16.328430] random: dropbearkey: uninitialized urandom read (32 bytes read)
[   16.342708] random: dropbearkey: uninitialized urandom read (32 bytes read)
Generating 2048 bit rsa key, this may take a while...
Public key portion is:
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCo4ZuAqs3czDyhKFkOOgz/cy4RlPHgHghy1ARKAowRMADldYx7PpYx7PpDFKSwsFrdDbX0jjlVRYCN6NYOr8fhh5sbghEPFysQTm9WMRtnAHt3W
kU75AdLxKg0g9dj4facUiEJR2NXki+eVZEM7KgSe36PW8H+MXlGAB6WY3sh2gT7pXu9mnJ5gUKo5QSwiBgy3t18k1ILJfS1fHV4RaaMCTj8bPIbeKojGZGxHxq/EVM4Ykm2jn0UOZpD8mVsCo46ON
cGW62zWEQzszvsvvN+i6z115vERvEQGWeBulyYyff4X2uBZgyZkTnoMSRnHv3AxCpGckzsdl15m7hP0Xzx root@xilinx-zcu102-2019_1
Fingerprint: sha1!! 86:31:f0:cf:2e:d0:6e:8a:82:42:17:03:b0:81:b1:76:cd:f3:d1:9f
dropbear.
Starting internet superserver: inetd.
Starting syslogd/klogd: done
Starting tcf-agent: OK

PetaLinux 2019.1 xilinx-zcu102-2019_1 /dev/ttyPS0

xilinx-zcu102-2019_1 login:
```

**<u><span>References</span></u>**

The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]