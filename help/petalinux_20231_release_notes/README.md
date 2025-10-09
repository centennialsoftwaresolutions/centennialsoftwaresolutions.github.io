# Title

## 000035006 - PetaLinux 2023.1 - Product Update Release Notes and Known Issues

# Description

This Answer Record acts as the release notes for PetaLinux 2023.1 and contains links to information about resolved issues and updated collateral contained in this release.

Please find the installation requirements specified in our user guide [here](https://docs.xilinx.com/r/en-US/ug1144-petalinux-tools-reference-guide/Installation-Requirements).

The packages required for installation per OS can also be found in the attached .xlsx (found at the bottom of this page)

Solution

## BSPs supported for the PetaLinux 2023.1 Release

This table contains supported BSPs for Zynq 7000, MicroBlaze, Zynq UltraScale+ MPSoC, and Versal available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/downloadNav/embedded-design-tools.html).

| SNO  | Platform               | Variant                   | BSP Name                                     | BSP Description                                              |
| ---- | ---------------------- | ------------------------- | -------------------------------------------- | ------------------------------------------------------------ |
| 1    | MicroBlaze             | AC701                     | xilinx-ac701-v2023.1-05080224.bsp            | **This BSP contains:**<br>**Hardware:** Vivado board preset example with MicroBlaze Processor and IPs like AXI UARTLITE, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** bitstream, fs-boot, U-Boot, Linux, rootfs. |
| 2    | MicroBlaze             | KC705                     | xilinx-kc705-v2023.1-05080224.bsp            | **Hardware:** MicroBlaze Processor, AXI UARTLITE, AXI Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal).<br>**Pre-built Images:** bitstream, fs-boot, U-Boot, Linux, rootfs. |
| 3    | MicroBlaze             | KCU105                    | xilinx-kcu105-v2023.1-05080224.bsp           | **Hardware:** MicroBlaze Processor, AXI UARTLITE, AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, AXI Ethernet.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal).<br>**Pre-built Images:** bitstream, fs-boot, U-Boot, Linux, rootfs. |
| 4    | MicroBlaze             | SP701                     | xilinx-sp701-v2023.1-05080224.bsp            | **Hardware:** MicroBlaze Processor, AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, AXI Uartlite, led_8bits, AXI Ethernet.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal).<br>**Pre-built Images:** bitstream, fs-boot, U-Boot, Linux, rootfs. |
| 5    | MicroBlaze             | VCU118                    | xilinx-vcu118-v2023.1-05080224.bsp           | **Hardware:** MicroBlaze Processor, AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, AXI Uartlite, led_8bits, AXI Ethernet.<br>**Software:** fs-boot, U-Boot, Linux, device-tree, rootfs (minimal).<br>**Pre-built Images:** bitstream, fs-boot, U-Boot, Linux, rootfs. |
| 6    | Zynq 7000              | ZC702                     | xilinx-zc702-v2023.1-05080224.bsp            | **Hardware:** Vivado board presets with Zynq-7000 PS (DDR, UART, SD, QSPI, Ethernet, AXI GPIO, led_4bits).<br>**Software:** FSBL, U-Boot, Linux, device-tree (includes open-amp), rootfs (minimal).<br>**Pre-built Images:** bitstream, FSBL, U-Boot, Linux, rootfs. |
| 7    | Zynq 7000              | ZC706                     | xilinx-zc706-v2023.1-05080224.bsp            | **Hardware:** Zynq-7000 PS (DDR, UART, SD, QSPI, Ethernet), AXI GPIO (led_4bits, dip_switches_4bits, gpio_sws_3bits).<br>**Software:** FSBL, U-Boot, Linux, device-tree (includes open-amp), rootfs (minimal).<br>**Pre-built Images:** bitstream, FSBL, U-Boot, Linux, rootfs. |
| 8    | Zynq UltraScale+ MPSoC | ZCU102 production silicon | xilinx-zcu102-v2023.1-05080224.bsp           | **Hardware:** Extensible platform with PS peripherals (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA), PL IPs (proc_sys_reset, axi_vip, axi_intc, axi_interconnect).<br>**Vitis:** pfm.tcl for platform generation.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rootfs (minimal/full).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 9    | Zynq UltraScale+ MPSoC | ZCU104 production silicon | xilinx-zcu104-v2023.1-05080224.bsp           | **Hardware:** Zynq UltraScale+ MPSoC PS + VCU DDR4 Controller, VCU IP, clk_wiz, axi_interconnect.<br>**Vitis:** pfm.tcl for platform generation.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), vcu-control, rootfs (minimal/full with multimedia packages).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 10   | Zynq UltraScale+ MPSoC | ZCU106 production silicon | xilinx-zcu106-v2023.1-05080224.bsp           | **Hardware 1/2:** Two designs with Zynq UltraScale+ MPSoC PS, VCU DDR4 Controller, VCU IP, clk_wiz, axi_interconnect.<br>**Vitis:** pfm.tcl for platform generation.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), fpga manager, vcu-control, rootfs (minimal/full).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 11   | Zynq UltraScale+ RFSoC | ZCU111                    | xilinx-zcu111-v2023.1-05080224.bsp           | **Hardware:** RFSoC PS (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA), rf_data_converters, sd_fec_dec, adc_sink, dac_source.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rfdc-drivers, rootfs (minimal/full).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 12   | Zynq UltraScale+ RFSoC | ZCU1275                   | xilinx-zcu1275-v2023.1-05080224.bsp          | **Hardware:** RFSoC PS (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA), rf_data_converters, adc_sink, dac_source.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rfdc-drivers, rootfs (minimal/full).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 13   | Zynq UltraScale+ RFSoC | ZCU1285                   | xilinx-zcu1285-v2023.1-05080224.bsp          | **Hardware:** RFSoC PS (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA), rf_data_converters, adc_sink, dac_source.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rfdc-drivers, rootfs (minimal/full).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 14   | Zynq UltraScale+ RFSoC | ZCU216                    | xilinx-zcu216-v2023.1-05080224.bsp           | **Hardware:** RFSoC PS (DDR, UART, SD, QSPI, Ethernet) with ADC_DDR_DMA, DAC_DDR_DMA, CLOCKING blocks.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rfclk, rfdc-drivers, rootfs (minimal/full).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 15   | Zynq UltraScale+ RFSoC | ZCU208                    | xilinx-zcu208-v2023.1-05080224.bsp           | **Hardware:** RFSoC PS (DDR, UART, SD, QSPI, Ethernet) with ADC_DDR_DMA, DAC_DDR_DMA CLOCKING blocks.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rfclk, rfdc-drivers, rootfs (minimal/full).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 16   | Zynq UltraScale+ RFSoC | ZCU208-SDFEC              | xilinx-zcu208-sdfec-v2023.1-05080224.bsp     | **Hardware:** RFSoC PS (DDR, UART, SD, QSPI, Ethernet) with SD-FEC, AXI stream, Monitor blocks.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rfclk, rfdc-drivers, rootfs (minimal/full).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 17   | Zynq UltraScale+ MPSoC | K26 Production SOM        | xilinx-k26-som-v2023.1-05080224.bsp          | **Hardware:** Zynq UltraScale PS (SOM-specific PS peripherals + UART).<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rootfs (minimal/full with SOM packages).<br>**Pre-built:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 18   | Zynq UltraScale+ MPSoC | kv260-starterkit          | xilinx-kv260-starterkit-v2023.1-05080224.bsp | *(Same as entry 17)*                                         |
| 19   | Zynq UltraScale+ MPSoC | kr260-starterkit          | xilinx-kr260-starterkit-v2023.1-05080224.bsp | *(Same as entry 17)*                                         |
| 20   | Versal                 | VCK190                    | xilinx-vck190-v2023.1-05080224.bsp           | **Hardware (Extensible Platform):** Versal CIPS PS (DDR, UART, SD, QSPI, Ethernet, USB) + AIE example.<br>**Vitis Platform:** for building Vitis apps.<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rootfs (minimal/full).<br>**Pre-built:** PDI, PLM, PSMFW, TF-A, U-Boot, DTBs, Linux, rootfs, Xen images.<br>**Note:** Supports vck190 rev1 & revA. |
| 21   | Versal                 | VCK190-OSPI               | xilinx-vck190-ospi-v2023.1-05080224.bsp      | *(Same as 20, with OSPI boot module).*                       |
| 22   | Versal                 | VCK190-EMMC               | xilinx-vck190-emmc-v2023.1-05080224.bsp      | *(Same as 20, with EMMC boot module).*                       |
| 23   | Versal                 | VMK180                    | xilinx-vmk180-v2023.1-05080224.bsp           | **Hardware:** Versal CIPS PS block (DDR, UART, SD, QSPI, Ethernet, USB).<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rootfs (minimal/full).<br>**Pre-built:** PDI, PLM, PSMFW, TF-A, U-Boot, Linux, rootfs, Xen images.<br>**Note:** Supports vmk180 rev1 & revA. |
| 24   | Versal                 | VMK180-EMMC               | xilinx-vmk180-emmc-v2023.1-05080224.bsp      | *(Same as 23, with EMMC boot module).*                       |
| 25   | Versal                 | VMK180-OSPI               | xilinx-vmk180-ospi-v2023.1-05080224.bsp      | *(Same as 23, with OSPI boot module).*                       |
| 26   | Versal                 | VPK120                    | xilinx-vpk120-v2023.1-05080224.bsp           | **Hardware:** Versal CIPS PS (LPDDR, UART, SD, QSPI, Ethernet, USB).<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rootfs (minimal/full).<br>**Pre-built:** PDI, PLM, PSMFW, TF-A, U-Boot, DTBs, Linux, rootfs, Xen images. |
| 27   | Versal                 | VPK180                    | xilinx-vpk180-v2023.1-05080224.bsp           | **Hardware:** Versal CIPS PS (LPDDR, UART, SD, QSPI, Ethernet, USB) with sysmon in secure mode & multi-SLRs.<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux, device-tree (open-amp, Xen), rootfs (minimal/full).<br>**Pre-built:** PDI, PLM, PSMFW, TF-A, U-Boot, DTBs, Linux, rootfs, Xen images. |

