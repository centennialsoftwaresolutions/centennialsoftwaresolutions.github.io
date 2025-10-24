## 69074 - PetaLinux 2017.1 - Product Update Release Notes and Known Issues



## Title

69074 - PetaLinux 2017.1 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2017.1 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for 2017.1 PetaLinux Release**

This table contains supported BSPs for Zynq, MicroBlaze, Zynq UltraScale+ MPSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).



| Platform               | Variant                   | BSP Name                                       |
| :--------------------- | :------------------------ | :--------------------------------------------- |
| Zynq                   | ZC702                     | xilinx-zc702-v2017.1-final.bsp                 |
| Zynq                   | ZC706                     | xilinx-zc706-v2017.1-final.bsp                 |
| Zynq                   | ZEDBOARD                  | avnet-digilent-zedboard-v2017.1-final.bsp      |
| MicroBlaze             | KC705                     | xilinx-kc705-v2017.1-final.bsp                 |
| MicroBlaze             | AC701                     | xilinx-ac701-v2017.1-final.bsp                 |
| MicroBlaze             | KCU105                    | xilinx-kcu105-axi-full-v2017.1-final.bsp       |
| Zynq UltraScale+ MPSoC | ZCU102 production silicon | xilinx-zcu102-v2017.1-final.bsp                |
| Zynq UltraScale+ MPSoC | ZCU102 Rev 1.0 ES2        | xilinx-zcu102-zu9-es2-rev1.0-v2017.1-final.bsp |

BSP's for earlier boards with ES Silicon can be found at:

