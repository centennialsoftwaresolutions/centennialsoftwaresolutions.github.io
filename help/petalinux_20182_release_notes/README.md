# 71201 - PetaLinux 2018.2 - Product Update Release Notes and Known Issues

## Title

71201 - PetaLinux 2018.2 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2018.2 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for the 2018.2 PetaLinux Release**

This table contains supported BSPs for Zynq-7000, MicroBlaze, Zynq UltraScale+ MPSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

| Platform               | Variant                   | BSP Name                   |
| ---------------------- | ------------------------- | -------------------------- |
| Zynq-7000              | ZC702                     | ZC702 BSP                  |
| Zynq-7000              | ZC706                     | ZC706 BSP                  |
| Zynq-7000              | ZEDBOARD                  | ZED BSP                    |
| MicroBlaze             | AC701                     | AC701 BSP                  |
| MicroBlaze             | KCU105                    | KCU105                     |
| MicroBlaze             | KC705                     | KC705 BSP                  |
| Zynq UltraScale+ MPSoC | ZCU102 production silicon | ZCU102 BSP (prod-silicon)  |
| Zynq UltraScale+ MPSoC | ZCU102 ZU9 ES2 Rev 1.0    | ZCU102 ZU9 ES2 Rev 1.0 BSP |
| Zynq UltraScale+ MPSoC | ZCU104 production silicon | ZCU104 BSP                 |
| Zynq UltraScale+ MPSoC | ZCU106 production silicon | ZCU106 BSP                 |
| Zynq UltraScale+ RFSoC | ZCU111 production silicon | ZCU111 BSP                 |

**Note**: The "[sstate cache file](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate-rel-v2018.2.tar.gz)" (sstate-rel-v2018.2.tar.gz) can be found on the Xilinx download area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2018.2_README) (sstate_rel_2018.2_README) file that outlines the procedure to use "sstate cache".

Refer to the attached file "2018.2_PetaLinux_Packages_List" for software package versions tested on host machines, which is required for PetaLinux installation tools.

See also the attached README.

 

**PetaLinux 2018.2 contains the following build collateral:**

