# 70277 - PetaLinux 2017.4 - Product Update Release Notes and Known Issues

## Title

70277 - PetaLinux 2017.4 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2017.4 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for 2017.4 PetaLinux Release**

This table contains supported BSPs for Zynq-7000, MicroBlaze, Zynq UltraScale+ MPSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

| Platform               | Variant                   | BSP Name                   |
| :--------------------- | :------------------------ | :------------------------- |
| Zynq-7000              | ZC702                     | ZC702 BSP                  |
| Zynq-7000              | ZC706                     | ZC706 BSP                  |
| Zynq-7000              | ZEDBOARD                  | ZED BSP                    |
| MicroBlaze             | AC701                     | AC701 BSP                  |
| MicroBlaze             | KCU105                    | KCU105                     |
| MicroBlaze             | KC705                     | KC705 BSP                  |
| Zynq UltraScale+ MPSoC | ZCU102 production silicon | ZCU102 BSP (prod-silicon)  |
| Zynq UltraScale+ MPSoC | ZCU102 ZU9 ES2 Rev 1.0    | ZCU102-ZU9-ES2 Rev 1.0 BSP |

**Note**: The "[sstate cache file](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate-rel-v2017.4.tar.gz&akdm=1)" (sstate-rel-v2017.4.tar.gz) can be found on the Xilinx download area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2017.4_README&akdm=0) (sstate_rel_2017.4_README) file that outlines the procedure to use "sstate cache".

Refer to the attached file "2017.4-PetaLinux-Packages-List" for software package versions tested on host machines, which is required for PetaLinux installation tools.

Follow the attached README for steps to create BSPs using template flow.

**PetaLinux 2017.4contains the following build collateral:**

| Component                  | Git repo                                                     | Branches/Tag   | Commit ID                                | Comments                                                     |
| :------------------------- | :----------------------------------------------------------- | :------------- | :--------------------------------------- | :----------------------------------------------------------- |
| FSBL                       | git://github.com/Xilinx/embeddedsw.git                       | xilinx-v2017.4 | 77448ae629133607b66e747c4baaa7677dc1123d | FSBL for Zynq7000 is at `embeddedsw/lib/sw_apps/zynq_fsbl`<br>FSBL for Zynq UltraScale+ is at `embeddedsw/lib/sw_apps/zynqmp_fsbl` |
| PMU Firmware               | git://github.com/Xilinx/embeddedsw.git                       | xilinx-v2017.4 | 77448ae629133607b66e747c4baaa7677dc1123d | PMU for Zynq UltraScale+ Firmware is at `embeddedsw/lib/sw-apps/zynqmp_pmufw` |
| Device-tree                | git://github.com/Xilinx/device-tree-xlnx.git                 | xilinx-v2017.4 | 3c7407f6f802461cd5ba8545e82c64fbd177452b |                                                              |
| Linux                      | git://github.com/Xilinx/linux-xlnx.git                       | xilinx-v2017.4 | b450e900fdb473a53613ad014f31eedbc80b1c90 | Kernel Version 4.9                                           |
| U-Boot                     | git://github.com/Xilinx/u-boot-xlnx.git                      | xilinx-v2017.4 | 5fa7d2ed066166571e969d036c1871c1759a921d | U-Boot Version 2017.01                                       |
| QEMU                       | git://github.com/Xilinx/qemu.git                             | xilinx-v2017.4 | 1d9d9d8bdb02aa2ab316e6571d495b8090f8a25d |                                                              |
| Xen                        | git://github.com/Xilinx/xen.git                              | xilinx-v2017.4 | 75c00aca503fe7093ccfecb3d0dd803642cb7bae |                                                              |
| ARM-Trusted-Firmware (ATF) | git://github.com/Xilinx/arm-trusted-firmware.git             | xilinx-v2017.4 | 47af34b94a52b8cdc8abbac44b6f3ffab33a2206 | ATF is based on upstream version 1.3                         |
| Yocto                      | git://github.com/Xilinx/meta-xilinx.git<br>git://github.com/Xilinx/meta-xilinx-tools.git<br>git://github.com/Xilinx/meta-petalinux.git | rel-v2017.4    |                                          | Yocto 2.2 Morty                                              |
| qemu-devicetrees           | git://github.com/Xilinx/qemu-devicetrees.git                 | xilinx-v2017.4 | 4b951c594078562e9dd828430075968dd91ac425 |                                                              |
| OpenAMP                    | git://github.com/Xilinx/open-amp.git                         | xilinx-v2017.4 | b041167a42a75f08c7b709622158f8d9d346a594 |                                                              |
| libmetal                   | git://github.com/Xilinx/libmetal.git                         | xilinx-v2017.4 | 962bc1fe8df758bfea0fe831f0c1192e1f6045b8 |                                                              |
| GCC                        |                                                              |                |                                          | MB compiler version 6.2<br>ARM 6.2                           |

