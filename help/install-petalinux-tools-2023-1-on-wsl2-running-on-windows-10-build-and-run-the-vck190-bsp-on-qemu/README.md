# Install PetaLinux Tools 2023.1 on WSL2 Running on Windows 10 & Build and Run the VCK190 BSP on QEMU

![AMD_logo_1](AMD_logo_1.png)

This post demonstrates how to **Install PetaLinux Tools 2023.1 on WSL2 Running on Windows 10 & Build and Run the VCK190 BSP on QEMU**.

## Computer Configuration

```
wsl --status
# Default Distribution: docker-desktop-data
# Default Version: 2

wsl -v
# WSL version: 1.2.5.0
# Kernel version: 5.15.90.1
# WSLg version: 1.0.51
# MSRDC version: 1.2.3770
# Direct3D version: 1.608.2-61064218
# DXCore version: 10.0.25131.1002-220531-1700.rs-onecore-base2-hyp
# Windows version: 10.0.19045.2846
```

```
systeminfo /fo csv | ConvertFrom-Csv | select OS*, System*, Hotfix* | Format-List -Property 'OS Version'
# OS Version : 10.0.19045 N/A Build 19045
```

```
$PSVersionTable
# Name                           Value
# ----                           -----
# PSVersion                      5.1.19041.2673
# PSEdition                      Desktop
# PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
# BuildVersion                   10.0.19041.2673
# CLRVersion                     4.0.30319.42000
# WSManStackVersion              3.0
# PSRemotingProtocolVersion      2.3
# SerializationVersion           1.1.0.1
```

## Download PetaLinux Tools and the VCK190 BSP

\# Download the PetaLinux Installer (TAR/GZIP - 3.18 GB) to Downloads from

https://www.xilinx.com/member/forms/download/xef.html?filename=petalinux-v2023.1-05012318-installer.run 

Note: MD5 SUM Value: 78fd08837e2d30541190a7ff20988e0f

\# Check MD5

\# Open a PowerShell

\# Run:

```
Get-FileHash -Path C:\Users\$env:username\Downloads\petalinux-v2023.1-05012318-installer.run  -Algorithm MD5
```

\# Download the VCK190 BSP (BSP - 1.99 GB) to Downloads from

https://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-vck190-v2023.1-05080224.bsp 

Note: MD5 SUM Value : a3c4dc3cd21ea0e2ba22b7bf5682cf25

\# Check MD5

\# Open a PowerShell

\# Run:

```
Get-FileHash -Path C:\Users\$env:username\Downloads\xilinx-vck190-v2023.1-05080224.bsp  -Algorithm MD5
```

\# Download **2023.1_PetaLinux_Package_List.xlsx** and README_content_v2023_1.txt from the bottom of https://support.xilinx.com/s/article/000035006?language=en_US 

\# List distributions

```
wsl --list --online
```

\# Note output:

```
The following is a list of valid distributions that can be installed.
Install using 'wsl.exe --install <Distro>'.
 
NAME                                   FRIENDLY NAME
Ubuntu                                 Ubuntu
Debian                                 Debian GNU/Linux
kali-linux                             Kali Linux Rolling
Ubuntu-18.04                           Ubuntu 18.04 LTS
Ubuntu-20.04                           Ubuntu 20.04 LTS
Ubuntu-22.04                           Ubuntu 22.04 LTS
OracleLinux_7_9                        Oracle Linux 7.9
OracleLinux_8_7                        Oracle Linux 8.7
OracleLinux_9_1                        Oracle Linux 9.1
SUSE-Linux-Enterprise-Server-15-SP4    SUSE Linux Enterprise Server 15 SP4
openSUSE-Leap-15.4                     openSUSE Leap 15.4
openSUSE-Tumbleweed                    openSUSE Tumbleweed
```

\# Install & Set Default (setting a default fixes [<u><span>this</span></u>](/help/wsl-error-3-wsl-8-error-createprocessentrycommon-370-getpwuid-0-failed-2) issue)

```
wsl --install Ubuntu-22.04
exit
wsl --set-default Ubuntu-22.04
# Check default
wsl --list
# Run
wsl
```

\# Get packages

Note: this downloads 638 MB

\# This differs from "Quick Installation steps for packages" in (2023.1\_PetaLinux\_Package\_List.xlsx) git instead of git-core, pylint instead of pylint3, no zlib1g:i386

```
sudo apt-get update
sudo apt-get install iproute2 gawk python3 python2 build-essential gcc git make net-tools libncurses5-dev tftpd zlib1g-dev libssl-dev flex bison libselinux1 gnupg wget git diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib automake screen pax gzip cpio python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint bc
```

