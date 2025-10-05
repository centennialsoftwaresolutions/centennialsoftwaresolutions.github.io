## 000037095 - PetaLinux 2024.2 - Product Update Release Notes and Known Issues

## Nov 18, 2024 Knowledge

### Title

000037095 - PetaLinux 2024.2 - Product Update Release Notes and Known Issues

### Description

This Answer Record acts as the release notes for PetaLinux 2024.2 and contains links to information about resolved issues and updated collateral contained in this release.

The PetaLinux source code and images provided/generated are for demonstration purposes only. 

Please refer to https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/2741928025/Moving+from+PetaLinux+to+Production+Deployment

for more details.

Please find the installation requirements specified in our user guide [here](https://docs.xilinx.com/r/en-US/ug1144-petalinux-tools-reference-guide/Installation-Requirements). 

The packages required for installation per OS can also be found in the attached .xlsx (found at the bottom of this page) 

### Solution

## BSPs supported for the PetaLinux 2024.2 Release

This table contains supported BSPs for Zynq 7000, MicroBlaze, Zynq UltraScale+ MPSoC, and Versal available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/downloadNav/embedded-design-tools.html).

| SNO  | Platform               | Variant                   | BSP Name                                 | BSP Description                                              |
| ---- | ---------------------- | ------------------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 1    | Zynq 7000              | ZC702                     | xilinx-zc702-v2024.2-11110212.bsp        | **This BSP contains:**<br>**Hardware:** Vivado board presets with Zynq 7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_4bits.<br>**System Device Tree:** `system-top.dts` with board DTSI files, platform DTSI files, PSU init files, include files and bitstream file if exists.<br>**Software:** FSBL, U-Boot, Linux, device-tree (includes OpenAMP), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test bitstream, FSBL, U-Boot, Linux and rootfs for booting U-Boot and Linux. |
| 2    | Zynq UltraScale+ MPSoC | ZCU102 production silicon | xilinx-zcu102-v2024.2-11110212.bsp       | **This BSP contains:**<br>**Hardware (Extensible Platform):** Vivado board presets with PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.) with PL proc_sys_reset, axi_vip, axi_intc, axi_interconnect, axi_register_slice IPs.<br>**System Device Tree:** `system-top.dts` and related files.<br>**Vitis:** `pfm.tcl` packed for Vitis platform generation.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (OpenAMP, Xen), Ramdisk and Full rootfs.<br>**Pre-built Images:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 3    | Zynq UltraScale+ MPSoC | ZCU104 production silicon | xilinx-zcu104-v2024.2-11110212.bsp       | **This BSP contains:**<br>**Hardware:** PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR), VCU IP, clk_wiz, axi_interconnect, proc_sys_reset IPs.<br>**System Device Tree:** `system-top.dts` and related files.<br>**Vitis:** `pfm.tcl` packed for Vitis platform generation.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (OpenAMP, Xen), vcu-control, minimal and full rootfs (GStreamer, OpenMAX, V4L2, libdrm, vcu-examples).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 4    | Zynq UltraScale+ MPSoC | ZCU106 production silicon | xilinx-zcu106-v2024.2-11110212.bsp       | **This BSP contains:**<br>**Hardware 1/2 (Extensible Platform):** PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR), VCU IP, clk_wiz, axi_interconnect, proc_sys_reset IPs.<br>**System Device Tree:** `system-top.dts` and related files.<br>**Vitis:** `pfm.tcl` packed for Vitis platform.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (OpenAMP, Xen), fpga manager, vcu-control, minimal and full rootfs (GStreamer, OpenMAX, etc.).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 5    | Zynq UltraScale+ RFSoC | ZCU216                    | xilinx-zcu216-v2024.2-11110212.bsp       | **This BSP contains:**<br>**Hardware:** PS block (DDR, UART, SD, QSPI, Ethernet etc.) with ADC_DDR_DMA, DAC_DDR_DMA, CLOCKING blocks, axi_gpio IPs.<br>**System Device Tree:** `system-top.dts` and related files.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (OpenAMP, Xen), rfclk, rfdc-drivers, minimal and full rootfs (RFCLK, RDFC examples).<br>**Pre-built Images:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 6    | Zynq UltraScale+ RFSoC | ZCU208                    | xilinx-zcu208-v2024.2-11110212.bsp       | Similar to ZCU216 BSP; includes RFCLK, RDFC example applications. |
| 7    | Zynq UltraScale+ RFSoC | ZCU208-SDFEC              | xilinx-zcu208-sdfec-v2024.2-11110212.bsp | **Hardware:** PS block (DDR, UART, SD, QSPI, Ethernet etc.) with AXI stream, Monitor, SD-FEC, axi_gpio, AXI intc IPs.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, (OpenAMP, Xen), rfclk, rfdc-drivers, minimal/full rootfs (RFCLK, RDFC, SDFEC examples). |
| 8    | Zynq UltraScale+ RFSoC | ZCU670                    | xilinx-zcu670-v2024.2-11110212.bsp       | **Hardware:** zcu670 board specific silicon XSA.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, (OpenAMP, Xen), rfclk, rfdc-drivers, full rootfs with python3, dfe packages.<br>**Pre-built Images:** bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux, rootfs. |
| 15   | Versal                 | VCK190                    | xilinx-vck190-v2024.2-11110212.bsp       | **Hardware (Extensible Platform):** versal CIPS IP (DDR, UART, SD, QSPI, Ethernet, USB, etc) + AIE example.<br>**Vitis Platform & AIE Project:** Includes .xsa, xclbin, AIE app.<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux (OpenAMP, Xen), minimal/full rootfs (TCL, xrt, zocl, python, jupyter, notebooks).<br>**Pre-built Images:** PDI, PLM, PSMFW, TF-A, U-Boot, DTBs, Linux, rootfs, Xen.<br>**Note:** Supports vck190 rev1 & revA. |
| 16   | Versal                 | VCK190-OSPI               | xilinx-vck190-ospi-v2024.2-11110212.bsp  | Same as VCK190 but includes OSPI boot mode.                  |
| 17   | Versal                 | VCK190-EMMC               | xilinx-vck190-emmc-v2024.2-11110212.bsp  | Same as VCK190 but includes eMMC boot mode.                  |
| 18   | Versal                 | VMK180                    | xilinx-vmk180-v2024.2-11110212.bsp       | **Hardware:** CIPS IP (DDR, UART, SD, QSPI, Ethernet, USB).<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux (OpenAMP, Xen), rootfs with Tcl, python, libstdc++.<br>**Note:** Supports vmk180 rev1 & revA. |
| 19   | Versal                 | VPK120                    | xilinx-vpk120-v2024.2-11110212.bsp       | **Hardware:** CIPS IP (LPDDR, UART, SD, QSPI, Ethernet, USB).<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux (OpenAMP, Xen), minimal/full rootfs. |
| 20   | Versal                 | VPK180                    | xilinx-vpk180-v2024.2-11110212.bsp       | **Hardware:** CIPS IP (LPDDR, UART, SD, QSPI, Ethernet, USB), sysmon secure mode, multi-SLR.<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux (OpenAMP, Xen), minimal/full rootfs. |
| 21   | Versal                 | VHK158                    | xilinx-vhk158-v2024.2-11110212.bsp       | **Hardware:** CIPS IP with PS (JTAG, HBM, SD, OSPI, eMMC).<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux (OpenAMP, Xen).<br>**Note:** Boots from HBM by default. |
| 22   | Versal                 | VEK280                    | xilinx-vek280-v2024.2-11110212.bsp       | **Hardware:** CIPS IP (LPDDR, UART, SD, QSPI, Ethernet, USB) with sysmon enabled.<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux (OpenAMP, Xen), full rootfs with Tcl, xrt, zocl, python, AIE-example, notebooks, libvdu, vdu-firmware.<br>**Pre-built Images:** PDI, PLM, PSMFW, TF-A, U-Boot, Linux, rootfs, Xen. |

