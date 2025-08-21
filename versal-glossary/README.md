# Versal Glossary

Details on abbreviations, acronyms, and other terms.

In this post, **_<u><span>*O</span></u>_** means that a component is optional and is not present in every Versal model. See AM011 section "Integrated Peripheral Options" for details.

For high-level diagrams, refer to:

-   AM011 figure "SoC Block Diagram" [<u><span>(link)</span></u>](https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/SoC-Block-Diagram)
    
-   AM011 section "Hardware Architecture" [<u><span>(link)</span></u>](https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/Hardware-Architecture)
    

## Miscellaneous

-   **ACAP**
    
    -   Adaptive Compute Acceleration Platform – how AMD marketing describes/classifies the Versal product
        

## Major system components

-   **Intelligent Engines**
    
    -   Name for the DSPs and AIEs
        
        -   **AIE**
            
        -   AI Engine – usually refers to the default DSP-optimized version of the AI Engine
            
            -   **AIE-ML**
            
        -   AI Engine, ML-optimized version (for machine learning training & inference)
            
            -   **DSP**
            
        -   Dedicated DSP (digital signal processor) accelerator engines, located inside the PL.
    
-   **Adaptive Engines / Adaptable Engines**
    
    -   Name for the FPGA and the BlockRAM/UltraRAM that it contains. Does not include the DSP blocks.
        
        -   **PL**
        
    -   Programmable Logic (the FPGA & its RAM). The DSP engines are located within the PL, and the AIEs connect to the PL. “PL” is also the name of a power domain, which includes the PL (FPGA/DSP), AIEs, and some peripherals.
    
-   **Scalar Engines**
    
    -   Name for the ARM cores (APU + RPU)
        
    -   **APU**
        
        -   Application Processing Unit. On Versal, this consists of the two ARM Cortex-A72 cores.
        
    -   **RPU**
        
        -   Realtime Processing Unit. On Versal, this consists of the two ARM Cortex-R5F cores.
        
    -   **OCM**
        
        -   256kb of ECC On-Chip Memory. This is connected directly to the RPU and indirectly to the APU.
    
-   **CIPS**
    
    -   Control, Interfaces, and Processing System. This includes the Scalar Engines (APU/RPU), PMC, and CPM. Formerly called the PS on Zynq-7000 and UltraScale+.
        
        -   **CCI**
            
        -   Cache-Coherent Interconnect for APU L2 cache. See AM011 chapter “Cache Coherent Interconnect.”
            
            -   **CPM, CCIX, CXL**
            
        -   \[Cache\] Coherent Module with PCIe. There are two versions, CPM4 and CPM5. This is an optional feature, not all Versal models have one. The CPM4 variant has a CCIX interconnect, see AM016 for details. The CPM5 variant has a CXL interconnect which can provide cache coherency with external PCIe devices. See AM011 page 26 (in v1.5).
            
            -   **PMC**
        
    -   Platform Management Controller. This includes the RCU, PPU, and to an extent also the PSM – a set of processors that control boot and system monitoring & management. The PMC also includs 128kb of **PMC RAM** which is used by the PLM, IO peripherals, debug interfaces, registers, the system monitor, RTC, configuration interfaces, and security modules. The PMC also has its own power domain, with one exception: though the PSM is logically part of the PMC, physically the PSM is located in the LPD. See AM011 "Platform Managment Controller", which includes a block diagram of the PMC.
        
    -   **RCU**
        
        -   ROM Code Unit. This block contains the RCU ROM (equivalent of BootROM on the Zynq-7000 and UltraScale+), a triple-redundant MicroBlaze processor (which executes the RCU ROM), and the PUF.
        
    -   **PPU**
        
        -   Platform Processing Unit. This includes the PPU itself (a triple redundant MicroBlaze processor) and some dedicated PPU RAM. The PPU executes the PLM. See AM011 chapter "Platform Processing Unit" (chapter 31 / page 309 in v1.5).
        
    -   **PSM**
        
        -   Processing System Management controller. This executes the PSMFW. This is logically part of the PMC but is in the LPD. The PSM does power management for the PS. See AM011 chapter "Processing System Manager" (chapter 32 / page 316 in v1.5).
    
-   **NoC**
    
    -   Network on Chip. This connects the PS, PL, AIEs, DDR controller, CPM, NPI, and HBM.
        

## Other system components

**Networking**

-   **MRMAC** **_<u><span>*O</span></u>_**
    
    -   100G Multirate Ethernet MAC
    
-   **DCMAC** **_<u><span>*O</span></u>_**
    
    -   600G Channelized Multirate Ethernet MAC
    
