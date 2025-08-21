# Successful 2019.1 PetaLinux Linux kernel JTAG Boot Log

![Xilinx_logo](Xilinx_logo.png)

This post lists a successful JTAG boot of the Linux kernel. This can be useful if a build doesn't boot and a developer is trying to figure out why. The developer can compare the last message printed with the log to get a clue on what isn't working.

**<u><span>Launched With</span></u>**

```
petalinux-boot --jtag --kernel -v --hw_server-url 10.0.0.2:3121
```

**<u><span>Load and Run Log</span></u>**

```
INFO: sourcing build tools
XSDB Script:
INFO: Launching XSDB for file download and boot.

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
puts stderr "INFO: Loading image: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/Image at 0x00080000"
dow -data "/home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/Image" 0x00080000
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Loading image: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/system.dtb at 0x1407f000"
dow -data "/home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/system.dtb" 0x1407f000
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/build/misc/linux-boot/linux-boot.elf to the target."
dow "/home/demo/plxprjs/xilinx-zcu102-2019.1/build/misc/linux-boot/linux-boot.elf"
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf to the target."
dow "/home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/bl31.elf"
after 2000
con
exit
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
100%    0MB   0.6MB/s  00:00    
Setting PC to Program Start Address 0xfffc0000
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/zynqmp_fsbl.elf
INFO: Loading image: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/Image at 0x00080000
100%   32MB   0.8MB/s  00:40    
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/Image
INFO: Loading image: /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/system.dtb at 0x1407f000
100%    0MB   0.8MB/s  00:00    
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/images/linux/system.dtb
INFO: Downloading ELF file: /home/demo/plxprjs/xilinx-zcu102-2019.1/build/misc/linux-boot/linux-boot.elf to the target.
Downloading Program -- /home/demo/plxprjs/xilinx-zcu102-2019.1/build/misc/linux-boot/linux-boot.elf
	section, .text: 0x10080000 - 0x10080027
100%    0MB   0.0MB/s  00:00    
Setting PC to Program Start Address 0x10080000
Successfully downloaded /home/demo/plxprjs/xilinx-zcu102-2019.1/build/misc/linux-boot/linux-boot.elf
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

**<u><span>Log</span></u>**

```
Xilinx Zynq MP First Stage Boot Loader
Release 2019.1   Jan 28 2021  -  08:16:00
NOTICE:  ATF running on XCZU9EG/silicon v3/RTL5.1 at 0xfffea000
NOTICE:  BL31: Secure code at 0x60000000
NOTICE:  BL31: Non secure code at 0x10080000
NOTICE:  BL31: v2.0(release):xilinx-v2018.3-720-g80d1c790
NOTICE:  BL31: Built : 21:11:59, May 15 2021
[    0.000000] Booting Linux on physical CPU 0x0000000000 [0x410fd034]
[    0.000000] Linux version 4.19.0-xilinx-v2019.1 (oe-user@oe-host) (gcc version 8.2.0 (GCC)) #1 SMP Thu Jan 28 08:1
4:00 UTC 2021
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
[    0.000000] Kernel command line: earlycon console=ttyPS0,115200 clk_ignore_unused cpuidle.off=1
[    0.000000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.000000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000000] software IO TLB: mapped [mem 0x6bc00000-0x6fc00000] (64MB)
[    0.000000] Memory: 3767016K/4193280K available (10812K kernel code, 636K rwdata, 5428K rodata, 16512K init, 316K
bss, 164120K reserved, 262144K cma-reserved)
[    0.000000] rcu: Hierarchical RCU implementation.
[    0.000000] rcu:     RCU event tracing is enabled.
[    0.000000] rcu:     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS: 64, nr_irqs: 64, preallocated irqs: 0
[    0.000000] GIC: Adjusting CPU interface base to 0x00000000f902f000
[    0.000000] GIC: Using split EOI/Deactivate mode
[    0.000000] arch_timer: cp15 timer(s) running at 99.99MHz (phys).
[    0.000000] clocksource: arch_sys_counter: mask: 0xffffffffffffff max_cycles: 0x170f8de2d3, max_idle_ns: 440795206
112 ns
[    0.000003] sched_clock: 56 bits at 99MHz, resolution 10ns, wraps every 4398046511101ns
[    0.008155] Console: colour dummy device 80x25
[    0.012293] Calibrating delay loop (skipped), value calculated using timer frequency.. 199.98 BogoMIPS (lpj=399960
)
[    0.022572] pid_max: default: 32768 minimum: 301
[    0.027224] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.033737] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.041452] ASID allocator initialised with 32768 entries
[    0.046133] rcu: Hierarchical SRCU implementation.
[    0.051104] EFI services will not be available.
[    0.055375] smp: Bringing up secondary CPUs ...
[    0.143967] Detected VIPT I-cache on CPU1
[    0.143995] CPU1: Booted secondary processor 0x0000000001 [0x410fd034]
[    0.245630] Detected VIPT I-cache on CPU2
[    0.245649] CPU2: Booted secondary processor 0x0000000002 [0x410fd034]
[    0.347400] Detected VIPT I-cache on CPU3
[    0.347419] CPU3: Booted secondary processor 0x0000000003 [0x410fd034]
[    0.347464] smp: Brought up 1 node, 4 CPUs
[    0.377080] SMP: Total of 4 processors activated.
[    0.381716] CPU features: detected: 32-bit EL0 Support
[    0.388408] CPU: All CPU(s) started at EL2
[    0.390820] alternatives: patching kernel code
[    0.396025] devtmpfs: initialized
[    0.403030] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.408069] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.419610] xor: measuring software checksum speed
[    0.458214]    8regs     :  2375.000 MB/sec
[    0.498242]    8regs_prefetch:  2052.000 MB/sec
[    0.538272]    32regs    :  2724.000 MB/sec
[    0.578301]    32regs_prefetch:  2308.000 MB/sec
[    0.578330] xor: using function: 32regs (2724.000 MB/sec)
[    0.582615] pinctrl core: initialized pinctrl subsystem
[    0.588351] NET: Registered protocol family 16
[    0.592380] audit: initializing netlink subsys (disabled)
[    0.597515] audit: type=2000 audit(0.548:1): state=initialized audit_enabled=0 res=1
[    0.605092] vdso: 2 pages (1 code @ (____ptrval____), 1 data @ (____ptrval____))
[    0.605096] hw-breakpoint: found 6 breakpoint and 4 watchpoint registers.
[    0.619731] DMA: preallocated 256 KiB pool for atomic allocations
[    0.638899] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
[    0.707991] raid6: int64x1  gen()   446 MB/s
[    0.775941] raid6: int64x1  xor()   453 MB/s
[    0.844043] raid6: int64x2  gen()   681 MB/s
[    0.912022] raid6: int64x2  xor()   600 MB/s
[    0.980085] raid6: int64x4  gen()   981 MB/s
[    1.048124] raid6: int64x4  xor()   737 MB/s
[    1.116158] raid6: int64x8  gen()  1163 MB/s
[    1.184203] raid6: int64x8  xor()   759 MB/s
[    1.252316] raid6: neonx1   gen()   736 MB/s
[    1.320306] raid6: neonx1   xor()   880 MB/s
[    1.388392] raid6: neonx2   gen()  1128 MB/s
[    1.456407] raid6: neonx2   xor()  1173 MB/s
[    1.524466] raid6: neonx4   gen()  1481 MB/s
[    1.592495] raid6: neonx4   xor()  1418 MB/s
[    1.660552] raid6: neonx8   gen()  1540 MB/s
[    1.728578] raid6: neonx8   xor()  1459 MB/s
[    1.728605] raid6: using algorithm neonx8 gen() 1540 MB/s
[    1.732538] raid6: .... xor() 1459 MB/s, rmw enabled
[    1.737430] raid6: using neon recovery algorithm
[    1.742676] SCSI subsystem initialized
[    1.745844] usbcore: registered new interface driver usbfs
[    1.751107] usbcore: registered new interface driver hub
[    1.756335] usbcore: registered new device driver usb
[    1.761346] media: Linux media interface: v0.10
[    1.765772] videodev: Linux video capture interface: v2.00
[    1.771175] pps_core: LinuxPPS API ver. 1 registered
[    1.776044] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.785063] PTP clock support registered
[    1.788931] EDAC MC: Ver: 3.0.0
[    1.792381] zynqmp-ipi-mbox mailbox@ff990400: Probed ZynqMP IPI Mailbox driver.
[    1.799461] FPGA manager framework
[    1.802714] Advanced Linux Sound Architecture Driver Initialized.
[    1.808836] Bluetooth: Core ver 2.22
[    1.812099] NET: Registered protocol family 31
[    1.816460] Bluetooth: HCI device and connection manager initialized
[    1.822726] Bluetooth: HCI socket layer initialized
[    1.827530] Bluetooth: L2CAP socket layer initialized
[    1.832522] Bluetooth: SCO socket layer initialized
[    1.837622] clocksource: Switched to clocksource arch_sys_counter
[    1.843412] VFS: Disk quotas dquot_6.6.0
[    1.847218] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.858759] NET: Registered protocol family 2
[    1.859138] tcp_listen_portaddr_hash hash table entries: 2048 (order: 3, 32768 bytes)
[    1.866026] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    1.873295] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    1.879991] TCP: Hash tables configured (established 32768 bind 32768)
[    1.886111] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.892042] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.898465] NET: Registered protocol family 1
[    1.902828] RPC: Registered named UNIX socket transport module.
[    1.908453] RPC: Registered udp transport module.
[    1.913095] RPC: Registered tcp transport module.
[    1.917714] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    1.974909] hw perfevents: no interrupt-affinity property for /pmu, guessing.
[    1.976528] hw perfevents: enabled with armv8_pmuv3 PMU driver, 7 counters available
[    1.984914] Initialise system trusted keyrings
[    1.988491] workingset: timestamp_bits=62 max_order=20 bucket_order=0
[    1.995489] NFS: Registering the id_resolver key type
[    1.999762] Key type id_resolver registered
[    2.003852] Key type id_legacy registered
[    2.007803] nfs4filelayout_init: NFSv4 File Layout Driver Registering...
[    2.014417] jffs2: version 2.2. (NAND) � 2001-2006 Red Hat, Inc.
[    3.108146] NET: Registered protocol family 38
[    3.168986] Key type asymmetric registered
[    3.169014] Asymmetric key parser 'x509' registered
[    3.172302] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 247)
[    3.179558] io scheduler noop registered
[    3.183416] io scheduler deadline registered
[    3.187646] io scheduler cfq registered (default)
[    3.192255] io scheduler mq-deadline registered
[    3.196716] io scheduler kyber registered
[    3.228266] Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled
[    3.232140] cacheinfo: Unable to detect cache hierarchy for CPU 0
[    3.239044] brd: module loaded
[    3.242857] loop: module loaded
[    3.243665] mtdoops: mtd device (mtddev=name/number) must be supplied
[    3.248641] libphy: Fixed MDIO Bus: probed
[    3.252615] tun: Universal TUN/TAP device driver, 1.6
[    3.256549] CAN device driver interface
[    3.261085] usbcore: registered new interface driver asix
[    3.265567] usbcore: registered new interface driver ax88179_178a
[    3.271561] usbcore: registered new interface driver cdc_ether
[    3.277308] usbcore: registered new interface driver net1080
[    3.282883] usbcore: registered new interface driver cdc_subset
[    3.288717] usbcore: registered new interface driver zaurus
[    3.294219] usbcore: registered new interface driver cdc_ncm
[    3.300241] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.306202] ehci-pci: EHCI PCI platform driver
[    3.310831] usbcore: registered new interface driver uas
[    3.315843] usbcore: registered new interface driver usb-storage
[    3.322242] rtc_zynqmp ffa60000.rtc: rtc core: registered ffa60000.rtc as rtc0
[    3.328906] i2c /dev entries driver
[    3.333839] usbcore: registered new interface driver uvcvideo
[    3.337951] USB Video Class driver (1.1.1)
[    3.342511] Bluetooth: HCI UART driver ver 2.3
[    3.346365] Bluetooth: HCI UART protocol H4 registered
[    3.351422] Bluetooth: HCI UART protocol BCSP registered
[    3.356676] Bluetooth: HCI UART protocol LL registered
[    3.361718] Bluetooth: HCI UART protocol ATH3K registered
[    3.367055] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.373256] Bluetooth: HCI UART protocol Intel registered
[    3.378554] Bluetooth: HCI UART protocol QCA registered
[    3.383715] usbcore: registered new interface driver bcm203x
[    3.389298] usbcore: registered new interface driver bpa10x
[    3.394782] usbcore: registered new interface driver bfusb
[    3.400188] usbcore: registered new interface driver btusb
[    3.405567] Bluetooth: Generic Bluetooth SDIO driver ver 0.1
[    3.411193] usbcore: registered new interface driver ath3k
[    3.416669] EDAC MC: ECC not enabled
[    3.420299] EDAC DEVICE0: Giving out device to module zynqmp-ocm-edac controller zynqmp_ocm: DEV ff960000.memory-c
ontroller (INTERRUPT)
[    3.432376] CPUidle arm: Failed to register cpuidle driver
[    3.437663] sdhci: Secure Digital Host Controller Interface driver
[    3.443579] sdhci: Copyright(c) Pierre Ossman
[    3.447868] sdhci-pltfm: SDHCI platform and OF driver helper
[    3.453772] ledtrig-cpu: registered to indicate activity on CPUs
[    3.459413] zynqmp_firmware_probe Platform Management API v1.1
[    3.465120] zynqmp_firmware_probe Trustzone version v1.0
[    3.472925] zynqmp-pinctrl firmware:zynqmp-firmware:pinctrl: zynqmp pinctrl initialized
[    3.499581] zynqmp_clk_mux_get_parent() getparent failed for clock: lpd_wdt, ret = -22
[    3.502269] alg: No test for xilinx-zynqmp-aes (zynqmp-aes)
[    3.507335] zynqmp_aes zynqmp_aes: AES Successfully Registered
[    3.507335]
[    3.514788] alg: No test for xilinx-keccak-384 (zynqmp-keccak-384)
[    3.520870] alg: No test for xilinx-zynqmp-rsa (zynqmp-rsa)
[    3.526411] usbcore: registered new interface driver usbhid
[    3.531692] usbhid: USB HID core driver
[    3.537693] fpga_manager fpga0: Xilinx ZynqMP FPGA Manager registered
[    3.542181] usbcore: registered new interface driver snd-usb-audio
[    3.548759] pktgen: Packet Generator for packet performance testing. Version: 2.75
[    3.555748] Initializing XFRM netlink socket
[    3.559651] NET: Registered protocol family 10
[    3.564300] Segment Routing with IPv6
[    3.567643] sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
[    3.573727] NET: Registered protocol family 17
[    3.577778] NET: Registered protocol family 15
[    3.582155] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load
br_netfilter if you need this.
[    3.594965] can: controller area network core (rev 20170425 abi 9)
[    3.601048] NET: Registered protocol family 29
[    3.605399] can: raw protocol (rev 20170425)
[    3.609602] can: broadcast manager protocol (rev 20170425 t)
[    3.615182] can: netlink gateway (rev 20170425) max_hops=1
[    3.620823] Bluetooth: RFCOMM TTY layer initialized
[    3.625398] Bluetooth: RFCOMM socket layer initialized
[    3.630463] Bluetooth: RFCOMM ver 1.11
[    3.634149] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.639377] Bluetooth: BNEP filters: protocol multicast
[    3.644528] Bluetooth: BNEP socket layer initialized
[    3.649417] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[    3.655253] Bluetooth: HIDP socket layer initialized
[    3.660256] 9pnet: Installing 9P2000 support
[    3.664364] Key type dns_resolver registered
[    3.668944] registered taskstats version 1
[    3.672591] Loading compiled-in X.509 certificates
[    3.677626] Btrfs loaded, crc32c=crc32c-generic
[    3.687959] ff000000.serial: ttyPS0 at MMIO 0xff000000 (irq = 47, base_baud =��r���console [ttyPS0] enabled
[    3.696833] console [ttyPS0] enabled
[    3.700423] bootconsole [cdns0] disabled
[    3.700423] bootconsole [cdns0] disabled
[    3.708610] ff010000.serial: ttyPS1 at MMIO 0xff010000 (irq = 48, base_baud = 6249375) is a xuartps
[    3.721902] of-fpga-region fpga-full: FPGA Region probed
[    3.727804] nwl-pcie fd0e0000.pcie: Link is DOWN
[    3.732447] nwl-pcie fd0e0000.pcie: host bridge /amba/pcie@fd0e0000 ranges:
[    3.739416] nwl-pcie fd0e0000.pcie:   MEM 0xe0000000..0xefffffff -> 0xe0000000
[    3.746637] nwl-pcie fd0e0000.pcie:   MEM 0x600000000..0x7ffffffff -> 0x600000000
[    3.754221] nwl-pcie fd0e0000.pcie: PCI host bridge to bus 0000:00
[    3.760395] pci_bus 0000:00: root bus resource [bus 00-ff]
[    3.765878] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xefffffff]
[    3.772747] pci_bus 0000:00: root bus resource [mem 0x600000000-0x7ffffffff pref]
[    3.783990] pci 0000:00:00.0: PCI bridge to [bus 01-0c]
[    3.789693] xilinx-dpdma fd4c0000.dma: Xilinx DPDMA engine is probed
[    3.796264] xilinx-zynqmp-dma fd500000.dma: ZynqMP DMA driver Probe success
[    3.803370] xilinx-zynqmp-dma fd510000.dma: ZynqMP DMA driver Probe success
[    3.810471] xilinx-zynqmp-dma fd520000.dma: ZynqMP DMA driver Probe success
[    3.817570] xilinx-zynqmp-dma fd530000.dma: ZynqMP DMA driver Probe success
[    3.824673] xilinx-zynqmp-dma fd540000.dma: ZynqMP DMA driver Probe success
[    3.831771] xilinx-zynqmp-dma fd550000.dma: ZynqMP DMA driver Probe success
[    3.838875] xilinx-zynqmp-dma fd560000.dma: ZynqMP DMA driver Probe success
[    3.845973] xilinx-zynqmp-dma fd570000.dma: ZynqMP DMA driver Probe success
[    3.853146] xilinx-zynqmp-dma ffa80000.dma: ZynqMP DMA driver Probe success
[    3.860249] xilinx-zynqmp-dma ffa90000.dma: ZynqMP DMA driver Probe success
[    3.867348] xilinx-zynqmp-dma ffaa0000.dma: ZynqMP DMA driver Probe success
[    3.874448] xilinx-zynqmp-dma ffab0000.dma: ZynqMP DMA driver Probe success
[    3.881549] xilinx-zynqmp-dma ffac0000.dma: ZynqMP DMA driver Probe success
[    3.888652] xilinx-zynqmp-dma ffad0000.dma: ZynqMP DMA driver Probe success
[    3.895751] xilinx-zynqmp-dma ffae0000.dma: ZynqMP DMA driver Probe success
[    3.902855] xilinx-zynqmp-dma ffaf0000.dma: ZynqMP DMA driver Probe success
[    3.910088] xilinx-psgtr fd400000.zynqmp_phy: Lane:1 type:8 protocol:4 pll_locked:yes
[    3.920044] xilinx-dp-snd-codec fd4a0000.zynqmp-display:zynqmp_dp_snd_codec0: Xilinx DisplayPort Sound Codec probe
d
[    3.930720] xilinx-dp-snd-pcm zynqmp_dp_snd_pcm0: Xilinx DisplayPort Sound PCM probed
[    3.938742] xilinx-dp-snd-pcm zynqmp_dp_snd_pcm1: Xilinx DisplayPort Sound PCM probed
[    3.947182] xilinx-dp-snd-card fd4a0000.zynqmp-display:zynqmp_dp_snd_card: xilinx-dp-snd-codec-dai <-> xilinx-dp-s
nd-codec-dai mapping ok
[    3.959625] xilinx-dp-snd-card fd4a0000.zynqmp-display:zynqmp_dp_snd_card: xilinx-dp-snd-codec-dai <-> xilinx-dp-s
nd-codec-dai mapping ok
[    3.972304] xilinx-dp-snd-card fd4a0000.zynqmp-display:zynqmp_dp_snd_card: Xilinx DisplayPort Sound Card probed
[    3.982490] OF: graph: no port node found in /amba/zynqmp-display@fd4a0000
[    3.989495] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.996103] [drm] No driver support for vblank timestamp query.
[    4.002077] xlnx-drm xlnx-drm.0: bound fd4a0000.zynqmp-display (ops 0xffffff8008bcf5e0)
[    5.089631] [drm] Cannot find any crtc or sizes
[    5.094375] [drm] Initialized xlnx 1.0.0 20130509 for fd4a0000.zynqmp-display on minor 0
[    5.102481] zynqmp-display fd4a0000.zynqmp-display: ZynqMP DisplayPort Subsystem driver probed
[    5.111437] xilinx-psgtr fd400000.zynqmp_phy: Lane:3 type:3 protocol:2 pll_locked:yes
[    5.119318] ahci-ceva fd0c0000.ahci: AHCI 0001.0301 32 slots 2 ports 6 Gbps 0x3 impl platform mode
[    5.128275] ahci-ceva fd0c0000.ahci: flags: 64bit ncq sntf pm clo only pmp fbs pio slum part ccc sds apst
[    5.138713] scsi host0: ahci-ceva
[    5.142299] scsi host1: ahci-ceva
[    5.145751] ata1: SATA max UDMA/133 mmio [mem 0xfd0c0000-0xfd0c1fff] port 0x100 irq 45
[    5.153663] ata2: SATA max UDMA/133 mmio [mem 0xfd0c0000-0xfd0c1fff] port 0x180 irq 45
[    5.162685] m25p80 spi0.0: n25q512a (131072 Kbytes)
[    5.167584] 3 fixed-partitions partitions found on MTD device spi0.0
[    5.173932] Creating 3 MTD partitions on "spi0.0":
[    5.178716] 0x000000000000-0x000001e00000 : "boot"
[    5.183963] 0x000001e00000-0x000001e40000 : "bootenv"
[    5.189399] 0x000001e40000-0x000004240000 : "kernel"
[    5.196738] macb ff0e0000.ethernet: Not enabling partial store and forward
[    5.204112] libphy: MACB_mii_bus: probed
[    5.212423] TI DP83867 ff0e0000.ethernet-ffffffff:0c: attached PHY driver [TI DP83867] (mii_bus:phy_addr=ff0e0000.
ethernet-ffffffff:0c, irq=POLL)
[    5.225471] macb ff0e0000.ethernet eth0: Cadence GEM rev 0x50070106 at 0xff0e0000 irq 30 (00:0a:35:00:22:01)
[    5.235647] xilinx-axipmon ffa00000.perf-monitor: Probed Xilinx APM
[    5.242175] xilinx-axipmon fd0b0000.perf-monitor: Probed Xilinx APM
[    5.248663] xilinx-axipmon fd490000.perf-monitor: Probed Xilinx APM
[    5.255136] xilinx-axipmon ffa10000.perf-monitor: Probed Xilinx APM
[    5.263127] dwc3 fe200000.dwc3: Failed to get clk 'ref': -2
[    5.268975] xilinx-psgtr fd400000.zynqmp_phy: Lane:2 type:0 protocol:3 pll_locked:yes
[    5.277136] xhci-hcd xhci-hcd.0.auto: xHCI Host Controller
[    5.282628] xhci-hcd xhci-hcd.0.auto: new USB bus registered, assigned bus number 1
[    5.290623] xhci-hcd xhci-hcd.0.auto: hcc params 0x0238f625 hci version 0x100 quirks 0x0000000202010810
[    5.300038] xhci-hcd xhci-hcd.0.auto: irq 54, io mem 0xfe200000
[    5.306162] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.19
[    5.314427] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.321645] usb usb1: Product: xHCI Host Controller
[    5.326515] usb usb1: Manufacturer: Linux 4.19.0-xilinx-v2019.1 xhci-hcd
[    5.333206] usb usb1: SerialNumber: xhci-hcd.0.auto
[    5.338349] hub 1-0:1.0: USB hub found
[    5.342110] hub 1-0:1.0: 1 port detected
[    5.346222] xhci-hcd xhci-hcd.0.auto: xHCI Host Controller
[    5.351706] xhci-hcd xhci-hcd.0.auto: new USB bus registered, assigned bus number 2
[    5.359363] xhci-hcd xhci-hcd.0.auto: Host supports USB 3.0  SuperSpeed
[    5.366087] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 4.19
[    5.374350] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.381568] usb usb2: Product: xHCI Host Controller
[    5.386439] usb usb2: Manufacturer: Linux 4.19.0-xilinx-v2019.1 xhci-hcd
[    5.393130] usb usb2: SerialNumber: xhci-hcd.0.auto
[    5.398244] hub 2-0:1.0: USB hub found
[    5.402007] hub 2-0:1.0: 1 port detected
[    5.407038] pca953x 0-0020: 0-0020 supply vcc not found, using dummy regulator
[    5.414285] pca953x 0-0020: Linked as a consumer to regulator.0
[    5.420931] pca953x 0-0021: 0-0021 supply vcc not found, using dummy regulator
[    5.428179] pca953x 0-0021: Linked as a consumer to regulator.0
[    5.435492] ina2xx 3-0040: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.442277] ina2xx 3-0041: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.449061] ina2xx 3-0042: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.455848] ina2xx 3-0043: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.462632] ina2xx 3-0044: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.469412] ina2xx 3-0045: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.475822] ata2: SATA link down (SStatus 0 SControl 330)
[    5.481255] ata1: SATA link down (SStatus 0 SControl 330)
[    5.481408] ina2xx 3-0046: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.493425] ina2xx 3-0047: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.500207] ina2xx 3-004a: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.506992] ina2xx 3-004b: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.513367] i2c i2c-0: Added multiplexed i2c bus 3
[    5.518792] ina2xx 4-0040: power monitor ina226 (Rshunt = 2000 uOhm)
[    5.525576] ina2xx 4-0041: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.532361] ina2xx 4-0042: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.539145] ina2xx 4-0043: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.545931] ina2xx 4-0044: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.552715] ina2xx 4-0045: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.559501] ina2xx 4-0046: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.566285] ina2xx 4-0047: power monitor ina226 (Rshunt = 5000 uOhm)
[    5.572665] i2c i2c-0: Added multiplexed i2c bus 4
[    5.595169] random: fast init done
[    5.613597] i2c i2c-0: Added multiplexed i2c bus 5
[    5.618515] i2c i2c-0: Added multiplexed i2c bus 6
[    5.623299] pca954x 0-0075: registered 4 multiplexed busses for I2C mux pca9544
[    5.630622] cdns-i2c ff020000.i2c: 400 kHz mmio ff020000 irq 32
[    5.638294] at24 7-0054: 1024 byte 24c08 EEPROM, writable, 1 bytes/write
[    5.645019] i2c i2c-1: Added multiplexed i2c bus 7
[    5.650019] i2c i2c-1: Added multiplexed i2c bus 8
[    5.656862] si570 9-005d: registered, current frequency 300000000 Hz
[    5.663242] i2c i2c-1: Added multiplexed i2c bus 9
[    5.682030] si570 10-005d: registered, current frequency 148500000 Hz
[    5.688497] i2c i2c-1: Added multiplexed i2c bus 10
[    5.693577] si5324 11-0069: si5328 probed
[    5.757681] si5324 11-0069: si5328 probe successful
[    5.762586] i2c i2c-1: Added multiplexed i2c bus 11
[    5.767584] i2c i2c-1: Added multiplexed i2c bus 12
[    5.772584] i2c i2c-1: Added multiplexed i2c bus 13
[    5.777571] i2c i2c-1: Added multiplexed i2c bus 14
[    5.782447] pca954x 1-0074: registered 8 multiplexed busses for I2C switch pca9548
[    5.790346] i2c i2c-1: Added multiplexed i2c bus 15
[    5.795353] i2c i2c-1: Added multiplexed i2c bus 16
[    5.800359] i2c i2c-1: Added multiplexed i2c bus 17
[    5.805726] i2c i2c-1: Added multiplexed i2c bus 18
[    5.810725] i2c i2c-1: Added multiplexed i2c bus 19
[    5.815724] i2c i2c-1: Added multiplexed i2c bus 20
[    5.820740] i2c i2c-1: Added multiplexed i2c bus 21
[    5.825747] i2c i2c-1: Added multiplexed i2c bus 22
[    5.830623] pca954x 1-0075: registered 8 multiplexed busses for I2C switch pca9548
[    5.838206] cdns-i2c ff030000.i2c: 400 kHz mmio ff030000 irq 33
[    5.844535] cdns-wdt fd4d0000.watchdog: Xilinx Watchdog Timer at (____ptrval____) with timeout 60s
[    5.853766] cdns-wdt ff150000.watchdog: Xilinx Watchdog Timer at (____ptrval____) with timeout 10s
[    5.863008] cpufreq: cpufreq_online: CPU0: Running at unlisted freq: 1199880 KHz
[    5.870454] cpufreq: cpufreq_online: CPU0: Unlisted initial frequency changed to: 1199999 KHz
[    5.911125] mmc0: SDHCI controller on ff170000.mmc [ff170000.mmc] using ADMA 64-bit
[    5.927119] input: gpio-keys as /devices/platform/gpio-keys/input/input0
[    5.934057] rtc_zynqmp ffa60000.rtc: setting system clock to 2021-05-15 21:04:42 UTC (1621112682)
[    5.942930] of_cfs_init
[    5.945385] of_cfs_init: OK
[    5.948296] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    6.092406] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[    6.098937] clk: Not disabling unused clocks
[    6.103203] ALSA device list:
[    6.106158]   #0: DisplayPort monitor
[    6.109869] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[    6.115869] Warning: unable to open an initial console.
[    6.118475] cfg80211: failed to load regulatory.db
[    6.128409] Freeing unused kernel memory: 16512K
[    6.153647] Run /init as init process
[    6.160527] mmc0: new high speed SDHC card at address e624
[    6.166541] mmcblk0: mmc0:e624 SL16G 14.8 GiB
[    6.176486]  mmcblk0: p1
[    6.229635] [drm] Cannot find any crtc or sizes
[    6.841406] udevd[1984]: starting version 3.2.5
[    6.846275] random: udevd: uninitialized urandom read (16 bytes read)
[    6.852756] random: udevd: uninitialized urandom read (16 bytes read)
[    6.859242] random: udevd: uninitialized urandom read (16 bytes read)
[    6.869727] udevd[1985]: starting eudev-3.2.5
[    7.307715] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[    7.716533] pps pps0: new PPS source ptp0
[    7.720553] macb ff0e0000.ethernet: gem-ptp-timer ptp clock registered.
[    7.727250] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.718022] macb ff0e0000.ethernet eth0: link up (1000/Full)
[    8.723693] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.700107] urandom_read: 5 callbacks suppressed
[   16.700112] random: dropbearkey: uninitialized urandom read (32 bytes read)
[   16.714355] random: dropbearkey: uninitialized urandom read (32 bytes read)

PetaLinux 2019.1 xilinx-zcu102-2019_1 /dev/ttyPS0

xilinx-zcu102-2019_1 login: 
Password:
```

**<u><span>"screen" Tips</span></u>**

-   Type **C-a :** to enter command mode and type **hardcopy -h** to save the entire buffer
    
    -   **C-a h** will save just what's visible on the screen to a file called **hardcopy.n** in the directory screen started in
    
-   **C-a d** will detach from screen
    
    -   **screen -x PID** will reattach to a screen session, find PID with: ps aux | grep tty
        

**<u><span>References</span></u>**

-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]