# PetaLinux 2025.1 Install Log

Commands and output from installing **PetaLinux 2025.1** on a VM, building the Linux kernel, U-Boot and the SDK from a ZCU102 xsct BSP, and testing U-Boot and the Linux Kernel booting. Command and boot outputs listed. 

------

# Environment

- **Host:** Windows 11 Pro (Version 10.0.26100 Build 26100)
- **Hypervisor:** VMware® Workstation 17 Pro (17.5.2 build-23775571)
- **Guest OS:** Ubuntu 24.04.3

------

# Before Installing

1. Switch default shell

   ```
   TARGET="$(command -v bash)"
   LINK="/bin/sh"
   sudo ln -sf "$TARGET" "$LINK"
   ```

2. Run provided dependency installer

   ```
   sudo FPGAs_AdaptiveSoCs_Unified_SDI_2025.1_0530_0145/installLibs.sh
   ```

3. Install additional packages not covered by `installLibs.sh`

   ```
   packages_missing_from_installlibs=(
     xterm
     autoconf
     libtool
     texinfo
   )
   sudo apt-get install -y "${packages_missing_from_installlibs[@]}"
   ```

------

# Install

1. Get “Product” & “Edition” for Install

   ```
   FPGAs_AdaptiveSoCs_Unified_SDI_2025.1_0530_0145/xsetup -b ConfigGen
   ```

   Output:

   ```
   This is a fresh install.
   Running in batch mode...
   Copyright (c) 1986-2022 Xilinx, Inc.  All rights reserved.
   Copyright (c) 2022-2025 Advanced Micro Devices, Inc.  All rights reserved.
   
   Select a Product from the list:
   1. Vitis
   2. Vivado
   3. Vitis Embedded Development
   4. BootGen
   5. Lab Edition
   6. Hardware Server
   7. Power Design Manager (PDM)
   8. On-Premises Install for Cloud Deployments
   9. PetaLinux
   10. Documentation Navigator (Standalone)
   
   Please choose: 9
   
   Select an Edition from the list:
   1. PetaLinux All platforms
   2. PetaLinux aarch64
   3. PetaLinux arm
   4. PetaLinux microblaze
   5. PetaLinux aarch64 and arm
   6. PetaLinux aarch64 and microblaze
   7. PetaLinux arm and microblaze
   
   Please choose: 1
   INFO  - Config file available at /home/demo/.Xilinx/install_config.txt.
           Please use -c <filename> to point to this install configuration.
   ```

2. Create an Installation Directory

   ```
   mkdir -p ~/petalinux_2025.1
   ```

3. First Install Attempt

   ```
   FPGAs_AdaptiveSoCs_Unified_SDI_2025.1_0530_0145/xsetup \
     --agree 3rdPartyEULA,XilinxEULA \
     --batch Install \
     --product "PetaLinux" \
     --edition "PetaLinux All platforms" \
     --location "~/petalinux_2025.1"
   ```

   Error Output

   ```
   This is a fresh install.
   Running in batch mode...
   Copyright (c) 1986-2022 Xilinx, Inc.  All rights reserved.
   Copyright (c) 2022-2025 Advanced Micro Devices, Inc.  All rights reserved.
   INFO  - User has accepted the EULAs.
   ERROR - Destination directory "~/petalinux_2025.1" has invalid character: ~
   ```

   > [!IMPORTANT]
   >
   > The installer does **not** expand `~`. A Linux installer should really be able to handle this.

4. Second Install Attempt (Using Full Path)

   ```
   FPGAs_AdaptiveSoCs_Unified_SDI_2025.1_0530_0145/xsetup \
     --agree 3rdPartyEULA,XilinxEULA \
     --batch Install \
     --product "PetaLinux" \
     --edition "PetaLinux All platforms" \
     --location "/home/demo/petalinux_2025.1"
   ```

   Success Output:

   ```
   This is a fresh install.
   Running in batch mode...
   Copyright (c) 1986-2022 Xilinx, Inc.  All rights reserved.
   Copyright (c) 2022-2025 Advanced Micro Devices, Inc.  All rights reserved.
   INFO  - User has accepted the EULAs.
   INFO  - Installing Edition: PetaLinux All platforms
   INFO  - Installation directory is /home/demo/petalinux_2025.1
   
   Installing files, 99% completed. (Done)
   It took 4 minutes to install files.
   
   INFO  - Installation completed successfully.
   Petalinux downloads, sstate and prebuilt bsps will be available in the below location.
   The usage of this content will be available in UG1144 PetaLinux User Guide.
   https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html
   ```

------

# Test Building

