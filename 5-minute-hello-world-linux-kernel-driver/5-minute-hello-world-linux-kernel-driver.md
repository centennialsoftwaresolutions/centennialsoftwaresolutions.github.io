# 5 Minute "Hello, World!" Linux Kernel Driver Tested on QEMU

![tux](tux.png)

This post shows you how to build and test a "Hello, World " Linux kernel driver in 5 min.

**<u><span>Before you Start</span></u>**

Read and follow the ARM instructions listed in **15 Minute Setup to Find, Change, Recompile and Test an ARM or x86 Linux Kernel Change in 12 Seconds** at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/15-minute-setup-to-find-change-recompile-and-test-an-arm-or-x86-linux-kernel-change-in-12-seconds)\]

**<u><span>Steps</span></u>**

**Set Up the Makefiles**

1\. Type **cd ~/tla/linux-4.10.6**

2\. Type **mkdir -p drivers/demo**

3\. Type **vi drivers/Makefile**

4\. Add **obj-y += demo/**

5\. Save the file with **:w** and quit with **:q**

6\. Type **vi drivers/demo/Makefile**

7\. Add **obj-y += demo.o**

8\. Save the file with **:w** and quit with **:q**

**Write the Driver**

1\. Type **cd ~/tla/linux-4.10.6**

2\. Type **vi drivers/demo/demo.c**

3\. Enter:

```
#include <linux/printk.h>                                                       
#include <linux/module.h>                                                       
                                                                                
static int demo_init(void)                                                      
{                                                                               
        printk(">>>>>>>>>> Hello, World! <<<<<<<<<<\n");                        
        return 0;                                                               
}                                                                               
                                                                                
module_init(demo_init);  
```

4\. Save the file with **:w** and quit with **:q**

**Compile and Run It**

1\. Type **cd ~/tla/linux-4.10.6**

2\. Type **source ~/envset.sh**

3\. Type **make**

You should see:

```
zpfeffer@z:~/tla/linux-4.10.6$ make
make[1]: Entering directory '/home/zpfeffer/tla/teeny-linux/obj/linux-arm-versatile_defconfig'
  CHK     include/config/kernel.release
  GEN     ./Makefile
  CHK     include/generated/uapi/linux/version.h
  CHK     include/generated/utsrelease.h
  Using /home/zpfeffer/tla/linux-4.10.6 as source for kernel
  CHK     include/generated/timeconst.h
  CHK     include/generated/bounds.h
  CHK     include/generated/asm-offsets.h
  CALL    /home/zpfeffer/tla/linux-4.10.6/scripts/checksyscalls.sh
  CHK     include/generated/compile.h
  CC      drivers/demo/demo.o
  LD      drivers/demo/built-in.o
  LD      drivers/built-in.o
  GEN     .version
  CHK     include/generated/compile.h
  UPD     include/generated/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      vmlinux.o
  MODPOST vmlinux.o
  KSYM    .tmp_kallsyms1.o
  KSYM    .tmp_kallsyms2.o
  LD      vmlinux
  SORTEX  vmlinux
  SYSMAP  System.map
  OBJCOPY arch/arm/boot/Image
  Building modules, stage 2.
  Kernel: arch/arm/boot/Image is ready
  MODPOST 24 modules
  GZIP    arch/arm/boot/compressed/piggy_data
  AS      arch/arm/boot/compressed/piggy.o
  LD      arch/arm/boot/compressed/vmlinux
  OBJCOPY arch/arm/boot/zImage
  Kernel: arch/arm/boot/zImage is ready
make[1]: Leaving directory '/home/zpfeffer/tla/teeny-linux/obj/linux-arm-versatile_defconfig'
```

4\. Run it by typing:

```
qemu-system-arm -M versatilepb  \
-dtb $KBUILD_OUTPUT/arch/arm/boot/dts/versatile-pb.dtb \
-kernel $KBUILD_OUTPUT/arch/arm/boot/zImage \
-initrd $TOP/obj/initramfs.igz \
-nographic -append "earlyprintk=serial,ttyS0 console=ttyAMA0"
```

You should see (look for >>>>>>>>>> Hello, World! <<<<<<<<<<):

```
zpfeffer@z:~/tla/linux-4.10.6$ qemu-system-arm -M versatilepb  -dtb $KBUILD_OUTPUT/arch/arm/boot/dts/versatile-pb.dtb -kernel $KBUILD_OUTPUT/arch/arm/boot/zImage -initrd $TOP/obj/initramfs.igz -nographic -append "earlyprintk=serial,ttyS0 console=ttyAMA0"
pulseaudio: set_sink_input_volume() failed
pulseaudio: Reason: Invalid argument
pulseaudio: set_sink_input_mute() failed
pulseaudio: Reason: Invalid argument
Uncompressing Linux... done, booting the kernel.
Booting Linux on physical CPU 0x0
Linux version 4.10.6 (zpfeffer@z) (gcc version 5.4.0 20160609 (Ubuntu/Linaro 5.4.0-6ubuntu1~16.04.9) ) #12 Fri Jan 4 15:52:47 MST 2019
CPU: ARM926EJ-S [41069265] revision 5 (ARMv5TEJ), cr=00093177
CPU: VIVT data cache, VIVT instruction cache
OF: fdt:Machine model: ARM Versatile PB
bootconsole [earlycon0] enabled
Memory policy: Data cache writeback
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 32512
Kernel command line: earlyprintk=serial,ttyS0 console=ttyAMA0
PID hash table entries: 512 (order: -1, 2048 bytes)
Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
Memory: 124060K/131072K available (3352K kernel code, 127K rwdata, 772K rodata, 156K init, 133K bss, 7012K reserved, 0K cma-reserved)
Virtual kernel memory layout:
    vector  : 0xffff0000 - 0xffff1000   (   4 kB)
    fixmap  : 0xffc00000 - 0xfff00000   (3072 kB)
    vmalloc : 0xc8800000 - 0xff800000   ( 880 MB)
    lowmem  : 0xc0000000 - 0xc8000000   ( 128 MB)
    modules : 0xbf000000 - 0xc0000000   (  16 MB)
      .text : 0xc0008000 - 0xc034e5f0   (3354 kB)
      .init : 0xc042b000 - 0xc0452000   ( 156 kB)
      .data : 0xc0452000 - 0xc0471f60   ( 128 kB)
       .bss : 0xc0471f60 - 0xc0493478   ( 134 kB)
NR_IRQS:16 nr_irqs:16 16
VIC @c8800000: id 0x00041190, vendor 0x41
FPGA IRQ chip 0 "intc" @ c8802000, 20 irqs, parent IRQ: 47
vpb_sic_write: Bad register offset 0x2c
clocksource: arm,sp804: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 1911260446275 ns
sched_clock: 32 bits at 1000kHz, resolution 1000ns, wraps every 2147483647500ns
Failed to initialize '/amba/timer@101e3000': -22
sched_clock: 32 bits at 24MHz, resolution 41ns, wraps every 89478484971ns
Console: colour dummy device 80x30
Calibrating delay loop... 296.14 BogoMIPS (lpj=1480704)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
CPU: Testing write buffer coherency: ok
Setting up static identity map for 0x8400 - 0x8458
VFP support v0.3: implementor 41 architecture 1 part 10 variant 9 rev 0
clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
futex hash table entries: 256 (order: -1, 3072 bytes)
NET: Registered protocol family 16
DMA: preallocated 256 KiB pool for atomic coherent allocations
OF: amba_device_add() failed (-19) for /amba/smc@10100000
OF: amba_device_add() failed (-19) for /amba/mpmc@10110000
OF: amba_device_add() failed (-19) for /amba/sctl@101e0000
OF: amba_device_add() failed (-19) for /amba/watchdog@101e1000
OF: amba_device_add() failed (-19) for /amba/sci@101f0000
OF: amba_device_add() failed (-19) for /amba/ssp@101f4000
OF: amba_device_add() failed (-19) for /amba/fpga/sci@a000
Serial: AMBA PL011 UART driver
101f1000.uart: ttyAMA0 at MMIO 0x101f1000 (irq = 28, base_baud = 0) is a PL011 rev1
console [ttyAMA0] enabled
console [ttyAMA0] enabled
bootconsole [earlycon0] disabled
bootconsole [earlycon0] disabled
101f2000.uart: ttyAMA1 at MMIO 0x101f2000 (irq = 29, base_baud = 0) is a PL011 rev1
101f3000.uart: ttyAMA2 at MMIO 0x101f3000 (irq = 30, base_baud = 0) is a PL011 rev1
uart-pl011 10009000.uart: aliased and non-aliased serial devices found in device tree. Serial port enumeration may be unpredictable.
10009000.uart: ttyAMA3 at MMIO 0x10009000 (irq = 54, base_baud = 0) is a PL011 rev1
clocksource: Switched to clocksource arm,sp804
NET: Registered protocol family 2
TCP established hash table entries: 1024 (order: 0, 4096 bytes)
TCP bind hash table entries: 1024 (order: 0, 4096 bytes)
TCP: Hash tables configured (established 1024 bind 1024)
UDP hash table entries: 256 (order: 0, 4096 bytes)
UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
NET: Registered protocol family 1
RPC: Registered named UNIX socket transport module.
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
Trying to unpack rootfs image as initramfs...
Freeing initrd memory: 1096K
NetWinder Floating Point Emulator V0.97 (double precision)
workingset: timestamp_bits=30 max_order=15 bucket_order=0
Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
jffs2: version 2.2. (NAND) © 2001-2006 Red Hat, Inc.
romfs: ROMFS MTD (C) 2007 Red Hat, Inc.
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
>>>>>>>>>> Hello, World! <<<<<<<<<<
pl061_gpio 101e4000.gpio: PL061 GPIO chip @0x101e4000 registered
pl061_gpio 101e5000.gpio: PL061 GPIO chip @0x101e5000 registered
pl061_gpio 101e6000.gpio: PL061 GPIO chip @0x101e6000 registered
pl061_gpio 101e7000.gpio: PL061 GPIO chip @0x101e7000 registered
clcd-pl11x dev:20: PL110 designer 41 rev0 at 0x10120000
clcd-pl11x dev:20: Versatile hardware, VGA display
Console: switching to colour frame buffer device 80x60
brd: module loaded
smc91x.c: v1.1, sep 22 2004 by Nicolas Pitre 
smc91x 10010000.net eth0: SMC91C11xFD (rev 1) at c8a65000 IRQ 41
smc91x 10010000.net eth0: Ethernet addr: 52:54:00:12:34:56
mousedev: PS/2 mouse device common for all mice
rtc-ds1307 0-0068: rtc core: registered ds1338 as rtc0
rtc-ds1307 0-0068: 56 bytes nvram
versatile reboot driver registered
mmci-pl18x fpga:05: mmc0: PL181 manf 41 rev0 at 0x10005000 irq 59,60 (pio)
mmci-pl18x fpga:0b: mmc1: PL181 manf 41 rev0 at 0x1000b000 irq 49,50 (pio)
input: AT Raw Set 2 keyboard as /devices/platform/amba/amba:fpga/10006000.kmi/serio0/input/input0
leds-syscon 10000000.core-module:led@08.0: registered LED versatile:0
leds-syscon 10000000.core-module:led@08.1: registered LED versatile:1
leds-syscon 10000000.core-module:led@08.2: registered LED versatile:2
leds-syscon 10000000.core-module:led@08.3: registered LED versatile:3
leds-syscon 10000000.core-module:led@08.4: registered LED versatile:4
leds-syscon 10000000.core-module:led@08.5: registered LED versatile:5
leds-syscon 10000000.core-module:led@08.6: registered LED versatile:6
leds-syscon 10000000.core-module:led@08.7: registered LED versatile:7
ledtrig-cpu: registered to indicate activity on CPUs
NET: Registered protocol family 17
rtc-ds1307 0-0068: setting system clock to 2019-01-04 22:52:54 UTC (1546642374)
Freeing unused kernel memory: 156K
This architecture does not have kernel memory protection.
mount: mounting none on /sys/kernel/debug failed: No such file or directory

Boot took 1.55 seconds

/bin/sh: can't access tty; job control turned off
/ # random: fast init done
input: ImExPS/2 Generic Explorer Mouse as /devices/platform/amba/amba:fpga/10007000.kmi/serio1/input/input2
random: crng init done
```

5\. Type **Control-a x** to quit QEMU

**<u><span>References</span></u>**

-   HTML escape from \[[<u><span>link</span></u>](https://www.freeformatter.com/html-escape.html)\]
    
-   Tux from \[[<u><span>link</span></u>](https://www.iconfinder.com/icons/367633/linux_tux_icon#size=128)\]