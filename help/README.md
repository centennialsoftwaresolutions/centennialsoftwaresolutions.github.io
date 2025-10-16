# 72950 - PetaLinux 2019.2 - Product Update Release Notes and Known Issues

## Title

72950 - PetaLinux 2019.2 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2019.2 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for the 2019.2 PetaLinux Release**  

This table contains supported BSPs for Zynq-7000, MicroBlaze, and Zynq UltraScale+ MPSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

**Note:** XY - Represents release year, Y - Represents release version.

| Platform                   | Variant                       | BSP Name                                  | BSP Description                                              |
| -------------------------- | ----------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| **MicroBlaze**             | **AC701**                     | xilinx-ac701-v20XY.Z-final.bsp            | This BSP contains two BSPs [AC701 lite, AC701 full].<br><br>**Hardware (AC701 lite):** Design contains MicroBlaze Processor, core peripherals UART_lite, Ethernet Lite, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br>AC701 lite contains the AXI Lite IPs UART_lite, Ethernet Lite etc. in contrast to AC701 Full.<br><br>**Hardware (AC701 full):** Design contains MicroBlaze Processor, core peripherals AXI UART16550, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br><br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | **KC705**                     | xilinx-kc705-v20XY.Z-final.bsp            | This BSP contains two BSPs [KC705 lite, KC705 full].<br><br>**Hardware (KC705 lite):** Design contains MicroBlaze Processor, core peripherals UART_lite, Ethernet Lite, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br>**Hardware (KC705 full):** Design contains MicroBlaze Processor, core peripherals AXI UART16550, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br><br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | **KCU105**                    | xilinx-kcu105-v20XY.Z-final.bsp           | **Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | **SP701**                     | xilinx-sp701-v20XY.Z-final.bsp            | **Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | **VCU118**                    | xilinx-vcu118-v20XY.Z-final.bsp           | **Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq-7000**              | **ZC702**                     | xilinx-zc702-v20XY.Z-final.bsp            | **Hardware:** Design contains Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_4bits.<br>**Software:** FSBL, U-boot, Linux, device-tree (includes Open AMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq-7000**              | **ZC706**                     | xilinx-zc706-v20XY.Z-final.bsp            | **Hardware:** Design contains Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_4bits, dip_switches_4bits, gpio_sws_3bits.<br>**Software:** FSBL, U-boot, Linux, device-tree (includes Open AMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq-7000**              | **Avnet Digilent Zedboard**   | avnet-digilent-zedboard-v20XY.Z-final.bsp | **Hardware:** Design contains Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_8bits, btns_5bits, sws_8bits.<br>**Software:** FSBL, U-boot, Linux, device-tree (includes Open AMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | **ZCU102 production silicon** | xilinx-zcu102-v20XY.Z-final.bsp           | **Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.)<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | **ZCU104 production silicon** | xilinx-zcu104-v20XY.Z-final.bsp           | **Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), vcu-control software, rootfs (minimal packages which includes additional SW packages like GStreamer, OpenMAX, V4L2, libdrm and vcu-examples).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | **ZCU106 production silicon** | xilinx-zcu106-v20XY.Z-final.bsp           | **Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes OpenAMP, Xen), vcu-control software, rootfs (minimal packages which includes additional SW packages like GStreamer, OpenMAX, V4L2, libdrm and vcu-examples).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ RFSoC** | **ZCU111 production silicon** | xilinx-zcu111-v20XY.Z-final.bsp           | **Hardware:** Design contains Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc) and rf_data_converters, sd_fec_dec, adc_sink, dac_source, axi_gpio, axi_intc IP's.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), rfdc-drivers, rootfs (minimal packages which includes RDFC example applications).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ RFSoC** | **ZCU1275**                   | xilinx-zcu1275-v20XY.Z-final.bsp          | **Hardware:** Design contains Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc) and rf_data_converters, adc_sink, dac_source, axi_gpio, axi_intc IP's.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), rfdc-drivers, rootfs (minimal packages which includes RDFC example applications).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ RFSoC** | **ZCU1285**                   | xilinx-zcu1285-v20XY.Z-final.bsp          | **Hardware:** Design contains Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc) and rf_data_converters, adc_sink, dac_source, axi_gpio, axi_intc IP's.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), rfdc-drivers, rootfs (minimal packages which includes RDFC example applications).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |

**Note**: The "<architecture> sstate-cache" (sstate\_<architecture>\_2019.2.tar.gz) file can be found on the Xilinx download area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2019.2_README.tar.gz) file that outlines the procedure to use "sstate cache".  

Refer to the attached file "[2019.2\_PetaLinux\_Packages\_List](https://www.xilinx.com/Attachment/2019.2_PetaLinux_Package_List.xlsx)" for software package versions tested on host machines, which is required for PetaLinux installation tools.  