**Wiki Updates:**

Covers details for Linux Kernel, Device drivers, U-boot, ATF and DTG changes (new features/fixes) in a particular release.

**2017.4 Linux and DTG release notes wiki page:**

http://www.wiki.xilinx.com/2017.4+Linux+and+DTG+Release+Notes

**2017.4 U-Boot release notes wiki page :**

http://www.wiki.xilinx.com/2017.4+U-boot+Release+Notes

**2017.4 ATF release notes wiki page :**

http://www.wiki.xilinx.com/2017.4+ATF+Release+Notes

 

**2017.4 New Features:**

 

**PetaLinux**

 

- None

**Yocto**

- Upgrade DTC(poky/meta/recipes-kernel/dtc) from v1.4.1 to v1.4.4

 

 

**FSBL**

 

- None

 

**U-boot**

 

- None

 

**Device-tree**

 

- None

 

**ARM-Trusted Firmware (ATF)**

 

 

- None

 

**FreeRTOS**

 

- None

 

**PMU Firmware (PMUFW)**

 

- None

 

**Power Management**

 

- None

 

**Standalone**

 

- None

**Linux Drivers**

- None

**OpenAMP and Libmetal**

 

- None

**QEMU**

 

- None

**VCU**

- None

 

**Known Issues for 2017.4:**

| Linux/Standalone | Application   | Description                                                  | Work-around           | To be fixed version |
| :--------------- | :------------ | :----------------------------------------------------------- | :-------------------- | :------------------ |
| Linux            | Documentation | 2017.3/4 PetaLinux: Ubuntu 16.04.1 version in supported linux distribution doesn't align with UG973 and UG1144. | (Xilinx Answer 70395) | 2018.1              |
| Linux            | Drivers       | 2017.1-2017.4 Zynq UltraScale+ MPSoC: Linux MACB MDIO support for single MAC managing multiple PHYs | (Xilinx Answer 69132) | 2018.1              |
| Linux            | QEMU          | 2017.1-2017.4 U-boot: spi_flash_probe_bus_cs() failed with KCU105 and AC701 QEMU | (Xilinx Answer 69103) | 2018.1              |
| Linux            | Drivers       | 2017.1-2017.4 Zynq UltraScale+ MPSoC: Linux hangs when accessing PL peripheral generated by Yocto | (Xilinx Answer 69587) | 2018.1              |
| Linux            | XSDK          | 2017.x-2018.1 Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle | (Xilinx Answer 69143) |                     |
| Linux            | PetaLinux     | Zynq UltraScale+ MPSoC: How to enable UHS (SD 3.0) support for ZCU102 and ZCU106 evaluation board PetaLinux BSPs | (Xilinx Answer 69978) |                     |
| Linux            | PetaLinux     | 2016.4-2017.4 Zynq UltraScale+ MPSoC: PetaLinux does not correctly override the U-boot environment variables to set SD boot when both eMMC(SDIO0) and SD(SDIO1) are enabled in design | (Xilinx Answer 69780) | 2018.1              |
| Linux            | Device-tree   | 2017.1-2017.4 Zynq UltraScale+ MPSoC: Linux mmcblk0 error -110 sending stop command, original cmd response 0x900, card status 0xe00 using Swissbit SD card | (Xilinx Answer 69995) | 2018.1              |
| Linux            | PetaLinux     | 2017.1-2017.4 PetaLinux: QEMU flash_stripe.c is not included in the QEMU utilities shipped with PetaLinux | (Xilinx Answer 69975) | 2018.1              |
| Linux            | Device-tree   | 2017.1-2017.4 Zynq UltraScale+ MPSoC: Linux causes a hang in RPU code which was running fine until Linux loaded | (Xilinx Answer 70009) | 2018.1              |
| Linux            | Drivers       | 2016.4-2017.4 Zynq UltraScale+ MPSoC: Linux DDR EDAC driver unable to inject ECC errors when using either 32-bit DQ width, address mapping or Bank/Row/Column addressing mode | (Xilinx Answer 69997) | 2018.1              |
| Linux            | Device-tree   | 2016.4-2017.4 PetaLinux: DTG build error with 16G PL DDR value out of range for 32-bit array element | (Xilinx Answer 70285) | 2018.1              |
| Linux            | Drivers       | 2017.1-2017.4 Zynq-7000, Zynq UltraScale+ MPSoC: Linux AXI INTC cascade to GIC doesn't generate interrupts with edge-triggered interrupt type | (Xilinx Answer 70286) | 2018.1              |
| Standalone       | FreeRTOS      | 2017.4 Zynq UltraScale+ MPSoC: Jumbo frames does not work in FreeRTOS LWIP example for R5 core | (Xilinx Answer 70287) | 2018.1              |
| Linux            | Device-tree   | 2017.3/4 PetaLinux: DTG build error (Value out of range for 32-bit array element) for MIG DDR with ECC enabled | (Xilinx Answer 70296) | 2018.1              |
| Standalone       | XSDK          | 2017.4 Zynq UltraScale+ MPSoC: FSBL error of XFSBL_DECRYPT:XFSBL_ERROR_BITSTREAM_GCM_TAG_MISMATCH | (Xilinx Answer 70302) | 2018.1              |
| Linux            | PMUFW         | 2017.4 Zynq UltraScale+ MPSoC: Linux Power Management FPD off suspend/resume stress test failed | (Xilinx Answer 70303) | 2018.1              |
| Linux            | PetaLinux     | 2017.1-2017.4 PetaLinux: Removing DTB "from boot image" settings causes U-Boot to fail to load ramdisk image.ub | (Xilinx Answer 70304) | 2018.1              |
| Linux            | Device-tree   | 2017.3/4 Zynq-7000: DTG does not build for single core Zynq design | (Xilinx Answer 70402) | 2018.1              |
| Linux            | PetaLinux     | 2016.4-2018.1 PetaLinux: Kernel configurations dependencies are not pulled properly when we use external source with kernel | (Xilinx Answer 71102) | 2018.2              |
| Linux            | Device-tree   | 2017.4 Zynq UltraScale+ MPSoC: DTG does not build without UART in design | (Xilinx Answer 71267) | 2018.1              |

