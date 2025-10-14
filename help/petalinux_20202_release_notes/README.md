# 75775 - PetaLinux 2020.2/3 - Product Update Release Notes and Known Issues

## Title

75775 - PetaLinux 2020.2/3 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2020.2 and 2020.3 (Versal specific) and contains links to information about resolved issues and updated collateral contained in this release.

**Note: the 2020.3 release is for** **Versal ACAP devices only**.

Customers who are using MicroBlaze, Zynq-7000, Zynq UltraScale+ MPSoC/RFSoC devices should use the 2020.2 release.

## Solution

**BSPs supported for the 2020.2 PetaLinux Release**

This table contains supported BSPs for MicroBlaze, Zynq-7000, Zynq UltraScale+ MPSoC/RFSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

**Note:** XY - Represents release year, Z - Represents release version.

| Platform               | Variant                   | BSP Name                                  | BSP Description                                              |
| ---------------------- | ------------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| MicroBlaze             | AC701                     | xilinx-ac701-v20XY.Z-final.bsp            | **This BSP contains:**<br>**Hardware:** Uses the Vivado board preset with a MicroBlaze Processor, and core peripherals IPs such as AXI UARTLITE, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, u-boot, Linux kernel, dtb, and rootfs for booting u-boot and Linux. |
| MicroBlaze             | KC705                     | xilinx-kc705-v20XY.Z-final.bsp            | **This BSP contains:**<br>**Hardware:** Vivado board preset with MicroBlaze Processor, and peripherals such as AXI UARTLITE, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, u-boot, Linux kernel, dtb, and rootfs for booting u-boot and Linux. |
| MicroBlaze             | KCU105                    | xilinx-kcu105-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware:** Vivado board preset with MicroBlaze Processor, AXI UARTLITE, AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI 1G/2.5G Ethernet.<br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, u-boot, Linux kernel, dtb, and rootfs for booting u-boot and Linux. |
| MicroBlaze             | SP701                     | xilinx-sp701-v20XY.Z-final.bsp            | **This BSP contains:**<br>**Hardware:** Vivado board preset with MicroBlaze Processor, and peripherals such as AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, AXI UARTLITE, led_8bits, and AXI 1G/2.5G Ethernet.<br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, u-boot, Linux kernel, dtb, and rootfs for booting u-boot and Linux. |
| MicroBlaze             | VCU118                    | xilinx-vcu118-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware:** Vivado board preset with MicroBlaze Processor, AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, AXI UARTLITE, led_8bits, and AXI 1G/2.5G Ethernet.<br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, fs-boot, u-boot, Linux kernel, dtb, and rootfs for booting u-boot and Linux. |
| Zynq-7000              | ZC702                     | xilinx-zc702-v20XY.Z-final.bsp            | **This BSP contains:**<br>**Hardware:** Vivado board preset with Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet, etc.) and AXI GPIO connected to led_4bits.<br>**Software:** FSBL, u-boot, Linux, device-tree (includes OpenAMP), rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, FSBL, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq-7000              | ZC706                     | xilinx-zc706-v20XY.Z-final.bsp            | **This BSP contains:**<br>**Hardware:** Vivado board preset with Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet, etc.) and AXI GPIO connected with led_4bits, dip_switches_4bits, gpio_sws_3bits.<br>**Software:** FSBL, u-boot, Linux, device-tree (includes OpenAMP), rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, FSBL, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq-7000              | Avnet Digilent Zedboard   | avnet-digilent-zedboard-v20XY.Z-final.bsp | **This BSP contains:**<br>**Hardware:** Vivado board preset with Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet, etc.) and AXI GPIO connected with led_8bits, btns_5bits, sws_8bits.<br>**Software:** FSBL, u-boot, Linux, device-tree (includes OpenAMP), rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, FSBL, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq UltraScale+ MPSoC | ZCU102 production silicon | xilinx-zcu102-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware:** Vivado board preset with Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA, etc.).<br>**Software:** FSBL, PMUFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), rootfs (minimal packages).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq UltraScale+ MPSoC | ZCU104 production silicon | xilinx-zcu104-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware:** Vivado board preset with Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA, etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br>**Software:** FSBL, PMUFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), vcu-control software, rootfs (minimal packages including GStreamer, OpenMAX, V4L2, libdrm, and vcu-examples).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq UltraScale+ MPSoC | ZCU106 production silicon | xilinx-zcu106-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware 1:** Vivado board preset with Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA, etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br>**Hardware 2:** Vivado board preset with new PL DDR part.<br>**Software:** FSBL, PMUFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), vcu-control software, rootfs (with GStreamer, OpenMAX, V4L2, libdrm, and vcu-examples).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq UltraScale+ RFSoC | ZCU111 production silicon | xilinx-zcu111-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware:** Vivado board preset with RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA, etc.) and rf_data_converters, sd_fec_dec, adc_sink, dac_source, axi_gpio, axi_intc IPs.<br>**Software:** FSBL, PMUFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), rfdc-drivers, rootfs (with RDFC example applications).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq UltraScale+ RFSoC | ZCU1275                   | xilinx-zcu1275-v20XY.Z-final.bsp          | **This BSP contains:**<br>**Hardware:** Vivado board preset with RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA, etc.) and rf_data_converters, adc_sink, dac_source, axi_gpio, axi_intc IPs.<br>**Software:** FSBL, PMUFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), rfdc-drivers, rootfs (with RDFC example applications).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq UltraScale+ RFSoC | ZCU1285                   | xilinx-zcu1285-v20XY.Z-final.bsp          | **This BSP contains:**<br>**Hardware:** Vivado board preset with RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA, etc.) and rf_data_converters, adc_sink, dac_source, axi_gpio, axi_intc IPs.<br>**Software:** FSBL, PMUFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), rfdc-drivers, rootfs (with RDFC example applications).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq UltraScale+ RFSoC | ZCU208                    | xilinx-zcu208-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware:** Vivado board preset with RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, etc.) and ADC_DDR_DMA, DAC_DDR_DMA CLOCKING blocks, axi_gpio IPs.<br>**Software:** FSBL, PMUFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), rfclk, rfdc-drivers, rootfs (with RFCLK and RDFC example applications).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq UltraScale+ RFSoC | ZCU208-SDFEC              | xilinx-zcu208-sdfec-v20XY.Z-final.bsp     | **This BSP contains:**<br>**Hardware:** Vivado board preset with RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, etc.) and SD-FEC, Monitor blocks, AXI GPIO, AXI INTC IPs.<br>**Software:** FSBL, PMUFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), rfclk, rfdc-drivers, rootfs (with RFCLK and RDFC examples).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Zynq UltraScale+ RFSoC | ZCU216                    | xilinx-zcu216-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware:** Vivado board preset with RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, etc.) and ADC_DDR_DMA, DAC_DDR_DMA CLOCKING blocks, axi_gpio IPs.<br>**Software:** FSBL, PMUFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), rfclk, rfdc-drivers, rootfs (with RFCLK and RDFC examples).<br>**Pre-built Images:** Bitstream, FSBL, PMUFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs. |
| Versal ACAP (AI Core)  | VCK190 Production silicon | xilinx-vck190-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware:** Vivado board preset with Versal CIPS IP PS block (DDR, UART, SD, QSPI, Ethernet, USB, etc.) and AIE IP in PL.<br>**Software:** PLM, PSMFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), rootfs (with TCL, xrt, zocl, python, libstdc++, aie-matrix-multiplication).<br>**Pre-built Images:** PDI, PLM, PSMFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs for u-boot and Linux.<br>**OOB Images:** Ready-to-boot SD images including Jupyter, pm-notebooks, openamp-demo-notebooks, python3-ipywidgets. |
| Versal ACAP (Prime)    | VMK180 Production silicon | xilinx-vmk180-v20XY.Z-final.bsp           | **This BSP contains:**<br>**Hardware:** Vivado board preset with Versal CIPS IP PS block (DDR, UART, SD, QSPI, Ethernet, USB, etc.) with production silicon.<br>**Software:** PLM, PSMFW, ATF, u-boot, Linux, device-tree (includes OpenAMP, Xen), rootfs (with TCL, python, libstdc++).<br>**Pre-built Images:** PDI, PLM, PSMFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs for u-boot and Linux.<br>**OOB Images:** Ready-to-boot SD images including Jupyter, pm-notebooks, openamp-demo-notebooks, python3-ipywidgets. |

