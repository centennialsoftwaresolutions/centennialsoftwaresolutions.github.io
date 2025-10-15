# 73686 - PetaLinux 2020.1 - Product Update Release Notes and Known Issues

## Title

73686 - PetaLinux 2020.1 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2020.1 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for the 2020.1 PetaLinux Release**

This table contains supported BSPs for Zynq-7000, MicroBlaze, and Zynq UltraScale+ MPSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

**Note:** XY - Represents release year, Y - Represents release version.

| Platform                   | Variant                         | BSP Name                                  | BSP Description                                              |
| -------------------------- | ------------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| **MicroBlaze**             | **AC701**                       | xilinx-ac701-v20XY.Z-final.bsp            | This BSP contains two BSPs [AC701 lite, AC701 full].<br>**Hardware (AC701 lite):** Design contains MicroBlaze Processor, core peripherals UART_lite, Ethernet Lite, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits. AC701 lite contains the AXI Lite IPs UART_lite, Ethernet Lite etc. in contrast to AC701 Full.<br>**Hardware (AC701 full):** Design contains MicroBlaze Processor, core peripherals AXI UART16550, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | **KC705**                       | xilinx-kc705-v20XY.Z-final.bsp            | This BSP contains two BSPs [KC705 lite, KC705 full].<br>**Hardware (KC705 lite):** Design contains MicroBlaze Processor, core peripherals UART_lite, Ethernet Lite, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br>**Hardware (KC705 full):** Design contains MicroBlaze Processor, core peripherals AXI UART16550, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs. |
| **MicroBlaze**             | **KCU105**                      | xilinx-kcu105-v20XY.Z-final.bsp           | **Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test bitstream, fs-boot, u-boot, Linux and rootfs. |
| **MicroBlaze**             | **SP701**                       | xilinx-sp701-v20XY.Z-final.bsp            | **Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs. |
| **MicroBlaze**             | **VCU118**                      | xilinx-vcu118-v20XY.Z-final.bsp           | **Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs. |
| **Zynq-7000**              | **ZC702**                       | xilinx-zc702-v20XY.Z-final.bsp            | **Hardware:** Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO with led_4bits.<br>**Software:** FSBL, U-boot, Linux, device-tree (includes Open AMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs. |
| **Zynq-7000**              | **ZC706**                       | xilinx-zc706-v20XY.Z-final.bsp            | **Hardware:** Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_4bits, dip_switches_4bits, gpio_sws_3bits.<br>**Software:** FSBL, U-boot, Linux, device-tree (includes Open AMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs. |
| **Zynq-7000**              | **Avnet Digilent Zedboard**     | avnet-digilent-zedboard-v20XY.Z-final.bsp | **Hardware:** Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_8bits, btns_5bits, sws_8bits.<br>**Software:** FSBL, U-boot, Linux, device-tree (includes Open AMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs. |
| **Zynq UltraScale+ MPSoC** | **ZCU102 (production silicon)** | xilinx-zcu102-v20XY.Z-final.bsp           | **Hardware:** Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.)<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), rootfs (minimal packages).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs. |
| **Zynq UltraScale+ MPSoC** | **ZCU104 (production silicon)** | xilinx-zcu104-v20XY.Z-final.bsp           | **Hardware:** Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), vcu-control software, rootfs (with GStreamer, OpenMAX, V4L2, libdrm, vcu-examples).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs. |
| **Zynq UltraScale+ MPSoC** | **ZCU106 (production silicon)** | xilinx-zcu106-v20XY.Z-final.bsp           | **Hardware:** Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), vcu-control software, rootfs (with GStreamer, OpenMAX, V4L2, libdrm, vcu-examples).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs. |
| **Zynq UltraScale+ RFSoC** | **ZCU111 (production silicon)** | xilinx-zcu111-v20XY.Z-final.bsp           | **Hardware:** Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.) and rf_data_converters, sd_fec_dec, adc_sink, dac_source, axi_gpio, axi_intc IPs.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), rfdc-drivers, rootfs (includes RDFC example apps).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs. |
| **Zynq UltraScale+ RFSoC** | **ZCU1275**                     | xilinx-zcu1275-v20XY.Z-final.bsp          | **Hardware:** Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.) and rf_data_converters, adc_sink, dac_source, axi_gpio, axi_intc IPs.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), rfdc-drivers, rootfs (includes RDFC example apps).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs. |
| **Zynq UltraScale+ RFSoC** | **ZCU1285**                     | xilinx-zcu1285-v20XY.Z-final.bsp          | **Hardware:** Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.) and rf_data_converters, adc_sink, dac_source, axi_gpio, axi_intc IPs.<br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes Open AMP, Xen), rfdc-drivers, rootfs (includes RDFC example apps).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs. |
| **Zynq UltraScale+ RFSoC** | **ZCU208**                      | xilinx-zcu208-v20XY.Z-final.bsp           | **Hardware:** Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet etc.) and ADC_DDR_DMA, DAC_DDR_DMA CLOCKING blocks, axi_gpio IPs.<br>**Software:** FSBL, PMUFW, ATF, U-Boot, Linux, device-tree (includes open-amp, xen), rfclk, rfdc-drivers, rootfs (includes RFCLK and RDFC example apps).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs. |
| **Zynq UltraScale+ RFSoC** | **ZCU216**                      | xilinx-zcu216-v20XY.Z-final.bsp           | **Hardware:** Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet etc.) and ADC_DDR_DMA, DAC_DDR_DMA CLOCKING blocks, axi_gpio IPs.<br>**Software:** FSBL, PMUFW, ATF, U-Boot, Linux, device-tree (includes open-amp, xen), rfclk, rfdc-drivers, rootfs (includes RFCLK and RDFC example apps).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, ATF, u-boot, Linux and rootfs. |

