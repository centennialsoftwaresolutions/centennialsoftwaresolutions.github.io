# 67409 - PetaLinux 2016.2 - Product Update Release Notes and Known Issues

## Title

67409 - PetaLinux 2016.2 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2016.2 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**PetaLinux 2016.2 contains the following build collateral:**

| Component | Tag Name       | Comments          |
| --------- | -------------- | ----------------- |
| Linux     | xilinx-v2016.2 | Version: 4.4      |
| U-boot    | xilinx-v2016.2 | Version: v2016.01 |

**PetaLinux 2016.2 New Features:**

**KERNEL**

Comparison of the log between the **2016.1** and **2016.2** kernels can be found here:

[https://github.com/Xilinx/linux-xlnx/compare/xilinx-v2016.1...xilinx-v2016.2](https://github.com/Xilinx/linux-xlnx/compare/xilinx-v2016.1...xilinx-v2016.2)

**QEMU**

Please refer to the change log here:

[http://www.wiki.xilinx.com/QEMU](http://www.wiki.xilinx.com/QEMU)

**FSBL**

| Answer Record Number                                         | Answer Record Title                                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Xilinx Answer 67411](https://adaptivesupport.amd.com/s/article/67411) | Zynq UltraScale+ MPSoC: 2016.2 FSBL, Added Boot time/performance measurement feature |
| [Xilinx Answer 67412](https://adaptivesupport.amd.com/s/article/67412) | Zynq UltraScale+ MPSoC: 2016.2 FSBL, Added DDR ECC Initialization feature |

**Bare-metal, Linux and u-boot**

| Answer Record Number                                         | Answer Record Title                                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Xilinx Answer 67413](https://adaptivesupport.amd.com/s/article/67413) | Zynq UltraScale+ MPSoC: Added software support in 2016.2 for eMMC MTFC64GJDDN-4M IT |

**Linux Driver**

  

-   Added support for Error Detection And Correction (EDAC) support for OCM.
-   Added EDAC support for DDR controller in PS block for Zynq MPSoC devices.
-   Added support for Quad SPI mode when using AXI QSPI IP

**Known Issues for 2016.2**

| Linux/Standalone     | Application | Description                                                  | Work-around                                                  | To be fixed version |
| -------------------- | ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------- |
| Linux and Standalone | PMUFW       | 2016.2 PMUFW - RPU1 suspend/resume operation does not work   | [Xilinx Answer 67418](https://adaptivesupport.amd.com/s/article/67418) | 2016.3              |
| Linux                | PetaLinux   | 2016.2 PetaLinux - Installer Automatically Appends Sub-Directory to Target Installation Path | [Xilinx Answer 67416](https://adaptivesupport.amd.com/s/article/67416) | 2016.3              |
| Linux and Standalone | FSBL        | FSBL unable to load PMUFW in SD boot mode                    | [Xilinx Answer 67414](https://adaptivesupport.amd.com/s/article/67414) | 2016.3              |
| Linux                | XEN         | XEN test is not working on Zynq UltraScale+ MPSoC boards in QEMU | [Xilinx Answer 67420](https://adaptivesupport.amd.com/s/article/67420) | 2016.3              |
| Linux                | Libraries   | ZCU102 vector in TCM failed to Jump to text in OCM on R5-1 core | none                                                         | 2016.3              |
| Linux                | PetaLinux   | PetaLinux, Zynq UltraScale+ MPSoC: Ethernet link between ZCU102 and a host machine at 100M/Full does not work | [Xilinx Answer 66553](https://adaptivesupport.amd.com/s/article/66553) | 2016.3              |
| Linux                | PetaLinux   | 2016.2 PetaLinux - PetaLinux Install require 32-bit compatible libraries to be installed | [Xilinx Answer 67503](https://adaptivesupport.amd.com/s/article/67503) | 2016.3              |

**2016.2 Bug Fixes**

| Linux/Standalone | Application | Description                                                  | CR#    | To be fixed version |
| ---------------- | ----------- | ------------------------------------------------------------ | ------ | ------------------- |
| Standalone       | Drivers     | The "MsaConfig->InitWait" calculation remains the same for RGB and YUV444. | 949773 | 2016.2              |
| Standalone       | Drivers     | Update the DisplayPort SS TX driver to set the MSA to asynchronous mode | 949772 | 2016.2              |