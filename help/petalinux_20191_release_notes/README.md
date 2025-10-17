# 72293 - PetaLinux 2019.1 - Product Update Release Notes and Known Issues

## Title

72293 - PetaLinux 2019.1 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2019.1 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for the 2019.1 PetaLinux Release**

This table contains supported BSPs for Zynq-7000, MicroBlaze, and Zynq UltraScale+ MPSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

**Note:** XY - Represents release year, Y - Represents release version.

| Platform                   | Variant                   | BSP Name                                  | BSP Description                                              |
| -------------------------- | ------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| **MicroBlaze**             | AC701                     | xilinx-ac701-v20XY.Z-final.bsp            | This BSP contains two BSPs [AC701 lite, AC701 full].<br>**Hardware (AC701 lite):** Design contains MicroBlaze Processor, core peripherals UART_lite, Ethernet Lite, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br>AC701 lite contains the AXI Lite IPs UART_lite, Ethernet Lite etc. in contrast to AC701 Full.<br>**Hardware (AC701 full):** Design contains MicroBlaze Processor, core peripherals AXI UART16550, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | KC705                     | xilinx-kc705-v20XY.Z-final.bsp            | This BSP contains two BSPs [KC705 lite, KC705 full].<br>**Hardware (KC705 lite):** Design contains MicroBlaze Processor, core peripherals UART_lite, Ethernet Lite, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br>**Hardware (KC705 full):** Design contains MicroBlaze Processor, core peripherals AXI UART16550, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | KCU105                    | xilinx-kcu105-v20XY.Z-final.bsp           | **Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | SP701                     | xilinx-sp701-v20XY.Z-final.bsp            | **Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | VCU118                    | xilinx-vcu118-v20XY.Z-final.bsp           | **Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq-7000**              | ZC702                     | xilinx-zc702-v20XY.Z-final.bsp            | **Hardware:** Design contains Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_4bits.<br>**Software:** FSBL, U-boot, Linux, device-tree (includes OpenAMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq-7000**              | ZC706                     | xilinx-zc706-v20XY.Z-final.bsp            | **Hardware:** Design contains Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_4bits, dip_switches_4bits, gpio_sws_3bits.<br>**Software:** FSBL, U-boot, Linux, device-tree (includes OpenAMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq-7000**              | Avnet Digilent Zedboard   | avnet-digilent-zedboard-v20XY.Z-final.bsp | **Hardware:** Design contains Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_8bits, btns_5bits, sws_8bits.<br>**Software:** FSBL, U-boot, Linux, device-tree (includes OpenAMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | ZCU102 production silicon | xilinx-zcu102-v20XY.Z-final.bsp           | **Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.)<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes OpenAMP, Xen), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | ZCU104 production silicon | xilinx-zcu104-v20XY.Z-final.bsp           | **Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes OpenAMP, Xen), vcu-control software, rootfs (minimal packages including additional SW packages like GStreamer, OpenMAX, V4L2, libdrm and vcu-examples).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | ZCU106 production silicon | xilinx-zcu106-v20XY.Z-final.bsp           | **Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes OpenAMP, Xen), vcu-control software, rootfs (minimal packages including additional SW packages like GStreamer, OpenMAX, V4L2, libdrm and vcu-examples).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ RFSoC** | ZCU111 production silicon | xilinx-zcu111-v20XY.Z-final.bsp           | **Hardware:** Design contains Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.) and rf_data_converters, sd_fec_dec, adc_sink, dac_source, axi_gpio, axi_intc IPs.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes OpenAMP, Xen), rfdc-drivers, rootfs (minimal packages including RDFC example applications).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ RFSoC** | ZCU1275                   | xilinx-zcu1275-v20XY.Z-final.bsp          | **Hardware:** Design contains Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.) and rf_data_converters, adc_sink, dac_source, axi_gpio, axi_intc IPs.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes OpenAMP, Xen), rfdc-drivers, rootfs (minimal packages including RDFC example applications).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ RFSoC** | ZCU1285                   | xilinx-zcu1285-v20XY.Z-final.bsp          | **Hardware:** Design contains Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.) and rf_data_converters, adc_sink, dac_source, axi_gpio, axi_intc IPs.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes OpenAMP, Xen), rfdc-drivers, rootfs (minimal packages including RDFC example applications).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs for booting u-boot and Linux. |

**Note**: The "[sstate cache file](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate-rel-v2019.1.tar.gz)" (sstate-rel-v2019.1.tar.gz) can be found on the Xilinx download area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2019.1_README.tar.gz) (sstate\_rel\_2019.1\_README) file that outlines the procedure to use "sstate cache".

