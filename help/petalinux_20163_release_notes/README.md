## 68057 - PetaLinux 2016.3 - Product Update Release Notes and Known Issues



## Title

68057 - PetaLinux 2016.3 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2016.3 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**PetaLinux 2016.3 contains the following build collateral:**

| Component                  | Tag/Branch     | Comments                               |
| :------------------------- | :------------- | :------------------------------------- |
| device-tree-generator      | xilinx-v2016.3 |                                        |
| Linux                      | xilinx-v2016.3 | Kernel Version 4.6                     |
| UBoot                      | xilinx-v2016.3 | Uboot Version 2016.7                   |
| Xen                        | xilinx-v2016.3 |                                        |
| ARM-Trusted-Firmware (ATF) | xilinx-v2016.3 | ATF is based on upstream version 1.2   |
| GCC                        |                | - MB compiler version 5.2<br>- ARM 5.2 |
| YOCTO                      |                | Krogoth (2.1)                          |

**BSPs supported for 2016.3 PetaLinux Release**

This table contains supported BSPs for Zynq, MicroBlaze and Zynq MPSoC.

| Platform   | Variant  | BSP Name                                  |
| ---------- | -------- | ----------------------------------------- |
| Zynq       | ZC702    | Xilinx-ZC702-v2016.3-final.bsp            |
| Zynq       | ZC706    | Xilinx-ZC706-v2016.3-final.bsp            |
| Zynq       | ZEDBOARD | Avnet-Digilent-ZedBoard-v2016.3-final.bsp |
| MicroBlaze | KC705    | Xilinx-KC705-v2016.3-final.bsp            |
| MicroBlaze | AC701    | Xilinx-AC701-v2016.3-final.bsp            |
| MicroBlaze | KCU105   | Xilinx-KCU105-AXI-full-v2016.3-final.bsp  |
| Zynq MPSoC | ZCU102   | Xilinx-ZCU102-v2016.3-final.bsp           |

**PetaLinux 2016.3 New Features:**

 

**PetaLinux**