**Note**: The "<architecture> sstate-cache" (sstate\_<architecture>\_2020.1.tar.gz) file can be found on the Xilinx [download](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools/2020-1.html) area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2020.1_README.tar.gz) file that outlines the procedure to use "sstate cache".

Refer to the attached file "2020.1\_PetaLinux\_Packages\_List" for software package versions tested on host machines, which is required for PetaLinux installation tools.

See also the attached README.

**PetaLinux 2020.1 contains the following build collateral:**

| Component                      | Git Repo                                                     | Git Branches          | Git Tags                    | Commit ID                                                    | Comments                                                     |
| ------------------------------ | ------------------------------------------------------------ | --------------------- | --------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **FSBL**                       | git://github.com/Xilinx/embeddedsw.git                       | release-2020.1        | xilinx-v2020.1              | 6cbb920f4de9e650dc361b8e487f139fd4c3c743                     | FSBL for Zynq-7000 is at `embeddedsw/lib/sw_apps/zynq_fsbl`<br>FSBL for Zynq UltraScale+ is at `embeddedsw/lib/sw_apps/zynqmp_fsbl` |
| **PMU Firmware**               | git://github.com/Xilinx/embeddedsw.git                       | release-2020.1        | xilinx-v2020.1              | 6cbb920f4de9e650dc361b8e487f139fd4c3c743                     | PMU for Zynq UltraScale+ Firmware is at `embeddedsw/lib/sw-apps/zynqmp_pmufw` |
| **Device-tree**                | git://github.com/Xilinx/device-tree-xlnx.git                 | master                | xilinx-v2020.1              | bc8445833318e9320bf485ea125921eecc3dc97a                     |                                                              |
| **Linux**                      | git://github.com/Xilinx/linux-xlnx.git                       | xlnx_rebase_v5.4      | xlnx_rebase_v5.4_2020.1     | 22b71b41620dac13c69267d2b7898ebfb14c954e                     | Linux Kernel rebase version 5.4                              |
| **U-Boot**                     | git://github.com/Xilinx/u-boot-xlnx.git                      | xlnx_rebase_v2020.01  | xlnx_rebase_v2020.01_2020.1 | 86c84c0d0f916ec00d5d76a32dc9372a25429ca9                     | U-Boot Version v2020.01                                      |
| **QEMU**                       | git://github.com/Xilinx/qemu.git                             | master                | xilinx-v2020.1              | e371d99ac19b9c4f3f98e6e6a3db1ea95091a50e                     |                                                              |
| **Xen**                        | git://github.com/Xilinx/xen.git                              | xilinx/release-2020.1 | xilinx-v2020.1              | 775913b2892a8c9b08dfa3db81b1cf93798399aa                     | Xen Version 4.13                                             |
| **ARM-Trusted-Firmware (ATF)** | git://github.com/Xilinx/arm-trusted-firmware.git             | xlnx_rebase_v2.2      | xilinx-v2020.1              | 5918e656ef29dbdf234a6324ec85bc8a68eca113                     | ATF is based on upstream version 2.2                         |
| **Yocto**                      | git://github.com/Xilinx/meta-xilinx.git<br>git://github.com/Xilinx/meta-xilinx-tools.git<br>git://github.com/Xilinx/meta-petalinux.git | rel-v2020.1           | No Tags                     | 7631da21ae8552cd3f562c81ab541ac54fc6a382<br>38ab571b4ec58e820636309bd66c6b03be59a39c<br>0fc49cd7d25481aef7b99cb9adb9f1416d652bd9 | Yocto 3.0.0 Zeus                                             |
| **qemu-devicetrees**           | git://github.com/Xilinx/qemu-devicetrees.git                 | branch/xilinx-v2020.1 | xilinx-v2020.1              | f128c06a10d45cfeadeb0fbff01ac63eaaaa104d                     |                                                              |
| **OpenAMP**                    | git://github.com/Xilinx/open-amp.git                         | master                | xilinx-v2020.1              | 7014401c4a720dcdc1472ccd530cce1eb046454e                     |                                                              |
| **libmetal**                   | git://github.com/Xilinx/libmetal.git                         | master                | xilinx-v2020.1              | 9ee43dbed82c088fdb91a1dbb8ba6ae4a2d18050                     |                                                              |
| **VCU OpenMax IL**             | git://github.com/Xilinx/vcu-omx-il.git                       | release-2020.1        | xilinx-v2020.1              | b5ffa7ec36814cb52c1616dffea2c4ced51fee19                     |                                                              |
| **VCU Control Software**       | git://github.com/Xilinx/vcu-ctrl-sw.git                      | release-2020.1        | xilinx-v2020.1              | 8ad2b1323bdc98d580360e1a01006d70625c4e65                     |                                                              |
| **VCU Firmware**               | git://github.com/Xilinx/vcu-firmware.git                     | release-2020.1        | xilinx-v2020.1              | 7ecfd476deb054f354791cc1300ccba069e234f5                     |                                                              |
| **VCU Modules**                | git://github.com/Xilinx/vcu-modules.git                      | release-2020.1        | xilinx-v2020.1              | 38827a9172cfb1f0243547c04b2babc045d411ee                     |                                                              |
| **GStreamer OpenMax IL**       | git://github.com/Xilinx/gst-omx.git                          | xilinx-master         | xilinx-v2020.1              | a051c245c3e9f4d323d2fc697a9faf18264b6ffb                     | GStreamer version 1.16.1                                     |
| **GStreamer Plugins-Base**     | git://github.com/Xilinx/gst-plugins-base.git                 | release-2020.1        | xilinx-v2020.1              | ffc05bce0bc02cb2cafd50914f01640dab47f274                     |                                                              |
| **GStreamer Plugins-Bad**      | git://github.com/Xilinx/gst-plugins-bad.git                  | release-2020.1        | xilinx-v2020.1              | 19b2018f2c31c0011c78fa7300544165739dc91a                     |                                                              |
| **GStreamer Plugins-Good**     | git://github.com/Xilinx/gst-plugins-good.git                 | release-2020.1        | xilinx-v2020.1              | 9aa8f9b9f1b5de43fa8557485d23fcb42d77d95d                     |                                                              |
| **GStreamer**                  | git://github.com/Xilinx/gstreamer.git                        | release-2020.1        | xilinx-v2020.1              | 10db9688beab0b11ea2e8c5b05d78c57a589ad03                     |                                                              |
| **hdmi-modules**               | git://github.com/Xilinx/hdmi-modules.git                     | rel-v2020.1           | xilinx-v2020.1              | 3a6e440b50263a3ed99492aba3e507d7c130355c                     |                                                              |
| **GCC**                        |                                                              |                       |                             |                                                              | MB compiler version 9.2<br>ARM compiler version 9.2          |