Refer to the attached file "2019.1\_PetaLinux\_Packages\_List" for software package versions tested on host machines, which is required for PetaLinux installation tools.

See also the attached README.

**PetaLinux 2019.1 contains the following build collateral:**

| Component                      | Git repo                                                     | Git Branches          | Git Tags                 | Commit ID                                                    | Comments                                                     |
| ------------------------------ | ------------------------------------------------------------ | --------------------- | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **FSBL**                       | git://github.com/Xilinx/embeddedsw.git                       | release-2019.1        | xilinx-v2019.1           | 26c14d9861010a0e3a55c73fb79efdb816eb42ca                     | FSBL for Zynq-7000 is at `embeddedsw/lib/sw_apps/zynq_fsbl`.<br>FSBL for Zynq UltraScale+ is at `embeddedsw/lib/sw_apps/zynqmp_fsbl`. |
| **PMU Firmware**               | git://github.com/Xilinx/embeddedsw.git                       | release-2019.1        | xilinx-v2019.1           | 26c14d9861010a0e3a55c73fb79efdb816eb42ca                     | PMU for Zynq UltraScale+ Firmware is at `embeddedsw/lib/sw-apps/zynqmp_pmufw`. |
| **Device-tree**                | git://github.com/Xilinx/device-tree-xlnx.git                 | master                | xilinx-v2019.1           | 73e546e312a22d7fb410c28d5c79174d2eb29938                     |                                                              |
| **Linux**                      | git://github.com/Xilinx/linux-xlnx.git                       | xlnx_rebase_v4.19     | xlnx_rebase_v4.19_2019.1 | 9811303824b66a8db9a8ec61b570879336a9fde5                     | Linux Kernel rebase version 4.19.                            |
| **U-Boot**                     | git://github.com/Xilinx/u-boot-xlnx.git                      | master                | xilinx-v2019.1           | d895ac5e94815d4b45dcf09d4752c5c2334a51db                     | U-Boot Version v2019.01.                                     |
| **QEMU**                       | git://github.com/Xilinx/qemu.git                             | master                | xilinx-v2019.1           | 5f38ea92fb697b94ad43f01fe162f3ed6e6b0e16                     |                                                              |
| **Xen**                        | git://github.com/Xilinx/xen.git                              | xilinx/release-2019.1 | xilinx-v2019.1           | e4547c663f7fc36fa90d0ee2c344624e5dbe2033                     | Xen Version 4.14.                                            |
| **ARM-Trusted-Firmware (ATF)** | git://github.com/Xilinx/arm-trusted-firmware.git             | master                | xilinx-v2019.1           | 80d1c79007fda42d4cc0be31b185a1da5799cd4d                     | ATF is based on upstream version 2.0.                        |
| **Yocto**                      | git://github.com/Xilinx/meta-xilinx.git<br>git://github.com/Xilinx/meta-xilinx-tools.git<br>git://github.com/Xilinx/meta-petalinux.git | rel-v2019.1           | No Tags                  | 94add75c0447ff7eb5b67cee0712777e198e9c5b<br>de93eacef30a578ab030964ceb95f1f7b6b79a74<br>de2b260c646dabbe4de3d3419cbc0878f57091c7 | Yocto 2.6.1 Thud.                                            |
| **qemu-devicetrees**           | git://github.com/Xilinx/qemu-devicetrees.git                 | branch/xilinx-v2019.1 | xilinx-v2019.1           | 445406ef4d06303f00387f7d81e8718255336fd0                     |                                                              |
| **OpenAMP**                    | git://github.com/Xilinx/open-amp.git                         | master                | xilinx-v2019.1           | f9039c27a00caa7f1548ffd53d863776edc6f223                     |                                                              |
| **libmetal**                   | git://github.com/Xilinx/libmetal.git                         | master                | xilinx-v2019.1           | a4d606a40535c8be029d01315303c2608359d789                     |                                                              |
| **VCU OpenMax IL**             | git://github.com/Xilinx/vcu-omx-il.git                       | master                | xilinx-v2019.1           | b93cec02cd5da223fa965073dce130a08ffd6419                     |                                                              |
| **VCU Control Software**       | git://github.com/Xilinx/vcu-ctrl-sw.git                      | master                | xilinx-v2019.1           | 32b7be620987283f62e4469185da81dddad1071c                     |                                                              |
| **VCU Firmware**               | git://github.com/Xilinx/vcu-firmware.git                     | master                | xilinx-v2019.1           | 4078b74d16e5eccca5ae3132c3877d3aff7fb168                     |                                                              |
| **VCU Modules**                | git://github.com/Xilinx/vcu-modules.git                      | master                | xilinx-v2019.1           | 13a8e5b3f614d94081481a808aa8d4bd00b26d76                     |                                                              |
| **GStreamer OpenMax IL**       | git://github.com/Xilinx/gst-omx.git                          | xilinx-master         | xilinx-v2019.1           | b2aa6a8a5e30d347d573378cf8968a127e2bd495                     | GStreamer version 1.14.4.                                    |
| **GStreamer Plugins-Base**     | git://github.com/Xilinx/gst-plugins-base.git                 | master-rel-1.12.2     | xilinx-v2019.1           | 334c48fb4ad71ba95502a68cb31f505d85b10b2d                     |                                                              |
| **GStreamer Plugins-Bad**      | git://github.com/Xilinx/gst-plugins-bad.git                  | master-rel-1.12.2     | xilinx-v2019.1           | ec1ff1219c99db2a9cc5262027f9b4d20f5f4e81                     |                                                              |
| **GStreamer Plugins-Good**     | git://github.com/Xilinx/gst-plugins-good.git                 | master-rel-1.12.2     | xilinx-v2019.1           | 265c66765515d09a578c401cdcb70327239b1b3d                     |                                                              |
| **GStreamer**                  | git://github.com/Xilinx/gstreamer.git                        | rel-v2019.1           | No Tags                  | 791c729f72cf91679bbfa36c24b1c7da5c332808                     |                                                              |
| **hdmi-modules**               | git://github.com/Xilinx/hdmi-modules.git                     | master                | xilinx-v2019.1           | 44d691f6937ad73ac974ed5b50722e73514459f6                     |                                                              |
| **GCC**                        |                                                              |                       |                          |                                                              | MB compiler version 8.2.<br>ARM 8.2.                         |