| Component                  | Git repo                                                     | Git Branches      | Git Tags                 | Commit ID                                                    | Comments                                                     |
| -------------------------- | ------------------------------------------------------------ | ----------------- | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| FSBL                       | git://github.com/Xilinx/embeddedsw.git                       | master            | xilinx-v2018.2           | "6e82c0183bdfb9c6838966b9b87ef8385ba35504"                   | FSBL for Zynq-7000 is at `embeddedsw/lib/sw_apps/zynq_fsbl`<br>FSBL for Zynq UltraScale+ is at `embeddedsw/lib/sw_apps/zynqmp_fsbl` |
| PMU Firmware               | git://github.com/Xilinx/embeddedsw.git                       | master            | xilinx-v2018.2           | "6e82c0183bdfb9c6838966b9b87ef8385ba35504"                   | PMU for Zynq UltraScale+ Firmware is at `embeddedsw/lib/sw-apps/zynqmp_pmufw` |
| Device-tree                | git://github.com/Xilinx/device-tree-xlnx.git                 | master            | xilinx-v2018.2           | "f38738e568210695f06bab078900d9469c2eff7b"                   |                                                              |
| Linux                      | git://github.com/Xilinx/linux-xlnx.git                       | xlnx_rebase_v4.14 | xlnx_rebase_v4.14_2018.2 | "ad4cd988ba86ab0fb306d57f244b7eaa6cce79a4"                   | Linux Kernel rebase version 4.14                             |
| U-Boot                     | git://github.com/Xilinx/u-boot-xlnx.git                      | master            | xilinx-v2018.2           | "21812b5fd359d8756d619a15b49b6079ae3f9f36"                   | U-Boot Version v2018.01                                      |
| QEMU                       | git://github.com/Xilinx/qemu.git                             | master            | xilinx-v2018.2           | "f5fb2a88ffe61ccb049715cb11b34e9cb216fd5c"                   |                                                              |
| Xen                        | git://github.com/Xilinx/xen.git                              | xilinx/stable-4.9 | xilinx-v2018.2           | "c227fe68589bdfb36b85f7b78c034a40c95b9a30"                   |                                                              |
| ARM-Trusted-Firmware (ATF) | git://github.com/Xilinx/arm-trusted-firmware.git             | master            | xilinx-v2018.2           | "93a69a5a3bc318027da4af5911124537f4907642"                   | ATF is based on upstream version 1.4                         |
| Yocto                      | git://github.com/Xilinx/meta-xilinx.git<br>git://github.com/Xilinx/meta-xilinx-tools.git<br>git://github.com/Xilinx/meta-petalinux.git | rel-v2018.2       | No Tags                  | "b7110d72bede3fd98eb350400db8ef55f0c39f28"<br>"620a0368d981c1648664865f245ef1051c6b9a06"<br>"68cb2ce19105a05fc60fc495b98cbeac04bfb85e" | Yocto 2.4.1 Rocko                                            |
| qemu-devicetrees           | git://github.com/Xilinx/qemu-devicetrees.git                 | master            | xilinx-v2018.2           | "181fb682575057b8f572a5e0d38e0b5bb78c845c"                   |                                                              |
| OpenAMP                    | git://github.com/Xilinx/open-amp.git                         | master            | xilinx-v2018.2           | "7f2d8ca88d643a9cec993add93d1630b2c7bd41e"                   |                                                              |
| libmetal                   | git://github.com/Xilinx/libmetal.git                         | master            | xilinx-v2018.2           | "18048c4144f276cda793c125399057a6b5773edb"                   |                                                              |
| VCU OpenMax IL             | git://github.com/Xilinx/vcu-omx-il.git                       | master            | xilinx-v2018.2           | "520542d3350ab8d2ccb9c3cf0044550539f95a42"                   |                                                              |
| VCU Control Software       | git://github.com/Xilinx/vcu-ctrl-sw.git                      | master            | xilinx-v2018.2           | "2975ba25430a221a3feaca4839f5a13424972a68"                   |                                                              |
| VCU Firmware               | git://github.com/Xilinx/vcu-firmware.git                     | master            | xilinx-v2018.2           | "a847c94546c3711a9d2b61bd6a568bc8f46a99bd"                   |                                                              |
| VCU Modules                | git://github.com/Xilinx/vcu-modules.git                      | master            | xilinx-v2018.2           | "646185390cc1850969c0fa3db59fc8f0e511922e"                   |                                                              |
| GStreamer OpenMax IL       | git://github.com/Xilinx/gst-omx.git                          | xilinx-master     | xilinx-v2018.2           | "5c2c023185923c88982dd55d1a7ade08c9a06e97"                   |                                                              |
| GStreamer Plugins-Base     | git://github.com/Xilinx/gst-plugins-base.git                 | master-rel-1.12.2 | xilinx-v2018.2           | "244ba6f2ad1915f6b9f62f8d8e8efbce1cf10ebb"                   |                                                              |
| GStreamer Plugins-Bad      | git://github.com/Xilinx/gst-plugins-bad.git                  | master-rel-1.12.2 | xilinx-v2018.2           | "230ad55826c3b1600fa2b57e5c02a77335d357a4"                   |                                                              |
| GStreamer Plugins-Good     | git://github.com/Xilinx/gst-plugins-good.git                 | master-rel-1.12.2 | xilinx-v2018.2           | "d7cac4c10e6365e5cc3ea06edb6646533fd5ce2c"                   |                                                              |
| GCC                        | —                                                            | —                 | —                        | —                                                            | MB compiler version 7.2                                      |
| ARM                        | —                                                            | —                 | —                        | —                                                            | ARM compiler version 7.2                                     |

**Wiki Updates:**

Covers details for below components changes (new features/fixes) in a particular release. 

**2018.2 FSBL release notes wiki page:**

http://www.wiki.xilinx.com/FSBL

**2018.2 PMUFW release notes wiki page:**

http://www.wiki.xilinx.com/PMU+Firmware

**2018.2 ATF release notes wiki page:**

http://www.wiki.xilinx.com/2018.2+ATF+Release+Notes


**2018.2 U-Boot release notes wiki page:**

http://www.wiki.xilinx.com/2018.2+u-boot+release+notes

**2018.2 Linux and DTG release notes wiki page:**

http://www.wiki.xilinx.com/2018.2+Linux+and+DTG+Release+Notes

**2018.2 Power Management release notes wiki page:**