1. Download XSCT BSP (Legacy Style) from [link](https://account.amd.com/en/forms/downloads/xef.html?filename=xilinx-zcu102-xsct-v2025.1-05221048.bsp).

   > [!IMPORTANT]
   >
   > Requires an AMD/Xilinx account login.

------

2. Source the PetaLinux Tools Environment

   ```
   source /home/demo/petalinux_2025.1/2025.1/PetaLinux/tool/settings.sh
   ```

   Output

   ```
   *************************************************************************************************************************************************
   The PetaLinux source code and images provided/generated are for demonstration purposes only.
   Please refer to https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/2741928025/Moving+from+PetaLinux+to+Production+Deployment
    for more details
   *************************************************************************************************************************************************
   PetaLinux environment set to '/home/demo/petalinux_2025.1/2025.1/PetaLinux/tool'
   [WARNING] This is not a supported OS
   [INFO] Checking free disk space
   [INFO] Checking installed tools
   [INFO] Checking installed development libraries
   [INFO] Checking network and other services
   [WARNING] No tftp server found - please refer to "UG1144 2025.1 PetaLinux Tools Documentation Reference Guide" for its impact and solution
   ```

   > [!NOTE]
   >
   > Re:*[WARNING] This is not a supported OS* later testing suggests that Ubuntu 24.04.3 works. Note, AMD support may ask you to reproduce issues on the last supported OS before they can help.

3. Create a Project from the BSP 

   Following UG1144 (v2025.1), *Creating a Project from a BSP* (p.18):

   ```
   petalinux-create project -s xilinx-zcu102-xsct-v2025.1-05221048.bsp
   ```

   Output

   ```
   [INFO] Create project:
   [INFO] Project(s):
   	* xilinx-zcu102-xsct-2025.1
   [INFO] Has been successfully installed to /home/demo/zcu102_petalinux/
   [INFO] New project successfully created in /home/demo/zcu102_petalinux/
   ```

4. Build a PetaLinux System Image

   Following UG1144 (v2025.1), p.27:

   ```
   cd xilinx-zcu102-xsct-2025.1/
   petalinux-build
   ```

   1. First Build Attempt; Error: Missing Library

      ```
      [INFO] Building project
      ...
      ERROR: libtinfo.so.5 (libtinfo.so.5) is required by meta-xilinx-tools.
      This library must be installed before the build system can use xsct. It is often part of an ncurses5 package.
      ```

      Fix (Install `libtinfo5`):

      ```
      sudo apt update
      wget http://security.ubuntu.com/ubuntu/pool/universe/n/ncurses/libtinfo5_6.3-2ubuntu0.1_amd64.deb
      sudo apt install ./libtinfo5_6.3-2ubuntu0.1_amd64.deb
      ```

   2. Second Build Attempt; Error: AppArmor Restriction

      ```
      ERROR: User namespaces are not usable by BitBake, possibly due to AppArmor.
      See https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890#unprivileged-user-namespace-restrictions for more information.
      ```

      Workaround (Temporary, Until Reboot)

      ```
      sudo su
      echo 0 > /proc/sys/kernel/apparmor_restrict_unprivileged_userns
      exit
      ```

      Persistent Workaround (Survives Reboot)

      ```
      sudo vi /etc/sysctl.d/60-apparmor-namespace.conf
      # Add kernel.apparmor_restrict_unprivileged_userns=0
      # Reboot
      ```

   3. Third Attempt; A Successful Build

      Re-run:

      ```
      cd xilinx-zcu102-xsct-2025.1/
      petalinux-build
      ```

      Output (Truncated)

      ```
      [INFO] Building project
      ...
      Parsing of 6138 .bb files complete (0 cached, 6138 parsed). 8821 targets, 1320 skipped, 28 masked, 0 errors.
      NOTE: Resolving any missing task queue dependencies
      ...
      Sstate summary: Wanted 2864 Local 0 Mirrors 2632 Missed 232 Current 0 (91% match, 0% complete)
      NOTE: Executing Tasks
      NOTE: Tasks Summary: Attempted 6305 tasks of which 5481 didn't need to be rerun and all succeeded.
      
      Summary: There was 1 WARNING message.
      [INFO] Failed to copy built images to tftp dir: /tftpboot
      [INFO] Successfully built project
      ```

5. Build SDK

   Following UG1144 (v2025.1), "Building SDK", p.165:

   ```
   petalinux-build --sdk
   ```

   Output:

   ```
   [INFO] Building project
   [INFO] Bitbake is not available, some functionality may be reduced.
   [INFO] Using HW file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/project-spec/hw-description/system.xsa
   [INFO] Getting Platform info from HW file
   [INFO] Silentconfig project
   [INFO] Silentconfig rootfs
   [INFO] Generating configuration files
   [INFO] Generating workspace directory
   NOTE: Starting bitbake server...
   NOTE: Started PRServer with DBfile: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/build/cache/prserv.sqlite3, Address: 127.0.0.1:42753, PID: 205449
   INFO: Specified workspace already set up, leaving as-is
   [INFO] bitbake petalinux-image-minimal -c do_populate_sdk
   NOTE: Started PRServer with DBfile: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/build/cache/prserv.sqlite3, Address: 127.0.0.1:43951, PID: 205509
   WARNING: XSCT has been deprecated. It will still be available for several releases. In the future, it's recommended to start new projects with SDT workflow.
   Loading cache: 100% |###########################################################################################################################################################| Time: 0:00:24
   Loaded 8815 entries from dependency cache.
   Parsing recipes: 100% |#########################################################################################################################################################| Time: 0:00:07
   Parsing of 6138 .bb files complete (6133 cached, 5 parsed). 8821 targets, 1320 skipped, 28 masked, 0 errors.
   NOTE: Resolving any missing task queue dependencies
   Checking sstate mirror object availability: 100% |##############################################################################################################################| Time: 0:01:17
   Sstate summary: Wanted 1425 Local 22 Mirrors 553 Missed 850 Current 1526 (40% match, 71% complete)
   NOTE: Executing Tasks
   NOTE: Tasks Summary: Attempted 6616 tasks of which 4885 didn't need to be rerun and all succeeded.
   
   Summary: There was 1 WARNING message.
   [INFO] Copying SDK Installer...
   [INFO] Failed to copy built images to tftp dir: /tftpboot
   [INFO] Successfully built project
   ```

# Test Running What Was Built

## Bring Up minicom

1. Configure Minicom

   Follow the guide: [Configure Minicom for a USB-to-Serial Converter](https://www.centennialsoftwaresolutions.com/help/configure-minicom-for-a-usb-to-serial-converter/)

2. Start Minicom in Another Window

   ```
   minicom
   ```

## Boot U-Boot

1. Boot U-Boot via ZCU102 Built-In USB-JTAG

   ```
   petalinux-boot jtag --u-boot
   ```

   Full Output

   ```
   [INFO] Use Bitstream: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/system.bit 
   [INFO] Please use --fpga <BITSTREAM> to specify a bitstream if you want to use other bitstream. 
   [INFO] Launching XSDB for file download and boot. 
   [INFO] This may take a few minutes, depending on the size of your image. attempting to launch hw_server 
   
   ****** Xilinx hw_server v2025.1
     **** Build date : May 6 2025 at 15:14:51
       ** Copyright 1986-2022 Xilinx, Inc. All Rights Reserved. 
       ** Copyright 2022-2025 Advanced Micro Devices, Inc. All Rights Reserved. 
       
   INFO: hw_server application started 
   INFO: Use Ctrl-C to exit hw_server application 
   
   INFO: To connect to this hw_server instance use url: TCP:127.0.0.1:3121 
   
   INFO: Configuring the FPGA... 
   INFO: Downloading bitstream: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/system.bit to the target. 
   INFO: Downloading ELF file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/pmufw.elf to the target. 
   INFO: Downloading ELF file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/zynqmp_fsbl.elf to the target. 
   INFO: Loading image: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/system.dtb at 0x100000. 
   INFO: Downloading ELF file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/u-boot.elf to the target. 
   INFO: Downloading ELF file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/bl31.elf to the target.
   ```

2. Observed no output in **minicom**.

   Debug: 

   1. Check system messages:

      ```
      sudo dmesg
      ```

   2. Check output:

      ```
      ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
      cp210x ttyUSB1: cp210x converter now disconnected from ttyUSB1
      cp210x ttyUSB2: cp210x converter now disconnected from ttyUSB2
      cp210x ttyUSB3: cp210x converter now disconnected from ttyUSB3
      cp210x ttyUSB4: cp210x converter now disconnected from ttyUSB4
      ```

      Output shows minicom was listening to `/dev/ttyUSB1`.

   Fix:

   1. Replug the USB-to-UART bridge so it reattaches as `/dev/ttyUSB0`.

   2. Check again with:

      ```
      sudo dmesg
      ```

   3. Check output (truncated)

      ```
      usb 1-2.2: cp210x converter now attached to ttyUSB0
      usb 1-2.2: cp210x converter now attached to ttyUSB1
      usb 1-2.2: cp210x converter now attached to ttyUSB2
      usb 1-2.2: cp210x converter now attached to ttyUSB3
      ```

   4. Check minicom:

      ```
      *** ERROR: `serverip' not set
      Retrieving file: pxelinux.cfg/default
      ethernet@ff0e0000 Waiting for PHY auto negotiation to complete......................................... TIMEOUT !
      *** ERROR: `serverip' not set
      ```

      Shows U-Boot is running and the UART is working.

## Boot the Linux Kernel

1. Boot the Linux kernel and rootfs via ZCU102 Built-In USB-JTAG

2. Hard reboot the ZCU102 using **SW1**.

3. Boot the kernel:

   ```
   petalinux-boot jtag --kernel
   ```

   Output

   ```
   demo@demo:~/zcu102_petalinux/xilinx-zcu102-xsct-2025.1$ petalinux-boot jtag --kernel
   [INFO] Use Bitstream: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/system.bit
   [INFO] Please use --fpga <BITSTREAM> to specify a bitstream if you want to use other bitstream.
   [INFO] Launching XSDB for file download and boot.
   [INFO] This may take a few minutes, depending on the size of your image.
   attempting to launch hw_server
   
   ****** Xilinx hw_server v2025.1
     **** Build date : May  6 2025 at 15:14:51
       ** Copyright 1986-2022 Xilinx, Inc. All Rights Reserved.
       ** Copyright 2022-2025 Advanced Micro Devices, Inc. All Rights Reserved.
   
   INFO: hw_server application started
   INFO: Use Ctrl-C to exit hw_server application
   
   INFO: To connect to this hw_server instance use url: TCP:127.0.0.1:3121
   
   INFO: Configuring the FPGA...
   INFO: Downloading bitstream: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/system.bit to the target.
   INFO: Downloading ELF file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/pmufw.elf to the target.
   INFO: Downloading ELF file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/zynqmp_fsbl.elf to the target.
   INFO: Loading image: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/system.dtb at 0x100000.
   INFO: Downloading ELF file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/u-boot.elf to the target.
   INFO: Loading image: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/Image at 0x200000.
   INFO: Loading image: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/ramdisk.cpio.gz.u-boot at 0x4000000.
   INFO: Loading image: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/boot.scr at 0x20000000.
   INFO: Downloading ELF file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/images/linux/bl31.elf to the target.
   ```

4. Check minicom for **FSBL output** which shows a good start:

   ```
   Zynq MP First Stage Boot Loader  Release 2025.1   May 14 2025  -  12:33:16 
   ```

5. minicom output after 25 min:

   ```
   Zynq MP First Stage Boot Loader
   Release 2025.1   May 14 2025  -  12:33:16
   
   
   U-Boot 2025.01-ga09d2660433d (May 16 2025 - 14:46:32 +0000)
   
   CPU:   ZynqMP
   Silicon: v3
   Chip:  zu9eg
   Model: ZynqMP ZCU102 Rev1.0
   Board: Xilinx ZynqMP
   DRAM:  2 GiB (effective 4 GiB)
   Xilinx I2C Legacy format at nvmem0:
    Board name:    zcu102
    Board rev:     1.0
    Board SN:      881461172208-66530
    Ethernet mac:  00:0a:35:07:8f:88
   EL Level:       EL2
   Secure Boot:    not authenticated, not encrypted
   Core:  77 devices, 30 uclasses, devicetree: board
   NAND:  0 MiB
   MMC:   mmc@ff170000: 0
   Loading Environment from nowhere... OK
   In:    serial
   Out:   serial,vidconsole
   Err:   serial,vidconsole
   Bootmode: JTAG_MODE
   Reset reason:   EXTERNAL
   Net:
   ZYNQ GEM: ff0e0000, mdio bus ff0e0000, phyaddr 12, interface rgmii-id
   
   Warning: ethernet@ff0e0000 MAC addresses don't match:
   Address in DT is                ff:ff:ff:ff:ff:ff
   Address in environment is       00:0a:35:07:8f:88
   eth0: ethernet@ff0e0000
   
   scanning bus for devices...
   SATA link 0 timeout.
   SATA link 1 timeout.
   AHCI 0001.0301 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
   flags: 64bit ncq pm clo only pmp fbss pio slum part ccc apst
   starting USB...
   Bus usb@fe200000: Register 2000440 NbrPorts 2
   Starting the controller
   USB XHCI 1.00
   scanning bus usb@fe200000 for devices... 1 USB Device(s) found
          scanning usb for storage devices... 0 Storage Device(s) found
   Hit any key to stop autoboot:  0
   JTAG: Trying to boot script at 20000000
   ## Executing script at 20000000
   Trying to load boot images from jtag
   ## Loading init Ramdisk from Legacy Image at 04000000 ...
      Image Name:   petalinux-initramfs-image-xilinx
      Created:      2011-04-05  23:00:00 UTC
      Image Type:   AArch64 Linux RAMDisk Image (uncompressed)
      Data Size:    5651900 Bytes = 5.4 MiB
      Load Address: 00000000
      Entry Point:  00000000
      Verifying Checksum ... OK
   ## Flattened Device Tree blob at 00100000
      Booting using the fdt blob at 0x100000
   Working FDT set to 100000
      Loading Ramdisk to 7777a000, end 77cdddbc ... OK
      Loading Device Tree to 0000000077768000, end 0000000077779bb1 ... OK
   Working FDT set to 77768000
   No RNG device
   
   Starting kernel ...
   
   [    0.000000] Booting Linux on physical CPU 0x0000000000 [0x410fd034]
   [    0.000000] Linux version 6.12.10-xilinx-g0a0f70e531c7 (oe-user@oe-host) (aarch64-amd-linux-gcc (GCC) 13.3.0, GNU ld (GNU B5
   [    0.000000] KASLR disabled due to lack of seed
   [    0.000000] Machine model: ZynqMP ZCU102 Rev1.0
   [    0.000000] earlycon: cdns0 at MMIO 0x00000000ff000000 (options '115200n8')
   [    0.000000] printk: legacy bootconsole [cdns0] enabled
   [    0.000000] efi: UEFI not found.
   [    0.000000] Zone ranges:
   [    0.000000]   DMA      [mem 0x0000000000000000-0x00000000ffffffff]
   [    0.000000]   DMA32    empty
   [    0.000000]   Normal   [mem 0x0000000100000000-0x000000087fffffff]
   [    0.000000] Movable zone start for each node
   [    0.000000] Early memory node ranges
   [    0.000000]   node   0: [mem 0x0000000000000000-0x000000007fefffff]
   [    0.000000]   node   0: [mem 0x0000000800000000-0x000000087fffffff]
   [    0.000000] Initmem setup node 0 [mem 0x0000000000000000-0x000000087fffffff]
   [    0.000000] On node 0, zone Normal: 256 pages in unavailable ranges
   [    0.000000] cma: Reserved 256 MiB at 0x0000000067600000 on node -1
   [    0.000000] psci: probing for conduit method from DT.
   [    0.000000] psci: PSCIv1.1 detected in firmware.
   [    0.000000] psci: Using standard PSCI v0.2 function IDs
   [    0.000000] psci: MIGRATE_INFO_TYPE not supported.
   [    0.000000] psci: SMC Calling Convention v1.5
   [    0.000000] percpu: Embedded 22 pages/cpu s51992 r8192 d29928 u90112
   [    0.000000] Detected VIPT I-cache on CPU0
   [    0.000000] CPU features: detected: ARM erratum 845719
   [    0.000000] alternatives: applying boot alternatives
   [    0.000000] Kernel command line: earlycon console=ttyPS0,115200 root=/dev/ram0 rw init_fatal_sh=1
   [    0.000000] Unknown kernel command line parameters "init_fatal_sh=1", will be passed to user space.
   [    0.000000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes, linear)
   [    0.000000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes, linear)
   [    0.000000] Built 1 zonelists, mobility grouping on.  Total pages: 1048320
   [    0.000000] mem auto-init: stack:all(zero), heap alloc:off, heap free:off
   [    0.000000] software IO TLB: area num 4.
   [    0.000000] software IO TLB: mapped [mem 0x000000007bf00000-0x000000007ff00000] (64MB)
   [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
   [    0.000000] rcu: Hierarchical RCU implementation.
   [    0.000000] rcu:     RCU event tracing is enabled.
   [    0.000000] rcu:     RCU restricting CPUs from NR_CPUS=16 to nr_cpu_ids=4.
   [    0.000000]  Tracing variant of Tasks RCU enabled.
   [    0.000000] rcu: RCU calculated value of scheduler-enlistment delay is 25 jiffies.
   [    0.000000] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
   [    0.000000] RCU Tasks Trace: Setting shift to 2 and lim to 1 rcu_task_cb_adjust=1 rcu_task_cpu_ids=4.
   [    0.000000] NR_IRQS: 64, nr_irqs: 64, preallocated irqs: 0
   [    0.000000] GIC: Adjusting CPU interface base to 0x00000000f902f000
   [    0.000000] Root IRQ handler: gic_handle_irq
   [    0.000000] GIC: Using split EOI/Deactivate mode
   [    0.000000] rcu: srcu_init: Setting srcu_struct sizes based on contention.
   [    0.000000] arch_timer: cp15 timer(s) running at 99.99MHz (phys).
   [    0.000000] clocksource: arch_sys_counter: mask: 0x1ffffffffffffff max_cycles: 0x170f8de2d3, max_idle_ns: 440795206112 ns
   [    0.000000] sched_clock: 57 bits at 100MHz, resolution 10ns, wraps every 4398046511101ns
   [    0.008372] Console: colour dummy device 80x25
   [    0.012561] Calibrating delay loop (skipped), value calculated using timer frequency.. 199.98 BogoMIPS (lpj=399960)
   [    0.022974] pid_max: default: 32768 minimum: 301
   [    0.027707] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes, linear)
   [    0.034991] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes, linear)
   [    0.066894] rcu: Hierarchical SRCU implementation.
   [    0.066941] rcu:     Max phase no-delay instances is 1000.
   [    0.071444] Timer migration: 1 hierarchy levels; 8 children per group; 1 crossnode level
   [    0.079549] EFI services will not be available.
   [    0.084059] smp: Bringing up secondary CPUs ...
   [    0.088814] Detected VIPT I-cache on CPU1
   [    0.088881] CPU1: Booted secondary processor 0x0000000001 [0x410fd034]
   [    0.089329] Detected VIPT I-cache on CPU2
   [    0.089374] CPU2: Booted secondary processor 0x0000000002 [0x410fd034]
   [    0.089796] Detected VIPT I-cache on CPU3
   [    0.089841] CPU3: Booted secondary processor 0x0000000003 [0x410fd034]
   [    0.089902] smp: Brought up 1 node, 4 CPUs
   [    0.124076] SMP: Total of 4 processors activated.
   [    0.128774] CPU: All CPU(s) started at EL2
   [    0.132865] CPU features: detected: 32-bit EL0 Support
   [    0.137999] CPU features: detected: CRC32 instructions
   [    0.143166] alternatives: applying system-wide alternatives
   [    0.149661] Memory: 3748120K/4193280K available (16960K kernel code, 1082K rwdata, 5080K rodata, 3200K init, 478K bss, 1794)
   [    0.163639] devtmpfs: initialized
   [    0.173769] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
   [    0.177902] futex hash table entries: 1024 (order: 4, 65536 bytes, linear)
   [    0.190190] 26016 pages in range for non-PLT usage
   [    0.190208] 517536 pages in range for PLT usage
   [    0.190398] pinctrl core: initialized pinctrl subsystem
   [    0.199676] DMI not present or invalid.
   [    0.205069] NET: Registered PF_NETLINK/PF_ROUTE protocol family
   [    0.209727] DMA: preallocated 512 KiB GFP_KERNEL pool for atomic allocations
   [    0.216180] DMA: preallocated 512 KiB GFP_KERNEL|GFP_DMA pool for atomic allocations
   [    0.223975] DMA: preallocated 512 KiB GFP_KERNEL|GFP_DMA32 pool for atomic allocations
   [    0.231765] audit: initializing netlink subsys (disabled)
   [    0.237258] audit: type=2000 audit(0.156:1): state=initialized audit_enabled=0 res=1
   [    0.237717] hw-breakpoint: found 6 breakpoint and 4 watchpoint registers.
   [    0.251736] ASID allocator initialised with 65536 entries
   [    0.257200] Serial: AMBA PL011 UART driver
   [    0.268410] /axi/interrupt-controller@f9010000: Fixed dependency cycle(s) with /axi/interrupt-controller@f9010000
   [    0.273221] /axi/pcie@fd0e0000: Fixed dependency cycle(s) with /axi/pcie@fd0e0000
   [    0.284619] /axi/pcie@fd0e0000: Fixed dependency cycle(s) with /axi/pcie@fd0e0000
   [    0.288068] /axi/pcie@fd0e0000: Fixed dependency cycle(s) with /axi/pcie@fd0e0000/legacy-interrupt-controller
   [    0.302187] /axi/display@fd4a0000: Fixed dependency cycle(s) with /dpcon
   [    0.304686] /dpcon: Fixed dependency cycle(s) with /axi/display@fd4a0000
   [    0.312677] HugeTLB: registered 1.00 GiB page size, pre-allocated 0 pages
   [    0.318131] HugeTLB: 0 KiB vmemmap can be freed for a 1.00 GiB page
   [    0.324397] HugeTLB: registered 32.0 MiB page size, pre-allocated 0 pages
   [    0.331175] HugeTLB: 0 KiB vmemmap can be freed for a 32.0 MiB page
   [    0.337441] HugeTLB: registered 2.00 MiB page size, pre-allocated 0 pages
   [    0.344226] HugeTLB: 0 KiB vmemmap can be freed for a 2.00 MiB page
   [    0.350492] HugeTLB: registered 64.0 KiB page size, pre-allocated 0 pages
   [    0.357277] HugeTLB: 0 KiB vmemmap can be freed for a 64.0 KiB page
   [    0.431622] raid6: neonx8   gen()  2271 MB/s
   [    0.499686] raid6: neonx4   gen()  2227 MB/s
   [    0.567763] raid6: neonx2   gen()  2113 MB/s
   [    0.635825] raid6: neonx1   gen()  1787 MB/s
   [    0.703903] raid6: int64x8  gen()  1415 MB/s
   [    0.771973] raid6: int64x4  gen()  1568 MB/s
   [    0.840047] raid6: int64x2  gen()  1399 MB/s
   [    0.908119] raid6: int64x1  gen()  1034 MB/s
   [    0.908160] raid6: using algorithm neonx8 gen() 2271 MB/s
   [    0.980202] raid6: .... xor() 1656 MB/s, rmw enabled
   [    0.980249] raid6: using neon recovery algorithm
   [    0.984720] iommu: Default domain type: Translated
   [    0.988924] iommu: DMA domain TLB invalidation policy: strict mode
   [    0.995413] SCSI subsystem initialized
   [    0.998996] usbcore: registered new interface driver usbfs
   [    1.004346] usbcore: registered new interface driver hub
   [    1.009651] usbcore: registered new device driver usb
   [    1.014768] mc: Linux media interface: v0.10
   [    1.018964] videodev: Linux video capture interface: v2.00
   [    1.024445] pps_core: LinuxPPS API ver. 1 registered
   [    1.029377] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
   [    1.038521] PTP clock support registered
   [    1.042451] EDAC MC: Ver: 3.0.0
   [    1.045765] scmi_core: SCMI protocol bus registered
   [    1.050576] zynqmp-ipi-mbox mailbox@ff9905c0: Registered ZynqMP IPI mbox with TX/RX channels.
   [    1.059428] FPGA manager framework
   [    1.062511] Advanced Linux Sound Architecture Driver Initialized.
   [    1.068898] Bluetooth: Core ver 2.22
   [    1.072023] NET: Registered PF_BLUETOOTH protocol family
   [    1.077322] Bluetooth: HCI device and connection manager initialized
   [    1.083674] Bluetooth: HCI socket layer initialized
   [    1.088545] Bluetooth: L2CAP socket layer initialized
   [    1.093596] Bluetooth: SCO socket layer initialized
   [    1.098875] clocksource: Switched to clocksource arch_sys_counter
   [    1.104738] VFS: Disk quotas dquot_6.6.0
   [    1.108487] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
   [    1.121488] NET: Registered PF_INET protocol family
   [    1.121684] IP idents hash table entries: 65536 (order: 7, 524288 bytes, linear)
   [    1.130875] tcp_listen_portaddr_hash hash table entries: 2048 (order: 3, 32768 bytes, linear)
   [    1.136679] Table-perturb hash table entries: 65536 (order: 6, 262144 bytes, linear)
   [    1.144401] TCP established hash table entries: 32768 (order: 6, 262144 bytes, linear)
   [    1.152524] TCP bind hash table entries: 32768 (order: 8, 1048576 bytes, linear)
   [    1.160513] TCP: Hash tables configured (established 32768 bind 32768)
   [    1.166308] UDP hash table entries: 2048 (order: 4, 65536 bytes, linear)
   [    1.173007] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes, linear)
   [    1.180232] NET: Registered PF_UNIX/PF_LOCAL protocol family
   [    1.186154] RPC: Registered named UNIX socket transport module.
   [    1.191646] RPC: Registered udp transport module.
   [    1.196340] RPC: Registered tcp transport module.
   [    1.201037] RPC: Registered tcp-with-tls transport module.
   [    1.206518] RPC: Registered tcp NFSv4.1 backchannel transport module.
   [    1.212965] PCI: CLS 0 bytes, default 64
   [    1.217267] Trying to unpack rootfs image as initramfs...
   [    1.223283] Initialise system trusted keyrings
   [    1.226834] workingset: timestamp_bits=46 max_order=20 bucket_order=0
   [    1.233858] NFS: Registering the id_resolver key type
   [    1.238215] Key type id_resolver registered
   [    1.242367] Key type id_legacy registered
   [    1.246401] nfs4filelayout_init: NFSv4 File Layout Driver Registering...
   [    1.253070] nfs4flexfilelayout_init: NFSv4 Flexfile Layout Driver Registering...
   [    1.260719] jffs2: version 2.2. (NAND) (SUMMARY)  © 2001-2006 Red Hat, Inc.
   [    1.323554] NET: Registered PF_ALG protocol family
   [    1.323625] xor: measuring software checksum speed
   [    1.328808]    8regs           :  2517 MB/sec
   [    1.333155]    32regs          :  2522 MB/sec
   [    1.337589]    arm64_neon      :  2368 MB/sec
   [    1.340554] xor: using function: 32regs (2522 MB/sec)
   [    1.345617] Key type asymmetric registered
   [    1.349694] Asymmetric key parser 'x509' registered
   [    1.354654] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 243)
   [    1.361965] io scheduler mq-deadline registered
   [    1.366486] io scheduler kyber registered
   [    1.370545] io scheduler bfq registered
   [    1.377554] irq-xilinx: /pl-bus/interrupt-controller@80020000: num_irq=32, edge=0x1
   [    1.387104] ledtrig-cpu: registered to indicate activity on CPUs
   [    1.425441] Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled
   [    1.427770] Serial: AMBA driver
   [    1.438266] brd: module loaded
   [    1.441975] loop: module loaded
   [    1.446940] CAN device driver interface
   [    1.447835] usbcore: registered new interface driver asix
   [    1.450547] usbcore: registered new interface driver ax88179_178a
   [    1.456674] usbcore: registered new interface driver cdc_ether
   [    1.462488] usbcore: registered new interface driver net1080
   [    1.468136] usbcore: registered new interface driver cdc_subset
   [    1.474053] usbcore: registered new interface driver zaurus
   [    1.479640] usbcore: registered new interface driver cdc_ncm
   [    1.485194] Freeing initrd memory: 5516K
   [    1.485289] usbcore: registered new interface driver r8153_ecm
   [    1.495449] VFIO - User Level meta-driver version: 0.3
   [    1.500892] usbcore: registered new interface driver uas
   [    1.505476] usbcore: registered new interface driver usb-storage
   [    1.511457] usbcore: registered new device driver onboard-usb-dev
   [    1.518682] rtc_zynqmp ffa60000.rtc: registered as rtc0
   [    1.522770] rtc_zynqmp ffa60000.rtc: setting system clock to 1970-01-15T02:01:09 UTC (1216869)
   [    1.531427] i2c_dev: i2c /dev entries driver
   [    1.537390] usbcore: registered new interface driver uvcvideo
   [    1.541374] Driver for 1-wire Dallas network protocol.
   [    1.547448] Bluetooth: HCI UART driver ver 2.3
   [    1.550950] Bluetooth: HCI UART protocol H4 registered
   [    1.556078] Bluetooth: HCI UART protocol BCSP registered
   [    1.561406] Bluetooth: HCI UART protocol LL registered
   [    1.566518] Bluetooth: HCI UART protocol ATH3K registered
   [    1.571931] Bluetooth: HCI UART protocol Three-wire (H5) registered
   [    1.578217] Bluetooth: HCI UART protocol Intel registered
   [    1.583592] Bluetooth: HCI UART protocol QCA registered
   [    1.588817] usbcore: registered new interface driver bcm203x
   [    1.594471] usbcore: registered new interface driver bpa10x
   [    1.600043] usbcore: registered new interface driver bfusb
   [    1.605521] usbcore: registered new interface driver btusb
   [    1.611018] usbcore: registered new interface driver ath3k
   [    1.616564] EDAC MC: ECC not enabled
   [    1.620337] EDAC DEVICE0: Giving out device to module zynqmp-ocm-edac controller zynqmp_ocm: DEV ff960000.memory-controller)
   [    1.632629] sdhci: Secure Digital Host Controller Interface driver
   [    1.638389] sdhci: Copyright(c) Pierre Ossman
   [    1.642744] sdhci-pltfm: SDHCI platform and OF driver helper
   [    1.648994] SMCCC: SOC_ID: ID = jep106:0049:0000 Revision = 0x24738093
   [    1.655003] zynqmp_firmware_probe Platform Management API v1.1
   [    1.660782] zynqmp_firmware_probe Trustzone version v1.0
   [    1.698075] securefw securefw: securefw probed
   [    1.698283] xilinx_ecdsa xilinx_ecdsa.0: ECDSA is not supported on the platform
   [    1.704591] zynqmp-aes zynqmp-aes.0: will run requests pump with realtime priority
   [    1.712197] zynqmp-sha3-384 zynqmp-sha3-384.0: will run requests pump with realtime priority
   [    1.720444] usbcore: registered new interface driver usbhid
   [    1.725868] usbhid: USB HID core driver
   [    1.732622] ARM CCI_400_r1 PMU driver probed
   [    1.733235] hw perfevents: enabled with armv8_cortex_a53 PMU driver, 7 (0,8000003f) counters available
   [    1.744499] fpga_manager fpga0: Xilinx ZynqMP FPGA Manager registered
   [    1.750264] usbcore: registered new interface driver snd-usb-audio
   [    1.756536] pktgen: Packet Generator for packet performance testing. Version: 2.75
   [    1.764326] Initializing XFRM netlink socket
   [    1.767766] NET: Registered PF_INET6 protocol family
   [    1.773264] Segment Routing with IPv6
   [    1.776370] In-situ OAM (IOAM) with IPv6
   [    1.780325] sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
   [    1.786533] NET: Registered PF_PACKET protocol family
   [    1.791220] NET: Registered PF_KEY protocol family
   [    1.796013] can: controller area network core
   [    1.800371] NET: Registered PF_CAN protocol family
   [    1.805132] can: raw protocol
   [    1.808091] can: broadcast manager protocol
   [    1.812270] can: netlink gateway - max_hops=1
   [    1.816703] Bluetooth: RFCOMM TTY layer initialized
   [    1.821495] Bluetooth: RFCOMM socket layer initialized
   [    1.826633] Bluetooth: RFCOMM ver 1.11
   [    1.830368] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
   [    1.835670] Bluetooth: BNEP filters: protocol multicast
   [    1.840892] Bluetooth: BNEP socket layer initialized
   [    1.845850] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
   [    1.851775] Bluetooth: HIDP socket layer initialized
   [    1.856762] 8021q: 802.1Q VLAN Support v1.8
   [    1.861092] 9pnet: Installing 9P2000 support
   [    1.865196] Key type dns_resolver registered
   [    1.869580] NET: Registered PF_VSOCK protocol family
   [    1.883182] registered taskstats version 1
   [    1.883326] Loading compiled-in X.509 certificates
   [    1.896016] Btrfs loaded, zoned=no, fsverity=no
   [    1.912919] ff000000.serial: ttyPS0 at MMIO 0xff000000 (irq = 25, base_baud = 6249375) is a xuartps
   [    1.922005] printk: legacy console [ttyPS0] enabled
   [    1.922005] printk: legacy console [ttyPS0] enabled
   [    1.926928] printk: legacy bootconsole [cdns0] disabled
   [    1.926928] printk: legacy bootconsole [cdns0] disabled
   [    1.976371] ff010000.serial: ttyPS2 at MMIO 0xff010000 (irq = 26, base_baud = 6249375) is a xuartps
   [    1.985815] of-fpga-region fpga-region: FPGA Region probed
   [    2.058495] xilinx-zynqmp-dpdma fd4c0000.dma-controller: Xilinx DPDMA engine is probed
   [    2.067343] spi-nor spi0.0: found mt25qu512a, expected m25p80
   [    2.074350] 3 fixed-partitions partitions found on MTD device spi0.0
   [    2.080745] Creating 3 MTD partitions on "spi0.0":
   [    2.085558] 0x000000000000-0x000001e00000 : "qspi-boot"
   [    2.092148] 0x000001e00000-0x000001e40000 : "qspi-bootenv"
   [    2.098554] 0x000001e40000-0x000004240000 : "qspi-kernel"
   [    2.150622] xilinx-axipmon ffa00000.perf-monitor: Probed Xilinx APM
   [    2.157451] xilinx-axipmon fd0b0000.perf-monitor: Probed Xilinx APM
   [    2.164075] xilinx-axipmon fd490000.perf-monitor: Probed Xilinx APM
   [    2.170701] xilinx-axipmon ffa10000.perf-monitor: Probed Xilinx APM
   [    2.178041] i2c i2c-0: using pinctrl states for GPIO recovery
   [    2.183976] i2c i2c-0: using generic GPIOs for recovery
   [    2.189621] pca953x 0-0020: supply vcc not found, using dummy regulator
   [    2.196313] pca953x 0-0020: using no AI
   [    2.201897] pca953x 0-0021: supply vcc not found, using dummy regulator
   [    2.208593] pca953x 0-0021: using no AI
   [    2.213252] pca954x 0-0075: supply vdd not found, using dummy regulator
   [    2.227693] i2c i2c-0: Added multiplexed i2c bus 2
   [    2.238660] i2c i2c-0: Added multiplexed i2c bus 3
   [    2.288283] i2c i2c-0: Added multiplexed i2c bus 4
   [    2.293216] i2c i2c-0: Added multiplexed i2c bus 5
   [    2.298015] pca954x 0-0075: registered 4 multiplexed busses for I2C mux pca9544
   [    2.305402] cdns-i2c ff020000.i2c: 400 kHz mmio ff020000 irq 49
   [    2.312455] i2c i2c-1: using pinctrl states for GPIO recovery
   [    2.318394] i2c i2c-1: using generic GPIOs for recovery
   [    2.324022] pca954x 1-0074: supply vdd not found, using dummy regulator
   [    2.331088] at24 6-0054: supply vcc not found, using dummy regulator
   [    2.337988] at24 6-0054: 1024 byte 24c08 EEPROM, writable, 1 bytes/write
   [    2.344735] i2c i2c-1: Added multiplexed i2c bus 6
   [    2.350127] si5341 7-0036: no regulator set, defaulting vdd_sel to 2.5V for out
   [    2.357447] si5341 7-0036: no regulator set, defaulting vdd_sel to 2.5V for out
   [    2.364763] si5341 7-0036: no regulator set, defaulting vdd_sel to 2.5V for out
   [    2.372083] si5341 7-0036: no regulator set, defaulting vdd_sel to 2.5V for out
   [    2.379396] si5341 7-0036: no regulator set, defaulting vdd_sel to 2.5V for out
   [    2.386701] si5341 7-0036: no regulator set, defaulting vdd_sel to 2.5V for out
   [    2.394013] si5341 7-0036: no regulator set, defaulting vdd_sel to 2.5V for out
   [    2.401327] si5341 7-0036: no regulator set, defaulting vdd_sel to 2.5V for out
   [    2.409413] si5341 7-0036: Chip: 5341 Grade: 1 Rev: 1
   [    2.438469] i2c i2c-1: Added multiplexed i2c bus 7
   [    2.445512] si570 8-005d: registered, current frequency 300000000 Hz
   [    2.451921] i2c i2c-1: Added multiplexed i2c bus 8
   [    2.458887] si570 9-005d: registered, current frequency 156250000 Hz
   [    2.465278] i2c i2c-1: Added multiplexed i2c bus 9
   [    2.470322] si5324 10-0069: si5328 probed
   [    2.524730] si5324 10-0069: si5328 probe successful
   [    2.529651] i2c i2c-1: Added multiplexed i2c bus 10
   [    2.534686] i2c i2c-1: Added multiplexed i2c bus 11
   [    2.539698] i2c i2c-1: Added multiplexed i2c bus 12
   [    2.544703] i2c i2c-1: Added multiplexed i2c bus 13
   [    2.549589] pca954x 1-0074: registered 8 multiplexed busses for I2C switch pca9548
   [    2.557338] pca954x 1-0075: supply vdd not found, using dummy regulator
   [    2.564277] i2c i2c-1: Added multiplexed i2c bus 14
   [    2.569304] i2c i2c-1: Added multiplexed i2c bus 15
   [    2.574339] i2c i2c-1: Added multiplexed i2c bus 16
   [    2.579386] i2c i2c-1: Added multiplexed i2c bus 17
   [    2.584405] i2c i2c-1: Added multiplexed i2c bus 18
   [    2.589424] i2c i2c-1: Added multiplexed i2c bus 19
   [    2.594457] i2c i2c-1: Added multiplexed i2c bus 20
   [    2.599472] i2c i2c-1: Added multiplexed i2c bus 21
   [    2.604351] pca954x 1-0075: registered 8 multiplexed busses for I2C switch pca9548
   [    2.611958] cdns-i2c ff030000.i2c: 400 kHz mmio ff030000 irq 50
   [    2.622586] cdns-wdt fd4d0000.watchdog: Xilinx Watchdog Timer with timeout 60s
   [    2.630143] cdns-wdt ff150000.watchdog: Xilinx Watchdog Timer with timeout 10s
   [    2.637811] cpufreq: cpufreq_online: CPU0: Running at unlisted initial frequency: 1199880 KHz, changing to: 1200000 KHz
   [    2.649380] nwl-pcie fd0e0000.pcie: host bridge /axi/pcie@fd0e0000 ranges:
   [    2.656300] nwl-pcie fd0e0000.pcie:      MEM 0x00e0000000..0x00efffffff -> 0x00e0000000
   [    2.664331] nwl-pcie fd0e0000.pcie:      MEM 0x0600000000..0x07ffffffff -> 0x0600000000
   [    2.672528] nwl-pcie fd0e0000.pcie: Link is DOWN
   [    2.677634] nwl-pcie fd0e0000.pcie: PCI host bridge to bus 0000:00
   [    2.683818] pci_bus 0000:00: root bus resource [bus 00-ff]
   [    2.689308] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xefffffff]
   [    2.696182] pci_bus 0000:00: root bus resource [mem 0x600000000-0x7ffffffff pref]
   [    2.703691] pci 0000:00:00.0: [10ee:d021] type 01 class 0x060400 PCIe Root Port
   [    2.711015] pci 0000:00:00.0: PCI bridge to [bus 00]
   [    2.715984] pci 0000:00:00.0:   bridge window [mem 0x00000000-0x000fffff]
   [    2.722776] pci 0000:00:00.0:   bridge window [mem 0x00000000-0x000fffff 64bit pref]
   [    2.730562] pci 0000:00:00.0: PME# supported from D0 D1 D2 D3hot
   [    2.738681] pci 0000:00:00.0: bridge configuration invalid ([bus 00-00]), reconfiguring
   [    2.746822] pci_bus 0000:01: busn_res: [bus 01-ff] end is updated to 01
   [    2.753446] pci 0000:00:00.0: PCI bridge to [bus 01]
   [    2.758413] pci_bus 0000:00: resource 4 [mem 0xe0000000-0xefffffff]
   [    2.764682] pci_bus 0000:00: resource 5 [mem 0x600000000-0x7ffffffff pref]
   [    2.773168] [drm] Initialized zynqmp-dpsub 1.0.0 for fd4a0000.display on minor 0
   [    2.803096] mmc0: SDHCI controller on ff170000.mmc [ff170000.mmc] using ADMA 64-bit
   [    3.041435] mmc0: new high speed SDHC card at address e624
   [    3.047348] mmcblk0: mmc0:e624 SL16G 14.8 GiB
   [    3.057378]  mmcblk0: p1
   [    3.818909] zynqmp-dpsub fd4a0000.display: [drm] Cannot find any crtc or sizes
   [    3.827726] zynqmp-dpsub fd4a0000.display: ZynqMP DisplayPort Subsystem driver probed
   [    3.835972] ahci-ceva fd0c0000.ahci: supply ahci not found, using dummy regulator
   [    3.843541] ahci-ceva fd0c0000.ahci: supply phy not found, using dummy regulator
   [    3.851036] ahci-ceva fd0c0000.ahci: supply target not found, using dummy regulator
   [    3.858975] ahci-ceva fd0c0000.ahci: AHCI vers 0001.0301, 32 command slots, 6 Gbps, platform mode
   [    3.867854] ahci-ceva fd0c0000.ahci: 2/2 ports implemented (port mask 0x3)
   [    3.874733] ahci-ceva fd0c0000.ahci: flags: 64bit ncq sntf pm clo only pmp fbs pio slum part ccc sds apst
   [    3.885240] scsi host0: ahci-ceva
   [    3.888901] scsi host1: ahci-ceva
   [    3.892335] ata1: SATA max UDMA/133 mmio [mem 0xfd0c0000-0xfd0c1fff] port 0x100 irq 59 lpm-pol 0
   [    3.901121] ata2: SATA max UDMA/133 mmio [mem 0xfd0c0000-0xfd0c1fff] port 0x180 irq 59 lpm-pol 0
   [    3.915299] macb ff0e0000.ethernet eth0: Cadence GEM rev 0x50070106 at 0xff0e0000 irq 47 (00:0a:35:07:8f:88)
   [    3.945052] xhci-hcd xhci-hcd.1.auto: xHCI Host Controller
   [    3.950585] xhci-hcd xhci-hcd.1.auto: new USB bus registered, assigned bus number 1
   [    3.958357] xhci-hcd xhci-hcd.1.auto: hcc params 0x0238f625 hci version 0x100 quirks 0x0000808002000810
   [    3.967794] xhci-hcd xhci-hcd.1.auto: irq 60, io mem 0xfe200000
   [    3.973803] xhci-hcd xhci-hcd.1.auto: xHCI Host Controller
   [    3.979290] xhci-hcd xhci-hcd.1.auto: new USB bus registered, assigned bus number 2
   [    3.986952] xhci-hcd xhci-hcd.1.auto: Host supports USB 3.0 SuperSpeed
   [    3.993610] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 6.12
   [    4.001875] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
   [    4.009102] usb usb1: Product: xHCI Host Controller
   [    4.013989] usb usb1: Manufacturer: Linux 6.12.10-xilinx-g0a0f70e531c7 xhci-hcd
   [    4.021305] usb usb1: SerialNumber: xhci-hcd.1.auto
   [    4.026560] hub 1-0:1.0: USB hub found
   [    4.030339] hub 1-0:1.0: 1 port detected
   [    4.034637] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 6.12
   [    4.042915] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
   [    4.050138] usb usb2: Product: xHCI Host Controller
   [    4.055020] usb usb2: Manufacturer: Linux 6.12.10-xilinx-g0a0f70e531c7 xhci-hcd
   [    4.062324] usb usb2: SerialNumber: xhci-hcd.1.auto
   [    4.067496] hub 2-0:1.0: USB hub found
   [    4.071261] hub 2-0:1.0: 1 port detected
   [    4.076114] input: gpio-keys as /devices/platform/gpio-keys/input/input0
   [    4.083194] of_cfs_init
   [    4.085651] of_cfs_init: OK
   [    4.088549] clk: Disabling unused clocks
   [    4.093432] PM: genpd: Disabling unused power domains
   [    4.098606] ALSA device list:
   [    4.101571]   #0: DisplayPort Monitor
   [    4.221157] ata2: SATA link down (SStatus 0 SControl 330)
   [    4.226580] ata1: SATA link down (SStatus 0 SControl 330)
   [    4.232802] Freeing unused kernel memory: 3200K
   [    4.237385] Run /init as init process
   [    4.874914] zynqmp-dpsub fd4a0000.display: [drm] Cannot find any crtc or sizes
   udhcpc: started, v1.36.1
   [    6.353064] macb ff0e0000.ethernet eth0: PHY [ff0e0000.ethernet-ffffffff:0c] driver [TI DP83867] (irq=POLL)
   [    6.362825] macb ff0e0000.ethernet eth0: configuring for phy/rgmii-id link mode
   [    6.370524] pps pps0: new PPS source ptp0
   [    6.374688] macb ff0e0000.ethernet: gem-ptp-timer ptp clock registered.
   udhcpc: broadcasting discover
   udhcpc: broadcasting discover
   udhcpc: broadcasting discover
   udhcpc: no lease, failing
   ERROR: There's no '/dev' on rootfs.
   
   sh: can't access tty; job control turned off
   ~ #
   ```

   > [!NOTE]
   >
   > Its useful to have the complete log as a reference. When future boots hang, you can see likely future messages This info can help narrow down boot issues.

# Reference

[Release notes](000037805 - PetaLinux 2025.1 - Product Update Release Notes and Known Issues) [archive](../petalinux-20251-release-notes)

UG1144 [archive](ug1144-petalinux-tools-reference-guide-en-us-2025.1.pdf)
