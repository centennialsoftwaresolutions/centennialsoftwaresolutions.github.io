# Versal overview, product lineup, and series comparisons

![Xilinx_logo](Xilinx_logo.png)

The Versal ACAP is Xilinx's latest FPGA product and is the successor to the Zynq UltraScale+. It combines an FPGA, real-time processor (2x ARM Cortex-R5F), application processor (2x ARM Cortex-A72), and an AI engine into one chip. A Network-on-Chip (NoC) connects all of these components.

The main upgrades from the UltraScale+ to the Versal are the NoC interconnect and the AI engine. We'll soon publish a more in-depth article about the Versal AI engine. In short, it's an interconnected collection of small processor cores which excel at AI/ML and DSP tasks. Each AI core is a mini-processor that can execute scalar instructions and parallel vector (VLIW SIMD) instructions - so the AI engine is much more flexible than a GPU. Xilinx makes two versions of the AI engine array, one suited for DSP tasks and one suited for ML inference tasks. Xilinx refers to the DSP-focused version as the AI Engine (AIE) and the ML-focused version as the AIE-ML.

Additionally, the PL (programmable logic), aka FPGA on the Versal [<u><span>ACAPs</span></u>](https://docs.xilinx.com/r/en-US/am016-versal-cpm-ccix/Introduction-to-Versal-ACAP) contains dedicated DSP engines. These are separate from the AI engines (even the DSP-focused AI engines). The amount of DSP engines on a chip depends on the size of that chip's FPGA - Versal models with larger FPGAs have more DSP engines.

Xilinx also has some new names for the chip components:

\- The ARM cores are the "Scalar Engines" (previously called APU on UltraScale+)

\- The FPGA is called the "Adaptive Engine"

\- The AI cores and DSP engines are collectively referred to as the "Intelligent Engines"

The Versal lineup is divided into five product series.

Every Versal, regardless of its series, has a NoC and has the same Scalar Engine (2x R5F + 2x A72). And every Versal has DSP engines in the PL.

\- The **AI Edge (VE)** series is the smallest version of Versal - the FPGAs on these range from 20k to 500k LUTS. The size of the AI engine ranges from 8 to 300 cores. Most AI Edge products have an ML-focused AI engine, but one AI Edge chip is available with 300 DSP-focused AI cores.

\- The **AI Core (VC)** is larger, with the FPGA ranging from 250k to 900k LUTs. Most AI Core products have a 130-400 core DSP-optimized AI engine, but some AI Core chips are also available with the ML-optimized AI engine (up to 300 cores).

Xilinx also makes a military and space-grade Versal. The Versal XQR is a radiation-hardened version of the AI Core VC1902 chip, with 900k LUTs and 400 DSP-focused AI cores. See [<u><span>XMP490</span></u>](https://docs.xilinx.com/api/khub/documents/9AfO6ZB47HjDtc88g1jVBA/content) for details.

All AI Edge and AI Core series Versal ACAPs have an AI engine. The remaining three series mostly do not have an AI engine - they only have the ARM cores and FPGA, much like an UltraScale+.

\- **Versal Prime (VM)** ACAPs are small-midsize chips without an AI engine. The FPGAs range from 150k to 1 million LUTs.

\- The **Versal Premium (VP)** series has large FPGAs, from 380k to 3.3 million LUTs. Most Versal Prime chips do not have AI engines, but two chips are available with 470 DSP-focused AI engines.

\- The **Versal HBM (VH)** series do not have AI engines but are equipped with up to 32 GB of on-chip HBM.

For more information, refer to [DS950: Versal Architecture and Product Data Sheet: Overview](https://docs.xilinx.com/v/u/en-US/ds950-versal-overview).