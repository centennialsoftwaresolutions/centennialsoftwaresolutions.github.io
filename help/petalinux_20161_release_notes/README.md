# 67156 - PetaLinux 2016.1 - Product Update Release Notes and Known Issues

## Title

67156 - PetaLinux 2016.1 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2016.1 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**PetaLinux 2016.1 contains the following build collateral:**

| Component | Tag Name       | Comments          |
| --------- | -------------- | ----------------- |
| Linux     | xilinx-v2016.1 | Version: 4.4      |
| U-boot    | xilinx-v2016.1 | Version: v2016.01 |

### PetaLinux 2016.1 New Features:

### Open Source Linux

-   QEMU, Linux and Bare metal Support for ZCU102 and ZCU106
-   Improved comments and documentation for Linux drivers
-   DTG Support for ZCU102
-   Updated AXI DMA driver to support Multi Channel DMA
-   Updated SYSMON to support UltraScale devices
-   CANFD device driver for Xilinx CANFD IP
-   DTG support added for 64 bit PL IP's
-   DTG support for PL devices and interrupts in Zynq MPSoC devices
-   Updated AXI Traffic Generator (ATG) driver for 64-bit support
-   Updated AXI VDMA driver to support Zynq MPSoC
-   USB 3.0 Device mode functionality verified for Mass Storage Gadget for Zynq MPSoC
-   Linux driver support for AXI Ethernet IP
-   Linux driver support for PL IP cores - AXI-DMA, AXI UART 16550, AXI UART Lite, AXI timebase WDT, AXI Quad SPI, AXI I2C, AXI CAN, AXI XADC, AXI Traffic Generator, AXI Performance Monitor, AXI GPIO in Zynq MPSoC devices.
-   SGMII support was added in macb driver to enable SGMII and PCS related settings for Zynq MPSoC devices.

**Petalinux Tools**

-   BSP support for both ZCU102 and ZCU106
-   Meta-Petalinux Yocto Layer is now available on GIT

| Answer Record Number                                         | Answer Record Title                                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Xilinx Answer 67158](https://adaptivesupport.amd.com/s/article/67158) | 2016.1 Petalinux - Petalinux-package command allows PMUFW to be included in the boot image |
| [Xilinx Answer 67159](https://adaptivesupport.amd.com/s/article/67159) | 2016.1 Petalinux tools - ATF can be built in OCM or DDR using Petalinux tools |
| [Xilinx Answer 67160](https://adaptivesupport.amd.com/s/article/67160) | 2016.1 Petalinux - How to add packages to Petalinux          |

**Power Management**

-   All of the hardware features will be supported. For example, ability to power down each of the peripherals that support power management.
-   Powering down the PL will be supported
-   PL will be able to reset without resetting the PS
-   PS will be able to reset without resetting the PL

**U-boot**

-   Support for SATA as a secondary boot mode
-   AXI Ethernet SGMII support for MicroBlaze
-   Added GEM SGMII support for Zynq and Zynq MP

**Known Issues for 2016.1**

| Linux/Standalone | Application | Description                                                  | Work-around | To be fixed version |
| ---------------- | ----------- | ------------------------------------------------------------ | ----------- | ------------------- |
| Linux            | Drivers     | No Display Port display on monitor using ZCU102 Rev-A board  | None        | 2016.2              |
| Standalone       | Drivers     | The "MsaConfig->InitWait" calculation remains the same for RGB and YUV444. | None        | 2016.2              |
| Standalone       | Drivers     | Update the DisplayPort SS TX driver to set the MSA to asynchronous mode | None        | 2016.2              |
| Standalone       | libraries   | ZCU102 vector in TCM failed to jump to text in OCM on R5-1 core | None        | 2016.2              |