\# Run:

```
sudo apt install libtinfo5
sudo apt install locales
sudo locale-gen en_US.UTF-8 # Select All
sudo dpkg-reconfigure locales # Select en_US.UTF-8
```

Note: this ^^^ fixes:

```
error loading hsi package: couldn't load file "libxv_commontasks.so": libtinfo.so.5: cannot open shared object file: No such file or directory on petalinux-build
```

\# Use bash

```
sudo dpkg-reconfigure dash
```

\# Select No

\# You should see:

```
Removing 'diversion of /bin/sh to /bin/sh.distrib by dash'
Adding 'diversion of /bin/sh to /bin/sh.distrib by bash'
Removing 'diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash'
Adding 'diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by bash'
```

\# In WSL2, Prepare to install PetaLinux Tools

```
chmod 755 "/mnt/c/Users/Zach Pfeffer/Downloads/petalinux-v2023.1-05012318-installer.run"
mkdir -p /home/$USER/petalinux/2023.1 && echo Success
cd "/mnt/c/Users/Zach Pfeffer/Downloads/"
./petalinux-v2023.1-05012318-installer.run --dir /home/$USER/petalinux/2023.1/
```

\# Press Enter q y q y

\# Note output:

```
INFO: Checking installation environment requirements...
WARNING: This is not a supported OS
INFO: Checking free disk space
INFO: Checking installed tools
environment: line 67: bc: command not found
WARNING: Seems like your machine does not have gcc 6 or greater version,
Please select Enable Buildtools Extended in petalinux-config --> Yocto Settings
INFO: Checking installed development libraries
INFO: Checking network and other services
WARNING: No tftp server found - please refer to "UG1144  PetaLinux Tools Documentation Reference Guide" for its impact and solution
INFO: Checking installer checksum...
INFO: Extracting PetaLinux installer...

LICENSE AGREEMENTS

PetaLinux SDK contains software from a number of sources.  Please review
the following licenses and indicate your acceptance of each to continue.

You do not have to accept the licenses, however if you do not then you may
not use PetaLinux SDK.

Use PgUp/PgDn to navigate the license viewer, and press 'q' to close

Press Enter to display the license agreements
Do you accept Xilinx End User License Agreement? [y/N] > y
Do you accept Third Party End User License Agreement? [y/N] > y
INFO: Installing PetaLinux...
INFO: Checking PetaLinux installer integrity...
INFO: Installing PetaLinux SDK to "/home/username/petalinux/2023.1/."
INFO: Installing buildtools in /home/username/petalinux/2023.1/./components/yocto/buildtools
INFO: Installing buildtools-extended in /home/username/petalinux/2023.1/./components/yocto/buildtools_extended
INFO: PetaLinux SDK has been installed to /home/username/petalinux/2023.1/.
```

\# Navigate to home

```
cd ~
pwd
```

\# Bring Up PetaLinux Tools

```
source /home/username/petalinux/2023.1/settings.sh
```

\# Note output:

```
# PetaLinux environment set to '/home/username/petalinux/2023.1'
# WARNING: This is not a supported OS
# INFO: Checking free disk space
# INFO: Checking installed tools
# INFO: Checking installed development libraries
# INFO: Checking network and other services
# WARNING: No tftp server found - please refer to "UG1144 2023.1 PetaLinux Tools Documentation Reference Guide" for its impact and solution
```

\# Run a small test

```
petalinux-create --help
```

You should see the "help" output

\# Build the BSP

```
mkdir -p ~/plxbsp/2023.1
cp "/mnt/c/Users/Zach Pfeffer/Downloads/xilinx-vck190-v2023.1-05080224.bsp" ~/plxbsp/2023.1/
cd ~
mkdir -p plxprj/2023.1
cd plxprj/2023.1
petalinux-create -t project -s ~/plxbsp/2023.1/xilinx-vck190-v2023.1-05080224.bsp
```

\# Note output:

```
INFO: Create project:
INFO: Projects:
INFO:   * xilinx-vck190-2023.1
INFO: Has been successfully installed to /home/username/plxprj/2023.1/
INFO: New project successfully created in /home/username/plxprj/2023.1/
```

\# Build the BSP

```
cd ~/plxprj/2023.1/xilinx-vck190-2023.1
petalinux-build
```

\# Note output:

