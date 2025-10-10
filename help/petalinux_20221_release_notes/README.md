# PetaLinux 2022.1 - Product Update Release Notes and Known Issues

## Title

PetaLinux 2022.1 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2022.1 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for the 2022.1 PetaLinux Release**

This table contains supported BSPs for MicroBlaze, Zynq-7000, Zynq UltraScale+ MPSoC/RFSoC and Versal devices which are available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

**Note:** mmddhhmm is a format replacing "-final" from BSP naming and will reflect the Released BSP's final build date and time information.

|                            |                           |                                          |                                                              |
| -------------------------- | ------------------------- | ---------------------------------------- | ------------------------------------------------------------ |
| Platform                   | Variant                   | BSP Name                                 | BSP Description                                              |
| **MicroBlaze**             | AC701                     | xilinx-ac701-v2022.1-04191534.bsp        | **This BSP contains:**<br>**Hardware:** Vivado board preset design with MicroBlaze Processor, AXI UARTLITE, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, U-Boot, Linux and rootfs. |
| **MicroBlaze**             | KC705                     | xilinx-kc705-v2022.1-04191534.bsp        | **This BSP contains:**<br>**Hardware:** Vivado board preset design with MicroBlaze Processor, AXI UARTLITE, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, U-Boot, Linux and rootfs. |
| **MicroBlaze**             | KCU105                    | xilinx-kcu105-v2022.1-04191534.bsp       | **This BSP contains:**<br>**Hardware:** Vivado board preset design with MicroBlaze Processor, AXI UARTLITE, AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI 1G/2.5G Ethernet.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, U-Boot, Linux and rootfs. |
| **MicroBlaze**             | SP701                     | xilinx-sp701-v2022.1-04191534.bsp        | **This BSP contains:**<br>**Hardware:** Vivado design with MicroBlaze Processor, AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, AXI UART_lite, led_8bits, and AXI 1G/2.5G Ethernet.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, U-Boot, Linux and rootfs. |
| **MicroBlaze**             | VCU118                    | xilinx-vcu118-v2022.1-04191534.bsp       | **This BSP contains:**<br>**Hardware:** Vivado design with MicroBlaze Processor, AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, AXI UART_lite, led_8bits, and AXI 1G/2.5G Ethernet.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, U-Boot, Linux and rootfs. |
| **Zynq-7000**              | ZC702                     | xilinx-zc702-v2022.1-04191534.bsp        | **This BSP contains:**<br>**Hardware:** Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet) and AXI GPIO (led_4bits).<br>**Software:** FSBL, U-Boot, Linux, device-tree (includes open-amp), rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, FSBL, U-Boot, Linux and rootfs. |
| **Zynq-7000**              | ZC706                     | xilinx-zc706-v2022.1-04191534.bsp        | **This BSP contains:**<br>**Hardware:** Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet) and AXI GPIO (led_4bits, dip_switches_4bits, gpio_sws_3bits).<br>**Software:** FSBL, U-Boot, Linux, device-tree (includes open-amp), rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, FSBL, U-Boot, Linux and rootfs. |
| **Zynq UltraScale+ MPSoC** | ZCU102 production silicon | xilinx-zcu102-v2022.1-04191534.bsp       | **This BSP contains:**<br>**Hardware (Extensible Platform):** Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA) with PL IPs like proc_sys_reset, axi_vip, axi_intc, axi_interconnect, axi_register_slice.<br>**Vitis:** pfm.tcl packed for generating Vitis platform.<br>**Software:** FSBL, PMUFW, ATF, U-Boot, Linux, device-tree (includes open-amp, Xen), Ramdisk and Full rootfs.<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, U-Boot, Linux and rootfs. |
| **Zynq UltraScale+ MPSoC** | ZCU104 production silicon | xilinx-zcu104-v2022.1-04191534.bsp       | **This BSP contains:**<br>**Hardware (Extensible Platform):** PS block with DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA; includes VCU DDR4 Controller, VCU IP, clk_wiz, axi_interconnect, proc_sys_reset.<br>**Vitis:** pfm.tcl packed for generating Vitis platform.<br>**Software:** FSBL, PMUFW, ATF, U-Boot, Linux, device-tree (open-amp, xen), vcu-control, minimal and full rootfs (GStreamer, OpenMAX, V4L2, libdrm, vcu-examples).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, U-Boot, Linux and rootfs. |
| **Zynq UltraScale+ MPSoC** | ZCU106 production silicon | xilinx-zcu106-v2022.1-04191534.bsp       | **This BSP contains:**<br>**Hardware 1/2 (Extensible Platform):** Two Vivado preset designs using PS block with DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA, VCU DDR4 Controller, VCU IP, clk_wiz, axi_interconnect, proc_sys_reset.<br>**Vitis:** pfm.tcl packed for Vitis platform.<br>**Software:** FSBL, PMUFW, ATF, U-Boot, Linux, device-tree (open-amp, xen), FPGA manager, vcu-control, minimal and full rootfs (includes GStreamer, OpenMAX, V4L2, libdrm, vcu-examples).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, U-Boot, Linux and rootfs. |
| **Zynq UltraScale+ RFSoC** | ZCU111 production silicon | xilinx-zcu111-v2022.1-04191534.bsp       | **This BSP contains:**<br>**Hardware:** RFSoC PS block with rf_data_converters, sd_fec_dec, adc_sink, dac_source, axi_gpio, axi_intc.<br>**Software:** FSBL, PMUFW, ATF, U-Boot, Linux, device-tree (open-amp, xen), rfdc-drivers, minimal and full rootfs (includes RDFC examples).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, U-Boot, Linux and rootfs. |
| **Zynq UltraScale+ RFSoC** | ZCU1275                   | xilinx-zcu1275-v2022.1-04191534.bsp      | Same as ZCU111.                                              |
| **Zynq UltraScale+ RFSoC** | ZCU1285                   | xilinx-zcu1285-v2022.1-04191534.bsp      | Same as ZCU111 (minor text fix for “packages”).              |
| **Versal**                 | VCK190                    | xilinx-vck190-v2022.1-04191534.bsp       | **This BSP contains:**<br>**Hardware (Extensible Platform):** Versal CIPS PS block with pre-production silicon, includes AIE example in PL.<br>**Vitis Platform:** Supports AIE projects (.xsa, xclbin).<br>**Software:** PLM, PSMFW, ATF, U-Boot, Linux, device-tree (open-amp, xen), minimal and full rootfs (includes Tcl, xrt, zocl, Python, AIE-example, Jupyter).<br>**Pre-built Images:** PDI, PLM, PSMFW, ATF, U-Boot, DTB’s, Linux, rootfs, and Xen images.<br>**Note:** Supports VCK190 rev1 and revA boards. |
| **Versal**                 | VMK180                    | xilinx-vmk180-v2022.1-04191534.bsp       | **This BSP contains:**<br>**Hardware:** Versal CIPS PS block with pre-production silicon.<br>**Software:** PLM, PSMFW, ATF, U-Boot, Linux, device-tree (open-amp, xen), minimal and full rootfs (Tcl, Python, libstdc++).<br>**Pre-built Images:** PDI, PLM, PSMFW, ATF, U-Boot, DTB’s, Linux, rootfs, and Xen images.<br>**Note:** Supports VMK180 rev1 and revA boards. |
| **Versal**                 | VCK190 OSPI               | xilinx-vck190-ospi-v2022.1-04191534.bsp  | Similar to VCK190, with **OSPI boot module**.                |
| **Versal**                 | VCK190 eMMC               | xilinx-vck190-emmc-v2022.1-04191534.bsp  | Similar to VCK190, with **eMMC boot module**.                |
| **Versal**                 | VMK180 OSPI               | xilinx-vmk180-ospi-v2022.1-04191534.bsp  | Similar to VMK180, with **OSPI boot module**.                |
| **Versal**                 | VMK180 eMMC               | xilinx-vmk180-emmc-v2022.1-04191534.bsp  | Similar to VMK180, with **eMMC boot module**.                |
| **Zynq UltraScale+ RFSoC** | ZCU216                    | xilinx-zcu216-v2022.1-04191534.bsp       | **This BSP contains:**<br>**Hardware:** RFSoC PS block with production silicon, ADC_DDR_DMA, DAC_DDR_DMA clocking, axi_gpio.<br>**Software:** FSBL, PMUFW, ATF, U-Boot, Linux, device-tree (open-amp, xen), rfclk, rfdc-drivers, minimal and full rootfs (RFCLK, RDFC examples).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, U-Boot, Linux, rootfs. |
| **Zynq UltraScale+ RFSoC** | ZCU208                    | xilinx-zcu208-v2022.1-04191534.bsp       | Same as ZCU216.                                              |
| **Zynq UltraScale+ RFSoC** | ZCU208-SDFEC              | xilinx-zcu208-sdfec-v2022.1-04191534.bsp | **This BSP contains:**<br>**Hardware:** RFSoC PS block with SD-FEC and related IPs.<br>**Software:** FSBL, PMUFW, ATF, U-Boot, Linux, device-tree (open-amp, xen), rfclk, rfdc-drivers, minimal and full rootfs (RFCLK, RDFC, SDFEC examples).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, U-Boot, Linux, rootfs. |
| **Zynq UltraScale+ MPSoC** | K26 Production SOM        | xilinx-k26-som-v2022.1-04191534.bsp      | **This BSP contains:**<br>**Hardware:** Zynq UltraScale PS block (SOM-specific peripherals + UART).<br>**Software:** FSBL, PMUFW, ATF, U-Boot, Linux, device-tree (open-amp, xen), minimal and full rootfs (includes packagegroup-petalinux-som, utils, networking, python, Jupyter).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, U-Boot, Linux, rootfs. |

 **Unified Images supported for the 2022.1 PetaLinux Release**

This table contains supported unified images for Zynq-7000 and Zynq UltraScale+ MPSoC/RFSoC and Versal devices which are available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