[http://www.wiki.xilinx.com/Zynq+UltraScale%EF%BC%8B+MPSoC+Power+Management](http://www.wiki.xilinx.com/Zynq+UltraScale＋+MPSoC+Power+Management)

**2018.2 Baremetal Drives and Libraries release notes wiki page:**

http://www.wiki.xilinx.com/Baremetal+Drivers+and+Libraries

**2018.2 OpenAMP release notes wiki page:**

[http://www.wiki.xilinx.com/OpenAMP%202018.2](http://www.wiki.xilinx.com/OpenAMP 2018.2)

**2018.2 QEMU release notes wiki page:**

http://www.wiki.xilinx.com/QEMU

**2018.2 VCU release notes wiki page:**

http://www.wiki.xilinx.com/Xilinx+Video+Codec+Unit

**2018.2 New Features:**

 

**PetaLinux**

- PetaLinux BSPs for Ultra96 (Rev 1.0) and ZCU111 production boards.

**Yocto**

- None

 

 

**FSBL**

 

- None

 

**U-boot**

 

- Added support for QPSI I/O mode for Zynq UltraScale+ devices.
- Fixed saveenv to SPI flash issue on AC701.
- Added support to setup MMU map based on memory node entries in device-tree for Zynq UltraScale+ devices.
- Added support to load bitstreams using zynqrsa command for Zynq devices.
- Fixed issue with Macronix QSPI flash devices in dual parallel mode.
- Add support for Macronix devices mx25u12835f and mx25u25635f.
- Enhanced Key Revocation XILSECURE for Zynq UltraScale+ devices.

**Device-tree Generator (DTG)**

- Add support for USB 2.0 for Zynq UltraScale+ devices.

 

**ARM-Trusted Firmware (ATF)**

- Add Zynq UltraScale+ MPSoC firmware IOCTL to set healthy bit.
- Fixed deprecated warnings.

 

**PMU Firmware (PMUFW)**

- Change healthy bit from GGS0[29] to GGS4[0]
- Provide read and write access to AFI configuration registers
- Enable PLL lock errors only after FSBL completes psu_init to avoid initial
- PLL lock errors that occur during psu_init
- Increased polling period of DDR status register to 1ms which is used during
- DDR re-initialization since 100us is not enough for some DDR memories
- Fix proc assignment in PmProcGetByWakeMask by returning proc pointer instead of node structure pointer
- If POS is enabled, signal the FSBL with boot type in APU only restart to avoid infinite wait loop in FSBL
- Use proper function(PmSlaveChangeState) when resetting the slave state
- Power Management
- Fixed APU only reset when Power Off Suspend is enabled
- Fixed reboot fail after powering down PLD issue
- Fixed compilation warning in xilpm build
- Updated SDK DDR self refresh example to use PMU APIs

**Linux Kernel and Drivers**

- Firmware driver
  - Add ZynqMP firmware sysfs and IOCTL to set healthy bit
- Display Port
  - Override the preferred format for fbdev. This allows the fbdev to be initialized with AR24
  - Update DRM planes asynchronously. Otherwise, framerate is time-shared when CRTC and plane are running.
- AXI DMA Driver
  - Add 64MB data transfer support.
- FPGA Manager
  - Add support for PL bitstream partial reconfiguration. For more details refer to the [ZynqMP PL Programming](http://www.wiki.xilinx.com/Solution+ZynqMP+PL+Programming) wiki page.

**OpenAMP and Libmetal**

- None

**QEMU**

 

- None

**VCU**

- Fixed AVC Decoder hang issue for corrupted input file
- Fixed data corruption issue observed with b-frame enable
- Fixed zynqmp_vcu_encode application to support b-frames in AVC.
- Fixed long run frame drop issue for AVC1080p60 decode display with large input file
- Fixed bad parameter error when setting baseline profile and level=5.1
- Fixed MCU clock division calculation in VCU Init driver.
- Improve CBR/VBR rate control for static video sequences.

 

**XEN**

 

- None

**FreeRTOS**

 

- Updated licensing information as per FreeRTOS 10.0

 

**Power Management**

 

- None

 

**Baremetal Drivers and Libraries**

- rfdc_v4_0:
  - Added XRFdc_MTS_Sysref_Config API to enable/disable sysref.
  - Updated max VCO value to 13108MHz to support max DAC sample rate of 6.554MHz.
  - Added macro to configure Threshold OFF mode.
  - Adjust calculated latency by sysref period, where doing so results in closer alignment to the target latency.
  - Corrected Set/Get MixerSettings API description for FineMixerScale parameter.
  - Enable VCO Auto selection while configuring the clock.
  - Added XRFdc_GetPLLConfig() API to get PLL Configurations.
  - Added XRFdc_GetLinkCoupling() API to get the Link Coupling mode.
  - Added clock configuration files for ZCU111 in examples.
- standalone_v6_7:
  - Fixed compilation warnings in xil_sleeptimer.c
- xilfpga_v4_1:
  - Added partial bitstream loading support.
- xilsecure_v3_1:
  - Added support for 512, 576, 704, 768, 992, 1024, 1152, 1408, 1536,1984, 3072 key sizes, where previous version has support only 2048 and 4096 key sizes.
  - On GCM tag failure, wrongly decrypted data will be zeroized.
  - Added support of user fuses revocation for single partition image.
  - Modified xilsecure_aes_example,input data will be overwritten with decrypted data
  - Added compilation flag for opting secure/non-secure environment, by default it is non -secure, mainly it is taken into account while building PMUFW
- xilskey_v6_5:
  - Fixed hanging issue for BBRAM Zynq UltraScale+ MPSoC when program/zeroize is requested while programming mode is in enabled state

**Known Issues for 2018.2:**

| Linux/Baremetal | Components       | Description                                                  | Work-around                                                  | To be fixed version |
| :-------------- | :--------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :------------------ |
| Linux           | Yocto/PetaLinux  | 2018.x Yocto/PetaLinux: Ubuntu 18.04.x LTS support           | [(Xilinx Answer 71448)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71448) |                     |
| Linux           | PetaLinux        | Zynq UltraScale+ MPSoC: How to enable UHS (SD 3.0) support for ZCU102 and ZCU106 evaluation board PetaLinux BSPs | [(Xilinx Answer 69978)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=69978) |                     |
| Linux           | XSDK             | 2017.x-2018.x Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle | [(Xilinx Answer 69143)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=69143) |                     |
| Linux           | Yocto, PetaLinux | 2018.x Zynq UltraScale+ MPSoC: Yocto or PetaLinux throws warnings when the build do_rootfs task completes | [(Xilinx Answer 71110)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71110) |                     |
| Linux           | Drivers          | 2018.1/2 Zynq UltraScale+ MPSoC: PetaLinux Warm-Restart BSP fails to wakeup Ethernet when FPD is off | [(Xilinx Answer 71028)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71028) | 2018.3              |
| Baremetal       | FSBL             | 2018.1/2 Zynq UltraScale+ MPSoC: FSBL R5 application does not work with default isolation enabled. | [(Xilinx Answer 71015)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71015) | 2018.3              |
| Linux           | VCU              | 2018.1/2 Zynq UltraScale+ MPSoC VCU - Why does the VCU MCU throw an exception when using multiple streams and Low Latency mode? | [(Xilinx Answer 71020)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71020) | 2018.3              |
| Linux           | VCU-GStreamer    | 2018.1/2 Zynq UltraScale+ MPSoC VCU: Why do I see frame drops at bitrates > 500Mbps when using GStreamer? | [(Xilinx Answer 71021)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71021) | 2018.3              |
| Linux           | Drivers          | 2018.1/2 Zynq UltraScale+ MPSoC: Linux 4.14 driver always assumes that the Display Port (GTR's) output will be used | [(Xilinx Answer 71043)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71043) | 2018.3              |
| Linux           | Drivers          | 2018.1/2 Zynq UltraScale+ MPSoC: Linux 4.14 driver does not support both PL live input and DP DMA input at the same time | [(Xilinx Answer 71044)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71044) | 2018.3              |
| Linux           | Device-tree      | 2018.1/2 Zynq UltraScale+ MPSoC: OpenAMP source device-tree file name has incorrect naming convention | [(Xilinx Answer 71048)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71048) | 2018.3              |
| Linux           | PetaLinux        | 2018.1/2 Zynq UltraScale+ MPSoC: ATF does not build in PetaLinux or Yocto when ATF DEBUG is enabled | [(Xilinx Answer 71156)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71156) | 2018.3              |
| Linux           | Drivers          | 2018.1/2 Zynq UltraScale+ MPSoC: Linux DRM driver does not need to update the plane for same framebuffer | [(Xilinx Answer 71230)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71230) | 2018.3              |
| Linux           | PetaLinux        | 2017.1-2018.2 Zynq-7000: Cannot boot Zynq-7000 PetaLinux images individually in legacy flow | [(Xilinx Answer 71231)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71231) | 2018.3              |
| Linux           | PetaLinux        | 2018.2 Ultra96: PetaLinux fails to build ultra96 BSP without network | [(Xilinx Answer 71240)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71240) | 2018.3              |
| Linux           | PetaLinux        | 2018.1/2 Zynq UltraScale+ MPSoC: PetaLinux ATF cannot boot up in QSPI flash mode when only UART1 is enabled in a Vivado design | [(Xilinx Answer 71272)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71272) | 2018.3              |
| Baremetal       | Xilfpga          | 2018.1/2 Zynq UltraScale+ MPSoC: PL programming from U-boot and Linux requires different bitstream formats | [(Xilinx Answer 71327)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71327) | 2018.3              |
| Linux           | Drivers          | 2018.1/2 Zynq UltraScale+ MPSoC: Linux GEM PTP time adjustment fails for large negative delta | [(Xilinx Answer 71332)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71332) | 2018.3              |
| Linux           | Device-tree      | 2018.2 Zynq UltraScale+ RFSoC: Additional settings required for Ethernet (using FMC card) to work on ZC1275 | [(Xilinx Answer 71333)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71333) | 2018.3              |
| Linux           | VCU              | 2018.1/2 Zynq UltraScale+ MPSoC - Video Codec Unit (VCU) TRD Design Module 3 does not build when using BB_NO_NETWORK (without network) | [(Xilinx Answer 71381)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71381) | 2018.3              |
| Linux           | Yocto            | 2018.1/2 Zynq UltraScale+ MPSoC - Video Codec Unit (VCU) TRD Design Module does not build with PetaLinux SDK generation | [(Xilinx Answer 71382)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71382) | 2018.3              |
| Linux           | Drivers          | 2017.1-2018.2 Zynq UltraScale+ MPSoC: Linux kernel boot failed while mounting a JFFS2 filesystem in QSPI boot mode | [(Xilinx Answer 71114)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71114) | 2018.3              |
| Linux           | Drivers          | 2017.1-2018.2 Zynq UltraScale+ MPSoC: Linux kernel panic for JFFS2 filesystem on POR or reboot | [(Xilinx Answer 71439)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71439) | 2018.3              |
| Linux           | PetaLinux        | 2018.2 Zynq UltraScale+ RFSoC: PetaLinux fails to build ZCU111 BSP without network | [(Xilinx Answer 71657)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71657) | 2018.3              |
| Linux           | VCU              | 2018.2 Zynq UltraScale+ MPSoC VCU - Why do I see the VCU control software fail to release memory after encoding? | [(Xilinx Answer 71815)](https://xilinx.sharepoint.com/sites/XKB/SitePages/Articleviewer.aspx?ArticleNumber=71815) | 2018.3              |

# README_content_v2018.2

=============================

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2018.2 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2018.2 Open Components Source Code (TAR/GZIP) file: 
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

# 2018.2_PetaLinux_Package_List

## Tool/Library Versions

### RHEL/CentOS versions

| Tool/Library                                    | CentOS 7.2                                                   | CentOS 7.3                                                   | CentOS 7.4                                                   | RHEL 7.2                                                     | RHEL 7.3                                                  | RHEL 7.4                                                     |
| ----------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------------------ |
| kernel Version                                  | 3.10.0-693.21.1.el7.x86_64                                   | 3.10.0-693.21.1.el7.x86_64                                   | 3.10.0-693.21.1.el7.x86_64                                   | 3.10.0-327.el7.x86_64                                        | 3.10.0-693.21.1.el7.x86_64                                | 3.10.0-693.21.el7.x86_64                                     |
| dos2unix                                        | dos2unix-6.0.3-7.el7.x86_64                                  | dos2unix-6.0.3-7.el7.x86_64                                  | dos2unix-6.0.3-7.el7.x86_64                                  | dos2unix-6.0.3-7.el7.x86_64                                  | dos2unix-6.0.3-7.el7.x86_64                               | dos2unix-6.0.3-7.el7.x86_64                                  |
| ip (iproute)                                    | iproute-3.10.0-87.0.1.el7.x86_64                             | iproute-3.10.0-87.el7.x86_64                                 | iproute-3.10.0-87.el7.x86_64                                 | iproute-3.10.0-87.0.1.el7.x86_64                             | iproute-3.10.0-74.0.1.el7.x86_64                          | iproute-3.10.0-87.0.1.el7.x86_64                             |
| gawk                                            | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7.x86_64                                   | gawk-4.0.2-4.el7_3.1.x86_64                                  |
| xvfb                                            | xorg-x11-server-Xvfb-1.19.3-11.el7_4.2.x86_64                | xorg-x11-server-Xvfb-1.19.3-11.el7_4.2.x86_64                | xorg-x11-server-Xvfb-1.19.3-11.el7_4.2.x86_64                | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                     | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                  | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                     |
| gcc(for RHEL, use devtoolset-2)                 | gcc-4.8.5-16.0.3.el7_4.2.x86_64                              | gcc-4.8.5-16.0.3.el7_4.2.x86_64                              | gcc-4.8.5-16.el7_4.2.x86_64                                  | gcc-4.8.5-16.el7.x86_64                                      | gcc-4.8.5-11.el7.x86_64                                   | gcc-4.8.5-16.0.1.el7_4.1.x86_64                              |
| git                                             | git-1.8.3.1-12.el7_4.x86_64                                  | git-1.8.3.1-12.el7_4.x86_64                                  | git-1.8.3.1-12.el7_4.x86_64                                  | git-1.8.3.1-12.el7_4.x86_64                                  | git-1.8.3.1-6.el7_2.1.x86_64                              | git-1.8.3.1-12.el7_4.x86_64                                  |
| make                                            | make-3.82-23.el7.x86_64                                      | make-3.82-23.el7.x86_64                                      | make-3.81-23.el6.x86_64                                      | make-3.82-23.el7.x86_64                                      | make-3.82-23.el7.x86_64                                   | make-3.82-23.el7.x86_64                                      |
| netstat (net-tools)                             | net-tools-2.0-0.22.20131004git.el7.x86_64                    | net-tools-2.0-0.22.20131004git.el7.x86_64                    | net-tools-2.0-0.22.20131004git.el7.x86_64                    | net-tools-2.0-0.22.20131004git.el7.x86_64                    | net-tools-2.0-0.17.20131004git.el7.x86_64                 | net-tools-2.0-0.22.20131004git.el7.x86_64                    |
| ncurses-devel                                   | ncurses-devel-5.9-14.20130511.el7.x86_64                     | ncurses-devel-5.9-14.20130511.el7.x86_64                     | ncurses-devel-5.9-14.20130511.el7.x86_64                     | ncurses-devel-5.9-14.20130511.el7.x86_64                     | ncurses-devel-5.9-13.20130511.el7.x86_64                  | ncurses-devel-5.9-14.20130511.el7.x86_64                     |
| tftp-server                                     | tftp-server-5.2-13.el7.x86_64                                | tftp-server-5.2-13.el7.x86_64                                | tftp-server-5.2-13.el7.x86_64                                | tftp-server-5.2-22.el7.x86_64                                | tftp-server-5.2-13.el7.x86_64                             | tftp-server-5.2-13.el7.x86_64                                |
| zlib-devel(also,install 32-bit of this version) | zlib-devel-1.2.7-17.el7.x86_64                               | zlib-devel-1.2.7-17.el7.x86_64  zlib-devel-1.2.7-17.el7.i686 | zlib-devel-1.2.7-17.el7.x86_64                               | zlib-devel-1.2.7-17.el7.x86_64  zlib-devel-1.2.7-17.el7.i686 | zlib-devel-1.2.7-17.el7.x86_64                            | zlib-devel-1.2.7-17.el7.x86_64  zlib-devel-1.2.7-17.el7.i686 |
| zlib-devel-1.2.7-17.el7.i686                    | zlib-devel-1.2.7-17.el7.i686                                 | zlib-devel-1.2.7-17.el7.i686                                 |                                                              |                                                              |                                                           |                                                              |
| openssl-devel                                   | openssl-devel-1.0.2k-8.0.1.el7_3.1.x86_64                    | openssl-devel-1.0.2k-8.0.1.el7_3.1.x86_64                    | openssl-devel-1.0.2k-8.el7_3.1.x86_64                        | openssl-devel-1.0.2k-12.0.1.el7_3.1.x86_64                   | openssl-devel-1.0.1e-60.0.1.el7_3.1.x86_64                | openssl-devel-1.0.2k-12.0.1.el7_3.1.x86_64                   |
| flex                                            | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                                  | flex-2.5.37-3.el7.x86_64                                     |
| bison                                           | bison-3.0.4-1.el7.x86_64                                     | bison-3.0.4-1.el7.x86_64                                     | bison-3.0.4-1.el7.x86_64                                     | bison-3.0.4-1.el7.x86_64                                     |                                                           | bison-3.0.4-1.el7.x86_64                                     |
| libselinux                                      | libselinux-2.5.11.el7.x86_64                                 | libselinux-2.5.11.el7.x86_64                                 | libselinux-2.5.11.el7.x86_64                                 | libselinux-2.5.12.el7.x86_64                                 | libselinux-2.5-6.el7.x86_64                               | libselinux-2.5.12.el7.x86_64                                 |
| gnupg                                           |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| wget                                            | wget-1.14-15.el7_4.1.x86_64                                  | wget-1.14-15.el7_4.1.x86_64                                  | wget-1.14-15.el7_4.1.x86_64                                  | wget-1.14-15.el7_4.1.x86_64                                  | wget-1.14-13.el7.x86_64                                   | wget-1.14-15.el7_4.1.x86_64                                  |
| diffstat                                        | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                                | diffstat-1.57-4.el7.x86_64                                   |
| chrpath                                         | chrpath-0.16-0.el7.x86_64                                    | chrpath-0.16-0.el7.x86_64                                    | chrpath-0.16-0.el7.x86_64                                    | chrpath-0.16-0.el7.x86_64                                    | chrpath-0.13-14.el7.x86_64                                | chrpath-0.16-0.el7.x86_64                                    |
| socat                                           | socat-1.7.3.2-2.el6.x86_64                                   | socat-1.7.3.2-2.el6.x86_64                                   | socat-1.7.3.2-2.el6.x86_64                                   | socat-1.7.3.2-2.el6.x86_64                                   | socat-1.7.2.2-5.el7.x86_64                                | socat-1.7.3.2-2.el6.x86_64                                   |
| xterm                                           | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                                    | xterm-295-3.el7.x86_64                                       |
| autoconf                                        | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                               | autoconf-2.69-11.el7.noarch                                  |
| libtool                                         | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                             | libtool-2.4.2-22.el7_3.x86_64                                |
| tar                                             | tar-1.26-32.el7.x86_64                                       | tar-1.26-32.el7.x86_64                                       | tar-1.26-32.el7.x86_64                                       | tar-1.26-34.el7.x86_64                                       | tar-1.26-31.el7.x86_64                                    | tar-1.26-34.el7.x86_64                                       |
| unzip                                           | unzip-6.0-16.el7.x86_64                                      | unzip-6.0-16.el7.x86_64                                      | unzip-6.0-5.el6.x86_64                                       | unzip-6.0-19.el7.x86_64                                      | unzip-6.0-16.el7.x86_64                                   | unzip-6.0-19.el7.x86_64                                      |
| texinfo                                         | texinfo-5.1-4.el7.x86_64                                     | texinfo-5.1-4.el7.x86_64                                     | texinfo-5.1-4.el7.x86_64                                     | texinfo-5.1-4.el7.x86_64                                     | texinfo-5.1-4.el7.x86_64                                  | texinfo-5.1-5.el7.x86_64                                     |
| zlib1g-dev                                      |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| gcc-multilib                                    |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| build-essential                                 |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| libsdl1.2-dev                                   |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| libglib2.0-dev                                  |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| SDL-devel                                       | SDL-devel-1.2.15-14.el7.i686                                 | SDL-devel-1.2.15-14.el7.i686                                 | SDL-devel-1.2.15-14.el7.i686                                 | SDL-devel-1.2.15-14.el7.i686                                 | SDL-devel-1.2.15-14.el7.i686                              | SDL-devel-1.2.15-14.el7.i686                                 |
| glibc-devel                                     | glibc-devel-2.17-196.el7_4.2.x86_64 glibc-devel-2.17-196.el7_4.2.i686 | glibc-devel-2.17-196.el7_4.2.x86_64                          | glibc-devel-2.17-196.el7_4.2.x86_64 glibc-devel-2.17-196.el7_4.2.i686 | glibc-devel-2.17-222.el7_4.2.x86_64 glibc-devel-2.17-222.el7_4.2.i686 | glibc-devel-2.17-157.el7_3.4.x86_64                       | glibc-devel-2.17-222.el7_4.2.x86_64                          |
| glibc-devel-2.17-196.el7_4.2.i686               | glibc-devel-2.17-157.el7_3.4.i686                            | glibc-devel-2.17-222.el7_4.2.i686                            |                                                              |                                                              |                                                           |                                                              |
| 32-bit glibc                                    | glibc-2.17-196.el7_4.2.i686                                  | glibc-2.17-196.el7_4.2.i686                                  | glibc-2.17-196.el7_4.2.i686                                  | glibc-2.17-222.el7_4.2.x86_64                                | glibc-2.17-157.el7_3.4.x86_64                             | glibc-2.17-222.el7_4.2.x86_64                                |
| glibc-2.17-196.el7_4.2.x86_64                   | glibc-2.17-196.el7_4.2.x86_64                                | glibc-2.17-196.el7_4.2.x86_64                                | glibc-2.17-222.el7_4.2.x86_64                                | glibc-2.17-157.el7_3.4.i686                                  | glibc-2.17-222.el7_4.2.i686                               |                                                              |
| glib2-devel                                     | glib2-devel-2.50.3-3.el7.x86_64                              | glib2-devel-2.50.3-3.el7.x86_64                              | glib2-devel-2.50.3-3.el7.x86_64                              | glib2-devel-2.54.2-2.el7.x86_64                              | glib2-devel-2.46.2-4.el7.x86_64                           | glib2-devel-2.54.2-2.el7.x86_64                              |
| automake                                        | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                              | automake-1.13.4-3.el7.noarch                                 |
| screen                                          | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             | screen-4.1.0-0.25.20120314git3c2946.el7.x86_64               | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64          | screen-4.1.0-0.25.20120314git3c2946.el7.x86_64               |
| pax                                             | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                                     | pax-3.4-19.el7.x86_64                                        |
| gzip                                            | gzip-1.5-9.el7.x86_64                                        | gzip-1.5-9.el7.x86_64                                        | gzip-1.5-9.el7.x86_64                                        | gzip-1.5-10.el7.x86_64                                       | gzip-1.5-8.el7.x86_64                                     | gzip-1.5-9.el7.x86_64                                        |
| libstdc++                                       | libstdc++-4.8.5-11.el7.x86_64                                | libstdc++-4.8.5-16.el7_4.1.x86_64                            | libstdc++-4.8.5-16.el7_4.1.x86_64 libstdc++-4.8.5-16.el7_4.1.i686 | libstdc++-4.8.5-16.el7.x86_64                                | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686 | libstdc++-4.8.5-16.0.1.el7_4.1.i686 libstdc++-4.8.5-28.0.1.el7.x86_64 |
| libstdc++-4.8.5-11.el7.i686                     | libstdc++-4.8.5-16.el7_4.1.i686                              | libstdc++-4.8.5-16.el7.x86_65                                |                                                              |                                                              |                                                           |                                                              |
| g++ (gcc-c++)                                   | gcc-c++-4.8.5-11.el7.x86_64                                  | gcc-c++-4.8.5-16.el7_4.1.x86_64                              | gcc-c++-4.8.5-16.el7_4.1.x86_64                              | gcc-c++-4.8.5-16.el7.x86_64                                  | gcc-c++-4.8.5-11.el7.x86_64                               | gcc-c++-4.8.5-28.0.1.el7.x86_64                              |
| patch                                           | patch-2.7.1.8.el7.x86_64                                     | patch-2.7.1.8.el7.x86_64                                     | patch-2.7.1.8.el7.x86_64                                     | patch-2.7.1.8.el7.x86_64                                     | patch-2.7.1.8.el7.x86_64                                  | patch-2.7.1.8.el7.x86_64                                     |
| zlib                                            | zlib-1.2.7-17.el7.x86_64                                     | zlib-1.2.7-17.el7.x86_64                                     | zlib-1.2.3-29.el6.x86_64                                     | zlib-1.2.7-17.el7.x86_64                                     | zlib-1.2.7-17.el7.x86_64                                  | zlib-1.2.7-17.el7.x86_64                                     |
| zlib-1.2.7-17.el7.i686                          | zlib-1.2.7-17.el7.i686                                       | zlib-1.2.7-17.el7.i686                                       | zlib-1.2.7-17.el7.i686                                       | zlib-1.2.7-17.el7.i686                                       | zlib-1.2.7-17.el7.i686                                    |                                                              |

### Ubuntu

| Tool/Library                                    | Ubuntu 16.04.3 Desktop             | Ubuntu 16.04.03 server             |
| ----------------------------------------------- | ---------------------------------- | ---------------------------------- |
| kernel Version                                  | 4.13.0-32-generic                  | 4.4.0-87-generic                   |
| dos2unix                                        | tofrodos_1.7.13+ds-2.debian.tar.xz | tofrodos_1.7.13+ds-2.debian.tar.xz |
| ip (iproute)                                    | iproute2                           | iproute2                           |
| gawk                                            | gawk                               | gawk                               |
| xvfb                                            | xvfb                               | xvfb                               |
| gcc(for RHEL, use devtoolset-2)                 | gcc 5.4                            | gcc 5.4                            |
| git                                             | git 1.7.1 or above                 | git 1.7.1 or above                 |
| make                                            | make 4.1                           | make 4.1                           |
| netstat (net-tools)                             | net-tools                          | net-tools                          |
| ncurses-devel                                   | libncurses5-dev                    | libncurses5-dev                    |
| tftp-server                                     | tftpd                              | tftpd                              |
| zlib-devel(also,install 32-bit of this version) | i386/zliob1g-2ubuntu4-dev          | i386/zliob1g-2ubuntu4-dev          |
|                                                 |                                    |                                    |
| openssl-devel                                   | libssl-dev                         | libssl-dev                         |
| flex                                            | flex                               | flex                               |
| bison                                           | bison                              | bison                              |
| libselinux                                      | libselinux1                        | libselinux1                        |
| gnupg                                           | gnupg                              | gnupg                              |
| wget                                            | wget                               | wget                               |
| diffstat                                        | diffstat                           | diffstat                           |
| chrpath                                         | chrpath                            | chrpath                            |
| socat                                           | socat                              | socat                              |
| xterm                                           | xterm                              | xterm                              |
| autoconf                                        | autoconf                           | autoconf                           |
| libtool                                         | libtool                            | libtool                            |
| tar                                             | tar1.24                            | tar1.24                            |
| unzip                                           | unzip                              | unzip                              |
| texinfo                                         | texinfo                            | texinfo                            |
| zlib1g-dev                                      | zlib1g-dev                         | zlib1g-dev                         |
| gcc-multilib                                    | gcc-multilib                       | gcc-multilib                       |
| build-essential                                 | build-essential                    | build-essential                    |
| libsdl1.2-dev                                   | libsdl1.2-dev                      | libsdl1.2-dev                      |
| libglib2.0-dev                                  | libglib2.0-dev                     | libglib2.0-dev                     |
| SDL-devel                                       |                                    |                                    |
| glibc-devel                                     |                                    |                                    |
|                                                 |                                    |                                    |
| 32-bit glibc                                    |                                    |                                    |
|                                                 |                                    |                                    |
| glib2-devel                                     |                                    |                                    |
| automake                                        |                                    |                                    |
| screen                                          | screen                             | screen                             |
| pax                                             | pax                                | pax                                |
| gzip                                            | gzip                               | gzip                               |
| libstdc++                                       |                                    |                                    |
|                                                 |                                    |                                    |
| g++ (gcc-c++)                                   |                                    |                                    |
| patch                                           |                                    |                                    |
| zlib                                            |                                    |                                    |
|                                                 |                                    |                                    |