ZCU102 Rev D ES1 BSP - [Headstart Lounge](https://www.xilinx.com/member/zcu102_headstart.html)  





ZCU102 Rev D ES2 BSP - [EA Lounge](https://www.xilinx.com/member/zcu102_ea.html)

**Note**: The "[sstate cache file](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate-rel-v2017.1.tar.gz&akdm=1)" (sstate-rel-v2017.1.tar.gz) can be found on the Xilinx download area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2017.1_README&akdm=1) file that outlines the procedure to use "sstate cache".

**PetaLinux 2017.1 contains the following build collateral:**

| Component                                                    | Git repo                                                     | Tag            | Commit ID                                  | Branch             | Comments                             |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :------------- | :----------------------------------------- | :----------------- | :----------------------------------- |
| Device-tree                                                  | [git://github.com/Xilinx/device-tree-xlnx.git](git://github.com/Xilinx/device-tree-xlnx.git) | xilinx-v2017.1 | `94fc615234001221f57e435ea2a5664d17f7622e` | master             |                                      |
| Linux                                                        | [git://github.com/Xilinx/linux-xlnx.git](git://github.com/Xilinx/linux-xlnx.git) | xilinx-v2017.1 | `68e6869cfb8154b80ee9ffafd64932971e9d1d07` | master             | Kernel Version 4.9                   |
| U-Boot                                                       | [git://github.com/Xilinx/u-boot-xlnx.git](git://github.com/Xilinx/u-boot-xlnx.git) | xilinx-v2017.1 | `92e3dd638b50ad22dd90072673c80d8730903e95` | master             | U-Boot Version 2017.01               |
| QEMU                                                         | [git://github.com/Xilinx/qemu.git](git://github.com/Xilinx/qemu.git) | xilinx-v2017.1 | `45d810957b0f837a5685fbe4bc8d9e3268c1fe64` | master             |                                      |
| Xen                                                          | [git://github.com/Xilinx/xen.git](git://github.com/Xilinx/xen.git) | xilinx-v2017.1 | `ba8ea4d7d843673f494e6cc277f119441ec7f77c` | xilinx/stable-4..8 |                                      |
| ARM-Trusted-Firmware (ATF)                                   | [git://github.com/Xilinx/arm-trusted-firmware.git](git://github.com/Xilinx/arm-trusted-firmware.git) | xilinx-v2017.1 | `7d1a6732c9ae113999aeabcb9912369760d05c13` | master             | ATF is based on upstream version 1.3 |
| Yocto                                                        | [git://github.com/Xilinx/meta-xilinx.git](git://github.com/Xilinx/meta-xilinx.git) |                |                                            |                    |                                      |
| [git://github.com/Xilinx/meta-xilinx-tools.git](git://github.com/Xilinx/meta-xilinx-tools.git) |                                                              |                |                                            |                    |                                      |
| [git://github.com/Xilinx/meta-petalinux.git](git://github.com/Xilinx/meta-petalinux.git) | rel-v2017.1                                                  |                |                                            | Yocto 2.2 Morty    |                                      |
| qemu-devicetrees                                             | [git://github.com/Xilinx/qemu-devicetrees.git](git://github.com/Xilinx/qemu-devicetrees.git) | xilinx-v2017.1 | `294ffabc02d8a3933f7acfb2256489677776af8d` | master             |                                      |
| OpenAMP                                                      | [git://github.com/Xilinx/open-amp.git](git://github.com/Xilinx/open-amp.git) | xilinx-v2017.1 | `d859dc047a93f2ce01d230f6bff0f3236201d9d4` | master             |                                      |
| libmetal                                                     | [git://github.com/Xilinx/libmetal.git](git://github.com/Xilinx/libmetal.git) | xilinx-v2017.1 | `51e08c67556474762257a825fc92cf8dbd30238`  | master             |                                      |
| GCC                                                          | —                                                            | —              | —                                          | —                  | MB compiler version 6.2, ARM 6.2     |

**PetaLinux 2017.1 New Features:**

- For more details please see [(UG1144)](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1144-petalinux-tools-reference-guide.pdf), [(UG1156)](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1156-petalinux-tools-workflow-tutorial.pdf) and [(UG1157)](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1157-petalinux-tools-command-line-guide.pdf).



**PetaLinux**



- Generate a readme for every BSP we deliver that contains the commands used for pre-built image
- Include V4L2 support in PetaLinux
- Vivado 2017.1 OS Support
- Integrate the DFU Utility in PetaLinux to support the USB Slave boot mode in Zynq UltraScale+ MPSoC
- Xen Linux / PetaLinux Documentation
- provide vmlinux image part of prebuild Images , which help customer to debug Linux without having to rebuild.
- petalinux-package --fpga option, please provide default value to point to bitstream in subsystems/linux/hw-description/ or images/linux
- petalinux-boot --qemu supports PMU for Zynq UltraScale+ MPSoC
- Enable lspci utilities default in rootfs
- Use meta-petalinux generated SDK in PetaLinux
- PetaLinux Tools adapt to Yocto Morty (2.2) for 2017.1
- Power Management Firmware Set #1
- Provided BSP for ZCU102 Rev1.0 (or Higher), which will have production silicon. Enabled the DP by default.
- Removed Board DTS generation in PetaLinux reference design builder, and make use of the DTG generated DTS for the same.







**Yocto**



- Upgraded to Yocto 2.2 Morty release





**FSBL**



- FSBL now includes a field that allows a customer to specify an "Operational Key"
- Provision to clear PL irrespective of BOOT.BIN having a bitstream file or not based on user configuration
- 56K chunk of OCM allocated for authentication and decryption of bitstream in secure boot, to make authentication more secure and speed up the boot process
- Support USB boot mode which allows secure and non secure boot using the image in a host machine connected via a DFU cable to the target device
- Support APU only restart
- FSBL code made compliant with MISRA-C norms







**U-boot**



- Non-Processor mode configuration support in AXI_Ethernet Driver in U-Boot.
- Capability to write/modify Boot environment variables in to uenv.txt and save it on SD/eMMC.
- Support for ZCU106 Board
- Mini U-boot for e-mmc flash programming through VDP Tool
- Support 1-bit and 2-bit mode QSPI flash programming
- QSPI flash programming support for Single mode: x1 & x2 and Stacked mode: x1 & x2
- Support for Ethernet to connect via PL to SFP+
- UBIFS file system support for QSPI in U-Boot.
- eMMC HS200 mode support in U-Boot
- Test DFU Util mode in U-Boot (sanity)
- Add encryption and authentication security functionality to U-boot for Zynq UltraScale+ applications
- Support for CG and EG Silicon
- SD 3.0 support in u-boot

**Device-tree**



- DTG to handle static Blob for MPSoC
- Support for Zynq UltraScale+ MPSoC CG family & EG extension devices
- Support for Device Tree Generation for Board Components.





**ARM-Trusted Firmware (ATF)**





- Support for ATF build from SDK
- ARM Trusted Firmware support for CG and EG Silicon







**FreeRTOS**





- All Bare-Metal Libraries must have a counterpart in FreeRTOS
- Updated FreeRTOS release version to the latest in SDK
- Added FreeRTOS support for CG and EG Silicon







**PMU Firmware (PMUFW)**









- PMUFW support for APU Restart
- PMUFW now uses system configuration data exported from the hardware design for PM operations.







**Power Management**











- FPD powered up when coherent mode is enabled for LPD peripherals
- Productization of Isolation Configuration
- OpenAMP dependencies on Power management to start/stop RPU from APU Linux kernel to use power management kernel APIs
- Support for Warm Restart
- Support PMF configuration change by PCW
- Enable Linux Clock Gating of devices/peripherals
- Framework in Linux to control power beyond what is specified in the ATF/PSCI
- Suspend/Resume time requirements from/to Deep Sleep & Power-off
- Created a use case example (RTC wakeup) showing how to switch to deep sleep and periodically wakeup from RTC
- Support Callbacks/Notifications across Master with PMF
- Frequency scaling will be supported
- Wake on Support for all the wake-on support devices including LAN, UART, GPIO and USB







**Standalone**











- Drive PS Peripherals from IP Located in the Programmable Logic (MB on PL drives/accesses PS peripherals).
- Improved documentation for bare metal drivers
- Float support in A53 Bare Metal BSP
- SD/eMMC - Code Cleanup (Bus width changes and HSD, DDR mode support for eMMC, support for enhanced partition)
- Performance Improvements for Bare Metal USB 3.0 driver
- Add DFU Example in USB BareMetal Driver
- Need driver support for SGMII LVDS for the VCU118 board
- Support lwip stack for "PS GEM + PCS PMA in PL" in bare-metal.
- Bare-Metal support for CG and EG Silicon
- Test application generation for tmrctr driver fails
- ATF compliant bare-metal BSP sources for AP
- Deprecate Xil_Kernel 
- Verified that all bare metal libraries can run in EL1 as Xen Guest (QSPI, IPI. LwIP issues)







**Linux Drivers**

- Support Latency configuration for islands during suspend/resume
- CCI enablement in PCW (support added in DTG to export CCI related information into DT nodes)
- Linux Driver for Zynq MPSoC AMS IP in the PS.
- FPGA manager support for Zynq and Zynq UltraScale+ (Full bitstream, nonSecure, Secure)
- FPGA Manager: Provide Support for Secure (Encrypted, Authenticated) Bit steam downloading
- Clock adaptation in all SoftIP Linux drivers including AXII2C, AXIWDT, AXIGPIO, AXI Ethernet, AXIDMA/CDMA/VDMA, AXISPI/QSPI, UartLite, Uartns550
- Test and report all the USB3.0 gadget devices that Linux supports
- SERDES driver Enhancements to access SLCR registers for all clock handling through ATF
- Test and confirm SERDES with all combinations (For example, SATA/DP/Ethernet/USB) in a single system
- Low Power Mode support for SATA
- USB 2.0 OTG Driver
- SDR modes 2 to 5 are failing to capture the read data at 90MHz nand_ref_clk with MAXIMUM SDF corner
- Added SoC revision read mechanism for Zynq MPSoC
- Implement I2C bus recovery Support in Linux driver
- Pin controller driver for Zynq UltraScale+
- Ethernet support for " PS GEM + PCS PMA in PL" in Linux
- USB 3.0 drivers should be tuned to get best performance (min 2Gbps)
- Support UBIFS file system in all QSPI flash configuration modes (Single, Dual Parallel, Dual stacked)
- I2C Slave functionality needs to be added in I2C Linux driver.
- 2.5G Ethernet Linux Drivers
- Linux Kernel support for CG and EG Silicon
- 10G Ethernet Linux driver for control and data plane with 1588 (Uses 10G/25G Ethernet subsystem)
- Extend DisplayPipe DRM driver to support UYVY formats and switch between YUYV and UYVY formats run time

**Known Issues for 2017.1:
**

| Linux/Standalone | Application | Description                                                  | Work-around                                                  | To be fixed version |
| :--------------- | :---------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :------------------ |
| Standalone       | FSBL        | 2017.1 Zynq UltraScale+ MPSoC: xilpm library fails to build  | [Xilinx Answer 69108](https://adaptivesupport.amd.com/s/article/69108) | 2017.2              |
| Standalone       | PMUFW       | 2017.1 Zynq UltraScale+ MPSoC: PMUFW does not apply appropriate access controls to MMIO calls | [Xilinx Answer 69109](https://adaptivesupport.amd.com/s/article/69109) | 2017.2              |
| Standalone       | PMUFW       | 2017.1 Zynq UltraScale+ MPSoC: PMUFW fails to detect and acknowledge XMPU/XPPU errors | [Xilinx Answer 69110](https://adaptivesupport.amd.com/s/article/69110) | 2017.2              |
| Standalone       | PMUFW       | 2017.1 - 2016.3/4 Zynq UltraScale+ MPSoC: PMUFW will enable AIB (if existing) to isolate powered down components | [Xilinx Answer 68003](https://adaptivesupport.amd.com/s/article/68003) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: PetaLinux Correct suspend/resume calls to work when FPD is off | [Xilinx Answer 69100](https://adaptivesupport.amd.com/s/article/69100) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: Linux Power Management Ethernet does not work after suspend-resume cycle | [Xilinx Answer 69101](https://adaptivesupport.amd.com/s/article/69101) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: Linux OpenAMP remoteproc "failed to declare rproc mem as DMA mem" | [Xilinx Answer 69114](https://adaptivesupport.amd.com/s/article/69114) | 2017.2              |
| Linux            | PetaLinux   | 2016.4/2017.1 PetaLinux: Static IP assignment in PetaLinux menu config "Subsystem AUTO Hardware Settings" not working | [Xilinx Answer 69119](https://adaptivesupport.amd.com/s/article/69119) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: petalinux-package command generated BOOT.BIN is not loading kernel image from QSPI | [Xilinx Answer 69111](https://adaptivesupport.amd.com/s/article/69111) | 2017.2              |
| Linux            | PetaLinux   | 2016.4/2017.1 MicroBlaze: PetaLinux ssh command failed to connect to MicroBlaze boards from host machine | [Xilinx Answer 69121](https://adaptivesupport.amd.com/s/article/69121) | 2017.2              |
| Linux            | PetaLinux   | 2016.4/2017.1 PetaLinux: Firmware Version Configuration not updated in the Linux image | [Xilinx Answer 69122](https://adaptivesupport.amd.com/s/article/69122) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 PetaLinux: XSDK crashes when running petalinux-build  | [Xilinx Answer 69104](https://adaptivesupport.amd.com/s/article/69104) | 2017.2              |
| Linux            | PetaLinux   | 2016.4 PetaLinux : Build (petalinux-build) failure when using ddr3 in the Kintex design | [Xilinx Answer 69106](https://adaptivesupport.amd.com/s/article/69106) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 PetaLinux: Xen images built by PetaLinux do not work as expected | [Xilinx Answer 69105](https://adaptivesupport.amd.com/s/article/69105) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 PetaLinux: Zynq UltraScale+ MPSoC lacks addressing for high-order DRAM | [Xilinx Answer 69117](https://adaptivesupport.amd.com/s/article/69117) | 2017.2              |
| Linux            | PetaLinux   | 2016.4/2017.1 PetaLinux: sysroot build errors during migration from 2016.3 version to 2016.4/2017.1 version | [Xilinx Answer 69124](https://adaptivesupport.amd.com/s/article/69124) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: PetaLinux fails to build and configure U-Boot | [Xilinx Answer 69112](https://adaptivesupport.amd.com/s/article/69112) | 2017.2              |
| Linux            | Device-tree | 2017.1 Zynq UltraScale+ MPSoC: PetaLinux menuconfig changing UART device settings does not change UART device number in device-tree | [Xilinx Answer 69126](https://adaptivesupport.amd.com/s/article/69126) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 MicroBlaze: PetaLinux includes MicroBlaze design or IP details in README. | [Xilinx Answer 69118](https://adaptivesupport.amd.com/s/article/69118) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: PetaLinux fails to build uboot with UBIFS file system support for QSPI | [Xilinx Answer 69113](https://adaptivesupport.amd.com/s/article/69113) | 2017.2              |
| Linux            | U-Boot      | 2017.1 U-Boot: spi_flash_probe_bus_cs() failed with QEMU     | [Xilinx Answer 69103](https://adaptivesupport.amd.com/s/article/69103) | 2017.2              |
| Linux            | OpenAMP     | 2017.1 Zynq UltraScale+ MPSoC: OpenAMP applications dependency on UART serial console | [Xilinx Answer 69115](https://adaptivesupport.amd.com/s/article/69115) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: Linux no V4L2 pixel format for RBG888 | [Xilinx Answer 69127](https://adaptivesupport.amd.com/s/article/69127) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: Linux Display does not show terminal logs after resume from FPD off | [Xilinx Answer 69129](https://adaptivesupport.amd.com/s/article/69129) | 2017.2              |
| Standalone       | Libraries   | v2.0 - xilfpga - Xilfpga library fails to load the Authenticated bit stream because of wrong check in XFpga_PL_BitSream_Load() | [Xilinx Answer 69125](https://adaptivesupport.amd.com/s/article/69125) | 2017.2              |
| Linux            | PetaLinux   | 2017.1 PetaLinux: Issue with USB2.0 UVC-gadget application on Zynq UltraScale+ MPSoC | [Xilinx Answer 69102](https://adaptivesupport.amd.com/s/article/69102) | 2017.2              |
| Standalone       | FSBL        | Zynq UltraScale+ MPSoC - SGMII using PS-GTR - Why is the Zynq MP PHY driver reconfiguring the lanes previously set up for SGMII by the FSBL? | [Xilinx Answer 68866](https://adaptivesupport.amd.com/s/article/68866) | None                |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: Linux MACB MDIO support for single MAC managing multiple PHYs | [Xilinx Answer 69132](https://adaptivesupport.amd.com/s/article/69132) | 2017.2              |
| Linux            | Device-tree | 2017.1/2 Zynq UltraScale+ MPSoC: Linux hangs when accessing PL peripheral generated by yocto | [Xilinx Answer 69587](https://adaptivesupport.amd.com/s/article/69587) | 2018.1              |
| Linux            | XSDK        | 2017.1-2017.3 Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle | [Xilinx Answer 69143](https://adaptivesupport.amd.com/s/article/69143) | 2017.4              |