Unified Images supported for the 2024.2 PetaLinux Release

This table contains supported unified images for Zynq UltraScale+ MPSoC/RFSoC and Versal devices which are available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html)

| SNO  | Platform               | Variant | BSP Name                                     | BSP Description                                              |
| ---- | ---------------------- | ------- | -------------------------------------------- | ------------------------------------------------------------ |
| 1    | Zynq UltraScale+ MPSoC | —       | xilinx-zynqmp-common-v2024.2_11110212.tar.gz | **This Tar contains:**<br>bl31.elf, boot.scr, Image, rootfs.ext4, rootfs.manifest, rootfs.tar.gz, sdk.sh, u-boot.elf<br><br>**README.txt:** Describes the files and provides usage information. |
| 2    | Versal                 | —       | xilinx-versal-common-v2024.2_11110212.tar.gz | **This Tar contains:**<br>bl31.elf, boot.scr, Image, rootfs.ext4, rootfs.manifest, rootfs.tar.gz, sdk.sh, u-boot.elf<br><br>**README.txt:** Describes the files and provides usage information. |

XSCT BSPS

| SNO  | Platform               | Variant      | BSP Name                                      | BSP Description                                              |
| ---- | ---------------------- | ------------ | --------------------------------------------- | ------------------------------------------------------------ |
| 1    | Zynq UltraScale+ MPSoC | ZCU102       | xilinx-zcu102-xsct-v2024.2-11110212.bsp       | **This BSP contains:**<br>**Hardware (Extensible Platform):** This design uses Vivado board presets with Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.) with PL proc_sys_reset, axi_vip, axi_intc, axi_interconnect, axi_register_slice IPs.<br>**Vitis:** pfm.tcl is packed for generating Vitis platform.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (includes OpenAMP, Xen), Ramdisk Rootfs (minimal rootfs), Full rootfs.<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, TF-A, U-Boot, Linux and rootfs. |
| 2    | Zynq UltraScale+ MPSoC | ZCU104       | xilinx-zcu104-xsct-v2024.2-11110212.bsp       | **This BSP contains:**<br>**Hardware (Extensible Platform):** Vivado board presets with Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR) and VCU IP, clk_wiz, axi_interconnect, proc_sys_reset IPs.<br>**Vitis:** pfm.tcl is packed for generating Vitis platform.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (includes OpenAMP, Xen), vcu-control software, Ramdisk Rootfs (minimal), Full rootfs (includes GStreamer, OpenMAX, V4L2, libdrm, vcu-examples).<br>**Pre-built Images:** Ready to test images for booting U-Boot and Linux. |
| 3    | Zynq UltraScale+ MPSoC | ZCU106       | xilinx-zcu106-xsct-v2024.2-11110212.bsp       | **This BSP contains:**<br>**Hardware 1/2 (Extensible Platform):** Vivado board presets with Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.) and VCU DDR4 Controller, VCU IP, clk_wiz, axi_interconnect, proc_sys_reset IPs.<br>**Vitis:** pfm.tcl packed for generating platform.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (OpenAMP, Xen), fpga manager, vcu-control, Ramdisk Rootfs, Full rootfs (includes multimedia packages).<br>**Pre-built Images:** Ready to test bootable images. |
| 4    | Zynq UltraScale+ MPSoC | ZCU208       | xilinx-zcu208-xsct-v2024.2-11110212.bsp       | **This BSP contains:**<br>**Hardware:** Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, etc.) with ADC_DDR_DMA, DAC_DDR_DMA CLOCKING, axi_gpio IPs.<br>**Software:** FSBL, PMUFW, TF-A, U-Boot, Linux, device-tree (OpenAMP, Xen), rfclk, rfdc-drivers, Ramdisk Rootfs, Full rootfs (RFCLK/RFDC examples).<br>**Pre-built Images:** Bootable images included. |
| 5    | Zynq UltraScale+ MPSoC | ZCU216       | xilinx-zcu216-xsct-v2024.2-11110212.bsp       | Same as ZCU208 — includes RFSoC design with ADC/DAC DMA blocks, drivers, and example applications. |
| 6    | Zynq UltraScale+ RFSoC | zcu208-sdfec | xilinx-zcu208-sdfec-xsct-v2024.2-11110212.bsp | **This BSP contains:**<br>Hardware design with AXI stream, monitor blocks, SD-FEC, GPIO, and interrupt controllers.<br>Software includes RFCLK, RFDC, and SDFEC examples. |
| 7    | Zynq UltraScale+ RFSoC | ZCU670       | xilinx-zcu670-xsct-v2024.2-11110212.bsp       | **This BSP contains:**<br>Hardware: xsa with ZCU670 board-specific silicon.<br>Software: RFCLK/RFDC examples, Python3, DFE packages. |
| 8    | Versal                 | VEK280       | xilinx-vek280-xsct-v2024.2-11110212.bsp       | **This BSP contains:**<br>**Hardware:** Versal CIPS (LPDDR, UART, SD, QSPI, Ethernet, USB), sysmon, es silicon.<br>**Software:** PLM, PSMFW, TF-A, U-Boot, Linux, OpenAMP/Xen, Full rootfs with Tcl, XRT, zocl, python, AIE examples, jupyter notebooks.<br>**Pre-built Images:** Bootable images including Xen. |
| 9    | Versal                 | VMK180       | xilinx-vmk180-xsct-v2024.2-11110212.bsp       | **This BSP contains:**<br>Versal CIPS (DDR, UART, SD, QSPI, Ethernet, USB) design.<br>Includes PLM, PSMFW, TF-A, U-Boot, Linux, OpenAMP/Xen.<br>Supports both VMK180 rev1 and revA boards. |
| 10   | Versal                 | VPK120       | xilinx-vpk120-xsct-v2024.2-11110212.bsp       | Similar to VMK180 with LPDDR configuration.                  |
| 11   | Versal                 | VPK180       | xilinx-vpk180-xsct-v2024.2-11110212.bsp       | Versal design with sysmon in secure mode and multi-slave SLRs.<br>Bootable PDI and Xen images included. |
| 12   | Versal                 | VHK158       | xilinx-vhk158-xsct-v2024.2-11110212.bsp       | **This BSP contains:**<br>HBM-enabled design with OSPI/eMMC support.<br>Default boot from HBM. |
| 13   | Versal                 | VCK190       | xilinx-vck190-xsct-v2024.2-11110212.bsp       | **This BSP contains:**<br>Extensible platform with AIE example in PL, Vitis and AIE projects, full software stack (OpenAMP/Xen, Jupyter, Python3).<br>Supports rev1 and revA boards. |
| 14   | Versal                 | VCK190-EMMC  | xilinx-vck190-emmc-xsct-v2024.2-11110212.bsp  | Same as VCK190, but with eMMC boot module.                   |
| 15   | Versal                 | VCK190-OSPI  | xilinx-vck190-ospi-xsct-v2024.2-11110212.bsp  | Same as VCK190, but with OSPI boot module.                   |
| 22   | Zynq                   | ZC702        | xilinx-zc702-xsct-v2024.2-11110212.bsp        | **This BSP contains:**<br>Hardware: Zynq-7000 PS (DDR, UART, SD, QSPI, Ethernet) with AXI GPIO LEDs.<br>Software: FSBL, U-Boot, Linux, OpenAMP.<br>Pre-built Images: Bootable bitstream, FSBL, U-Boot, Linux, rootfs. |
| 23   | MicroBlaze             | SP701        | xilinx-sp701-xsct-v2024.2-11110212.bsp        | **This BSP contains:**<br>Hardware: MicroBlaze Processor with AXI I2C, GPIO, DDR, QSPI, UARTLite, LEDs, Ethernet.<br>Software: fs-boot, U-Boot, Linux, device-tree, rootfs (minimal).<br>Pre-built Images: Ready-to-test bootable set. |