**2020.1 Release Notes for Open Source components wiki page:**

Covers details for below components changes (new features/fixes) in a particular release.

https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/541130754/2020.1+Release+Notes+for+Open+Source+Components

**2020.1 Release pre-built images wiki page:**

[https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/559875220/2020.1+Release](https://xilinx-wiki.atlassian.net/wiki/spaces/XWUC/pages/559875220/2020.1+Release)

**2020.1 New Features:**

**Note: Versal content are in bold font**

**PetaLinux**

-   Upgraded to Yocto Project version to 3.0 Zeus release
-   Upgraded GCC too chain version to 9.2
-   Host OS dependent packages are part of PetaLinux tools
    -   gpg, make unzip, wget, diffstat, chrpath, socat, tar, bzip2, gzip and diffutils are part of PetaLinux tool now and there is no need to install as Host OS dependency packages
-   Added support for selecting desired Yocto eSDK when installing PetaLinux tool, so you can install PetaLinux tools for specific platforms only such as MicroBlaze, Zynq-7000, ZynqMP and **Versal**.
-   Added support for upgrading desired Yocto eSDK with already installed PetaLinux tool, means you can upgrade PetaLinux tools for specific platforms only such as MicroBlaze, Zynq-7000, ZynqMP and **Versal** from current version to release version.
-   Reduced installed tool size by removing minimal download and sstate cache files.
-   Yocto eSDK now is part of PetaLinux tools.
-   Added warnings message if the xsa changes in the specified directory.
-   Removed meta-plnx-generated layer from PetaLinux project to minimize build time.
-   Added compiler configuration in petalinux-config options for PMUFW and FSBL where you can pass PMUFW/FSBL Debug or Compiler flags to build.
-   Added support for remote source for apps when you create apps using petalinux-create commands.
-   Default PetaLinux build images are INITRD based.
-   Added support for building open source bootgen from PetaLinux for on-target use.
-   Added archiver option in petalinux-build command which will pack all the source and licenses of petalinux-build packages.
-   Added support for SD Image creation with required boot partition using Yocto WIC utility.
-   Added support for mechanism and infrastructure for users to work with readily available dtsi files instead of relying on XSA for FPGA Manager.
-   Added support for xen-image-builder in PetaLinux where it generates a U-Boot script with kernel offsets auto-calculated that can be used to load all of the binaries automatically and boot the full system.
-   Added support for unified kernel and rootfs images
    -   Zynq-7000 devices
    -   Zynq UltraScale+ MPSoC/RFSoC devices
    -   **Versal devices**

**GPU MALI-400**

-   Mali headless egl backend now supports pixmap surface (particularly arm specific handle for dmabuf).
-   Incremental performance change over render to texture.

**2020.1 Bug Fixes:**

**Note: Versal content are in bold font**

**PetaLinux**

-   Fixed Debugging Linux kernel breaking point issue using Vitis.
-   Fixed U-boot QSPI flash configuration for maximum read speed.
-   Fixed XSA with MicroBlaze not working using PetaLinux 2019.2 release.
-   Fixed PetaLinux hang issue when you package R5 application to BOOT.bin using BIF attributes.
-   Fixed PetaLinux kernel config using bsg.cfg not propagating through kernel menuconfig.
-   Fixed PetaLinux "devtool update-recipe" issue for U-boot
-   Fixed Warning messages when sourcing PetaLinux tools on RHEL 7.6 
-   Updated U-boot deconfigs for MicroBlaze BSP.
-   Fixed error messages which copying images to /tftpboot directory.
-   Fixed build errors when external source pathc is assigned to a variable.
-   **Fixed PetaLinux VCK190 and VMK180 BSP nomenclature.**

**GPU MALI-400**

-   Fixed Pixmap offscreen rendering issue using MALI Headless backend.
-   Fixed eglCreateImageKHR API not working for YUYV format.

**Known Issues for 2020.1:**

| Linux/Baremetal | Components | Description                                                  | Work-around           | To be fixed version |
| --------------- | ---------- | ------------------------------------------------------------ | --------------------- | ------------------- |
| Linux           | PetaLinux  | Zynq UltraScale+ MPSoC: How to enable UHS (SD 3.0) support for ZCU102 and ZCU106 evaluation board PetaLinux BSPs | (Xilinx Answer 69978) |                     |
| Linux           | XSDK       | Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle    | (Xilinx Answer 69143) |                     |
| Linux           | FSBL       | Zynq UltraScale+ MPSoC: How to achieve SATA performance in Linux | (Xilinx Answer 71584) |                     |
| Linux           | FSBL       | Zynq UltraScale+ MPSoC: How to make SMMU work with SATA IP   | (Xilinx Answer 71790) |                     |
| Linux           | PetaLinux  | 2020.1 PetaLinux: Configuring project with same xsa more than once will delete all the files from hw-description directory | (Xilinx Answer 75213) | 2020.2              |
| Linux           | PetaLinux  | 2020.1 PetaLinux: Devtool Workspace location has incorrect text in help menu | (Xilinx Answer 75204) | 2020.2              |
| Linux           | Drivers    | 2020.1 Zynq-7000: Ethernet Performance Numbers Lower in Linux 5.4 kernel | (Xilinx Answer 75195) | 2020.2              |
| Linux           | Drivers    | 2020.1 Linux: Does Linux 5.4 kernel supports ISSI and Macronix flash QSPI drivers | (Xilinx Answer 75214) | 2020.2              |
| Linux           | U-boot     | 2020.1 Zynq UltraScale+ RFSoC: Ethernet doesn't work in U-boot on ZC1275 and ZC1285 evaluation boards | (Xilinx Answer 75209) | 2020.2              |
| Linux           | PetaLinux  | 2019.1-2020.1 PetaLinux: MCS Flash boot gets stuck at FSBOOT for MicroBlaze based designs | (Xilinx Answer 75155) | 2020.2              |
| Linux           | Drivers    | 2020.1 Zynq UltraScale+ MPSoC VCU: VCU demo decode display example fails to run with SD UHS mode | (Xilinx Answer 75219) | 2020.2              |
| Linux           | Drivers    | 2020.1 Zynq UltraScale+ MPSoC: AXI Ethernet driver in specific MCDMA configuration throws swiotlb full error with jumbo frames | (Xilinx Answer 75218) | 2020.2              |
| Linux           | PetaLinux  | 2020.1 PetaLinux: Does git based bootgen supports security features | (Xilinx Answer 75327) | 2020.2              |

# 2020.1_PetaLinux_Package_List

## Linux Distribution OS details:

1. RHEL 7.4, 7.5, 7.6, 7.7 and 8.1 Server:  Infrastructure Server
2. RHEL 7.4, 7.5, 7.6, 7.7 and 8.1 Desktop : Development and Creative workstation.
3. CentOS 7.4, 7.5, 7.6, 7.7 and 8.1 Server (From Everything.ISO): Infrastructure server.
4. CentOS 7.4, 7.5, 7.6, 7.7 and 8.1 Desktop (From Everything.ISO): Development and Creative workstation.
5. Ubuntu 16.04.05 and Ubuntu 16.04.06 Desktop.
6. Ubuntu 16.04.05  and Ubuntu 16.04.06 Server.
7. Ubuntu 18.04.01, 18.04.02, 18.04.03 and Ubuntu 18.04.04 Desktop.
8. Ubuntu 18.04.01, 18.04.02, 18.04.03  and Ubuntu 18.04.04 Server.

### Note:

1. Empty packages are not installed means assuming these are default from Linux Distribution.

## Tool/Library Versions

### RHEL/CentOS versions

| Tool/Library                                    | Red Hat Enterprise Desktop/Server  7.4 (64-bit)              | Red Hat Enterprise Destop/Server 7.5(64-bit) | Red Hat Enterprise Desktop/Server  7.6 (64-bit) | Red Hat Enterprise Desktop/Server  7.7(64-bit) | Red Hat Enterprise Desktop/Server  8.1 (64-bit) | CentOS Desktop/Server 7.4  (64-bit)        | CentOS Desktop/Server 7.5  (64-bit)        | CentOS Desktop/Server 7.6  (64-bit)        | CentOS Desktop/Server 7.7  (64-bit)        | CentOS Desktop/Server 8.1  (64-bit)       |
| ----------------------------------------------- | ------------------------------------------------------------ | -------------------------------------------- | ----------------------------------------------- | ---------------------------------------------- | ----------------------------------------------- | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ----------------------------------------- |
| Quick Installation steps for packages:          | su yum install net-tools gawk make wget tar bzip2.x86_64 gzip python unzip perl patch.x86_64 diffutils diffstat git cpp gcc gcc-c++ glibc-devel texinfo chrpath socat perl-Data-Dumper perl-Text-ParseWords perl-Thread-Queue python34-pip xz which SDL-devel xterm autoconf libtool.x86_64 zlib-devel automake glib2-devel zlib ncurses-devel openssl-devel dos2unix flex bison glibc.i686 screen pax glibc-devel.i686 compat-libstdc++-33.i686 libstdc++.i686 |                                              |                                                 |                                                |                                                 |                                            |                                            |                                            |                                            |                                           |
| ip (iproute)                                    | iproute-3.10.0-87.el7.x86_64                                 | iproute-4.11.0-14.el7.x86_64                 | iproute-4.11.0-14.el7.x86_64                    | iproute-4.11.0-25.el7_7.2.x86_64               | iproute-5.3.0-1.el8.x86_64                      | iproute-3.10.0-87.el7.x86_64               | iproute-4.11.0-14.el7.x86_64               | iproute-4.11.0-14.el7.x86_64               | iproute-4.11.0-25.el7_7.2.x86_64           | iproute-5.3.0-1.el8.x86_64                |
| gawk                                            | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7_3.1.x86_64                  | gawk-4.0.2-4.el7_3.1.x86_64                     | gawk-4.0.2-4.el7_3.1.x86_64                    | gawk-4.2.1-1.el8.x86_64                         | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.2.1-1.el8.x86_64                   |
| gcc                                             | gcc-4.8.5-16.el7_4.1.x86_64                                  | gcc-4.8.5-16.el7_4.1.x86_64                  | gcc-4.8.5-16.el7_4.1.x86_64                     | gcc-4.8.5-39.el7.x86_64                        | gcc-8.3.1-5.el8.x86_64                          | gcc-4.8.5-16.el7_4.1.x86_64                | gcc-4.8.5-39.el7.x86_64                    | gcc-4.8.5-39.el7.x86_64                    | gcc-4.8.5-39.el7.x86_64                    | gcc-8.3.1-5.el8.x86_64                    |
| netstat (net-tools)                             | net-tools-2.0-0.22.20131004git.el7.x86_64                    | net-tools-2.0-0.25.20131004git.el7.x86_64    | net-tools-2.0-0.24.20131004git.el7.x86_64       | net-tools-2.0-0.25.20131004git.el7.x86_64      | net-tools-2.0-0.51.20160912git.el8.x86_64       | net-tools-2.0-0.24.20131004git.el7.x86_64  | net-tools-2.0-0.22.20131004git.el7.x86_64  | net-tools-2.0-0.24.20131004git.el7.x86_64  | net-tools-2.0-0.25.20131004git.el7.x86_64  | net-tools-2.0-0.51.20160912git.el8.x86_64 |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-5.9-14.20130511.el7_4.x86_64                   | ncurses-devel-5.9-14.20130511.el7_4.x86_64   | ncurses-devel-5.9-14.20130511.el7_4.x86_64      | ncurses-devel-5.9-14.20130511.el7_4.x86_64     | ncurses-devel-6.1-7.20180224.el8.x86_64         | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-6.1-7.20180224.el8.x86_64   |
| zlib-devel(also,install 32-bit of this version) | zlib-devel-1.2.7-18.el7.x86_64                               | zlib-devel-1.2.7-18.el7.x86_64               | zlib-devel-1.2.7-18.el7.x86_64                  | zlib-devel-1.2.7-18.el7.x86_64                 | zlib-devel-1.2.11-13.el8.x86_64                 | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.11-13.el8.x86_64           |
| openssl-devel                                   | openssl-devel-1.0.2k-8.el7.x86_64                            | openssl-devel-1.0.2k-19.el7.x86_64           | openssl-devel-1.0.2k-19.el7.x86_64              | openssl-devel-1.0.2k-19.el7.x86_64             | openss-devell-1.1.1c-15.el8.x86_64              | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openss-devell-1.1.1c-15.el8.x86_64        |
| flex                                            | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                     | flex-2.5.37-3.el7.x86_64                        | flex-2.5.37-6.el7.x86_64                       | flex-2.5.37-3.el7.x86_64                        | flex-2.5.37-3.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-3.el7.x86_64                  |
| bison                                           | flex-2.5.37-3.el7.x86_64                                     | bison-3.0.4-1.el7.x86_64                     | bison-3.0.4-1.el7.x86_64                        | flex-2.5.37-6.el7.x86_64                       | flex-2.5.37-3.el7.x86_64                        | bison-3.0.4-1.el7.x86_64                   | bison-3.0.4-2.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-3.el7.x86_64                  |
| libselinux                                      | libselinux-2.5-11.el7.x86_64                                 | libselinux-2.5-14.1.el7.x86_64               | libselinux-2.5-14.1.el7.x86_64                  | libselinux-2.5-14.1.el7.x86_64                 | libselinux-2.9-3.el8.x86_64                     | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.5-12.1.el7.x86_64             | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.9-3.el8.x86_64               |
| xterm                                           | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                       | xterm-295-3.el7.x86_64                          | xterm-295-3.el7.x86_64                         | xterm-331-1.el8.x86_64                          | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-331-1.el8.x86_64                    |
| autoconf                                        | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                  | autoconf-2.69-11.el7.noarch                     | autoconf-2.69-11.el7.noarch                    | autoconf-2.69-27.el8.noarch                     | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-27.el8.noarch               |
| libtool                                         | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                | libtool-2.4.2-22.el7_3.x86_64                   | libtool-2.4.2-22.el7_3.x86_64                  | libtool-2.4.6-25.el8.x86_64                     | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.6-25.el8.x86_64               |
| texinfo                                         | texinfo-5.1-5.el7.x86_64                                     | texinfo-5.1-5.el7.x86_64                     | texinfo-5.1-5.el7.x86_64                        | texinfo-5.1-5.el7.x86_64                       | texinfo-5.1-5.el7.x86_64                        | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                  |
| zlib1g-dev                                      |                                                              |                                              |                                                 |                                                |                                                 |                                            |                                            |                                            |                                            |                                           |
| gcc-multilib                                    |                                                              |                                              |                                                 |                                                |                                                 |                                            |                                            |                                            |                                            |                                           |
| build-essential                                 |                                                              |                                              |                                                 |                                                |                                                 |                                            |                                            |                                            |                                            |                                           |
| SDL-devel                                       | SDL-devel-1.2.15-14.el7.x86_64                               | SDL-devel-1.2.15-14.el7.x86_64               | SDL-devel-1.2.15-14.el7.x86_64                  | SDL-devel-1.2.15-14.el7.x86_64                 | SDL-1.2.15-37.el8.x86_64                        | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-1.2.15-37.el8.x86_64                  |
| glibc-devel                                     | glibc-devel-2.17-292.el7.x86_64                              | glibc-devel-2.17-292.el7.x86_64              | glibc-devel-2.17-307.el7.x86_64                 | glibc-devel-2.17-307.el7.1.x86_64              | glibc-devel-2.28-101.el8.x86_64                 | glibc-devel-2.17-292.el7.x86_64            | glibc-devel-2.17-307.el7.x86_64            | glibc-devel-2.17-292.el7.x86_64            | glibc-devel-2.17-307.el7.1.x86_64          | glibc-devel-2.28-101.el8.x86_64           |
|                                                 |                                                              |                                              |                                                 |                                                |                                                 |                                            |                                            |                                            |                                            |                                           |
| glib2-devel                                     | glib2-devel-2.56.1-5.el7.x86_64                              | glib2-devel-2.56.1-5.el7.x86_64              | glib2-devel-2.56.1-5.el7.x86_64                 | glib2-devel-2.56.1-5.el7.x86_64                | glib2-2.56.4-8.el8.x86_64                       | glib2-devel-2.56.1-5.el7.x86_64            | glib2-devel-2.56.1-5.el7.x86_64            | glib2-devel-2.56.1-5.el7.x86_64            | glib2-devel-2.56.1-5.el7.x86_64            | glib2-2.56.4-8.el8.x86_64                 |
| automake                                        | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                    | automake-1.13.4-3.el7.noarch                   | automake-1.16.1-6.el8.noarch                    | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.16.1-6.el8.noarch              |
| screen                                          | gnome-screenshot-3.22.0-1.el7.x86_64                         | gnome-screenshot-3.22.0-1.el7.x86_64         | gnome-screenshot-3.22.0-1.el7.x86_64            | gnome-screenshot-3.22.0-1.el7.x86_64           | gnome-screenshot-3.22.0-1.el7.x86_64            | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64      |
| pax                                             | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                        | pax-3.4-19.el7.x86_64                           | gnome-screenshot-3.22.0-1.el7.x86_64           | pax-3.4-19.el7.x86_64                           | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | pax-3.4-19.el7.x86_64                     |
| libstdc++                                       | libstdc++-4.8.5-39.el7_4.1.x86_64                            | libstdc++-4.8.5-16.el7_4.1.x86_64            | libstdc++-4.8.5-39.el7_4.1.x86_64               | libstdc++-4.8.5-39.el7.x86_64                  | libstdc++-8.3.1-5.el8.x86_64                    | libstdc++-4.8.5-16.el7_4.1.x86_64          | libstdc++-4.8.5-39.el7.x86_64              | libstdc++-4.8.5-39.el7.x86_64              | libstdc++-4.8.5-39.el7.x86_64              | libstdc++-8.3.1-5.el8.x86_64              |
| g++ (gcc-c++)                                   | gcc-c++-4.8.5-16.el7_4.1.x86_64                              | gcc-c++-4.8.5-16.el7_4.1.x86_64              | gcc-c++-4.8.5-16.el7_4.1.x86_64                 | gcc-c++-4.8.5-39.el7.x86_64                    | gcc-c++-8.3.1-5.el8.x86_64                      | gcc-c++-4.8.5-16.el7_4.1.x86_64            | gcc-c++-4.8.5-39.el7_4.1.x86_64            | gcc-c++-4.8.5-39.el7.x86_64                | gcc-c++-4.8.5-39.el7.x86_64                | gcc-c++-8.3.1-5.el8.x86_64                |
| python3                                         | python34-pip-8.1.2-10.el7.noarch                             | python34-pip-8.1.2-10.el7.noarch             | python34-pip-8.1.2-10.el7.noarch                | python34-pip-8.1.2-10.el7.noarch               | python34-pip-8.1.2-10.el7.noarch                | glibc-devel-2.17.292.el7.x86-64            | python34-pip-8.1.2-10.el7.noarch           | python34-pip-8.1.2-10.el7.noarch           | python34-pip-8.1.2-10.el7.noarch           | python34-pip-8.1.2-10.el7.noarch          |

### Ubuntu

| Tool/Library                                    | Ubuntu Desktop   /Server 16.04.05(64-bit)                    | Ubuntu Desktop /Server 16.04.06 (64-bit) | Ubuntu Desktop /Server 18.04.01 (64-bit)    | Ubuntu Desktop /Server 18.04.02 (64-bit)    | Ubuntu Desktop /Server 18.04.03 (64-bit)    | Ubuntu Desktop /Server 18.04.04 (64-bit)    |
| ----------------------------------------------- | ------------------------------------------------------------ | ---------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| Quick Installation steps for packages:          | sudo apt-get install gawk python build-essential gcc git make net-tools libncurses5-dev tftpd zlib1g-dev libssl-dev flex bison libselinux1 gnupg wget diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib build-essential-dev zlib1g:i386 screen pax gzip |                                          |                                             |                                             |                                             |                                             |
| ip (iproute)                                    |                                                              |                                          |                                             |                                             |                                             |                                             |
| gawk                                            | gawk-1:4.1.3+dfsg-0.1                                        | gawk-1:4.1.3+dfsg-0.1                    | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   |
| gcc                                             | gcc-4:5.3.1-1ubuntu1 500                                     | gcc-4:5.3.1-1ubuntu1 500                 | gcc-4:7.4.0-1ubuntu2.3                      | gcc-4:7.4.0-1ubuntu2.3                      | gcc-4:7.4.0-1ubuntu2.3                      | gcc-4:7.4.0-1ubuntu2.3                      |
| netstat (net-tools)                             | net-tools-1.60-26ubuntu1 500                                 | net-tools-1.60-26ubuntu1 500             | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-6.0+20160213-1ubuntu1                          | ncurses-devel-6.0+20160213-1ubuntu1      | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            |
| zlib-devel(also,install 32-bit of this version) |                                                              |                                          |                                             |                                             |                                             |                                             |
| openssl-devel                                   | openssl-devel-1.0.2g-1ubuntu4.15                             | openssl-devel-1.0.2g-1ubuntu4.15         | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-ubuntu2.1~18.04.4       |
| flex                                            | flex-2.6.0-11                                                | flex-2.6.0-11                            | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                |
| bison                                           | bison-2:3.0.4.dfsg-1                                         | bison-2:3.0.4.dfsg-1                     | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  |
| libselinux                                      |                                                              |                                          |                                             |                                             |                                             |                                             |
| xterm                                           | xterm-322-1ubuntu1                                           | xterm-322-1ubuntu1                       | xterm-330-1ubuntu2                          | xterm-330-1ubuntu2                          | xterm-330-1ubuntu2                          | xterm-330-1ubuntu2                          |
| autoconf                                        | autoconf-2.69-9                                              | autoconf-2.69-9                          | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            |
| libtool                                         | libtool-2.4.6-0.1                                            | libtool-2.4.6-0.1                        | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             |
| texinfo                                         | texinfo-6.1.0.dfsg.1-5                                       | texinfo-6.1.0.dfsg.1-5                   | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      |
| zlib1g-dev                                      | zlib1g-dev1:1.2.8.dfsg-2ubuntu4.1                            | zlib1g-dev1:1.2.8.dfsg-2ubuntu4.1        | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            |
| gcc-multilib                                    | gcc-multilib-4:5.3.1-1ubuntu1                                | gcc-multilib-4:5.3.1-1ubuntu1            | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             |
| build-essential                                 | build-essential-12.1ubuntu2                                  | build-essential-12.1ubuntu2              | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 |
| SDL-devel                                       |                                                              |                                          |                                             |                                             |                                             |                                             |
| glibc-devel                                     |                                                              |                                          |                                             |                                             |                                             |                                             |
|                                                 |                                                              |                                          |                                             |                                             |                                             |                                             |
| glib2-devel                                     |                                                              |                                          |                                             |                                             |                                             |                                             |
| automake                                        | automake-1:1.15-4ubuntu1                                     | automake-1:1.15-4ubuntu1                 | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  |
| screen                                          | screen-4.3.1-2build1                                         | screen-4.3.1-2build1                     | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       |
| pax                                             | pax-1:20151013-1                                             | pax-1:20151013-1                         | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-2                            |
| libstdc++                                       | libstdc++-5.4.0-6ubuntu1~16.04.9cross1                       | libstdc++-5.4.0-6ubuntu1~16.04.9cross1   | libstdc++-6.5.0-2ubuntu1~18.04              | libstdc++-8.3.0-6ubuntu1~18.04.1            | libstdc++-8.3.0-6ubuntu1~18.04.1            | libstdc++-8.3.0-6ubuntu1~18.04.1            |
| g++ (gcc-c++)                                   | gcc-c++-4:5.3.1-1ubuntu1                                     | gcc-c++-4:5.3.1-1ubuntu1                 | gcc-c++-4:7.4.0-1ubuntu2.3                  | gcc-c++-7.4.0-1ubuntu1~18.04.1              | gcc-c++-7.4.0-1ubuntu1~18.04.1              | gcc-c++-7.4.0-1ubuntu1~18.04.1              |
| python3                                         | python34-pip-19.3.1                                          | python34-pip-19.3.1                      | python34-pip-19.3.1                         | python34-pip-19.3.1                         | python34-pip-19.3.1                         | python34-pip-19.3.1                         |

# README_content_v2020_1

=============================

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2020.1 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2020.1 Open Components Source Code (TAR/GZIP) file: 
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