-   **ILKN** **_<u><span>*O</span></u>_**
    
    -   600G Interlaken Core
        

**Debug**

-   **ARM DAP**
    
    -   ARM Debug Access Port. Used to perform debug operations on the APU and RPU.
    
-   **TAP**
    
    -   \[JTAG\] Test Access Port
    
-   **DPC**
    
    -   Debug Packet Controller. See AM011 section "Debug Packet Controller."
    
-   **SBI**
    
    -   Supervised Boot Interface. See AM011 chapter "SBI for JTAG and SelectMAP."
        

**Security & crypto**

-   **HSC** **_<u><span>*O</span></u>_**
    
    -   High-Speed Crypto Engine
    
-   **eFUSE**
    
    -   One-time-programmable fuses in the chip. eFuses can be blown to enable secure boot and other security options. They can also store secure boot keys.
    
-   **BBRAM**
    
    -   Battery-backed RAM. This is a small (288 bit) RAM unit inside the Versal, but requires an external battery to be connected to preserve data when the chip is powered off. Can store things like encryption & authentication keys. See AM011 chapter "Battery-Backed RAM."
    
-   **PUF**
    
    -   Physically Unclonable Function. This is a security unit in the PMC. See AM011 chapter "PMC Security Units."
    
-   **KEK**
    
    -   Key Encryption Key - generated by the PUF. Used by certain secure boot methods.
    
-   **TRNG**
    
    -   True Random Number Generator. This is a security unit in the PMC. See AM011 chapter "PMC Security Units."
    
-   **SSS**
    
    -   Secure Stream Switch. This connects the two PMC DMAs, AES-GCM, SHA3-384, and SBI. See AM011 chapter "Secure Stream Switch."
    
-   **XMPU**
    
    -   Xilinx Memory Protection Unit. There are multiple on the Versal. These control access to memories on the system. See AM011 section "Xilinx Memory Protection Unit."
    
-   **XPPU**
    
    -   Xilinx Peripheral Protection Unit. There are multiple on the Versal. These can block access to various configuration registers. See AM011 chapter "Xilinx Peripheral Protection Unit."
        

**Configuration**

-   **CFU, CFI, CRAM**
    
    -   Configuration Frame Unit and Configuration Frame Interface, used to configure the PL. The CFU is a bridge to transfer data between the PMC main switch and into the CFI & PL Configuration RAM (CRAM).
    
-   **NPI**
    
    -   NoC Programming Interface - used to configure the NoC, DDR controller, AI Engines, transceivers, and some other things in the PL and SPD.
        

**Memory**

-   **XRAM** **_<u><span>*O</span></u>_**
    
    -   Accelerator RAM. See AM011 section "Accelerator RAM."
    
-   **TCM**
    
    -   Tightly-coupled Memory. See AM011 section "Tightly-coupled Memories"
    
-   **SMMU**
    
    -   System Memory Management Unit. See AM011 section "System Memory Management Unit."
        

**Miscellaneous**

-   **DNA**
    
    -   A 128-bit device identifier. No two Versal chips have the same DNA value. See AM011 section "DNA Introduction."
    
-   **VDU** **_<u><span>*O</span></u>_**
    
    -   Video Decoder Unit
        

## Power domains

For more details on power domains, see AM011 section "Power Domains." [<u><span>(link)</span></u>](https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/Power-Domains)

-   **FPD**
    
    -   Full Power Domain
    
-   **LPD**
    
    -   Low Power Domain
    
-   **BPD**
    
    -   Battery Power Domain
    
-   **SPD**
    
    -   System Power Domain
        

## Software

**Configuration and Boot**

-   **PDI**
    
    -   Programmable Device Image. A file that contains configuration data needed to initialize components on the chip. See [https://support.xilinx.com/s/article/1146981?language=en\_US](https://support.xilinx.com/s/article/1146981?language=en_US)
    
-   **PSMFW**
    
    -   PSM Firmware. This is loaded into and executed by the PSM during boot.
    
-   **PLM**
    
    -   Platform Loader and Manager. This is roughly equivalent to the FSBL (First Stage Boot Loader) on the Zynq-7000 and UltraScale+.
        

## References

[<u><span>AM011</span></u>](https://docs.xilinx.com/r/en-US/am011-versal-acap-trm): Versal Adaptive SoC Technical Reference Manual

[<u><span>UG1304</span></u>](https://docs.xilinx.com/r/en-US/ug1304-versal-acap-ssdg): Versal Adaptive SoC System Software Developers Guide