## PetaLinux 2024.2 contains the following build collateral:

## Commits Information

The following table contains Repo, Tag, and commit ID information for the 2024.2 Release.

## Meta Layers

| Component              | Branch      | Commit ID                                | URL                                                          |
| ---------------------- | ----------- | ---------------------------------------- | ------------------------------------------------------------ |
| yocto-scripts          | rel-v2024.2 | 46e44e6c37a6af28074cbb35d7da2f799225bb58 | [Link](https://github.com/Xilinx/yocto-scripts/tree/rel-v2024.2) |
| yocto-manifests        | rel-v2024.2 | 24efacab2d8451f64446d76fdda87ccd1ce760f6 | [Link](https://github.com/Xilinx/yocto-manifests/tree/rel-v2024.2) |
| poky                   | rel-v2024.2 | e86fd88e8efbbc2aa4730776ab284e072d57da04 | [Link](https://github.com/Xilinx/poky/tree/rel-v2024.2)      |
| meta-xilinx-tsn        | rel-v2024.2 | 6a6c645f104f8c822c857933eb560bf9003843b8 | [Link](https://github.com/Xilinx/meta-xilinx-tsn/tree/rel-v2024.2) |
| meta-xilinx-tools      | rel-v2024.2 | 34c19155fe66a6863c3b4f95b867ef32faf300b0 | [Link](https://github.com/Xilinx/meta-xilinx-tools/tree/rel-v2024.2) |
| meta-xilinx            | rel-v2024.2 | 7c79383570dc4182bb21cdee68598ccf47403150 | [Link](https://github.com/Xilinx/meta-xilinx/tree/rel-v2024.2) |
| meta-vitis             | rel-v2024.2 | e67ca9ef8ec8dc085edf397c55b33f46094d1716 | [Link](https://github.com/Xilinx/meta-vitis/tree/rel-v2024.2) |
| meta-virtualization    | rel-v2024.2 | f8a35f5e39eeb122be4e29b289102211bc63beea | [Link](https://github.com/Xilinx/meta-virtualization/tree/rel-v2024.2) |
| meta-system-controller | rel-v2024.2 | f06303b078538f4ea7fef90112277751ccf0f347 | [Link](https://github.com/Xilinx/meta-system-controller/tree/rel-v2024.2) |
| meta-security          | rel-v2024.2 | 459d837338ca230254baa2994f870bf6eb9d0139 | [Link](https://github.com/Xilinx/meta-security/tree/rel-v2024.2) |
| meta-ros               | rel-v2024.2 | ff76fa90fb66d0b83238d99f882c60f2373eb875 | [Link](https://github.com/Xilinx/meta-ros/tree/rel-v2024.2)  |
| meta-rauc              | rel-v2024.2 | 1e3e6b334defd7fbf95cb43d23975e7b3de4b520 | [Link](https://github.com/Xilinx/meta-rauc/tree/rel-v2024.2) |
| meta-qt5               | rel-v2024.2 | eb828418264a49b8d00035cb3d7b12fcea3be801 | [Link](https://github.com/Xilinx/meta-qt5/tree/rel-v2024.2)  |
| meta-petalinux         | rel-v2024.2 | 559ddcca5b8a9e9ed806666d62beab4e8cf4fc2d | [Link](https://github.com/Xilinx/meta-petalinux/tree/rel-v2024.2) |
| meta-openembedded      | rel-v2024.2 | 735ae0310870ffce07ce0c55c4f87c20ac161ff9 | [Link](https://github.com/Xilinx/meta-openembedded/tree/rel-v2024.2) |
| meta-openamp           | rel-v2024.2 | 68049285b561f071bd7cc093f9ecbe4f5518ddf9 | [Link](https://github.com/Xilinx/meta-openamp/tree/rel-v2024.2) |
| meta-mingw             | rel-v2024.2 | acbba477893ef87388effc4679b7f40ee49fc852 | [Link](https://github.com/Xilinx/meta-mingw/tree/rel-v2024.2) |
| meta-kria              | rel-v2024.2 | ee572f578f8d8e416e1b218a3bb05ae530163295 | [Link](https://github.com/Xilinx/meta-kria/tree/rel-v2024.2) |
| meta-jupyter           | rel-v2024.2 | 6b9b2542f3e52d30f5100747ce312dc46791c5cc | [Link](https://github.com/Xilinx/meta-jupyter/tree/rel-v2024.2) |
| meta-embedded-plus     | rel-v2024.2 | e53324381f5a575c0e6b8b43c81cdbff9a2118b5 | [Link](https://github.com/Xilinx/meta-embedded-plus/tree/rel-v2024.2) |
| meta-aws               | rel-v2024.2 | 4ab666977b3a91ada750d6a0b70af8a7945dfea4 | [Link](https://github.com/Xilinx/meta-aws/tree/rel-v2024.2)  |
| meta-arm               | rel-v2024.2 | 1947c000299c0330e8a866996505221a14c0e1ea | [Link](https://github.com/Xilinx/meta-arm/tree/rel-v2024.2)  |
| meta-amd-adaptive-socs | rel-v2024.2 | 1f7d1d78192eb3ca0bd32873d49b4351c5d08183 | [Link](https://github.com/Xilinx/meta-amd-adaptive-socs/tree/rel-v2024.2) |

## SSW Components

| Component               | Branch               | Commit ID                                | URL                                                          |
| ----------------------- | -------------------- | ---------------------------------------- | ------------------------------------------------------------ |
| gen-machine-conf        | xlnx_rel_v2024.2     | 3e691e28bf47876fb7e0c4be3c62be6b9d46bf87 | [GitHub](https://github.com/Xilinx/gen-machine-conf)         |
| openamp-demo-notebooks  | main                 | 30b76d864261e5dd321fadfaf74b933b7cd88892 | [GitHub](https://github.com/Xilinx/OpenAMP-notebooks)        |
| tsn-utils               | main                 | 22859262a9d7834785a36c09d09904e727e4811e | [GitHub](https://github.com/Xilinx/tsn-utils)                |
| tsn-examples            | main                 | b68dc4efb12954623148d60e188d77f85f887acb | [GitHub](https://github.com/Xilinx/tsn-talker-listener)      |
| ai-engine-driver        | xlnx_rel_v2024.2     | 8845d962e5b30b576c87dcf6635fb84a90ef1e36 | [GitHub](https://github.com/Xilinx/aie-rt)                   |
| board-id-data           | xlnx_rel_v2024.1     | b2ae845b7b1b24f82a9410c2db5bc2eae5b4a545 | [GitHub](https://github.com/Xilinx/xlnx-board-id-data)       |
| labtool-jtag-support    | xlnx_rel_v2024.2     | 1ea8d52c4f173541075036ac11ad7c8241b4a346 | [GitHub](https://github.com/Xilinx/systemctl-labtool)        |
| power-advantage-tool    | xlnx_rel_v2023.2     | 6a527f77fd865c2edd4463a9798486e7d34a43bf | [GitHub](https://github.com/Xilinx/jupyter-pat)              |
| pm-notebooks            | xlnx_rel_v2023.2     | c502be361b6857e21ab903f31c9ead69e3a0d9ba | [GitHub](https://github.com/Xilinx/platform-management-notebooks) |
| image-update            | master               | 1bd7d7405b484d808176c6e711691a846c18b4f0 | [GitHub](https://github.com/Xilinx/linux-image_update)       |
| xlnx-platformstats      | master               | c5771895bf1b9d68785a0cb8e24b5220d4bb9748 | [GitHub](https://github.com/Xilinx/xlnx_platformstats)       |
| ddr-qos                 | master               | 26ab6bb5837a1c48c600c6c61f3d214e8c633808 | [GitHub](https://github.com/Xilinx/ddr-qos)                  |
| axi-qos                 | master               | 1efd01554f9f1d79e69ceab5db242a6f5813e9cc | [GitHub](https://github.com/Xilinx/axi-qos)                  |
| kria-dashboard          | xlnx_rel_v2024.1     | 550a59619ad63b9d4bf1ebc7c31988862e4fa0ea | [GitHub](https://github.com/Xilinx/kria-dashboard)           |
| xmutil                  | master               | 51510bb0fd7d586841709a49c493fe3398bd2d2c | [GitHub](https://github.com/Xilinx/xmutil)                   |
| dfx-mgr                 | xlnx_rel_v2024.2     | 839e8e646c54a63326e36c48a7bd879f5e8efa31 | [GitHub](https://github.com/Xilinx/dfx-mgr)                  |
| image-builder           | xlnx_rel_v2024.1     | 297a48f8635713a14469a92d49f7e292554dedc9 | [GitHub](https://github.com/Xilinx/imagebuilder)             |
| sdfec                   | xlnx_rel_v2024.1     | 84b31cb194325640a631380ed8bfc1db21bab883 | [GitHub](https://github.com/Xilinx/linux-examples)           |
| libdfx                  | xlnx_rel_v2024.2     | af8d735fae286e7bc94c830a86c960598a4ac014 | [GitHub](https://github.com/Xilinx/libdfx)                   |
| pmtool                  | 2.0                  | 517110007c67e1cd7142a760aa88ca28ebf7080e | [GitHub](https://github.com/Xilinx/system-controller-pmtool) |
| scweb                   | xlnx_rel_v2024.2     | 886a9b2d4dc98fbd7569dea6a90fa045b4c1cccf | [GitHub](https://github.com/Xilinx/system-controller-web)    |
| bootgen                 | xlnx_rel_v2024.2     | 6f448fece5d999985128fd454ae047e065a5e45d | [GitHub](https://github.com/Xilinx/bootgen)                  |
| gstreamer1.0            | xlnx-rebase-v1.22.12 | d036bef6c66d7e2351e0f7252d653bca137efe90 | [GitHub](https://github.com/Xilinx/gstreamer)                |
| system-controller-app   | master               | fabff460f708ef4cc0c288dabec6bc17b76e13f5 | [GitHub](https://github.com/Xilinx/system-controller-app)    |
| xrt                     | 2024.2               | d05b18dc38cc6804ecb4b3dbe6de23f158319567 | [GitHub](https://github.com/Xilinx/XRT)                      |
| gstreamer-vdu-notebooks | xlnx_rel_v2024.2     | ef7a7236144a04977cb5bb800d6d7cf319e52b58 | [GitHub](https://github.com/Xilinx/multimedia-notebooks)     |
| lopper                  | master               | c0facd087263a24a83f7fad917884348db03175d | [GitHub](https://github.com/devicetree-org/lopper)           |
| kernel-module-dp        | master               | e20942b256e6fb18eaef919c7441f65ad8afcf43 | [GitHub](https://github.com/xilinx/dp-modules)               |
| kernel-module-hdmi21    | master               | 26a1d40723c58783f7aedba028a208ab9410df5f | [GitHub](https://github.com/Xilinx/hdmi21-modules)           |
| kernel-module-hdmi      | xlnx_rel_v2024.2     | 4bb89eb3f3062eac8de1aa2b7e64d7f861e18caa | [GitHub](https://github.com/Xilinx/hdmi-modules)             |
| vdu-firmware            | xlnx_rel_v2024.2     | 724de80630edcb87d865d69f1a6c0dc61c3f9f12 | [GitHub](https://github.com/Xilinx/vdu-firmware)             |
| libvdu-ctrlsw           | xlnx_rel_v2024.2     | 361a822a223dc430ca44641be148fe1cbc13dd10 | [GitHub](https://github.com/Xilinx/vdu-ctrl-sw)              |
| kernel-module-vdu       | xlnx_rel_v2024.2     | 25773344ce1e539e7136c5a30cdee98a6cf490a8 | [GitHub](https://github.com/Xilinx/vdu-modules)              |
| libvdu-omxil            | xlnx_rel_v2024.2     | af9c6e8935799f4dcd579b0164dd05eb039b569d | [GitHub](https://github.com/Xilinx/vdu-omx-il)               |
| libomxil-xlnx           | xlnx_rel_v2024.2     | b259cf0b3eaa1b0b17d2e807f233bfef5b9dbddd | [GitHub](https://github.com/Xilinx/vcu-omx-il)               |
| kernel-module-vcu       | xlnx_rel_v2024.2     | 91d19a16308a438596138d30d8174e148fc45584 | [GitHub](https://github.com/Xilinx/vcu-modules)              |
| libvcu-xlnx             | xlnx_rel_v2024.2     | bcb5ff5f77f2a8ea8222eb64b69c1f9f730cc6b1 | [GitHub](https://github.com/Xilinx/vcu-ctrl-sw)              |
| vcu-firmware            | xlnx_rel_v2024.2     | 83d64885c681e835dd7d54064c6c2f66c46071d3 | [GitHub](https://github.com/Xilinx/vcu-firmware)             |
| open-amp-xlnx           | xlnx_rel_v2024.2     | 47caef116ccbf5d5a9778082a98fe8f3710b549c | [GitHub](https://github.com/Xilinx/open-amp)                 |
| libmetal-xlnx           | xlnx_rel_v2024.2     | e2fdb4fecbebe41b4cd1c0b4fbfa3496bcded485 | [GitHub](https://github.com/Xilinx/libmetal)                 |
| libmali-xlnx            | xlnx_rel_v2024.2     | 644dc96597172e3cf15aea63b4ee947d421810aa | [GitHub](https://github.com/Xilinx/mali-userspace-binaries)  |
| runx-xlnx               | xlnx_rebase_1.1      | 0c7edb3453398d7a0c594ce026c9c1e93c2541cc | [GitHub](https://github.com/Xilinx/runx)                     |
| xen                     | xlnx_rebase_4.18     | c9de96c0cbe9b2f2aa5e55a0e1e645ca72865102 | [GitHub](https://github.com/Xilinx/xen)                      |
| qemu-xilinx             | xlnx_rel_v2024.2     | 01482fa113dcbfa785feb7d513df50d15ec4c5df | [GitHub](https://github.com/Xilinx/qemu)                     |
| qemu-devicetrees-native | xlnx_rel_v2024.2     | a6eeb7ec0fdb765ab0057d95eb6201d97359eff9 | [GitHub](https://github.com/Xilinx/qemu-devicetrees)         |
| device-tree             | xlnx_rel_v2024.2     | 5627d845bcc9006c18cb957f8f360b405d60c86d | [GitHub](https://github.com/Xilinx/device-tree-xlnx)         |
| fsbl-firmware           | xlnx_rel_v2024.2     | 6e4d0b89d2958994ab9b3531eb4c6e648a63f201 | [GitHub](https://github.com/Xilinx/embeddedsw)               |
| trusted-firmware-a      | xlnx_rebase_v2.10    | 14cea4616b6edaceabb607c7c92332436a1699e5 | [GitHub](https://github.com/Xilinx/arm-trusted-firmware)     |
| u-boot-xlnx             | xlnx_rebase_v2024.01 | 7f6ec94aac7eacfec07bd45c83a6d17df4b7d383 | [GitHub](https://github.com/Xilinx/u-boot-xlnx)              |
| linux-xlnx              | xlnx_rebase_v6.6_LTS | 2b7f6f70a62a52a467bed030a27c2ada879106e9 | [GitHub](https://github.com/Xilinx/linux-xlnx)               |

## PetaLinux components

| Component               | Branch           | Commit ID                                | URL                                                          |
| ----------------------- | ---------------- | ---------------------------------------- | ------------------------------------------------------------ |
| system-device-tree-xlnx | xlnx_rel_v2024.2 | 08bd7d03ea709e9f5c2b7eafae39607bb2a00c65 | [GitHub](https://github.com/Xilinx/system-device-tree-xlnx/tree/xlnx_rel_v2024.2) |
| meta-petalinux-tools    | xlnx_rel_v2024.2 | bf13c624141ec68a10f4441db808007acd45494d | [GitHub](https://github.com/Xilinx/meta-petalinux-tools/tree/xlnx_rel_v2024.2) |

## Open Source components New Features

- See [here ](https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/3089891329/2024.2+Release+Notes+for+Open+Source+Components)for the list of features

## Known Issues for the 2024.2 release

| Linux/Baremetal | Components          | Platform/SoC Supported | Work-around Article Description and Link                     | To be Fixed Version |
| --------------- | ------------------- | ---------------------- | ------------------------------------------------------------ | ------------------- |
| Linux           | PetaLinux           | —                      | 2024.2 SDT Flow: Serial settings except TF-A are not reflecting as per config changes for SDT BSPs with PetaLinux 2024.2 | 2025.1              |
| Linux           | PetaLinux           | —                      | 2024.2 PetaLinux: `petalinux-config` advanced flash settings flags have no effect | 2025.1              |
| Linux           | Yocto               | All                    | 2024.2 PetaLinux/Yocto: `meta-ros2-jazzy` hardware-interface fails to build with Scarthgap | 2025.1              |
| Linux           | Platform Management | Versal                 | 2024.2 Versal: Linux boot hangs randomly during subsystem restart stress test when Linux CPU idle is enabled | 2025.1              |
| All             | Platform Management | Versal, Versal-Net     | 2024.2 Versal: Linux boot hangs when IPI_CRC enabled         | 2025.1              |
| Linux           | SDT / XXV Ethernet  | ZynqMP, Versal         | [000037116 - Zynq MP - Boot with AXI 10G MCDMA and no 1588 hangs in SDT flow](#) | 2025.1              |
| Linux           | SDT                 | PL                     | [000037123 - 2024.1 - reset-gpios Property Missing in Device Trees When the Slice IP is Not Used Between AXI GPIO IP and the HLS Video Processing IPs](#) | 2025.1              |
| Linux           | SDT                 | PL                     | [000037125 - 2024.1: How to Get the "xlnx,versal-gt" and "dp-gtquad" properties of the DisplayPort 1.4 RX Subsystem Node in the Device Tree for a VCK190](#) | 2025.1              |
| Linux           | SDT                 | PL                     | 2024.1 - AXI4-Stream Subset Converter Node Missing in Device Tree | 2025.1              |
| Linux           | PetaLinux           | Kintex 7               | 2024.2: BPI flash programming fails on KC705 with `program_flash` utility | 2025.1              |
| Linux           | PetaLinux           | All                    | [000037108 - 2024.2 Versal: PetaLinux get hw-description configuration fails if SMMU-CCI is enabled in the design](#) | 2025.1              |
| Baremetal       | lwIP                | ZynqMP, Versal         | 2024.2: Issues when using LWIP220 with Vitis Unified IDE     | 2025.1              |
| Linux           | DTG                 | All                    | 2024.2: Observed a DTG error while using the 2024.2 L20 MRMAC design during the PetaLinux build | 2025.1              |
| Linux           | Yocto               | All                    | 2024.2 PetaLinux/Yocto: Firmware files do not install on rootfs using `dfx_user_dts` bbclass | 2025.1              |
| Linux           | DTG                 | All                    | 2024.2: Video Codec Unit v1.2 - Media node is missing while upgrading the 2023.1 VCU TRD designs to the 2024.2 build | 2025.1              |
| All             | U-Boot              | Versal                 | Versal - 2024.2: Flash Lock/Unlock not working for ISSI QSPI/OSPI parts | 2025.1              |
| Linux           | Platform Management | Versal                 | 2024.2: SD and QSPI Boot fails with Versal isolation enabled CCI/SMMU designs | 2025.1              |

# 2024.2_PetaLinux_OS_Package_List.xlsx

## Linux Distribution OS details:

 Desktop (From Everything.ISO): Development and Creative workstation.

1. Ubuntu 20.04.5,20.04.6 and Ubuntu 22.04.1,22.04.2,22.04.3,22.04.4,24.04
2. Ubuntu 20.04.5,20.04.6,22.04 and Ubuntu 22.04.1,22.04.2,22.04.3,22.04.4,24.04 Server.
3. OPEN SUSE LEAP 15.4,Almalinux 8.7,Almalinux 9.1,Almalinux 8.10,Almalinux 9.4  (From Everything.ISO): Infrastructure server
  4.OPEN SUSE LEAP 15.4 ,Almalinux 8.7,Almalinux 9.1,Almalinux 8.10,Almalinux 9.4 Desktop,Rhel 9.4 (From Everything.ISO): Development and Creative workstation.
  Note: 
4. Empty packages are not installed means assuming these are default from Linux Distribution.
5. For RHEL/CentOS/Suse you need to installGitPython and jinja2 using pip3 commands as mentioned below.
  Host GCC Version Upgrade:
  From 2021.1 release, the gcc version should be greater than 6. Using lower versions of gcc causes build issues. You can also enable the Enable buildtools extended option from petalinux -config → Yocto settings, which uses the pre-compiled gcc binaries from the PetaLinux tool.  

## Quick Installation steps for packages

### Almalinux and Rhel Desktop/Server 64-bit

```
sudo yum/Zypper install net-tools gawk make wget tar bzip2 gzip python3 unzip perl patch diffutils diffstat git cpp gcc gcc-c++ glibc-devel texinfo chrpath socat perl-Data-Dumper perl-Text-ParseWords perl-Thread-Queue python3-pip python3-GitPython python3-jinja2 python3-pexpect xz which SDL-devel xterm autoconf libtool.x86_64 zlib-devel automake glib2-devel zlib ncurses-devel openssl-devel dos2unix flex bison glibc.i686 glibc.x86_64 screen pax glibc-devel.i686 compat-libstdc++-33.i686 libstdc++.i686 libstdc++.x86_64
pip3 install GitPython jinja2
```

### Ubuntu  Desktop/Server 64 bit

```
sudo apt-get install iproute2 gawk python3 python build-essential gcc git make net-tools libncurses5-dev tftpd zlib1g-dev libssl-dev flex bison libselinux1 gnupg wget git-core diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib automake zlib1g:i386 screen pax gzip cpio python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3
```

## Tool/Library Versions

### Ubuntu

| Tool/Library                                    | Ubuntu Desktop /Server 20.04.6(64-bit) | Ubuntu Desktop /Server 22.04.1(64-bit)     | Ubuntu Desktop /Server 22.04.2(64-bit) | Ubuntu Desktop /Server 22.04.3(64-bit) | Ubuntu Desktop /Server 22.04.4(64-bit) | Ubuntu Desktop /Server 20.04.5(64-bit) | Ubuntu Desktop /Server 24.04(64-bit) |
| ----------------------------------------------- | -------------------------------------- | ------------------------------------------ | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | ------------------------------------ |
| gawk                                            | gawk-1:5.0.1+dfsg-1                    | gawk-1:5.1.0-1build3                       | gawk-1:5.1.0-1build3                   | gawk-1:5.1.0-1ubuntu0.1                | gawk-1:5.1.0-1ubuntu0.1                | gawk-1:5.0.1+dfsg-1                    | gawk-1:5.2.1-2build3                 |
| gcc                                             | gcc-4:9.3.0-1ubuntu2                   | gcc-4:11.2.0-1ubuntu1                      | gcc-4:11.2.0-1ubuntu1                  | gcc-4:11.2.0-1ubuntu1                  | gcc-4:11.2.0-1ubuntu1                  | gcc-4:9.3.0-1ubuntu2                   | gcc-4:13.2.0-7ubuntu1                |
| netstat (net-tools)                             | NA                                     | NA                                         | NA                                     | NA                                     | NA                                     | NA                                     | NA                                   |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-6.2-0ubuntu2             | ncurses-devel-6.3-2ubuntu0.1               | ncurses-6.3-2ubuntu0.1                 | ncurses-6.3-2ubuntu0.1                 | ncurses-6.3-2ubuntu0.1                 | ncurses-6.2-0ubuntu2.1                 | ncurses-6.4+20240113-1ubuntu2        |
| zlib-devel(also,install 32-bit of this version) | NA                                     | NA                                         | NA                                     | NA                                     | NA                                     | NA                                     | NA                                   |
| openssl-devel                                   | openssl -1.2.28-2                      | openssl -3.0.2-0ubuntu1.9                  | openssl -1.2.33-1build2                | openssl -1.2.33-1build2                | openssl -21.0.0-1                      | openssl -1.1.1f-1ubuntu2.16            | openssl -3.0.13-0ubuntu3.1           |
| libselinux                                      | libselinux-3.0-1build2                 | libselinux1-3.3-1build2                    | NA                                     | libselinux-3.3-1build2                 | libselinux-3.3-1build2                 | libselinux-3.0-1build2                 | libselinux-3.5-2ubuntu2              |
| xterm                                           | xterm-353-1ubuntu1.20.04.2             | xterm-372-1ubuntu1                         | xterm-372-1ubuntu1                     | xterm-372-1ubuntu1                     | xterm-372-1ubuntu1                     | xterm-353-1ubuntu1.20.04.2             | xterm-390-1ubuntu3                   |
| zlib1g-dev                                      | zlib1g-dev-1:1.2.11.dfsg-2ubuntu1.5    | zlib1g-dev:amd64 -1:1.2.11.dfsg-2ubuntu9.2 | zlib1g-1:1.2.11.dfsg-2ubuntu9.2        | zlib1g-1:1.2.11.dfsg-2ubuntu9.2        | zlib1g-1:1.2.11.dfsg-2ubuntu9.2        | zlib1g-1:1.2.11.dfsg-2ubuntu1.5        | zlib1g-1:1.3.dfsg-3.1ubuntu2.1       |
| gcc-multilib                                    | gcc-multilib-4:9.3.0-1ubuntu2          | gcc-multilib -4:11.2.0-1ubuntu1            | gcc-multilib -4:11.2.0-1ubuntu1        | gcc-multilib -4:11.2.0-1ubuntu1        | gcc-multilib -4:11.2.0-1ubuntu1        | gcc-multilib -4:9.3.0-1ubuntu2         | gcc-multilib -4:13.2.0-7ubuntu1      |
| build-essential                                 | build-essential-12.8ubuntu1.1          | build-essential-12.9ubuntu3                | build-essential  -12.9ubuntu3          | build-essential  -12.9ubuntu3          | build-essential  -12.9ubuntu3          | build-essential-12.8ubuntu1.1          | build-essential -12.10ubuntu1        |
| automake                                        | automake -1:1.16.1-4ubuntu6            | automake-1:1.16.5-1.3                      | automake-1:1.16.5-1.3                  | automake-1:1.16.5-1.3                  | automake-1:1.16.5-1.3                  | automake-1:1.16.1-4ubuntu6             | automake-1:1.16.5-1.3ubuntu1         |
| screen                                          | screen -4.8.0-1ubuntu0.1               | screen  - 4.9.0-1                          | screen-4.9.0-1                         | screen-4.9.0-1                         | screen-4.9.0-1                         | screen-4.8.0-1ubuntu0.1                | screen-4.9.1-1build1                 |
| libstdc++                                       | libstdc++-9.4.0-1ubuntu1~20.04.2       | libstdc-11.4.0-1ubuntu1~22.04              | libstdc++--12.3.0-1ubuntu1~22.04       | libstdc++-11.4.0-1ubuntu1~22.04        | libstdc++-11.4.0-1ubuntu1~22.04        | libstdc++-9.4.0-1ubuntu1~20.04.2       | libstdc++-13.2.0-23ubuntu4           |
| g++ (gcc-c++)                                   | g++ -4:9.3.0-1ubuntu2                  | g++ -4:11.2.0-1ubuntu1                     | g++ -4:11.2.0-1ubuntu1                 | g++ -4:11.2.0-1ubuntu1                 | g++ -4:11.2.0-1ubuntu1                 | g++ -4:9.3.0-1ubuntu2                  | g++ -4:13.2.0-7ubuntu1               |
| python3-pip                                     | NA                                     | NA                                         | NA                                     | NA                                     | NA                                     | NA                                     | NA                                   |
| xz(xz-utils)                                    | xz-utils -5.2.4-1ubuntu1.1             | xz-utils-5.2.5-2ubuntu1                    | xz-utils-5.2.5-2ubuntu1                | xz-utils-5.2.5-2ubuntu1                | xz-utils-5.2.5-2ubuntu1                | xz-utils-5.2.4-1ubuntu1.1              | xz-utils- 5.6.1+really5.4.5-1        |
| cpp                                             | cpp-4:9.3.0-1ubuntu2                   | cpp-4:11.2.0-1ubuntu1                      | cpp-4:11.2.0-1ubuntu1                  | cpp-4:11.2.0-1ubuntu1                  | cpp-4:11.2.0-1ubuntu1                  | cpp-4:9.3.0-1ubuntu2                   | cpp-4:13.2.0-7ubuntu1                |
| patch                                           | patch-2.7.6-6                          | patch-2.7.6-7build2                        | patch-2.7.6-7build2                    | patch-2.7.6-7build2                    | patch-2.7.6-7build2                    | patch-2.7.6-6                          | patch-2.7.6-7build3                  |
| python3- GitPython(python3-git)                 | NA                                     | NA                                         | NA                                     | NA                                     | NA                                     | NA                                     | NA                                   |
| python3-jinja2                                  | python3-jinja2-2.10.1-2                | python3-jinja2-3.0.3-1                     | NA                                     | python3-3.0.3-1                        | python3-3.0.3-1                        | python3-jinja2-2.10.1-2                | NA                                   |
| python3-pexpect                                 | python3-4.6.0-1build1                  | python3-pexpect-4.8.0-2ubuntu1             | python3-4.8.0-2ubuntu1                 | python3-4.8.0-2ubuntu1                 | python3-4.8.0-2ubuntu1                 | python3-pexpect-4.6.0-1build1          | NA                                   |
| diffutils                                       | diffutils-1:3.7-3                      | diffutils-1:3.8-0ubuntu2                   | diffutils-1:3.8-0ubuntu2               | diffutils-1:3.8-0ubuntu2               | diffutils-1:3.8-0ubuntu2               | diffutils-1:3.7-3                      | diffutils-1:3.10-1build1             |
| debianutils                                     | debainutils-4.9.1                      | debianutils -5.5-1ubuntu2                  | debianutils-5.5-1ubuntu2               | debianutils-5.5-1ubuntu2               | debianutils-5.5-1ubuntu2               | debianutils-4.9.1                      | debianutils-5.17build1               |
| iputils-ping                                    | iputils-ping-3:20190709-3              | iputils-ping-3:20211215-1                  | iputils-ping-3:20211215-1              | iputils-ping-3:20211215-1              | iputils-ping-3:20211215-1              | iputils-ping-3:20190709-3              | iputils-ping-3:20240117-1build1      |
| libegl1-mesa                                    | NA                                     | NA                                         | libegl1-mesa-23.2.1-1ubuntu3.1~22.04.2 | NA                                     | NA                                     | NA                                     | NA                                   |
| libsdl1.2-dev                                   | NA                                     | NA                                         | 23.2.1-1ubuntu3.1~22.04.2              | NA                                     | NA                                     | NA                                     | NA                                   |
| pylint3                                         | NA                                     | NA                                         | NA                                     | NA                                     | NA                                     | NA                                     | NA                                   |
| python3                                         | python3-3.8.2-0ubuntu2                 | python3-3.10.6-1~22.04                     | python3-3.10.6-1~22.04                 | python3-3.10.6-1~22.04                 | python3-3.10.6-1~22.04                 | python3-.3.8.2-0ubuntu2                | python3-3.12.3-0ubuntu1              |
| cpio                                            | cpio-2.13+dfsg-2ubuntu0.3              | cpio-2.13+dfsg-7                           | cpio -2.13+dfsg-7                      | cpio -2.13+dfsg-7                      | cpio -2.13+dfsg-7                      | cpio -2.13+dfsg-2ubuntu0.3             | cpio -2.15+dfsg-1ubuntu2             |
| gnupg                                           | gnupg-2.2.19-3ubuntu2.2                | gnupg-2.2.27-3ubuntu2.1                    | gnupg-2.2.27-3ubuntu2.1                | gnupg-2.2.27-3ubuntu2.1                | gnupg-2.2.27-3ubuntu2.1                | gnupg- 2.2.19-3ubuntu2.2               | gnupg-2.4.4-2ubuntu17                |
| bind-utils                                      | N/A                                    | N/A                                        | N/A                                    | N/A                                    | N/A                                    | N/A                                    | N/A                                  |

### Rhel/Opensuse/Almalinux Versions

| Tool/Library                                    | Rhel 9.4 Desktop /Server (64-bit)  | Opensuse Leap 15.4 Desktop /Server (64-bit) | Almalinux 8.7 Desktop /Server (64-bit) | Almalinux 9.4 Desktop /Server (64-bit) | Almalinux 8.10 Desktop /Server (64-bit) | Almalinux 9.1 Desktop /Server (64-bit) |
| ----------------------------------------------- | ---------------------------------- | ------------------------------------------- | -------------------------------------- | -------------------------------------- | --------------------------------------- | -------------------------------------- |
| gawk                                            | gawk- 5.1.0-6.el9                  | gawk-1.35.0-150400.4.5.1                    | gawk-4.2.1-4.el8                       | gawk-5.1.0-6                           | gawk-4.2.1-4                            | gawk-11.4.1-3.el9                      |
| gcc                                             | gcc-11.4.1-3.el9                   | gcc - 7.5.0+r278197-150000.4.35.1           | gcc-8.5.0-22                           | gcc - 11.4.1-3                         | gcc-8.5.0-22                            | gcc-11.4.1-3.el9                       |
| netstat (net-tools)                             | net-tools-2.0-0.62.20160912git.el9 | net-tools -2.0+git20170221.479bb4a-3.11     | net-tools -2.0-0.52.20160912git        | net-tools-2.0-0.62.20160912git         | net-tools -2.0-0.52.20160912git         | net-tools -2.0-0.62.20160912git.el9    |
| ncurses-devel(libncurses5-dev)                  | ncurses -devel-6.2-10.20210508.el9 | ncurses - 4.3.3-150400.1.5                  | ncurses - 6.1-10.20180224              | ncurses-6.1-10.20180224                | ncurses - 6.1-10.20180224               | ncurses - 6.1-10.20180224              |
| zlib-devel(also,install 32-bit of this version) | zlib-1.2.11-bp153.1.81             | zlib-devel-1.12-bp154.1.31                  | zlib-devel-1.2.11-25                   | zlib-devel-1.2.11-39.el9               | zlib-devel-1.2.11-25                    | zlib-devel-1.2.11-40                   |
| openssl-devel                                   | openssl-1:3.0.7-28.el9_4           | openssl- 1.1.1l-150400.1.5                  | openssl- 1:1.1.1k-12                   | openssl- 1:3.0.1-43.el9                | openssl- 1:1.1.1k-7.el8                 | openssl- 1:3.0.1-43                    |
| libselinux                                      | libselinux  -3.6-1.el9             | libselinux  - 3.1-150400.1.69               | libselinux -2.9-8                      | libselinux -3.5-1.el9                  | libselinux -2.9-6.el8                   | libselinux -3.6-1.el9                  |
| xterm                                           | xterm-366-9.el9                    | xterm- 330-150200.11.12.1                   | xterm-331-2                            | xterm-366-8.el9                        | xterm-331-2.el8                         | xterm-366-9.el9                        |
| zlib1g-dev                                      | zlib1g-1.2.11-40.el9               | NA                                          | NA                                     | zlib1g-devel-1.2.11-40                 | NA                                      | NA                                     |
| gcc-multilib                                    | NA                                 | NA                                          | NA                                     | NA                                     | NA                                      | NA                                     |
| build-essential                                 | NA                                 | NA                                          | NA                                     | NA                                     | NA                                      | NA                                     |
| automake                                        | automake-1.16.2-8.el9              | automake  -1.15.1-4.10.2                    | automake-1.16.1-8                      | automake-1.16.2-8                      | automake-1.16.1-8                       | automake-1.16.2-8                      |
| screen                                          | NA                                 | screen-4.6.1-bp154.1.34                     | NA                                     | NA                                     | NA                                      | NA                                     |
| libstdc++                                       | libstdc++-11.4.1-3.el9             | libstdc++-0.91-bp154.1.45                   | libstdc++-8.5.0-22                     | libstdc++-11.4.1-3                     | libstdc++-8.5.0-22.el8                  | libstdc++-11.4.1-3.el9                 |
| g++ (gcc-c++)                                   | gcc-11.4.1-3.el9                   | NA                                          | NA                                     | NA                                     | NA                                      | NA                                     |
| python3-pip                                     | python3-pip  -21.2.3-8.el9         | python3-pip-20.0.2-150400.20.1              | python3-pip-9.0.3-24                   | python3-pip-21.2.3-8                   | python3-pip-9.0.3-24                    | python3-pip-21.2.3-6.el9               |
| xz(xz-utils)                                    | xz-utils-5.2.5-8.el9_0             | NA                                          | xz-utils-5.2.4-4                       | xz-5.2.5-8                             | xz-utils-5.2.4-4.el8_6                  | xz-utils-5.2.5-8.el9_0                 |
| cpp                                             | cpp -11.4.1-3.el9                  | cpp -3.2.1-150200.5.3.3                     | cpp-8.5.0-22                           | cpp -11.4.1-3                          | cpp-8.5.0-22.el8                        | cpp-11.4.1-3.el9                       |
| patch                                           | patch-2.7.6-16.el9                 | patch-1.35.0-150400.4.5.1                   | NA                                     | patch-2.7.6-16                         | patch-1.21-2.el8                        | NA                                     |
| python3- GitPython(python3-git)                 | NA                                 | python3-1.5.1-bp154.1.41                    | NA                                     | NA                                     | NA                                      | NA                                     |
| python3-jinja2                                  | python3-jinja2- 2.11.3-5.el9       | python3-jinja2-2.10.1-3.10.2                | NA                                     | python3-jinja2-2.11.3-5                | python3-jinja2-2.10.1-3                 | NA                                     |
| python3-pexpect                                 | python3-pexpect-4.8.0-7.el9        | python3-pexpect-4.8.0-150400.17.64          | NA                                     | python3-pexpect-4.8.0-7                | NA                                      | NA                                     |
| diffutils                                       | diffutils-3.6-4.3.1                | diffutils-1.35.0-150400.4.5.1               | diffutils-3.6-6                        | diffutils-3.7-12                       | diffutils- 3.6-6.el8                    | diffutils-3.7-12                       |
| debianutils                                     | NA                                 | debianutils-5.4-8.11                        | NA                                     | NA                                     | NA                                      | NA                                     |
| iputils-ping                                    | NA                                 | NA                                          | NA                                     | NA                                     | NA                                      | NA                                     |
| libegl1-mesa                                    | NA                                 | NA                                          | NA                                     | NA                                     | NA                                      | NA                                     |
| libsdl1.2-dev                                   | NA                                 | NA                                          | NA                                     | NA                                     | NA                                      | NA                                     |
| pylint3                                         | pylint - 3.2.8-bp153.1.16          | NA                                          | NA                                     | NA                                     | NA                                      | NA                                     |
| python3                                         | python3 -3.9.18-3.el9_4.5          | python3 - 20180125-lp154.1.2                | python3 -3.1.2-1                       | python3 -3.9.18-3                      | python3 -3.0.7-4                        | python3 -3.9.14-1                      |
| cpio                                            | cpio -2.13-16.el9                  | cpio -0.10-bp154.1.19                       | cpio-2.12-11                           | cpio -2.13-16                          | cpio-2.12-11                            | cpio-2.13-16                           |
| gnupg                                           | gnupg-2.3.3-4.el9                  | gnupg-0.4.7-150400.5.69                     | gnupg-2.2.20-3                         | gnupg-2.3.3-4                          | gnupg-2.2.20-3                          | gnupg-2.3.3-2                          |
| bind-utils                                      | bind-utils-32:9.16.23-18.el9_4.6   | bind-utils-9.16.44-150400.5.37.2            | bind-utils-32:9.11.36-16               | bind-utils-32:9.16.23-18               | bind-utils-32:9.11.36-16                | bind-utils-32:9.16.23-18               |