**Unified Images supported for the 2023.1 PetaLinux Release**

This table contains supported unified images for Zynq-7000 and Zynq UltraScale+ MPSoC/RFSoC and Versal devices which are available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html)

| Platform                   | File Name                                    | Description                                                  |
| -------------------------- | -------------------------------------------- | ------------------------------------------------------------ |
| **Zynq UltraScale+ MPSoC** | xilinx-zynqmp-common-v2023.1_05080224.tar.gz | **This tar contains:**<br>• bl31.elf<br>• boot.scr<br>• Image<br>• rootfs.ext4<br>• rootfs.manifest<br>• rootfs.tar.gz<br>• sdk.sh<br>• u-boot.elf<br><br>**README.txt:** Describes the files and provides usage information. |
| **Versal**                 | xilinx-versal-common-v2023.1_05080224.tar.gz | **This tar contains:**<br>• bl31.elf<br>• boot.scr<br>• Image<br>• rootfs.ext4<br>• rootfs.manifest<br>• rootfs.tar.gz<br>• sdk.sh<br>• u-boot.elf<br><br>**README.txt:** Describes the files and provides usage information. |

**Note:** Refer to the README.hw file for the type and version of all IP's in the BSP designs.

## PetaLinux 2023.1 contains the following build collateral:

## Commits Information

The following table briefs Repo's, Tag's, and commits ID's information for 2023.1 Release

### Yocto Components