```
[INFO] Sourcing buildtools
[INFO] Building project
[INFO] Generating Kconfig for project
[INFO] Silentconfig project
[INFO] Generating kconfig for rootfs
[INFO] Silentconfig rootfs
[INFO] Adding user layers
[INFO] Generating machine conf file
[INFO] Generating plnxtool conf file
[INFO] Generating workspace directory
INFO: bitbake petalinux-image-minimal
NOTE: Started PRServer with DBfile: /home/username/plxprj/2023.1/xilinx-vck190-2023.1/build/cache/prserv.sqlite3, Address: 127.0.0.1:33273, PID: 21389
WARNING: You are running bitbake under WSLv2, this works properly but you should optimize your VHDX file eventually to avoid running out of storage space
Loading cache: 100% |                                                                                                                                                                                             | ETA:  --:--:--
Loaded 0 entries from dependency cache.
Parsing recipes: 100% |############################################################################################################################################################################################| Time: 0:02:55
Parsing of 4346 .bb files complete (0 cached, 4346 parsed). 6277 targets, 311 skipped, 1 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
NOTE: Fetching uninative binary shim file:///home/username/plxprj/2023.1/xilinx-vck190-2023.1/components/yocto/downloads/uninative/5fab9a5c97fc73a21134e5a81f74498cbaecda75d56aab971c934e0b803bcc00/x86_64-nativesdk-libc-3.8.1.tar.xz;sha256sum=5fab9a5c97fc73a21134e5a81f74498cbaecda75d56aab971c934e0b803bcc00 (will check PREMIRRORS first)
Initialising tasks: 100% |#########################################################################################################################################################################################| Time: 0:00:09
Checking sstate mirror object availability: 100% |#################################################################################################################################################################| Time: 0:00:52
Sstate summary: Wanted 1745 Local 0 Mirrors 1524 Missed 221 Current 0 (87% match, 0% complete)
NOTE: Executing Tasks
WARNING: zocl-202310.2.15.0-r0 do_package_qa: QA Issue: File /lib/modules/6.1.5-xilinx-v2023.1/extra/zocl.ko in package kernel-module-zocl-6.1.5-xilinx-v2023.1 contains reference to TMPDIR [buildpaths]
NOTE: Tasks Summary: Attempted 4616 tasks of which 3794 didn't need to be rerun and all succeeded.

Summary: There were 2 WARNING messages.
INFO: Failed to copy built images to tftp dir: /tftpboot
[INFO] Successfully built project
```

\# Package the BSP

Note: you will get a "can't find BOOT.BIN error if you don't run this"

```
petalinux-package --boot --u-boot
```

\# Note output:

```
[INFO] Sourcing buildtools
INFO: File in BOOT BIN: "/home/username/plxprj/2023.1/xilinx-vck190-2023.1/project-spec/hw-description/vpl_gen_fixed.pdi"
INFO: File in BOOT BIN: "/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/plm.elf"
INFO: File in BOOT BIN: "/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/psmfw.elf"
INFO: File in BOOT BIN: "/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/system-default.dtb"
INFO: File in BOOT BIN: "/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/bl31.elf"
INFO: File in BOOT BIN: "/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/u-boot.elf"
INFO: Generating versal binary package BOOT.BIN...


****** Bootgen v2023.1
  **** Build date : Apr  7 2023-10:18:04
    ** Copyright 1986-2022 Xilinx, Inc. All Rights Reserved.
    ** Copyright 2022-2023 Advanced Micro Devices, Inc. All Rights Reserved.


[INFO]   : Bootimage generated successfully

INFO: Generating QEMU boot images...
INFO:  File in qemu_boot.img: /home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/BOOT.BIN
INFO:  File in qemu_boot.img: /home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/ramdisk.cpio.gz.u-boot
INFO:  File in qemu_boot.img: /home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/boot.scr
INFO: Binary is ready.
WARNING: Unable to access the TFTPBOOT folder /tftpboot!!!
WARNING: Skip file copy to TFTPBOOT folder!!!
```

## Boot on QEMU

Note: this will appear to hang for a minute

```
petalinux-boot --qemu --kernel
```

\# Note output:

