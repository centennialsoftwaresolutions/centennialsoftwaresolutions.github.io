## 69952 - PetaLinux 2017.3 - Product Update Release Notes and Known Issues

## Title

69952 - PetaLinux 2017.3 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2017.3 and contains links to information about resolved issues and updated collateral contained in this release.

 

## Solution

 

**BSPs supported for 2017.3 PetaLinux Release**

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

**Note**: The "[sstate cache file](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate-rel-v2017.3.tar.gz&akdm=1)" (sstate-rel-v2017.3.tar.gz) can be found on the Xilinx download area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2017.3_README&akdm=1) file that outlines the procedure to use "sstate cache".

Refer to the attached file "2017.3-PetaLinux-Packages-List" for software package versions tested on host machines, which is required for PetaLinux installation tools.

 

Follow the attached README for steps to create BSPs using the template flow.

 

**PetaLinux 2017.3 contains the following build collateral:**

| Component                  | Git repo                                                     | Branches/Tag     | Commit ID                                  | Comments                                                     |
| :------------------------- | :----------------------------------------------------------- | :--------------- | :----------------------------------------- | :----------------------------------------------------------- |
| FSBL                       | [git://github.com/Xilinx/embeddedsw.git](git://github.com/Xilinx/embeddedsw.git) | xilinx-v2017.3   | `3c9f0cfde9307c2dc1a298f9f22d492601232821` | FSBL for Zynq7000 is at `embeddedsw/lib/sw_apps/zynq_fsbl`<br>FSBL for Zynq UltraScale+ is at `embeddedsw/lib/sw_apps/zynqmp_fsbl` |
| PMU Firmware               | [git://github.com/Xilinx/embeddedsw.git](git://github.com/Xilinx/embeddedsw.git) | xilinx-v2017.3   | `3c9f0cfde9307c2dc1a298f9f22d492601232821` | PMU for Zynq UltraScale+ Firmware is at `embeddedsw/lib/sw-apps/zynqmp_pmufw` |
| Device-tree                | [git://github.com/Xilinx/device-tree-xlnx.git](git://github.com/Xilinx/device-tree-xlnx.git) | xilinx-v2017.3.1 | `5b21302249df23f0de9b3b6ec4c75704339e3414` |                                                              |
| Linux                      | [git://github.com/Xilinx/linux-xlnx.git](git://github.com/Xilinx/linux-xlnx.git) | xilinx-v2017.3   | `f1b1e077d641fc83b54c1b8f168cbb58044fbd4e` | Kernel Version 4.9                                           |
| U-Boot                     | [git://github.com/Xilinx/u-boot-xlnx.git](git://github.com/Xilinx/u-boot-xlnx.git) | xilinx-v2017.3   | `da811c4511ef9caeb95f9a22fe49d38bd8e56ded` | U-Boot Version 2017.01                                       |
| QEMU                       | [git://github.com/Xilinx/qemu.git](git://github.com/Xilinx/qemu.git) | xilinx-v2017.3   | `8f8c89b18f6e4523099e41d81769fc534064b8de` |                                                              |
| Xen                        | [git://github.com/Xilinx/xen.git](git://github.com/Xilinx/xen.git) | xilinx-v2017.3   | `89dceb9fc81120e6a914f998763dd4c49b74d3d5` |                                                              |
| ARM-Trusted-Firmware (ATF) | [git://github.com/Xilinx/arm-trusted-firmware.git](git://github.com/Xilinx/arm-trusted-firmware.git) | xilinx-v2017.3   | `f9b244beaa7ac6a670b192192b6e92e5fd6044dc` | ATF is based on upstream version 1.3                         |
| Yocto                      | [git://github.com/Xilinx/meta-xilinx.git](git://github.com/Xilinx/meta-xilinx.git)<br>[git://github.com/Xilinx/meta-xilinx-tools.git](git://github.com/Xilinx/meta-xilinx-tools.git)<br>[git://github.com/Xilinx/meta-petalinux.git](git://github.com/Xilinx/meta-petalinux.git) | rel-v2017.3      |                                            | Yocto 2.2 Morty                                              |
| qemu-devicetrees           | [git://github.com/Xilinx/qemu-devicetrees.git](git://github.com/Xilinx/qemu-devicetrees.git) | xilinx-v2017.3   | `4b951c594078562e9dd828430075968dd91ac425` |                                                              |
| OpenAMP                    | [git://github.com/Xilinx/open-amp.git](git://github.com/Xilinx/open-amp.git) | xilinx-v2017.3   | `b041167a42a75f08c7b709622158f8d9d346a594` |                                                              |
| libmetal                   | [git://github.com/Xilinx/libmetal.git](git://github.com/Xilinx/libmetal.git) | xilinx-v2017.3   | `962bc1fe8df758bfea0fe831f0c1192e1f6045b8` |                                                              |
| GCC                        |                                                              |                  |                                            | MB compiler version 6.2<br>ARM 6.2                           |

**Wiki Updates:**

Covers details for Linux Kernel, Device drivers, U-boot, ATF and DTG changes (new features/fixes) in a particular release.

**2017.3 Linux and DTG release notes wiki page:**

 

http://www.wiki.xilinx.com/+2017.3+Linux+and+DTG+Release+Notes

**2017.3 U-Boot release notes wiki page :**

 

 

http://www.wiki.xilinx.com/2017.3+u-boot+Release+Notes

**2017.3 ATF release notes wiki page :**

 

 

 

http://www.wiki.xilinx.com/2017.3+ATF+Release+Notes

 

**2017.3 New Features:**

 

**PetaLinux**

 

- Individual workspace of XSCT in PetaLinux projects
- PetaLinux support for Vivado 2017.3 installed host OS
- For more details please see [(UG1144)](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_3/ug1144-petalinux-tools-reference-guide.pdf), [(UG1156)](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_3/ug1156-petalinux-tools-workflow-tutorial.pdf) and [(UG1157)](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_3/ug1157-petalinux-tools-command-line-guide.pdf).

 

**Yocto**

- None

 

 

**FSBL**

 

- None

 

**U-boot**

- U-Boot Documentation Improvements - Capture the Filesystem types supported for all the Boot mediums
- Provide UBIFS file system support for on-die ECC enabled NAND on Zynq UltraScale+ MPSoC

 

**Device-tree**

 

- Add support for AXI Interrupt controller in cascade mode in the Device tree generator

 

**ARM-Trusted Firmware (ATF)**

 

 

- Added new SMC support for SHA3 calculation support from ELs other than EL3.
- Added new SMC support for RSA to encrypt with private key and verify with public key.
- Fixed incorrect chipId calculation.

 

**FreeRTOS**

 

- None

 

**PMU Firmware (PMUFW)**

 

- None

 

**Power Management**

 

- None

 

**Standalone**

 

- Removed older versions of drivers are libraries that have become obsolete.
- EL1-NS support for Zynq MP PS drivers
- CCI support for Zynq MP PS drivers using DMA
  - NAND, QSPI, zDMA, EmacPS, SD
- New drivers added for:
  - dpdma_v1_0 driver for the DP DMA in Zynq MP
  - avbuf_v1_0 driver for Video Pipeline of the DisplayPort Subsystem in Zynq MP
  - dppsu_v1_0 driver for DisplayPort Transmitter in Zynq MP
  - mcdma_v1_0 driver for AXI MultiChannel Direct Memory Access IP
  - v_sdirx_v1_0 driver for UHDSDI Rx soft IP
  - v_sdirxss_v1_0 driver UHDSDI Rx subsystem soft IP
  - v_sditx_v1_0 driver for UHDSDI Tx soft IP
  - v_sditxss_v1_0 driver for UHDSDI Tx subsystem soft IP
  - sdi_common_v1_0 driver for common functions used in SDI drivers and applications
  - v_demosaic_v1_0 for DeMosiac IP
  - v_gamma_lut_v1_0 for Gamma Lut IP
- Changes around Video related drivers
  - v_csc_v2_2 , vprocss_v2_4 drivers : Support for conversion from 420/422/444/RGB to 420/422/444/RGB
  - v_frmbuf_rd_v2_0, v_frmbuf_wr_v2_0, v_mix_v3_0 drivers : New streaming and memory video formats and 64 bit address support for memory mapped interfaces. Support for second buffer for semi-planar formats
  - video_common_v4_2 driver
    - Addition of new video modes, frame rates, color formats for SDI.
    - Addition of new member AspectRatio to video stream structure
    - Addition of XVIDC_VM_3840x2160_60_P_RB video format
    - Addition of new streaming alpha formats and new memory formats
- Baremetal BSP (standalone_v6_4):
  - Support for CCI at EL1-NS.
  - Revamp of R5 MPU handling logic with addition of new APIs
  - Bug fixes
- XilFpga Library(xilfpga_v3_0):
  - Support for Device-key Encrypted bitstream loading and PL configuration registers readback.
- XilSecure Library(xilsecure_v2_2):
  - RSA decrypt with private key and encrypt with public key support.
  - RSA 2048 support.
  - New APIs to support xilsecure functionalities in Linux.
- XilSkey Library (xilskey_v6_3):
  - Support for programming eFUSE and BBRAM of Kintex UltraScale plus.
- lwIP stack(lwip141_v1_9):
  - Support for EL1-NS
  - Support for CCI
  - FreeRTOS support for AXI Ethernet adapter that uses AXI FIFO
  - Bug fixes
- XilIsf Library(xilisf_v5_9):
  - 4Byte addressing support for Micron devices.
- AXI Ethernet Driver(axiethernet_v5_6):
  - Support for MCDMA.
- SDPS Driver (sdps_v3_3):
  - Support for 64bit DMA addressing
  - Support for 200MHz in SD driver
- AXI DMA Driver (axidma_v9_4):
  - Support for cyclic DMA mode.
- mbox driver(mbox_v4_2):
  - Support for FIFO reset using hardware control register
- Minor bug fixes across drivers
- Fix for compilation warning across drivers
- Fix for doxygen documenting across drivers
- ZynqMP_FSBL
  - Support for Secondary boot mode as specified in image header of the boot image
  - Support for 1-bit and 2-bit QSPI buswidths
  - For secure boot, added PPK invalidity checks
- ZynqMP_PMUFW
  - Added three level debug prints for PMU Firmware application
  - Added xilsecure API calls to support xilsecure functionality from Linux
  - Multiple changes related to self refresh functionality (save/restore)

**Linux Drivers**

- Support for QSPI IS25LP256D, N25Q00, MT25Q 128 Mb, 256 Mb devices and Parallel NOR Flash: MT28EW devices 128Mb, 256Mb
- Support Linux PCIe RP Driver for PL based PCIe Hard IP on Zynq UltraScale+ MPSoC devices
- USB3.0 stream transfers for Bulk endpoint validation
- Support for VLAN and Priority queue support in macb driver
- Support for 10G/25G Ethernet 1588 MCDMA driver
- HW Crypto Accelerators accessing framework for RSA and SHA3

**OpenAMP and Libmetal**

 

- LibMetal source clean-up
- LibMetal Documentation Enhancement
- OpenAMP Documentation Enhancements

**QEMU**

 

- QEMU Windows Host Support

**VCU**

- Support 4K60 through the VCU SW stack with File IO
- Documentation of Multimedia software stack for Zynq MPSoC
- VCU SW stack latency report for Control SW, OMX and Gstreamer

 

**Known Issues for 2017.3:**

| Linux/Standalone | Application   | Description                                                  | Work-around                                                  | To be fixed version |
| :--------------- | :------------ | :----------------------------------------------------------- | :----------------------------------------------------------- | :------------------ |
| Linux            | Documentation | 2017.3/4 PetaLinux: Ubuntu 16.04.1 version in supported linux distribution doesn't align with UG973 and UG1144. | [Xilinx Answer 70395](https://adaptivesupport.amd.com/s/article/70395) | 2018.1              |
| Linux            | Drivers       | 2017.1-2017.4 Zynq UltraScale+ MPSoC: Linux MACB MDIO support for single MAC managing multiple PHYs | [Xilinx Answer 69132](https://adaptivesupport.amd.com/s/article/69132) | 2018.1              |
| Linux            | QEMU          | 2017.1-2017.4 U-boot: spi_flash_probe_bus_cs() failed with KCU105 and AC701 QEMU | [Xilinx Answer 69103](https://adaptivesupport.amd.com/s/article/69103) | 2018.1              |
| Linux            | Drivers       | 2017.1-2017.4 Zynq UltraScale+ MPSoC: Linux hangs when accessing PL peripheral generated by Yocto | [Xilinx Answer 69587](https://adaptivesupport.amd.com/s/article/69587) | 2018.1              |
| Linux            | XSDK          | 2017.1-2017.4 Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle | [Xilinx Answer 69143](https://adaptivesupport.amd.com/s/article/69143) |                     |
| Standalone       | XSDK          | 2017.3 Vivado/SDK - SDK fails to generate xparameters for PCS/PMA when connecting to ENET1/2/3 | [Xilinx Answer 69980](https://adaptivesupport.amd.com/s/article/69980) | 2017.4              |
| Linux            | PetaLinux     | Zynq UltraScale+ MPSoC: How to enable UHS(SD 3.0) support for ZCU102 and ZCU106 evaluation board PetaLinux BSPs | [Xilinx Answer 69978](https://adaptivesupport.amd.com/s/article/69978) |                     |
| Linux            | PetaLinux     | 2017.3 PetaLinux: Change to the name of FIT image (image.ub) in petalinux-config menu not reflected once images are built | [Xilinx Answer 69979](https://adaptivesupport.amd.com/s/article/69979) | 2017.4              |
| Linux            | PetaLinux     | 2016.4-2017.4 Zynq UltraScale+ MPSoC: PetaLinux does not correctly override the U-boot environment variables to set SD boot when both eMMC (SDIO0) and SD (SDIO1) are enabled in design | [Xilinx Answer 69780](https://adaptivesupport.amd.com/s/article/69780) | 2018.1              |
| Linux            | PetaLinux     | 2017.1-2017.4 PetaLinux: QEMU flash_stripe.c is not included in the QEMU utilities shipped with PetaLinux | [Xilinx Answer 69975](https://adaptivesupport.amd.com/s/article/69975) | 2018.1              |
| Linux            | Device-tree   | 2017.1-2017.4 Zynq UltraScale+ MPSoC: Linux mmcblk0 error -110 sending stop command, original cmd response 0x900, card status 0xe00 using Swissbit SD card | [Xilinx Answer 69995](https://adaptivesupport.amd.com/s/article/69995) | 2018.1              |
| Standalone       | XSDK          | 2017.2/3 Zynq UltraScale+ MPSoC: FSBL Boot image with Key Rolling causes XFSBL Tag Mismatch error | [Xilinx Answer 70005](https://adaptivesupport.amd.com/s/article/70005) | 2017.4              |
| Linux            | Device-tree   | 2017.1-2017.4 Zynq UltraScale+ MPSoC: Linux causes a hang in RPU code which was running fine until Linux loaded | [Xilinx Answer 70009](https://adaptivesupport.amd.com/s/article/70009) | 2018.1              |
| Linux            | Drivers       | 2016.4-2017.4 Zynq UltraScale+ MPSoC: Linux DDR EDAC driver unable to inject ECC errors when using either 32-bit DQ width, address mapping or Bank/Row/Column addressing mode | [Xilinx Answer 69997](https://adaptivesupport.amd.com/s/article/69997) | 2018.1              |
| Linux            | Driver        | 2017.3 Linux: AXI DMA test client errors                     | [Xilinx Answer 70011](https://adaptivesupport.amd.com/s/article/70011) | 2017.4              |
| Linux            | VCU           | 2017.3 Zynq UltraScale+ MPSoC (VCU): Frame drops are observed in 4kp60fps transcode use case in Linux | [Xilinx Answer 70013](https://adaptivesupport.amd.com/s/article/70013) | 2017.4              |
| Linux            | VCU           | 2017.3 Zynq UltraScale+ MPSoC (VCU): Multistream decoder > 4 FULL HD instance fails with memory allocation errors in Linux | [Xilinx Answer 70014](https://adaptivesupport.amd.com/s/article/70014) | 2017.4              |
| Linux            | Xen           | 2017.3 Zynq UltraScale+ MPSoC: Xen Ethernet passthrough fails in PetaLinux | [Xilinx Answer 70007](https://adaptivesupport.amd.com/s/article/70007) | 2017.4              |
| Linux            | Xen           | 2017.3 Zynq UltraScale+ MPSoC: Xen Linux reboot command on Dom0 does not work. | [Xilinx Answer 70163](https://adaptivesupport.amd.com/s/article/70163) | 2017.4              |
| Standalone       | XSDK          | 2017.3 Zynq UltraScale+ MPSoC: SDK extra_compiler_flags appending the default values | [Xilinx Answer 70217](https://adaptivesupport.amd.com/s/article/70217) | 2017.4              |
| Linux            | PetaLinux     | 2017.1-2017.4 PetaLinux: Removing DTB "from boot image" settings causes U-Boot to fail to load ramdisk image.ub | [Xilinx Answer 70304](https://adaptivesupport.amd.com/s/article/70304) | 2018.1              |
| Linux            | Device-tree   | 2017.3/4 Zynq-7000: DTG does not build for single core Zynq design | [Xilinx Answer 70402](https://adaptivesupport.amd.com/s/article/70402) | 2018.1              |

# README_content

=============================

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2017.3 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2017.3 Open Components Source Code (TAR/GZIP) file: 
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

# README

================================
MICROBLAZE BSP generation steps:
================================
This section explain about BSP generation steps.
1.	Create and Configure a project
		$ petalinux-create -t project --template microblaze --force -n <name of the project>
		$ petalinux-config --get-hw-description=<path to hdf directory> --oldconfig
		$ petalinux-config -c kernel
2.	Select following configs and save it.
		I2C_MUX
		EEPROM_AT24
		I2C_MUX_PCA954x
		I2C_CHARDEV
		COMMON_CLK_SI570
		CONFIG_TMPFS (enable for kcu105 design)
3.	Project Build
		$ petalinux-build
		$ mkdir -p pre-built/linux/images
		$ cp <project root>/images/linux/* <project root>/pre-built/linux/images/
4.	Package the BSP with files generated with following command
		$ petalinux-package --bsp -p <plnx-proj-root> --hwsource <hw-project-root> --output <name of the BSP>

NOTE: --hwsource is optional and can be removed

==========================
ZYNQ BSP generation steps:
==========================
This section explain about BSP generation steps.
Note: While building bsps, we use openAMP files from internal repos. when configuring and packing
the root file system of the target. If you want to use openamp on your target ,Please copy files from  
from published bsp's. While copying files please maintain same directory structure.

1.	Create and Configure a project
		$ petalinux-create -t project --template microblaze --force -n <name of the project>
		$ petalinux-config --get-hw-description=<path to hdf directory> --oldconfig
		$ petalinux-config -c kernel
2.	Select following configs and save it.
		I2C_XILINX
		I2C_MUX
		I2C_MUX_PCA954x
		I2C_CHARDEV
3.	Choose any desired board and follow steps in it.
	a.	zc702 board
		$ petalinux-config
		Add zynq_zc702_config to SUBSYSTEM_UBOOT_CONFIG_TARGET
	b.	zc706 board
		$ petalinux-config
		Add zynq_zc706_config to SUBSYSTEM_UBOOT_CONFIG_TARGET
4.	Get openamp device tree
		$ cp <any-zynq-BSP>/project-spec/meta-user/recipes-bsp/device-tree/files/openamp-overlay.dtsi <project root>/project-spec/meta-user/recipes-bsp/device-tree/files
		$ echo '/include/ "openamp-overlay.dtsi"' >> <project root>/project-spec/meta-user/recipes-bsp/device-tree/files/system-user.dtsi
		$ echo 'SRC_URI += "file://openamp-overlay.dtsi"' >> project-spec/meta-user/recipes-bsp/device-tree/device-tree-generation_%.bbappend
5.	Enable openamp and its examples in rootfs
		$ petalinux-config -c rootfs
		Enable following packages and save it
			openamp-fw-echo-testd
			openamp-fw-mat-muld
			openamp-fw-rpc-demo
			packagegroup-petalinux-openamp
6.	Project Build
		$ petalinux-build
		$ mkdir -p pre-built/linux/images
		$ cp <project root>/images/linux/* <project root>/pre-built/linux/images
7.	Clean up configurations by default few configurations are enabled to generate prebuilt images. These configurations are cleaned up while packaging a bsp. However you can keep them if you needed them in project.
		$ petalinux-config -c rootfs
		Disable following packages and save it
			openamp-fw-echo-testd
			openamp-fw-mat-muld
			openamp-fw-rpc-demo
			packagegroup-petalinux-openamp
8.	Package the BSP with files generated with following command
		$ petalinux-package --bsp -p <plnx-proj-root> --hwsource <hw-project-root> --output <name of the BSP>

NOTE: --hwsource is optional and can be removed

============================
ZYNQMP BSP generation steps:
============================
This section explain about BSP generation steps.
Note: While building bsps, we use some openAMP, Xen and QEMU files from internal repos.
If you want to use openAMP, Xen or QEMU,Please copy the files from published bsp's. 
While copying files, please maintain same directory structure.

1.	Creation and configuration of project
		$ petalinux-create -t project --template zynqMP --force -n <name of project>
		$ petalinux-config --get-hw-description=<path to hdf directory> --oldconfig
2.	Get openamp,qemu and xen device trees
		$ cp -r <any-zynqMP-BSP>/project-spec/meta-user/recipes-bsp/device-tree/files/{openamp-overlay.dtsi,xen-overlay.dtsi,zynqmp-qemu-arm.dts,multi-arch/} <project root>/project-spec/meta-user/recipes-bsp/device-tree/files
		$ echo '/include/ "openamp-overlay.dtsi"' >> <project root>/project-spec/meta-user/recipes-bsp/device-tree/files/system-user.dtsi
		$ echo 'SRC_URI += "file://openamp-overlay.dtsi"' >> project-spec/meta-user/recipes-bsp/device-tree/device-tree-generation_%.bbappend
3.	Enable openamp and its examples in rootfs
		$ petalinux-config -c rootfs
		Select following packages and save it
			openamp-fw-echo-testd
			openamp-fw-mat-muld
			openamp-fw-rpc-demo
			packagegroup-petalinux-openamp
4.	Configuring BSP
	a.	zcu102 production and zcu102 rev1.0 boards
	b.	zcu102 es1, zcu102 es2 and zcu102 revD boards
	c.	zcu104 board
	d.	zcu102 warm restart board
	e.	zcu106 board
	f.	zc1254 board
5.	Choose any desired board and follow steps in it.
	a.	zcu102 production and es2 rev1.0 board
		$ petalinux-config
		Add xilinx_zynqmp_zcu102_rev1_0_defconfig to SUBSYSTEM_UBOOT_CONFIG_TARGET
	b.	zcu102 es1, es2 and revD board
		$ petalinux-config
		Add xilinx_zynqmp_zcu102_revB_defconfig to SUBSYSTEM_UBOOT_CONFIG_TARGET
	c.	zcu104 board
		$ petalinux-config
		Add xilinx_zynqmp_zcu104_revA_defconfig to SUBSYSTEM_UBOOT_CONFIG_TARGET
	d.	zcu102 warm restart board
		$ cat >> project-spec/meta-user/recipes-core/images/petalinux-image.bbappend <<EOF
		IMAGE_INSTALL_append = " wdt-heartbeat"
		IMAGE_INSTALL_append = " mpsrm-init"
		IMAGE_INSTALL_append = " openamp-fw"
		EOF
		$ petalinux-config --oldconfig
		$ petalinux-config -c rootfs
		Select following packages and save it
			wdt-heartbeat
			mpsrm-init
			openamp-fw
		$ echo 'SIGGEN_UNLOCKED_RECIPES += "initscripts"' >> <project root>/build/conf/local.conf
		$ petalinux-config -c kernel
		Select following configs and save it
			IRQ_DOMAIN_DEBUG
			GCOV_KERNEL
			FREEZER
			SUSPEND
			PM
			SRAM
		$ petalinux-config
		Add xilinx_zynqmp_zcu102_rev1_0_defconfig to SUBSYSTEM_UBOOT_CONFIG_TARGET
		NOTE: Copy wdt-heartbeat,mpsrm-init,openamp-fw recipes from the warm restart BSP at project-spec/meta-user/recipes-apps/{openamp-fw,wdt-heartbeat}, project-spec/meta-user/recipes-core/mpsrm-init
	e.	zcu106 design
		$ echo 'IMAGE_INSTALL_append = " gstreamer-vcu-examples"' >> <project root>/project-spec/meta-user/recipes-core/images/petalinux-image.bbappend
		$ petalinux-config --oldconfig
		$ petalinux-config -c rootfs
		Select following packages and save it
			packagegroup-petalinux-gstreamer
			packagegroup-petalinux-matchbox
			packagegroup-petalinux-x11
			libdrm
			libdrm-kms
			libdrm-tests
			gstreamer-vcu-examples
		$ petalinux-config
		Add xilinx_zynqmp_zcu106_revA_defconfig to SUBSYSTEM_UBOOT_CONFIG_TARGET
		NOTE: Copy recipee-multimedia from zcu106 bsp at project-spec/meta-user/recipes-multimedia
	f.	zc1254
		$ cat >> project-spec/meta-user/recipes-core/images/petalinux-image.bbappend <<EOF
		IMAGE_INSTALL_append = " rfdc"
		IMAGE_INSTALL_append = " rfdc-intr"
		IMAGE_INSTALL_append = " rfdc-read-write"
		IMAGE_INSTALL_append = " rfdc-selftest"
		EOF
		$ petalinux-config --oldconfig
		$ petalinux-config -c rootfs
		Select following packages and save it
			rfdc
			rfdc-intr
			rfdc-read-write
			rfdc-selftest
		$ petalinux-config
		Add xilinx_zynqmp_zc1254_revA_defconfig to SUBSYSTEM_UBOOT_CONFIG_TARGET
		NOTE: Copy fsbl from zc1254 bsp at project-spec/meta-user/recipes-bsp/fsbl
6.	Project Build
		$ petalinux-build
		$ mkdir -p pre-built/linux/images
		$ cp <project root>/images/linux/* <project root>/pre-built/linux/images/
7.	Build xen images
		$ echo '/include/ "xen-overlay.dtsi"' >> <project root>/project-spec/meta-user/recipes-bsp/device-tree/files/system-user.dtsi
		$ echo 'SRC_URI += "file://xen-overlay.dtsi \"' >> project-spec/meta-user/recipes-bsp/device-tree/device-tree-generation_%.bbappend
		$ petalinux-config
		Select following config and save it.
			Image Packaging Configuration
			Root filesystem type (INITRD)
		$ petalinux-config -c rootfs
		Select following package and save it
			packagegroup-petalinux-xen
		$ petalinux-build
		$ cp -L <project root>/images/linux/Image <project root>/pre-built/linux/images/xen-Image
		$ cp -L <project root>/images/linux/system.dtb <project root>/pre-built/linux/images/xen.dtb
		$ cp -L <project root>/images/linux/xen.ub <project root>/pre-built/linux/images/xen.ub
		$ cp -L <project root>/images/linux/rootfs.cpio.gz.u-boot <project root>/pre-built/linux/images/xen-rootfs.cpio.gz.u-boot
8.	Clean up of configurations by default few configurations are enabled to generate prebuilt images. These configurations are cleaned up while packaging a bsp. However you can keep them if you needed them in project.
		$ petalinux-config -c rootfs
		Disable following packages and save it
			openamp-fw-echo-testd
			openamp-fw-mat-muld
			openamp-fw-rpc-demo
			packagegroup-petalinux-openamp
			packagegroup-petalinux-xen
		$ petalinux-config
		Select following config and save it.
			Image Packaging Configuration
			Root filesystem type (INITRAMFS)
9.	Package the BSP with files generated with following command
		$ petalinux-package --bsp -p <plnx-proj-root> --hwsource <hw-project-root> --output <name of the BSP>

NOTE: --hwsource is optional and can be removed

# 2017.3-PetaLinux-Packages-List

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