| Component              | Branch      | Commit ID                                | URL                                                          | GitHub Tag       |
| ---------------------- | ----------- | ---------------------------------------- | ------------------------------------------------------------ | ---------------- |
| yocto-scripts          | rel-v2023.1 | 0baffcc5d99da5338fb399d7b687ee9faf9631cb | [https://github.com/Xilinx/yocto-scripts/tree/rel-v2023.1](https://github.com/Xilinx/yocto-scripts/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| yocto-manifests        | rel-v2023.1 | ef412004388b27083dbd356883b9e2a6b4547a89 | [https://github.com/Xilinx/yocto-manifests/tree/rel-v2023.1](https://github.com/Xilinx/yocto-manifests/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| poky                   | rel-v2023.1 | 12029f5899b23b3839b961eb68cc7a867e6b8d15 | [https://github.com/Xilinx/poky/tree/rel-v2023.1](https://github.com/Xilinx/poky/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-xilinx-tsn        | rel-v2023.1 | 87b60ad671f6800b034935a7f4f5a125fbd59d28 | [https://github.com/Xilinx/meta-xilinx-tsn/tree/rel-v2023.1](https://github.com/Xilinx/meta-xilinx-tsn/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-xilinx-tools      | rel-v2023.1 | 280695ffd7ae40009e37b568dd9a7c5cbab5bfbd | [https://github.com/Xilinx/meta-xilinx-tools/tree/rel-v2023.1](https://github.com/Xilinx/meta-xilinx-tools/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-xilinx            | rel-v2023.1 | d4732aa636e6764c64030083a20975283c2352d5 | [https://github.com/Xilinx/meta-xilinx/tree/rel-v2023.1](https://github.com/Xilinx/meta-xilinx/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-virtualization    | rel-v2023.1 | 1cd805c747da2001506f029c276e656760cec02b | [https://github.com/Xilinx/meta-virtualization/tree/rel-v2023.1](https://github.com/Xilinx/meta-virtualization/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-system-controller | rel-v2023.1 | 3c97b2c358e9e5cf690eca83e320fa50cedbe945 | [https://github.com/Xilinx/meta-system-controller/tree/rel-v2023.1](https://github.com/Xilinx/meta-system-controller/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-security          | rel-v2023.1 | 2aa48e6f4e519abc7d6bd56da2c067309a303e80 | [https://github.com/Xilinx/meta-security/tree/rel-v2023.1](https://github.com/Xilinx/meta-security/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-ros               | rel-v2023.1 | fb6cc73c4013a41cbbeb763213efe62e0d2c08f3 | [https://github.com/Xilinx/meta-ros/tree/rel-v2023.1](https://github.com/Xilinx/meta-ros/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-qt5               | rel-v2023.1 | 1a917695e439d602ec85e1db4e0478533cfbfaa8 | [https://github.com/Xilinx/meta-qt5/tree/rel-v2023.1](https://github.com/Xilinx/meta-qt5/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-petalinux         | rel-v2023.1 | b63a17e6fbea148adf59ea88d273bacac8ba98f0 | [https://github.com/Xilinx/meta-petalinux/tree/rel-v2023.1](https://github.com/Xilinx/meta-petalinux/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-openembedded      | rel-v2023.1 | c354f92778c1d4bcd3680af7e0fb0d1414de2344 | [https://github.com/Xilinx/meta-openembedded/tree/rel-v2023.1](https://github.com/Xilinx/meta-openembedded/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-openamp           | rel-v2023.1 | dc4fa75634c80ad3cd00bf634b0f3c67b4f8210f | [https://github.com/Xilinx/meta-openamp/tree/rel-v2023.1](https://github.com/Xilinx/meta-openamp/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-mingw             | rel-v2023.1 | b0067202db8573df3d23d199f82987cebe1bee2c | [https://github.com/Xilinx/meta-mingw/tree/rel-v2023.1](https://github.com/Xilinx/meta-mingw/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-kria              | rel-v2023.1 | c6c75805883c3f36795ee9275f511bc560e3b4e5 | [https://github.com/Xilinx/meta-kria/tree/rel-v2023.1](https://github.com/Xilinx/meta-kria/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-jupyter           | rel-v2023.1 | ad54a81a36e2734284709cee118c1944e6d510e7 | [https://github.com/Xilinx/meta-jupyter/tree/rel-v2023.1](https://github.com/Xilinx/meta-jupyter/tree/rel-v2023.1) | xlnx-rel-v2023.1 |
| meta-aws               | rel-v2023.1 | b18ab37cc3a490d5c27ad5aa962a6851d2ab0215 | [https://github.com/Xilinx/meta-aws/tree/rel-v2023.1](https://github.com/Xilinx/meta-aws/tree/rel-v2023.1) | xlnx-rel-v2023.1 |

### SSW Components

| Component             | Branch               | Commit ID                                | URL                                                     | Github Tag                  |
| --------------------- | -------------------- | ---------------------------------------- | ------------------------------------------------------- | --------------------------- |
| tsn-utils             | xlnx_rel_v2023.1     | f62d79efc1a74cde8e755ec85ca26702c4fe6fbf | https://github.com/Xilinx/tsn-utils                     | xilinx_v2023.1              |
| tsn-examples          | xlnx_rel_v2023.1     | 5959b0819c0ed72444b78984d2f98077c45d54f3 | https://github.com/Xilinx/tsn-talker-listener           | xilinx_v2023.1              |
| ai-engine-driver      | xlnx_rel_v2023.1     | 1ad203de0b7f282b1c0659fd2ae3f218652c7274 | https://github.com/Xilinx/aie-rt                        | xilinx_v2023.1              |
| board-id-data         | xlnx_rel_v2023.1     | d4e775aa6110b659587686c428a5e0f42e5e4f3d | https://github.com/Xilinx/xlnx-board-id-data            | xilinx_v2023.1              |
| labtool-jtag-support  | xlnx_rel_v2023.1     | 697c375bb772a8d842db1b1f276b07f8d6024607 | https://github.com/Xilinx/systemctl-labtool             | xilinx_v2023.1              |
| power-advantage-tool  | xlnx_rel_v2023.1     | 6a527f77fd865c2edd4463a9798486e7d34a43bf | https://github.com/Xilinx/jupyter-pat                   | xilinx_v2023.1              |
| ultra96-startup-pages | master               | 276b6efd462fc14f22dcea1af4c51cc3d31d1c95 | https://github.com/Xilinx/ultra96-startup-pages         | master                      |
| pm-notebooks          | xlnx_rel_v2023.1     | c502be361b6857e21ab903f31c9ead69e3a0d9ba | https://github.com/Xilinx/platform-management-notebooks | xilinx_v2023.1              |
| external-hdf          | xlnx_rel_v2023.1     | d084dd895cbdc7475f65dda9c3fb5dbdf66d78b2 | https://github.com/Xilinx/hdf-examples                  | xilinx_v2023.1              |
| image-update          | xlnx_rel_v2023.1     | 38b05d94e95a9b97362c57026d57f91c76d9ff08 | https://github.com/Xilinx/linux-image_update            | xilinx_v2023.1              |
| xlnx-platformstats    | xlnx_rel_v2023.1     | 9b4327f86b238ba0ba07bba4a0186766c9a803ac | https://github.com/Xilinx/xlnx_platformstats            | xilinx_v2023.1              |
| ddr-qos               | xlnx_rel_v2023.1     | 6d1304e5b826cea21da02bd7ca04512176f665ff | https://github.com/Xilinx/ddr-qos                       | xilinx_v2023.1              |
| axi-qos               | xlnx_rel_v2023.1     | 2fd1b627c83778d03b1a91c99990d3714d261bbd | https://github.com/Xilinx/axi-qos                       | xilinx_v2023.1              |
| kria-dashboard        | xlnx_rel_v2023.1     | 7b24d185268d1a4d310b21367beb361001e4c7a3 | https://github.com/Xilinx/kria-dashboard                | xilinx_v2023.1              |
| xmutil                | xlnx_rel_v2023.1     | b5b1ad13bcc48d4cbd20476c97d05589bdfc7772 | https://github.com/Xilinx/xmutil                        | xilinx_v2023.1              |
| dfx-mgr               | xlnx_rel_v2023.1     | 5918fb3406d828693cca484b77229ffd031b5dc4 | https://github.com/Xilinx/dfx-mgr                       | xilinx_v2023.1              |
| image-builder         | xlnx_rel_v2023.1     | 37ba04b63cb2c01d8e683f31a9eb3878f1e80305 | https://github.com/Xilinx/imagebuilder                  | xilinx_v2023.1              |
| sdfec                 | xlnx_rel_v2023.1     | 91a9fc9b6758959f34fef92dbfd3bb3556181f3e | https://github.com/Xilinx/linux-examples                | xilinx_v2023.1              |
| libdfx                | xlnx_rel_v2023.1     | 52c1d83c72a2b2e85d256411a199ed1baed12ae1 | https://github.com/Xilinx/libdfx                        | xilinx_v2023.1              |
| pmtool                | xlnx_rel_v2023.1     | 8aaad5c95c67974df8a1c590d1afb3f6ad39fa31 | https://github.com/Xilinx/system-controller-pmtool      | xilinx_v2023.1              |
| scweb                 | xlnx_rel_v2023.1     | 63f3e6f77a1631fe8879ad2b74bcaa0357b8e18b | https://github.com/Xilinx/system-controller-web         | xilinx_v2023.1              |
| bootgen               | xlnx_rel_v2023.1     | 4f1e1caf2c09cdeacc35cbeedaf2550c6e44c7fd | https://github.com/Xilinx/bootgen                       | xilinx_v2023.1              |
| gstreamer1.0          | xlnx-rebase-v1.20.5  | 48eba62b98efe83b86cef38ee876e9f5b23f3397 | https://github.com/Xilinx/gstreamer                     | xlnx-rebase-v1.20.5_2023.1  |
| system-controller-app | xlnx_rel_v2023.1     | 84e5684563bf0e2e48a7eda2c709816e949743e0 | https://github.com/Xilinx/system-controller-app         | xilinx_v2023.1              |
| xrt                   | 2023.1               | 64c933573e7e50a8aba939a74209590c2b739e8b | https://github.com/Xilinx/XRT                           | 2023.1                      |
| kernel-module-dp      | xlnx_rel_v2023.1     | 5b0969ac09f301c33bccc140c8f60e832f5cf222 | https://github.com/xilinx/dp-modules                    | xilinx_v2023.1              |
| kernel-module-hdmi    | xlnx_rel_v2023.1     | 1c6330f02fea68992e22400fdbc8c0d0e63e2958 | https://github.com/Xilinx/hdmi-modules                  | xilinx_v2023.1              |
| vdu-firmware          | xlnx_rel_v2023.1     | 63fe2fce6e46d5bf03e33300a58a37d8568722ee | https://github.com/Xilinx/vdu-firmware                  | xilinx_v2023.1              |
| libvdu-ctrlsw         | xlnx_rel_v2023.1     | 06fc18b303b40d4fee7549ad162c22ee1bc31582 | https://github.com/Xilinx/vdu-ctrl-sw                   | xilinx_v2023.1              |
| kernel-module-vdu     | xlnx_rel_v2023.1     | 82d06e395c93a1e941b83cccbb6f2e4e6d966f1c | https://github.com/Xilinx/vdu-modules                   | xilinx_v2023.1              |
| libvdu-omxil          | xlnx_rel_v2023.1     | 811eefac953fd5e098c69cada97a0dd35f5e9015 | https://github.com/Xilinx/vdu-omx-il                    | xilinx_v2023.1              |
| libomxil-xlnx         | xlnx_rel_v2023.1     | 4773b372b72b88ccbabc122b023f042fb22a019e | https://github.com/Xilinx/vcu-omx-il                    | xilinx_v2023.1              |
| kernel-module-vcu     | xlnx_rel_v2023.1     | 4afe0ab4eb3b7f2d17bcb823dee0caa0f03ab7a0 | https://github.com/Xilinx/vcu-modules                   | xilinx_v2023.1              |
| libvcu-xlnx           | xlnx_rel_v2023.1     | 83aabb84c26667f7d6aee632654c63e504838061 | https://github.com/Xilinx/vcu-ctrl-sw                   | xilinx_v2023.1              |
| vcu-firmware          | xlnx_rel_v2023.1     | c90288595ac9a12ff401de6dfa680b1f9adce5f6 | https://github.com/Xilinx/vcu-firmware                  | xilinx_v2023.1              |
| open-amp-xlnx         | xlnx_rel_v2023.1     | c8aaf2f26d5493f492f0af09dd558d45908636da | https://github.com/Xilinx/open-amp                      | xilinx_v2023.1              |
| libmetal-xlnx         | xlnx_rel_v2023.1     | be635252271de342014a146825870b64bd41d6eb | https://github.com/Xilinx/libmetal                      | xilinx_v2023.1              |
| libmali-xlnx          | xlnx_rel_v2023.1     | b3a772aad859cdadc8513b11c3e995546c20e75e | https://github.com/Xilinx/mali-userspace-binaries       | xilinx_v2023.1              |
| runx-xlnx             | xlnx_rebase_1.1      | 0c7edb3453398d7a0c594ce026c9c1e93c2541cc | https://github.com/Xilinx/runx                          | xlnx_rebase_1.1_2023.1      |
| xen                   | xlnx_rebase_4.17     | d1258f1cefe406a3f91237b8106746c089864651 | https://github.com/Xilinx/xen                           | xlnx_rebase_4.17_2023.1     |
| qemu-xilinx           | xlnx_rel_v2023.1     | 21adc9f99e813fb24fb65421259b5b0614938376 | https://github.com/Xilinx/qemu                          | xilinx_v2023.1              |
| qemu-devicetrees      | xlnx_rel_v2023.1     | 1c45adcde1fc06432c01be250bf668c6477d8459 | https://github.com/Xilinx/qemu-devicetrees              | xilinx_v2023.1              |
| device-tree           | xlnx_rel_v2023.1     | 0bd6e466ba52c49da0dd31601233d926ccf5f9be | https://github.com/Xilinx/device-tree-xlnx              | xilinx_v2023.1              |
| fsbl-firmware         | xlnx_rel_v2023.1     | 86f54b77641f325042a1101fead96b2714e6d3ef | https://github.com/Xilinx/embeddedsw                    | xilinx_v2023.1              |
| arm-trusted-firmware  | xlnx_rebase_v2.8     | c9b71dc96f3f18ca94cad590612aae3224c8c84d | https://github.com/Xilinx/arm-trusted-firmware          | xlnx_rebase_v2.8_2023.1     |
| u-boot-xlnx           | xlnx_rebase_v2023.01 | 40a08d69e749c0472103551c85c02c41f979453d | https://github.com/Xilinx/u-boot-xlnx                   | xlnx_rebase_v2023.01_2023.1 |
| linux-xlnx            | xlnx_rebase_v6.1_LTS | 716921b6d7dc9db49660369428fb61ca96947ccb | https://github.com/Xilinx/linux-xlnx                    | xlnx_rebase_v6.1_LTS_2023.1 |

## VCU New Features

-   Dynamic Insertion of IDR frame in GDR mode supported.

## GPU New Features

-   None

## Open Source components New Features

-   [SSW 2023.1 Features](https://xilinx-wiki.atlassian.net/wiki/spaces/XWUC/pages/2632286215/2023.1+Release+Notes+for+Open+Source+Components)

## VCU Bug Fixes

| Component Name | Platform               | Bug Description                                              |
| -------------- | ---------------------- | ------------------------------------------------------------ |
| SSW_VCU        | Zynq UltraScale+ MPSoC | - Fixed scheduler destruction if the input stream exceeds its capability for a number of times.<br>- h264parser: Fixed return value parsing short header. The appropriate return value for incomplete NAL header should be `GST_H264_PARSER_NO_NAL_END`.<br>- Fixed file descriptor handling at gst-omx and omx-il.<br>- Fixed frame tear in LLP2 after hotplug event.<br>- Fixed input stream concealment for split-input mode.<br>- `gstbasesrc`: changed blocksize of source based on proposed allocation size from upstream element.<br>- Fixed VCU Decoder alignment issues for the resolution less than 540p. |

## GPU Bug Fixes

-   Runtime fixes after update glmark2 to 2021.12 from 2021.02
-   Fixed gfxbench compilation issues
-   Fixed openglcts issues by updating to latest version 3.2.9 from 3.2.4
-   Fixed Mali driver probe failure due to kernel upgrade

## Known Issues for the 2023.1 release

| Linux/Baremetal | Components      | Platform/SoC Supported                           | Work-around Article Description and Link                     | To be fixed version |
| --------------- | --------------- | ------------------------------------------------ | ------------------------------------------------------------ | ------------------- |
| Linux           | SSW_Drivers     | Zynq UltraScale+ MPSoC<br>Zynq UltraScale+ RFSoC | 2021.2/2022.X Zynq UltraScale+ MPSoC TSN: Traffic drops for board to board connection with large number of packets | 2023.2              |
| Linux           | SSW_Drivers     | Zynq UltraScale+ MPSoC<br>Zynq UltraScale+ RFSoC | 000034373 - TSN Pre-emption Does Not Work in 2022.1 Linux TSN kernel and tsn-utils User Space Apps | 2023.2              |
| Linux           | SSW_VCU         | Zynq UltraScale+ MPSoC<br>Zynq UltraScale+ RFSoC | Memory leak observed with decoder app with LLP2 mode         | 2023.2              |
| Linux           | SSW_Video-Linux | Zynq UltraScale+ MPSoC<br>Zynq UltraScale+ RFSoC | Weston10.0.0 has compatibility issues because of which we are seeing issues while running weston compositor | 2023.2              |
| Linux           | PetaLinux       | Zynq UltraScale+ MPSoC<br>Zynq UltraScale+ RFSoC | 000035184 - 2023.1 PetaLinux - QEMU boot for WIC image is failing | 2023.2              |
| Linux           | QEMU            | Zynq UltraScale+ MPSoC<br>Zynq UltraScale+ RFSoC | 000035216 - 2023.1 Zynq UltraScale+ MPSoC: Error prints observed when booting QEMU with ZCU104/ZCU106 BSP images | 2023.2              |
| Linux           | SSW_Drivers     | Zynq UltraScale+ MPSoC<br>Zynq UltraScale+ RFSoC | SMMU_CCI enabled images: Observed "xhci-hcd xhci-hcd.1.auto: ERROR mismatched command completion event" while resume in ZCU102 Rev1.0 board | 2023.2              |
| Linux           | SSW_Drivers     | Zynq UltraScale+ MPSoC<br>Zynq UltraScale+ RFSoC | 000035136 - 2022.x BBT of NAND is different between U-boot and Linux kernel | 2023.2              |
| Linux           | SSW_Drivers     | Zynq                                             | 000035215 - 2023.1 Zynq 7000 Linux: QSPI-flashprotect case is Failing for IS25WP064A-JMLE flash on Zynq boards | 2023.2              |
| Linux           | PetaLinux       | Versal                                           | The boot script offset in bif does not change accordingly when it is changed in u-boot configuration | 2023.2              |
| Linux           | PetaLinux       | Versal                                           | 000035185 - 2023.1 Zynq UltraScale+ MPSoC: PetaLinux Error in creating final DTS when XSA and DTSI are inputs to SRCURI for partial reconfiguration - DFX | 2023.2              |
| Linux           | Yocto           | Zynq<br>Zynq UltraScale+ MPSoC<br>Versal         | Static Device Nodes error strings observed in PetaLinux      | N/A                 |
| Linux           | Yocto           | Zynq<br>Zynq UltraScale+ MPSoC<br>Versal         | Kernel Trace File System error strings observed in PetaLinux | N/A                 |
| Linux           | Yocto           | Zynq UltraScale+ MPSoC                           | Yocto ZynqMP SDT built images doesn't boot on HW with PL included in SDT | 2023.2              |
| Linux           | Yocto           | Zynq<br>Zynq UltraScale+ MPSoC<br>Versal         | PACKAGECONFIG Warnings observed in SDT builds                | 2023.2              |
| Baremetal       | SSW_Libraries   | Zynq<br>Zynq UltraScale+ MPSoC<br>Versal         | 000035213 - 2023.1 Cortex R5: Xil_DCacheFlushRange: Memory out of range for OCM boundary | 2023.2              |

# 2023.1_PetaLinux_Package_List

## Linux Distribution OS details:

1. Ubuntu Desktop/Server 18.04.01 LTS, 18.04.02 LTS, 18.04.03 LTS, 18.04.04 LTS, 18.04.05 LTS,18.04.06 LTS, 20.04 LTS,20.04.1 LTS, 20.04.2 LTS,20.04.03 LTS,20.04.04 LTS,20.04.5 LTS(64-bit),22.04 LTS and Ubuntu 22.04.1 LTS.

3. OPEN SUSE LEAP 15.3 Server (From Everything.ISO): Infrastructure server
4. OPEN SUSE LEAP 15.3 Desktop (From Everything.ISO): Development and Creative workstation.
5. Alma Linux 8.7  Server (From Everything.ISO): Infrastructure server
6. Alma Linux 8.7  Desktop (From Everything.ISO): Development and Creative workstation.

### Note: 

1. Empty packages are not installed means assuming these are default from Linux Distribution.

2. For Suse you need to install GitPython and jinja2 using pip3 commands as mentioned below.

### Host GCC Version Upgrade:

From 2021.1 release, the gcc version should be greater than 6. Using lower versions of gcc causes build issues. You can also enable the Enable buildtools extended option from petalinux -config → Yocto settings, which uses the pre-compiled gcc binaries from the PetaLinux tool. 

## Quick Installation steps for packages

### Ubuntu Desktop/Server 64-bit

```
sudo apt-get install iproute2 gawk python3 python build-essential gcc git make net-tools libncurses5-dev tftpd zlib1g-dev libssl-dev flex bison libselinux1 gnupg wget git-core diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib automake zlib1g:i386 screen pax gzip cpio python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3
```

## Tool/Library Versions

### Ubuntu

| Tool/Library                                    | Ubuntu Desktop /Server 18.04.01 (64-bit)    | Ubuntu Desktop /Server 18.04.02 (64-bit)    | Ubuntu Desktop /Server 18.04.03 (64-bit)    | Ubuntu Desktop /Server 18.04.04 (64-bit)    | Ubuntu Desktop /Server 18.04.05 (64-bit)    | Ubuntu Desktop /Server 18.04.06 (64-bit)    | Ubuntu Desktop /Server 20.04 (64-bit)         | Ubuntu Desktop /Server 20.04.1(64-bit)      | Ubuntu Desktop /Server 20.04.2(64-bit)      | Ubuntu Desktop /Server 20.04.3(64-bit)      | Ubuntu Desktop /Server 20.04.4(64-bit)                     | Ubuntu Desktop /Server 20.04.5(64-bit)      | Ubuntu Desktop /Server 22.04(64-bit)        | Ubuntu Desktop /Server 22.04.1(64-bit)                |
| ----------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | --------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ----------------------------------------------------- |
| ip (iproute)                                    | iproute2-4.15.0-2ubuntu1                    | iproute2-4.15.0-2ubuntu1                    | iproute2-4.15.0-2ubuntu1.3                  | iproute2-4.15.0-2ubuntu1.1                  | iproute2-4.15.0-2ubuntu1.3                  | iproute2-4.15.0-2ubuntu1.3                  | iproute2 -5.5.0-1ubuntu1                      | iproute2 -5.5.0-1ubuntu1                    | iproute2 -5.5.0-1ubuntu1                    | iproute2 -5.5.0-1ubuntu1                    | iproute2-5.5.0-1ubuntu1                                    | iproute2-5.5.0-1ubuntu1                     | iproute2-5.15.0-1ubuntu2                    | iproute2-5.15.0-1ubuntu2                              |
| gawk                                            | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:5.0.1+dfsg-1                           | gawk-1:5.0.1+dfsg-1                         | gawk-1:5.0.1+dfsg-1                         | gawk-1:5.0.1+dfsg-1                         | gawk-1:5.0.1+dfsg-1                                        | gawk-1:5.0.1+dfsg-1                         | gawk-1:5.1.0-1build3                        | gawk-1:5.1.0-1build3                                  |
| gcc                                             | gcc-7.5.0-3ubuntu1~18.04                    | gcc-7.5.0-3ubuntu1~18.04                    | gcc-7.5.0-3ubuntu1~18.04                    | gcc-7.5.0-3ubuntu1~18.04                    | gcc-7.5.0-3ubuntu1~18.04                    | gcc-7.4.0-1ubuntu2.3~18.04                  | gcc-4:9.3.0-1ubuntu2                          | gcc-4:9.3.0-1ubuntu2                        | gcc-4:9.3.0-1ubuntu2                        | gcc-4:9.3.0-1ubuntu2                        | gcc-4:9.3.0-1ubuntu2                                       | gcc-4:9.3.0-1ubuntu2                        | gcc-4:11.2.0-1ubuntu1                       | gcc-4:11.2.0-1ubuntu1                                 |
| netstat (net-tools)                             | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20180626.aebd88e-1ubuntu1   | net-tools-1.60+git20180626.aebd88e-1ubuntu1 | net-tools-1.60+git20180626.aebd88e-1ubuntu1 | net-tools-1.60+git20180626.aebd88e-1ubuntu1 | net-tools-1.60+git20180626.aebd88e-1ubuntu1                | net-tools-1.60+git20180626.aebd88e-1ubuntu1 | net-tools-1.60+git20181103.0eebece-1ubuntu5 | net-tools-1.60+git20181103.0eebece-1ubuntu5           |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.2-0ubuntu2                    | ncurses-devel-6.2-0ubuntu2                  | ncurses-devel-6.2-0ubuntu2                  | ncurses-devel-6.2-0ubuntu2                  | ncurses-devel-6.2-0ubuntu2                                 | 6.2-0ubuntu2                                | ncurses-devel-6.3-2                         | ncurses-devel-6.3-2                                   |
| zlib-devel(also,install 32-bit of this version) | zlib-devel-1:1.2.11.dfsg-0ubuntu2           | zlib-devel-1:1.2.11.dfsg-0ubuntu2           | zlib-devel-1:1.2.11.dfsg-0ubuntu2           | zlib-devel-1:1.2.11.dfsg-0ubuntu2           | zlib-devel-1:1.2.11.dfsg-0ubuntu2           | zlib-devel-1:1.2.11.dfsg-0ubuntu2           | zlib-devel-1:1.2.11.dfsg-2ubuntu1.3           | zlib-devel-1:1.2.11.dfsg-2ubuntu1.3         | zlib-devel-1:1.2.11.dfsg-2ubuntu1.3         | zlib-devel-1:1.2.11.dfsg-2ubuntu1.2         | NA                                                         | NA                                          | NA                                          | NA                                                    |
| openssl-devel                                   | openssl - 17.5.0-1ubuntu1                   | openssl - 17.5.0-1ubuntu1                   | openssl - 17.5.0-1ubuntu1                   | openssl -1.1.1-1ubuntu2.1~18.04.6           | openssl -17.5.0-1ubuntu1                    | openssl  - 1.1.1-1ubuntu2.1~18.04.14        | openssl - 19.0.0-1build1                      | openssl - 19.0.0-1build1                    | openssl - 19.0.0-1build1                    | openssl-1.1.1f-1ubuntu2.10                  | openssl -1.1.1f-1ubuntu2.16                                | openssl -1.1.1f-1ubuntu2.16                 | openssl-3.0.2-0ubuntu1                      | openssl- 3.0.2-0ubuntu1.6                             |
| flex                                            | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6.2                                | flex-2.6.4-6.2                              | flex-2.6.4-6.2                              | flex-2.6.4-6.2                              | NA                                                         | NA                                          | NA                                          | NA                                                    |
| bison                                           | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build2                  | bison-2:3.0.4.dfsg-1build2                  | bison-2:3.0.4.dfsg-1build4                    | bison-2:3.0.4.dfsg-1build5                  | bison-2:3.0.4.dfsg-1build5                  | bison-2:3.0.4.dfsg-1build5                  | NA                                                         | NA                                          | NA                                          | NA                                                    |
| libselinux                                      | linselinux1-2.7-2build2                     | linselinux1-2.7-2build2                     | linselinux1-2.7-2build2                     | linselinux1-2.7-2build2                     | linselinux1-2.7-2build2                     | linselinux1-2.7-2build2                     | linselinux1-3.0-1build2                       | linselinux1-3.0-1build2                     | linselinux1-3.0-1build2                     | linselinux1-3.0-1build2                     | linselinux1-3.0-1build2                                    | linselinux1-3.0-1build2                     | linselinux1-3.3-1build2                     | linselinux1-3.3-1build2                               |
| xterm                                           | xterm-330-1ubuntu2.2                        | xterm-330-1ubuntu2.2                        | xterm-330-1ubuntu2.2                        | xterm-330-1ubuntu2.2                        | xterm-330-1ubuntu2.2                        | xterm-330-1ubuntu2.2                        | xterm-353-1ubuntu1.20.04.2                    | xterm-353-1ubuntu1.20.04.2                  | xterm-353-1ubuntu1.20.04.2                  | xterm-353-1ubuntu1.20.04.2                  | xterm-353-1ubuntu1.20.04.2                                 | xterm-353-1ubuntu1.20.04.2                  | xterm-372-1ubuntu1                          | xterm-372-1ubuntu1                                    |
| autoconf                                        | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11.1                            | autoconf-2.69-11.1                          | autoconf-2.69-11.1                          | autoconf-2.69-11.1                          | autoconf-2.69-11.1                                         | autoconf-2.69-11.1                          | autoconf-2.71-2                             | autoconf-2.71-2                                       |
| libtool                                         | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-14                              | libtool-2.4.6-14                            | libtool-2.4.6-14                            | libtool-2.4.6-14                            | libtool-2.4.6-14                                           | libtool-2.4.6-14                            | libtool-2.4.6-15build2                      | libtool-2.4.6-15build2                                |
| texinfo                                         | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo -6.5.0.dfsg.1-2                     | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.7.0.dfsg.2-5                        | texinfo-6.7.0.dfsg.2-5                      | texinfo-6.7.0.dfsg.2-5                      | texinfo-6.7.0.dfsg.2-5                      | texinfo-6.7.0.dfsg.2-5                                     | texinfo-6.7.0.dfsg.2-5                      | texinfo                         6.8-4build1 | texinfo                         6.8-4build1           |
| zlib1g-dev                                      | zlib1g-dev1:1:1.2.11.dfsg-0ubuntu2.2        | zlib1g-dev1:1.2.11.dfsg-0ubuntu2.2          | zlib1g-dev1:1.2.11.dfsg-0ubuntu2.2          | zlib1g-dev1:1.2.11.dfsg-0ubuntu2.2          | zlib1g-dev1:1.2.11.dfsg-0ubuntu2.2          | zlib1g-dev1:1.2.11.dfsg-0ubuntu2.2          | zlib1g-dev1:1:1.2.11.dfsg-2ubuntu1.5          | zlib1g-dev1:1:1.2.11.dfsg-2ubuntu1.5        | zlib1g-dev1:1:1.2.11.dfsg-2ubuntu1.5        | zlib1g-dev1:1:1.2.11.dfsg-2ubuntu1.5        | zlib1g-dev:amd64                  1:1.2.11.dfsg-2ubuntu1.3 | zlib1g-dev:amd64 1:1.2.11.dfsg-2ubuntu1.5   | zlib1g-dev:amd64 1:1.2.11.dfsg-2ubuntu9.2   | zlib1g-dev:amd64 1:1.2.11.dfsg-2ubuntu9.2             |
| gcc-multilib                                    | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:9.3.0-1ubuntu2                 | gcc-multilib-4:9.3.0-1ubuntu2               | gcc-multilib-4:9.3.0-1ubuntu2               | gcc-multilib-4:9.3.0-1ubuntu2               | gcc-multilib-4:9.3.0-1ubuntu2                              | gcc-multilib-4:9.3.0-1ubuntu2               | gcc-multilib-411.2.0-1ubuntu1               | gcc-multilib- 4:11.2.0-1ubuntu1                       |
| build-essential                                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.8ubuntu1.1                 | build-essential-12.8ubuntu1.1               | build-essential-12.8ubuntu1.1               | build-essential-12.8ubuntu1.1               | build-essential-12.8ubuntu1.1                              | build-essential-12.8ubuntu1.1               | build-essential - 12.9ubuntu3               | build-essential -12.9ubuntu3                          |
| SDL-devel                                       | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| glibc-devel                                     | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| glib2-devel                                     | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| automake                                        | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake -1:1.16.1-4ubuntu6                   | automake -1:1.16.1-4ubuntu6                 | automake -1:1.16.1-4ubuntu6                 | automake -1:1.16.1-4ubuntu6                 | automake -1:1.16.1-4ubuntu6                                | automake -1:1.16.1-4ubuntu6                 | automake- 1:1.16.5-1.3                      | automake-1:1.16.5-1.3                                 |
| screen                                          | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       | screen -  4.6.2-1ubuntu1.1                  | screen -4.6.2-1ubuntu1                      | screen -4.6.2-1ubuntu1.1                    | screen -4.6.2-1ubuntu1.1                    | screen - 4.8.0-1                              | screen - 4.8.0-1                            | screen -4.8.0-1ubuntu0.1                    | screen -4.8.0-1ubuntu0.1                    | screen -4.8.0-1ubuntu0.1                                   | screen  4.8.0-1ubuntu0.1                    | screen  4.9.0-1                             | screen  4.9.0-1                                       |
| pax                                             | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-3                            | pax-1:20171021-3                            | pax-1:20171021-5                              | pax-1:20171021-6                            | pax-1:20171021-6                            | pax-1:20171021-6                            | NA                                                         | NA                                          | NA                                          | NA                                                    |
| libstdc++                                       | libstdc++-7.5.0-3ubuntu1~18.04              | libstdc++-7.5.0-3ubuntu1~18.04              | libstdc++-7.5.0-3ubuntu1~18.04              | libstdc++-7.5.0-3ubuntu1~18.04              | libstdc++-7.5.0-3ubuntu1~18.04              | libstdc++- 7.5.0-3ubuntu1~18.04             | libstdc++- 9.4.0-1ubuntu1~20.04.1             | libstdc++- 9.4.0-1ubuntu1~20.04.1           | libstdc++- 9.4.0-1ubuntu1~20.04.1           | libstdc++- 9.4.0-1ubuntu1~20.04.1           | libstdc++-9.4.0-1ubuntu1~20.04.1                           | libstdc++-9.4.0-1ubuntu1~20.04.1            | libstdc++-11-dev:11.3.0-1ubuntu1~22.04      | libstdc++-11-dev: 11.3.0-1ubuntu1~22.04               |
| g++ (gcc-c++)                                   | g++ -4:7.4.0-1ubuntu2.3                     | g++ -4:7.4.0-1ubuntu2.3                     | g++ -4:7.4.0-1ubuntu2.3                     | g++ -4:7.4.0-1ubuntu2.3                     | g++ -4:7.4.0-1ubuntu2.3                     | g++ -4:7.4.0-1ubuntu2.3                     | g++ -4:9.3.0-1ubuntu2                         | g++ -4:9.3.0-1ubuntu2                       | g++ -4:9.3.0-1ubuntu2                       | g++ -4:9.3.0-1ubuntu2                       | g++ -4:9.3.0-1ubuntu2                                      | g++ -4:9.3.0-1ubuntu2                       | g++  -4:11.2.0-1ubuntu1                     | g++  -4:11.2.0-1ubuntu1                               |
| python3-pip                                     | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                         | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | NA                                                         | NA                                          | NA                                          | NA                                                    |
| perl-dat-dumper                                 | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| perl-thread-queue                               | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| perl-Text-ParseWords                            | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| xz(xz-utils)                                    | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        | xz-utils - 5.2.2-1.3ubuntu0.1               | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        | xz-utils - 5.2.4-1                            | xz-utils- 5.2.4-1ubuntu1                    | xz-utils- 5.2.4-1ubuntu1                    | xz-utils- 5.2.4-1ubuntu1                    | xz-utils -5.2.4-1ubuntu1.1                                 | xz-utils -5.2.4-1ubuntu1.1                  | xz-utils - 5.2.5-2ubuntu1                   | xz-utils - 5.2.5-2ubuntu1                             |
| perl                                            | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| cpp                                             | cpp-7- 7.5.0-3ubuntu1~18.04                 | cpp-7- 7.5.0-3ubuntu1~18.04                 | cpp-7- 7.5.0-3ubuntu1~18.04                 | cpp-7- 7.5.0-3ubuntu1~18.04                 | cpp-7- 7.5.0-3ubuntu1~18.04                 | cpp-7- 7.5.0-3ubuntu1~18.04                 | cpp-9- 9.4.0-1ubuntu1~20.04.1                 | cpp-9- 9.4.0-1ubuntu1~20.04.1               | cpp-9- 9.4.0-1ubuntu1~20.04.1               | cpp-9- 9.4.0-1ubuntu1~20.04.1               | cpp-9- 9.4.0-1ubuntu1~20.04.1                              | cpp-9- 9.4.0-1ubuntu1~20.04.1               | cpp-11 - 11.3.0-1ubuntu1~22.04              | cpp-11                          11.3.0-1ubuntu1~22.04 |
| patch                                           | patch -  2.7.6-2ubuntu1                     | patch -  2.7.6-2ubuntu1                     | patch-  2.7.6-2ubuntu1.1                    | patch-  2.7.6-2ubuntu1.1                    | patch-  2.7.6-2ubuntu1.1                    | patch-  2.7.6-2ubuntu1.1                    | patch-  2.7.6-6                               | patch-  2.7.6-6                             | patch-  2.7.6-6                             | patch-  2.7.6-6                             | patch-  2.7.6-6                                            | patch-  2.7.6-6                             | patch-2.7.6-7build2                         | patch-2.7.6-7build2                                   |
| python3- GitPython(python3-git)                 | python3-jinja2  -2.10-1                     | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                         | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git                                                | NA                                          | NA                                          | NA                                                    |
| python3-jinja2                                  | python3-jinja2  -2.10-1                     | python3-jinja2   2.10-1ubuntu0.18.04.1      | python3-jinja2   2.10-1ubuntu0.18.04.1      | python3-jinja2   2.10-1ubuntu0.18.04.1      | python3-jinja2   2.10-1ubuntu0.18.04.1      | python3-jinja2 -2.10-1ubuntu0.18.04.1       | python3-jinja2 -2.10.1-2                      | python3-jinja2 -2.10.1-2                    | python3-jinja2 -2.10.1-2                    | python3-jinja2 -2.10.1-2                    | python3-jinja2                                             | python3-jinja2                              | python3-jinja2 -  3.0.3-1                   | python3-jinja2 -  3.0.3-1                             |
| python3-pexpect                                 | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect -4.6.0-1build1                | python3-pexpect -4.6.0-1build1              | python3-pexpect -4.6.0-1build1              | python3-pexpect -4.6.0-1build1              | NA                                                         | NA                                          | NA                                          | NA                                                    |
| diffutils                                       | diffutils 1:3.6-1                           | diffutils-1:3.6-1                           | diffutils-1:3.6-1                           | diffutils-1:3.6-1                           | diffutils-1:3.6-1                           | diffutils-1:3.6-1                           | diffutils-1:3.7-3                             | diffutils-1:3.7-3                           | diffutils-1:3.7-3                           | diffutils-1:3.7-3                           | diffutils-1:3.7-3                                          | diffutils-1:3.7-3                           | diffutils-1:3.8-0ubuntu2                    | diffutils-1:3.8-0ubuntu2                              |
| ccache                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| which                                           | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| debianutils                                     | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.9.1)                           | debianutils (4.9.1)                         | debianutils (4.9.1)                         | debianutils (4.9.1)                         | debianutils (4.9.1)                                        | NA                                          | debianutils(5.5-1ubuntu2)                   | debianutils(5.5-1ubuntu2)                             |
| iputils-ping                                    | iputils-ping 3:20161105-1ubuntu2            | iputils-ping 3:20161105-1ubuntu3            | iputils-ping 3:20161105-1ubuntu3            | iputils-ping 3:20161105-1ubuntu3            | iputils-ping 3:20161105-1ubuntu3            | iputils-ping 3:20161105-1ubuntu3            | iputils-ping 3:20190709-3                     | iputils-ping 3:20190709-3                   | iputils-ping 3:20190709-3                   | iputils-ping 3:20190709-3                   | iputils-ping 3:20190709-3                                  | iputils-ping 3:20190709-3                   | iputils-ping 3:20211215-1                   | iputils-ping - 3:20211215-1                           |
| libegl1-mesa                                    | libegl1-mesa 20.0.8-0ubuntu1~18.04.1        | libegl1-mesa 20.0.8-0ubuntu1~18.04.1        | libegl1-mesa 20.0.8-0ubuntu1~18.04.1        | libegl1-mesa 20.0.8-0ubuntu1~18.04.1        | libegl1-mesa 20.0.8-0ubuntu1~18.04.1        | libegl1-mesa 20.0.8-0ubuntu1~18.04.1        | libegl-mesa0:amd64  21.2.6-0ubuntu0.1~20.04.2 | libegl1-mesa 21.2.6-0ubuntu0.1~20.04.2      | libegl1-mesa 21.2.6-0ubuntu0.1~20.04.2      | libegl1-mesa 21.2.6-0ubuntu0.1~20.04.2      | NA                                                         | NA                                          | NA                                          | NA                                                    |
| libsdl1.2-dev                                   | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.2     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.2     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.4       | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.5     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.5     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.5     | NA                                                         | NA                                          | NA                                          | NA                                                    |
| pylint3                                         | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| python3                                         | python3 -3.6.5-3ubuntu1                     | python3  3.6.7-1~18.04                      | python3 (3.6.7-1 ~18.04)                    | python3 (3.6.7-1 ~18.04)                    | python3 (3.6.7-1 ~18.04)                    | python3 (3.6.7-1 ~18.04)                    | python3 (3.8.2-0ubuntu2)                      | python3 (3.8.2-0ubuntu2)                    | python3 (3.8.2-0ubuntu2)                    | python3 (3.8.2-0ubuntu2)                    | python3 (3.8.2-0ubuntu2)                                   | python3 (3.8.2-0ubuntu2)                    | python3(3.10.6-1~22.04)                     | python3(3.10.4-0ubuntu2)                              |
| cpio                                            | cpio-2.12+dfsg-6                            | cpio-2.12+dfsg-6                            | cpio 2.12+dfsg-6ubuntu0.18.04.1             | cpio 2.12+dfsg-6ubuntu0.18.04.1             | cpio 2.12+dfsg-6ubuntu0.18.04.1             | cpio  -2.12+dfsg-6ubuntu0.18.04.4           | cpio - 2.13+dfsg-2                            | cpio- 2.12+dfsg-6ubuntu0.18.04.1            | cpio -2.13+dfsg-2                           | cpio  -  2.13+dfsg-2ubuntu0.3               | cpio  -  2.13+dfsg-2ubuntu0.3                              | cpio  -  2.13+dfsg-2ubuntu0.3               | cpio - 2.13+dfsg-7                          | cpio - 2.13+dfsg-7                                    |
| git-core                                        | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                          | NA                                            | NA                                          | NA                                          | NA                                          | NA                                                         | NA                                          | NA                                          | NA                                                    |
| tftp-server                                     | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                     | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                                  | NA                                          | NA                                          | NA                                                    |
| gnupg                                           | gnupg-2.2.4-1ubuntu1.1                      | gnupg-2.2.4-1ubuntu1.2                      | gnupg - 2.2.4-1ubuntu1.6                    | gnupg-2.2.4-1ubuntu1.2                      | gnupg-2.2.4-1ubuntu1.4                      | gnupg-2.2.4-1ubuntu1.4                      | gnupg-2.2.19-3ubuntu2                         | gnupg-2.2.19-3ubuntu2                       | gnupg-2.2.19-3ubuntu2.1                     | gnupg-2.2.19-3ubuntu2.1                     | gnupg- 2.2.19-3ubuntu2.2                                   | gnupg- 2.2.19-3ubuntu2.2                    | gnupg - 2.2.27-3ubuntu2                     | gnupg -2.2.27-3ubuntu2.1                              |

### openSUSE/AlmaLinux OS Versions

| Tool/Library                                    | opensuse  Leap Desktop /Server 15.3(64-bit) | Almalinux  Desktop/Server 8.7(64-bit) |
| ----------------------------------------------- | ------------------------------------------- | ------------------------------------- |
| ip (iproute)                                    | iproute2  - 5.3-5.5.1                       | iproute2- 5.18.0-1.el8                |
| gawk                                            | gawk-4.2.1-1.41                             | gawk-4.2.1-4.el8                      |
| gcc                                             | gcc - 7-3.9.1                               | gcc-8.5.0-16.el8_7.alma               |
| netstat (net-tools)                             | net-tools -2.0+git20170221.479bb4a-3.11     | net-tools-2.0-0.52.20160912git.el8    |
| ncurses-devel(libncurses5-dev)                  | ncurses - 3.14.3-bp153.1.25                 | ncurses-devel-6.26.1-9.20180224.el8   |
| zlib-devel(also,install 32-bit of this version) |                                             | zlib-devel-  1.2.11-21.el8_7          |
| openssl-devel                                   | openssl- 3.14.3-bp153.1.25                  | openssl -1:1.1.1k-7.el8_6             |
| flex                                            | flex  - 2.6.4-3.157                         | NA                                    |
| bison                                           | bison- 3.0.4-3.3.1                          | bison  - 3.0.4-3.3.1                  |
| libselinux                                      | libselinux  - 3.0-1.31                      | linselinux1-2.9-6.el8                 |
| xterm                                           | xterm- 330-150200.11.6.1                    | xterm-331-1.el8_3.2                   |
| autoconf                                        | autoconf  - 2.69-1.445                      | autoconf.noarch-2.69-29.el8           |
| libtool                                         | libtool  -2.4.6-3.4.1                       | libtool-2.4.6-25.el8                  |
| texinfo                                         | texinfo- 6.5-4.17                           | texinfo-6.5-7.el8                     |
| zlib1g-dev                                      | NA                                          | zlib-1.2.11-21.el8_7                  |
| gcc-multilib                                    | NA                                          | NA                                    |
| build-essential                                 | NA                                          | NA                                    |
| SDL-devel                                       | NA                                          | NA                                    |
| glibc-devel                                     | glibc-devel 2.31-150300.41.1                | glibc-devel -2.28-211.el8             |
| glib2-devel                                     | glib2-devel  - 1.1.13-150200.4.26.1         | glib2-devel-2.56.4-159.el8            |
| automake                                        | automake- 1.15.1-4.10.2                     | automake.noarch  -1.16.1-7.el8        |
| screen                                          | NA                                          | NA                                    |
| pax                                             | pax-utils - 1.2.2-bp153.1.16                | NA                                    |
| libstdc++                                       | libstdc++6-12.2.1+git416-150000.1.5.1       | libstdc++ - 8.5.0-16.el8_7.alma       |
| g++ (gcc-c++)                                   | NA                                          | gcc-c++ -8.5.0-16.el8_7.alma          |
| python3-pip                                     | python3-pip  -20.0.2-150100.6.18.1          | python3-pip- 9.0.3-22.el8             |
| perl-dat-dumper                                 | NA                                          | NA                                    |
| perl-thread-queue                               | NA                                          | perl-Thread-Queue.noarch-3.13-1.el8   |
| perl-Text-ParseWords                            | NA                                          | NA                                    |
| xz(xz-utils)                                    | NA                                          | xz- 5.2.4-4.el8_6                     |
| perl                                            | NA                                          | NA                                    |
| cpp                                             | cpp - 7-3.9.1                               | cpp - 8.5.0-16.el8_7.alma             |
| patch                                           | NA                                          | NA                                    |
| python3- GitPython(python3-git)                 | python3-GitPython- 3.0.5-bp153.1.18         | NA                                    |
| python3-jinja2                                  | NA                                          | python3-jinja2.noarch- 2.10.1-3.el8   |
| python3-pexpect                                 | python3-pexpect - 4.8.0-5.3.5               | NA                                    |
| diffutils                                       | diffutils 3.6-4.3.1                         | diffutils-  3.6-6.el8                 |
| ccache                                          | ccache   - 3.4.2-1.9                        | NA                                    |
| which                                           | Which   - 1.22-1.22                         | which - 2.21-18.el8                   |
| debianutils                                     | NA                                          | NA                                    |
| iputils-ping                                    | NA                                          | iputils -20180629-10.el8              |
| libegl1-mesa                                    | Mesa-libEGL1   - 20.2.4-150300.59.6.1       | NA                                    |
| libsdl1.2-dev                                   | libSDL-1_2-0 - 1.2.15-150000.3.19.1         | NA                                    |
| pylint3                                         | pylint - 1.8.2-150000.3.3.1                 | NA                                    |
| python3                                         | python3( 3.6.15-150300.10.30.1)             | NA                                    |
| cpio                                            | cpio -2.12-3.9.1                            | cpio - 2.12-11.el8                    |
| git-core                                        | git-core - 2.35.3-150300.10.18.1            | NA                                    |
| tftp-server                                     | tftp-server  -4.3.1-1.99                    | NA                                    |
| gnupg                                           | GnuPG-Interface -0.52-bp153.1.3             | gnupg2-2.2.20-3.el8_6                 |

# README_content_v2023_1.txt

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2023.1 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2023.1 Open Components Source Code (TAR/GZIP) file: 
-----------------------------------------------------------------------

	This file contains the source code of all the SW components shipped as 
part of the PetaLinux tool. It also contains the source code for all the 
SW packages, available at https://petalinux.xilinx.com/ that petaLinux tool packages
 in the project, when selected. This file is provide as part of legal requirement 
for your viewing only. It is not required to be downloaded for using 
the PetaLinux tool or BSPs.



3.	Petalinux 2023.1 Board Supported Package specfic Sources and Licenses (TAR/GZIP) file:
----------------------------------------------------------------------------------------------

	This file contains the source code and licenses of all the SW components enabled
as part of this BSP. This file is provide as part of legal requirement for your viewing only.
It is not required to be downloaded for using the PetaLinux tool or BSPs.
		


Sample list of components in the files 1), 2) and 3):

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