**2019.1 Release Notes for Open Source components wiki page:**

Covers details for below components changes (new features/fixes) in a particular release.

https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/134054004/2019.1+Release+Notes+for+Open+Source+Components

**2019.1 New Features:**

**PetaLinux**

-   PetaLinux upgraded to Yocto 2.6.1 Thud release.
-   PetaLinux BSP's for
    1.  MicroBlaze SP701 board
    2.  MicroBlaze VCU118 Rev2.0 production silicon
    3.  Zynq UltraScale+ RFSoC ZCU1275 Rev 2.0 production silicon
    4.  Zynq UltraScale+ RFSoC ZCU1285 Rev 2.0 pre-production silicon
-   Added support for device tree overlay support for Zynq7000 devices
-   PetaLinux Upgrade support in tool where you can upgrade a PetaLinux project to a new version of the components like U-boot, Linux, OpenAMP, Xen, DTG and Rootfs

**GPU MALI-400**

-   Added a variable to toggle different backend has been decoupled from DISTRO\_FEATURES. A new variable "MALI\_BACKEND\_DEFAULT" is used to select backend.  
    For example If fbdev backend is required then add MALI\_BACKEND\_DEFAULT ="fbdev" to petalinuxbsp.conf (PetaLinux) or local.conf (Yocto)
-   Users can now toggle libMali backend at runtime using update-alternatives.  
    For more details refer [https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/18841928/Xilinx+MALI+driver](https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/18841928/Xilinx+MALI+driver)

**2019.1 Bug Fixes:**

**PetaLinux**

-   PetaLinux host packages docs matches with Yocto Thud release docs
-   Fixed device-tree MicroBlaze processor errors even though the processor is present hardware design
-   Fixed ARM Trusted Firmware hangs on Zynq MPSoC when UART0 is disabled
-   Fixed incorrect MicroBlaze lite locked signs (SIGGEN\_LOCKEDSIGS\_TYPES)
-   Fixed DT Overlays enabled doesn't copy pl.dtbo to <plnx-proj-root>/images/linux directory
-   Fixed for enabling DT Overlays in PetaLinux generates in correct bitstream name in <plnx-proj-root>/images/linux directory
-   Fixed application name using "system-<NAME>" not included petalinux-user-image_._bb even though it is enabled from rootfs menu config

**GPU MALI-400**