| Platform                   | SoC Variant    | Tar File Name                       | Unified Image Description                                    |
| -------------------------- | -------------- | ----------------------------------- | ------------------------------------------------------------ |
| **Zynq UltraScale+ MPSoC** | CG, EG, EV, DR | xilinx-zynqmp-common-v2022.1.tar.gz | **This Tar contains:**<br>**Pre-built Images:** bl31.elf, boot.scr, Image, rootfs.ext4, rootfs.manifest, rootfs.tar.gz, sdk.sh, u-boot.elf<br>**README.txt:** Describes how to install and use these image files. |
| **Versal ACAP**            | AI Core, Prime | xilinx-versal-common-v2022.1.tar.gz | **This Tar contains:**<br>**Pre-built Images:** bl31.elf, boot.scr, Image, rootfs.ext4, rootfs.manifest, rootfs.tar.gz, sdk.sh, u-boot.elf<br>**README.txt:** Describes how to install and use these image files. |
| **Zynq-7000**              | All            | xilinx-zynq-common-v2022.1.tar.gz   | **This Tar contains:**<br>**Pre-built Images:** boot.scr, rootfs.ext4, rootfs.manifest, rootfs.tar.gz, sdk.sh, u-boot.elf, uImage<br>**README.txt:** Describes how to install and use these image files. |

