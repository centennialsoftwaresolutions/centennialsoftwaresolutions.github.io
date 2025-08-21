# Unlocking FPGA Magic: From HDL to Hardware

![amd_wizard](amd_wizard.png)

Welcome to the world of FPGA design, where your ideas can come to life in silicon! This blog post discusses common processes and tools to turn HDL into hardware. First, we'll give a quick synthesis overview - this is where your HDL code gets transformed into the actual logic on an FPGA. It's like a puzzle where your code pieces fit into the FPGA's configurable logic blocks (CLBs), Block RAMS (BRAMs), and other elements (a full list is given below). Next, we discuss the cool tools and compilers that perform synthesis from HDL (Hardware Description Language) and can help simulate designs. Lastly, we'll cover High-Level Synthesis tools that can transform C/C++/System C into HDL. It's all about choosing the right tool for the job. So, buckle up, and let's explore how to go from lines of HDL to a chip that does your bidding!

###### HDL CLB Translation Process

The process of translating HDL (Hardware Description Language) code into a configuration for the CLBs (Configurable Logic Blocks) of an FPGA (Field-Programmable Gate Array) is known as "synthesis." Here's a brief overview of the steps involved in this process:

**HDL Coding**: The desired digital circuit is initially described using a Hardware Description Language such as VHDL or Verilog. This HDL code represents the logical behavior and structure of the digital circuit.

**Synthesis:** The synthesis tool takes the HDL code as input and translates it into a netlist. This netlist describes the circuit in terms of generic logic gates and interconnections. During synthesis, the tool optimizes to reduce the circuit's complexity, improve performance, or meet other design constraints.

**Technology Mapping**: The next step is to map the generic logic elements in the netlist to the specific resources available on the FPGA. For FPGAs, this involves mapping the logic to Configurable Logic Blocks (CLBs), Block RAMs (BRAMs), Digital Signal Processing (DSP), I/O Blocks (IOBs), Clock Management Tiles (CMTs), Switch Matrix or Interconnect, SerDes (Serializer/Deserializer) Blocks, Transceivers, Hard IP Cores, Embedded Processors, Configuration Memory, Power Management Blocks, and Analog-to-Digital Converters (ADCs), and **now AI Engines!**

**Place and Route**: The "place and route" step is performed after technology mapping. Here, the tool assigns the mapped elements to specific elements on the FPGA and determines the interconnections' routing.

**Bitstream Generation**: A bitstream is generated once the design is successfully placed and routed. This bitstream is a binary file containing the FPGA configuration data. When loaded into the FPGA, this bitstream configures the resources to implement the desired circuit.

**Loading to FPGA**: Finally, the bitstream is loaded onto the FPGA, configuring it to perform the functions defined by the original HDL code.

FPGA design software like Xilinx Vivado, Intel Quartus Prime, and others facilitate this process, providing integrated environments for HDL coding, synthesis, simulation, and bitstream generation.

###### FPGA Synthesis Tools

Here are some of the most widely used tools that synthesize a bitstream from a design described in HDL.