**BSPs supported for the 2020.3 PetaLinux Release**

This table contains supported BSPs for Versal ACAP available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html)

**Note:** XY - Represents release year, Y - Represents release version.

| Platform                  | Variant                   | BSP Name                        | BSP Description                                              |
| ------------------------- | ------------------------- | ------------------------------- | ------------------------------------------------------------ |
| **Versal ACAP (AI Core)** | VCK190 Production silicon | xilinx-vck190-v20XY.Z-final.bsp | **This BSP contains:**<br>**Hardware:** This design uses the Vivado board preset with Versal CIPS IP PS block (DDR, UART, SD, QSPI, Ethernet, USB, etc.) with production silicon and AIE IP in PL.<br>**Software:** PLM, PSMFW, ATF, U-Boot, Linux, device-tree (includes open-amp, xen), rootfs (minimal packages such as Tcl, xrt, zocl, Python, libstdc++, aie-matrix-multiplication).<br>**Pre-built Images:** Ready-to-test images including PDI, PLM, PSMFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs booting u-boot, Linux, and Xen.<br>**OOB Images:** Ready-to-boot images with rootfs in SD ext4 partition. Out-of-the-box demo images include packages such as packagegroup-petalinux-jupyter, pm-notebooks, openamp-demo-notebooks, python3-ipywidgets. |
| **Versal ACAP (Prime)**   | VMK180 Production silicon | xilinx-vmk180-v20XY.Z-final.bsp | **This BSP contains:**<br>**Hardware:** This design uses the Vivado board preset with Versal CIPS IP PS block (DDR, UART, SD, QSPI, Ethernet, USB, etc.) with production silicon.<br>**Software:** PLM, PSMFW, ATF, U-Boot, Linux, device-tree (includes open-amp, xen), rootfs (minimal packages such as Tcl, Python, libstdc++).<br>**Pre-built Images:** Ready-to-test images including PDI, PLM, PSMFW, ATF, u-boot, boot.scr, Linux kernel, dtb, and rootfs booting u-boot, Linux, and Xen.<br>**OOB Images:** Ready-to-boot images with rootfs in SD ext4 partition. Out-of-the-box demo images include packages such as packagegroup-petalinux-jupyter, pm-notebooks, openamp-demo-notebooks, python3-ipywidgets. |

**Unified Images supported for the 2020.2 PetaLinux Release**

This table contains supported unified images for Zynq-7000 and Zynq UltraScale+ MPSoC/RFSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

**Note:** XY - Represents release year, Z - Represents release version.

| Platform                         | SOC Variant    | Tar File Name                       | Unified Image Description                                    |
| -------------------------------- | -------------- | ----------------------------------- | ------------------------------------------------------------ |
| **Zynq-7000**                    | All            | xilinx-zynq-common-v2020.2.tar.gz   | **This tar file contains:**<br>**Pre-built Images:** Ready-to-test images such as `u-boot.elf`, `boot.scr`, `Image`, `rootfs.ext4`, `rootfs.manifest`, `rootfs.tar.gz`, and `sdk.sh`.<br>**README.txt:** This readme file describes how to install and use these image files. |
| **Zynq UltraScale+ MPSoC/RFSoC** | CG, EG, EV, DR | xilinx-zynqmp-common-v2020.2.tar.gz | **This tar file contains:**<br>**Pre-built Images:** Ready-to-test images such as `bl31.elf`, `u-boot.elf`, `boot.scr`, `Image`, `rootfs.ext4`, `rootfs.manifest`, `rootfs.tar.gz`, and `sdk.sh`.<br>**README.txt:** This readme file describes how to install and use these image files. |
| **Versal ACAP**                  | AI Core, Prime | xilinx-versal-common-v2020.2.tar.gz | **This tar file contains:**<br>**Pre-built Images:** Ready-to-test images such as `u-boot.elf`, `boot.scr`, `Image`, `rootfs.ext4`, `rootfs.manifest`, `rootfs.tar.gz`, and `sdk.sh`.<br>**README.txt:** This readme file describes how to install and use these image files. |