**Note**: The "<architecture> sstate-cache" (sstate\_<architecture>\_2022.1.tar.gz) file can be found on the Xilinx [download](https://www.xilinx.com/downloadNav/embedded-design-tools/2022-1.html)  area along with an associated [README](https://www.xilinx.com/bin/public/openDownload?filename=sstate_rel_2022.1_README.txt)  file that outlines the procedure to use "sstate cache".

Refer to the "2022\_1\_PetaLinux\_Packages\_List.xlsx" from attachments for software package versions tested on host machines, which is required for PetaLinux installation tools.

Refer to  "README\_content\_v2022\_1.txt" from attachments for the downloads area.

**2022.1 Petalinux contains the following build collateral:**

| Yocto Components    |             |                                          |                                                              |                  |
| ------------------- | ----------- | ---------------------------------------- | ------------------------------------------------------------ | ---------------- |
| Component           | Branch      | Commit ID                                | URL                                                          | Github Tag       |
| yocto-scripts       | rel-v2022.1 | 484bd017441f0d895f7d24a82192acdf497408a8 | [GitHub](https://github.com/Xilinx/yocto-scripts/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| yocto-manifests     | rel-v2022.1 | 5f5e18fae4c31a28625a533133c8853c3779837f | [GitHub](https://github.com/Xilinx/yocto-manifests/tree/rel-v2022.1) |                  |
| poky                | rel-v2022.1 | c6eaeb34a5e310e29e965e6f2d53987c2b6999d4 | [GitHub](https://github.com/Xilinx/poky/tree/rel-v2022.1)    | xlnx-rel-v2022.1 |
| meta-xilinx-tools   | rel-v2022.1 | 3fa6ed0d67077749ada967501efcba3d97cbaf8e | [GitHub](https://github.com/Xilinx/meta-xilinx-tools/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-xilinx         | rel-v2022.1 | 80dd93fc46d56861dc506d6752e39ca9787cf065 | [GitHub](https://github.com/Xilinx/meta-xilinx/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-virtualization | rel-v2022.1 | 930c63fee5ed076d03d52e9db2fc37711873159d | [GitHub](https://github.com/Xilinx/meta-virtualization/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-som            | rel-v2022.1 | 2d2d812a40e345486a8e6c037dbd1744342a1e6d | [GitHub](https://github.com/Xilinx/meta-som/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-security       | rel-v2022.1 | 5c604857445b19dcd7d8ce9416566419b53532c9 | [GitHub](https://github.com/Xilinx/meta-security/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-qt5            | rel-v2022.1 | 19c3d955113878578526112bb00643b721f77f82 | [GitHub](https://github.com/Xilinx/meta-qt5/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-python2        | rel-v2022.1 | 7a1ae67682a8ddb21e1ed8f344567456a472f4a0 | [GitHub](https://github.com/Xilinx/meta-python2/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-petalinux      | rel-v2022.1 | 03abb492e1a7e897e87617b4ff2ab6597ac9e51e | [GitHub](https://github.com/Xilinx/meta-petalinux/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-openembedded   | rel-v2022.1 | 5d871d57b49f2779ad4ceb276d43ebe747097e12 | [GitHub](https://github.com/Xilinx/meta-openembedded/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-openamp        | rel-v2022.1 | 26132603e0c1c99d6198b88cb5f19c0a0a6dc75b | [GitHub](https://github.com/Xilinx/meta-openamp/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-mingw          | rel-v2022.1 | f5d761cbd5c957e4405c5d40b0c236d263c916a8 | [GitHub](https://github.com/Xilinx/meta-mingw/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-jupyter        | rel-v2022.1 | 213b7bb5f64703701b1f90bfdfd8cf9a29f2241e | [GitHub](https://github.com/Xilinx/meta-jupyter/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-clang          | rel-v2022.1 | 088904d40231d9e099c2f5039cd3c2bc47d332d1 | [GitHub](https://github.com/Xilinx/meta-clang/tree/rel-v2022.1) | xlnx-rel-v2022.1 |
| meta-browser        | rel-v2022.1 | d25d8ee98a656b2534d0eec6138ef264529fab4f | [GitHub](https://github.com/Xilinx/meta-browser/tree/rel-v2022.1) | xlnx-rel-v2022.1 |

| **System Software Components** |                       |                                          |                                                              |                              |
| ------------------------------ | --------------------- | ---------------------------------------- | ------------------------------------------------------------ | ---------------------------- |
| Component                      | Branch                | Commit ID                                | URL                                                          | Github Tag                   |
| k26-starter-kits               | xlnx_rel_v2022.1      | 1d0dde7d0f7f8fe8816a526876d978480458850b | [GitHub](https://github.com/Xilinx/kria-base-firmware)       | xilinx_v2022.1               |
| ai-engine-driver               | xlnx_rel_v2022.1      | 5f8a3950061fa4d2426a40774129723878cbdbeb | [GitHub](https://github.com/Xilinx/aie-rt)                   | xilinx_v2022.1               |
| libcma                         | image_v2.4            | 3d659d374701b7c34fa702e7aa23f71f9113f826 | [GitHub](https://github.com/Xilinx/PYNQ)                     |                              |
| ultra96-startup-pages          | master                | 276b6efd462fc14f22dcea1af4c51cc3d31d1c95 | [GitHub](https://github.com/Xilinx/ultra96-startup-pages)    |                              |
| pm-notebooks                   | xlnx_rel_v2022.1      | 74693121d9dbc72d5e8290805708b64d37042d79 | [GitHub](https://github.com/Xilinx/platform-management-notebooks) | xilinx_v2022.1               |
| external-hdf                   | xlnx_rel_v2022.1      | e7669d3aaca520c0c1bc2c9a64c67864daafb499 | [GitHub](https://github.com/Xilinx/hdf-examples)             | xilinx_v2022.1               |
| image-update                   | xlnx_rel_v2022.1      | b19467ac98921cea15c8650ceb43e89b239c4653 | [GitHub](https://github.com/Xilinx/linux-image_update)       | xilinx_v2022.1               |
| platformstats                  | xlnx_rel_v2022.1      | 13cbf86e0f3df4a022a72ea9b976cef0069db535 | [GitHub](https://github.com/Xilinx/platformstats)            | xilinx_v2022.1               |
| ddr-qos                        | xlnx_rel_v2022.1      | 6d1304e5b826cea21da02bd7ca04512176f665ff | [GitHub](https://github.com/Xilinx/ddr-qos)                  | xilinx_v2022.1               |
| axi-qos                        | xlnx_rel_v2022.1      | 2fd1b627c83778d03b1a91c99990d3714d261bbd | [GitHub](https://github.com/Xilinx/axi-qos)                  | xilinx_v2022.1               |
| som-dashboard                  | xlnx_rel_v2022.1      | a2922acfee17e8d4e6dc5ea7e52db1b1e928c7f2 | [GitHub](https://github.com/Xilinx/SOM-Dashboard)            | xilinx_v2022.1               |
| xmutil                         | xlnx_rel_v2022.1      | 33e2332ba7e9201ac34ce6e99eed640eff308619 | [GitHub](https://github.com/Xilinx/xmutil)                   | xilinx_v2022.1               |
| dfx-mgr                        | xlnx_rel_v2022.1      | b82419d93ec3cff6fe8095b5298a28bffb75b184 | [GitHub](https://github.com/Xilinx/dfx-mgr)                  | xilinx_v2022.1               |
| image-builder                  | xlnx_rel_v2022.1      | 8934dc43c2ab835a1a291fbb4140abe6276ec0cb | [GitHub](https://github.com/Xilinx/imagebuilder)             | xilinx_v2022.1               |
| sdfec                          | xlnx_rel_v2022.1      | 91a9fc9b6758959f34fef92dbfd3bb3556181f3e | [GitHub](https://github.com/Xilinx/linux-examples)           | xilinx_v2022.1               |
| libdfx                         | xlnx_rel_v2022.1      | 6d423bbafd9ac14194a6a80f4d276c9024d2defa | [GitHub](https://github.com/Xilinx/libdfx)                   | xilinx_v2022.1               |
| bootgen                        | xlnx_rel_v2022.1      | 4eac958eb6c831ffa5768a0e2cd4be23c5efe2e0 | [GitHub](https://github.com/Xilinx/bootgen)                  | xilinx_v2022.1               |
| gstreamer1.0-plugins-bad       | xlnx-rebase-v1.18.5   | cadd0347435b6f46791a38a87f57553f279f439f | [GitHub](https://github.com/Xilinx/gst-plugins-bad)          | xlnx-rebase-v1.18.5_2022.1   |
| gstreamer1.0-plugins-good      | xlnx-rebase-v1.18.5   | adc0e0329d96be5a2cd7010f5b1eaccabd12ff16 | [GitHub](https://github.com/Xilinx/gst-plugins-good)         | xlnx-rebase-v1.18.5_2022.1   |
| gstreamer1.0-plugins-base      | xlnx-rebase-v1.18.5   | ce156424eb9cbb66dc1aa446c4be6372d3ff5792 | [GitHub](https://github.com/Xilinx/gst-plugins-base)         | xlnx-rebase-v1.18.5_2022.1   |
| gstreamer1.0-omx               | xlnx-rebase-v1.18.5   | 0aa11eaf4175c1731970f1c410d9857acbff65e9 | [GitHub](https://github.com/Xilinx/gst-omx)                  | xlnx-rebase-v1.18.5_2022.1   |
| gstreamer1.0                   | xlnx-rebase-v1.18.5   | e483cd3a0894f4d5270cdb80a62baf1df24ccf89 | [GitHub](https://github.com/Xilinx/gstreamer)                | xlnx-rebase-v1.18.5_2022.1   |
| xrt                            | 2022.1                | 2a6dc026480914ea1c9f02977a6ab4b57e8a3c8d | [GitHub](https://github.com/Xilinx/XRT)                      | 202210.2.13.0_PetaLinux      |
| kernel-module-dp               | xlnx_rel_v2022.1      | 9a025fdb7134a8af12de8d69f5a428c8284ae9b3 | [GitHub](https://github.com/xilinx/dp-modules)               | xilinx_v2022.1               |
| kernel-module-hdmi             | xlnx_rel_v2022.1      | 25b6fe7a26a975be15c002b48cfd4c291486491e | [GitHub](https://github.com/Xilinx/hdmi-modules)             | xilinx_v2022.1               |
| libomxil-xlnx                  | xlnx_rel_v2022.1      | b3308c608be7ed9250b9c6732f6e0a02b1a2e985 | [GitHub](https://github.com/Xilinx/vcu-omx-il)               | xilinx_v2022.1               |
| kernel-module-vcu              | xlnx_rel_v2022.1      | 9d2657550eccebccce08cacfcdd369367b9f6be4 | [GitHub](https://github.com/Xilinx/vcu-modules)              | xilinx_v2022.1               |
| libvcu-xlnx                    | xlnx_rel_v2022.1      | 5bf158af204b181f00ac009c8745557642ecfe5f | [GitHub](https://github.com/Xilinx/vcu-ctrl-sw)              | xilinx_v2022.1               |
| vcu-firmware                   | xlnx_rel_v2022.1      | 569f980527fd58f43baf16bd0b294bf8c7cdf963 | [GitHub](https://github.com/Xilinx/vcu-firmware)             | xilinx_v2022.1               |
| open-amp                       | xlnx_rel_v2022.1      | a6555a3d7b98741737c7d03b47567044cc5eb91e | [GitHub](https://github.com/Xilinx/open-amp)                 | xilinx_v2022.1               |
| libmetal                       | xlnx_rel_v2022.1      | bee059dfedcfd98d1b113d8d6cce1c8aa916ff54 | [GitHub](https://github.com/Xilinx/libmetal)                 | xilinx_v2022.1               |
| libmali-xlnx                   | xlnx_rel_v2022.1      | a1a22c9f03b20d8cb70b91727fe51c1db7f4b061 | [GitHub](https://github.com/Xilinx/mali-userspace-binaries)  | xilinx_v2022.1               |
| runx-xlnx                      | xlnx_rebase_1.1       | 0c7edb3453398d7a0c594ce026c9c1e93c2541cc | [GitHub](https://github.com/Xilinx/runx)                     | xlnx_rebase_1.1_2022.1       |
| xen                            | xlnx_rebase_4.16      | 894492ad1998fc3fe2167b23a0795a76c8b566e9 | [GitHub](https://github.com/Xilinx/xen)                      | xlnx_rebase_4.16_2022.1      |
| qemu-xilinx                    | xlnx_rel_v2022.1      | 52a9b22faeb149a6b17646b1f912f06ea6c269ca | [GitHub](https://github.com/Xilinx/qemu)                     | xilinx_v2022.1               |
| qemu-devicetrees               | xlnx_rel_v2022.1      | 0499324af1178057c3730b0989c8fb5c5bbc4cf8 | [GitHub](https://github.com/Xilinx/qemu-devicetrees)         | xilinx_v2022.1               |
| device-tree                    | xlnx_rel_v2022.1      | 1b364a44fae80fed4ea2863accc71f380b46c038 | [GitHub](https://github.com/Xilinx/device-tree-xlnx)         | xilinx_v2022.1               |
| fsbl-firmware                  | xlnx_rel_v2022.1      | b3d8b420b421730ea505da55b42174dc90f885c1 | [GitHub](https://github.com/Xilinx/embeddedsw)               | xilinx_v2022.1               |
| arm-trusted-firmware           | xlnx_rebase_v2.6      | 67ca59c67f542322554d78820bf9ddaa736d6a84 | [GitHub](https://github.com/Xilinx/arm-trusted-firmware)     | xlnx_rebase_v2.6_2022.1      |
| u-boot-xlnx                    | xlnx_rebase_v2022.01  | c50d6c48f4e1368cd38699278e35563cb4b0e444 | [GitHub](https://github.com/Xilinx/u-boot-xlnx)              | xlnx_rebase_v2022.01_2022.1  |
| linux-xlnx                     | xlnx_rebase_v5.15_LTS | b0c1be301e78c320df8c4d93b18393bfd7fd4e9d | [GitHub](https://github.com/Xilinx/linux-xlnx)               | xlnx_rebase_v5.15_LTS_2022.1 |

**2022.1 Release Notes for Open Source components wiki page:**

The below page covers details for all of the open source components changes such as New Features and Bug Fixes in a particular release.

https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/2323742945

**2022.1 New Features:**

**Yocto**

-   Yocto version upgrade to 3.4 (Honister) 
-   Deprecated usage of BOARD/BOARD\_VARIANT in favor of machine inheritance model
-   Root login and auto-login disabled by default, default user set to PetaLinux with password expiration on first login
-   systemd as default init manager on aarch64 architecture (was sysVinit)
-   python2 has been deprecated
-   microblaze\_lite template has been deprecated and renamed microblaze\_full to microblaze-generic (similar to other generic machines)
-   Versal DFX Single slot support 

**PetaLinux**

-   Auto login has been disabled
-   PetaLinux user login has been enabled and user need to set the password on the first boot
-   Root login has been disabled and if user wants root login then they need to enable debug tweaks
-   MicroBlaze lite has been removed from the tool
-   Version information added into SOM boot.bin
-   SOM builds has OpenAMP support enabled by default
-   Added VPK120 BSP with supporting both RevA and RevB boards through manual intervention
-   Added common VCK190/VMK180 BSP that works with both RevA and RevB boards through manual intervention
-   Added support for VCK190/VMK180 eMMc and OSPI boot module based BSPs with both RevA and RevB boards through manual intervention
-   PetaLinux is based on yocto honister (3.4) version
-   The default rootfs is changed to systemD for ZynqMP and Versal.
-   DFX single slot support in Versal
-   Removed board/board\_variant support and added yocto machine support
-   Zynq common tar will not have X11 package

**Linux Kernel and Drivers** 

-   Linux Kernel upgraded to 5.15
-   TTC PWM Linux driver updated to support dynamic fan control
-   Propagation of PL configuration failure errors to user space
-   XilFPGA: Replaced library specific utility functions and standard lib functions with Xilinx maintained secure functions
-   XilFPGA and Linux FPGA manager version and feature check to maintain backward compatibility for Zynq UltraScale+ MPSoC
-   FreeRTOS version upgrade to v10.4.6
-   TMR MicroBlaze experimental support at Linux for error injection, detection and reporting.
-   Dynamic SGMII configuration support for ZynqMP GEM in Linux driver
-   Optional UDP "block till sent" support for LWIP AXI Ethernet and GEM
-   New level shifter(Auto Direction) support in SD BareMetal and Linux driver
-   Erase feature support in SD/eMMC driver and xilffs library 
-   Dynamic Device Tree configuration support for ZynqMP SD Linux driver
-   SLG7XL45106 I2C GPO Linux driver support for reset expansion
-   USB2244 Linux driver support for SD over USB

**PLM**

-   EAM module in PLM updated to meet safety requirements
-   PLM error behavior updated for Slave PDIs in SSIT devices
-   Support for skipping MJTAG workaround image when boot mode is JTAG or reset reason is not ePOR
-   PLM memory footprint improvements

**Secure features**

-   XilPUF client support
-   Support extended to PLM MicroBlaze for Versal Secure libraries (XilSecure, XIlNVM, XilPUF) client side and TRNG driver
-   Library specific utility functions replaced with those of standard library functions

**ZynqMP FSBL**

-   Added support for ZCU670 boards for SPD support

**BSP, Drivers and Libraries**

-   XilPM library: ZynqMP: Added IOCTL support for dynamic feature enablement
-   XilFPGA: Replaced library specific utility functions and standard lib functions with Xilinx maintained secure functions
-   XilFPGA and Linux FPGA manager version and feature check to maintain backward compatibility for Zynq UltraScale+.
-   New level shifter(Auto Direction) support in SD BareMetal
-   Erase feature support in SD/eMMC driver and xilffs library
-   XilPM: Versal: IOCTLs for AIE/AIE2 operations required for Partition Init and Teardown
-   XilPM: Versal: Support for AIE dynamic clock frequency scaling via QoS field
-   XilPM: Versal: Client library support for PL MicroBlaze ( Limited to IOCTL APIs)
-   XilPM: Versal: IOCTL for secure register access

**PMUFW (Platform Management Unit Firmware)**

-   Updated to give/change permissions for writing another overlay config object
-   Cleanup of dynamic feature config logic to enable them only if dynamic feature config is enabled
-   Added IOCTL support for dynamic SD, GEM and USB configuration under ENABLE\_DYNAMIC\_MIO\_CONFIG macro which is disabled by default
-   Added provision in ZynqMP PMUFW to skip XFPGA\_SECURE\_MODE macro
-   Added support for feature check API
-   Implemented new API's to get XilFPGA component information
-   Provided user option to manually enable DDR XMPU settings using ENABLE\_DDR\_XMPU macro which is disabled by default

**Secure Libraries and Drivers**

-   Refer to Secure Features section
    

**U-Boot**

-   U-Boot upgraded to mainline 2022.01 Version
-   Added ZynqMP pinctrl driver
-   Added ZynqMP GPIO modepin driver
-   Added support for slg7xl45106 i2c GPO expander
-   Added power domain driver to load dynamic PMU config object
-   Added USB2244 USB driver(SD over USB)
-   Added USB5744 USB driver(USB hub reset)
-   Dynamic SD configuration support
-   Support to read MAC address from Multirecord FRU data
-   Added support to read ethernet-phy-id from PHY node and reset the PHY with GPIO

**DTG**

-   Auto generation of AIE clock information
-   DFX single slot support in Versal

**ATF**

-   TF-A upgraded to upstream v2.6 version
-   Disabled the -mbranch-protection flag as this was causing the TF-A size increase with new GCC 11.2 version
-   Added multiple irq handler support in Versal
-   Common callback type used for core and subsystem for Versal
-   Added support to get the xilfpga component info in ZynqMP
-   Added common interfaces to handle EEMI commands in Versal
-   Added support to parse module id from EEMI API ID in Versal
-   Enhanced PM\_IOCTL EEMI API to support additional arguments in Versal
-   Added support to use common interface for EEMI APIs in ZynqMP
-   Added support for the ProvenCore Secure OS in ZynqMP

**AI Engine (AIE)**

-   SYSFS updated for FIFO counter
-   Dynamic Clock Frequency 
-   Baremetal Error handling

**OpenAMP**

-   SOM support - install apps from DNF, use remoteproc and rpmsg
-   More comprehensive support of OCM and TCM memory banks in kernel driver from perspective of powering up required power islands
-   Upgraded to 2021.10 upstream openamp and libmetal

**QEMU**

-   Updated to 6.1.0 QEMU version 
-   WDT support in Zynq UltraScale+ MPSoC
-   Vitis AIE/AIE2 NPI forwarding support in Versal 
-   Bitstream loading 

**Xen/Containers**

-   Xen updated to 4.16, the latest upstream Xen release
-   PV Drivers support for Dom0less VMs
-   Plain Share memory and event channels for VM-to-VM communication
-   Dynamic FPGA assignment to running VMs
    -   Program an FPGA bitstream at runtime, then assign the new hardware resources to any VM, new or already running
-   Out of the box device assignment configurations

**Platform Management**

-   EEMI API runtime decoupling - clients can query whether a firmware API is supported or not and then use the API or gracefully fail
-   Versal: AIE runtime clock frequency scaling  - Client(Linux AIE driver) can get/set the QoS ( divider value) for AIE Array
-   Versal: IOCTLs for AIE/AIE2 operations required for Partition Init and Teardown
-   Versal: XilPM client library support for PL MicroBlaze ( Limited to IOCTL APIs)
-   Versal: IOCTL for secure register access
-   ZU+: Extend PMU configuration object for dynamic enablement of board specific features (OT and external WDT)
-   ZU+: PMU Configuration Object Dynamic Loading
-   ZU+: Support for dynamic MIO config across the stack (PMUFW, ATF, Linux Firmware Driver)

**Multimedia**

-   Updated V4l2, PS DP DRM and VCU kernel driver SW to support 5.15 Linux kernel
-   GStreamer xilinx repos are rebased to support v1.18.5
-   Dmafd support for VCU Encoder output.
-   YUV444 support for encoder and decoder using Xilinx custom solution.
-   Added support for 44.1k & 48k sampled rate audio for PS DisplayPort with proper channel status settings as per IEC60958. Moved DisplayPort audio registers to separate node in Device Tree to handle this.
-   Moved VCU encoder/decoder clk setting to vcu-modues because as per upstream commit a2fe7, xlnx\_vcu driver is just a clock controller driver which provides clocks that can be used by driver/s for the enc/dec units. Also updated VCU DT node with updated clk name sequence and index as per upstream driver.

**XilSEM**

-   New user interfaces: to read total number of frames, golden SHA in NPI descriptors, total number of descriptors in NPI scan, FRAME ECC & CRC in CRAM, read XilSEM configuration that was done through CIPS
-   CRAM error injection at startup making sure that no latent faults in the CRAM ECC checker
-   Self-checks in NPI scan to make sure: scanning is done all descriptors and no descriptor is missed out, the time taken for NPI scan is within the budgeted time
-   Correction of CRAM errors, if any, before partial reconfiguration
-   Miscellaneous
    -   Runtime checks if CRAM/NPI scan is enabled in the design
    -   Validation of user-specified NPI scan frequency (valid range: 80 to 1000ms)
    -   Removed PSM RAM dependency during descriptor processing
    -   Replace standard library functions
    -   Improve NPI scan error log
    -   Separate events for error notification

## GPU MALI-400

-   Mali Kernel driver rebased to support Linux kernel v5.15

## **Open Source components New Features**

-   Open Source component features are in [https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/2323742945](https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/2323742945)

**2022.1 Bug Fixes**

**PetaLinux** **Bug Fixes:**

| Components    | Features                                                  | Description                                                  |
| ------------- | --------------------------------------------------------- | ------------------------------------------------------------ |
| **PetaLinux** | **Document Update**                                       | PetaLinux User Guide UG1145 has been updated to remove the explanation for the command `petalinux-config -c bootloader`. In older tool flows, the `devtool` flow was used for `petalinux-config` to get FSBL source code. From 2021.x onwards, bitbake is used and FSBL source can be obtained using: `petalinux-devtool modify fsbl`. |
| **PetaLinux** | **MicroBlaze**                                            | For the MicroBlaze use case, JTAG boot with INITRAMFS was not working. When moving to distro boot support for MicroBlaze, the tool added `boot.scr` for INITRAMFS, which used `linux.bin.ub`, causing boot failure as it is not an ELF file. To resolve this, the tool now skips `boot.scr` when INITRAMFS is used. |
| **PetaLinux** | **Zynq-7000, Zynq UltraScale+ MPSoC, Versal**             | The `petalinux-package` command always packaged the bitstream when `petalinux-package --boot --u-boot` was used. This forced customers to pack the bitstream in `boot.bin`. Customers who wanted to load the bitstream from U-Boot can now do so using:<br>`petalinux-package --boot --fpga --bitstream` |
| **PetaLinux** | **Document Update**                                       | In the PetaLinux User Guide UG1144, the QSPI/OSPI U-Boot offsets were incorrectly referred to as load addresses, leading to confusion with DDR addresses. The document has been updated to refer to them correctly as **offsets**. |
| **PetaLinux** | **Document Update**                                       | If there was a mismatch between QSPI/OSPI offsets in `petalinux-config → u-boot configuration` and `petalinux-config -c subsystem auto hardware settings → flash settings`, boot would fail. The PetaLinux User Guide UG1144 has been updated to explain these configurations. |
| **PetaLinux** | **MicroBlaze, Zynq-7000, Zynq UltraScale+ MPSoC, Versal** | As Xilinx-provided board firmware did not include NTP by default, users accessing HTTPS or SSL-enabled sites could encounter errors due to incorrect system dates. NTP support has now been added by default to the rootfs. |

**VCU Bug Fixes:**

-   Memory leak issue observed with GStreamer based low-latency VCU pipelines has been fixed
-   Reset has to released for DisplayPort before accessing DisplayPort registers. Accessing DisplayPort registers without releasing the reset can make the system hang

**Open Source components Bug Fixes:**

-   Open Source component bug fixed are in [https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/2323742945](https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/2323742945)

**Known Issues for 2022.1:**

| Linux/Baremetal     | Components          | Work-around Article Description and Link                     | To be fixed version |
| ------------------- | ------------------- | ------------------------------------------------------------ | ------------------- |
| Linux               | VCU                 | 2022.1 Zynq UltraScale+ MPSoC VCU TRD - Why is audio loss/distortion observed in serial/streaming pipelines during long run? | 2022.2              |
| Linux               | VCU                 | 2022.1 Zynq UltraScale+ MPSoC VCU TRD - SIGINT (Ctrl+C) does not work while killing low-latency or Xilinx low-latency pipeline | 2022.2              |
| Linux               | VCU                 | 2022.1 Zynq UltraScale+ MPSoC VCU TRD - FPS drop observed with Xilinx Low-Latency for 2 streams of 4kp30 AVC serial use-case | 2022.2              |
| Linux & Baremetal   | Platform Management | Versal - Vivado 2021.2: Exception while accessing the DDR Memory Controller (DDRMC) when hardware design has only one DDRMC | 2022.2              |
| Linux & Baremetal   | Platform Management | Versal Premium - Version 2021.2 - QSPI Controller clock disabled by PLM post QSPI boot | 2022.2              |
| Linux               | U-Boot              | 2021.2 MicroBlaze Spartan-7 SP701: Erase operation failed while booting from QSPI flash for SP701 BSP | 2022.2              |
| Linux               | QEMU                | Versal QEMU: BURST fails when executing advanced SIMD instructions | 2023.1              |
| Linux               | PetaLinux           | 2022.1 PetaLinux: DTG overrides the DFX partial DTSI firmware-name set from Yocto YAML configuration | 2022.2              |
| Linux               | PetaLinux           | 2022.1 PetaLinux: User layer path limitation in PetaLinux tool | 2022.2              |
| Linux               | DTG                 | 2022.1 Versal: DTG incorrect `gpio-cells` value generated in DFX flow if XSCT is used to generate the dtsi | 2022.2              |
| Linux               | Drivers             | 2022.1 Zynq UltraScale+ MPSoC: PetaLinux syntax error in pl.dtsi when there are multiple Ethernet IPs present in the design | 2022.2              |
| Linux               | DTG                 | 2022.1 Zynq/ZynqMP/Versal: PetaLinux ttc0 status is currently "disabled" instead of "okay" by default | 2022.2              |
| Linux               | Drivers             | 2021.2 Zynq UltraScale+ MPSoC TSN: Traffic drops for board-to-board connection with large number of packets | 2022.2              |
| Linux               | Drivers             | 2022.1 Zynq UltraScale+ MPSoC: Dynamic loading of TSN drivers causing stack trace errors | 2022.2              |
| Linux               | Drivers             | 2021.1 Zynq UltraScale+ MPSoC: TSN Qbv OOB app on ZCU102 results in kernel panic (system deadlocked on memory) | 2022.2              |
| Linux               | Drivers             | 2021.2/2022.1 Zynq UltraScale+ MPSoC: Issue with Linux Suspend Resume Wake-on-LAN test fails on ZCU102 with SMMU | 2022.2              |
| Linux               | Yocto, PetaLinux    | 2022.X PetaLinux: How to find the exact PetaLinux build used | -                   |
| Linux and Baremetal | Platform Management | 2022.1 PetaLinux: `rst -proc` from xsdb clears AXI RD/WR protection registers in LPD_IOU_SECURE_SLCR and PMC_IOU_SECURE_SLCR | 2022.2              |
| Baremetal           | AI Engine           | AI Engine driver is coupled with PLM version from 2022.1     | 2022.2              |
| Xen Hypervisor      |                     | 000034059 - 2022.1 PetaLinux: SMMU error seen on guests using passthrough devices | 2022.2              |
| Linux               | U-Boot              | 000034058 - 2022.1 PetaLinux: Subsystem reboot test fails for Zynq MP boards due to failure to start USB after reboot | 2022.2              |
| Linux               | Platform Management | 2022.1 PetaLinux: Random hang observed on Versal boards during multiple subsystem restarts | 2022.2              |
| Linux               | AI Engine           | 000034050 - 2022.1 AI Engine: Compilation errors in `drivers/misc/xilinx-ai-engine/ai-engine-sysfs-event.c` | 2022.2              |
| Baremetal           | Drivers             | 000034069 - 2022.1 Baremetal: SysMonPsv MicroBlaze compilation issue | 2022.2              |
| Baremetal/FreeRTOS  | Libraries           | 000034049 - 2022.1 FreeRTOS: GIC re-initialization fails on Versal A72 FreeRTOS-based applications | 2022.2              |
| Baremetal           | PLM                 | 000034048 - 2022.1 Versal: PLM exception when DDR calibration fails on a board with less than four physical DDRs | 2022.2              |
| Baremetal           | FSBL                | 000034057 - 2022.1 PetaLinux: FSBL build fails when `XFSBL_ENABLE_DDR_SR` is enabled in the FSBL | 2022.2              |

# README_content_v2022_1.txt

=============================

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2022.1 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2022.1 Open Components Source Code (TAR/GZIP) file: 
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

# 2022.1_PetaLinux_Package_List.xlsx

## Linux Distribution OS details:

1. RHEL 7.4, 7.5, 7.6 ,7.7, 7.8, 7.9, 8.1 , 8.2, 8.3 , 8.4 and 8.5 Server:  Infrastructure Server
2. RHEL 7.4, 7.5, 7.6 , 7.7, 7.8, 7.9 , 8.1,8.2, 8.3, 8.4 and 8.5 Desktop : Development and Creative workstation.
3. CentOS 7.4, 7.5, 7.6,7.7, 7.8 and 7.9 Server (From Everything.ISO): Infrastructure server.
4. CentOS 7.4, 7.5, 7.6 ,7.7, 7.8 and  7.9  Desktop (From Everything.ISO): Development and Creative workstation.
5. Ubuntu 18.04.01, 18.04.02, 18.04.03, 18.04.04, 18.04.05, 20.04,20.04.1, 20.04.2 and Ubuntu 20.04.3 Desktop.
6. Ubuntu 18.04.01, 18.04.02, 18.04.03, 18.04.04, 18.04.05, 20.04, 20.04.1, 20.04.2  and Ubuntu 20.04.3 Server.
7. SUSE 15.2 Server (From Everything.ISO): Infrastructure server
8. SUSE 15.2 Desktop (From Everything.ISO): Development and Creative workstation.

### Note: 

1. Empty packages are not installed means assuming these are default from Linux Distribution.
2. For RHEL/CentOS/Suse you need to installGitPython and jinja2 using pip3 commands as mentioned below.

### Host GCC Version Upgrade:

From 2021.1 release, the gcc version should be greater than 6. Using lower versions of gcc causes build issues. You can also enable the Enable buildtools extended option from petalinux -config → Yocto settings, which uses the pre-compiled gcc binaries from the PetaLinux tool.  

## Quick Installation steps for packages

### RHEL and CentOS Desktop/Server 64-bit

```
su yum install net-tools gawk make wget tar bzip2 gzip python3 unzip perl patch diffutils diffstat git cpp gcc gcc-c++ glibc-devel texinfo chrpath socat perl-Data-Dumper perl-Text-ParseWords perl-Thread-Queue python3-pip python3-GitPython python3-jinja2 python3-pexpect xz which SDL-devel xterm autoconf libtool.x86_64 zlib-devel automake glib2-devel zlib ncurses-devel openssl-devel dos2unix flex bison glibc.i686 glibc.x86_64 screen pax glibc-devel.i686 compat-libstdc++-33.i686 libstdc++.i686 libstdc++.x86_64
pip3 install GitPython jinja2
```

### Ubuntu Desktop/Server 64-bit

```
sudo apt-get install iproute2 gawk python3 python build-essential gcc git make net-tools libncurses5-dev tftpd zlib1g-dev libssl-dev flex bison libselinux1 gnupg wget git-core diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib automake zlib1g:i386 screen pax gzip cpio python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3
```

## Tool/Library Versions

### RHEL/CentOS/SUSE Versions

| Tool/Library                                    | Red Hat Enterprise Destop/Server  7.5(64-bit) | Red Hat Enterprise Desktop/Server  7.8(64-bit) | Red Hat Enterprise Desktop/Server  7.9(64-bit) | Red Hat Enterprise Desktop/Server  8.1(64-bit) | Red Hat Enterprise Desktop/Server  8.2(64-bit) | Red Hat Enterprise Desktop/Server  8.3(64-bit) | Red Hat Enterprise Desktop/Server  8.4(64-bit) | Red Hat Enterprise Desktop/Server  8.5(64-bit) | CentOS Desktop/Server 7.4  (64-bit)        | CentOS Desktop/Server 7.5  (64-bit)        | CentOS Desktop/Server 7.6  (64-bit)        | CentOS Desktop/Server 7.7  (64-bit)        | CentOS Desktop/Server 7.8  (64-bit)        | CentOS Desktop/Server 7.9  (64-bit)        | Suse Desktop /Server 15.2(64-bit)       |
| ----------------------------------------------- | --------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | --------------------------------------- |
| ip (iproute)                                    | iproute-4.11.0-14.el7.x86_64                  | iproute-4.11.0-25.el7_7.2.x86_64               | iproute-4.11.0-25.el7_7.2.x86_64               | iproute-4.18.0-15.el8_7.2.x86_64               | iproute-5.3.0-1.el8                            | iproute-5.3.0-1.el8                            | iproute-5.9.0-4.el8                            | iproute-5.3.0-1.el8                            | iproute-3.10.0-87.el7.x86_64               | iproute-4.11.0-14.el7.x86_64               | iproute-4.11.0-14.el7.x86_64               | iproute-4.11.0-25.el7_7.2.x86_64           | iproute-4.11.0-25.el7_7.2.x86_64           | iproute-4.11.0-25.el7_7.2.x86_64           | iproute2-5.3-5.2.1.x86_64               |
| gawk                                            | gawk-4.0.2-4.el7_3.1.x86_64                   | gawk-4.0.2-4.el7_3.1.x86_64                    | gawk-4.0.2-4.el7_3.1.x86_64                    | gawk-4.2.1-1.el8.x86_64                        | gawk-4.2.1-1.el8                               | gawk-4.2.1-1.el8                               | gawk-4.2.1-2.el8                               | gawk-.2.1-2.el8                                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.2.1-1.41.x86_64                  |
| gcc                                             | gcc-4.8.5-44.el7_4.1.x86_64                   | gcc-4.8.5-44.el7_4.1.x86_64                    | gcc-4.8.5-44.el7_4.1.x86_64                    | gcc-8.5.0-4.el8_5                              | gcc-8.5.0-4.el8_5                              | gcc-8.5.0-4.el8_5                              | gcc-8.5.0-4.el8_5                              | gcc-8.5.0-4.el8_5                              | gcc-4.8.5-44.el7_4.1.x86_64                | gcc-4.8.5-44.el7_4.1.x86_64                | gcc-4.8.5-44.el7_4.1.x86_64                | gcc-4.8.5-44.el7_4.1.x86_64                | gcc-4.8.5-44.el7_4.1.x86_64                | gcc-4.8.5-44.el7_4.1.x86_64                | gcc7-7.5.0+r278197-4.30.1               |
| netstat (net-tools)                             | net-tools-2.0-0.22.20131004git.el7.x86_64     | net-tools-2.0-0.25.20131004git.el7.x86_64      | net-tools-2.0-0.25.20131004git.el7.x86_64      | net-tools-2.0-0.51.20160912git.el8.x86_64      | net-tools-2.0-0.51.20160912git.el8.x86_65      | net-tools-2.0-0.51.20160912git.el8.x86_65      | net-tools-2.0-0.52.20160912git.el8             | net-tools-2.0-0.51.20160912git.el8.x86_65      | net-tools-2.0-0.22.20131004git.el7.x86_64  | net-tools-2.0-0.22.20131004git.el7.x86_64  | net-tools-2.0-0.24.20131004git.el7.x86_64  | net-tools-2.0-0.25.20131004git.el7.x86_64  | net-tools-2.0-0.25.20131004git.el7.x86_64  | net-tools-2.0-0.25.20131004git.el7.x86_64  | net-tools-2.0+git20170221.479bb4a-3.11  |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-5.9-14.20130511.el7_4.x86_64    | ncurses-devel-5.9-14.20130511.el7_4.x86_64     | ncurses-devel-5.9-14.20130511.el7_4.x86_64     | ncurses-devel-6.1-7.20180224.el8.x86_64        | ncurses-devel-6.1-7.20180224.el8.x86_65        | ncurses-devel-6.1-9.20180224.el8               | ncurses-devel-6.1-9.20180224.el8               | ncurses-devel-6.1-9.20180224.el8               | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-6.1-5.9.1.x86_64          |
| zlib-devel(also,install 32-bit of this version) | zlib-devel-1.2.7-19.el7.x86_64                | zlib-devel-1.2.7-19.el7.x86_64                 | zlib-devel-1.2.7-18.el7.x86_64                 | zlib-devel-1.2.11-17.el8.x86_64                | zlib-devel-1.2.11-17.el8.x86_65                | zlib-devel-1.2.11-17.el8.x86_65                | zlib-devel-1.2.11-17.el8.x86_65                | zlib-devel-1.2.11-17.el8.x86_65                | zlib-devel-1.2.7-19.el7.x86_64             | zlib-devel-1.2.7-19.el7_9                  | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-19.el7.x86_64             | zlib-devel-1.2.11-3.24.1.x86_64         |
| openssl-devel                                   | openssl-devel-1.0.2k-19.el7.x86_64            | openssl-devel-1.0.2k-19.el7.x86_64             | openssl-devel-1.0.2k-19.el7.x86_64             | openssl-devel-1.1.1.1c-2.el8.x86_64            | openssl-devel-1.0.2k-19.el7.x86_65             | openssl-devel-1.0.2k-19.el7.x86_65             | openssl-devel-1.0.2k-19.el7.x86_65             | openssl-devel-1.0.2k-19.el7.x86_65             | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-1_1-1.1.1d-11.23.1.x86_64       |
| flex                                            | flex-2.5.37-3.el7.x86_64                      | flex-2.5.37-6.el7.x86_64                       | flex-2.5.37-6.el7.x86_64                       | flex-2.5.37-6.el7.x86_64                       | flex-2.5.37-6.el7.x86_65                       | flex-2.5.37-6.el7.x86_65                       | flex-2.5.37-6.el7.x86_65                       | flex-2.5.37-6.el7.x86_65                       | flex-2.5.37-3.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-3.el7.x86_64                   | NA                                      |
| bison                                           | bison-3.0.4-1.el7.x86_64                      | bison-3.0.4-1.el7.x86_64                       | bison-3.0.4-1.el7.x86_64                       | bison-3.0.4-1.el7.x86_64                       | bison-3.0.4-1.el7.x86_65                       | bison-3.0.4-1.el7.x86_65                       | bison-3.0.4-1.el7.x86_65                       | bison-3.0.4-1.el7.x86_65                       | bison-3.0.4-1.el7.x86_64                   | bison-3.0.4-2.el7.x86_64                   | bison-3.0.4-1.el7.x86_64                   | bison-3.0.4-1.el7.x86_64                   | bison-3.0.4-1.el7.x86_64                   | bison-3.0.4-2.el7.x86_64                   | NA                                      |
| libselinux                                      | libselinux-2.5-12.1.el7.x86_64                | libselinux-2.5-15.1.el7.x86_64                 | libselinux-2.5-14.1.el7.x86_64                 | libselinux-2.9-2.el8.x86_64                    | libselinux-2.9-3.el8.x86_65                    | libselinux-2.9-4.el8_3                         | libselinux-2.9-5.el8                           | libselinux-2.9-5.el8                           | libselinux-2.5-11.el7.x86_64               | libselinux-2.5-12.1.el7.x86_64             | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.5-14.el7.x86_64               | libselinux-2.5-15.el7.x86_64               | NA                                      |
| xterm                                           | xterm-295-3.el7.x86_64                        | xterm-295-3.el7.x86_64                         | xterm-295-3.el7.x86_64                         | xterm-331-1.el8_3.2.x86_64                     | xterm-331-1.el8_3.2.x86_65                     | xterm-331-1.el8_3.2.x86_65                     | xterm-331-1.el8_3.2.x86_65                     | xterm-331-1.el8_3.2.x86_65                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-330-11.3.1.x86_64                 |
| autoconf                                        | autoconf-2.69-11.el7.noarch                   | autoconf-2.69-11.el7.noarch                    | autoconf-2.69-11.el7.noarch                    | autoconf-2.69-27.el8.noarch                    | autoconf-2.69-27.el8.noarch                    | autoconf-2.69-29.el8                           | autoconf-2.69-29.el8                           | autoconf-2.69-29.el8                           | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-1.445.noarch              |
| libtool                                         | libtool-2.4.2-22.el7_3.x86_64                 | libtool-2.4.2-22.el7_3.x86_64                  | libtool-2.4.2-22.el7_3.x86_64                  | libtool-2.4.6-25.el8.x86_64                    | libtool-2.4.6-25.el8.x86_65                    | libtool-2.4.6-25.el8.x86_65                    | libtool-2.4.6-25.el8.x86_65                    | libtool-2.4.6-25.el8.x86_65                    | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.6-3.4.1.x86_64              |
| texinfo                                         | texinfo-5.1-5.el7.x86_64                      | texinfo-5.1-5.el7.x86_64                       | texinfo-5.1-5.el7.x86_64                       | texinfo-5.1-5.el7.x86_64                       | texinfo-5.1-5.el7.x86_65                       | texinfo-5.1-5.el7.x86_65                       | texinfo-5.1-5.el7.x86_65                       | texinfo-5.1-5.el7.x86_65                       | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-6.5-4.17.x86_64                 |
| zlib1g-dev                                      | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| gcc-multilib                                    | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| build-essential                                 | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| SDL-devel                                       | SDL-devel-1.2.15-14.el7.x86_64                | SDL-devel-1.2.15-14.el7.x86_64                 | SDL-devel-1.2.15-14.el7.x86_64                 | SDL-devel-1.2.15-14.el7.x86_64                 | SDL-devel-1.2.15-14.el7.x86_65                 | SDL-devel-1.2.15-14.el7.x86_65                 | SDL-devel-1.2.15-14.el7.x86_65                 | SDL-devel-1.2.15-14.el7.x86_65                 | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-1.2.15-37.el8.x86_64                   |                                         |
| glibc-devel                                     | glibc-devel-2.17-325.el7.x86_64               | glibc-devel-2.17-325.el7_9                     | glibc-devel-2.17-325.el7_9                     | glibc-devel-2.28-72.el8.x86_64                 | glibc-devel-2.28-101.el8.x86_65                | glibc-devel-2.28-101.el8.x86_65                | glibc-devel-2.28-151.el8                       | glibc-devel-2.28-164.el8                       | glibc-devel-2.17-324.el7.x86_64            | glibc-devel-2.17-325.el7_9                 | glibc-devel-2.17-324.el7.x86_64            | glibc-devel-2.17-325.el7_9                 | glibc-devel-2.17-325.el7_9                 | glibc-devel-2.17-325.el7_9                 | glibc-devel-2.26-13.62.1.x86_64         |
| glib2-devel                                     | glib2-devel-2.54.2-2.el7.x86_64               | glib2-devel-2.56.1-5.el7.x86_64                | glib2-devel-2.56.1-5.el7.x86_64                | glib2-devel-2.56.4-7.el8.x86_64                | glib2-devel-2.56.1-5.el7.x86_65                | glib2-devel-2.56.1-5.el7.x86_65                | glib2-devel-2.28-151.el8                       | glib2-devel-2.28-164.el8                       | glib2-devel-2.56.1-9.el7.x86_64            | glib2-devel-2.56.1-9.el7.x86_64            | glib2-devel-2.56.1-9.el7.x86_64            | glib2-devel-2.56.1-9.el7.x86_64            | glib2-devel-2.56.1-9.el7.x86_64            | glib2-devel-2.56.1-9.el7.x86_64            | glib2-devel-2.62.6-3.6.1.x86_64         |
| automake                                        | automake-1.13.4-3.el7.noarch                  | automake-1.13.4-3.el7.noarch                   | automake-1.13.4-3.el7.noarch                   | automake-1.16.1-7.el8.noarch                   | automake-1.16.1-7.el8.noarch                   | automake-1.16.1-7.el8.noarch                   | automake-1.16.1-7.el8.noarch                   | automake-1.16.1-7.el8.noarch                   | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.15.1-4.10.2.noarch           |
| screen                                          | gnome-screenshot-3.22.0-1.el7.x86_64          | gnome-screenshot-3.22.0-1.el7.x86_64           | gnome-screenshot-3.22.0-1.el7.x86_64           | pax-3.4-19.el7.x86_64                          | pax-3.4-19.el7.x86_65                          | pax-3.4-19.el7.x86_65                          | pax-3.4-19.el7.x86_65                          | pax-3.4-19.el7.x86_65                          | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_65       | screen-4.6.2-5.3.1.x86_64               |
| pax                                             | pax-3.4-19.el7.x86_64                         | pax-3.4-19.el7.x86_64                          | pax-3.4-19.el7.x86_64                          | libstdc++-8.3.1-4.5.el8.x86_64                 | libstdc++-8.3.1-5.el8                          | libstdc++-8.3.1-5.el8                          | libstdc++-8.3.1-5.el8                          | libstdc++-8.5.0-4.el8_5                        | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_65                      | pax                                     |
| libstdc++                                       | libstdc++-4.8.5-28.el7.x86_64                 | libstdc++-4.8.5-39.el7.x86_64                  | libstdc++-4.8.5-44.el7.x86_64                  | gcc-8.5.0-4.el8_5                              | gcc-8.5.0-4.el8_5                              | gcc-8.5.0-4.el8_5                              | gcc-8.5.0-4.el8_5                              | gcc-8.5.0-4.el8_5                              | libstdc++-4.8.5-44.el7.x86_64              | libstdc++-4.8.5-44.el7.x86_64              | libstdc++-4.8.5-44.el7.x86_64              | libstdc++-4.8.5-44.el7.x86_64              | libstdc++-4.8.5-39.el7                     | libstdc++-4.8.5-44.el7.x86_64              | libstdc++-7-7.5.0+r278197-4.30.1.x86_64 |
| g++ (gcc-c++)                                   | gcc-c++-4.8.5-44.el7.x86_64                   | gcc-c++-4.8.5-44.el7.x86_64                    | gcc-c++-4.8.5-44.el7.x86_64                    | gcc-c++-8.3.1-4.el8.x86_64                     | gcc-c++-8.4.1-1.el8.x86_65                     | gcc-c++-8.4.1-1.el8.x86_65                     | gcc-c++-8.4.1-1.el8.x86_65                     | gcc-c++-8.4.1-1.el8.x86_65                     | gcc-c++-4.8.5-16.el7_4.1.x86_64            | gcc-c++-4.8.5-44.el7_4.1.x86_64            | gcc-c++-4.8.5-44.el7_4.1.x86_64            | gcc-c++-4.8.5-44.el7_4.1.x86_64            | gcc-c++-4.8.5-44.el7_4.1.x86_64            | gcc-c++-4.8.5-44.el7_4.1.x86_64            | g++                                     |
| python3-pip                                     | python3-pip-9.0.3-8.el7                       | python3-pip-9.0.3-8.el7                        | python3-pip-9.0.3-8.el7                        | python3-pip-9.0.3-20.el8                       | python3-pip-9.0.3-20.el8                       | python3-pip-9.0.3-20.el8                       | python3-pip-9.0.3-20.el8                       | python3-pip-9.0.3-20.el8                       | python34-pip-8.1.2-10.el7.noarch           | python3-pip-9.0.3-8.el7                    | python3-pip-9.0.3-8.el7                    | python3-pip-9.0.3-8.el7                    | python3-pip-9.0.3-8.el7                    | python3-pip-9.0.3-8.el7                    | python3-3.6.15-3.91.4.x86_64            |
| perl-dat-dumper                                 | perl-dat-dumper-2.145-3.el7.x86_64            | perl-dat-dumper-2.145-3.el7.x86_64             | perl-dat-dumper-2.145-3.el7.x86_64             | perl-dat-dumper-2.167-399.el8                  | perl-dat-dumper-2.167-399.el8                  | perl-dat-dumper-2.167-399.el8                  | perl-dat-dumper-2.167-399.el8                  | perl-dat-dumper-2.167-399.el8                  | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper                         |
| perl-thread-queue                               | perl-thread-queue-3.02-2.el7.noarch           | perl-thread-queue-3.02-2.el7.noarch            | perl-thread-queue-3.02-2.el7.noarch            | perl-thread-queue-3.13-1.el8                   | perl-thread-queue-3.13-1.el8                   | perl-thread-queue-3.13-1.el8                   | perl-thread-queue-3.13-1.el8                   | perl-thread-queue-3.13-1.el8                   | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue                       |
| perl-Text-ParseWords                            | perl-Text-ParseWords-3.29-4.el7.noarch        | perl-Text-ParseWords-3.29-4.el7.noarch         | perl-Text-ParseWords-3.29-4.el7.noarch         | perl-Text-ParseWords-3.30-395.el8              | perl-Text-ParseWords-3.30-395.el8              | perl-Text-ParseWords-3.30-395.el8              | perl-Text-ParseWords-3.30-395.el8              | perl-Text-ParseWords-3.30-395.el8              | NA                                         | perl-Text-ParseWords-3.29-4.el7.noarch     | perl-Text-ParseWords-3.29-4.el7.noarch     | perl-Text-ParseWords-3.29-4.el7.noarch     | perl-Text-ParseWords-3.29-4.el7.noarch     | perl-Text-ParseWords-3.29-4.el7.noarch     | perl-Text-ParseWords                    |
| xz(xz-utils)                                    | xz-5.2.2-1.el7.x86_64                         | xz-5.2.2-1.el7.x86_64                          | xz-5.2.2-1.el7.x86_64                          | xz-5.2.4-3.el8.x86_64                          | xz-5.2.4-3.el8                                 | xz-5.2.4-3.el8                                 | xz-5.2.4-3.el8                                 | xz-5.2.4-3.el8                                 | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_65                      | xz-5.2.3-4.3.1.x86_64                   |
| perl                                            | perl-5.16.3-292.el7.x86_64                    | perl-4:5.16.3-299.el7_9                        | perl-4:5.16.3-299.el7_9                        | perl-5.16.3-292.el7.x86_64                     | perl-5.16.3-292.el7.x86_64                     | perl-4:5.26.3-420.el8                          | perl-5.16.3-292.el7.x86_64                     | perl-5.16.3-292.el7.x86_64                     | perl-5.16.3-292.el7.x86_64                 | perl-4:5.16.3-299.el7_9                    | perl-4:5.16.3-299.el7_9                    | perl-5.16.3-292.el7.x86_64                 | perl-4:5.16.3-299.el7_9                    | perl-4:5.16.3-299.el7_9                    | perl-5.26.1-7.12.1.x86_64               |
| cpp                                             | cpp-4.8.5-44.el7_4.1.x86_64                   | cpp-4.8.5-44.el7_4.1.x86_64                    | cpp-4.8.5-44.el7_4.1.x86_64                    | cpp-8.5.0-4.el8_5                              | cpp-8.5.0-4.el8_5                              | cpp-8.5.0-4.el8_5                              | cpp-8.5.0-4.el8_5                              | cpp-8.5.0-4.el8_5                              | cpp-4.8.5-44.el7.x86_64                    | cpp-4.8.5-44.el7.x86_64                    | cpp-4.8.5-44.el7.x86_64                    | cpp-4.8.5-44.el7.x86_64                    | cpp-4.8.5-44.el7.x86_64                    | cpp-4.8.5-44.el7.x86_64                    | cpp7-7.5.0+r278197-4.30.1.x86_64        |
| patch                                           | patch-2.7.1-8.el7.x86_64                      | patch-2.7.1-8.el7.x86_64                       | patch-2.7.1-8.el7.x86_64                       | patch-1.21-2.el8.x86_64                        | patch-2.7.1-8.el7.x86_64                       | patch-2.7.1-8.el7.x86_64                       | patch-2.7.1-8.el7.x86_64                       | patch-2.7.1-8.el7.x86_64                       | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_65                  | patch                                   |
| python3- GitPython(python3-git)                 | python3-GitPython                             | python3-GitPython                              | python3-GitPython                              | python3-GitPython                              | python3-GitPython                              | python3-GitPython                              | python3-GitPython                              | python3-GitPython                              | python3-GitPython                          | python3-GitPython                          | python3-GitPython                          | python3-GitPython                          | python3-GitPython                          | python3-GitPython                          | python3-git                             |
| python3-jinja2                                  | python3-jinja2                                | python3-jinja2                                 | python3-jinja3                                 | python3-jinja4                                 | python3-jinja2-2.10.1-2.el8_0                  | python3-jinja2-2.10.1-2.el8_0                  | python3-jinja2-2.10.1-2.el8_0                  | python3-jinja2-2.10.1-2.el8_0                  | python3-jinja2                             | python3-jinja2                             | python3-jinja2                             | python3-jinja2                             | python-jinja2                              | python-jinja2                              | python3-jinja2                          |
| python3-pexpect                                 | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| diffutils                                       | diffutils-3.3-4.el7.x86_64                    | diffutils-3.3-5.el7.x86_64                     | diffutils-3.3-5.el7.x86_64                     | diffutils-3.6-5.el7.x86_64                     | diffutils-3.6-6.el8                            | diffutils-3.6-6.el8                            | diffutils-3.6-6.el8                            | diffutils-3.6-6.el8                            | diffutils-3.3-4.el7.x86_64                 | diffutils-3.3-4.el7.x86_64                 | diffutils-3.3-4.el7.x86_64                 | diffutils-3.3-5.el7.x86_64                 | diffutils-3.3-5.el7.x86_64                 | diffutils-3.3-5.el7.x86_64                 | diffutils-3.6-4.3.1.x86_64              |
| ccache                                          | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| which                                           | which-2.20-7.el7.x86_64                       | which-2.20-7.el7.x86_64                        | which-2.20-7.el7.x86_65                        | which-2.21-10.el8.x86_66                       | which-2.21-12.el8                              | which-2.21-12.el8                              | which-2.21-12.el8                              | which-2.21-16.el8                              | which-2.20-7.el7.x86_64                    | which-2.20-7.el7.x86_64                    | which-2.20-7.el7.x86_64                    | which-2.20-7.el7.x86_64                    | which-2.20-7.el7.x86_64                    | which-2.20-7.el7.x86_65                    | which-2.21-2.20.x86_64                  |
| debianutils                                     | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| iputils-ping                                    | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| libegl1-mesa                                    | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| libsdl1.2-dev                                   | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| pylint3                                         | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| python3                                         | python3-3.6.8-13.el7.x86_64                   | python3-3.6.8-18.el7.x86_64                    | python3-3.6.8-18.el7.x86_64                    | python3-3.6.8-18.el7.x86_64                    | python3-3.6.8-18.el7.x86_64                    | python3-3.6.8-18.el7.x86_64                    | python3-3.6.8-18.el7.x86_64                    | python3-3.6.8-18.el7.x86_64                    | python3-3.6.8-13.el7.x86_64                | python3-3.6.8-13.el7.x86_64                | python3-3.6.8-13.el7.x86_64                | python3-3.6.8-13.el7.x86_64                | python3-3.6.8-13.el7.x86_64                | python3-3.6.8-13.el7.x86_65                | python3-3.6.15-3.91.4.x86_64            |
| cpio                                            | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | cpio-2.12-3.3.1.x86_64                  |
| git-core                                        | NA                                            | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         | NA                                      |
| tftp-server                                     | tftp-server                                   | tftp-server                                    | tftp-server                                    | tftp-server                                    | tftp-server                                    | tftp-server                                    | tftp-server                                    | tftp-server                                    | tftp-server                                | tftp-server                                | tftp-server                                | tftp-server                                | tftp-server                                | tftp-server                                | tftpd-hpa                               |
| gnupg                                           | gnupg2-2.0.22-5.el7.x86_64                    | gnupg2-2.0.22-5.el7.x86_64                     | gnupg2-2.0.22-5.el7.x86_64                     | gnupg2-2.9-1.el8.x86_64                        | gnupg2-2.2.9-1.el8                             | gnupg2-2.2.20-2.el8                            | gnupg2-2.2.20-2.el8                            | gnupg2-2.2.20-2.el8                            | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_65                 | gnupg                                   |

### Ubuntu

| Tool/Library                                    | Ubuntu Desktop /Server 18.04.01 (64-bit)    | Ubuntu Desktop /Server 18.04.02 (64-bit)    | Ubuntu Desktop /Server 18.04.03 (64-bit)    | Ubuntu Desktop /Server 18.04.04 (64-bit)    | Ubuntu Desktop /Server 18.04.05 (64-bit)    | Ubuntu Desktop /Server 20.04 (64-bit)   | Ubuntu Desktop /Server 20.04.1(64-bit)  | Ubuntu Desktop /Server 20.04.2(64-bit)  | Ubuntu Desktop /Server 20.04.3(64-bit)  |
| ----------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- |
| ip (iproute)                                    | iproute-2 4.15.0-2ubuntu1.3                 | iproute-2 4.15.0-2ubuntu1.3                 | iproute-2 4.15.0-2ubuntu1.3                 | iproute-2 4.15.0-2ubuntu1.3                 | iproute-2 4.15.0-2ubuntu1.3                 | iproute2 -5.5.0-1ubuntu1                | iproute2 -5.5.0-1ubuntu1                | iproute2 -5.5.0-1ubuntu1                | iproute2 -5.5.0-1ubuntu1                |
| gawk                                            | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build2                   | gawk-1:5.0.1+dfsg-1                     | gawk-1:5.0.1+dfsg-1                     | gawk-1:5.0.1+dfsg-1                     | gawk-1:5.0.1+dfsg-1                     |
| gcc                                             | gcc-7.5.0-3ubuntu1~18.04                    | gcc-7.5.0-3ubuntu1~18.04                    | gcc-7.5.0-3ubuntu1~18.04                    | gcc-7.5.0-3ubuntu1~18.04                    | gcc-7.5.0-3ubuntu1~18.05                    | gcc-9.3.0-10ubuntu2                     | gcc-9.4.0-1ubuntu1                      | gcc-9.3.0-17ubuntu1                     | gcc-9.4.0-1ubuntu1                      |
| netstat (net-tools)                             | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu2 | net-tools-1.60+git20180626-1ubuntu1     | net-tools-1.60+git20180626-1ubuntu1     | net-tools-1.60+git20180626-1ubuntu1     | net-tools-1.60+git20180626-1ubuntu1     |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.2-0ubuntu2              | ncurses-devel-6.2-0ubuntu2              | ncurses-devel-6.2-0ubuntu2              | ncurses-devel-6.2-0ubuntu2              |
| zlib-devel(also,install 32-bit of this version) | zlib-devel-1:1.2.11.dfsg-2ubuntu2           | zlib-devel-1:1.2.11.dfsg-2ubuntu2           | zlib-devel-1:1.2.11.dfsg-2ubuntu1.6         | zlib-devel-1:1.2.11.dfsg-2ubuntu1.7         | zlib-devel-1:1.2.11.dfsg-2ubuntu1.8         | zlib-devel-1:1.2.11.dfsg-2ubuntu1.2     | zlib-devel-1:1.2.11.dfsg-2ubuntu1.2     | zlib-devel-1:1.2.11.dfsg-2ubuntu1.2     | zlib-devel-1:1.2.11.dfsg-2ubuntu1.2     |
| openssl-devel                                   | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-1ubuntu2.1~18.04.10     | openssl-devel-1.1.1f-1ubuntu2.10        | openssl-devel-1.1.1f-1ubuntu2.10        | openssl-devel-1.1.1f-1ubuntu2.10        | openssl-devel-1.1.1f-1ubuntu2.10        |
| flex                                            | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                            | flex-2.6.4-6                            | flex-2.6.4-6                            | flex-2.6.4-6                            |
| bison                                           | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build2                  | bison-2:3.0.4.dfsg-1build4              | bison-2:3.0.4.dfsg-1build5              | bison-2:3.0.4.dfsg-1build5              | bison-2:3.0.4.dfsg-1build5              |
| libselinux                                      | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| xterm                                           | xterm-330-1ubuntu2                          | xterm-330-1ubuntu2                          | xterm-330-1ubuntu2                          | xterm-330-1ubuntu2                          | xterm-330-1ubuntu3                          | xterm-353-1ubuntu1                      | xterm-353-1ubuntu1                      | xterm-353-1ubuntu1                      | xterm-353-1ubuntu1                      |
| autoconf                                        | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-12                            | autoconf-2.69-11                        | autoconf-2.69-11.1                      | autoconf-2.69-11.1                      | autoconf-2.69-11.1                      |
| libtool                                         | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-3                             | libtool-2.4.6-14                        | libtool-2.4.6-14                        | libtool-2.4.6-14                        | libtool-2.4.6-14                        |
| texinfo                                         | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-3                      | texinfo-6.7.0.dfsg.2-4                  | texinfo-6.7.0.dfsg.2-5                  | texinfo-6.7.0.dfsg.2-5                  | texinfo-6.7.0.dfsg.2-5                  |
| zlib1g-dev                                      | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-2ubuntu1        | zlib1g-dev1:1.2.11.dfsg-2ubuntu1.2      | zlib1g-dev1:1.2.11.dfsg-2ubuntu1.2      | zlib1g-dev1:1.2.11.dfsg-2ubuntu1.2      |
| gcc-multilib                                    | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:9.3.0-1ubuntu1           | gcc-multilib-4:9.3.0-1ubuntu2           | gcc-multilib-4:9.3.0-1ubuntu2           | gcc-multilib-4:9.3.0-1ubuntu2           |
| build-essential                                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu2                 | build-essential-12.8ubuntu1             | build-essential-12.8ubuntu1.1           | build-essential-12.8ubuntu1.1           | build-essential-12.8ubuntu1.1           |
| SDL-devel                                       | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| glibc-devel                                     | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| glib2-devel                                     | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| automake                                        | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu3                  | automake-1:1.16.1-4ubuntu5              | automake-1:1.16.1-4ubuntu6              | automake-1:1.16.1-4ubuntu6              | automake-1:1.16.1-4ubuntu6              |
| screen                                          | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu2                       | screen-4.8.0-1ubuntu                    | screen-4.8.0-1ubuntu0.1                 | screen-4.8.0-1ubuntu0.1                 | screen-4.8.0-1ubuntu0.1                 |
| pax                                             | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-3                            | pax-1:20171021-5                        | pax-1:20171021-6                        | pax-1:20171021-6                        | pax-1:20171021-6                        |
| libstdc++                                       | libstdc++-7.5.0-3ubuntu1~18.04              | libstdc++-7.5.0-3ubuntu1~18.04              | libstdc++-7.5.0-3ubuntu1~18.04              | libstdc++-7.5.0-3ubuntu1~18.04              | libstdc++-7.5.0-10ubuntu3                   | libstdc++-9.3.0-10ubuntu2               | libstdc++-9.4.0-1ubuntu1                | libstdc++-9.3.0-17ubuntu1               | libstdc++-9.4.0-1ubuntu1                |
| g++ (gcc-c++)                                   | g++-7.5.0-3ubuntu1~18.04                    | g++-7.5.0-3ubuntu1~18.04                    | libstdc++-7.5.0-3ubuntu1~18.04              | g++-7.5.0-3ubuntu1~18.04                    | g++-7.5.0-3ubuntu1~18.05                    | g++-9.3.0-10ubuntu2                     | g++-9.3.0-17ubuntu1                     | g++-9.4.0-17ubuntu1                     | g++-9.3.0-17ubuntu1                     |
| python3-pip                                     | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                   | python3-pip (9.0.1-2)                   | python3-pip (9.0.1-2)                   | python3-pip (9.0.1-2)                   |
| perl-dat-dumper                                 | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| perl-thread-queue                               | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| perl-Text-ParseWords                            | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| xz(xz-utils)                                    | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.4)                        | xz-utils (5.2.4)                        | xz-utils (5.2.4)                        | xz-utils (5.2.4)                        |
| perl                                            | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| cpp                                             | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| patch                                           | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| python3- GitPython(python3-git)                 | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                   | python3-git (2.1.8-1)                   | python3-git (2.1.8-1)                   | python3-git (2.1.8-1)                   |
| python3-jinja2                                  | python3-jinja2 (2.10-1ubuntu0.18.04)        | python3-jinja2 (2.10-1ubuntu0.18.04)        | python3-jinja2 (2.10-1ubuntu0.18.04)        | python3-jinja2 (2.10-1ubuntu0.18.04)        | python3-jinja2 -2.10-1ubuntu0.18.04.1       | python3-jinja2 -2.10.1-2                | python3-jinja2 -2.10.1-2                | python3-jinja2 -2.10.1-2                | python3-jinja2 -2.10.1-2                |
| python3-pexpect                                 | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect -4.6.0-1build1          | python3-pexpect -4.6.0-1build1          | python3-pexpect -4.6.0-1build1          | python3-pexpect -4.6.0-1build1          |
| diffutils                                       | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| ccache                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| which                                           | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| debianutils                                     | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.9.1)                     | debianutils (4.9.1)                     | debianutils (4.9.1)                     | debianutils (4.9.1)                     |
| iputils-ping                                    | iputils-ping 3:20161105-1ubuntu3            | iputils-ping 3:20161105-1ubuntu3            | iputils-ping 3:20161105-1ubuntu2            | iputils-ping 3:20161105-1ubuntu2            | iputils-ping 3:20161105-1ubuntu3            | iputils-ping 3:20190709-3               | iputils-ping 3:20190709-3               | iputils-ping 3:20190709-3               | iputils-ping 3:20190709-3               |
| libegl1-mesa                                    | libegl1-mesa 19.2.8-0ubuntu0~18.04          | libegl1-mesa 19.2.8-0ubuntu0~18.04          | libegl1-mesa 19.2.8-0ubuntu0~18.04          | libegl1-mesa 19.2.8-0ubuntu0~18.04          | libegl1-mesa 19.2.8-0ubuntu0~18.05          | libegl1-mesa 19.2.8-0ubuntu0~18.07      | libegl1-mesa 19.2.8-0ubuntu0~18.08      | libegl1-mesa 19.2.8-0ubuntu0~18.08      | libegl1-mesa 19.2.8-0ubuntu0~18.08      |
| libsdl1.2-dev                                   | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.2     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.4 | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.5 | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.5 | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.5 |
| pylint3                                         | pylint3-1.8.3-1                             | pylint3-1.8.3-1                             | pylint3-1.8.3-1                             | pylint3-1.8.3-1                             | pylint3-1.8.3-2                             | pylint3-1.8.3-4                         | pylint3-1.8.3-5                         | pylint3-1.8.3-5                         | pylint3-1.8.3-5                         |
| python3                                         | python3 (3.6.5)                             | python3 (3.6.8)                             | python3 (3.6.9)                             | python3 (3.6.9)                             | python3 (3.6.9)                             | python3 (3.8.5)                         | python3 (3.8.5)                         | python3 (3.8.5)                         | python3 (3.8.5)                         |
| cpio                                            | cpio 2.12+dfsg-6ubuntu0.18.04.1             | cpio 2.12+dfsg-6ubuntu0.18..1               | cpio 2.12+dfsg-6ubuntu0.18..1               | cpio 2.12+dfsg-6ubuntu0.18..1               | cpio 2.12+dfsg-6ubuntu0.18..1               | cpio-2.13+dfsg-2                        | cpio -2.13+dfsg-2                       | cpio -2.13+dfsg-2                       | cpio -2.13+dfsg-2                       |
| git-core                                        | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                      | NA                                      | NA                                      | NA                                      |
| tftp-server                                     | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                               | tftpd-hpa                               | tftpd-hpa                               | tftpd-hpa                               |
| gnupg                                           | gnupg-2.2.4-1ubuntu1.4                      | gnupg-2.2.4-1ubuntu1.2                      | gnupg-2.2.4-1ubuntu1.2                      | gnupg-2.2.4-1ubuntu1.2                      | gnupg-2.2.4-1ubuntu1.4                      | gnupg-2.2.19-3ubuntu2                   | gnupg-2.2.19-3ubuntu2                   | gnupg-2.2.19-3ubuntu2                   | gnupg-2.2.19-3ubuntu2                   |