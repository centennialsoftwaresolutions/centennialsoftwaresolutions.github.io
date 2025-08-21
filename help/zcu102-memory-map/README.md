# ZCU102 Memory Map

![Xilinx_logo](Xilinx_logo.png)This post's table contains: (1) A memory map of the Zynq UltraScale+ MPSoC, (2) An overlay of the Linux kernel, U-Boot, PMUFW, FSBL, and ATF load addresses, (3) FIT load address examples, (4) Output from the Linux kernel booting on a ZCU102.

| **Device  Name**                                             | **Start Address** | **End Address** | **Size**    | **Size (MB)** |
| :----------------------------------------------------------- | :---------------- | :-------------- | :---------- | :------------ |
| DDR Low                                                      | 0x00000000        | 0x7FFFFFFF      | 2147483648  | 2048          |
| Image (Linux kernel) Load  Address                           | 0x00080000        |                 |             | 0             |
| Linux Load Address                                           | 0x00080000        |                 |             | 0             |
| Linux Entry Point                                            | 0x00080000        |                 |             | 0             |
| Example Device Tree Load Address                             | 0x079a0000        | 0x79ad147       | 53576       | 0.051094055   |
| Example Ramdisk Load  Address                                | 0x079ae000        | 0x07fff968      | 6625641     | 6.318703651   |
| netstart (Linux FIT load address)                            | 0x10000000        |                 |             | 0             |
| u-boot.elf .data:                                            | 0x10080000        | 0x1014c51f      | 836896      | 0.798126221   |
| u-boot.elf Program Start Address                             | 0x10080000        |                 |             | 0             |
| linux-boot.elf .text:                                        | 0x10080000        | 0x10080027      | 40          | 3.8147E-05    |
| linux-boot.elf Program Start Address                         | 0x10080000        |                 |             | 0             |
| NOTICE: BL31: Non secure code at                             | 0x10080000        |                 |             | 0             |
| system.dtb Load Address                                      | 0x1407f000        |                 |             | 0             |
| NOTICE: BL31: Secure code at                                 | 0x60000000        |                 |             | 0             |
| [   0.000000] software IO TLB: mapped [mem 0x6bc00000-0x6fc00000] (64MB) | 0x6bc00000        | 0x6fc00000      | 67108865    | 64.00000095   |
| [  0.000000] cma: Reserved 256 MiB at  0x000000006fc00000    | 0x6fc00000        |                 |             | 0             |
| u-boot.elf run (reloc off 0x6fd6a000) irq sp                 | 0x7dd9ec70        |                 |             | 0             |
| u-boot.elf (reloc off  0x6fd6a000) sp start                  | 0x7dd9ec70        |                 |             | 0             |
| u-boot.elf (reloc off 0x6fd6a000) fdt_blob                   | 0x7dd9ec88        |                 |             | 0             |
| u-boot.elf (reloc off  0x6fd6a000) relocaddr                 | 0x7fdea000        |                 |             | 0             |
| u-boot.elf (reloc off 0x6fd6a000) TLB addr                   | 0x7fee0000        |                 |             | 0             |
| M_AXI_HPM0_LPD (LPD_PL)                                      | 0x80000000        | 0x9FFFFFFF      | 536870912   | 512           |
| VCU Encoder                                                  | 0xA0000000        |                 |             | 0             |
| VCU Decoder                                                  | 0xA0020000        |                 |             | 0             |
| VCU System-Level Control                                     | 0xA0040000        |                 |             | 0             |
| M_AXI_HPM0_FPD (HPM0)  interface(1)                          | 0xA4000000        | 0xAFFFFFFF      | 201326592   | 192           |
| M_AXI_HPM1_FPD (HPM1) interface                              | 0xB0000000        | 0xBFFFFFFF      | 268435456   | 256           |
| Quad-SPI                                                     | 0xC0000000        | 0xDFFFFFFF      | 536870912   | 512           |
| PCIe  Low                                                    | 0xE0000000        | 0xEFFFFFFF      | 268435456   | 256           |
| [   3.737648] nwl-pcie fd0e0000.pcie:   MEM 0xe0000000..0xefffffff -> 0xe0000000 | 0xe0000000        | 0xefffffff      | 268435456   | 256           |
| [  3.764108] pci_bus 0000:00: root bus  resource [mem 0xe0000000-0xefffffff] | 0xe0000000        | 0xefffffff      | 268435456   | 256           |
| Reserved                                                     | 0xF0000000        | 0xF7FFFFFF      | 134217728   | 128           |
| 128  MB reserved                                             | 0xF0000000        | 0xF7FFFFFF      | 134217728   | 128           |
| STM CoreSight                                                | 0xF8000000        | 0xF8FFFFFF      | 16777216    | 16            |
| APU  GIC                                                     | 0xF9000000        | 0xF90FFFFF      | 1048576     | 1             |
| GIC distributor.                                             | 0xF9000000        | 0xF9001FFF      | 8192        | 0.0078125     |
| APU GIC Interrupt Controller;  GICv2                         | 0xF9000000        |                 |             | 0             |
| RPU GIC Interrupt  Controller; GICv1                         | 0xF9000000        |                 |             | 0             |
| GICC interface.                                              | 0xF9002000        | 0xF9002FFF      | 4096        | 0.00390625    |
| [  0.000000] GIC: Adjusting CPU interface  base to 0x00000000f902f000 | 0xf902f000        |                 |             | 0             |
| Reserved                                                     | 0xF9100000        | 0xFCFFFFFF      | 66060288    | 63            |
| 63 MB reserved                                               | 0xF9100000        | 0xFCFFFFFF      | 66060288    | 63            |
| FPD devices                                                  | 0xFD000000        | 0xFDFFFFFF      | 16777216    | 16            |
| DDR_XMPU{0:5}                                                | 0xFD000000        |                 |             | 0             |
| Memory Protection Unit (XMPU) 0  Configuration               | 0xFD000000        |                 |             | 0             |
| Memory Protection  Unit (XMPU) 1 Configuration               | 0xFD010000        |                 |             | 0             |
| Memory Protection Unit (XMPU) 2  Configuration               | 0xFD020000        |                 |             | 0             |
| Memory Protection  Unit (XMPU) 3 Configuration               | 0xFD030000        |                 |             | 0             |
| Memory Protection Unit (XMPU) 4  Configuration               | 0xFD040000        |                 |             | 0             |
| Memory Protection  Unit (XMPU) 5 Configuration               | 0xFD050000        |                 |             | 0             |
| DDR controller                                               | 0xFD070000        |                 |             | 0             |
| DDR Memory  Controller                                       | 0xFD070000        |                 |             | 0             |
| DDR PHY                                                      | 0xFD080000        |                 |             | 0             |
| DDR PHY Register  Description, DDR PHY Control               | 0xFD080000        |                 |             | 0             |
| DDR QoS control                                              | 0xFD090000        |                 |             | 0             |
| DDR QoS Control                                              | 0xFD090000        |                 |             | 0             |
| Arm for DDR                                                  | 0xFD0B0000        |                 |             | 0             |
| AXI DDR  Performance Monitor                                 | 0xFD0B0000        |                 |             | 0             |
| SATA registers (HBA, vendor, port-0/1 control)               | 0xFD0C0000        |                 |             | 0             |
| SATA AHCI HBA  Spec                                          | 0xFD0C0000        |                 |             | 0             |
| [   5.115769] ahci-ceva fd0c0000.ahci: AHCI 0001.0301 32 slots 2 ports 6  Gbps 0x3 impl platform mode | 0xfd0c0000        |                 |             | 0             |
| [  5.142191] ata1: SATA max UDMA/133 mmio  [mem 0xfd0c0000-0xfd0c1fff] port 0x100 irq 45 | 0xfd0c0000        | 0xfd0c1fff      | 8192        | 0.0078125     |
| SATA AHCI Vendor                                             | 0xFD0C00A0        |                 |             | 0             |
| SATA AHCI Port 0  Control                                    | 0xFD0C0100        |                 |             | 0             |
| SATA AHCI Port 1 Control                                     | 0xFD0C0180        |                 |             | 0             |
| AXI PCIe bridge                                              | 0xFD0E0000        |                 |             | 0             |
| PCIe Bridge - Main Control and  Status                       | 0xFD0E0000        |                 |             | 0             |
| AXI PCIe ingress {0:7}                                       | 0xFD0E0800        |                 |             | 0             |
| PCIe Bridge - Ingress Addr  Translation 0                    | 0xFD0E0800        |                 |             | 0             |
| PCIe Bridge -  Ingress Addr Translation 1                    | 0xFD0E0820        |                 |             | 0             |
| PCIe Bridge - Ingress Addr  Translation 2                    | 0xFD0E0840        |                 |             | 0             |
| PCIe Bridge -  Ingress Addr Translation 3                    | 0xFD0E0860        |                 |             | 0             |
| PCIe Bridge - Ingress Addr  Translation 4                    | 0xFD0E0880        |                 |             | 0             |
| PCIe Bridge -  Ingress Addr Translation 5                    | 0xFD0E08A0        |                 |             | 0             |
| PCIe Bridge - Ingress Addr  Translation 6                    | 0xFD0E08C0        |                 |             | 0             |
| PCIe Bridge -  Ingress Addr Translation 7                    | 0xFD0E08E0        |                 |             | 0             |
| AXI PCIe egress {0:7}                                        | 0xFD0E0C00        |                 |             | 0             |
| PCIe Bridge -  Egress Addr Translation 0                     | 0xFD0E0C00        |                 |             | 0             |
| PCIe Bridge - Egress Addr  Translation 1                     | 0xFD0E0C20        |                 |             | 0             |
| PCIe Bridge -  Egress Addr Translation 2                     | 0xFD0E0C40        |                 |             | 0             |
| PCIe Bridge - Egress Addr  Translation 3                     | 0xFD0E0C60        |                 |             | 0             |
| PCIe Bridge -  Egress Addr Translation 4                     | 0xFD0E0C80        |                 |             | 0             |
| PCIe Bridge - Egress Addr  Translation 5                     | 0xFD0E0CA0        |                 |             | 0             |
| PCIe Bridge -  Egress Addr Translation 6                     | 0xFD0E0CC0        |                 |             | 0             |
| PCIe Bridge - Egress Addr  Translation 7                     | 0xFD0E0CE0        |                 |             | 0             |
| AXI PCIe DMA {0:7}                                           | 0xFD0F0000        |                 |             | 0             |
| PCIe Bridge - DMA Channel 0                                  | 0xFD0F0000        |                 |             | 0             |
| PCIe Bridge - DMA  Channel 1                                 | 0xFD0F0080        |                 |             | 0             |
| PCIe Bridge - DMA Channel 2                                  | 0xFD0F0100        |                 |             | 0             |
| PCIe Bridge - DMA  Channel 3                                 | 0xFD0F0180        |                 |             | 0             |
| CRF_APB                                                      | 0xFD1A0000        |                 |             | 0             |
| Clock and Reset  control registers for FPD.                  | 0xFD1A0000        |                 |             | 0             |
| QoS and FIFO Configuration                                   | 0xFD360000        |                 |             | 0             |
| S_AXI_HPC1_FPD  QoS and FIFO Configuration                   | 0xFD370000        |                 |             | 0             |
| S_AXI_HP0_FPD QoS and FIFO  Configuration                    | 0xFD380000        |                 |             | 0             |
| S_AXI_HP1_FPD QoS  and FIFO Configuration                    | 0xFD390000        |                 |             | 0             |
| S_AXI_HP2_FPD QoS and FIFO  Configuration                    | 0xFD3A0000        |                 |             | 0             |
| S_AXI_HP3_FPD QoS  and FIFO Configuration                    | 0xFD3B0000        |                 |             | 0             |
| SerDes Control and Debug                                     | 0xFD3D0000        |                 |             | 0             |
| SerDes  Configuration                                        | 0xFD400000        |                 |             | 0             |
| [   5.265331] xilinx-psgtr fd400000.zynqmp_phy: Lane:2 type:0 protocol:3  pll_locked:yes | 0xfd400000        |                 |             | 0             |
| PCIe Controller  Attributes                                  | 0xFD480000        |                 |             | 0             |
| CCI APM Control and Configuration                            | 0xFD490000        |                 |             | 0             |
| DisplayPort  Controller                                      | 0xFD4A0000        |                 |             | 0             |
| GPU with two pixel processors,  Graphics Processing Unit     | 0xFD4B0000        |                 |             | 0             |
| DisplayPort DMA                                              | 0xFD4C0000        |                 |             | 0             |
| FPD_SWDT, system watchdog timer (swdt1)                      | 0xFD4D0000        |                 |             | 0             |
| XMPU_Sink (FPD)                                              | 0xFD4F0000        |                 |             | 0             |
| FPD_DMA channels {0:7}                                       | 0xFD500000        |                 |             | 0             |
| FPD DMA Channel 0                                            | 0xFD500000        |                 |             | 0             |
| FPD DMA Channel 1                                            | 0xFD510000        |                 |             | 0             |
| FPD DMA Channel 2                                            | 0xFD520000        |                 |             | 0             |
| FPD DMA Channel 3                                            | 0xFD530000        |                 |             | 0             |
| FPD DMA Channel 4                                            | 0xFD540000        |                 |             | 0             |
| FPD DMA Channel 5                                            | 0xFD550000        |                 |             | 0             |
| FPD DMA Channel 6                                            | 0xFD560000        |                 |             | 0             |
| FPD DMA Channel 7                                            | 0xFD570000        |                 |             | 0             |
| APU                                                          | 0xFD5C0000        |                 |             | 0             |
| APU settings, APU Configuration                              | 0xFD5C0000        |                 |             | 0             |
| FPD_XMPU                                                     | 0xFD5D0000        |                 |             | 0             |
| FPD XMPU Configuration                                       | 0xFD5D0000        |                 |             | 0             |
| CCI_REG register set  wrapper: debug enables                 | 0xFD5E0000        |                 |             | 0             |
| AXI Cache Coherent Interconnect  Configuration               | 0xFD5E0000        |                 |             | 0             |
| SMMU_REG (interrupts,  power, and unit control)              | 0xFD5F0000        |                 |             | 0             |
| SMMU Configuration and Event  Control                        | 0xFD5F0000        |                 |             | 0             |
| FPD System-level  Control                                    | 0xFD610000        |                 |             | 0             |
| FPD System-level Control - Secure                            | 0xFD690000        |                 |             | 0             |
| CCI_GPV                                                      | 0xFD6E0000        |                 |             | 0             |
| CCI_GPV (CCI400, parameters)                                 | 0xFD6E0000        |                 |             | 0             |
| FPD_GPV (parameters)                                         | 0xFD700000        |                 |             | 0             |
| SMMU_GPV (SMMU500, parameters)                               | 0xFD800000        |                 |             | 0             |
| SMMU-500 GPV                                                 | 0xFD800000        |                 |             | 0             |
| Upper LPD devices                                            | 0xFE000000        | 0xFEFFFFFF      | 16777216    | 16            |
| IOU_GPV (parameters)                                         | 0xFE000000        |                 |             | 0             |
| GPV                                                          | 0xFE000000        |                 |             | 0             |
| LPD_GPV (parameters)                                         | 0xFE100000        |                 |             | 0             |
| GPV                                                          | 0xFE100000        |                 |             | 0             |
| USB Port 0 XHCI                                              | 0xFE200000        |                 |             | 0             |
| [   5.296271] xhci-hcd xhci-hcd.0.auto: irq 54, io mem 0xfe200000 | 0xfe200000        |                 |             | 0             |
| USB Port 1 XHCI                                              | 0xFE300000        |                 |             | 0             |
| CoreSight top level ROM in DAP,  DAP ROM                     | 0xFE800000        |                 |             | 0             |
| Master Timestamp  generator                                  | 0xFE900000        |                 |             | 0             |
| Funnel for multiple trace streams  to single ATB             | 0xFE910000        |                 |             | 0             |
| Funnel for  multiple trace streams to single ATB             | 0xFE920000        |                 |             | 0             |
| Funnel for multiple trace streams  to single ATB             | 0xFE930000        |                 |             | 0             |
| Embedded Trace  FIFO                                         | 0xFE940000        |                 |             | 0             |
| Embedded Trace FIFO                                          | 0xFE950000        |                 |             | 0             |
| Replicator forks  ATB data to multiple streams               | 0xFE960000        |                 |             | 0             |
| Embedded Trace Router                                        | 0xFE970000        |                 |             | 0             |
| Test Port  Interface Unit bridge to on-chip trace data       | 0xFE980000        |                 |             | 0             |
| SoC Cross Trigger Interface with  to/from broadcast          | 0xFE990000        |                 |             | 0             |
| SoC Cross Trigger  Interface with to/from broadcast          | 0xFE9A0000        |                 |             | 0             |
| SoC Cross Trigger Interface with  to/from broadcast          | 0xFE9B0000        |                 |             | 0             |
| System Trace  Macrocell with multiple SW and HW stimulus ports for MIPI STPv2 traces | 0xFE9C0000        |                 |             | 0             |
| Fabric Trigger Macrocell interface  from PL to ECT           | 0xFE9D0000        |                 |             | 0             |
| R5 Integration  ROM                                          | 0xFEBE0000        |                 |             | 0             |
| Cortex-R5 built-in debug logic, R5  Debug Logic              | 0xFEBF0000        |                 |             | 0             |
| Cortex-R5  built-in debug logic, R5 Debug Logic              | 0xFEBF2000        |                 |             | 0             |
| R5 Cross Trigger Interface with  to/from broadcast           | 0xFEBF8000        |                 |             | 0             |
| R5 Cross Trigger  Interface with to/from broadcast           | 0xFEBF9000        |                 |             | 0             |
| R5 Embedded Trace Macrocell                                  | 0xFEBFC000        |                 |             | 0             |
| A53 Integration  ROM                                         | 0xFEC00000        |                 |             | 0             |
| Cortex-A53 built-in debug logic,  A53 Debug Logic            | 0xFEC10000        |                 |             | 0             |
| A53 Cross Trigger  Interface with to/from broadcast          | 0xFEC20000        |                 |             | 0             |
| A53 Performance Monitor Unit  profiler                       | 0xFEC30000        |                 |             | 0             |
| A53 Embedded  Trace Macrocell                                | 0xFEC40000        |                 |             | 0             |
| Cortex-A53 built-in debug logic,  A53 Debug Logic            | 0xFED10000        |                 |             | 0             |
| A53 Cross Trigger  Interface with to/from broadcast          | 0xFED20000        |                 |             | 0             |
| A53 Performance Monitor Unit  profiler                       | 0xFED30000        |                 |             | 0             |
| A53 Embedded  Trace Macrocell                                | 0xFED40000        |                 |             | 0             |
| Cortex-A53 built-in debug logic,  A53 Debug Logic            | 0xFEE10000        |                 |             | 0             |
| A53 Cross Trigger  Interface with to/from broadcast          | 0xFEE20000        |                 |             | 0             |
| A53 Performance Monitor Unit  profiler                       | 0xFEE30000        |                 |             | 0             |
| A53 Embedded  Trace Macrocell                                | 0xFEE40000        |                 |             | 0             |
| Cortex-A53 built-in debug logic,  A53 Debug Logic            | 0xFEF10000        |                 |             | 0             |
| A53 Cross Trigger  Interface with to/from broadcast          | 0xFEF20000        |                 |             | 0             |
| A53 Performance Monitor Unit  profiler                       | 0xFEF30000        |                 |             | 0             |
| A53 Embedded  Trace Macrocell                                | 0xFEF40000        |                 |             | 0             |
| Lower LPD devices                                            | 0xFF000000        | 0xFFBFFFFF      | 12582912    | 12            |
| UART 0 Controller                                            | 0xFF000000        |                 |             | 0             |
| [  0.000000] earlycon: cdns0 at MMIO  0x00000000ff000000 (options '115200n8') | 0xff000000        |                 |             | 0             |
| \FD\FDr\FD\AA\FD\FD\FDconsole [ttyPS0]  enabledttyPS0 at MMIO 0xff000000 (irq = 47, base_baud = 6249375) is a xuartps | 0xff000000        |                 |             | 0             |
| UART 1 Controller                                            | 0xFF010000        |                 |             | 0             |
| [   3.706910] ff010000.serial: ttyPS1 at MMIO 0xff010000 (irq = 48,  base_baud = 6249375) is a xuartps | 0xff010000        |                 |             | 0             |
| I2C 0 Controller                                             | 0xFF020000        |                 |             | 0             |
| I2C 1 Controller                                             | 0xFF030000        |                 |             | 0             |
| SPI 0 Controller                                             | 0xFF040000        |                 |             | 0             |
| SPI 1 Controller                                             | 0xFF050000        |                 |             | 0             |
| CAN 0 Controller                                             | 0xFF060000        |                 |             | 0             |
| CAN 1 Controller                                             | 0xFF070000        |                 |             | 0             |
| GPIO Controller                                              | 0xFF0A0000        |                 |             | 0             |
| Gigabit Ethernet; GEM  0 Controller                          | 0xFF0B0000        |                 |             | 0             |
| Gigabit Ethernet; GEM 1 Controller                           | 0xFF0C0000        |                 |             | 0             |
| Gigabit Ethernet; GEM  2 Controller                          | 0xFF0D0000        |                 |             | 0             |
| Gigabit Ethernet; GEM 3 Controller                           | 0xFF0E0000        |                 |             | 0             |
| [   5.221947] macb ff0e0000.ethernet eth0: Cadence GEM rev 0x50070106 at  0xff0e0000 irq 30 (00:0a:35:00:22:01) | 0xff0e0000        |                 |             | 0             |
| Quad SPI Controller                                          | 0xFF0F0000        |                 |             | 0             |
| NAND ONFI Control                                            | 0xFF100000        |                 |             | 0             |
| Triple Timer Counter 0                                       | 0xFF110000        |                 |             | 0             |
| Triple Timer  Counter 1                                      | 0xFF120000        |                 |             | 0             |
| Triple Timer Counter 2                                       | 0xFF130000        |                 |             | 0             |
| Triple Timer  Counter 3                                      | 0xFF140000        |                 |             | 0             |
| LPD_SWDT, system watchdog timer (swdt0)                      | 0xFF150000        |                 |             | 0             |
| LPD System  Watchdog Timer                                   | 0xFF150000        |                 |             | 0             |
| SD0                                                          | 0xFF160000        |                 |             | 0             |
| SDIO 0 Controller                                            | 0xFF160000        |                 |             | 0             |
| SD1                                                          | 0xFF170000        |                 |             | 0             |
| SDIO 1 Controller                                            | 0xFF170000        |                 |             | 0             |
| IOU_SLCR                                                     | 0xFF180000        |                 |             | 0             |
| IOP System-level  Control                                    | 0xFF180000        |                 |             | 0             |
| IOU_SECURE_SLCR                                              | 0xFF240000        |                 |             | 0             |
| IOP System-level  Control - Secure                           | 0xFF240000        |                 |             | 0             |
| System Timestamp Generator                                   | 0xFF250000        |                 |             | 0             |
| IOU_SCNTRS                                                   | 0xFF260000        |                 |             | 0             |
| System Timestamp Generator -  Secure                         | 0xFF260000        |                 |             | 0             |
| Inter-processor interrupts  (IPI)                            | 0xFF300000        |                 |             | 0             |
| Inter-Processor Interrupts Control  and Status               | 0xFF300000        |                 |             | 0             |
| LPD_SLCR                                                     | 0xFF410000        |                 |             | 0             |
| Low-power Domain System-level  Control Registers             | 0xFF410000        |                 |             | 0             |
| LPD_SLCR_SECURE                                              | 0xFF4B0000        |                 |             | 0             |
| Low-power Domain System-level  Control Registers - Secure    | 0xFF4B0000        |                 |             | 0             |
| CRL_APB                                                      | 0xFF5E0000        |                 |             | 0             |
| Clock and Reset control registers  for LPD.                  | 0xFF5E0000        |                 |             | 0             |
| OCM Memory  Controller Configuration                         | 0xFF960000        |                 |             | 0             |
| XPPU (Xilinx peripheral protection unit)                     | 0xFF980000        |                 |             | 0             |
| XPPU  Configuration                                          | 0xFF980000        |                 |             | 0             |
| IPI message buffer memory; see Table 13-3.                   | 0xFF990000        |                 |             | 0             |
| Realtime  Processing Unit, Real time Processing Unit         | 0xFF9A0000        |                 |             | 0             |
| PL_LPD (S_AXI_LPD)                                           | 0xFF9B0000        |                 |             | 0             |
| QoS and FIFO  Configuration for seven PL to PS AXI interfaces. | 0xFF9B0000        |                 |             | 0             |
| XPPU Sink Controller                                         | 0xFF9C0000        |                 |             | 0             |
| USB Core 0  Controller                                       | 0xFF9D0000        |                 |             | 0             |
| USB Core 1 Controller                                        | 0xFF9E0000        |                 |             | 0             |
| Arm for OCM interconnect                                     | 0xFFA00000        |                 |             | 0             |
| OCM Performance Monitor                                      | 0xFFA00000        |                 |             | 0             |
| Arm for LPD to FPD  interconnect                             | 0xFFA10000        |                 |             | 0             |
| LPD Performance Monitor                                      | 0xFFA10000        |                 |             | 0             |
| System monitor register  sets (AMS)                          | 0xFFA50000        |                 |             | 0             |
| PS/PL SysMon Units Control and  Status                       | 0xFFA50000        |                 |             | 0             |
| System monitor register  sets (PSSYSMON)                     | 0xFFA50800        |                 |             | 0             |
| PS System Monitor                                            | 0xFFA50800        |                 |             | 0             |
| System monitor register  sets (PLSYSMON)                     | 0xFFA50C00        |                 |             | 0             |
| PL System Monitor                                            | 0xFFA50C00        |                 |             | 0             |
| Real-time clock (RTC)                                        | 0xFFA60000        |                 |             | 0             |
| Real Time Clock Control and  Configuration                   | 0xFFA60000        |                 |             | 0             |
| OCM_XMPU                                                     | 0xFFA70000        |                 |             | 0             |
| OCM Memory Protection Unit  Configuration                    | 0xFFA70000        |                 |             | 0             |
| LPD_DMA channels {0:7}                                       | 0xFFA80000        |                 |             | 0             |
| LPD DMA Channel 0                                            | 0xFFA80000        |                 |             | 0             |
| LPD DMA Channel 1                                            | 0xFFA90000        |                 |             | 0             |
| LPD DMA Channel 2                                            | 0xFFAA0000        |                 |             | 0             |
| LPD DMA Channel 3                                            | 0xFFAB0000        |                 |             | 0             |
| LPD DMA Channel 4                                            | 0xFFAC0000        |                 |             | 0             |
| LPD DMA Channel 5                                            | 0xFFAD0000        |                 |             | 0             |
| LPD DMA Channel 6                                            | 0xFFAE0000        |                 |             | 0             |
| LPD DMA Channel 7                                            | 0xFFAF0000        |                 |             | 0             |
| CSU, PMU, TCM, OCM                                           | 0xFFC00000        | 0xFFFFFFFF      | 4194304     | 4             |
| CSU_ROM                                                      | 0x00FFC00000      | 0x00FFC1FFFF    | 131072      | 0.125         |
| CSU_RAM                                                      | 0x00FFC40000      | 0x00FFC47FFF    | 32768       | 0.03125       |
| CSU module DMA  Engine, CSU DMA Control                      | 0xFFC80000        |                 |             | 0             |
| Configuration and security unit (CSU)                        | 0xFFCA0000        |                 |             | 0             |
| CSU_SWDT, system watchdog  timer (csu_pmu_wdt).              | 0xFFCB0000        |                 |             | 0             |
| eFUSE Control                                                | 0xFFCC0000        |                 |             | 0             |
| Battery-backed RAM (BBRAM)  control and data                 | 0xFFCD0000        |                 |             | 0             |
| RSA Core Data and Configuration                              | 0xFFCE0000        |                 |             | 0             |
| RSA Data and  Configuration                                  | 0xFFCE002C        |                 |             | 0             |
| PMU_ROM                                                      | 0x00FFD00000      | 0x00FFD3FFFF    | 262144      | 0.25          |
| PMU IO Module -  Private                                     | 0xFFD40000        |                 |             | 0             |
| PMU Local Control - Private                                  | 0xFFD60000        |                 |             | 0             |
| PMU Global  Control                                          | 0xFFD80000        |                 |             | 0             |
| PMU_RAM                                                      | 0x00FFDC0000      | 0x00FFDDFFFF    | 131072      | 0.125         |
| pmufw.elf .vectors.reset:                                    | 0xffdc0000        | 0xffdc0007      | 8           | 7.62939E-06   |
| pmufw.elf .vectors.sw_exception:                             | 0xffdc0008        | 0xffdc000f      | 8           | 7.62939E-06   |
| pmufw.elf  .vectors.interrupt:                               | 0xffdc0010        | 0xffdc0017      | 8           | 7.62939E-06   |
| pmufw.elf .vectors.hw_exception:                             | 0xffdc0020        | 0xffdc0027      | 8           | 7.62939E-06   |
| pmufw.elf .text:                                             | 0xffdc0050        | 0xffdd0dc7      | 68984       | 0.065788269   |
| pmufw.elf Program Start Address                              | 0xffdcffe0        |                 |             | 0             |
| pmufw.elf .rodata:                                           | 0xffdd0dc8        | 0xffdd2edf      | 8472        | 0.008079529   |
| pmufw.elf .data:                                             | 0xffdd2ee0        | 0xffdd71d7      | 17144       | 0.016349792   |
| pmufw.elf .sdata2:                                           | 0xffdd71d8        | 0xffdd71d7      | 0           | 0             |
| pmufw.elf .sdata:                                            | 0xffdd71d8        | 0xffdd71d7      | 0           | 0             |
| pmufw.elf .sbss:                                             | 0xffdd71d8        | 0xffdd71d7      | 0           | 0             |
| pmufw.elf .bss:                                              | 0xffdd71e0        | 0xffddb20b      | 16428       | 0.015666962   |
| pmufw.elf .srdata:                                           | 0xffddb20c        | 0xffddbb2f      | 2340        | 0.002231598   |
| pmufw.elf .stack:                                            | 0xffddbb30        | 0xffddcb2f      | 4096        | 0.00390625    |
| pmufw.elf  .xpbr_serv_ext_tbl:                               | 0xffddf6e0        | 0xffddfadf      | 1024        | 0.000976563   |
| R5_0_ATCM_SPLIT                                              | 0x00FFE00000      | 0x00FFE0FFFF    | 65536       | 0.0625        |
| R5_0_ATCM_LSTEP                                              | 0x00FFE00000      | 0x00FFE1FFFF    | 131072      | 0.125         |
| R5_0_BTCM_SPLIT                                              | 0x00FFE20000      | 0x00FFE2FFFF    | 65536       | 0.0625        |
| R5_0_BTCM_LSTEP                                              | 0x00FFE20000      | 0x00FFE3FFFF    | 131072      | 0.125         |
| R5_0_ICACHE                                                  | 0x00FFE40000      | 0x00FFE4FFFF    | 65536       | 0.0625        |
| R5_0_DCACHE                                                  | 0x00FFE50000      | 0x00FFE5FFFF    | 65536       | 0.0625        |
| R5_1_ATCM_SPLIT                                              | 0x00FFE90000      | 0x00FFE9FFFF    | 65536       | 0.0625        |
| R5_1_BTCM_SPLIT                                              | 0x00FFEB0000      | 0x00FFEBFFFF    | 65536       | 0.0625        |
| R5_1_ICACHE                                                  | 0x00FFEC0000      | 0x00FFECFFFF    | 65536       | 0.0625        |
| R5_1_DCACHE                                                  | 0x00FFED0000      | 0x00FFEDFFFF    | 65536       | 0.0625        |
| OCM_RAM                                                      | 0x00FFFC0000      | 0x00FFFFFFFF    | 262144      | 0.25          |
| zynqmp_fsbl.elf .text:                                       | 0xfffc0000        | 0xfffd410b      | 82188       | 0.078380585   |
| zynqmp_fsbl.elf Program Start Address                        | 0xfffc0000        |                 |             | 0             |
| zynqmp_fsbl.elf .init:                                       | 0xfffd4140        | 0xfffd4173      | 52          | 4.95911E-05   |
| zynqmp_fsbl.elf .fini:                                       | 0xfffd4180        | 0xfffd41b3      | 52          | 4.95911E-05   |
| zynqmp_fsbl.elf  .note.gnu.build-id:                         | 0xfffd41b4        | 0xfffd41d7      | 36          | 3.43323E-05   |
| zynqmp_fsbl.elf .rodata:                                     | 0xfffd4200        | 0xfffd474f      | 1360        | 0.001296997   |
| zynqmp_fsbl.elf  .sys_cfg_data:                              | 0xfffd4780        | 0xfffd4f67      | 2024        | 0.001930237   |
| zynqmp_fsbl.elf .mmu_tbl0:                                   | 0xfffd5000        | 0xfffd500f      | 16          | 1.52588E-05   |
| zynqmp_fsbl.elf .mmu_tbl1:                                   | 0xfffd6000        | 0xfffd7fff      | 8192        | 0.0078125     |
| zynqmp_fsbl.elf .mmu_tbl2:                                   | 0xfffd8000        | 0xfffdbfff      | 16384       | 0.015625      |
| zynqmp_fsbl.elf .data:                                       | 0xfffdc000        | 0xfffdd3b7      | 5048        | 0.004814148   |
| zynqmp_fsbl.elf .sbss:                                       | 0xfffdd3b8        | 0xfffdd3bf      | 8           | 7.62939E-06   |
| zynqmp_fsbl.elf .bss:                                        | 0xfffdd3c0        | 0xfffdf5bf      | 8704        | 0.008300781   |
| zynqmp_fsbl.elf .heap:                                       | 0xfffdf5c0        | 0xfffdf9bf      | 1024        | 0.000976563   |
| zynqmp_fsbl.elf .stack:                                      | 0xfffdf9c0        | 0xfffe19bf      | 8192        | 0.0078125     |
| zynqmp_fsbl.elf .dup_data:                                   | 0xfffe19c0        | 0xfffe2d77      | 5048        | 0.004814148   |
| zynqmp_fsbl.elf  .handoff_params:                            | 0xfffe9e00        | 0xfffe9e87      | 136         | 0.0001297     |
| bl31.elf .text:                                              | 0xfffea000        | 0xffff1fff      | 32768       | 0.03125       |
| bl31.elf Program Start  Address                              | 0xfffea000        |                 |             | 0             |
| NOTICE: ATF running on XCZU9EG/silicon v3/RTL5.1 at          | 0xfffea000        |                 |             | 0             |
| zynqmp_fsbl.elf  .bitstream_buffer:                          | 0xffff0040        | 0xfffffc3f      | 64512       | 0.061523438   |
| bl31.elf .rodata:                                            | 0xffff2000        | 0xffff2fff      | 4096        | 0.00390625    |
| bl31.elf .data:                                              | 0xffff3000        | 0xffff6777      | 14200       | 0.013542175   |
| bl31.elf stacks:                                             | 0xffff6780        | 0xffff787f      | 4352        | 0.004150391   |
| bl31.elf .bss:                                               | 0xffff7880        | 0xffff8613      | 3476        | 0.003314972   |
| bl31.elf xlat_table:                                         | 0xffff9000        | 0xffffdfff      | 20480       | 0.01953125    |
| bl31.elf coherent_ram:                                       | 0xffffe000        | 0xffffefff      | 4096        | 0.00390625    |
| Reserved                                                     | 0x0100000000      | 0x03FFFFFFFF    | 12884901888 | 12288         |
| M_AXI_HPM0_FPD (HPM0)                                        | 0x0400000000      | 0x04FFFFFFFF    | 4294967296  | 4096          |
| M_AXI_HPM1_FPD (HPM1)                                        | 0x0500000000      | 0x05FFFFFFFF    | 4294967296  | 4096          |
| PCIe High                                                    | 0x0600000000      | 0x07FFFFFFFF    | 8589934592  | 8192          |
| [   3.744867] nwl-pcie fd0e0000.pcie:   MEM 0x600000000..0x7ffffffff -> 0x600000000 | 0x600000000       | 0x7ffffffff     | 8589934592  | 8192          |
| [  3.770977] pci_bus 0000:00: root bus  resource [mem 0x600000000-0x7ffffffff pref] | 0x600000000       | 0x7ffffffff     | 8589934592  | 8192          |
| DDR High                                                     | 0x0800000000      | 0x0FFFFFFFFF    | 34359738368 | 32768         |
| M_AXI_HPM0_FPD (HPM0)                                        | 0x1000000000      | 0x47FFFFFFFF    | 2.40518E+11 | 229376        |
| M_AXI_HPM1_FPD (HPM1)                                        | 0x4800000000      | 0x7FFFFFFFFF    | 2.40518E+11 | 229376        |
| PCIe High                                                    | 0x8000000000      | 0xBFFFFFFFFF    | 2.74878E+11 | 262144        |
| Reserved                                                     | 0xC000000000      | 0xFFFFFFFFFF    | 2.74878E+11 | 262144        |

**<u><span>References</span></u>**

-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]