# Xilinx 2018.2 Software Tool Installation Overview and Assessment

![xilinx_logo_1](xilinx_logo_1.png)

This post enumerates the size of the Vivado, SDK, PetaLinux Tools and SDx (which includes SDSoC and SDAccel) installers, the system requirements and installation documentation. It also provides a high-level assessment based on the enumeration and 3 calls to action for Xilinx.

*Looking for help build software for Xilinx SoCs? Email* [*inquiries@centennialsoftwaresolutions.com*](mailto:inquiries@centennialsoftwaresolutions.com?subject=I'm+looking+for+a+30-min+consult+on+building+software+for+Xilinx+SoCs+for+$99.00) ***today\*** *to schedule a 30-min consult for $99.00*

This post may be useful to anyone trying to size a local development computer, AWS or Google Cloud instance and trying to gauge how long an installation might take. It also contains links to Xilinx documentation on each tools listed.

It also provides a view of most of the major tools so it may be easier to see holistic issues between them.

This post will be updated with the actual size of the installed tools (once I install them). I also need to add all the packages that SDAccel requires.

**High-Level Assessment of Installation and Documentation Issues**

-   Vivado, the SDK, PetaLinux Tools, SDSoC and SDAccel Operating Systems support lists are not aligned
    
-   This may imply that tool development at Xilinx is siloed. It also implies quality issues between tools.
    
-   There are also many instances of errors in documentation, for instance:
    
-   In the 2018.2 PetaLinux Tools Documentation Reference Guide UG1144 (v2018.2) June 6, 2018 it lists:
    
-   "IMPORTANT: PetaLinux v2018.1 works only with Vivado 2018.1."
    
-   ...but this is a 2018.2 guide
    
-   or "$ ./petalinux-v2018.1-final-installer.run /opt/pkg/petalinux"
    
-   PetaLinux Tools and SDx require the user to manually install large lists of additional packages
    
-   These additional packages are specified ambiguously, i.e. the versions of all packages are note listed
    
-   This \_will\_ cause quality issues for customers because their builds will not be 100% reproduceable
    
-   Because installing these additional packages is error prone, customers will not be able to reproduce the results that Xilinx has produced, e.g. the customer may use a different version of "diffstat" vs. the one that was used at Xilinx, introducing a subtle bug.
    
-   You will need to download over 44 GB of installers to install: Vivado (17.1 GB), the SDK is installer (TBD), PetaLinux Tools (6.5 GB) and SDx (includes SDSoC and SDAccel) (20.35 GB).
    
-   Vivado may need up to 50 GB of memory to synthesize a design
    
-   If you install Vivado, the SDK, PetaLinux Tools and SDx you could have **2 copies of Vivado** and **4 copies of the SDK**
    
-   ****Vivado contains the SDK, SDx contains the SDK and Vivado, PetaLinux Tools includes the SDK
    
-   SDSoC doesn't support all the boards that PetaLinux Tools supports
    
-   As far as I am aware, the Linux kernel drivers for the Xilinx® Kintex UltraScale FPGA KCU1500 Reconfigurable Acceleration card based on XCKU115-FLVB2104-2-E FPGA and the Xilinx Virtex UltraScale+ FPGA VCU1525 Reconfigurable Acceleration card based on XCVU9P-L2FSGD2104E FPGA have not been submitted upstream
    
-   This means the drivers may have performance, compilation or quality issues
    
-   Note: Intel (Altera) have already upstreamed support for their card
    
-   This means when you plug an Altera card in, it just works, but a Xilinx card will require compiling a module
    
-   This may be an issue if you're installing cards in a data center
    

**Calls to Action for Xilinx**

-   Unify the supported OS's across all tools
    
-   Ensure SDSoC runs on all the BSPs that PetaLinux Tools supports
    
-   Leverage you Linaro membership and upstream the Linux drivers for the boards that SDAccel supports
    

**Vivado 2018.2**

Xilinx Vivado Developer Zone at \[[link](http://www.xilinx.com/products/design-tools/vivado.html)\].

The Vivado installer contains:

-   Design Tools
    
-   Vivado
    
-   Vivado High-Level Synthesis - build "logic" with C, C++ and System C \[[link](http://www.xilinx.com/products/design-tools/vivado/integration/esl-design.html)\]
    
-   Vivado IP Integrator - Connect interfaces, e.g. AXI4 not signals \[[link](http://www.xilinx.com/products/design-tools/vivado/integration.html)\]
    
-   Vivado Simulator - supports Verilog, SystemVerilog and VHDL \[[link](http://www.xilinx.com/products/design-tools/vivado/simulator.html)\]
    
-   Vivado Simulation Flow - simulate your design \[[link](http://www.xilinx.com/products/design-tools/vivado/simulation.html)\]
    
-   Vivado Hardware Debug - debug on hardware \[[link](http://www.xilinx.com/products/design-tools/vivado/debug.html)\]
    
-   HW Manager is available as a separate package called Vivado Lab Edition. See \[[link](http://www.xilinx.com/products/design-tools/vivado/debug.html)\]
    
-   HW manager programs the FPGA, accesses the system monitor, provides basic remote debugging and advanced debugging using the Xilinx Virtual Cable \[[link](http://www.xilinx.com/products/intellectual-property/xvc.html)\].
    
-   Model Composer - Automatic High-Level HDL from MathWorks Simulink® \[[link](http://www.xilinx.com/products/design-tools/vivado/integration/model-composer.html)\]
    
-   System Generator for DSP - Lower level DSP to HDL than Model Composer \[[link](http://www.xilinx.com/products/design-tools/vivado/integration/sysgen.html)\]
    
-   Verification IP - verify AXI3, AXI4 and AXI-Lite, etc... \[[link](http://www.xilinx.com/products/design-tools/vivado/verification-ip.html)\]
    
-   the SDK
    
-   and DocNav
    
-   Support for these devices
    
-   Production Devices
    
-   SoCs
    
-   7-Series
    
-   UltraScale
    
-   UtraScale+
    
-   Engineering Sample Devices
    
-   Kintex UltraScale+ ES
    
-   Virtex UltraScale+ ES
    
-   Virtext UltraScale+ HBM ES
    
-   Zynq UltraScale+ MPSoC ES
    
-   Zynq UltraScale+ RFSoC ES
    
-   Also includes support for
    
-   Windows and Linux drivers for the Xilinx Platform Cable USB II
    
-   The Vivado® License Manager (VLM) for getting and managing license keys
    
-   WebTalk that tells Xilinx how you're using the tools (always enabled for WebPACK) for Vivado and the SDK
    
-   WinPCap for Ethernet Hardware Co-simulation
    
-   An ability to launch a configuration manager to associate System Generator for DSP with MATLAB
    

Installer

Download page at \[[link](http://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools.html)\]

Vivado HLx 2018.2: All OS installer Single-File Download (TAR/GZIP - 17.11 GB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=Xilinx_Vivado_SDK_2018.2_0614_1954.tar.gz)\]

Editions

-   Vivado HL WebPACK
    
-   Vivado HL WebPACK is the no cost, **device limited** version of Vivado HL Design Edition. **Users can optionally add Model Composer and System Generator for DSP to this installation.**
    
-   Vivado HL Design Edition
    
-   Vivado HL Design Edition includes the full complement of Vivado Design Suite tools for design, including C-based design with Vivado High-Level Synthesis, implementation, verification and device programming. Complete device support, cable drivers and Documentation Navigator are included. **Users can optionally add Model Composer to the installation**.
    
-   Vivado HL System Edition
    
-   Vivado HL System Edition is a superset of Vivado HL Design Edition with the **addition of System Generator for DSP**. Complete device support, cable drivers and Documentation Navigator are included. Users can optionally add Model Composer to this installation.
    
-   Documentation Navigator (Standalone)
    
-   Xilinx Documentation Navigator (DocNav) provides access to Xilinx technical documentation both on the Web and on the Desktop. This is a standalone installation without Vivado Deisng Suite.
    

_WebPACK vs. Other Editions_

Vivado Design Suite WebPACK™ tool versus all other Vivado Design Suite editions. : Sheet1

| From: Vivado Design Suite 2018.2 Release Notes UG973 (v2018.2) June 6, 2018 |                                                              |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Device                                                       | Vivado WebPACK Tool                                          | Vivado Design Suite (All Other Editions)                     |
| Zynq® Device                                                 | Zynq-7000 SoC Device • XC7Z010, XC7Z015, XC7Z020, XC7Z030, XC7Z007S, XC7Z012S, and XC7Z014S | Zynq-7000 SoC Device • All                                   |
| Zynq® UltraScale™+ MPSoC                                     | UltraScale+ MPSoC • XCZU2EG, XCZU2CG, XCZU3EG, XCZU3CG XCZU4EG, XCZU4CG, XCZU4EV, XCZU5EG, XCZU5CG, XCZU5EV, XCZU7EV, XCZU7EG, and XCZU7CG | UltraScale+ MPSoC • All                                      |
| Zynq® UltraScale+™ RFSoC                                     | Zynq® UltraScale+™ RFSoC • None                              | Zynq® UltraScale+™ RFSoC • All                               |
| Virtex® FPGA                                                 | Virtex-7 FPGA • None  Virtex UltraScale™ FPGA • None         | Virtex-7 FPGA • All Virtex UltraScale FPGA • All Virtex UltraScale+ FPGA • All |
| Kintex® FPGA                                                 | Kintex-7 FPGA • XC7K70T, XC7K160T Kintex UltraScale™ FPGA • XCKU025, XCKU035 Kintex UltraScale+ FPGA • XCKU3P. XCKU5P | Kintex-7 FPGA • All Kintex UltraScale FPGA • All Kintex UltraScale+ FPGA • All |
| Artix® FPGA                                                  | Artix-7 FPGA • XC7A12T, XC7A15T, XC7A25T, XC7A35T, XC7A50T, XC7A75T, XC7A100T, XC7A200T | Artix-7 FPGA • All                                           |
| Spartan®-7                                                   | Spartan-7 • XC7S6, XC7S15 • XC7S25, XC7S50                   | Spartan-7 • All                                              |

Sheet at [[link](http://docs.google.com/spreadsheets/d/1B8_Y2Ul9vEuOtbjyGCiWDxnCf_uPbRi8iyWTPdl3b1c/edit?usp=sharing)].

Operating Systems Supported

Copied verbatim from page 11 of UG973 (v2018.2) June 6, 2018

-   Microsoft Windows Support
    
-   Windows 7 SP1 Professional (64-bit), English/Japanese.
    
-   Windows 10.0 Fall Creators update (version 1709), 10.0 Version 1803 (64-bit), English/Japanese.
    
-   Linux Support
    
-   Red Hat Enterprise Workstation/Server 7.2, 7.3, and 7.4 (64-bit)
    
-   Red Hat Enterprise Workstation 6.6, 6.7, 6.8, and 6.9 (64-bit)
    
-   SUSE Linux Enterprise 11.4 and 12.3 (64-bit)
    
-   CentOS 7.2, 7.3, and 7.4 (64-bit)
    
-   CentOS 6.7, 6.8, and 6.9 (64-bit)
    
-   Ubuntu Linux 16.04.3 LTS (64-bit)
    

BUG: **32-bit OSs are not supported as stated**. On page 11 of UG973 (v2018.2) June 6, 2018 it lists, "Xilinx® supports the following operating systems on x86 and x86-64 processor architectures." however, none of the operating systems listed is a 32-bit operating system.

Installed Disk Requirements

TBD

Memory Recommendations for Vivado

| From https://www.xilinx.com/products/design-tools/vivado/memory.html on Jun 6, 2018 |          |                                 |       |
| ------------------------------------------------------------ | -------- | ------------------------------- | ----- |
| Family                                                       | Device   | GBs on Windows / Linux (64-bit) |       |
| Typical                                                      | Peak     |                                 |       |
| Kintex UltraScale+                                           | XCKU3P   | 7                               | 10    |
| XCKU5P                                                       | 9        | 13                              |       |
| XCKU9P                                                       | 10       | 15                              |       |
| XCKU11P                                                      | 11       | 16                              |       |
| XCKU13P                                                      | 12       | 18                              |       |
| XCKU15P                                                      | 13       | 30                              |       |
| Virtex UltraScale+                                           | XCVU3P   | 11                              | 16    |
| XCVU5P                                                       | 13       | 21                              |       |
| XCVU7P                                                       | 21       | 29                              |       |
| XCVU9P                                                       | 27       | 37                              |       |
| XCVU11P                                                      | 33       | 43                              |       |
| XCVU13P                                                      | 35       | 50                              |       |
| Zynq UltraScale+                                             | XCZU2EG  | 3                               | 4     |
| XCZU3EG                                                      | 4        | 5                               |       |
| XCZU4EV                                                      | 5        | 6                               |       |
| XCZU5EV                                                      | 6        | 8                               |       |
| XCZU6EG                                                      | 9        | 14                              |       |
| XCZU7EV                                                      | 9        | 14                              |       |
| XCZU9EG                                                      | 10       | 15                              |       |
| XCZU11EG                                                     | 10       | 16                              |       |
| XCZU15EG                                                     | 11       | 16                              |       |
| XCZU17EG                                                     | 12       | 18                              |       |
| XCZU19EG                                                     | 13       | 21                              |       |
| Kintex UltraScale                                            | XCKU025  | 5                               | 7     |
| XCKU035                                                      | 5        | 7                               |       |
| XCKU040                                                      | 5        | 7                               |       |
| XCKU060                                                      | 7        | 11                              |       |
| XCKU085                                                      | 9        | 14                              |       |
| XCKU095                                                      | 9        | 14                              |       |
| XCKU115                                                      | 9        | 14                              |       |
| Virtex UltraScale                                            | XCVU065  | 7                               | 11    |
| XCVU080                                                      | 8        | 12                              |       |
| XCVU095                                                      | 9        | 14                              |       |
| XCVU125                                                      | 10       | 16                              |       |
| XCVU160                                                      | 14       | 20                              |       |
| XCVU190                                                      | 18       | 24                              |       |
| XCVU440                                                      | 32       | 48                              |       |
| Virtex-7                                                     | XC7V585T | 4                               | 6     |
| XC7V2000T                                                    | 10       | 16                              |       |
| XC7VX330T                                                    | 3        | 5                               |       |
| XC7VX415T                                                    | 3        | 5                               |       |
| XC7VX485T                                                    | 4        | 5                               |       |
| XC7VX550T                                                    | 4        | 6                               |       |
| XC7VX690T                                                    | 5        | 7                               |       |
| XC7VX980T                                                    | 7        | 9                               |       |
| XC7VX1140T                                                   | 8        | 10                              |       |
| XC7VH580T                                                    | 4        | 6                               |       |
| XC7VH870T                                                    | 6        | 8                               |       |
| Kintex-7                                                     | XC7K70T  | 1.6                             | 2.5   |
| XC7K160T                                                     | 2        | 3                               |       |
| XC7K325T                                                     | 3        | 4                               |       |
| XC7K355T                                                     | 3        | 5                               |       |
| XC7K410T                                                     | 3        | 5                               |       |
| XC7K420T                                                     | 3        | 5                               |       |
| XC7K480T                                                     | 4        | 6.5                             |       |
| Artix-7                                                      | XC7A15T  | 2                               | 3     |
| XC7A35T                                                      | 2        | 3                               |       |
| XC7A50T                                                      | 2        | 3                               |       |
| XC7A75T                                                      | 2        | 3                               |       |
| XC7A100T                                                     | 2        | 3                               |       |
| XC7A200T                                                     | 2.5      | 3.5                             |       |
| Zynq-7000                                                    | XC7Z010  | 1                               | 1.6   |
| XC7Z015                                                      | 1.3      | 1.9                             |       |
| XC7Z020                                                      | 1.3      | 1.9                             |       |
| XC7Z030                                                      | 1.8      | 2.7                             |       |
| XC7Z035                                                      | 3        | 5                               |       |
| XC7Z045                                                      | 3        | 5                               |       |
|                                                              | Avg      | 8.10                            | 12.01 |
|                                                              | Min      | 1                               | 1.6   |
|                                                              | Max      | 35                              | 50    |

Sheet at [[link](http://docs.google.com/spreadsheets/d/1dSPo0sMx14Y513ix39iYsVnmUvQM_2pFeZpllw-Bi28/edit?usp=sharing)].

**SDK 2018.2**

The SDK allows you to:

-   Build software that does not require an operating system, aka "bare-metal apps"
    
-   Debug user space Linux code
    
-   Debug Linux kernel code\* (still trying to get this to work)
    
-   Debug the Xen hypervisor (haven't tried this)
    
-   Debug and build PMUFW
    
-   Debug and build FSBL
    

2018.2 Release Notes and Known Issues at \[[link](http://www.xilinx.com/support/answers/66303.html)\]

The SDK installer contains:

TBD

Installers

Download page at \[[link](http://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html)\].

SDK 2018.2 Web Install for Windows 64 (EXE - 50.4 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=Xilinx_SDK_2018.2_0614_1954_Win64.exe)\] 

SDK 2018.2 Web Install for Linux 64 (BIN - 99.29 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=Xilinx_SDK_2018.2_0614_1954_Lin64.bin)\]

Development Hardware Requirements

-   CPU Speed
    
-   2.2 GHz minimum or higher; Hyper-threading (HHT) or Multi-core recommended.
    
-   Processor
    
-   Intel Pentium 4, Intel Core Duo, or Xeon Processors; SSE2 minimum
    
-   Memory/RAM
    
-   2 GB or higher
    
-   Display Resolution
    
-   1024×768 or higher at normal size (96 dpi)
    

Operating Systems Supported

Copied verbatim from **System Requirements** at \[[link](http://www.xilinx.com/html_docs/xilinx2018_2/SDK_Doc/xsct/intro/xsct_system_requirements.html?hl=install)\]

-   Windows
    
-   Windows 7 SP1 (64-bit)
    
-   Windows 8.1 (64-bit)
    
-   Windows 10 Pro (64-bit)
    
-   Linux (Note: Additional library installation required.)
    
-   Red Hat Enterprise Linux:
    
-   6.6-6.9 (64-bit)
    
-   7.0-7.1 (64-bit)
    
-   CentOS:
    
-   6.7-6.8 (64-bit)
    
-   7.2-7.3 (64-bit)
    
-   SUSE Linux Enterprise:
    
-   11.4 (64-bit)
    
-   12.2 (64-bit)
    
-   Ubuntu Linux 16.04.2 LTS (64-bit)
    

Note: 32-bit machine support is now only available through Lab Tools and Hardware Server standalone product installers.

Disk Requirements

TBD

**PetaLinux Tools 2018.2**

Installers

Download page at \[[link](http://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html)\].

PetaLinux 2018.2 Installer (TAR/GZIP - 6.15 GB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=petalinux-v2018.2-final-installer.run)\]

-   Zynq-7000
    
-   ZC702 BSP (BSP - 105.1 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-zc702-v2018.2-final.bsp)\]
    
-   ZC706 BSP (BSP - 106.72 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-zc706-v2018.2-final.bsp)\]
    
-   ZED BSP (BSP - 106.97 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=avnet-digilent-zedboard-v2018.2-final.bsp)\]
    
-   AC701 BSP (BSP - 570.06 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-ac701-v2018.2-final.bsp)\]
    
-   KCU105 BSP (BSP - 353.14 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-kcu105-axi-full-v2018.2-final.bsp)\]
    
-   KC705 BSP (BSP - 529.46 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-kc705-v2018.2-final.bsp)\]
    
-   Zynq UltraScale+ MPSoC
    
-   ZCU102 BSP (prod-silicon) (BSP - 599.59 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-zcu102-v2018.2-final.bsp)\]
    
-   ZCU102 ZU9 ES2 Rev 1.0 BSP (BSP - 599.12 MB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-zcu102-zu9-es2-rev1.0-v2018.2-final.bsp)\]
    
-   ZCU104 BSP (BSP - 1.27 GB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-zcu104-v2018.2-final.bsp)\]
    
-   ZCU106 BSP (BSP - 1.24 GB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-zcu106-v2018.2-final.bsp)\]
    
-   Ultra96 BSP (BSP - 2.76 GB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-ultra96-reva-v2018.2-final.bsp)\]
    

Development Hardware Requirements

Copied verbatim from **Supported OS** on page 9 of \[[link](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug1144-petalinux-tools-reference-guide.pdf)\]

-   8 GB RAM (recommended minimum for Xilinx tools)
    
-   2 GHz CPU clock or equivalent (minimum of 8 cores)
    
-   100 GB free HDD space
    

Operating Systems Supported

Copied verbatim from **Supported OS** on page 9 of \[[link](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug1144-petalinux-tools-reference-guide.pdf)\]

-   Linux
    
-   Red Hat Enterprise Workstation/Server 7.2, 7.3, 7.4 (64-bit)
    
-   CentOS 7.2, 7.3, 7.4 (64-bit)
    
-   Ubuntu Linux 16.04.3 (64-bit)
    

Packages and Linux Workstation Environments

Packages and Linux Workstation Environments : Table 2-1 UG1144 (v2018.2) Jun 6 2018

| Tool / Library                                    | CentOS 7.2/7.3/7.4                                        | RHEL7.2/7.3/7.4                                           | Ubuntu 16.04.3                            |
| ------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | ----------------------------------------- |
| dos2unix                                          | dos2unix-6.0.3-4.el7.x86_64.rpm                           | dos2unix-6.0.3-4.el7.x86_64.rpm                           | tofrodos_1.7.13+ds-2.debian.tar.xz        |
| ip                                                | iproute-3.10.0-74.el7.x86_64.rpm                          | iproute-3.10.0-74.el7.x86_64.rpm                          | iproute2 4.3.0-1ubuntu3                   |
| gawk                                              | gawk-4.0.2-4.el7.x86_64.rpm                               | gawk-4.0.2-4.el7.x86_64.rpm                               | gawk (1:4.1.3+dfsg-0.1)                   |
| gcc                                               | gcc-4.8.5-11.el7.x86_64                                   | gcc-4.8.5-11.el7.x86_64                                   | -                                         |
| g++ (gcc-c++)                                     | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64.rpm              | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64.rpm              | -                                         |
| xvfb                                              | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64.rpm              | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64.rpm              | xvfb (2:1.18.3-1ubuntu2.3)                |
| git                                               | git 1.8.3                                                 | git 1.8.3                                                 | git 1.7.1 or above                        |
| make                                              | make 3.81                                                 | make 3.82                                                 | make 3.81                                 |
| netstat                                           | net-tools 2.0                                             | net-tools 2.0                                             | net-tools                                 |
| ncurses devel                                     | ncurses-devel 5.9-13                                      | ncurses-devel 5.9-13                                      | libncurses5-dev                           |
| tftp server                                       | tftp-server                                               | tftp-server                                               | tftpd                                     |
| zlib devel (also, install 32-bit of this version) | zlib-devel-1.2.7-17.el7.x86_64.rpm                        | zlib-devel-1.2.7-17.el7.x86_64.rpm                        | i386/zlib1g-dev/1:1.2.8.dfsg-2ubuntu4-dev |
| openssl devel                                     | openssl-devel 1.0                                         | openssl-devel 1.0                                         | libssl-dev                                |
| flex                                              | flex 2.5.37                                               | flex 2.5.37                                               | flex                                      |
| bison                                             | bison-2.7                                                 | bison-2.7.4                                               | bison                                     |
| libselinux                                        | libselinux 2.2.2                                          | libselinux 2.2.3                                          | libselinux1                               |
| gnupg                                             | gnupg                                                     | gnupg                                                     | gnupg                                     |
| wget                                              | wget                                                      | wget                                                      | wget                                      |
| diffstat                                          | diffstat                                                  | diffstat                                                  | diffstat                                  |
| chrpath                                           | chrpath                                                   | chrpath                                                   | chrpath                                   |
| socat                                             | socat                                                     | socat                                                     | socat                                     |
| xterm                                             | xterm                                                     | xterm                                                     | xterm                                     |
| autoconf                                          | autoconf                                                  | autoconf                                                  | autoconf                                  |
| libtool                                           | libtool                                                   | libtool                                                   | libtool                                   |
| tar                                               | tar:1.24                                                  | tar:1.24                                                  | tar:1.24                                  |
| unzip                                             | unzip                                                     | unzip                                                     | unzip                                     |
| texinfo                                           | texinfo                                                   | texinfo                                                   | texinfo                                   |
| zlib1g-dev                                        | -                                                         | -                                                         | zlib1g-dev                                |
| gcc-multilib                                      | -                                                         | -                                                         | gcc-multilib                              |
| build-essential                                   | -                                                         | -                                                         | build-essential                           |
| libsdl1.2-dev                                     | -                                                         | -                                                         | libsdl1.2-dev                             |
| libglib2.0-dev                                    | -                                                         | -                                                         | libglib2.0-dev                            |
| SDL-devel                                         | SDL-devel                                                 | SDL-devel                                                 | -                                         |
| 32-bit glibc                                      | glibc-2.17-157.el7_3.4.i686 glibc-2.17-157.el7_3.4.x86_64 | glibc-2.17-157.el7_3.4.i686 glibc-2.17-157.el7_3.4.x86_64 | -                                         |
| glibc-devel                                       | glibc-devel                                               | glibc-devel                                               | -                                         |
| automake                                          | automake                                                  | automake                                                  | -                                         |
| screen                                            | screen                                                    | screen                                                    | screen                                    |
| pax                                               | pax                                                       | pax                                                       | pax                                       |
| gzip                                              | gzip                                                      | gzip                                                      | gzip                                      |
| libstdc++                                         | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686 | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686 | -                                         |

Sheet at [[link](http://docs.google.com/spreadsheets/d/1O3xpkJ_JbvwBkVRE0inlY4PR_enIi0ZKvAksvw26iaM/edit?usp=sharing)].

**SDx: SDSoC and SDAccel**

Installers

SDSoC Download page at \[[link](http://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/sdx-development-environments.html)\]

SDAccel Download page at \[[link](http://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/sdaccel-development-environment.html)\]

SDx 2018.2 SFD (TAR/GZIP - 20.35 GB) at \[[link](http://feedback.xilinx.com/se.ashx?s=40A62BAE53BF137B?wsb5=xef.html&wsb7=Xilinx_SDx_2018.2_0614_1954.tar.gz)\]

SDAccel 2018.2 SFD (TAR/GZIP - 20.35 GB) at \[[link](http://www.xilinx.com/member/forms/download/xef.html?filename=Xilinx_SDx_2018.2_0614_1954.tar.gz)\] (same as SDx 2018.2 SFD, see analysis at \[[link](http://www.zachpfeffer.com/single-post/SDx-20182-SFD-is-the-same-thing-as-SDAccel-20182-SFD)\])

Boards Supported

SDSoC supports these boards:

-   Zynq-7000
    
-   ZC702
    
-   ZC706
    
-   ZedBoard
    
-   Zynq UltraScale+ MPSoC
    
-   ZCU102
    
-   ZCU104
    
-   ZCU106
    

Note: The SDSoC Platform Utility enables you to target any custom Zynq and Zynq UltraScale+ MPSoC board.

SDAccel supports the following acceleration cards:

-   Xilinx® Kintex UltraScale FPGA KCU1500 Reconfigurable Acceleration card based on XCKU115-FLVB2104-2-E FPGA.
    
-   Xilinx Virtex UltraScale+ FPGA VCU1525 Reconfigurable Acceleration card based on XCVU9P-L2FSGD2104E FPGA
    

Plugged into a host computer with:

-   Motherboard with a PCIe® Gen3 X8 slot
    
-   64 GB RAM
    
-   100GB free disk space
    

Operating Systems Supported

Copied verbatim from page 32 of **SDx Release Notes, Installation, and Licensing Guide UG1238 (v2018.2) June 6, 2018**

-   Windows
    
-   Windows 7 and 7 SP1 Professional (64-bit), SDSoC™ only
    
-   Windows 10 Professional versions 1709 and 1803(64-bit), SDSoC only
    
-   Linux Support
    
-   Red Hat Enterprise Workstation/Server 7.3-7.4 (64-bit)
    
-   Red Hat Enterprise Workstation 6.7, and 6.8 (SDSoC only)
    
-   CentOS 7.2
    
-   CentOS 7.3-7.4 (64-bit) (SDSoC only)
    
-   Ubuntu Linux 16.04.3 LTS (64-bit)
    
-   Linux kernel 4.4.0 is supported
    
-   Ubuntu LTS enablement (also called HWE or Hardware Enablement) is not supported
    

SDSoC Note

The installation of SDSoC™ includes the following:

-   SDSoC environment, including an Eclipse/CDT-based GUI, high-level system compiler, and
    
-   ARM GNU toolchain
    
-   Vivado® Design Suite System Edition with Vivado® High-Level Synthesis (HLS) and the Xilinx® Software Development Kit (SDK)
    

The SDSoC environment includes the same GNU ARM toolchain included with the Xilinx Software Development Kit (SDK), which also provides additional tools used by the SDSoC environment. The SDSoC environment setup script sets PATH variables to use this toolchain.

**References**

-   Vivado Design Suite Release Notes, Installation, and Licensing Guide at \[[link](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug973-vivado-release-notes-install-license.pdf)\]
    
-   A.K.A. Vivado Design Suite 2018.2 Release Notes, UG973 (v2018.2) June 6, 2018
    
-   Vivado Memory Recommendations at \[[link](http://www.xilinx.com/products/design-tools/vivado/memory.html)\]
    
-   SDK Documentation at \[[link](http://www.xilinx.com/html_docs/xilinx2018_2/SDK_Doc/index.html)\]
    
-   System Requirements at \[[link](http://www.xilinx.com/html_docs/xilinx2018_2/SDK_Doc/xsct/intro/xsct_system_requirements.html?hl=install)\]
    
-   PetaLinux Tools Documentation: Reference Guide, UG1144 (v2018.2) at \[[link](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug1144-petalinux-tools-reference-guide.pdf)\]
    
-   SDx Development Environment Release Notes, Installation, and Licensing Guide UG1238 (v2018.2) June 6, 2018 at \[[link](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug1238-sdx-rnil.pdf)\]
    
-   100% iframe tip from stackoverflow at \[[link](http://stackoverflow.com/questions/5867985/full-screen-iframe-with-a-height-of-100)\]
    
-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]