# README_content

================================

Contents in the down load area
================================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for down load:


1.	PetaLinux 2017.4 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2017.4 Open Components Source Code (TAR/GZIP) file: 
-----------------------------------------------------------------------

	This file contains the source code of all the SW components shipped as 
part of the PetaLinux tool. It also contains the source code for all the 
SW packages, available at https://petalinux.xilinx.com/ that petaLinux tool packages
 in the project, when selected. This file is provide as part of legal requirement 
for your viewing only. It is not required to be downloaded for using 
the PetaLinux tool or BSPs.


Sample list of components in the files 1) and 2):

---------------------------------------------

		QEMU
	
		busybox
	
		mtd-utils
	
		libfdt
	
		dtc
	
		u-boot
	
		device-tree-generator
	
		iso-codes
	
		ca-certificates
	
		db
	
		bash
	
		Linux
	
		ATF
	
		XEN
	
		kconfig-frontends
	
		Note: more than 1000 other SW components.

# 2017.4-PetaLinux-Packages-List

## Tool/Library Versions

### RHEL/CentOS versions

| Tool/Library                                                 | CentOS 7.2                                                  | Centosn7.3                                                   | RHEL 7.2                                                  | RHEL 7.3                                                     |
| ------------------------------------------------------------ | ----------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------------------ |
| kernel Version                                               | 3.10.0-514.21.2.el7.x86_64                                  | 3.10.0-514.el7.x86_64                                        | 3.10.0-327.el7.x86_64                                     | 3.10.0-514.el7.x86_64                                        |
| python                                                       | Pyton 3                                                     | python 3                                                     | python 3                                                  | python 3                                                     |
| dos2unix                                                     | dos2unix-6.0.3-4.el7.x86_64                                 | dos2unix-3.1-37.el6.x86_64                                   | dos2unix-6.0.3-4.el7.x86_64                               | dos2unix-6.0.3-4.el7.x86_64                                  |
| ip (iproute)                                                 | iproute-3.10.0-74.0.1.el7.x86_64                            | iproute-3.10.0-74.el7.x86_64                                 | iproute-3.10.0-74.0.1.el7.x86_64                          | iproute-3.10.0-74.0.1.el7.x86_64                             |
| gawk                                                         | gawk-4.0.2-4.el7.x86_64                                     | gawk-4.0.2-4.el7.x86_64                                      | gawk-4.0.2-4.el7.x86_64                                   | gawk-4.0.2-4.el7.x86_64                                      |
| xvfb                                                         | xorg-x11-server-Xvfb-1.17.2-22.el7.x86_64                   | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                     | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                  | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                     |
| gcc                                                          | gcc-4.8.5-11.el7.x86_64                                     | gcc-4.8.5-11.el7.x86_64                                      | gcc-4.8.5-11.el7.x86_64                                   | gcc-4.8.5-11.el7.x86_64                                      |
| git                                                          | git-1.8.3.1-6.el7_2.1.x86_64                                | git-1.8.3.1-6.el7_2.1.x86_64                                 | git-1.8.3.1-6.el7_2.1.x86_64                              | git-1.8.3.1-6.el7_2.1.x86_64                                 |
| make                                                         | make-3.82-23.el7.x86_64                                     | make-3.82-23.el7.x86_64                                      | make-3.82-23.el7.x86_64                                   | make-3.82-23.el7.x86_64                                      |
| netstat (net-tools)                                          | net-tools-2.0-0.17.20131004git.el7.x86_64                   | net-tools-2.0-0.20150915git.4.mga6.x86_64                    | net-tools-2.0-0.17.20131004git.el7.x86_64                 | net-tools-2.0-0.17.20131004git.el7.x86_64                    |
| ncurses-devel                                                | ncurses-devel-5.9-13.20130511.el7.x86_64                    | ncurses-devel-5.9-13.20130511.el7.x86_64                     | ncurses-devel-5.9-13.20130511.el7.x86_64                  | ncurses-devel-5.9-13.20130511.el7.x86_64                     |
| tftp-server                                                  | tftp-server-5.2-13.el7.x86_64                               | tftp-server-0.49-8.el6.x86_64                                | tftp-server-5.2-13.el7.x86_64                             | tftp-server-5.2-13.el7.x86_64                                |
| zlib-devel(also,install 32-bit of this version)              | zlib-devel-1.2.7-17.el7.x86_64 zlib-devel-1.2.7-17.el7.i686 | zlib-devel-1.2.7-17.el7.x86_64                               | zlib-devel-1.2.7-17.el7.x86_64                            | zlib-devel-1.2.7-17.el7.x86_64 zlib-devel-1.2.7-17.el7.i686  |
| openssl-devel                                                | openssl-devel-1.0.1e-60.0.1.el7_3.1.x86_64                  | openssl-devel-1.0.1e-60.el7.x86_64                           | openssl-devel-1.0.1e-60.el7_3.1.x86_64                    | openssl-devel-1.0.1e-60.0.1.el7_3.1.x86_64                   |
| flex                                                         | flex-2.5.37-3.el7.x86_64                                    | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                                  | flex-2.5.37-3.el7.x86_64                                     |
| bison                                                        | bison-2.7-4.el7.x86_64                                      | bison-2.7-4.el7.x86_64                                       | bison-2.7-4.el7.x86_64                                    |                                                              |
| libselinux                                                   | libselinux-2.5-6.el7.x86_64                                 | libselinux-2.5-6.el7.x86_64                                  | libselinux-2.5-6.el7.x86_64                               | libselinux-2.5-6.el7.x86_64                                  |
| gnupg                                                        | gnupg-1.4.21                                                | gnupg-1.4.21                                                 | gnupg-1.4.21                                              |                                                              |
| wget                                                         | wget-1.14-13.el7.x86_64                                     | wget-1.14-13.el7.x86_64                                      | wget-1.14-13.el7.x86_64                                   | wget-1.14-13.el7.x86_64                                      |
| diffstat                                                     | diffstat-1.57-4.el7.x86_64                                  | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                                | diffstat-1.57-4.el7.x86_64                                   |
| chrpath                                                      | chrpath-0.13-14.el7.x86_64                                  | chrpath-0.13-14.el7.x86_64                                   | chrpath-0.13-14.el7.x86_64                                | chrpath-0.13-14.el7.x86_64                                   |
| socat                                                        | socat-1.7.2.2-5.el7.x86_64                                  | socat-1.7.2.2-5.el7.x86_64                                   | socat-1.7.2.2-5.el7.x86_64                                | socat-1.7.2.2-5.el7.x86_64                                   |
| xterm                                                        | xterm-295-3.el7.x86_64                                      | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                                    | xterm-295-3.el7.x86_64                                       |
| autoconf                                                     | autoconf-2.69-11.el7.noarch                                 | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                               | autoconf-2.69-11.el7.noarch                                  |
| libtool                                                      | libtool-2.4.2-22.el7_3.x86_64                               | libtool-2.4.2-21.el7_2.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                             | libtool-2.4.2-22.el7_3.x86_64                                |
| tar                                                          | tar-1.26-31.el7.x86_64                                      | tar-1.26-31.el7.x86_64                                       | tar-1.26-31.el7.x86_64                                    | tar-1.26-31.el7.x86_64                                       |
| unzip                                                        | unzip-6.0-16.el7.x86_64                                     | unzip-6.0-16.el7.x86_64                                      | unzip-6.0-16.el7.x86_64                                   | unzip-6.0-16.el7.x86_64                                      |
| texinfo                                                      | texinfo-5.1-4.el7.x86_64                                    | texinfo-5.1-4.el7.x86_64                                     | texinfo-5.1-4.el7.x86_64                                  | texinfo-5.1-4.el7.x86_64                                     |
| zlib1g-dev                                                   |                                                             |                                                              |                                                           |                                                              |
| gcc-multilib                                                 |                                                             |                                                              |                                                           |                                                              |
| build-essential                                              |                                                             |                                                              |                                                           |                                                              |
| libsdl1.2-dev                                                |                                                             |                                                              |                                                           |                                                              |
| libglib2.0-dev                                               |                                                             |                                                              |                                                           |                                                              |
| SDL-devel                                                    | SDL-devel-1.2.15-14.el7.x86_64                              | SDL-devel-1.2.15-14.el7.x86_64                               | SDL-devel-1.2.15-14.el7.x86_64                            | SDL-devel-1.2.15-14.el7.i686                                 |
| glibc-devel                                                  | glibc-devel-2.17-157.el7_3.4.x86_64                         | glibc-devel-2.17-157.el7_3.4.i686 glibc-devel-2.17-157.el7_3.4.x86_64 | glibc-devel-2.17-157.el7_3.4.x86_64                       | glibc-devel-2.17-157.el7_3.4.x86_64 glibc-devel-2.17-157.el7_3.4.i686 |
| 32-bit glibc                                                 | glibc-2.17-157.el7_3.4.i686 glibc-2.17-157.el7_3.4.x86_64   | glibc-2.17-157.el7_3.4.i686 glibc-2.17-157.el7_3.4.x86_64    | glibc-2.17-157.el7_3.4.x86_64 glibc-2.17-157.el7_3.4.i686 | glibc-2.17-157.el7_3.4.x86_64 glibc-2.17-157.el7_3.4.i686    |
| glib2-devel                                                  | glib2-devel-2.46.2-4.el7.x86_64                             | glib2-devel-2.46.2-4.el7.x86_64                              | glib2-devel-2.46.2-4.el7.x86_64                           | glib2-devel-2.46.2-4.el7.x86_64                              |
| automake                                                     | automake-1.13.4-3.el7.noarch                                | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                              | automake-1.13.4-3.el7.noarch                                 |
| screen                                                       | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64            | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64          | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             |
| pax                                                          | pax-3.4-19.el7.x86_64                                       |                                                              | pax-3.4-19.el7.x86_64                                     | pax-3.4-19.el7.x86_64                                        |
| gzip                                                         | gzip-1.5-8.el7.x86_64                                       | gzip-1.5-8.el7.x86_64                                        | gzip-1.5-8.el7.x86_64                                     | gzip-1.5-8.el7.x86_64                                        |
| libz.so.1                                                    |                                                             | libz.so.1                                                    |                                                           |                                                              |
| libstdc++                                                    | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686   | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686    | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686 | libstdc++-4.8.5-11.el7.i686                                  |
| g++ (gcc-c++)                                                | gcc-c++-4.8.5-11.el7.x86_64                                 | gcc-c++-4.8.5-11.el7.x86_64                                  | gcc-c++-4.8.5-11.el7.x86_64                               | gcc-c++-4.8.5-11.el7.x86_64                                  |
| patch                                                        | patch-2.7.1-8.el7.x86_64                                    | patch-2.7.1-8.el7.x86_64                                     | patch-2.7.1-8.el7.x86_64                                  | patch-2.7.1-8.el7.x86_64                                     |
| lsb_release                                                  |                                                             |                                                              |                                                           |                                                              |
| zlib                                                         | zlib-1.2.7-17.el7.x86_64 zlib-1.2.7-17.el7.i686             | zlib-1.2.7-17.el7.x86_64 zlib-1.2.7-17.el7.i686              | zlib-1.2.7-17.el7.x86_64 zlib-1.2.7-17.el7.i686           | zlib-1.2.7-17.el7.x86_64 zlib-1.2.7-17.el7.i686              |
|                                                              |                                                             |                                                              |                                                           |                                                              |
| Note: The cells with empty fields were not installed. Top row kernel version is shipped from distribution |                                                             |                                                              |                                                           |                                                              |