**Note**: The "<architecture> sstate-cache" (sstate\_<architecture>\_2020.2.tar.gz) file can be found on the Xilinx [download](https://www.xilinx.com/downloadNav/embedded-design-tools/2020-2.html) area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2020.2-README.tar.gz) file that outlines the procedure to use "sstate cache".

Refer to the attached file "2020.2\_PetaLinux\_Packages\_List" for software package versions tested on host machines, which is required for PetaLinux installation tools.

See the attached README also.


**Unified Images supported for the 2020.3 PetaLinux Release**

This table contains supported unified images for Versal ACAP available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

**Note:** XY - Represents release year, Z - Represents release version.

| Platform        | SOC Variant    | Tar File Name                       | Unified Image Description                                    |
| --------------- | -------------- | ----------------------------------- | ------------------------------------------------------------ |
| **Versal ACAP** | AI Core, Prime | xilinx-versal-common-v2020.3.tar.gz | **This tar file contains:**<br>**Pre-built Images:** Ready-to-test images such as `u-boot.elf`, `boot.scr`, `Image`, `rootfs.ext4`, `rootfs.manifest`, `rootfs.tar.gz`, and `sdk.sh`.<br>**README.txt:** This readme file describes how to install and use these image files. |


**Note**: The "<architecture> sstate-cache" (sstate\_<architecture>\_2020.3.tar.gz) file can be found on the Xilinx [download](https://www.xilinx.com/downloadNav/embedded-design-tools/2020-2.html) area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2020.2-README.tar.gz) file that outlines the procedure to use "sstate cache".

Refer to the attached file "2020.2\_PetaLinux\_Packages\_List" (No changes for 2020.3 release) for software package versions tested on host machines, which is required for PetaLinux installation tools.

**PetaLinux 2020.2 contains the following build collateral:**

| Component                             | Git Repo                                                     | Git Branches          | Git Tags                    | Commit ID                                                    | Comments                                                     |
| ------------------------------------- | ------------------------------------------------------------ | --------------------- | --------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| FSBL, PMU Firmware, PLM, PSM Firmware | git://github.com/Xilinx/embeddedsw.git                       | master-rel-2020.2     | xilinx-v2020.2              | 08b9f4304d1634ed632f4276d603d834940fd55a                     | FSBL for Zynq-7000: `embeddedsw/lib/sw_apps/zynq_fsbl`<br>FSBL for Zynq UltraScale+: `embeddedsw/lib/sw_apps/zynqmp_fsbl`<br>PMU for Zynq UltraScale+: `embeddedsw/lib/sw-apps/zynqmp_pmufw`<br>PLM for Versal ACAP: `embeddedsw/lib/sw-apps/versal_plm`<br>PSM for Versal ACAP Firmware: `embeddedsw/lib/sw-apps/versal_psmfw` |
| Device-tree                           | git://github.com/Xilinx/device-tree-xlnx.git                 | master                | xilinx-v2020.2              | f725aaecffb806aff8dc081b6ab508ce7bb1fc3d                     |                                                              |
| Linux                                 | git://github.com/Xilinx/linux-xlnx.git                       | xlnx_rebase_v5.4      | xlnx_rebase_v5.4_2020.2     | 62ea514294a0c9a80455e51f1f4de36e66e8c546                     | Linux Kernel rebase version 5.4                              |
| U-Boot                                | git://github.com/Xilinx/u-boot-xlnx.git                      | xlnx_rebase_v2020.01  | xlnx_rebase_v2020.01_2020.2 | bb4660c33aa7ea64f78b2682bf0efd56765197d6                     | U-boot Version v2020.01                                      |
| QEMU                                  | git://github.com/Xilinx/qemu.git                             | branch/xilinx-v2020.2 | xilinx-v2020.2              | 7e3e3ae09af8abe70383a5dcf2e80801a07512d0                     |                                                              |
| Xen                                   | git://github.com/Xilinx/xen.git                              | xilinx/release-2020.2 | xilinx-v2020.2              | dfa58d1a3f0db395f2c8799419cf6fa537eb2aeb                     | Xen Version 4.13                                             |
| ARM-Trusted-Firmware (ATF)            | git://github.com/Xilinx/arm-trusted-firmware.git             | xlnx_rebase_v2.2      | xilinx_rebase_v2.2_2020.2   | e6eea88b14aaf456c49f9c7e6747584224648cb9                     | ATF is based on upstream version 2.2                         |
| Yocto                                 | git://github.com/Xilinx/meta-xilinx.git<br>git://github.com/Xilinx/meta-xilinx-tools.git<br>git://github.com/Xilinx/meta-petalinux.git<br>git://github.com/Xilinx/meta-vitis-ai.git | rel-v2020.2           | No Tags                     | e32c768b7e30c2f949b0b98e807afe82ac213556<br>76a415bd5d238cbdaa850ba1c202144990e87968<br>ef895be94f61e3f315701b0120497dde556136bf<br>e24ef77f2363b142c78484c8ac181998f9386c15 | Yocto 3.0.0 Zeus                                             |
| qemu-devicetrees                      | git://github.com/Xilinx/qemu-devicetrees.git                 | branch/xilinx-v2020.2 | xilinx-v2020.2              | 0097f0f651d67b3a8495693e9e17c443948d3c77                     |                                                              |
| OpenAMP                               | git://github.com/Xilinx/open-amp.git                         | rel-v2020.2           | xilinx-v2020.2              | 29eb98c02326199ad4245a484611a3b199d55bab                     |                                                              |
| libmetal                              | git://github.com/Xilinx/libmetal.git                         | rel-v2020.2           | xilinx-v2020.2              | 595d97e827c2cd3974e26a2be70e7fe48b7fe67e                     |                                                              |
| VCU OpenMax IL                        | git://github.com/Xilinx/vcu-omx-il.git                       | release-2020.2        | xilinx-v2020.2              | 4e9daf282a12ecba19fe12f296a31315f6a6bd2d                     |                                                              |
| VCU Control Software                  | git://github.com/Xilinx/vcu-ctrl-sw.git                      | release-2020.2        | xilinx-v2020.2              | b82de3783fe66ee72f28b51313e8b42827d3f202                     |                                                              |
| VCU Firmware                          | git://github.com/Xilinx/vcu-firmware.git                     | release-2020.2        | xilinx-v2020.2              | 97faa66c559f31ab7be5ba40ddfa18530274cdd1                     |                                                              |
| VCU Modules                           | git://github.com/Xilinx/vcu-modules.git                      | release-2020.2        | xilinx-v2020.2              | 844d4c4292e08ad8c3f22ac78e9a937395c1db4b                     |                                                              |
| GStreamer OpenMax IL                  | git://github.com/Xilinx/gst-omx.git                          | release-2020.2        | xilinx-v2020.2              | f3061fb074c6ef86df252bfe769ca5bf124fa3bf                     | GStreamer version 1.16.1                                     |
| GStreamer Plugins-Base                | git://github.com/Xilinx/gst-plugins-base.git                 | release-2020.2        | xilinx-v2020.2              | a46ce57c6ddd1146c118133d9eecd5e7a10d2cf7                     |                                                              |
| GStreamer Plugins-Bad                 | git://github.com/Xilinx/gst-plugins-bad.git                  | release-2020.2        | xilinx-v2020.2              | 34f6d133877dd667002824169bf467ef6de04cb3                     |                                                              |
| GStreamer Plugins-Good                | git://github.com/Xilinx/gst-plugins-good.git                 | release-2020.2        | xilinx-v2020.2              | 7b1c7fbeac702c5f1d648074d7b7191c9512af9f                     |                                                              |
| GStreamer                             | git://github.com/Xilinx/gstreamer.git                        | release-2020.2        | xilinx-v2020.2              | 10db9688beab0b11ea2e8c5b05d78c57a589ad03                     |                                                              |
| hdmi-modules                          | git://github.com/Xilinx/hdmi-modules.git                     | release-2020.2        | xilinx-v2020.2              | 47b8ffe39df1543a69b1eca67a33029b5f85de9f                     |                                                              |
| GPU MALI                              | git://github.com/Xilinx/mali-userspace-binaries.git          | rel-v2020.2           | xilinx-v2020.2              | da73805e3e011382c4d014ac10037cd193aaa9a0                     |                                                              |
| GCC                                   |                                                              |                       |                             |                                                              | MB compiler version 9.2, ARM 9.2                             |

**2020.2 Release Notes for Open Source components wiki page:**

The below page covers details for all of the open source components changes such as New Features and Bug Fixes in a particular release.

https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/981860495/2020.2+Release+Notes+for+Open+Source+Components 

**2020.2 Release pre-built images wiki page:**

[https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/1065451521/2020.2+Release](https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/1065451521/2020.2+Release) 

**2020.2 New Features:**

**Note: Versal content is in bold font**

**PetaLinux**

-   Added support for TMPDIR option while creating a project 
-   Added support for Unified Web Installer
-   Added support to build u-boot using external DTB option in petalinux-config menu.
-   Added new petalinux-devtool command to support Yocto devtool feature.
-   Updated Vitis AI dependency packages in common rootfs.
-   Added support for Multiboot.
-   Obsolete (UG1157) documentation and all content from (UG1157) are merged into (UG1144).
-   **Added unified image support for Zynq-7000, Zynq UltraScale+ MPSoC/RFSoC and Versal platforms.**
-   Added Yocto WIC image support in all BSP's pre-built images.
-   Added support for resize utility package for rootfs to change the SD partitions.

**GPU MALI-400**

-   None

**2020.2 Bug Fixes:**

**Note: Versal content is in bold font**

**PetaLinux**

-   Fixed MicroBlaze fsboot hang issue in axi\_quad\_spi\_0 when axi4\_interface(CONFIG.C\_TYPE\_OF\_AXI4\_INTERFACE) support is enabled.
-   (UG1144) doc changes.
    -   Fixed Ubuntu version from 18.04.02 to 18.04.2
    -   Fixed Ubuntu package version in host packages table
    -   Updated TFTP boot steps
    -   Updated petalinux-devtool commands
-   Updated BIF attributes order and printing attribute value on terminal.
-   Fixed issue with MicroBlaze design targeted for ZCU106 board.
-   Added openssl binary support in petalinux-config -c rootfs
-   Fixed petalinux-config -c kernel issue with ext-local-src
-   Fixed issue where PetaLinux config generates incorrect DDR size and DTB padding when you parse XSA for a second time
-   Added menu entry for 4K erase block size in JFFS2 in PetaLinux config

**GPU MALI-400**

-   None

 

**PetaLinux 2020.3 contains the following build collateral:**

| Component                  | Git Repo                                                     | Git Branches          | Git Tags                    | Commit ID                                                    | Comments                                                     |
| -------------------------- | ------------------------------------------------------------ | --------------------- | --------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| PLM, PSM Firmware          | git://github.com/Xilinx/embeddedsw.git                       | master-rel-2020.3     | xilinx-v2020.3              | d12149e44651c1c429ee32322e250c3aff3edddf                     | PLM for Versal ACAP: `embeddedsw/lib/sw-apps/versal_plm`<br>PSM for Versal ACAP Firmware: `embeddedsw/lib/sw-apps/versal_psmfw` |
| Device-tree                | git://github.com/Xilinx/device-tree-xlnx.git                 | master-rel-2020.3     | xilinx-v2020.3              | e5a0e31284d1c02bbdf19b579d2e89fa45da96b8                     |                                                              |
| Linux                      | git://github.com/Xilinx/linux-xlnx.git                       | xlnx_rebase_v5.4      | xlnx_rebase_v5.4_2020.3     | 49bdb4e70d2001f3a5bf0bf5e990cca4a85210f4                     | Linux Kernel rebase version 5.4                              |
| U-Boot                     | git://github.com/Xilinx/u-boot-xlnx.git                      | xlnx_rebase_v2020.01  | xlnx_rebase_v2020.01_2020.3 | a1bf7f435872d7cdf79ec8777c2a078f06ac9f6b                     | U-boot Version v2020.01                                      |
| QEMU                       | git://github.com/Xilinx/qemu.git                             | branch/xilinx-v2020.3 | xilinx-v2020.3              | 53d6b4ffc13d94ad9d5416b17be1eb70148b7f7f                     |                                                              |
| Xen                        | git://github.com/Xilinx/xen.git                              | xilinx/release-2020.3 | xilinx-v2020.3              | f19a872233fbfe2eb933f25fa3d9a780ced774e5                     | Xen Version 4.13                                             |
| ARM-Trusted-Firmware (ATF) | git://github.com/Xilinx/arm-trusted-firmware.git             | xlnx_rebase_v2.2      | xilinx_rebase_v2.2_2020.3   | e6eea88b14aaf456c49f9c7e6747584224648cb9                     | ATF is based on upstream version 2.2                         |
| Yocto                      | git://github.com/Xilinx/meta-xilinx.git<br>git://github.com/Xilinx/meta-xilinx-tools.git<br>git://github.com/Xilinx/meta-petalinux.git<br>git://github.com/Xilinx/meta-vitis-ai.git | rel-v2020.3           | No Tags                     | 5417b9f25f71cb902dddb143b684b0e74e97ba79<br>ff69b201522fec7416f2c5ee631368a8e6afb260<br>9e54bce798679b1232bc257ba61ef49c7142eed6<br>f7b2f9b1d51a5943241396b87c0c6cc0ef4bf078 | Yocto 3.0.0 Zeus                                             |
| qemu-devicetrees           | git://github.com/Xilinx/qemu-devicetrees.git                 | branch/xilinx-v2020.3 | xilinx-v2020.3              | cd033c4e08cecc378d53ff14e001fb346df74df5                     |                                                              |
| OpenAMP                    | git://github.com/Xilinx/open-amp.git                         | rel-v2020.2           | xilinx-v2020.2              | 29eb98c02326199ad4245a484611a3b199d55bab                     |                                                              |
| libmetal                   | git://github.com/Xilinx/libmetal.git                         | rel-v2020.2           | xilinx-v2020.2              | 595d97e827c2cd3974e26a2be70e7fe48b7fe67e                     |                                                              |
| hdmi-modules               | git://github.com/Xilinx/hdmi-modules.git                     | release-2020.2        | xilinx-v2020.2              | 47b8ffe39df1543a69b1eca67a33029b5f85de9f                     |                                                              |
| Bootgen                    | git://github.com/Xilinx/bootgen.git                          | xlnx-rel-v2020.3      |                             | 82211840048d60cfde8816df8f572278390210cb                     |                                                              |
| RunX                       | git://github.com/Xilinx/runx.git                             | xilinx/release-2020.3 |                             | f19a872233fbfe2eb933f25fa3d9a780ced774e5                     |                                                              |
| XRT                        | git://github.com/Xilinx/xrt.git                              | xilinx/release-2020.3 |                             | f9af081618f5f2e05d66c25887bd8f816633759e                     |                                                              |
| GCC                        |                                                              |                       |                             |                                                              | MB compiler version 9.2, ARM 9.2                             |

**2020.3 Release Notes for Open Source components wiki page:**

The below wiki page covers details for all of the open source components changes such as New Features and Bug Fixes in a particular release.

https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/1589018630/2020.3+Release+Notes+for+Open+Source+Components 

**2020.3 New Features:**

https://xilinx-wiki.atlassian.net/wiki/spaces/XWUC/pages/1545633793/2020.3+Release 

**PetaLinux**

-   None

**2020.3 Bug Fixes:**

**PetaLinux**

-   None

 

**Known Issues for 2020.2 and 2020.3:**

| Linux/Baremetal | Components  | Description                                                  | Work-around           | To be fixed version |
| --------------- | ----------- | ------------------------------------------------------------ | --------------------- | ------------------- |
| Linux           | PetaLinux   | Zynq UltraScale+ MPSoC: How to enable UHS (SD 3.0) support for ZCU102 and ZCU106 evaluation board PetaLinux BSPs | (Xilinx Answer 69978) | NA                  |
| Linux           | XSDK        | Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle    | (Xilinx Answer 69143) | NA                  |
| Linux           | FSBL        | Zynq UltraScale+ MPSoC: How to achieve SATA performance in Linux | (Xilinx Answer 71584) | NA                  |
| Linux           | FSBL        | Zynq UltraScale+ MPSoC: How to make SMMU work with SATA IP   | (Xilinx Answer 71790) | NA                  |
| Linux           | QEMU        | 2020.2 QEMU Versal and Zynq UltraScale+ MPSoC - Incorrect dummy cycles sent when using GQSPI dual or quad mode byte transfer instead of CS hold time | (Xilinx Answer 75599) | NA                  |
| Linux           | QEMU        | QEMU 2020.2 Versal and Zynq UltraScale+ MPSOC: Incorrect dummy cycle count for Quad I/O read command on Micron flashes | (Xilinx Answer 75600) | NA                  |
| Linux           | QEMU        | 2020.2 QEMU Versal and Zynq UltraScale+ MPSoC: QEMU program stops with XSDB | (Xilinx Answer 75614) | NA                  |
| Linux           | QEMU        | 2020.2 Versal and Zynq UltraScale+ MPSOC: QEMU GDB unable to catch segfaults | (Xilinx Answer 75615) | NA                  |
| Linux           | QEMU        | 2020.2 Versal QEMU: LPD XPPU does not cover TCM              | (Xilinx Answer 75684) | NA                  |
| Linux           | PetaLinux   | 2020.x-2021.x PetaLinux: Why platform-top.h doesn't work in u-boot distro boot | (Xilinx Answer 75730) | 2021.2              |
| Linux           | PetaLinux   | 2020.1/2 PetaLinux: Running petalinux-config menu crashes with segmentation fault on CentOS 7.x | (Xilinx Answer 75816) | 2021.1              |
| Linux           | Device-tree | 2020.1 Zynq UltraScale+ MPSoC: PetaLinux fails to build DTG when FPGA Manager is enabled using xxv_ethernet design | (Xilinx Answer 75856) | 2021.1              |
| Linux           | PetaLinux   | 2020.2 PetaLinux: EmbeddedSW components build fails when upgrading eSDK from 2020.1 to 2020.2 | (Xilinx Answer 75870) | 2021.1              |
| Linux           | PetaLinux   | 2020.2 PetaLinux: Installer log does not capture all of the missing packages while installing | (Xilinx Answer 75878) | 2021.1              |
| Linux           | PetaLinux   | 2020.1/2 MicroBlaze: PetaLinux tool generates unsupported u-boot distro boot files for MicroBlaze project | (Xilinx Answer 75879) | 2021.1              |
| Linux           | PetaLinux   | 2020.2 PetaLinux: Tools throws warnings when you source PetaLinux env scripts on RHEL 7.8 | (Xilinx Answer 75880) | 2021.1              |
| Linux           | AIE         | 2020.2 Versal ACAP: AIE Matrix Multiplication demo application does not work on VCK190 ES1 boards | (Xilinx Answer 75881) | NA                  |
| Linux           | U-boot      | 2020.2 Zynq-7000 : S25FL256XXX flash is not supported for addresses beyond 16MB in U-boot | (Xilinx Answer 75887) | NA                  |
| Linux           | Drivers     | 2020.2 Versal ACAP: Ethernet does not work after subsystem restart in either SD or QSPI bootmodes | (Xilinx Answer 75892) | 2021.1              |
| Linux           | U-boot      | 2020.2 Versal ACAP: SD timeout occurs after subsystem restart in QSPI bootmode | (Xilinx Answer 75893) | 2021.1              |
| Linux           | Device-tree | 2019.x-2020.x Zynq UltraScale+ MPSoC: PetaLinux fails to build DTG using xxv_ethernet design | (Xilinx Answer 76029) | 2021.1              |
| Linux           | Device-tree | 2020.2 Versal ACAP, Zynq Ultrascale+ MPSoC: Device Tree Generator generates incorrect nodes for AXI4 Switch IP | (Xilinx Answer 76043) | 2021.1              |
| Linux           | Device-tree | 2020.2 Device Tree: MIPI CSI2 RX Linux driver fails to probe when using version 5.1 of the MIPI CSI2 RX IP in XSA | (Xilinx Answer 76113) | 2021.1              |
| Linux           | ATF         | 2020.2 Zynq UltraScale+ RFSoC: ATF prints out XCZUUNKN for device when running on ZU43/46/47DR devices | (Xilinx Answer 76231) | 2021.1              |
| Linux           | Device-tree | 2020.x Versal ACAP, Zynq UltraScale+ MPSoC: DTG generates incorrect phy-mode for 1000BaseX phy type in AXI Ethernet design | (Xilinx Answer 76328) | 2021.1              |
| Linux           | Device-tree | 2020.2 Zynq Ultrascale+ MPSoC: DTG fails to create node for Xilinx MIPI DSI IP | (Xilinx Answer 76348) | 2021.1              |
| Linux           | PetaLinux   | 2020.2/3 Versal ACAP: VCK190 and VMK180 System Controller OOB SD card images do not boot | (Xilinx Answer 76355) | 2021.1              |
| Linux           | Device-tree | 2020.2 Versal ACAP, Zynq Ultrascale+ MPSoC: DTG fails to build with AXI Stream in MIPI design | (Xilinx Answer 76376) | 2021.1              |
| Baremetal       | PLM         | 2020.2/3 Versal ACAP: AIE mem clear operation might fail by consuming very high power | (Xilinx Answer 76381) | 2021.1              |
| Baremetal       | PLM         | 2020.2/3 Versal ACAP: Poll for GTY HOUSECLEAN DONE bit before de-asserting INITCTRL | (Xilinx Answer 76382) | 2021.1              |
| Linux           | Device-tree | 2020.x Device Tree: In MIPI CSI2 RX design reset-gpio nodes to assert video_aresetn are not generated by DTG | (Xilinx Answer 76392) | 2021.1              |
| Linux           | Device-tree | 2020.2 Versal ACAP: Device Tree Generator fails to build when ILA added to to Versal AXI Stream Interface IP in design | (Xilinx Answer 76440) | 2021.1              |
| Linux           | Device-tree | 2020.2 Zynq UltraScale+ MPSoC: PetaLinux fails to build DTG using xxv_ethernet multicore design | (Xilinx Answer 76457) | 2021.1              |
| Linux           | PetaLinux   | 2020.x PetaLinux: Linux AXI UART Lite driver boot hangs with loopback mode | (Xilinx Answer 76468) | 2021.1              |
| Linux           | Device-tree | 2020.2 Versal, Zynq Ultrascale+ MPSoC: DTG doesn't generate phy, gpio and other include files for template board | (Xilinx Answer 76509) | 2021.1              |
| Linux           | Device-tree | 2020.2 Zynq UltraScale+ MPSoC: Linux DisplayPort 1.4 Phy out of tree module driver assertion fails during probe | (Xilinx Answer 76573) | 2021.1              |
| Linux           | Device-tree | 2020.2-2021.1 Versal ACAP: DTG fails to generate the nodes when ILA added to Versal AXI Stream Interface IP | (Xilinx Answer 76575) | 2021.2              |
| Linux           | Device-tree | 2020.2 Versal ACAP: DTG fails to generate the nodes with Versal AXI Stream Switch IP in some usecase | (Xilinx Answer 76577) | 2021.1              |
| Linux           | Yocto       | 2020.2 Yocto: Booting Linux on KC705 using Yocto build images hangs at boot | (Xilinx Answer 76588) | 2021.1              |
| Linux           | Yocto       | 2020.2/2021.1 Versal ACAP: Yocto runqemu command results in error if image size is not a power of 2 | (Xilinx Answer 76596) | 2021.2              |
| Linux           | FSBL, PMUFW | 2020.2 Zynq UltraScale+ MPSoC: PetaLinux fails to build FSBL and PMUFW when nFIQ is enabled in HW design | (Xilinx Answer 76761) | 2021.1              |

# 2020.2_PetaLinux_Package_List

## Linux Distribution OS details:

1. RHEL 7.4, 7.5, 7.6 ,7.7 and 7.8 Server:  Infrastructure Server
2. RHEL 7.4, 7.5, 7.6 , 7.7 and 7.8 Desktop : Development and Creative workstation.
3. CentOS 7.4, 7.5, 7.6,7.7 and 7.8 Server (From Everything.ISO): Infrastructure server.
4. CentOS 7.4, 7.5, 7.6 ,7.7 and 7.8 Desktop (From Everything.ISO): Development and Creative workstation.
5. Ubuntu 16.04.05 and Ubuntu 16.04.06 Desktop.
6. Ubuntu 16.04.05  and Ubuntu 16.04.06 Server.
7. Ubuntu 18.04.01, 18.04.02, 18.04.03 and Ubuntu 18.04.04 Desktop.
8. Ubuntu 18.04.01, 18.04.02, 18.04.03  and Ubuntu 18.04.04 Server.

### Note: 

1. Empty packages are not installed means assuming these are default from Linux Distribution.
2. For RHEL/CentOS you need to installGitPython and jinja2 using pip3 commands as mentioned below.

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

### RHEL/CentOS versions

| Tool/Library                                    | Red Hat Enterprise Desktop/Server  7.4 (64-bit) | Red Hat Enterprise Destop/Server 7.5(64-bit) | Red Hat Enterprise Desktop/Server  7.6 (64-bit) | Red Hat Enterprise Desktop/Server  7.7(64-bit) | Red Hat Enterprise Desktop/Server  7.8(64-bit) | CentOS Desktop/Server 7.4  (64-bit)        | CentOS Desktop/Server 7.5  (64-bit)        | CentOS Desktop/Server 7.6  (64-bit)        | CentOS Desktop/Server 7.7  (64-bit)        | CentOS Desktop/Server 7.8  (64-bit)        |
| ----------------------------------------------- | ----------------------------------------------- | -------------------------------------------- | ----------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| ip (iproute)                                    | iproute-3.10.0-87.el7.x86_64                    | iproute-4.11.0-14.el7.x86_64                 | iproute-4.11.0-14.el7.x86_64                    | iproute-4.11.0-25.el7_7.2.x86_64               | iproute-4.11.0-25.el7_7.2.x86_64               | iproute-3.10.0-87.el7.x86_64               | iproute-4.11.0-14.el7.x86_64               | iproute-4.11.0-14.el7.x86_64               | iproute-4.11.0-25.el7_7.2.x86_64           | iproute-4.11.0-25.el7_7.2.x86_64           |
| gawk                                            | gawk-4.0.2-4.el7_3.1.x86_64                     | gawk-4.0.2-4.el7_3.1.x86_64                  | gawk-4.0.2-4.el7_3.1.x86_64                     | gawk-4.0.2-4.el7_3.1.x86_64                    | gawk-4.0.2-4.el7_3.1.x86_64                    | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                | gawk-4.0.2-4.el7_3.1.x86_64                |
| gcc                                             | gcc-4.8.5-44.el7_4.1.x86_64                     | gcc-4.8.5-44.el7_4.1.x86_64                  | gcc-4.8.5-44.el7_4.1.x86_64                     | gcc-4.8.5-44.el7_4.1.x86_64                    | gcc-4.8.5-44.el7_4.1.x86_64                    | gcc-4.8.5-16.el7_4.1.x86_64                | gcc-4.8.5-39.el7.x86_64                    | gcc-4.8.5-39.el7.x86_64                    | gcc-4.8.5-39.el7.x86_64                    | gcc-4.8.5-39.el7.x86_64                    |
| netstat (net-tools)                             | net-tools-2.0-0.22.20131004git.el7.x86_64       | net-tools-2.0-0.25.20131004git.el7.x86_64    | net-tools-2.0-0.24.20131004git.el7.x86_64       | net-tools-2.0-0.25.20131004git.el7.x86_64      | net-tools-2.0-0.25.20131004git.el7.x86_64      | net-tools-2.0-0.24.20131004git.el7.x86_64  | net-tools-2.0-0.22.20131004git.el7.x86_64  | net-tools-2.0-0.24.20131004git.el7.x86_64  | net-tools-2.0-0.25.20131004git.el7.x86_64  | net-tools-2.0-0.25.20131004git.el7.x86_64  |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-5.9-14.20130511.el7_4.x86_64      | ncurses-devel-5.9-14.20130511.el7_4.x86_64   | ncurses-devel-5.9-14.20130511.el7_4.x86_64      | ncurses-devel-5.9-14.20130511.el7_4.x86_64     | ncurses-devel-5.9-14.20130511.el7_4.x86_64     | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 | ncurses-devel-5.9-14.20130511.el7_4.x86_64 |
| zlib-devel(also,install 32-bit of this version) | zlib-devel-1.2.7-18.el7.x86_64                  | zlib-devel-1.2.7-18.el7.x86_64               | zlib-devel-1.2.7-18.el7.x86_64                  | zlib-devel-1.2.7-18.el7.x86_64                 | zlib-devel-1.2.7-18.el7.x86_64                 | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             | zlib-devel-1.2.7-18.el7.x86_64             |
| openssl-devel                                   | openssl-devel-1.0.2k-8.el7.x86_64               | openssl-devel-1.0.2k-19.el7.x86_64           | openssl-devel-1.0.2k-19.el7.x86_64              | openssl-devel-1.0.2k-19.el7.x86_64             | openssl-devel-1.0.2k-19.el7.x86_64             | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         | openssl-devel-1.0.2k-19.el7.x86_64         |
| flex                                            | flex-2.5.37-3.el7.x86_64                        | flex-2.5.37-3.el7.x86_64                     | flex-2.5.37-3.el7.x86_64                        | flex-2.5.37-6.el7.x86_64                       | flex-2.5.37-6.el7.x86_64                       | flex-2.5.37-3.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   | flex-2.5.37-6.el7.x86_64                   |
| bison                                           | bison-3.0.4-1.el7.x86_64                        | bison-3.0.4-1.el7.x86_64                     | bison-3.0.4-1.el7.x86_64                        | bison-3.0.4-1.el7.x86_64                       | bison-3.0.4-1.el7.x86_64                       | bison-3.0.4-1.el7.x86_64                   | bison-3.0.4-2.el7.x86_64                   | bison-3.0.4-1.el7.x86_64                   | bison-3.0.4-1.el7.x86_64                   | bison-3.0.4-1.el7.x86_64                   |
| libselinux                                      | libselinux-2.5-11.el7.x86_64                    | libselinux-2.5-14.1.el7.x86_64               | libselinux-2.5-14.1.el7.x86_64                  | libselinux-2.5-14.1.el7.x86_64                 | libselinux-2.5-14.1.el7.x86_64                 | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.5-12.1.el7.x86_64             | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.5-14.1.el7.x86_64             | libselinux-2.5-14.1.el7.x86_64             |
| xterm                                           | xterm-295-3.el7.x86_64                          | xterm-295-3.el7.x86_64                       | xterm-295-3.el7.x86_64                          | xterm-295-3.el7.x86_64                         | xterm-295-3.el7.x86_64                         | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     | xterm-295-3.el7.x86_64                     |
| autoconf                                        | autoconf-2.69-11.el7.noarch                     | autoconf-2.69-11.el7.noarch                  | autoconf-2.69-11.el7.noarch                     | autoconf-2.69-11.el7.noarch                    | autoconf-2.69-11.el7.noarch                    | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                | autoconf-2.69-11.el7.noarch                |
| libtool                                         | libtool-2.4.2-22.el7_3.x86_64                   | libtool-2.4.2-22.el7_3.x86_64                | libtool-2.4.2-22.el7_3.x86_64                   | libtool-2.4.2-22.el7_3.x86_64                  | libtool-2.4.2-22.el7_3.x86_64                  | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              | libtool-2.4.2-22.el7_3.x86_64              |
| texinfo                                         | texinfo-5.1-5.el7.x86_64                        | texinfo-5.1-5.el7.x86_64                     | texinfo-5.1-5.el7.x86_64                        | texinfo-5.1-5.el7.x86_64                       | texinfo-5.1-5.el7.x86_64                       | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   | texinfo-5.1-5.el7.x86_64                   |
| zlib1g-dev                                      | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| gcc-multilib                                    | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| build-essential                                 | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| SDL-devel                                       | SDL-devel-1.2.15-14.el7.x86_64                  | SDL-devel-1.2.15-14.el7.x86_64               | SDL-devel-1.2.15-14.el7.x86_64                  | SDL-devel-1.2.15-14.el7.x86_64                 | SDL-devel-1.2.15-14.el7.x86_64                 | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             | SDL-devel-1.2.15-14.el7.x86_64             |
| glibc-devel                                     | glibc-devel-2.17-292.el7.x86_64                 | glibc-devel-2.17-292.el7.x86_64              | glibc-devel-2.17-307.el7.x86_64                 | glibc-devel-2.17-307.el7.1.x86_64              | glibc-devel-2.17-307.el7.1.x86_64              | glibc-devel-2.17-292.el7.x86_64            | glibc-devel-2.17-307.el7.x86_64            | glibc-devel-2.17-292.el7.x86_64            | glibc-devel-2.17-307.el7.1.x86_64          | glibc-devel-2.17-307.el7.1.x86_64          |
| glib2-devel                                     | glib2-devel-2.56.1-5.el7.x86_64                 | glib2-devel-2.56.1-5.el7.x86_64              | glib2-devel-2.56.1-5.el7.x86_64                 | glib2-devel-2.56.1-5.el7.x86_64                | glib2-devel-2.56.1-5.el7.x86_64                | glib2-devel-2.56.1-5.el7.x86_64            | glib2-devel-2.56.1-5.el7.x86_64            | glib2-devel-2.56.1-5.el7.x86_64            | glib2-devel-2.56.1-5.el7.x86_64            | glib2-devel-2.56.1-5.el7.x86_64            |
| automake                                        | automake-1.13.4-3.el7.noarch                    | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                    | automake-1.13.4-3.el7.noarch                   | automake-1.13.4-3.el7.noarch                   | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               | automake-1.13.4-3.el7.noarch               |
| screen                                          | gnome-screenshot-3.22.0-1.el7.x86_64            | gnome-screenshot-3.22.0-1.el7.x86_64         | gnome-screenshot-3.22.0-1.el7.x86_64            | gnome-screenshot-3.22.0-1.el7.x86_64           | gnome-screenshot-3.22.0-1.el7.x86_64           | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       | gnome-screenshot-3.22.0-1.el7.x86_64       |
| pax                                             | pax-3.4-19.el7.x86_64                           | pax-3.4-19.el7.x86_64                        | pax-3.4-19.el7.x86_64                           | pax-3.4-19.el7.x86_64                          | pax-3.4-19.el7.x86_64                          | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      | pax-3.4-19.el7.x86_64                      |
| libstdc++                                       | libstdc++-4.8.5-44.el7.x86_64                   | libstdc++-4.8.5-44.el7.x86_64                | libstdc++-4.8.5-44.el7.x86_64                   | libstdc++-4.8.5-44.el7.x86_64                  | libstdc++-4.8.5-44.el7.x86_64                  | libstdc++-4.8.5-16.el7_4.1.x86_64          | libstdc++-4.8.5-39.el7.x86_64              | libstdc++-4.8.5-39.el7.x86_64              | libstdc++-4.8.5-39.el7.x86_64              | libstdc++-4.8.5-39.el7.x86_64              |
| g++ (gcc-c++)                                   | gcc-c++-4.8.5-44.el7.x86_64                     | gcc-c++-4.8.5-44.el7.x86_64                  | gcc-c++-4.8.5-44.el7.x86_64                     | gcc-c++-4.8.5-44.el7.x86_64                    | gcc-c++-4.8.5-44.el7.x86_64                    | gcc-c++-4.8.5-16.el7_4.1.x86_64            | gcc-c++-4.8.5-39.el7_4.1.x86_64            | gcc-c++-4.8.5-39.el7.x86_64                | gcc-c++-4.8.5-39.el7.x86_64                | gcc-c++-4.8.5-39.el7.x86_64                |
| python3-pip                                     | python34-pip-8.1.2-10.el7.noarch                | python34-pip-8.1.2-10.el7.noarch             | python34-pip-8.1.2-10.el7.noarch                | python34-pip-8.1.2-10.el7.noarch               | python34-pip-8.1.2-10.el7.noarch               | python34-pip-8.1.2-10.el7.noarch           | python34-pip-8.1.2-10.el7.noarch           | python34-pip-8.1.2-10.el7.noarch           | python34-pip-8.1.2-10.el7.noarch           | python34-pip-8.1.2-10.el7.noarch           |
| perl-dat-dumper                                 | perl-dat-dumper-2.145-3.el7.x86_64              | perl-dat-dumper-2.145-3.el7.x86_64           | perl-dat-dumper-2.145-3.el7.x86_64              | perl-dat-dumper-2.145-3.el7.x86_64             | perl-dat-dumper-2.145-3.el7.x86_64             | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         | perl-dat-dumper-2.145-3.el7.x86_64         |
| perl-thread-queue                               | perl-thread-queue-3.02-2.el7.noarch             | perl-thread-queue-3.02-2.el7.noarch          | perl-thread-queue-3.02-2.el7.noarch             | perl-thread-queue-3.02-2.el7.noarch            | perl-thread-queue-3.02-2.el7.noarch            | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        | perl-thread-queue-3.02-2.el7.noarch        |
| perl-Text-ParseWords                            | NA                                              | perl-Text-ParseWords-3.29-4.el7.noarch       | perl-Text-ParseWords-3.29-4.el7.noarch          | perl-Text-ParseWords-3.29-4.el7.noarch         | perl-Text-ParseWords-3.29-4.el7.noarch         | NA                                         | perl-Text-ParseWords-3.29-4.el7.noarch     | perl-Text-ParseWords-3.29-4.el7.noarch     | perl-Text-ParseWords-3.29-4.el7.noarch     | perl-Text-ParseWords-3.29-4.el7.noarch     |
| xz(xz-utils)                                    | xz-5.2.2-1.el7.x86_64                           | xz-5.2.2-1.el7.x86_64                        | xz-5.2.2-1.el7.x86_64                           | xz-5.2.2-1.el7.x86_64                          | xz-5.2.2-1.el7.x86_64                          | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      | xz-5.2.2-1.el7.x86_64                      |
| perl                                            | perl-5.16.3-292.el7.x86_64                      | perl-5.16.3-292.el7.x86_64                   | perl-5.16.3-292.el7.x86_64                      | perl-5.16.3-292.el7.x86_64                     | perl-5.16.3-292.el7.x86_64                     | perl-5.16.3-292.el7.x86_64                 | perl-5.16.3-292.el7.x86_64                 | perl-5.16.3-292.el7.x86_64                 | perl-5.16.3-292.el7.x86_64                 | perl-5.16.3-292.el7.x86_64                 |
| cpp                                             | cpp-4.8.5-44.el7_4.1.x86_64                     | cpp-4.8.5-44.el7_4.1.x86_64                  | cpp-4.8.5-44.el7_4.1.x86_64                     | cpp-4.8.5-44.el7_4.1.x86_64                    | cpp-4.8.5-44.el7_4.1.x86_64                    | cpp-4.8.5-39.el7.x86_64                    | cpp-4.8.5-39.el7.x86_64                    | cpp-4.8.5-39.el7.x86_64                    | cpp-4.8.5-39.el7.x86_64                    | cpp-4.8.5-39.el7.x86_64                    |
| patch                                           | patch-2.7.1-8.el7.x86_64                        | patch-2.7.1-8.el7.x86_64                     | patch-2.7.1-8.el7.x86_64                        | patch-2.7.1-8.el7.x86_64                       | patch-2.7.1-8.el7.x86_64                       | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_64                  | patch-2.7.1-11.el7.x86_64                  |
| python3- GitPython(python3-git)                 | python3-GitPython                               | python3-GitPython                            | python3-GitPython                               | python3-GitPython                              | python3-GitPython                              | python3-GitPython                          | python3-GitPython                          | python3-GitPython                          | python3-GitPython                          | python3-GitPython                          |
| python3-jinja2                                  | python3-jinja2                                  | python3-jinja2                               | python3-jinja2                                  | python3-jinja2                                 | python3-jinja2                                 | python3-jinja2                             | python3-jinja2                             | python3-jinja2                             | python3-jinja2                             | python3-jinja2                             |
| python3-pexpect                                 | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| diffutils                                       | diffutils-3.3-4.el7.x86_64                      | diffutils-3.3-4.el7.x86_64                   | diffutils-3.3-4.el7.x86_64                      | diffutils-3.3-4.el7.x86_64                     | diffutils-3.3-4.el7.x86_64                     | diffutils-3.3-4.el7.x86_64                 | diffutils-3.3-4.el7.x86_64                 | diffutils-3.3-4.el7.x86_64                 | diffutils-3.3-4.el7.x86_64                 | diffutils-3.3-4.el7.x86_64                 |
| ccache                                          | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| which                                           | which-2.20-7.el7.x86_64                         | which-2.20-7.el7.x86_64                      | which-2.20-7.el7.x86_64                         | which-2.20-7.el7.x86_64                        | which-2.20-7.el7.x86_64                        | which-2.20-7.el7.x86_64                    | which-2.20-7.el7.x86_64                    | which-2.20-7.el7.x86_64                    | which-2.20-7.el7.x86_64                    | which-2.20-7.el7.x86_64                    |
| debianutils                                     | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| iputils-ping                                    | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| libegl1-mesa                                    | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| libsdl1.2-dev                                   | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| pylint3                                         | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| python3                                         | python3-3.6.8-13.el7.x86_64                     | python3-3.6.8-13.el7.x86_64                  | python3-3.6.8-13.el7.x86_64                     | python3-3.6.8-13.el7.x86_64                    | python3-3.6.8-13.el7.x86_64                    | python3-3.6.8-13.el7.x86_64                | python3-3.6.8-13.el7.x86_64                | python3-3.6.8-13.el7.x86_64                | python3-3.6.8-13.el7.x86_64                | python3-3.6.8-13.el7.x86_64                |
| cpio                                            | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| git-core                                        | NA                                              | NA                                           | NA                                              | NA                                             | NA                                             | NA                                         | NA                                         | NA                                         | NA                                         | NA                                         |
| tftp-server                                     | tftp-server                                     | tftp-server                                  | tftp-server                                     | tftp-server                                    | tftp-server                                    | tftp-server                                | tftp-server                                | tftp-server                                | tftp-server                                | tftp-server                                |
| gnupg                                           | gnupg2-2.0.22-4.el7.x86_64                      | gnupg2-2.0.22-4.el7.x86_64                   | gnupg2-2.0.22-4.el7.x86_64                      | gnupg2-2.0.22-4.el7.x86_64                     | gnupg2-2.0.22-4.el7.x86_64                     | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 | gnupg2-2.0.22-4.el7.x86_64                 |

### Ubuntu

| Tool/Library                                    | Ubuntu Desktop   /Server 16.04.05(64-bit) | Ubuntu Desktop /Server 16.04.06 (64-bit) | Ubuntu Desktop /Server 18.04.01 (64-bit)    | Ubuntu Desktop /Server 18.04.02 (64-bit)    | Ubuntu Desktop /Server 18.04.03 (64-bit)    | Ubuntu Desktop /Server 18.04.04 (64-bit)    |
| ----------------------------------------------- | ----------------------------------------- | ---------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| ip (iproute)                                    | iproute2 4.3.0-1ubuntu3.16.04.5           | iproute2 4.3.0-1ubuntu3.16.04.6          | iproute2 4.15.0-2ubuntu1.1                  | iproute2 4.15.0-2ubuntu1.1                  | iproute2 4.15.0-2ubuntu1.1                  | iproute2 4.15.0-2ubuntu1.1                  |
| gawk                                            | gawk-1:4.1.3+dfsg-0.1                     | gawk-1:4.1.3+dfsg-0.1                    | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   | gawk-1:4.1.4+dfsg-1build1                   |
| gcc                                             | gcc-4:5.3.1-1ubuntu1 500                  | gcc-4:5.3.1-1ubuntu1 500                 | gcc-4:7.4.0-1ubuntu2.3                      | gcc-4:7.4.0-1ubuntu2.3                      | gcc-4:7.4.0-1ubuntu2.3                      | gcc-4:7.4.0-1ubuntu2.3                      |
| netstat (net-tools)                             | net-tools-1.60-26ubuntu1 500              | net-tools-1.60-26ubuntu1 500             | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 | net-tools-1.60+git20161116.90da8a0-1ubuntu1 |
| ncurses-devel(libncurses5-dev)                  | ncurses-devel-6.0+20160213-1ubuntu1       | ncurses-devel-6.0+20160213-1ubuntu1      | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            | ncurses-devel-6.1-1ubuntu1.18.04            |
| zlib-devel(also,install 32-bit of this version) |                                           |                                          |                                             |                                             |                                             |                                             |
| openssl-devel                                   | openssl-devel-1.0.2g-1ubuntu4.15          | openssl-devel-1.0.2g-1ubuntu4.15         | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-ubuntu2.1~18.04.4       | openssl-devel-1.1.1-ubuntu2.1~18.04.6       | openssl-devel-1.1.1-ubuntu2.1~18.04.4       |
| flex                                            | flex-2.6.0-11                             | flex-2.6.0-11                            | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                | flex-2.6.4-6                                |
| bison                                           | bison-2:3.0.4.dfsg-1                      | bison-2:3.0.4.dfsg-1                     | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  | bison-2:3.0.4.dfsg-1build1                  |
| libselinux                                      |                                           |                                          |                                             |                                             |                                             |                                             |
| xterm                                           | xterm-322-1ubuntu1                        | xterm-322-1ubuntu1                       |                                             | xterm-330-1ubuntu2                          | xterm-330-1ubuntu2                          | xterm-330-1ubuntu2                          |
| autoconf                                        | autoconf-2.69-9                           | autoconf-2.69-9                          | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            | autoconf-2.69-11                            |
| libtool                                         | libtool-2.4.6-0.1                         | libtool-2.4.6-0.1                        | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             | libtool-2.4.6-2                             |
| texinfo                                         | texinfo-6.1.0.dfsg.1-5                    | texinfo-6.1.0.dfsg.1-5                   | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      | texinfo-6.5.0.dfsg.1-2                      |
| zlib1g-dev                                      | zlib1g-dev1:1.2.8.dfsg-2ubuntu4.1         | zlib1g-dev1:1.2.8.dfsg-2ubuntu4.1        | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            | zlib1g-dev1:1.2.11.dfsg-0ubuntu2            |
| gcc-multilib                                    | gcc-multilib-4:5.3.1-1ubuntu1             | gcc-multilib-4:5.3.1-1ubuntu1            | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             | gcc-multilib-4:7.4.0-1ubuntu2.3             |
| build-essential                                 | build-essential-12.1ubuntu2               | build-essential-12.1ubuntu2              | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 | build-essential-12.4ubuntu1                 |
| SDL-devel                                       | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| glibc-devel                                     | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| glib2-devel                                     | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| automake                                        | automake-1:1.15-4ubuntu1                  | automake-1:1.15-4ubuntu1                 | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  | automake-1:1.15.1-3ubuntu2                  |
| screen                                          | screen-4.3.1-2build1                      | screen-4.3.1-2build1                     | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       | screen-4.6.2-1ubuntu1                       |
| pax                                             | pax-1:20151013-1                          | pax-1:20151013-1                         | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-2                            | pax-1:20171021-2                            |
| libstdc++                                       | libstdc++-5.4.0-6ubuntu1~16.04.9cross1    | libstdc++-5.4.0-6ubuntu1~16.04.9cross1   | libstdc++-6.5.0-2ubuntu1~18.04              | libstdc++-8.3.0-6ubuntu1~18.04              | libstdc++-8.3.0-6ubuntu1~18.04              | libstdc++-8.3.0-6ubuntu1~18.04              |
| g++ (gcc-c++)                                   | g++-4:5.3.1-1ubuntu1                      | g++-4:5.3.1-1ubuntu1                     | g++-4:7.4.0-1ubuntu2.3                      | g++-7.4.0-1ubuntu1~18.04                    | g++-7.4.0-1ubuntu1~18.04                    | g++-7.4.0-1ubuntu1~18.04                    |
| python3-pip                                     | python3-pip (8.1.1-2)                     | python3-pip (8.1.1-2)                    | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       | python3-pip (9.0.1-2)                       |
| perl-dat-dumper                                 | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| perl-thread-queue                               | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| perl-Text-ParseWords                            | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| xz(xz-utils)                                    | xz-utils (5.1.1alpha+20120614-2ubuntu2)   | xz-utils (5.1.1alpha+20120614-2ubuntu2)  | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        | xz-utils (5.2.2-1.3)                        |
| perl                                            | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| cpp                                             | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| patch                                           | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| python3- GitPython(python3-git)                 | python3-git (1.0.1+git137-gc8b8379-2.1)   | python3-git (1.0.1+git137-gc8b8379-2.1)  | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       | python3-git (2.1.8-1)                       |
| python3-jinja2                                  | python3-jinja2 (2.8-1ubuntu0.1)           | python3-jinja2 (2.8-1ubuntu0.1)          | python3-jinja2 (2.10-1ubuntu0.18.04)        | python3-jinja2 (2.10-1ubuntu0.18.04)        | python3-jinja2 (2.10-1ubuntu0.18.04)        | python3-jinja2 (2.10-1ubuntu0.18.04)        |
| python3-pexpect                                 | python3-pexpect (4.0.1-1)                 | python3-pexpect (4.0.1-1)                | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   | python3-pexpect (4.2.1-1)                   |
| diffutils                                       | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| ccache                                          | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| which                                           | NA                                        | NA                                       | NA                                          | NA                                          | NA                                          | NA                                          |
| debianutils                                     | debianutils 4.7                           | debianutils 4.7                          | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.8.4)                         | debianutils (4.8.4)                         |
| iputils-ping                                    | iputils-ping 3:20121221-5ubuntu2          | iputils-ping 3:20121221-5ubuntu2         | iputils-ping 3:20161105-1ubuntu2            | iputils-ping 3:20161105-1ubuntu2            | iputils-ping 3:20161105-1ubuntu2            | iputils-ping 3:20161105-1ubuntu2            |
| libegl1-mesa                                    | libegl1-mesa 11.2.0-1ubuntu2              | libegl1-mesa 11.2.0-1ubuntu2             | libegl1-mesa 19.2.8-0ubuntu0~18.04          | libegl1-mesa 19.2.8-0ubuntu0~18.04          | libegl1-mesa 19.2.8-0ubuntu0~18.04          | libegl1-mesa 19.2.8-0ubuntu0~18.04          |
| libsdl1.2-dev                                   | libsdl1.2-dev 1.2.15+dfsg1-3ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg1-3ubuntu0.1    | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     | libsdl1.2-dev 1.2.15+dfsg2-0.1ubuntu0.1     |
| pylint3                                         | pylint3-1.5.2-1ubuntu1                    | pylint3-1.5.2-1ubuntu1                   | pylint3-1.8.3-1                             | pylint3-1.8.3-1                             | pylint3-1.8.3-1                             | pylint3-1.8.3-1                             |
| python3                                         | python3 (3.5.1-3)                         | python3 (3.5.1-3)                        | python3 (3.6.5-3)                           | python3 (3.6.5-3)                           | python3 (3.6.5-3)                           | python3 (3.6.5-3)                           |
| cpio                                            | cpio 2.11+dfsg-5ubuntu1.1                 | cpio 2.11+dfsg-5ubuntu1.1                | cpio 2.12+dfsg-6ubuntu0.18.04               | cpio 2.12+dfsg-6ubuntu0.18.04               | cpio 2.12+dfsg-6ubuntu0.18.04               | cpio 2.12+dfsg-6ubuntu0.18.04               |
| git-core                                        | git-core 1:2.7.4-0ubuntu1.9               | git-core 1:2.7.4-0ubuntu1.9              | NA                                          | NA                                          | NA                                          | NA                                          |
| tftp-server                                     | tftpd-hpa                                 | tftpd-hpa                                | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   | tftpd-hpa                                   |
| gnupg                                           | gnupg-1.4.20-1ubuntu3.3                   | gnupg-1.4.20-1ubuntu3.3                  | gnupg-2.2.4-1ubuntu1.2                      | gnupg-2.2.4-1ubuntu1.2                      | gnupg-2.2.4-1ubuntu1.2                      | gnupg-2.2.4-1ubuntu1.2                      |

# README_content_v2020_2

=============================

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2020.2 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2020.2 Open Components Source Code (TAR/GZIP) file: 
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