```
[INFO] Sourcing buildtools
INFO: No DTB has been specified, use the default one "/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/system.dtb".
INFO: Starting microblaze QEMU
INFO: Starting the above QEMU command in the background
INFO:  qemu-system-microblazeel -M microblaze-fdt  -serial mon:stdio -display none -device loader,addr=0xf0000000,data=0xba020004,data-len=4 -device loader,addr=0xf0000004,data=0xb800fffc,data-len=4 -device loader,file=/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/pmc_cdo.bin,addr=0xf2000000 -device loader,file=/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/BOOT_bh.bin,addr=0xf201e000,force-raw=on -device loader,file=/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/plm.elf      -hw-dtb /home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/versal-qemu-multiarch-pmc.dtb -machine-path /tmp/tmp.lkiXYlX5gW -device loader,addr=0xF1110624,data=0x0,data-len=4 -device loader,addr=0xF1110620,data=0x1,data-len=4
INFO: TCP PORT is free 9000
INFO: Starting aarch64 QEMU
INFO:  qemu-system-aarch64 -M arm-generic-fdt  -serial null -serial null  -serial mon:stdio -serial /dev/null -display none -boot mode=5 -drive if=sd,index=1,file=/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/qemu_boot.img,format=raw -device loader,file=/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/ramdisk.cpio.gz.u-boot,addr=0x04000000,force-raw=on -device loader,file=/home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/Image,addr=0x00200000,force-raw=on -gdb tcp::9000   -net nic,netdev=eth0 -netdev user,id=eth0,tftp=/tftpboot -net nic   -hw-dtb /home/username/plxprj/2023.1/xilinx-vck190-2023.1/images/linux/versal-qemu-multiarch-ps.dtb -machine-path /tmp/tmp.lkiXYlX5gW   -m 8G
qemu-system-microblazeel: Failed to connect to '/tmp/tmp.lkiXYlX5gW/qemu-rport-_ps_pmc_rp@0': No such file or directory
qemu-system-microblazeel: info: QEMU waiting for connection on: disconnected:unix:/tmp/tmp.lkiXYlX5gW/qemu-rport-_ps_pmc_rp@0,server=on
qemu-system-aarch64: warning: hub 0 is not connected to host network
QEMU 7.1.0 monitor - type 'help' for more information
# (qemu)
```

It'll look like it hangs here ^^^. Wait a minute, then you should see:

```
[13425.428]****************************************
[13426.148]Xilinx Versal Platform Loader and Manager
[13426.371]Release 2023.1   May  1 2023  -  00:38:12
[13427.046]Platform Version: v0.0 PMC: v0.0, PS: v0.0
```

...

```
[   24.231715] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
udhcpc: broadcasting discover
udhcpc: broadcasting select for 10.0.2.15, server 10.0.2.2
udhcpc: lease of 10.0.2.15 obtained from 10.0.2.2, lease time 86400
/etc/udhcpc.d/50default: Adding DNS 10.0.2.3
ERROR: There's no '/dev' on rootfs.

sh: can't access tty; job control turned off
/ #
```

\# Type **ctrl-a x** to qut QEMU

## Summary

This post has demonstrated how to **Install PetaLinux Tools 2023.1 on WSL2 Running on Windows 10 & Build and Run the VCK190 BSP on QEMU.**

## References

-   Finding Checksum Values in Windows 10 [<u><span>https://answers.microsoft.com/en-us/windows/forum/all/finding-checksum-values-in-windows-10/dbc3c569-4b5a-4967-8810-c25255cdc1fd</span></u>](https://answers.microsoft.com/en-us/windows/forum/all/finding-checksum-values-in-windows-10/dbc3c569-4b5a-4967-8810-c25255cdc1fd)
    
-   What's New in Embedded Software and Tools 2023.1 [<u><span>https://www.xilinx.com/products/design-tools/embedded-software/whats-new.html#2023-1</span></u>](https://www.xilinx.com/products/design-tools/embedded-software/whats-new.html#2023-1)
    
-   PetaLinux Tools Documentation: Reference Guide (UG1144) [<u><span>https://docs.xilinx.com/r/en-US/ug1144-petalinux-tools-reference-guide/Steps-to-Set-Up-PetaLinux-Working-Environment</span></u>](https://docs.xilinx.com/r/en-US/ug1144-petalinux-tools-reference-guide/Steps-to-Set-Up-PetaLinux-Working-Environment)
    
-   /bin/bash: warning: setlocale: LC\_ALL: cannot change locale (en\_US.UTF-8) [<u><span>https://stackoverflow.com/questions/66859800/bin-bash-warning-setlocale-lc-all-cannot-change-locale-en-us-utf-8</span></u>](https://stackoverflow.com/questions/66859800/bin-bash-warning-setlocale-lc-all-cannot-change-locale-en-us-utf-8)
    
-   petalinux-config error when importing hardware configuration [<u><span>https://support.xilinx.com/s/question/0D52E00006tcCJ9SAM/petalinuxconfig-error-when-importing-hardware-configuration?language=en_US</span></u>](https://support.xilinx.com/s/question/0D52E00006tcCJ9SAM/petalinuxconfig-error-when-importing-hardware-configuration?language=en_US)
    
-   AMD Logo from [<u><span>link</span></u>](https://library.amd.com/web/241bcd26472f10b9/amd-corporate-logo/?mediaId=8C984466-7CF4-4E8C-9D5433E63251D45B)
