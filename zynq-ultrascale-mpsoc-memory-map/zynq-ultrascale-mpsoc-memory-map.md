# Zynq UltraScale+ MPSoC Memory Map

![Xilinx_logo](Xilinx_logo.png)

This post lists the memory map of the Zynq UltraScale+ MPSoC.

**<u><span>Links</span></u>**

Zynq UltraScale+ Device Technical Reference Manual UG1085 (v2.2) December 4, 2020

[<u><span>https://www.xilinx.com/support/documentation/user_guides/ug1085-zynq-ultrascale-trm.pdf</span></u>](https://www.xilinx.com/support/documentation/user_guides/ug1085-zynq-ultrascale-trm.pdf)

Zynq UltraScale+ Devices Register Reference UG1087 (v1.7) February 8, 2019

[<u><span>https://www.xilinx.com/html_docs/registers/ug1087/ug1087-zynq-ultrascale-registers.html</span></u>](https://www.xilinx.com/html_docs/registers/ug1087/ug1087-zynq-ultrascale-registers.html)

**<u><span>Memory Map</span></u>**

| Device Name                                                  | Start Address | End Address  |
| :----------------------------------------------------------- | :------------ | :----------- |
| DDR Low                                                      | 0x00000000    | 0x7FFFFFFF   |
| M_AXI_HPM0_LPD (LPD_PL)                                      | 0x80000000    | 0x9FFFFFFF   |
| VCU Encoder                                                  | 0xA0000000    |              |
| VCU Decoder                                                  | 0xA0020000    |              |
| VCU System-Level Control                                     | 0xA0040000    |              |
| M_AXI_HPM0_FPD (HPM0) interface(1)                           | 0xA4000000    | 0xAFFFFFFF   |
| M_AXI_HPM1_FPD (HPM1) interface                              | 0xB0000000    | 0xBFFFFFFF   |
| Quad-SPI                                                     | 0xC0000000    | 0xDFFFFFFF   |
| PCIe Low                                                     | 0xE0000000    | 0xEFFFFFFF   |
| Reserved                                                     | 0xF0000000    | 0xF7FFFFFF   |
| 128 MB reserved                                              | 0xF0000000    | 0xF7FFFFFF   |
| STM CoreSight                                                | 0xF8000000    | 0xF8FFFFFF   |
| APU GIC                                                      | 0xF9000000    | 0xF90FFFFF   |
| GIC distributor.                                             | 0xF9000000    | 0xF9001FFF   |
| APU GIC Interrupt  Controller; GICv2                         | 0xF9000000    |              |
| RPU GIC Interrupt  Controller; GICv1                         | 0xF9000000    |              |
| GICC interface.                                              | 0xF9002000    | 0xF9002FFF   |
| Reserved                                                     | 0xF9100000    | 0xFCFFFFFF   |
| 63 MB reserved                                               | 0xF9100000    | 0xFCFFFFFF   |
| FPD devices                                                  | 0xFD000000    | 0xFDFFFFFF   |
| Memory Protection Unit  (XMPU) 0 Configuration               | 0xFD000000    |              |
| Memory Protection Unit  (XMPU) 1 Configuration               | 0xFD010000    |              |
| Memory Protection Unit  (XMPU) 2 Configuration               | 0xFD020000    |              |
| Memory Protection Unit  (XMPU) 3 Configuration               | 0xFD030000    |              |
| Memory Protection Unit  (XMPU) 4 Configuration               | 0xFD040000    |              |
| Memory Protection Unit  (XMPU) 5 Configuration               | 0xFD050000    |              |
| DDR controller                                               | 0xFD070000    |              |
| DDR Memory Controller                                        | 0xFD070000    |              |
| DDR PHY                                                      | 0xFD080000    |              |
| DDR PHY Register  Description, DDR PHY Control               | 0xFD080000    |              |
| DDR QoS control                                              | 0xFD090000    |              |
| DDR QoS Control                                              | 0xFD090000    |              |
| Arm for DDR                                                  | 0xFD0B0000    |              |
| AXI DDR Performance  Monitor                                 | 0xFD0B0000    |              |
| SATA registers (HBA, vendor, port-0/1  control)              | 0xFD0C0000    |              |
| SATA AHCI HBA Spec                                           | 0xFD0C0000    |              |
| SATA AHCI Vendor                                             | 0xFD0C00A0    |              |
| SATA AHCI Port 0 Control                                     | 0xFD0C0100    |              |
| SATA AHCI Port 1 Control                                     | 0xFD0C0180    |              |
| AXI PCIe bridge                                              | 0xFD0E0000    |              |
| PCIe Bridge - Main  Control and Status                       | 0xFD0E0000    |              |
| AXI PCIe ingress {0:7}                                       | 0xFD0E0800    |              |
| PCIe Bridge - Ingress  Addr Translation 0                    | 0xFD0E0800    |              |
| PCIe Bridge - Ingress  Addr Translation 1                    | 0xFD0E0820    |              |
| PCIe Bridge - Ingress  Addr Translation 2                    | 0xFD0E0840    |              |
| PCIe Bridge - Ingress  Addr Translation 3                    | 0xFD0E0860    |              |
| PCIe Bridge - Ingress  Addr Translation 4                    | 0xFD0E0880    |              |
| PCIe Bridge - Ingress  Addr Translation 5                    | 0xFD0E08A0    |              |
| PCIe Bridge - Ingress  Addr Translation 6                    | 0xFD0E08C0    |              |
| PCIe Bridge - Ingress  Addr Translation 7                    | 0xFD0E08E0    |              |
| AXI PCIe egress {0:7}                                        | 0xFD0E0C00    |              |
| PCIe Bridge - Egress  Addr Translation 0                     | 0xFD0E0C00    |              |
| PCIe Bridge - Egress  Addr Translation 1                     | 0xFD0E0C20    |              |
| PCIe Bridge - Egress  Addr Translation 2                     | 0xFD0E0C40    |              |
| PCIe Bridge - Egress  Addr Translation 3                     | 0xFD0E0C60    |              |
| PCIe Bridge - Egress  Addr Translation 4                     | 0xFD0E0C80    |              |
| PCIe Bridge - Egress  Addr Translation 5                     | 0xFD0E0CA0    |              |
| PCIe Bridge - Egress  Addr Translation 6                     | 0xFD0E0CC0    |              |
| PCIe Bridge - Egress  Addr Translation 7                     | 0xFD0E0CE0    |              |
| AXI PCIe DMA {0:7}                                           | 0xFD0F0000    |              |
| PCIe Bridge - DMA  Channel 0                                 | 0xFD0F0000    |              |
| PCIe Bridge - DMA  Channel 1                                 | 0xFD0F0080    |              |
| PCIe Bridge - DMA  Channel 2                                 | 0xFD0F0100    |              |
| PCIe Bridge - DMA  Channel 3                                 | 0xFD0F0180    |              |
| CRF_APB                                                      | 0xFD1A0000    |              |
| Clock and Reset control  registers for FPD.                  | 0xFD1A0000    |              |
| QoS and FIFO  Configuration                                  | 0xFD360000    |              |
| S_AXI_HPC1_FPD QoS and  FIFO Configuration                   | 0xFD370000    |              |
| S_AXI_HP0_FPD QoS and  FIFO Configuration                    | 0xFD380000    |              |
| S_AXI_HP1_FPD QoS and  FIFO Configuration                    | 0xFD390000    |              |
| S_AXI_HP2_FPD QoS and  FIFO Configuration                    | 0xFD3A0000    |              |
| S_AXI_HP3_FPD QoS and  FIFO Configuration                    | 0xFD3B0000    |              |
| SerDes Control and Debug                                     | 0xFD3D0000    |              |
| SerDes Configuration                                         | 0xFD400000    |              |
| PCIe Controller  Attributes                                  | 0xFD480000    |              |
| CCI APM Control and  Configuration                           | 0xFD490000    |              |
| DisplayPort Controller                                       | 0xFD4A0000    |              |
| GPU with two pixel  processors, Graphics Processing Unit     | 0xFD4B0000    |              |
| DisplayPort DMA                                              | 0xFD4C0000    |              |
| FPD_SWDT, system watchdog timer (swdt1)                      | 0xFD4D0000    |              |
| XMPU_Sink (FPD)                                              | 0xFD4F0000    |              |
| FPD_DMA channels {0:7}                                       | 0xFD500000    |              |
| FPD DMA Channel 0                                            | 0xFD500000    |              |
| FPD DMA Channel 1                                            | 0xFD510000    |              |
| FPD DMA Channel 2                                            | 0xFD520000    |              |
| FPD DMA Channel 3                                            | 0xFD530000    |              |
| FPD DMA Channel 4                                            | 0xFD540000    |              |
| FPD DMA Channel 5                                            | 0xFD550000    |              |
| FPD DMA Channel 6                                            | 0xFD560000    |              |
| FPD DMA Channel 7                                            | 0xFD570000    |              |
| APU settings, APU  Configuration                             | 0xFD5C0000    |              |
| FPD XMPU Configuration                                       | 0xFD5D0000    |              |
| AXI Cache Coherent  Interconnect Configuration               | 0xFD5E0000    |              |
| SMMU_REG (interrupts, power, and unit  control)              | 0xFD5F0000    |              |
| FPD System-level Control                                     | 0xFD610000    |              |
| FPD System-level Control  - Secure                           | 0xFD690000    |              |
| CCI_GPV (CCI400, parameters)                                 | 0xFD6E0000    |              |
| FPD_GPV (parameters)                                         | 0xFD700000    |              |
| SMMU_GPV (SMMU500, parameters)                               | 0xFD800000    |              |
| Upper LPD devices                                            | 0xFE000000    | 0xFEFFFFFF   |
| IOU_GPV (parameters)                                         | 0xFE000000    |              |
| LPD_GPV (parameters)                                         | 0xFE100000    |              |
| USB Port 0 XHCI                                              | 0xFE200000    |              |
| USB Port 1 XHCI                                              | 0xFE300000    |              |
| CoreSight top level ROM  in DAP, DAP ROM                     | 0xFE800000    |              |
| Master Timestamp  generator                                  | 0xFE900000    |              |
| Funnel for multiple  trace streams to single ATB             | 0xFE910000    |              |
| Funnel for multiple  trace streams to single ATB             | 0xFE920000    |              |
| Funnel for multiple  trace streams to single ATB             | 0xFE930000    |              |
| Embedded Trace FIFO                                          | 0xFE940000    |              |
| Embedded Trace FIFO                                          | 0xFE950000    |              |
| Replicator forks ATB  data to multiple streams               | 0xFE960000    |              |
| Embedded Trace Router                                        | 0xFE970000    |              |
| Test Port Interface Unit  bridge to on-chip trace data       | 0xFE980000    |              |
| SoC Cross Trigger  Interface with to/from broadcast          | 0xFE990000    |              |
| SoC Cross Trigger  Interface with to/from broadcast          | 0xFE9A0000    |              |
| SoC Cross Trigger  Interface with to/from broadcast          | 0xFE9B0000    |              |
| System Trace  Macrocell                                      | 0xFE9C0000    |              |
| Fabric Trigger Macrocell  interface from PL to ECT           | 0xFE9D0000    |              |
| R5 Integration ROM                                           | 0xFEBE0000    |              |
| Cortex-R5 built-in debug  logic, R5 Debug Logic              | 0xFEBF0000    |              |
| Cortex-R5 built-in debug  logic, R5 Debug Logic              | 0xFEBF2000    |              |
| R5 Cross Trigger  Interface with to/from broadcast           | 0xFEBF8000    |              |
| R5 Cross Trigger  Interface with to/from broadcast           | 0xFEBF9000    |              |
| R5 Embedded Trace  Macrocell                                 | 0xFEBFC000    |              |
| A53 Integration ROM                                          | 0xFEC00000    |              |
| Cortex-A53 built-in  debug logic, A53 Debug Logic            | 0xFEC10000    |              |
| A53 Cross Trigger  Interface with to/from broadcast          | 0xFEC20000    |              |
| A53 Performance Monitor  Unit profiler                       | 0xFEC30000    |              |
| A53 Embedded Trace  Macrocell                                | 0xFEC40000    |              |
| Cortex-A53 built-in  debug logic, A53 Debug Logic            | 0xFED10000    |              |
| A53 Cross Trigger  Interface with to/from broadcast          | 0xFED20000    |              |
| A53 Performance Monitor  Unit profiler                       | 0xFED30000    |              |
| A53 Embedded Trace  Macrocell                                | 0xFED40000    |              |
| Cortex-A53 built-in  debug logic, A53 Debug Logic            | 0xFEE10000    |              |
| A53 Cross Trigger  Interface with to/from broadcast          | 0xFEE20000    |              |
| A53 Performance Monitor  Unit profiler                       | 0xFEE30000    |              |
| A53 Embedded Trace  Macrocell                                | 0xFEE40000    |              |
| Cortex-A53 built-in  debug logic, A53 Debug Logic            | 0xFEF10000    |              |
| A53 Cross Trigger  Interface with to/from broadcast          | 0xFEF20000    |              |
| A53 Performance Monitor  Unit profiler                       | 0xFEF30000    |              |
| A53 Embedded Trace  Macrocell                                | 0xFEF40000    |              |
| Lower LPD devices                                            | 0xFF000000    | 0xFFBFFFFF   |
| UART 0 Controller                                            | 0xFF000000    |              |
| UART 1 Controller                                            | 0xFF010000    |              |
| I2C 0 Controller                                             | 0xFF020000    |              |
| I2C 1 Controller                                             | 0xFF030000    |              |
| SPI 0 Controller                                             | 0xFF040000    |              |
| SPI 1 Controller                                             | 0xFF050000    |              |
| CAN 0 Controller                                             | 0xFF060000    |              |
| CAN 1 Controller                                             | 0xFF070000    |              |
| GPIO Controller                                              | 0xFF0A0000    |              |
| Gigabit Ethernet; GEM 0  Controller                          | 0xFF0B0000    |              |
| Gigabit Ethernet; GEM 1  Controller                          | 0xFF0C0000    |              |
| Gigabit Ethernet; GEM 2  Controller                          | 0xFF0D0000    |              |
| Gigabit Ethernet; GEM 3  Controller                          | 0xFF0E0000    |              |
| Quad SPI Controller                                          | 0xFF0F0000    |              |
| NAND ONFI Control                                            | 0xFF100000    |              |
| Triple Timer Counter 0                                       | 0xFF110000    |              |
| Triple Timer Counter 1                                       | 0xFF120000    |              |
| Triple Timer Counter 2                                       | 0xFF130000    |              |
| Triple Timer Counter 3                                       | 0xFF140000    |              |
| LPD_SWDT, system watchdog timer (swdt0)                      | 0xFF150000    |              |
| LPD System Watchdog  Timer                                   | 0xFF150000    |              |
| SD0                                                          | 0xFF160000    |              |
| SDIO 0 Controller                                            | 0xFF160000    |              |
| SD1                                                          | 0xFF170000    |              |
| SDIO 1 Controller                                            | 0xFF170000    |              |
| IOU_SLCR                                                     | 0xFF180000    |              |
| IOP System-level Control                                     | 0xFF180000    |              |
| IOU_SECURE_SLCR                                              | 0xFF240000    |              |
| IOP System-level Control  - Secure                           | 0xFF240000    |              |
| System Timestamp  Generator                                  | 0xFF250000    |              |
| IOU_SCNTRS                                                   | 0xFF260000    |              |
| System Timestamp  Generator - Secure                         | 0xFF260000    |              |
| Inter-processor interrupts (IPI)                             | 0xFF300000    |              |
| Inter-Processor  Interrupts Control and Status               | 0xFF300000    |              |
| LPD_SLCR                                                     | 0xFF410000    |              |
| Low-power Domain  System-level Control Registers             | 0xFF410000    |              |
| LPD_SLCR_SECURE                                              | 0xFF4B0000    |              |
| Low-power Domain  System-level Control Registers - Secure    | 0xFF4B0000    |              |
| CRL_APB                                                      | 0xFF5E0000    |              |
| Clock and Reset control  registers for LPD.                  | 0xFF5E0000    |              |
| OCM Memory Controller  Configuration                         | 0xFF960000    |              |
| XPPU (Xilinx peripheral protection unit)                     | 0xFF980000    |              |
| XPPU Configuration                                           | 0xFF980000    |              |
| IPI message buffer memory; see Table  13-3.                  | 0xFF990000    |              |
| Realtime Processing  Unit, Real time Processing Unit         | 0xFF9A0000    |              |
| PL_LPD (S_AXI_LPD)                                           | 0xFF9B0000    |              |
| QoS and FIFO  Configuration for seven PL to PS AXI interfaces. | 0xFF9B0000    |              |
| XPPU Sink Controller                                         | 0xFF9C0000    |              |
| USB Core 0 Controller                                        | 0xFF9D0000    |              |
| USB Core 1 Controller                                        | 0xFF9E0000    |              |
| Arm for OCM interconnect                                     | 0xFFA00000    |              |
| OCM Performance Monitor                                      | 0xFFA00000    |              |
| Arm for LPD to FPD interconnect                              | 0xFFA10000    |              |
| LPD Performance Monitor                                      | 0xFFA10000    |              |
| System monitor register sets (AMS)                           | 0xFFA50000    |              |
| PS/PL SysMon Units  Control and Status                       | 0xFFA50000    |              |
| System monitor register sets (PSSYSMON)                      | 0xFFA50800    |              |
| PS System Monitor                                            | 0xFFA50800    |              |
| System monitor register sets (PLSYSMON)                      | 0xFFA50C00    |              |
| PL System Monitor                                            | 0xFFA50C00    |              |
| Real-time clock (RTC)                                        | 0xFFA60000    |              |
| Real Time Clock Control  and Configuration                   | 0xFFA60000    |              |
| OCM_XMPU                                                     | 0xFFA70000    |              |
| OCM Memory Protection  Unit Configuration                    | 0xFFA70000    |              |
| LPD_DMA channels {0:7}                                       | 0xFFA80000    |              |
| LPD DMA Channel 0                                            | 0xFFA80000    |              |
| LPD DMA Channel 1                                            | 0xFFA90000    |              |
| LPD DMA Channel 2                                            | 0xFFAA0000    |              |
| LPD DMA Channel 3                                            | 0xFFAB0000    |              |
| LPD DMA Channel 4                                            | 0xFFAC0000    |              |
| LPD DMA Channel 5                                            | 0xFFAD0000    |              |
| LPD DMA Channel 6                                            | 0xFFAE0000    |              |
| LPD DMA Channel 7                                            | 0xFFAF0000    |              |
| CSU, PMU, TCM, OCM                                           | 0xFFC00000    | 0xFFFFFFFF   |
| CSU_ROM                                                      | 0x00FFC00000  | 0x00FFC1FFFF |
| CSU_RAM                                                      | 0x00FFC40000  | 0x00FFC47FFF |
| CSU module DMA Engine,  CSU DMA Control                      | 0xFFC80000    |              |
| Configuration and security unit (CSU)                        | 0xFFCA0000    |              |
| CSU_SWDT, system watchdog timer  (csu_pmu_wdt).              | 0xFFCB0000    |              |
| eFUSE Control                                                | 0xFFCC0000    |              |
| Battery-backed RAM (BBRAM) control and  data                 | 0xFFCD0000    |              |
| RSA Core Data and  Configuration                             | 0xFFCE0000    |              |
| RSA Data and  Configuration                                  | 0xFFCE002C    |              |
| PMU_ROM                                                      | 0x00FFD00000  | 0x00FFD3FFFF |
| PMU IO Module - Private                                      | 0xFFD40000    |              |
| PMU Local Control -  Private                                 | 0xFFD60000    |              |
| PMU Global Control                                           | 0xFFD80000    |              |
| PMU_RAM                                                      | 0x00FFDC0000  | 0x00FFDDFFFF |
| R5_0_ATCM_SPLIT                                              | 0x00FFE00000  | 0x00FFE0FFFF |
| R5_0_ATCM_LSTEP                                              | 0x00FFE00000  | 0x00FFE1FFFF |
| R5_0_BTCM_SPLIT                                              | 0x00FFE20000  | 0x00FFE2FFFF |
| R5_0_BTCM_LSTEP                                              | 0x00FFE20000  | 0x00FFE3FFFF |
| R5_0_ICACHE                                                  | 0x00FFE40000  | 0x00FFE4FFFF |
| R5_0_DCACHE                                                  | 0x00FFE50000  | 0x00FFE5FFFF |
| R5_1_ATCM_SPLIT                                              | 0x00FFE90000  | 0x00FFE9FFFF |
| R5_1_BTCM_SPLIT                                              | 0x00FFEB0000  | 0x00FFEBFFFF |
| R5_1_ICACHE                                                  | 0x00FFEC0000  | 0x00FFECFFFF |
| R5_1_DCACHE                                                  | 0x00FFED0000  | 0x00FFEDFFFF |
| OCM_RAM                                                      | 0x00FFFC0000  | 0x00FFFFFFFF |
| Reserved                                                     | 0x0100000000  | 0x03FFFFFFFF |
| M_AXI_HPM0_FPD (HPM0)                                        | 0x0400000000  | 0x04FFFFFFFF |
| M_AXI_HPM1_FPD (HPM1)                                        | 0x0500000000  | 0x05FFFFFFFF |
| PCIe High                                                    | 0x0600000000  | 0x07FFFFFFFF |
| DDR High                                                     | 0x0800000000  | 0x0FFFFFFFFF |
| M_AXI_HPM0_FPD (HPM0)                                        | 0x1000000000  | 0x47FFFFFFFF |
| M_AXI_HPM1_FPD (HPM1)                                        | 0x4800000000  | 0x7FFFFFFFFF |
| PCIe High                                                    | 0x8000000000  | 0xBFFFFFFFFF |
| Reserved                                                     | 0xC000000000  | 0xFFFFFFFFFF |

**<u><span>Reference</span></u>**

The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]