[**<u><span>AMD (Xilinx) Vivado Design Suite</span></u>**](https://www.xilinx.com/products/design-tools/vivado.html): This software suite for designing systems using Xilinx FPGAs. Vivado includes tools for HDL synthesis, simulation, and debugging. It supports VHDL, Verilog, and SystemVerilog.

[**<u><span>Intel Quartus Prime</span></u>**](https://www.intel.com/content/www/us/en/products/details/fpga/development-tools/quartus-prime.html): Similar to Vivado, but for Intel (formerly Altera) FPGAs. Quartus Prime supports VHDL, Verilog, and SystemVerilog for design entry, synthesis, and verification.

[**<u><span>Lattice Diamond</span></u>**](https://www.latticesemi.com/latticediamond): This is the design software for Lattice Semiconductor FPGAs. It supports HDL synthesis and is used for Lattice's low-power FPGA families.

[**<u><span>Microchip Libero SoC</span></u>**](https://www.microchip.com/en-us/products/fpgas-and-plds/fpga-and-soc-design-tools/fpga/libero-software-later-versions): This tool is used for Microchip (used to be Microsemi) FPGAs. It provides HDL synthesis, simulation, and other design tools.

[**<u><span>GHDL</span></u>**](https://github.com/ghdl/ghdl): An open-source simulator for VHDL that can be used with other FPGA design tools.

[**<u><span>Icarus Verilog</span></u>**](https://github.com/steveicarus/iverilog): Another open-source tool, this time for Verilog HDL. It is primarily a simulator but can be used as part of a toolchain for FPGA design.

[**<u><span>Synopsys Synplify/Synplify Pro</span></u>**](https://www.synopsys.com/implementation-and-signoff/fpga-based-design/synplify.html): These synthesis tools support VHDL, Verilog, and SystemVerilog, and are often used with other FPGA design software.

[**<u><span>ModelSim</span></u>**](https://en.wikipedia.org/wiki/ModelSim) **and** [**<u><span>QuestaSim </span></u>**](https://eda.sw.siemens.com/en-US/ic/questa/simulation/advanced-simulator/) **from Siemens**: These are comprehensive simulation and debugging tools for VHDL and Verilog often used in FPGA development.

###### HLS

In addition to these tools, there are high-level synthesis (HLS) tools like AMD's Vitis HLS, which allow designers to write code in C, C++, or SystemC and then compile it into HDL for FPGA implementation.

High-Level Synthesis (HLS) tools are designed to allow engineers and designers to write their algorithms in high-level programming languages like C, C++, or SystemC and then compile these into hardware description languages (HDL) for implementation on FPGAs or ASICs.

Here are some notable HLS tools:

[**<u><span>AMD Vitis HLS</span></u>**](https://www.xilinx.com/products/design-tools/vitis/vitis-hls.html): This tool enables designers to use C or C++ to develop their algorithms, which are then synthesized into optimized RTL code for Xilinx FPGAs.

[**<u><span>Intel FPGA SDK for OpenCL (Legacy)</span></u>**](https://www.intel.com/content/www/us/en/support/programmable/support-resources/devices/opencl-legacy-support.html): This tool allows developers to write their FPGA designs in OpenCL, a high-level, parallel programming language, and compile them for use on Intel FPGAs.

[**<u><span>Cadence Stratus High-Level Synthesis</span></u>**](https://www.cadence.com/en_US/home/tools/digital-design-and-signoff/synthesis/stratus-high-level-synthesis.html): Stratus HLS from Cadence allows for C/C++/SystemC-based design entry, providing an efficient path to RTL for both FPGA and ASIC implementations.

[**<u><span>Synopsys Synphony HLS</span></u>**](https://news.synopsys.com/index.php?s=20295&item=123096): This tool from Synopsys enables synthesizing high-level Matlab and Simulink models, along with C and C++ code, into RTL for both FPGAs and ASICs.

[**<u><span>Siemens Precision FPGA Synthesis</span></u>**](https://eda.sw.siemens.com/en-US/ic/precision/): Precision Synthesis is an FPGA vendor-independent solution. Precision has tight integration across the Siemens FPGA flow from C++/SystemC/RTL design through simulation and formal verification to board design.

[**<u><span>Microchip's SmartHLS</span></u>**](https://www.microchip.com/en-us/products/fpgas-and-plds/fpga-and-soc-design-tools/smarthls-compiler): Implement your design in C++ software and verify the functionality with software tests. Then, use SmartHLS high-level synthesis software to compile the C++ program into functionality-equivalent Verilog hardware modules.

[**<u><span>Mathworks HDL Coder</span></u>**](https://www.mathworks.com/products/hdl-coder.html): This tool generates Verilog, SystemVerilog, and VHDL code for FPGA and ASIC designs.

These tools may significantly streamline the FPGA design process, enabling designers to work at a higher level of abstraction, possibly accelerating the development cycle. However, these gains may not materialize in practice due to the different "execution" models C/C++ and HDLs abstract.