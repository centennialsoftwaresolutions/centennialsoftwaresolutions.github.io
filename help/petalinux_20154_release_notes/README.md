# 66107 - PetaLinux 2015.4 - Product Update Release Notes and Known Issues

## Title

66107 - PetaLinux 2015.4 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2015.4 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**PetaLinux 2015.4 contains the following build collateral:**

\* Linux Kernel Version 4.0 (Git tag: xilinx-v2015.4)

\* U-Boot Version 2015.07 (Git tag: xilinx-v2015.4)

**PetaLinux 2015.4 New Features**

- PetaLinux, QEMU, OpenAMP will now support Zynq UltraScale+ MPSoC.

- Arm Trusted Firmware (ATF) is now included with Petalinux 2015.4 to support Zynq UltraScale+

- Petalinux 2015.4 release supports the new Vivado DDR patch. For more details, see [(Xilinx Answer 65982)](https://adaptivesupport.amd.com/s/article/65982)

- Xen Hypervisor is now included in ZCU102 BSP as a technology demonstration.

| Answer Record Number                                         | Answer Record Title                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Xilinx Answer 66148](https://adaptivesupport.amd.com/s/article/66148) | 2015.4 Petalinux - petalinux-util command allows connection of XSDB to a running QEMU instance |
| [Xilinx Answer 66150](https://adaptivesupport.amd.com/s/article/66150) | 2015.4 Petalinux - Petalinux DTG will now support Zynq MPSoC, Zynq 7000 and MicroBlaze processors |
| [Xilinx Answer 66163](https://adaptivesupport.amd.com/s/article/66163) | 2015.4 Petalinux - Splits pre-built packages into -dbg and -dev |
| [Xilinx Answer 66213](https://adaptivesupport.amd.com/s/article/66213) | 2015.4 Petalinux - U-BOOT autoconfig is now enabled by default for Zynq MPSoC |

**Petalinux 2015.4 Bug fixes**

| Answer Record Number                                         | Answer Record Title                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Xilinx Answer 66152](https://adaptivesupport.amd.com/s/article/66152) | 2015.2.1 Petalinux - Selecting ncurses-tools package for rootfs causes errors during petalinux-build |
| [Xilinx Answer 66164](https://adaptivesupport.amd.com/s/article/66164) | 2015.4 Petalinux - FIT image image.ub works for ZynqMP       |

**Known Issues for 2015.4**

**There are file name mismatches between the documentation and the actual filenames for the installer downloads on [www.xilinx.com](http://www.xilinx.com/)**

| Documented Installer file Name        | Actual Installer filenames                |
| :------------------------------------ | :---------------------------------------- |
| petalinux-v2015.4-final-installer.run | petalinux-v2015.4-final-installer-dec.run |
| Xilinx-ZCU102-v2015.4-final.bsp       | Xilinx-ZCU102-v2015.4-final-dec.bsp       |

| Answer Record Number                                         | Answer Record Title                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Xilinx Answer 66110](https://adaptivesupport.amd.com/s/article/66110) | 2015.4 Petalinux - Device Tree Generator generates DTSIs for PS but not for PL in Zynq MPSoC |
| [Xilinx Answer 66144](https://adaptivesupport.amd.com/s/article/66144) | 2015.4 Petalinux - Zynq MPSoC clock.dtsi is static.          |
| [Xilinx Answer 66145](https://adaptivesupport.amd.com/s/article/66145) | 2015.4 Petalinux - petalinux-util --jtag-logbuf will not support A53 |
| [Xilinx Answer 66170](https://adaptivesupport.amd.com/s/article/66170) | 2015.4 Petalinux - Libraries from toolchains such as libc are not stripped on the target rootfs |
| [Xilinx Answer 66176](https://adaptivesupport.amd.com/s/article/66176) | 2015.4 XSDK, OpenAMP - Cannot create FreeRTOS OpenAMP apps when selecting "Create New" BSP option |
| [Xilinx Answer 66177](https://adaptivesupport.amd.com/s/article/66177) | 2015.4 XSDK, OpenAMP - Compilation warnings when building FreeRTOS Zynq OpenAMP applications |
| [Xilinx Answer 66178](https://adaptivesupport.amd.com/s/article/66178) | 2015.4 XSDK, OpenAMP - Running FreeRTOS OpenAMP apps display an assert error saying “Assert failed in file port.c, line 410” when exiting the application. |
| [Xilinx Answer 66185](https://adaptivesupport.amd.com/s/article/66185) | 2015.4 OPENAMP FreeRTOS RPC demo fails occasionally on Zynq MPSoC |
| [Xilinx Answer 66182](https://adaptivesupport.amd.com/s/article/66182) | 2015.4 Petalinux - QEMU does not include SDL to display graphic output over virtual Display Port |
| [Xilinx Answer 66187](https://adaptivesupport.amd.com/s/article/66187) | 2015.4 Petalinux - QEMU does not connect all GEM's to host network |
| [Xilinx Answer 66367](https://adaptivesupport.amd.com/s/article/66367) | 2015.4 Petalinux - MIO Ethernet does not work on ZCU102 RevB boards with the 2015.4 Petalinux ZCU102 BSP |