-   Fixed ARM Mali 400 Support download bundle name changed in [MALI download](https://www.xilinx.com/products/design-tools/embedded-software/petalinux-sdk/arm-mali-400-software-download.html) page.
-   Work-around fix for fatal errors when you enable MALI and X11, see [(Xilinx Answer 72363)](https://adaptivesupport.amd.com/s/article/72363)

**Known Issues for 2019.1:**

| Linux/Baremetal | Components       | Description                                                  | Work-around           | To be fixed version |
| --------------- | ---------------- | ------------------------------------------------------------ | --------------------- | ------------------- |
| Linux           | PetaLinux        | Zynq UltraScale+ MPSoC: How to enable UHS (SD 3.0) support for ZCU102 and ZCU106 evaluation board PetaLinux BSPs | (Xilinx Answer 69978) |                     |
| Linux           | XSDK             | Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle    | (Xilinx Answer 69143) |                     |
| Linux           | FSBL             | Zynq UltraScale+ MPSoC: How to achieve SATA performance in Linux | (Xilinx Answer 71584) |                     |
| Linux           | FSBL             | Zynq UltraScale+ MPSoC: How to make SMMU work with SATA IP   | (Xilinx Answer 71790) |                     |
| Linux           | Yocto, PetaLinux | 2019.x Zynq UltraScale+ MPSoC: Yocto or PetaLinux throws warnings when you enable libmali with fbdev windowing system | (Xilinx Answer 72139) |                     |
| Linux           | Yocto, PetaLinux | 2019.x Zynq UltraScale+ MPSoC: Linux boot throws fatal errors with libmali and X11 enabled in PetaLinux or Yocto images | (Xilinx Answer 72363) |                     |
| Linux           | Kernel           | 2019.x Zynq7000, Zynq UltraScale+ MPSoC: Yocto or PetaLinux build with petalinux-image-full images hangs without reaching Linux boot login prompt | (Xilinx Answer 72377) |                     |
| Baremetal       | LwIP             | 2019.1 Zynq UltraScale+ MPSoC: LwIP Support for A53 32-bit Toolchain | (Xilinx Answer 72379) |                     |
| Linux           | U-boot           | 2017.1-2019.1 Zynq-7000: Cannot boot Zynq-7000 PetaLinux images individually in legacy flow | (Xilinx Answer 71231) | 2019.2              |
| Linux           | Drivers          | 2019.1 Zynq UltraScale+ MPSoC: USB 3.0 getting missed Interval for Isochronous transfers when operating in Super-Speed Mode | (Xilinx Answer 72290) | 2019.2              |
| Linux           | Drivers          | 2018.3-2019.1 Zynq UltraScale+ MPSoC: Linux stress test on mtd-device fails | (Xilinx Answer 72327) | 2019.2              |
| Linux           | PMUFW            | 2019.1 Zynq UltraScale+ MPSoC: Linux APU-Only restart fails on Ultra96 boards | (Xilinx Answer 72336) | 2019.2              |
| Linux           | Drivers          | 2018.3-2019.1 Zynq UltraScale+ MPSoC: Unable to mount JFFS2 filesystem with single flash configuration | (Xilinx Answer 72349) | 2019.2              |
| Linux           | Driver           | 2019.1 MicroBlaze: EEPROM does not work in VCU118 and SP701 PetaLinux BSP's | (Xilinx Answer 72380) | 2019.2              |
| Linux           | U-boot           | 2018.x-2019.1 Zynq UltraScale+ MPSoC: USB core reset in Linux may cause issues with USB device connected if it was previously powered in U-boot | (Xilinx Answer 72376) | 2019.2              |
| Baremetal       | BSP              | 2019.1 MicroBlaze standalone BSP does not have a handler for unaligned access to 64 bit addresses exceptions | (Xilinx Answer 72398) | 2019.2              |
| Linux           | VCU, GStreamer   | 2019.1 Zynq UltraScale+ MPSoC VCU - Why is there initial "jerkiness" when transcoding with a 4Kp60 AVC pipeline? | (Xilinx Answer 72328) | 2019.2              |
| Linux           | Yocto, PetaLinux | 2019.1 Zynq UltraScale+ MPSoC: Yocto or PetaLinux doesn't support distrocmd introduced in u-boot-xlnx | (Xilinx Answer 72393) | 2019.2              |
| Linux           | Device-tree      | 2019.1 Zynq UltraScale+ MPSoC: U-boot fails to read MAC address from EEPROM on ZCU102 board | (Xilinx Answer 72401) | 2019.2              |
| Linux           | Yocto            | 2019.1 Zynq UltraScale+ MPSoC: Yocto XRT and ZOCL commit IDs are out of sync | (Xilinx Answer 72400) | 2019.2              |
| Linux           | Drivers          | 2019.1 MicroBlaze: Linux AXI Ethernet driver probe fails when using VCU118 PetaLinux BSPs | (Xilinx Answer 72396) | 2019.2              |
| Linux           | Drivers          | Zynq UltraScale+ MPSoC (Vivado 2019.1) - PL-PCIe Root Port - Driver Compilation Fails | (Xilinx Answer 72389) | 2019.2              |
| Linux           | U-boot           | 2019.1 Zynq UltraScale+ MPSoC: Linux USB 3.0 device mode doesn't work | (Xilinx Answer 72409) | 2019.2              |
| Linux           | VCU              | 2018.3-2019.1 Zynq UltraScale+ MPSoC VCU - Why do I sometimes see heavy APU loading for high bitrate encoding? | (Xilinx Answer 72460) | 2019.2              |
| Linux           | Libmetal         | 2019.1 Zynq UltraScale+ MPSoC: Why does my OpenAMP libmetal C++ application not build | (Xilinx Answer 72561) | 2019.2              |
| Linux           | VCU, GStreamer   | 2019.1 Zynq UltraScale+ MPSoC VCU - Why do I see frame drops or Block Noise for some Use Case 2 (UC2) use cases when PL-DDR is being used? | (Xilinx Answer 72325) |                     |
| Linux           | VCU, GStreamer   | 2019.1 Zynq UltraScale+ MPSoC VCU - Why do I get an Out of Memory error when encoding two 4Kp30 HEVC Streams over a long period of time and using the Use Case 2 (UC2) with PL-DDR? | (Xilinx Answer 72329) | 2019.2              |
| Linux           | VCU              | 2019.1 Zynq UltraScale+ MPSoC VCU - Why do I see the Zynq UltraScale+ MPSoC VCU Encoder HEVC EnableSkip settings cause encoding to stall after the 600th frame? | (Xilinx Answer 72605) | 2019.2              |
| Linux           | VCU              | 2019.1 Zynq UltraScale+ MPSoC VCU - Why do I see the Zynq UltraScale+ MPSoC VCU Decoder fail with GET_DMA_PHY: Invalid argument when trying to decode a 1280x960 H.265 stream? | (Xilinx Answer 72732) | 2019.2              |
| Linux           | VCU              | 2019.1 Zynq UltraScale+ MPSoC VCU - Why do I occasionally see Zynq UltraScale+ MPSoC VCU OMX Encoder crashes when transitioning out of the recording state? | (Xilinx Answer 72734) | 2019.2              |
| Linux           | VCU              | 2019.1 Zynq UltraScale+ MPSoC VCU - Why does the VCU Decoder crash when trying to decode two reduced latency streams? | (Xilinx Answer 72958) | 2019.2              |

# 2019.1_PetaLinux_Package_List

## Linux Distribution OS details:

1. RHEL Server:  Infrastructure Server
2. RHEL Workstation : Development and Creative workstation.
3. CentOS Server (From Everything.ISO): Infrastructure server.
4. CentOS Workstation (From Everything.ISO): Development and Creative workstation.
5. Ubuntu 16.04.05 and 18.04.1 Desktop.
6. Ubuntu 16.04.05 and 18.04.1 Server.

### Note: 

1. Empty packages are not installed means assuming these are default from Linux Distribution.

## Tool/Library Versions

### RHEL/CentOS versions

| Library/Package | CentOS 7.4 (workstation)                     | CentOS 7.4 (server)                              | CentOS 7.5 (workstation)                                     | CentOS 7.5 (server)                              | CentOS 7.6 (workstation)             | CentOS 7.6 (server)                              | RHEL 7.4 (workstation)                       | RHEL 7.4 (server)                                | RHEL 7.6 (workstation)                       | RHEL 7.6 (Server)                                | RHEL 7.5 (workstation)                   | RHEL 7.5 (server)                                |
| --------------- | -------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------ | ------------------------------------------------ | -------------------------------------------- | ------------------------------------------------ | -------------------------------------------- | ------------------------------------------------ | ---------------------------------------- | ------------------------------------------------ |
| dos2unix        | dos2unix                                     | dos2unix                                         | dos2unix                                                     | dos2unix                                         | dos2unix                             | dos2unix                                         | dos2unix                                     | dos2unix                                         | dos2unix                                     | dos2unix                                         | dos2unix                                 | dos2unix                                         |
| ip              | iproute                                      | iproute                                          | iproute                                                      | iproute                                          | iproute                              | iproute                                          | iproute                                      | iproute                                          | iproute                                      | iproute                                          | iproute                                  | iproute                                          |
| gawk            | gawk                                         | gawk                                             | gawk                                                         | gawk                                             | gawk                                 | gawk                                             | gawk                                         | gawk                                             | gawk                                         | gawk                                             | gawk                                     | gawk                                             |
| gcc             | gcc.x86_64 0:4.8.5-28.el7_5.1                | gcc.x86_64 0:4.8.5-28.el7_5.1                    | gcc.x86_64 0:4.8.5-36.0.1.el7                                | gcc.x86_64 0:4.8.5-28.el7_5.1                    | gcc-4.8.5-36.0.1.el7_6.2.x86_64      | gcc-4.8.5-36.0.1.el7_6.2.x86_64                  | gcc.x86_64 0:4.8.5-36.0.1.el7                | gcc.x86_64 0:4.8.5-36.0.1.el7                    | gcc.x86_64 0:4.8.5-36.0.1.el7                | gcc.x86_64 0:4.8.5-36.0.1.el7                    | gcc.x86_64 0:4.8.5-36.0.1.el7            | gcc.x86_64 0:4.8.5-36.0.1.el7                    |
| g++             | g++                                          | g++                                              | g++                                                          | g++                                              | g++                                  | g++                                              | g++                                          | g++                                              | g++                                          | g++                                              | g++                                      | g++                                              |
| make            | make                                         | make                                             | make                                                         | make                                             | make                                 | make                                             | make                                         | make                                             | make                                         | make                                             | make                                     | make                                             |
| ncurses devel   | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4 | ncurses-devel-5.9-14.20130511.el7_4              | ncurses-devel-5.9-14.20130511.el7_4                          | ncurses-devel-5.9-14.20130511.el7_4              | ncurses-devel-5.9-14.20130511.el7_5  | ncurses-devel-5.9-14.20130511.el7_6              | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4 | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4     | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4 | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4     | ncurses-devel-5.9-14.20130511.el7_4      | ncurses-devel-5.9-14.20130511.el7_4              |
| tftp server     | tftp-server                                  | tftp-server                                      | tftp-server                                                  | tftp-server                                      |                                      |                                                  | tftp-server                                  | tftp-server                                      | tftp-server                                  | tftp-server                                      | tftp-server                              | tftp-server                                      |
| openssl devel   | openssl-devel.x86_64 1:1.0.2k-12.el7         | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         | openssl-devel.x86_64 1:1.0.2k-12.0.3.el7                     | openssl-devel.x86_64 1:1.0.2k-12.el7             | openssl-devel.x86_64 1:1.0.2k-16.el7 | openssl-devel.x86_64 1:1.0.2k-16.el7             | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7     | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7     | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7 | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         |
| zlib devel      | zlib-devel.x86_64 0:1.2.7-17.el7             | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7                             | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7     | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-18.el7             | zlib-devel.x86_64 0:1.2.7-18.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7             | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7         | zlib-devel.x86_64 0:1.2.7-17.el7                 |
| flex            | flex                                         | flex                                             | flex                                                         | flex                                             | flex                                 | flex                                             | flex                                         | flex                                             | flex                                         | flex                                             | flex                                     | flex                                             |
| bison           | bison                                        | bison                                            | bison                                                        | bison                                            | bison                                | bison                                            | bison                                        | bison                                            | bison                                        | bison                                            | bison                                    | bison                                            |
| libselinux      | libselinux                                   | libselinux                                       | libselinux                                                   | libselinux                                       | libselinux                           | libselinux                                       | libselinux                                   | libselinux                                       | libselinux                                   | libselinux                                       | libselinux                               | libselinux                                       |
| gnupg           | gnupg                                        | gnupg                                            | gnupg                                                        | gnupg                                            | gnupg                                | gnupg                                            | gnupg                                        | gnupg                                            | gnupg                                        | gnupg                                            | gnupg                                    | gnupg                                            |
| wget            | wget                                         | wget                                             | wget                                                         | wget                                             | wget                                 | wget                                             | wget                                         | wget                                             | wget                                         | wget                                             | wget                                     | wget                                             |
| diffstat        | diffstat.x86_64 0:1.57-4.el7                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7                                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el8         | diffstat.x86_64 0:1.57-4.el9                     | diffstat.x86_64 0:1.57-4.el7                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7             | diffstat.x86_64 0:1.57-4.el7                     |
| chrpath         | chrpath.x86_64 0:0.16-0.el7                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7                                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el8          | chrpath.x86_64 0:0.16-0.el9                      | chrpath.x86_64 0:0.16-0.el7                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7              | chrpath.x86_64 0:0.16-0.el7                      |
| socat           | socat.x86_64 0:1.7.3.2-2.el7                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7                                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el8         | socat.x86_64 0:1.7.3.2-2.el9                     | socat.x86_64 0:1.7.3.2-2.el7                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7             | socat.x86_64 0:1.7.3.2-2.el7                     |
| xterm           | xterm.x86_64 0:295-3.el7                     | xterm.x86_64 0:295-3.el7                         | xterm.x86_64 0:295-3.el7                                     | xterm.x86_64 0:295-3.el7                         | xterm.x86_64 0:295-3.el8             | xterm.x86_64 0:295-3.el9                         | xterm.x86_64 0:295-3.el7                     | xterm.x86_64 0:295-3.el7                         | xterm.x86_64 0:295-3.el7                     |                                                  | xterm.x86_64 0:295-3.el7                 | xterm.x86_64 0:295-3.el7                         |
| libtool         | libtool.x86_64 0:2.4.2-22.el7_3              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3                              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_4      | libtool.x86_64 0:2.4.2-22.el7_5                  | libtool.x86_64 0:2.4.2-22.el7_3              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3          | libtool.x86_64 0:2.4.2-22.el7_3                  |
| autoconf        | autoconf.noarch 0:2.69-11.el7                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7                                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el8        | autoconf.noarch 0:2.69-11.el9                    | autoconf.noarch 0:2.69-11.el7                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7            | autoconf.noarch 0:2.69-11.el7                    |
| unzip           | unzip                                        | unzip                                            | unzip                                                        | unzip                                            | unzip                                | unzip                                            | unzip                                        | unzip                                            | unzip                                        | unzip                                            | unzip                                    | unzip                                            |
| texinfo         | texinfo.x86_64 0:5.1-5.el7                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7                                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el8           | texinfo.x86_64 0:5.1-5.el9                       | texinfo.x86_64 0:5.1-5.el7                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7               | texinfo.x86_64 0:5.1-5.el7                       |
| zlib1g-dev      |                                              |                                                  |                                                              |                                                  |                                      |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |
| gzip            | gzip                                         | gzip                                             | gzip                                                         | gzip                                             | gzip                                 | gzip                                             | gzip                                         | gzip                                             | gzip                                         | gzip                                             | gzip                                     | gzip                                             |
| libsdl1.2-dev   |                                              |                                                  |                                                              |                                                  |                                      |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |
| automake        | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                     | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7                            | automake-1.13.4-3.el8                | automake-1.13.4-3.el9                            | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                     | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                     | automake-1.13.4-3.el7.noarch             | automake-1.13.4-3.el7.noarch                     |
| libglib2.0-dev  | glib2-devel.x86_64 0:2.54.2-2.el7            | glib2-devel.x86_64 0:2.54.2-2.el7                | glib2-devel.x86_64 0:2.54.2-2.el7 or glib2-devel.x86_64 0:2.56.1-2.el7 | glib2-devel.x86_64 0:2.54.2-2.el7                | glib2-devel.x86_64 0:2.56.1-2.el7    | glib2-devel.x86_64 0:2.56.1-2.el7                | glib2-devel.x86_64 0:2.54.2-2.el7            | glib2-devel.x86_64 0:2.56.1-2.el7                | glib2-devel.x86_64 0:2.56.1-2.el7            | glib2-devel.x86_64 0:2.56.1-2.el7                | glib2-devel.x86_64 0:2.56.1-2.el7        | glib2-devel.x86_64 0:2.56.1-2.el7                |
| pax             | pax                                          | pax                                              | pax                                                          | pax                                              | pax                                  | pax                                              | pax                                          | pax                                              | pax                                          | pax                                              | pax                                      | pax                                              |
| patch           | patch.x86_64 0:2.7.1-10.el7_5                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5                                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_6        | patch.x86_64 0:2.7.1-10.el7_7                    | patch.x86_64 0:2.7.1-10.el7_5                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5            | patch.x86_64 0:2.7.1-10.el7_5                    |
| gcc-c++         | gcc-c++.x86_64 0:4.8.5-28.el7_5.1            | gcc-c++.x86_64 0:4.8.5-28.el7_5.1                | gcc-c++.x86_64 0:4.8.5-28.0.1.el7_5.1 or gcc-c++.x86_64 0:4.8.5-36.0.1.el7 | gcc-c++.x86_64 0:4.8.5-28.el7_5.1                | gcc-c++.x86_64 0:4.8.5-36.0.1.el7    | gcc-c++.x86_64 0:4.8.5-36.0.1.el7                | gcc-c++.x86_64 0:4.8.5-36.0.1.el7            | gcc-c++.x86_64 0:4.8.5-36.0.1.el7                | gcc-c++.x86_64 0:4.8.5-36.0.1.el7            | gcc-c++.x86_64 0:4.8.5-36.0.1.el7                | gcc-c++.x86_64 0:4.8.5-36.0.1.el7        | gcc-c++.x86_64 0:4.8.5-36.0.1.el7                |
| screen          |                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                      | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                          | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |
| build-essential |                                              |                                                  |                                                              |                                                  |                                      |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |
| gcc-multilib    |                                              |                                                  |                                                              |                                                  |                                      |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |
| libglib2.0-dev  |                                              |                                                  |                                                              |                                                  |                                      |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |
| python2         |                                              |                                                  |                                                              |                                                  |                                      |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |

### Ubuntu

| Library/Package | Ubuntu 16.04.5 (workstation) | Ubuntu 16.04.5 (server) | Ubuntu 18.04.1 (workstation) | Ubuntu 18.04.1 (server) |
| --------------- | ---------------------------- | ----------------------- | ---------------------------- | ----------------------- |
| dos2unix        | dos2unix                     | dos2unix                | dos2unix                     | dos2unix                |
| ip              | iproute                      | iproute                 | iproute                      | iproute                 |
| gawk            | gawk                         | gawk                    | gawk                         | gawk                    |
| gcc             | gcc                          | gcc                     | gcc                          | gcc                     |
| g++             | g++                          | g++                     | g++                          | g++                     |
| make            | make                         | make                    | make                         | make                    |
| ncurses devel   | ncurses-devel                | libncurses-dev          | libncurses-dev               | libncurses-dev          |
| tftp server     | tftp-server                  | tftp-server             | tftp-server                  | tftp-server             |
| openssl devel   | openssl-devel                | openssl                 | openssl                      | openssl                 |
| zlib devel      | zlib-devel                   | zlib-devel              | zlib-devel                   | zlib-devel              |
| flex            | flex                         | flex                    | flex                         | flex                    |
| bison           | bison                        | bison                   | bison                        | bison                   |
| libselinux      | libselinux                   | libselinux              | libselinux                   | libselinux              |
| gnupg           | gnupg                        | gnupg                   | gnupg                        | gnupg                   |
| wget            | wget                         | wget                    | wget                         | wget                    |
| diffstat        | diffstat                     | diffstat                | diffstat                     | diffstat                |
| chrpath         | chrpath                      | chrpath                 | chrpath                      | chrpath                 |
| socat           | socat                        | socat                   | socat                        | socat                   |
| xterm           | xterm                        | xterm                   | xterm                        | xterm                   |
| libtool         | libtool                      | libtool                 | libtool                      | libtool                 |
| autoconf        | autoconf                     | autoconf                | autoconf                     | autoconf                |
| unzip           | unzip                        | unzip                   | unzip                        | unzip                   |
| texinfo         | texinfo                      | unzip                   | texinfo                      | texinfo                 |
| zlib1g-dev      |                              | zlib1g-dev              | zlib1g-dev                   | zlib1g-dev              |
| gzip            | gzip                         | gzip                    | gzip                         | gzip                    |
| libsdl1.2-dev   |                              | libsdl1.2-dev           | libsdl1.2-dev                | libsdl1.2-dev           |
| automake        | automake                     | automake                | automake                     | automake                |
| libglib2.0-dev  | libglib2.0-dev               | glib2-devel             | libglib2.0-dev               | libglib2.0-dev          |
| pax             | pax                          | pax                     | pax                          | pax                     |
| patch           | patch                        | patch                   | patch                        | patch                   |
| gcc-c++         | gcc-c++                      | gcc-c++                 | gcc-c++                      | gcc-c++                 |
| screen          | screen                       | screen                  | screen                       | screen                  |
| build-essential | build-essential              | build-essential         | build-essential              | build-essential         |
| gcc-multilib    | gcc-multilib                 | gcc-multilib            | gcc-multilib                 | gcc-multilib            |
| libglib2.0-dev  | libglib2.0-dev               | libglib2.0-dev          | libglib2.0-dev               | libglib2.0-dev          |
| python2         |                              |                         |                              | python2                 |

# README_content_v2019.1

=============================

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2019.1 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2018.3 Open Components Source Code (TAR/GZIP) file: 
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