[README](https://www.xilinx.com/Attachment/README_content_v2019.2.txt) for downloads area.  

**PetaLinux 2019.2 contains the following build collateral:**

| Component                      | Git repo                                                     | Git Branches          | Git Tags       | Commit ID                                                    | Comments                                                     |
| ------------------------------ | ------------------------------------------------------------ | --------------------- | -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **FSBL**                       | git://github.com/Xilinx/embeddedsw.git                       | release-2019.2        | xilinx-v2019.2 | e8db5fb118229fdc621e0ec7848641a23bf60998                     | FSBL for Zynq-7000 is at `embeddedsw/lib/sw_apps/zynq_fsbl`<br>FSBL for Zynq UltraScale+ is at `embeddedsw/lib/sw_apps/zynqmp_fsbl` |
| **PMU Firmware**               | git://github.com/Xilinx/embeddedsw.git                       | release-2019.2        | xilinx-v2019.2 | e8db5fb118229fdc621e0ec7848641a23bf60998                     | PMU for Zynq UltraScale+ Firmware is at `embeddedsw/lib/sw-apps/zynqmp_pmufw` |
| **Device-tree**                | git://github.com/Xilinx/device-tree-xlnx.git                 | master                | xilinx-v2019.2 | a8b39cf536e6ccda56affb27b2727c1e4d6edad2                     |                                                              |
| **Linux**                      | git://github.com/Xilinx/linux-xlnx.git                       | xlnx_rebase_v4.19     | xilinx-v2019.2 | b983d5fd71d4feaf494cdbe0593ecc29ed471cb8                     | Linux Kernel rebase version 4.19                             |
| **U-Boot**                     | git://github.com/Xilinx/u-boot-xlnx.git                      | master                | xilinx-v2019.2 | dc61275b1d505f6a236de1c5b0f35485914d2bcc                     | U-Boot Version v2019.01                                      |
| **QEMU**                       | git://github.com/Xilinx/qemu.git                             | master                | xilinx-v2019.2 | 6617fbc8be3525ca524f7d4ef7fc7b14c5b0c822                     |                                                              |
| **Xen**                        | git://github.com/Xilinx/xen.git                              | xilinx/release-2019.2 | xilinx-v2019.2 | 0bb0d1c1f59da1a0fbc8d3fea843434678bcd6d9                     | Xen Version 4.11                                             |
| **ARM-Trusted-Firmware (ATF)** | git://github.com/Xilinx/arm-trusted-firmware.git             | master                | xilinx-v2019.2 | 713dace94b259845fd8eede11061fbd8f039011e                     | ATF is based on upstream version 2.0                         |
| **Yocto**                      | git://github.com/Xilinx/meta-xilinx.git<br>git://github.com/Xilinx/meta-xilinx-tools.git<br>git://github.com/Xilinx/meta-petalinux.git | rel-v2019.2           | No Tags        | 586e4001cdd90e3db67692b14bbe5daabc565478<br>1f0161a321aac36b0dfe6d742f2019abd146d998<br>6f3c49f124d2ce1bfcea006091fd72063a63ed95 | Yocto 2.6.1 Thud                                             |
| **qemu-devicetrees**           | git://github.com/Xilinx/qemu-devicetrees.git                 | branch/xilinx-v2019.2 | xilinx-v2019.2 | d119986a6dd800bc3e71ea171b5b6741e0128289                     |                                                              |
| **OpenAMP**                    | git://github.com/Xilinx/open-amp.git                         | master                | xilinx-v2019.2 | 7fd76b240fb009d25b774c098e73908b2ddb7d92                     |                                                              |
| **libmetal**                   | git://github.com/Xilinx/libmetal.git                         | master                | xilinx-v2019.2 | c7fe342fcabb638dc98f3356d7eea869f8363ec6                     |                                                              |
| **VCU OpenMax IL**             | git://github.com/Xilinx/vcu-omx-il.git                       | master                | xilinx-v2019.2 | 9bbb40e3ceddd9e166d1d97aa4ac380459166344                     |                                                              |
| **VCU Control Software**       | git://github.com/Xilinx/vcu-ctrl-sw.git                      | master                | xilinx-v2019.2 | f3001b44eeaf770cbd9f95d2cfd0b02d3f65b2d3                     |                                                              |
| **VCU Firmware**               | git://github.com/Xilinx/vcu-firmware.git                     | master                | xilinx-v2019.2 | 29ab982965b797b1c9b567faba47378578398f4a                     |                                                              |
| **VCU Modules**                | git://github.com/Xilinx/vcu-modules.git                      | master                | xilinx-v2019.2 | d4b46f2ee10e5d13609ca982d8d8bae662468837                     |                                                              |
| **GStreamer OpenMax IL**       | git://github.com/Xilinx/gst-omx.git                          | xilinx-master         | xilinx-v2019.2 | f511f62c737318dc329a6417dca5d38065d70a77                     | GStreamer version 1.14.4                                     |
| **GStreamer Plugins-Base**     | git://github.com/Xilinx/gst-plugins-base.git                 | master-rel-1.12.2     | xilinx-v2019.2 | 0deb29a2e32b92cfd92d61136576d9fa310528c1                     |                                                              |
| **GStreamer Plugins-Bad**      | git://github.com/Xilinx/gst-plugins-bad.git                  | master-rel-1.12.2     | xilinx-v2019.2 | 33016ba0374828b3188f9c9b236b185a5496cfe7                     |                                                              |
| **GStreamer Plugins-Good**     | git://github.com/Xilinx/gst-plugins-good.git                 | master-rel-1.12.2     | xilinx-v2019.2 | 29b75b92985f58770c9580b58582404eadbb256a                     |                                                              |
| **GStreamer**                  | git://github.com/Xilinx/gstreamer.git                        | rel-v2019.2           | No Tags        | c3c502011e3585749c664e6d2125c49419bb9889                     |                                                              |
| **hdmi-modules**               | git://github.com/Xilinx/hdmi-modules.git                     | master                | xilinx-v2019.2 | be354cc3c8889932aabede8cddda0770d77e7843                     |                                                              |
| **GCC**                        |                                                              |                       |                |                                                              | MB compiler version 8.2<br>ARM 8.2                           |

**2019.2 Release Notes for Open Source components wiki page:**

Covers details for below components changes (new features/fixes) in a particular release.  

https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/182190690/2019.2+Release+Notes+for+Open+Source+Components

**2019.2 Release pre-built images wiki page:**

[https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/183304302/Zynq+2019.2+Release](https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/183304302/Zynq+2019.2+Release)  

**2019.2 New Features:**  

**PetaLinux**

-   PetaLinux supports Yocto devtool

**GPU MALI-400**

-   Added r9p0 DDK which has some bug fixes and supports GBM 1.17  
    
-   Support for rendering graphics on different surfaces using EGL config variable for Qt GBM or KMS backend.

**2019.2 Bug Fixes:**

**PetaLinux**

-   Fixed Makefile indentation in (UG1144) docs which caused build errors when adding custom libraries.  
    
-   Fixed Migration section in (UG1144) docs for changes to config, .bb and .bbapend files.  
    
-   Fixed PetaLinux C++ template apps which fails to build when using LDFLAGS compiler options in recipes.  
    
-   Fixed PetaLinux project zynqMP template flow u-boot configs and #defines generated from tool.  
    
-   Fixed PetaLinux build errors when fpga-manager option is enabled with HDF that does not contain bitstream.  
    
-   Fixed petalinux-boot with --before-connect and --after-connect options.  
    
-   Fixed PetaLinux BSP README content.
-   Fixed booting Zynq-7000 kernel, dtb and rootfs images separately using bootm commands.

**GPU MALI-400**

-   Fixed ARM libmali is made compatible with wayland 1.15
-   Wayland-egl implementation will now come from wayland (>=1.14)
-   Bug fix in gbm implementation (API: gbm\_bo\_import)

**Known Issues for 2019.2:**  

| Linux/Baremetal | Components       | Description                                                  | Work-around           | To be fixed version |
| --------------- | ---------------- | ------------------------------------------------------------ | --------------------- | ------------------- |
| Linux           | PetaLinux        | Zynq UltraScale+ MPSoC: How to enable UHS (SD 3.0) support for ZCU102 and ZCU106 evaluation board PetaLinux BSPs | (Xilinx Answer 69978) |                     |
| Linux           | XSDK             | Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle    | (Xilinx Answer 69143) |                     |
| Linux           | FSBL             | Zynq UltraScale+ MPSoC: How to achieve SATA performance in Linux | (Xilinx Answer 71584) |                     |
| Linux           | FSBL             | Zynq UltraScale+ MPSoC: How to make SMMU work with SATA IP   | (Xilinx Answer 71790) |                     |
| Linux           | Yocto, PetaLinux | 2019.x Zynq UltraScale+ MPSoC: Yocto or PetaLinux throws warnings when you enable libmali with fbdev windowing system | (Xilinx Answer 72139) |                     |
| Linux           | Yocto, PetaLinux | 2019.x Zynq UltraScale+ MPSoC: Linux boot throws fatal errors with libmali and X11 enabled in PetaLinux or Yocto images | (Xilinx Answer 72363) |                     |
| Linux           | Kernel           | 2019.x Zynq7000, Zynq UltraScale+ MPSoC: Yocto or PetaLinux build with petalinux-image-full images hangs without reaching Linux boot login prompt | (Xilinx Answer 72377) |                     |
| Baremetal       | BSP              | 2019.2 Zynq UltraScale+ MPSoC/RFSoC: RPU suspend-resume multiple times does not work | (Xilinx Answer 73015) | 2020.1              |
| Linux           | VCU              | 2019.2 Zynq UltraScale+ MPSoC VCU - Why do I see a hang while transcoding a Dynamically Changing Resolution stream containing a 4K resolution from AVC or HEVC to AVC using a GStreamer pipeline? | (Xilinx Answer 73020) | 2020.1              |
| Linux           | VCU              | 2019.2 Zynq UltraScale+ MPSoC VCU - Why do I see a hang while running two 4kp30 AVC encoding and decoding GStreamer pipelines and running for more than 12 hours? | (Xilinx Answer 73021) |                     |
| Linux           | VCU              | 2019.2 Zynq UltraScale+ MPSoC VCU - Why do I see errors when trying to encode 10-bit 4:2:2 4K DCI to HEVC format? | (Xilinx Answer 73022) |                     |
| Linux           | VCU              | 2019.2 Zynq UltraScale+ MPSoC VCU - Why do I see "VCU: unavailable resource error" errors when trying switching from a 4Kp30 stream to a 4Kp60 stream, when using the Low Latency Phase 2 (LLP2) mode? | (Xilinx Answer 73023) |                     |
| Linux           | VCU              | 2019.2 Zynq UltraScale+ MPSoC VCU - Why do I see the VCU hang when encoding 4Kp60 AVC num-slices=16, when using the Low Latency Phase 2 (LLP2) mode? | (Xilinx Answer 73024) |                     |
| Linux           | VCU              | 2019.2 Zynq UltraScale+ MPSoC VCU - Why are the QP values in the last row, not properly updated when using the Example GStreamer Application? | (Xilinx Answer 73049) | 2020.1              |
| Linux           | VCU              | 2019.2 Zynq UltraScale+ MPSoC VCU - Why do I see the high decoder latency number while decoding a reduced latency HEVC encoded stream? | (Xilinx Answer 73051) | 2020.1              |
| Linux           | Device-tree      | 2019.2 Zynq UltraScale+ MPSoC: PetaLinux ZCU106 BSP fails to detect SD Card FAT32 or EXT4 partition when booting Linux | (Xilinx Answer 73079) | 2020.1              |

# README_content_v2019.2

=============================

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2019.2 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2019.2 Open Components Source Code (TAR/GZIP) file: 
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

# 2019.2_PetaLinux_Package_List

## Linux Distribution OS details:

1. RHEL 7.4, 7.5 and 7.6 Server:  Infrastructure Server
2. RHEL 7.4, 7.5 and 7.6 Desktop : Development and Creative workstation.
3. CentOS 7.4, 7.5 and 7.6 Server (From Everything.ISO): Infrastructure server.
4. CentOS 7.4, 7.5 and 7.6 Desktop (From Everything.ISO): Development and Creative workstation.
5. Ubuntu 16.04.05 and Ubuntu 16.04.06 Desktop.
6. Ubuntu 16.04.05  and Ubuntu 16.04.06 Server.
7. Ubuntu 18.04.01 and Ubuntu 18.04.02 Desktop.
8. Ubuntu 18.04.02  and Ubuntu 18.04.02 Server.

### Note: 

1. Empty packages are not installed means assuming these are default from Linux Distribution.

## Tool/Library Versions

### RHEL/CentOS versions

| Tool/Library                                    | Red Hat Enterprise Desktop/Server  7.4 (64-bit)              | Red Hat Enterprise Destop/Server 7.5(64-bit) | Red Hat Enterprise Desktop/Server  7.6 (64-bit) | CentOS Desktop/Server7.4  (64-bit)         | CentOS Desktop/Server 7.5  (64-bit)        | CentOS Desktop/Server 7.6  (64-bit)        |
| ----------------------------------------------- | ------------------------------------------------------------ | -------------------------------------------- | ----------------------------------------------- | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| Quick Installation steps for packages:          | su yum install net-tools gawk make wget tar bzip2.x86_64 gzip python unzip perl patch.x86_64 diffutils diffstat git cpp gcc gcc-c++ glibc-devel texinfo chrpath socat perl-Data-Dumper perl-Text-ParseWords perl-Thread-Queue python34-pip xz which SDL-devel xterm autoconf libtool.x86_64 zlib-devel automake glib2-devel zlib ncurses-devel openssl-devel dos2unix flex bison glibc.i686 screen pax glibc-devel.i686 compat-libstdc++-33.i686 libstdc++.i686 |                                              |                                                 |                                            |                                            |                                            |
| kernel Version                                  | 3.10.0-693.17.1.el7.x86_64                                   | 3.10.0-693.17.1.el7.x86_64                   | 3.10.0-693.17.1.el7.x86_64                      | 3.10.0-693.17.1.el7.x86_64                 | 3.10.0-862.el7.x86_64                      | 3.10.0-957.el7.x86_64                      |
| dos2unix                                        | dos2unix-6.0.3-7.el7.x86_64                                  | dos2unix-6.0.3-7.el7.x86_64                  | dos2unix-6.0.3-7.el7.x86_64                     | dos2unix-6.0.3-7.el7.x86_64                | dos2unix-6.0.3-7.el7.x86_64                | dos2unix-6.0.3-7.el7.x86_64                |
| ip (iproute)                                    | iproute-3.10.0-87.el7.x86_64                                 | iproute-3.10.0-87.el7.x86_64                 | iproute-3.10.0-87.el7.x86_64                    | iproute-3.10.0-87.el7.x86_64               | iproute-4.11.0-14.el7.x86_64               | iproute-4.11.0-14.el7.x86_64               |
| gawk                                            | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7_3.1.x86_64                  | gawk-4.0.2-4.el7_3.1.x86_64                     | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                |
| gcc                                             | gcc-4.8.5-16.el7_4.1.x86_64                                  | gcc-4.8.5-16.el7_4.1.x86_64                  | gcc-4.8.5-16.el7_4.1.x86_64                     | gcc-4.8.5-16.el7_4.1.x86_64                | gcc-4.8.5-39.el7.x86_64                    | gcc-4.8.5-39.el7.x86_64                    |
| git                                             | git-1.8.3.1-12.el7_4.x86_64                                  | git-1.8.3.1-12.el7_4.x86_64                  | git-1.8.3.1-12.el7_4.x86_64                     | git-1.8.3.1-12.el7_4.x86_64                | git-1.8.3.1-12.el7_4.x86_64                | git-1.8.3.1-12.el7_4.x86_64                |
| make                                            | make-3.82-23.el7.x86_64                                      | make-3.82-23.el7.x86_64                      | make-3.82-23.el7.x86_64                         | make-3.82-23.el7.x86_64                    | make-3.82-23.el7.x86_64                    | make-3.82-23.el7.x86_64                    |
| netstat (net-tools)                             | net-tools-2.0-0.24.20131004git.el7.x86_64                    | net-tools-2.0-0.24.20131004git.el7.x86_64    | net-tools-2.0-0.24.20131004git.el7.x86_64       | net-tools-2.0-0.24.20131004git.el7.x86_64  | net-tools-2.0-0.24.20131004git.el7.x86_64  | net-tools-2.0-0.24.20131004git.el7.x86_64  |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-5.9-14.20130511.el7_4.x86_64                   | ncurses-devel-5.9-14.20130511.el7_4.x86_64   | ncurses-devel-5.9-14.20130511.el7_4.x86_64      | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 |
| tftp-server                                     | tftp-server                                                  | tftp-server                                  | tftp-server                                     | tftp-server                                | tftp-server                                | tftp-server                                |
| zlib-devel(also,install 32-bit of this version) | zlib-devel-1.2.7-18.el7.x86_64                               | zlib-devel-1.2.7-18.el7.x86_64               | zlib-devel-1.2.7-18.el7.x86_64                  | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             |
|                                                 |                                                              |                                              |                                                 |                                            |                                            |                                            |
| openssl-devel                                   | openssl-devel-1.0.2k-19.el7.x86_64                           | openssl-devel-1.0.2k-19.el7.x86_64           | openssl-devel-1.0.2k-19.el7.x86_64              | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         |
| flex                                            | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                     | flex-2.5.37-3.el7.x86_64                        | flex-2.5.37-3.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   |
| bison                                           | bison-3.0.4-1.el7.x86_64                                     | bison-3.0.4-1.el7.x86_64                     | bison-3.0.4-1.el7.x86_64                        | bison-3.0.4-1.el7.x86_64                   | bison-3.0.4-2.el7.x86_64                   | bison-3.0.4-2.el7.x86_64                   |
| libselinux                                      | libselinux-2.5-14.1.el7.x86_64                               | libselinux-2.5-14.1.el7.x86_64               | libselinux-2.5-14.1.el7.x86_64                  | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.5-14.1.el7.x86_64             |
| gnupg                                           | gnupg2-2.0.22-4.el7.x86_64                                   | gnupg2-2.0.22-4.el7.x86_64                   | gnupg2-2.0.22-4.el7.x86_64                      | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 |
| wget                                            | wget-1.14-15.el7_4.1.x86_64                                  | wget-1.14-15.el7_4.1.x86_64                  | wget-1.14-15.el7_4.1.x86_64                     | wget-1.14-15.el7_4.1.x86_64                | wget-1.14-15.el7_4.1.x86_64                | wget-1.14-18.el7.x86_64                    |
| diffstat                                        | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                   | diffstat-1.57-4.el7.x86_64                      | diffstat-1.57-4.el7.x86_64                 | diffstat-1.57-4.el7.x86_64                 | diffstat-1.57-4.el7.x86_64                 |
| chrpath                                         | chrpath-0.16-0.el7.x86_64                                    | chrpath-0.16-0.el7.x86_64                    | chrpath-0.16-0.el7.x86_64                       | chrpath-0.16-0.el7.x86_64                  | chrpath-0.16-0.el7.x86_64                  | chrpath-0.16-0.el7.x86_64                  |
| socat                                           | socat-1.7.3.2-2.el7.x86_64                                   | socat-1.7.3.2-2.el7.x86_64                   | socat-1.7.3.2-2.el7.x86_64                      | socat-1.7.3.2-2.el7.x86_64                 | socat-1.7.3.2-2.el7.x86_64                 | socat-1.7.3.2-2.el7.x86_64                 |
| xterm                                           | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                       | xterm-295-3.el7.x86_64                          | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     |
| autoconf                                        | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                  | autoconf-2.69-11.el7.noarch                     | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                |
| libtool                                         | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                | libtool-2.4.2-22.el7_3.x86_64                   | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              |
| tar                                             | tar-1.26-32.el7.x86_64                                       | tar-1.26-32.el7.x86_64                       | tar-1.26-32.el7.x86_64                          | tar-1.26-32.el7.x86_64                     | tar-1.26-34.el7.x86_64                     | tar-1.26-35.el7.x86_64                     |
| unzip                                           | unzip-6.0-16.el7.x86_64                                      | unzip-6.0-16.el7.x86_64                      | unzip-6.0-16.el7.x86_64                         | unzip-6.0-16.el7.x86_64                    | unzip-6.0-19.el7.x86_64                    | unzip-6.0-19.el7.x86_64                    |
| texinfo                                         | texinfo-5.1-5.el7.x86_64                                     | texinfo-5.1-5.el7.x86_64                     | texinfo-5.1-5.el7.x86_64                        | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   |
| zlib1g-dev                                      |                                                              |                                              |                                                 |                                            |                                            |                                            |
| gcc-multilib                                    |                                                              |                                              |                                                 |                                            |                                            |                                            |
| build-essential                                 |                                                              |                                              |                                                 |                                            |                                            |                                            |
| SDL-devel                                       | SDL-devel-1.2.15-14.el7.x86_64                               | SDL-devel-1.2.15-14.el7.x86_64               | SDL-devel-1.2.15-14.el7.x86_64                  | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             |
| glibc-devel                                     | glibc-devel-2.17-292.el7.x86_64                              | glibc-devel-2.17-292.el7.x86_64              | glibc-devel-2.17-292.el7.x86_64                 | glibc-devel-2.17-292.el7.x86_64            | glibc-devel-2.17-292.el7.x86_64            | glibc-devel-2.17-292.el7.x86_64            |
|                                                 |                                                              |                                              |                                                 |                                            |                                            |                                            |
| glib2-devel                                     | glib2-devel-2.56.1-5.el7.x86_64                              | glib2-devel-2.56.1-5.el7.x86_64              | glib2-devel-2.56.1-5.el7.x86_64                 | glib2-devel-2.56.1-5.el7.x86_64            | glib2-devel-2.56.1-5.el7.x86_64            | glib2-devel-2.56.1-5.el7.x86_64            |
| automake                                        | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                    | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               |
| screen                                          | gnome-screenshot-3.22.0-1.el7.x86_64                         | gnome-screenshot-3.22.0-1.el7.x86_64         | gnome-screenshot-3.22.0-1.el7.x86_64            | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       |
| pax                                             | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                        | pax-3.4-19.el7.x86_64                           | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      |
| gzip                                            | gzip-1.5-9.el7.x86_64                                        | gzip-1.5-9.el7.x86_64                        | gzip-1.5-9.el7.x86_64                           | gzip-1.5-9.el7.x86_64                      | gzip-1.5-10.el7.x86_64                     | gzip-1.5-9.el7.x86_64                      |
| libstdc++                                       | libstdc++-4.8.5-16.el7_4.1.x86_64                            | libstdc++-4.8.5-16.el7_4.1.x86_64            | libstdc++-4.8.5-16.el7_4.1.x86_64               | libstdc++-4.8.5-16.el7_4.1.x86_64          | libstdc++-4.8.5-39.el7.x86_64              | libstdc++-4.8.5-39.el7.x86_64              |
| g++ (gcc-c++)                                   | gcc-c++-4.8.5-16.el7_4.1.x86_64                              | gcc-c++-4.8.5-16.el7_4.1.x86_64              | gcc-c++-4.8.5-16.el7_4.1.x86_64                 | gcc-c++-4.8.5-16.el7_4.1.x86_64            | gcc-c++-4.8.5-16.el7_4.1.x86_64            | gcc-c++-4.8.5-39.el7.x86_64                |
| patch                                           | patch-2.7.1-8.el7.x86_64                                     | patch-2.7.1-8.el7.x86_64                     | patch-2.7.1-8.el7.x86_64                        | patch-2.7.1-8.el7.x86_64                   | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_64                  |
| zlib                                            | zlib-1.2.7-18.el7.x86_64                                     | zlib-1.2.7-18.el7.x86_64                     | zlib-1.2.7-18.el7.x86_64                        | zlib-1.2.7-18.el7.x86_64                   | zlib-1.2.7-18.el7.x86_64                   | zlib-1.2.7-18.el7.x86_64                   |
| python2                                         | Python 2.7.5                                                 | Python 2.7.5                                 | Python 2.7.5                                    | Python 2.7.5                               | Python 2.7.5                               | Python 2.7.5                               |
| tftpd                                           |                                                              |                                              |                                                 |                                            |                                            |                                            |
| libssl-dev                                      |                                                              |                                              |                                                 |                                            |                                            |                                            |
| diffutils                                       | diffutils-3.3-4.el7.x86_64                                   | diffutils-3.3-4.el7.x86_64                   | diffutils-3.3-4.el7.x86_64                      | diffutils-3.3-4.el7.x86_64                 | diffutils-3.3-4.el7.x86_64                 | diffutils-3.3-4.el7.x86_64                 |
| bzip2.x86-64                                    | bzip2-1.0.6-13.el7.x86-64                                    | bzip2-1.0.6-13.el7.x86-64                    | bzip2-1.0.6-13.el7.x86-64                       | bzip2-1.0.6-13.el7.x86-64                  | bzip2-1.0.6-13.el7.x86-64                  | bzip2-1.0.6-13.el7.x86-64                  |
| perl                                            | perl-5.16.3-292.el7.x86_64                                   | perl-5.16.3-292.el7.x86_64                   | perl-5.16.3-292.el7.x86_64                      | perl-5.16.3-292.el7.x86_64                 | perl-5.16.3-292.el7.x86_64                 | perl-5.16.3-292.el7.x86_64                 |
| cpp                                             | cpp-4.8.5-16.el7.x86_64                                      | cpp-4.8.5-28.el7.x86_64                      | cpp-4.8.5-39.el7.x86_64                         | cpp-4.8.5-16.el7.x86_64                    | cpp-4.8.5-28.el7.x86_64                    | cpp-4.8.5-39.el7.x86_64                    |
| glibc-devel                                     | glibc-devel-2.17.292.el7.x86-64                              | glibc-devel-2.17.292.el7.x86-64              | glibc-devel-2.17.292.el7.x86-64                 | glibc-devel-2.17.292.el7.x86-64            | glibc-devel-2.17.292.el7.x86-64            | glibc-devel-2.17.292.el7.x86-64            |
| perl-dat-dumper                                 | perl-dat-dumper-2.145-3.el7.x86_64                           | perl-dat-dumper-2.145-3.el7.x86_64           | perl-dat-dumper-2.145-3.el7.x86_64              | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         |
| perl-thread-queue                               | perl-thread-queue-3.02-2.el7.noarch                          | perl-thread-queue-3.02-2.el7.noarch          | perl-thread-queue-3.02-2.el7.noarch             | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        |
| xz                                              | xz-5.2.2-1.el7.x86_64                                        | xz-5.2.2-1.el7.x86_64                        | xz-5.2.2-1.el7.x86_64                           | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      |
| perl-Text-ParseWords                            |                                                              | perl-Text-ParseWords-3.29-4.el7.noarch       | perl-Text-ParseWords-3.29-4.el7.noarch          |                                            | perl-Text-ParseWords-3.29-4.el7.noarch     | perl-Text-ParseWords-3.29-4.el7.noarch     |
| python34-pip                                    | python34-pip-8.1.2-10.el7.noarch                             | python34-pip-8.1.2-10.el7.noarch             | python34-pip-8.1.2-10.el7.noarch                | python34-pip-8.1.2-10.el7.noarch           | python34-pip-8.1.2-10.el7.noarch           | python34-pip-8.1.2-10.el7.noarch           |

### Ubuntu

| Tool/Library                                    | Ubuntu Desktop   /Server 16.04.05(64-bit)                    | Ubuntu Desktop /Server 16.04.06 (64-bit) | Ubuntu Desktop /Server 18.04.01 (64-bit)    | Ubuntu Desktop /Server 18.04.02 (64-bit)    |
| ----------------------------------------------- | ------------------------------------------------------------ | ---------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| Quick Installation steps for packages:          | sudo apt-get install gawk python build-essential gcc git make net-tools libncurses5-dev tftpd zlib1g-dev libssl-dev flex bison libselinux1 gnupg wget diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib build-essential-dev zlib1g:i386 screen pax gzip |                                          |                                             |                                             |
| kernel Version                                  | 4.15.0-45-generic                                            | 4.15.0-45-generic                        | 4.15.0-29-generic                           | 5.0.0-31-generic                            |
| dos2unix                                        | dos2unix-6.0.4-1 500                                         | dos2unix-6.0.4-1 500                     | dos2unix-7.3.4-3                            | dos2unix-7.3.4-3                            |
| ip (iproute)                                    |                                                              |                                          |                                             |                                             |
| gawk                                            | gawk-1:4.1.3+dfsg-0.1                                        | gawk-1:4.1.3+dfsg-0.1                    | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   |
| gcc                                             | gcc-4:5.3.1-1ubuntu1 500                                     | gcc-4:5.3.1-1ubuntu1 500                 | gcc-4:7.4.0-1ubuntu2.3                      | gcc-4:7.4.0-1ubuntu2.3                      |
| git                                             | git-1:2.7.4-0ubuntu1.6 500                                   | git-1:2.7.4-0ubuntu1.6 500               | git-1:2.17.1-1ubuntu0.4                     | git-1:2.17.1-1ubuntu0.4                     |
| make                                            | make-4.1-6 500                                               | make-4.1-6 500                           | make-4.1-9.1ubuntu1                         | make-4.1-9.1ubuntu1                         |
| netstat (net-tools)                             | net-tools-1.60-26ubuntu1 500                                 | net-tools-1.60-26ubuntu1 500             | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-6.0+20160213-1ubuntu1                          | ncurses-devel-6.0+20160213-1ubuntu1      | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            |
| tftp-server                                     |                                                              |                                          |                                             |                                             |
| zlib-devel(also,install 32-bit of this version) |                                                              |                                          |                                             |                                             |
|                                                 |                                                              |                                          |                                             |                                             |
| openssl-devel                                   | openssl-devel-1.0.2g-1ubuntu4.15                             | openssl-devel-1.0.2g-1ubuntu4.15         | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-ubuntu2.1~18.04.4       |
| flex                                            | flex-2.6.0-11                                                | flex-2.6.0-11                            | flex-2.6.4-6                                | flex-2.6.4-6                                |
| bison                                           | bison-2:3.0.4.dfsg-1                                         | bison-2:3.0.4.dfsg-1                     | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  |
| libselinux                                      |                                                              |                                          |                                             |                                             |
| gnupg                                           | gnupg-1.4.20-1ubuntu3.3                                      | gnupg-1.4.20-1ubuntu3.3                  | gnupg-2.2.4-1ubuntu1.2                      | gnupg-2.2.4-1ubuntu1.2                      |
| wget                                            | wget-1.17.1-1ubuntu1.5                                       | wget-1.17.1-1ubuntu1.5                   | wget-1.19.4-1ubuntu2.2                      | wget-1.19.4-1ubuntu2.2                      |
| diffstat                                        | diffstat-1.61-1                                              | diffstat-1.61-1                          | diffstat-1.61-1build1                       | diffstat-1.61-1build1                       |
| chrpath                                         | chrpath-0.16-1                                               | chrpath-0.16-1                           | chrpath-0.16-2                              | chrpath-0.16-2                              |
| socat                                           | socat-1.7.3.1-1                                              | socat-1.7.3.1-1                          | socat-1.7.3.2-2ubuntu2                      | socat-1.7.3.2-2ubuntu2                      |
| xterm                                           | xterm-322-1ubuntu1                                           | xterm-322-1ubuntu1                       | xterm-330-1ubuntu2                          | xterm-330-1ubuntu2                          |
| autoconf                                        | autoconf-2.69-9                                              | autoconf-2.69-9                          | autoconf-2.69-11                            | autoconf-2.69-11                            |
| libtool                                         | libtool-2.4.6-0.1                                            | libtool-2.4.6-0.1                        | libtool-2.4.6-2                             | libtool-2.4.6-2                             |
| tar                                             | tar-1.28-2.1                                                 | tar-1.28-2.1                             | tar-1.29b-2ubuntu0.1                        | tar-1.29b-2ubuntu0.1                        |
| unzip                                           | unzip-6.0-20ubuntu1                                          | unzip-6.0-20ubuntu1                      | unzip-6.0-21ubuntu1                         | unzip-6.0-21ubuntu1                         |
| texinfo                                         | texinfo-6.1.0.dfsg.1-5                                       | texinfo-6.1.0.dfsg.1-5                   | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      |
| zlib1g-dev                                      | zlib1g-dev1:1.2.8.dfsg-2ubuntu4.1                            | zlib1g-dev1:1.2.8.dfsg-2ubuntu4.1        | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            |
| gcc-multilib                                    | gcc-multilib-4:5.3.1-1ubuntu1                                | gcc-multilib-4:5.3.1-1ubuntu1            | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             |
| build-essential                                 | build-essential-12.1ubuntu2                                  | build-essential-12.1ubuntu2              | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 |
| SDL-devel                                       |                                                              |                                          |                                             |                                             |
| glibc-devel                                     |                                                              |                                          |                                             |                                             |
|                                                 |                                                              |                                          |                                             |                                             |
| glib2-devel                                     |                                                              |                                          |                                             |                                             |
| automake                                        | automake-1:1.15-4ubuntu1                                     | automake-1:1.15-4ubuntu1                 | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  |
| screen                                          | gnome-screenshot-4.3.1-2build1                               | gnome-screenshot-4.3.1-2build1           | gnome-screenshot-4.6.2-1ubuntu1             | gnome-screenshot-4.6.2-1ubuntu1             |
| pax                                             | pax-1:20151013-1                                             | pax-1:20151013-1                         | pax-1:20171021-2                            | pax-1:20171021-2                            |
| gzip                                            | gzip-1.6-4ubuntu1                                            | gzip-1.6-4ubuntu1                        | gzip-1.6-5ubuntu1                           | gzip-1.6-5ubuntu1                           |
| libstdc++                                       | libstdc++-5.4.0-6ubuntu1~16.04.9cross1                       | libstdc++-5.4.0-6ubuntu1~16.04.9cross1   | libstdc++-6.5.0-2ubuntu1~18.04              | libstdc++-8.3.0-6ubuntu1~18.04.1            |
| g++ (gcc-c++)                                   | gcc-c++-4:5.3.1-1ubuntu1                                     | gcc-c++-4:5.3.1-1ubuntu1                 | gcc-c++-4:7.4.0-1ubuntu2.3                  | gcc-c++-7.4.0-1ubuntu1~18.04.1              |
| patch                                           | patch-2.7.5-1ubuntu0.16.04.1                                 | patch-2.7.5-1ubuntu0.16.04.1             | patch-2.7.6-2ubuntu1                        | patch-2.7.6-2ubuntu1                        |
| zlib                                            |                                                              |                                          |                                             |                                             |
| python2                                         | Python 2.7.12                                                | Python 2.7.12                            | Python 2.7.15~rc1-1                         | Python 2.7.15                               |
| tftpd                                           | tftpd-0.17-18ubuntu2                                         | tftpd-0.17-18ubuntu2                     | tftpd-0.17-18ubuntu3                        | tftpd-0.17-18ubuntu3                        |
| libssl-dev                                      | libssl-dev-1.0.2g-1ubuntu4.15                                | libssl-dev-1.0.2g-1ubuntu4.15            | libssl-dev-1.1.1-1ubuntu2.1~18.04.4         | libssl-dev-1.1.1-1ubuntu2.1~18.04.4         |
| diffutils                                       | diffutils-1:3.3-3                                            | diffutils-1:3.3-3                        | diffutils-1:3.6-1                           | diffutils-1:3.6-1                           |
| bzip2.x86-64                                    | bzip2-1.0.6-13.el7.x86-64                                    | bzip2-1.0.6-8ubuntu0.2                   | bzip2-1.0.6-8ubuntu0.2                      | bzip2-1.0.6-8ubuntu0.2                      |
| perl                                            | perl-5.16.3-292.el7.x86_64                                   | perl-5.22.1-9ubuntu0.6                   | perl-5.22.1-9ubuntu0.6                      | perl-5.22.1-9ubuntu0.6                      |
| cpp                                             | cpp-4:5.3.1-1ubuntu1                                         | cpp-4:5.3.1-1ubuntu1                     | cpp-4:5.3.1-1ubuntu1                        | cpp-4:5.3.1-1ubuntu1                        |
| glibc-devel                                     |                                                              |                                          |                                             |                                             |
| perl-dat-dumper                                 |                                                              |                                          |                                             |                                             |
| perl-thread-queue                               |                                                              |                                          |                                             |                                             |
| xz                                              |                                                              |                                          |                                             |                                             |
| perl-Text-ParseWords                            |                                                              |                                          |                                             |                                             |
| python34-pip                                    | pip-19.3.1                                                   | pip-19.3.1                               | pip-9.0.1                                   | python34-pip-19.3.1                         |