| Answer Record Number                                         | Answer Record Title                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Xilinx Answer 67958](https://adaptivesupport.amd.com/s/article/67958) | 2016.3 PetaLinux - XEN backend Network Driver Enabled by Default |
| [Xilinx Answer 67968](https://adaptivesupport.amd.com/s/article/67968) | 2016.3 PetaLinux - The Bridge Utils package is included in the PetaLinux Root File System and is enabled by Default |
| [Xilinx Answer 67971](https://adaptivesupport.amd.com/s/article/67971) | 2016.3 PetaLinux - Drop Bear is now enabled by default in the PetaLinux Root File System |
| [Xilinx Answer 67985](https://adaptivesupport.amd.com/s/article/67985) | 2016.3 PetaLinux - KCU105 Board Support Package is supported in 2016.3 PetaLinux |
| [Xilinx Answer 68124](https://adaptivesupport.amd.com/s/article/68124) | 2016.3 PetaLinux - PetaLinux now supports Zynq Single core devices |

**Yocto**

| Answer Record Number                                         | Answer Record Title           |
| :----------------------------------------------------------- | :---------------------------- |
| [Xilinx Answer 68119](https://adaptivesupport.amd.com/s/article/68119) | 2016.3 Yocto Release features |

**FSBL**

| Answer Record Number                                         | Answer Record Title                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Xilinx Answer 67952](https://adaptivesupport.amd.com/s/article/67952) | Zynq-7000 SoC, 2016.3 FSBL: Supports Single-core ARM Cortex-A9 MPCore |
| [Xilinx Answer 67953](https://adaptivesupport.amd.com/s/article/67953) | Zynq UltraScale+ MPSoC, 2016.3 FSBL and PMUFW: Support for Isolation (Enhanced Security Configuration) |
| [Xilinx Answer 67954](https://adaptivesupport.amd.com/s/article/67954) | Zynq UltraScale+ MPSoC, 2016.3 FSBL: Memory Layout changes   |
| [Xilinx Answer 67955](https://adaptivesupport.amd.com/s/article/67955) | Zynq UltraScale+ MPSoC, 2016.3 FSBL: Add XFsbl_HookPsuInit() to provide a way to load alternative psu_init |
| [Xilinx Answer 67987](https://adaptivesupport.amd.com/s/article/67987) | Zynq UltraScale+ MPSoC: 2016.3 FSBL TCM ECC Initialization   |

**UBoot**

**Configuration device support for Uboot:**

[(Xilinx Answer 65463)](https://adaptivesupport.amd.com/s/article/65463)

 

**PMU Firmware**

| Answer Record Number                                         | Answer Record Title                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Xilinx Answer 67820](https://adaptivesupport.amd.com/s/article/67820) | Zynq UltraScale+ MPSoC: 2016.3 PMUFW, Error Management       |
| [Xilinx Answer 67818](https://adaptivesupport.amd.com/s/article/67818) | Zynq UltraScale+ MPSoC: 2016.3 PMUFW Loading via JTAG / SD Boot Modes and Running An Example |
| [Xilinx Answer 67819](https://adaptivesupport.amd.com/s/article/67819) | Zynq UltraScale+ MPSoC: 2016.3 PMUFW, How to add custom init code. |

**Linux Driver**

| Answer Record Number                                         | Answer Record Title                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Xilinx Answer 68058](https://adaptivesupport.amd.com/s/article/68058) | 2016.3 PetaLinux Zynq UltraScale+ MPSoC Linux Reset Controller Driver |
| [Xilinx Answer 68077](https://adaptivesupport.amd.com/s/article/68077) | 2016.3 PetaLinux Zynq UltraScale+ MPSoC AXI Performance Monitor (APM) sample clock via Common Clock Framework (CCF) |
| [Xilinx Answer 68078](https://adaptivesupport.amd.com/s/article/68078) | 68078 - 2016.3 PetaLinux Zynq UltraScale+ MPSoC Power Management in NAND Linux driver |

**Known Issues for 2016.3**

| Linux/Standalone     | Application     | Description                                                  | Work-around                                                  | To be fixed version |
| :------------------- | :-------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :------------------ |
| Linux and Standalone | OpenAmp         | Zynq UltraScale+ MPSoC: 2016.3 RPU does not run from OCM when booting from SD. | [Xilinx Answer 67995](https://adaptivesupport.amd.com/s/article/67995) | 2017.1              |
| Linux                | PMU Firmware    | Zynq UltraScale+ MPSoC: 2016.3 PMU FW can hang when the debug prints are enabled. | [Xilinx Answer 67996](https://adaptivesupport.amd.com/s/article/67996) | 2017.1              |
| Standalone           | SSW_Libraries   | Zynq UltraScale+ MPSoC: In some cases, the USE_AMP flag enabled for RPU_1, prevents RPU_1 from getting interrupts | [Xilinx Answer 68000](https://adaptivesupport.amd.com/s/article/68000) | 2016.4              |
| Standalone           | FSBL            | Zynq UltraScale+ MPSoC, 2016.3 FSBL: Vectors region overwritten in R5 with secure partitions |                                                              | 2017.1              |
| Linux                | Devicetree      | 2016.3 PetaLinux - Zynq UltraScale+ MPSoC: During Linux boot up, warning messages are generated [ 5.001929] xilinx-zynqmp-dma ffa80000.dma: main clock not found | [Xilinx Answer 68118](https://adaptivesupport.amd.com/s/article/68118) | 2016.4              |
| Linux                | PetaLinux       | 2016.3 PetaLinux - Error message during bootup "[Firmware Warn]: /amba/ethernet@e000b000/mdio/phy@7: Whitelisted compatible string. Please remove" | [Xilinx Answer 68095](https://adaptivesupport.amd.com/s/article/68095) | 2016.4              |
| Standalone           | FSBL            | Zynq UltraScale+ MPSoC, 2016.3 FSBL: Vectors region overwritten in R5 with secure partitions | [Xilinx Answer 68001](https://adaptivesupport.amd.com/s/article/68001) | 2017.1              |
| Linux                | PMU Firmware    | Zynq UltraScale+ MPSoC, 2016.3 self-suspend example: Resume failed for R5-OCM | [Xilinx Answer 68002](https://adaptivesupport.amd.com/s/article/68002) | 2016.4              |
| Linux                | PMU Firmware    | Zynq UltraScale+ MPSoC: 2016.3 PMUFW will enable AIB (if existing) to isolate powered down components | [Xilinx Answer 68003](https://adaptivesupport.amd.com/s/article/68003) | 2016.4              |
| Linux                | PetaLinux       | 2016.3 PetaLinux: TCF agent is not loading automatically if I enable the TCF agent in the PetaLinux Config for all MicroBlaze designs. | [Xilinx Answer 68004](https://adaptivesupport.amd.com/s/article/68004) | 2016.4              |
| Standalone           | FSBL            | Zynq UltraScale+ MPSoC: 2016.3 FSBL fails to load latest PMUFW in NAND boot mode | [Xilinx Answer 68005](https://adaptivesupport.amd.com/s/article/68005) | 2016.4              |
| Linux                | ATF             | 2016.3 SDK - ATF: Suspend/Resume FPD down failed with SDK generated ATF Images | [Xilinx Answer 68162](https://adaptivesupport.amd.com/s/article/68162) | 2016.4              |
| Linux                | u-boot          | 2016.3 Zynq UltraScale+ MPSoC, Create Boot Image: u-boot image fails to boot | [Xilinx Answer 68061](https://adaptivesupport.amd.com/s/article/68061) | 2017.1              |
| Linux                | PetaLinux/Yocto | 2016.3/2016.4 PetaLinux/Yocto: Linux reboot command causing board to hang | [Xilinx Answer 68514](https://adaptivesupport.amd.com/s/article/68514) | 2017.1              |