### Ubuntu

| Tool/Library                                                 | Ubuntu 16.04 Server                | Ubuntu 16.04 LTS Desktop(GNOME)    |
| ------------------------------------------------------------ | ---------------------------------- | ---------------------------------- |
| kernel Version                                               | 4.4.0-21-generic                   | 4.4.0-21-generic                   |
| python                                                       | python 3                           | python 3                           |
| dos2unix                                                     | tofrodos_1.7.13+ds-2.debian.tar.xz | tofrodos_1.7.13+ds-2.debian.tar.xz |
| ip (iproute)                                                 | iproute2                           | iproute2                           |
| gawk                                                         | gawk                               | gawk                               |
| xvfb                                                         | xvfb                               | xvfb                               |
| gcc                                                          | gcc 4.8                            | gcc 4.8                            |
| git                                                          | git 1.7.1 or above                 | git 1.7.1 or above                 |
| make                                                         | make 3.81                          | make 3.81                          |
| netstat (net-tools)                                          | net-tools                          | net-tools                          |
| ncurses-devel                                                | libncurses5-dev                    | libncurses5-dev                    |
| tftp-server                                                  | tftpd                              | tftpd                              |
| zlib-devel(also,install 32-bit of this version)              | i386/zliob1g-2ubuntu4-dev          | i386/zliob1g-2ubuntu4-dev          |
| openssl-devel                                                | libssl-dev                         | libssl-dev                         |
| flex                                                         | flex                               | flex                               |
| bison                                                        | bison                              | bison                              |
| libselinux                                                   | libselinux1                        | libselinux1                        |
| gnupg                                                        | gnupg                              | gnupg                              |
| wget                                                         | wget                               | wget                               |
| diffstat                                                     | diffstat                           | diffstat                           |
| chrpath                                                      | chrpath                            | chrpath                            |
| socat                                                        | socat                              | socat                              |
| xterm                                                        | xterm                              | xterm                              |
| autoconf                                                     | autoconf                           | autoconf                           |
| libtool                                                      | libtool                            | libtool                            |
| tar                                                          | tar1.24                            | tar1.24                            |
| unzip                                                        | unzip                              | unzip                              |
| texinfo                                                      | texinfo                            | texinfo                            |
| zlib1g-dev                                                   | zlib1g-dev                         | zlib1g-dev                         |
| gcc-multilib                                                 | gcc-multilib                       | gcc-multilib                       |
| build-essential                                              | build-essential                    | build-essential                    |
| libsdl1.2-dev                                                | libsdl1.2-dev                      | libsdl1.2-dev                      |
| libglib2.0-dev                                               | libglib2.0-dev                     | libglib2.0-dev                     |
| SDL-devel                                                    |                                    |                                    |
| glibc-devel                                                  |                                    |                                    |
| 32-bit glibc                                                 |                                    |                                    |
| glib2-devel                                                  |                                    |                                    |
| automake                                                     |                                    |                                    |
| screen                                                       | screen                             | screen                             |
| pax                                                          | pax                                | pax                                |
| gzip                                                         | gzip                               | gzip                               |
| libz.so.1                                                    |                                    |                                    |
| libstdc++                                                    |                                    |                                    |
| g++ (gcc-c++)                                                |                                    |                                    |
| patch                                                        |                                    |                                    |
| lsb_release                                                  |                                    |                                    |
| zlib                                                         |                                    |                                    |
|                                                              |                                    |                                    |
| Note: The cells with empty fields were not installed. Top row kernel version is shipped from distribution |                                    |                                    |