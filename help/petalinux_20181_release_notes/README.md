# 70896 - PetaLinux 2018.1 - Product Update Release Notes and Known Issues

## Title

70896 - PetaLinux 2018.1 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2018.1 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for the 2018.1 PetaLinux Release**

This table contains supported BSPs for Zynq-7000, MicroBlaze, Zynq UltraScale+ MPSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/sdx-development-environments.html).

| Platform               | Variant                   | BSP Name                   |
| ---------------------- | ------------------------- | -------------------------- |
| Zynq-7000              | ZC702                     | ZC702 BSP                  |
| Zynq-7000              | ZC706                     | ZC706 BSP                  |
| Zynq-7000              | ZEDBOARD                  | ZED BSP                    |
| MicroBlaze             | AC701                     | AC701 BSP                  |
| MicroBlaze             | KCU105                    | KCU105                     |
| MicroBlaze             | KC705                     | KC705 BSP                  |
| Zynq UltraScale+ MPSoC | ZCU102 production silicon | ZCU102 BSP (prod-silicon)  |
| Zynq UltraScale+ MPSoC | ZCU102 ZU9 ES2 Rev 1.0    | ZCU102 ZU9 ES2 Rev 1.0 BSP |
| Zynq UltraScale+ MPSoC | ZCU104 production silicon | ZCU104 BSP                 |
| Zynq UltraScale+ MPSoC | ZCU106 production silicon | ZCU106 BSP                 |

**Note**: The "[sstate cache file](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate-rel-v2018.1.tar.gz&akdm=1)" (sstate-rel-v2018.1.tar.gz) can be found on the Xilinx download area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2018.1_README&akdm=0) (sstate_rel_2018.1_README) file that outlines the procedure to use "sstate cache".

Refer to the attached file "2018.1_PetaLinux_Packages_List" for software package versions tested on host machines, which is required for PetaLinux installation tools.

See also the attached README.

**PetaLinux 2018.1 contains the following build collateral:**

| Component                  | Git repo                                                     | Git Branches      | Git Tags                 | Commit ID                                                    | Comments                                                     |
| -------------------------- | ------------------------------------------------------------ | ----------------- | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| FSBL                       | [git://github.com/Xilinx/embeddedsw.git](http://github.com/Xilinx/embeddedsw.git) | master            | xilinx-v2018.1           | aaa566bc3fa19255de4d434ebfa57ae3a9d261b2                     | FSBL for Zynq 7000: `embeddedsw/lib/sw_apps/zynq_fsbl`<br>FSBL for Zynq UltraScale+: `embeddedsw/lib/sw_apps/zynqmp_fsbl` |
| PMU Firmware               | [git://github.com/Xilinx/embeddedsw.git](http://github.com/Xilinx/embeddedsw.git) | master            | xilinx-v2018.1           | aaa566bc3fa19255de4d434ebfa57ae3a9d261b2                     | PMU for Zynq UltraScale+: `embeddedsw/lib/sw-apps/zynqmp_pmufw` |
| Device-tree                | [git://github.com/Xilinx/device-tree-xlnx.git](http://github.com/Xilinx/device-tree-xlnx.git) | master            | xilinx-v2018.1           | 682c126ef65f1bac3f853f6158a5b37109cdad94                     |                                                              |
| Linux                      | [git://github.com/Xilinx/linux-xlnx.git](http://github.com/Xilinx/linux-xlnx.git) | xlnx_rebase_v4.14 | xlnx_rebase_v4.14_2018.1 | 4ac76ffacb54712b0361e51d0b7156e53d062e3c                     | Linux Kernel rebase version 4.14                             |
| U-Boot                     | [git://github.com/Xilinx/u-boot-xlnx.git](http://github.com/Xilinx/u-boot-xlnx.git) | master            | xilinx-v2018.1           | 1c81b42a326e5b74a5b79e55de9c52b5781b7a8a                     | U-Boot Version v2018.01                                      |
| QEMU                       | [git://github.com/Xilinx/qemu.git](http://github.com/Xilinx/qemu.git) | master            | xilinx-v2018.1           | 1d5516986ea296d91a599ac23252e302a4003914                     |                                                              |
| Xen                        | [git://github.com/Xilinx/xen.git](http://github.com/Xilinx/xen.git) | xilinx/stable-4.9 | xilinx-v2018.1           | c227fe68589bdfb36b85f7b78c034a40c95b9a30                     |                                                              |
| ARM-Trusted-Firmware (ATF) | [git://github.com/Xilinx/arm-trusted-firmware.git](http://github.com/Xilinx/arm-trusted-firmware.git) |                   | xilinx-v2018.1           | df4a7e97d57494c7d79de51b1e0e450d982cea98                     | ATF is based on upstream version 1.4                         |
| Yocto                      | [meta-xilinx](http://github.com/Xilinx/meta-xilinx.git)<br>[meta-xilinx-tools](http://github.com/Xilinx/meta-xilinx-tools.git)<br>[meta-petalinux](http://github.com/Xilinx/meta-petalinux.git) | rel-v2018.1       | No Tags                  | e7a6531bd8fc9ce5797be082c8478a2701c3766a<br>93d6b87bdc451ee81d6d716809e0d7e9bc3b7021<br>4e84d60865bf505d1ea425f3e5c84e37bf8f7455 | Yocto 2.4.1 Rocko                                            |
| qemu-devicetrees           | [git://github.com/Xilinx/qemu-devicetrees.git](http://github.com/Xilinx/qemu-devicetrees.git) | master            | xilinx-v2018.1           | d5017f8119b6493d8b2fcdfd5caa4e8b16580877                     |                                                              |
| OpenAMP                    | [git://github.com/Xilinx/open-amp.git](http://github.com/Xilinx/open-amp.git) | master            | xilinx-v2018.1           | 7f2d8ca88d643a9cec993add93d1630b2c7bd41e                     |                                                              |
| libmetal                   | [git://github.com/Xilinx/libmetal.git](http://github.com/Xilinx/libmetal.git) | master            | xilinx-v2018.1           | 18048c4144f276cda793c125399057a6b5773edb                     |                                                              |
| VCU OpenMax IL             | [git://github.com/Xilinx/vcu-omx-il.git](http://github.com/Xilinx/vcu-omx-il.git) | master            | xilinx-v2018.1           | 68e385ace99ab699feaa50f24b7a78680c411f75                     |                                                              |
| VCU Control Software       | [git://github.com/Xilinx/vcu-ctrl-sw.git](http://github.com/Xilinx/vcu-ctrl-sw.git) | master            | xilinx-v2018.1           | aa4b6871346c915f28a069190afec5d30963762f                     |                                                              |
| VCU Firmware               | [git://github.com/Xilinx/vcu-firmware.git](http://github.com/Xilinx/vcu-firmware.git) | master            | xilinx-v2018.1           | 7c6f282da07253c1987665846ed676059925ef40                     |                                                              |
| VCU Modules                | [git://github.com/Xilinx/vcu-modules.git](http://github.com/Xilinx/vcu-modules.git) | master            | xilinx-v2018.1           | 646185390cc1850969c0fa3db59fc8f0e511922e                     |                                                              |
| GStreamer OpenMax IL       | [git://github.com/Xilinx/gst-omx.git](http://github.com/Xilinx/gst-omx.git) | xilinx-master     | xilinx-v2018.1           | 35e719b29e757a1592a4d76d5480c21356d88d3c                     |                                                              |
| GStreamer Plugins-Base     | [git://github.com/Xilinx/gst-plugins-base.git](http://github.com/Xilinx/gst-plugins-base.git) | master-rel-1.12.2 | xilinx-v2018.1           | 244ba6f2ad1915f6b9f62f8d8e8efbce1cf10ebb                     |                                                              |
| GStreamer Plugins-Bad      | [git://github.com/Xilinx/gst-plugins-bad.git](http://github.com/Xilinx/gst-plugins-bad.git) | master-rel-1.12.2 | xilinx-v2018.1           | 995c899ca8668aa392851290aea9b779ff2b66bc                     |                                                              |
| GStreamer Plugins-Good     | [git://github.com/Xilinx/gst-plugins-good.git](http://github.com/Xilinx/gst-plugins-good.git) | master-rel-1.12.2 | xilinx-v2018.1           | d7cac4c10e6365e5cc3ea06edb6646533fd5ce2c                     |                                                              |
| GCC                        |                                                              |                   |                          |                                                              | MB compiler version 7.2 ARM 7.2                              |

**Wiki Updates:**

Covers details for Linux Kernel, Device drivers, U-boot, ATF and DTG changes (new features/fixes) in a particular release.

**2018.1 FSBL release notes wiki page:**

http://www.wiki.xilinx.com/FSBL

**2018.1 PMUFW release notes wiki page:**

http://www.wiki.xilinx.com/PMU+Firmware

**2018.1 ATF release notes wiki page:**

[http://www.wiki.xilinx.com/2018.1+ATF+Release+Notes ](http://www.wiki.xilinx.com/2018.1+ATF+Release+Notes)

**2018.1 U-Boot release notes wiki page:**

 [http://www.wiki.xilinx.com/2018.1%20u-boot%20release%20notes](http://www.wiki.xilinx.com/2018.1 u-boot release notes)

**2018.1 Linux and DTG release notes wiki page:**

 [http://www.wiki.xilinx.com/2018.1%20Linux%20and%20DTG%20Release%20Notes](http://www.wiki.xilinx.com/2018.1 Linux and DTG Release Notes)

**2018.1 Power Management release notes wiki page:**

 [http://www.wiki.xilinx.com/Zynq+UltraScale%EF%BC%8B+MPSoC+Power+Management](http://www.wiki.xilinx.com/Zynq+UltraScale＋+MPSoC+Power+Management)

**2018.1 Baremetal Drives and Libraries release notes wiki page:**

 http://www.wiki.xilinx.com/Baremetal+Drivers+and+Libraries

**2018.1 OpenAMP release notes wiki page:**

 http://www.wiki.xilinx.com/OpenAMP+2018.1

**2018.1 QEMU release notes wiki page:**

[http://www.wiki.xilinx.com/OpenAMP+2018.1](http://www.wiki.xilinx.com/QEMU)

**2018.1 VCU release notes wiki page:**

 http://www.wiki.xilinx.com/Xilinx+Video+Codec+Unit

 **2018.1 New Features:**

 **PetaLinux**

- PetaLinux tool enhanced to use Rocko release (2.4.1).
- PetaLinux BSPs for ZCU104 and ZCU106 for Production boards and Silicon are added now.
- PetaLinux tool package groups are regrouped to be more user-friendly.
- PetaLinux tool enhanced to provide sysroot as PetaLinux build product.

**Yocto**

- Yocto updated to Rocko release (2.4.1) 
- Supported Linux Distribution RHEL 7.x, Centos-7.x, and Ubuntu-16.04 
- Update recipe Linux-xlnx kernel version 4.14
- Update recipe Arm trusted firmware version 1.4
- Update recipe U-boot-xlnx version v2018.01
- Update recipe Xen version 4.9
- Update recipe QEMU version v2.11.0
- Support for meta-browser layer
- Added support for ZCU106, ZCU104, ZC254, ZC1275, ZCU111 evaluation boards
- Change xilinx-bootbin from a class to a bb recipe:
  This helps in easy overrides using bbappends and using PREFERRED_PROVIDER for bootbin generation
- device-tree.bbappend: device-tree-generation recipe is removed and replaced with device-tree.bbappend, device-tree recipe is available in the meta-xilinx layer, this just extends the recipe to use DTG.
- Add DTG hooks for all new evaluation boards ZCU111, ZCU106, ZCU104, ZC1254, ZC1275

**FSBL**

- Added support for NIST-SHA3 padding
- Added Boot header authentication
- Forcing encryption for all partitions when ENC_ONLY eFUSE bit is set
- Fixed AES KEY and IV re-use vulnerability issue
- Added support to exclude partition loading
- Added warning prints in case PMU-FW is not running
- Added support for Macronix 1.8V flash
- Added support to make FSBL wait for PMU to detect boot type
- Added support to make FSBL indicate boot type detection to PMUFW
- Isolation fully enabled in FSBL

**U-boot**

- Upgraded to mainline version v2018.01
- Added Fixed link Ethernet feature support for Zynq UltraScale+.
- Added support for authentication and decryption of secure Images using the new u-boot command "zynqmp secure". For more details use help for the zynqmp command.
- Added support for authentication and decryption of secure bitstreams by fixing the security vulnerabilities with the previous version. For more details use help for the "fpga loads" command.
- Added support for QSPI parts IS25LP256D, IS25WP256D for Zynq and Zynq UltraScale+.
- Support for parallel NOR flash devices MT28EW 128 and 256 for Zynq.
- Added support for MT25QL02G and MT25QU02G for Zynq

**Device-tree Generator (DTG)**

- Clock support in the DTG
- TSN IP driver support
- Added the placeholder comment for generic drivers
- Added support for the interrupt name property

**ARM-Trusted Firmware (ATF)**

- Upgraded to mainline v1.4. Also consists of patches for spectra meltdown.
- Added new APIs and functionalities to handle platform management functionalities Query platform data, Clock control, Pin control and ioctl.
- Changed PL bitstream loading to blocking call to PMUFW. This means a response will not be sent to upper layers until it is received from the PMUFW.
- Added a new PM API for handling secure images.
- Changed the behavior to build ATF with the DEBUG option to DDR (0x1000-0x80000) instead of OCM earlier.
- Added an SMC call to provide ATF PM module version
- Replaced IPI interrupt with TTC3_0 interrupt to register a WDT restart event

**PMU Firmware (PMUFW)**

- Using CSU WDT for PMU fail-safe mechanism instead of LPD WDT
- Implemented idle hooks for nodes USB, DP, and SATA
- Added support for graceful forcepowerdown of PU to prevent any mid-flightaxi transactions from locking up the interconnect and hanging the device.
- Added wake on USB support to wake up all masters for which USB is set as a wakeup source
- Corrected the timeout logic in node idling functions
- Separated FPD and PLD power supply check hooks to increase FPD power up delay to 40ms (this is the maximum ramp up time for FPD power rails)
- Added GPO section to config object to get the initial state of PMU GPO's and configure them in the PMU Firmware
- Using TTC instead of IPI interrupt from PMU to interrupt APU upon WDT event
- Added all builds flags to xpfw_config.h file so that the user can enable/disable any functionality from this config file
- Added misc folder to PMU Firmware
- Added modularity of xilfpga and xilsecure features using compiler switches
- Skip FPD power down when debugger is connected
- Added Power Off Suspend to RAM feature
- Use IPI-1 for callbacks/communication initiated by PMU Firmware to other masters
- Updated PM version to 1.0 to match with EEMI API version
- Added support for resetting GPIO5 resets going to PL
- Keeping OCM bank3 ON during suspend if wake on LAN is set
- Added API to support secure single partition image
- Sending PL_INIT status in PmGetChipid API response to indicate PL EFUSE is loaded into EFUSE IPDISABLE or not
- Polling for acknowledgment from AIB after isolation is enabled when power domain or island is powered down
- Checking all access regions present in pmAccessTable to find valid permissions for MMIO read and write calls
- Updated PM API IDs list in PMU Firmware with the new API IDs implemented n EEMI
- Updated xilfpga API calls in PMU Firmware with the latest version of xilfpga library

**Linux Kernel and Drivers**

- Linux kernel
  - Upgrade to 4.14
- Ethernet driver (GEM)
  - Add WOL support for ZynqMP
  - Use mainline implementation of 64 bit addressing
- AXI Ethernet Driver
  - Add support for USXGMII
- PM driver
  - Replaced old PM driver (drivers/soc/xilinx/zynqmp/pm.c) with new driver (drivers/soc/xilinx/zynqmp/power.c).
    Power.c now only contains power management related functions. Earlier pm.c had some platform management functions which are now moved to firmware interface.
  - Power Management driver now uses mailbox for receiving PM callbacks from firmware instead of registering IPI interrupt handler.
  - Changed Sysfs/debugfs paths and their usage\
  - Change in device tree bindings
  - Removed "xlnx,zynqmp-pm" binding and replaced with new binding("xlnx,zynqmp-power") for power management driver
  - Replaced IPI interrupt properties with mailbox properties
- Firmware driver
  - Replaced old firmware interface (drivers/soc/xilinx/zynqmp/firmware.c) with new firmware interface (drivers/firmware/xilinx/zynqmp/*)
  - Extracted firmware interface part from old PM driver (drivers/soc/xilinx/zynqmp/pm.c) to firmware driver.
  - Removed MMIO interface
  - Added sysfs to set shutdown scope
  - Extracted firmware related property from old PM binding and created separate DT binding for ZynqMP firmware ("xlnx,zynqmp-firmware")
- Pin control driver
  - Request pin information from firmware instead of registering hard coded pin information in driver
  - Use firmware interface APIs to control/configure pins
  - Change in device tree binding - Removed "xlnx,pinctrl-zynqmp" binding and replaced with new "xlnx,zynqmp-pinctrl" binding
- Common Clock Framework
  - Request clock information from firmware instead of registering hard coded clocks in driver
  - Use firmware APIs to control clocks
  - Change in device tree binding - Removed "xlnx,zynqmp-clkc" binding and replaced with new "xlnx,zynqmp-clk" binding
- SHA/RSA/QSPI/ZynqMP Serdes/GT/Tap Delay /FPGA Manager/ZynqMP PL programming/ Nvmem- SoC revision read mechanism/ZynqMP R5 remoteproc driver/ ZynqMP power domain driver/Reset-Controller  
  - Replaced MMIO read/write with new firmware APIs
- Display Port
  - Switched to restructured DRM driver:
  - https://github.com/Xilinx/linux-xlnx/tree/master/drivers/gpu/drm/xlnx
  - Support atomic modesetting
  - Support 10bit formats
  - Additional soft IP drivers

**OpenAMP and Libmetal**

- RPMsg and Remoteproc drivers work with 4.14 kernel
- internal support for OpenAMP demo to use upstream RPMsg char driver
- Added support for MicroBlaze platform in libmetal

**QEMU** 

- Updated QEMU to mainline v2.11.1
- Merged new Register API model
- Add MMIO execution for QSPI (Linear mode)
- QSPI support added for mainline board xlnx-zcu102
- Added ZynqMP RTC
- Enabled MTTCG support
- Enable syncs for non-icount runs

**VCU**

- Dynamic Bitrate support
- Dynamic GOP support, this includes
  - Adding Key Frames (IDR) on request
  - Changing number of B frames in the GOP
  - Changing GOP length based on request
- Region of Interest based Encoding
- Sub-frame latency support for encoder/decoder
- 422/420 10bit support at Gstreamer level
- Encoder/Decoder flush related fixes

**XEN** 

- Merged with Stable-4.9 version
- Added new EEMI api IDs
- Support 64 bit smc calls
- Add platform_hvc
- Handles guest SMC calls (as well as HVC calls) in a platform specific way

**FreeRTOS** 

- Upgraded FreeRTOS kernel version to 10.0
- Updated FreeRTOS Tcl to fix bug in detecting latest standalone version.
- Export platform macros to xparameters.h based on processor.
- Added interrupt handler APIs for A9, A53, R5.
- Added support for ttc in MicroBlaze systems
- Fixed compilation warnings related to interrupt handling APIs
- Add new software applications for LWIP TCP/UDP performance tests: freertos_lwip_tcp_perf_client and freertos_lwip_tcp_perf_server, freertos_lwip_udp_perf_client and freertos_lwip_udp_perf_server.

**Power Management** 

- "Hello PM" out-of-box demo
- Wake-up on USB and LAN.
- Suspend with full chip power off.

**Baremetal Drivers and Libraries**

- rfdc_v3_2:
  - Add XRFdc_SetInterpolationFactor() and XRFdc_SetDecimationFactor() APIs.
  - Add CoarseMixMode field in mixer settings.
  - Add XRFdc_SetCalibrationMode() and XRFdc_GetCalibrationMode() APIs for calibration modes switch.
  - Add XRFdc_DynamicPLLConfig() API for PLL and external clock switch support.
  - Add XRFdc_GetClockSource() API to get clock source.
  - Add XRFdc_GetPLLLockStatus() API to get PLL lock status.
  - Add XRFdc_GetDriverVersion() API to get the driver version.
  - Add XRFdc_MultiConverter_Sync() and XRFdc_MultiConverter_Init() APIs to support Multi-Tile Sync.
  - Updated Set/Get Interpolation/Decimation factor APIs to consider the actual factor.
  - Add XRFdc_SetInvSincFIR() and XRFdc_GetInvSincFIR() APIs to support inverse-sinc.
  - Add XRFdc_MultiBand() and XRFdc_SetSignalFlow() APIs to configure Multiband and Singleband.
  - Update PLL structure in XRFdc_DynamicPLLConfig() API.
  - Update ADC and DAC datatypes in Mixer API and use input datatype for ADC in threshold and QMC APIs.
  - Removed FIFO disable check in DDC and DUC APIs.
  - Support for Marker event source for DAC block.
  - Fixed DAC latency calculation in MTS.
  - Support for reloading DTC scans.
  - Option to configure sysref capture after MTS.
  - Update XRFdc_SetPLLConfig() API to correct PLL settings(PLL_CRS1, PLL_LPF1, PLL_CRS2).
- qspipsu_v1_7:
  - Removed unsupported 4 byte write and sector erase commands.
  - Support for MT25QL02G flash from Micron
  - Support for S25FL064L flash from Spansion
  - Support for MX66U1G45G flash from Macronix
  - Removed the check for writing the data to DMA MSB.
  - API in driver to toggle the WP pin of the flash.
  - Added write protect example.
  - Support in EL1 non-secure mode.
  - In dual parallel mode enable both CS when issuing write enable command.
- standalone_v6_6:
  - Updated cortexa9/xil_errata.h and cortexa9/xil_cache.c to remove errata 753970
  - Export platform macros to bspconfig.h based on processor.
  - Updated sleep routines to support user configurable sleep implementation. Now sleep routines will use TTC instance specified by user
  - Added a macro to replace conditional loops
  - Fixed the compilation warning in A53
  - Made changes to ensure that for A9/Zynq, C stack information is flushed out from L1 D cache or L2 cache only when the respective caches are enabled.
  - Updated asm_vectors.S and boot.S in Cortexa53 64 bit BSP, to add isb after writing to cpacr_el1/cptr_el3 registers. It would ensure disabling/enabling of floating-point unit, before any subsequent instruction.
  - Updated get_connected_if proc in standalone Tcl to detect the HPC port configured with smart interconnect.
  - Updated the csu_wdt interupt to the correct value.
  - Fix for heap handling in ARM platforms.
  - Updated Xil_DCacheInvalidateRange and Xil_ICacheInvalidateRange APIs in Cortexa53 64 bit BSP, to fix a bug in handling upper DDR addresses.
  - Updated makefile of Cortexa53 32bit BSP to add includes_ps directory in the list of include paths. This change allows applications/BSP files to include .h files in include_ps directory.
  - Updated Cortex R5 BSP to add new mld parameter "lockstep_mode_debug", to enable/disable debug logic in non-JTAG boot mode, when processor is in lockstep configuration.
    By default, value of this parameter is "false" and debug logic would be disabled. It can be enabled through BSP setting by changing value of "lockstep_mode_debug" as "true".
  - By default CPUACTLR_EL1 is accessible only from EL3, it results into abort if accessed from EL1 non secure privilege level.
  - Updated Xil_ConfigureL1Prefetch function in Cortexa53 64 bit BSP to avoid CPUACTLR_EL1 access from privilege levels other than EL3.
  - Updated hypervisor enabled BSP to use PV console, based on the XEN_USE_PV_CONSOLE flag. By default hypervisor enabled BSP would use UART console, PV console can be enabled by appending "-DXEN_USE_PV_CONSOLE" to the BSP extra compiler flags.
- libmetal_v1_4:
  - Sync libmetal OSS project with upstream
- libmetal_demo:
  - Update to work with updated libmetal lib
- openamp_v1.5:
  - Sync openamp OSS project with upstream
    - openamp_rpc_demo:
    - openamp_matrix_multiply_demo:
    - openamp_echo_test
    - Update to work with updated openamp and libmetal libs
- xilfpga_v4_0:
  - Added the following Secure features to the xilfpga library.
  - Authenticated Bitstream loading using DDR.
  - Authenticated Bitstream loading Using OCM.
  - Authenticated + Encrypted Bitstream loading Using DDR with User-key.
  - Authenticated + Encrypted Bitstream Loading Using OCM with Device-key.
  - Authenticated + Encrypted + Key rolling Bitstream loading Using DDR with User-key.
  - Authenticated + Encrypted + Key rolling Bitstream loading Using DDR with Device-key.
  - Authenticated + Encrypted + Key rolling Bitstream Loading Using OCM with User-key.
  - Authenticated + Encrypted + Key rolling Bitstream Loading Using OCM with Device-key
  - For this version onwards we are not stripping the Header for Both Secure and Non-Secure Bitstream Images.
    As a result, the entry point interface will be changed as follows : u32 XFpga_PL_BitSream_Load (UINTPTR WrAddr, UINTPTR KeyAddr, u32 flags);
  - Added the legacy bit file loading feature support from U-boot.
  - Improved the error handling support by returning the proper ERROR value upon error conditions.
- xilrsa_v1_5:
  - Added description in mld
- xilsecure_v3_0:
  - Added support for NIST-SHA3 padding
  - Added API to make KECCAK/NIST(default)padding selection
  - Added AES and KUP key clear call after decryption
  - Modified XSecure_AesDecrypt() to use key in Secure header
  - Added APIs to load secure single partition image
- xilskey_v6_4:
  - Corrected status bits for UltraScale+
  - Added support for Virtex UltraScale and UltraScale+
  - Cache is being re-loaded by library after programming eFUSE bits in ZynqMP
- xxvethernet_v1_0:
  - Added new driver for XXV Ethernet IP
  - Support for USXGMII IP

**Known Issues for 2018.1:**

| Linux/Baremetal | Components       | Description                                                  | Work-around                                                  | To be fixed version |
| --------------- | ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------- |
| Linux           | Yocto/PetaLinux  | 2018.x Yocto/PetaLinux: Ubuntu 18.04.x LTS support           | [Xilinx Answer 71448](https://adaptivesupport.amd.com/s/article/71448) |                     |
| Linux           | PetaLinux        | Zynq UltraScale+ MPSoC: How to enable UHS (SD 3.0) support for ZCU102 and ZCU106 evaluation board PetaLinux BSPs | [Xilinx Answer 69978](https://adaptivesupport.amd.com/s/article/69978) |                     |
| Linux           | XSDK             | 2017.x-2018.1 Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle | [Xilinx Answer 69143](https://adaptivesupport.amd.com/s/article/69143) |                     |
| Linux           | Yocto, PetaLinux | 2018.1 Zynq UltraScale+ MPSoC: Yocto or PetaLinux throws warnings when the build do_rootfs task completes | [Xilinx Answer 71110](https://adaptivesupport.amd.com/s/article/71110) |                     |
| Linux           | Drivers          | 2018.1 Zynq UltraScale+ MPSoC: PetaLinux Warm-Restart BSP fails to wakeup Ethernet when FPD is off | [Xilinx Answer 71028](https://adaptivesupport.amd.com/s/article/71028) | 2018.2              |
| Baremetal       | FSBL             | 2018.1 Zynq UltraScale+ MPSoC: FSBL R5 application does not work with default isolation enabled. | [Xilinx Answer 71015](https://adaptivesupport.amd.com/s/article/71015) | 2018.2              |
| Linux           | XEN              | 2018.1 Zynq UltraScale+ MPSoC: XEN boot fails with pre-built images for ZCU106 PetaLinux BSP | [Xilinx Answer 70956](https://adaptivesupport.amd.com/s/article/70956) | 2018.2              |
| Linux           | VCU-GStreamer    | 2018.1 Zynq UltraScale+ MPSoC VCU: Frame drops are observed with 4kp60fps live source gstreamer pipeline in Linux | [Xilinx Answer 70959](https://adaptivesupport.amd.com/s/article/70959) | 2018.2              |
| Linux           | VCU              | 2018.1 Zynq UltraScale+ MPSoC VCU - Why does the VCU MCU throw an exception when using multiple streams and Low Latency mode? | [Xilinx Answer 71020](https://adaptivesupport.amd.com/s/article/71020) | 2018.2              |
| Linux           | VCU-GStreamer    | 2018.1 Zynq UltraScale+ MPSoC VCU: Why do I see frame drops at bitrates > 500Mbps when using GStreamer? | [Xilinx Answer 71021](https://adaptivesupport.amd.com/s/article/71021) | 2018.2              |
| Linux           | Drivers          | 2018.1 Zynq UltraScale+ MPSoC: Linux 4.14 driver always assumes that the Display Port (GTR's) output will be used | [Xilinx Answer 71043](https://adaptivesupport.amd.com/s/article/71043) | 2018.2              |
| Linux           | Drivers          | 2018.1 Zynq UltraScale+ MPSoC: Linux 4.14 driver does not support both PL live input and DP DMA input at the same time | [Xilinx Answer 71044](https://adaptivesupport.amd.com/s/article/71044) | 2018.2              |
| Linux           | Device-tree      | 2017.3-2018.1 Zynq UltraScale+ MPSoC: DMA/AXI Bridge for PCI Express Subsystem - Bridge Root Port mode - pcie-xdma-pl driver - AXIBAR0 configured in upper address space will result in incomplete S_AXIB transactions | [Xilinx Answer 71045](https://adaptivesupport.amd.com/s/article/71045) | 2018.2              |
| Linux           | PMUFW            | 2018.1 Zynq UltraScale+ MPSoC - PMUFW: Reboot fails after Power On Suspend wakeup | [Xilinx Answer 71025](https://adaptivesupport.amd.com/s/article/71025) | 2018.2              |
| Baremetal       | OpenAMP          | 2018.1 Zynq UltraScale+ MPSoC: OpenAMP FreeRTOS application changes in embeddedsw | [Xilinx Answer 71038](https://adaptivesupport.amd.com/s/article/71038) | 2018.2              |
| Linux           | Libmetal         | 2018.1 Zynq UltraScale+ MPSoC: Libmetal HAS_XINTC check removed from cmake/options.cmake file | [Xilinx Answer 71037](https://adaptivesupport.amd.com/s/article/71037) | 2018.2              |
| Linux           | OpenAMP          | 2018.1 Zynq UltraScale+ MPSoC: OpenAMP example DTSI has a incorrect address symbol in reserved memory | [Xilinx Answer 71047](https://adaptivesupport.amd.com/s/article/71047) | 2018.2              |
| Linux           | Device-tree      | 2018.1 Zynq UltraScale+ MPSoC: OpenAMP source device-tree file name has incorrect naming convention. | [Xilinx Answer 71048](https://adaptivesupport.amd.com/s/article/71048) | 2018.2              |
| Linux           | PetaLinux        | 2016.4-2018.1 PetaLinux: Kernel configurations dependencies are not pulled properly when we use external source with kernel | [Xilinx Answer 71102](https://adaptivesupport.amd.com/s/article/71102) | 2018.2              |
| Linux           | Device-tree      | 2018.1 Zynq UltraScale+ MPSoC: Linux 10G/25G Ethernet Subsystem design does not build with device-tree | [Xilinx Answer 71136](https://adaptivesupport.amd.com/s/article/71136) | 2018.2              |
| Linux           | PetaLinux        | 2018.1/2 Zynq UltraScale+ MPSoC: ATF doesn't build in PetaLinux or Yocto when ATF DEBUG is enabled | [Xilinx Answer 71156](https://adaptivesupport.amd.com/s/article/71156) | 2018.3              |
| Linux           | PetaLinux        | 2018.1 PetaLinux: Configuring a PetaLinux project using hdf throws HDF deprecate warnings | [Xilinx Answer 71172](https://adaptivesupport.amd.com/s/article/71172) | 2018.2              |
| Linux           | VCU-GStreamer    | 2018.1 Zynq UltraScale+ MPSoC VCU - Why do I get **(gst-launch-1.0:3316): WARNING**: GopLength should be in multiple of (b-frames + 1). Now setting it to default value? | [Xilinx Answer 71253](https://adaptivesupport.amd.com/s/article/71253) |                     |
| Linux           | PetaLinux        | 2018.1/2 Zynq UltraScale+ MPSoC: PetaLinux ATF cannot boot up in QSPI flash mode when only UART1 is enabled in a Vivado design | [Xilinx Answer 71272](https://adaptivesupport.amd.com/s/article/71272) | 2018.3              |
| Baremetal       | Xilfpga          | 2018.1/2 Zynq UltraScale+ MPSoC: PL programming from U-boot and Linux requires different bitstream formats | [Xilinx Answer 71327](https://adaptivesupport.amd.com/s/article/71327) | 2018.3              |
| Linux           | Drivers          | 2018.1/2 Zynq UltraScale+ MPSoC: Linux GEM PTP time adjustment fails for large negative delta | [Xilinx Answer 71332](https://adaptivesupport.amd.com/s/article/71332) | 2018.3              |
| Linux           | VCU              | 2018.1 Zynq UltraScale+ MPSoC - Video Codec Unit (VCU) TRD Design Module 3 does not build with PetaLinux DTG | [Xilinx Answer 71380](https://adaptivesupport.amd.com/s/article/71380) | 2018.3              |
| Linux           | VCU              | 2018.1/2 Zynq UltraScale+ MPSoC - Video Codec Unit (VCU) TRD Design Module 3 does not build when using BB_NO_NETWORK (without network) | [Xilinx Answer 71381](https://adaptivesupport.amd.com/s/article/71381) | 2018.3              |
| Linux           | Yocto            | 2018.1/2 Zynq UltraScale+ MPSoC - Video Codec Unit (VCU) TRD Design Module does not build with PetaLinux SDK generation | [Xilinx Answer 71382](https://adaptivesupport.amd.com/s/article/71382) | 2018.3              |
| Linux           | Drivers          | 2017.1-2018.2 Zynq UltraScale+ MPSoC: Linux kernel boot failed while mounting a JFFS2 filesystem in QSPI boot mode | [Xilinx Answer 71114](https://adaptivesupport.amd.com/s/article/71114) | 2018.3              |
| Linux           | Drivers          | 2017.1-2018.2 Zynq UltraScale+ MPSoC: Linux kernel panic for JFFS2 filesystem on POR or reboot | [Xilinx Answer 71439](https://adaptivesupport.amd.com/s/article/71439) | 2018.3              |

# 2018.1_PetaLinux_Package_List

## Tool/Library Versions

### RHEL/CentOS versions

| Tool/Library                                    | CentOS 7.2                                                   | CentOS 7.3                                                   | CentOS 7.4                                                   | RHEL 7.2                                                     | RHEL 7.3                                                  | RHEL 7.4                                                     |
| ----------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------------------ |
| kernel Version                                  | 3.10.0-693.21.1.el7.x86_64                                   | 3.10.0-693.21.1.el7.x86_64                                   | 3.10.0-693.21.1.el7.x86_64                                   | 3.10.0-327.el7.x86_64                                        | 3.10.0-693.21.1.el7.x86_64                                | 3.10.0-693.21.el7.x86_64                                     |
| dos2unix                                        | dos2unix-6.0.3-7.el7.x86_64                                  | dos2unix-6.0.3-7.el7.x86_64                                  | dos2unix-6.0.3-7.el7.x86_64                                  | dos2unix-6.0.3-7.el7.x86_64                                  | dos2unix-6.0.3-7.el7.x86_64                               | dos2unix-6.0.3-7.el7.x86_64                                  |
| ip (iproute)                                    | iproute-3.10.0-87.0.1.el7.x86_64                             | iproute-3.10.0-87.el7.x86_64                                 | iproute-3.10.0-87.el7.x86_64                                 | iproute-3.10.0-87.0.1.el7.x86_64                             | iproute-3.10.0-74.0.1.el7.x86_64                          | iproute-3.10.0-87.0.1.el7.x86_64                             |
| gawk                                            | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7_3.1.x86_64                                  | gawk-4.0.2-4.el7.x86_64                                   | gawk-4.0.2-4.el7_3.1.x86_64                                  |
| xvfb                                            | xorg-x11-server-Xvfb-1.19.3-11.el7_4.2.x86_64                | xorg-x11-server-Xvfb-1.19.3-11.el7_4.2.x86_64                | xorg-x11-server-Xvfb-1.19.3-11.el7_4.2.x86_64                | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                     | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                  | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                     |
| gcc(for RHEL, use devtoolset-2)                 | gcc-4.8.5-16.0.3.el7_4.2.x86_64                              | gcc-4.8.5-16.0.3.el7_4.2.x86_64                              | gcc-4.8.5-16.el7_4.2.x86_64                                  | gcc-4.8.5-16.el7.x86_64                                      | gcc-4.8.5-11.el7.x86_64                                   | gcc-4.8.5-16.0.1.el7_4.1.x86_64                              |
| git                                             | git-1.8.3.1-12.el7_4.x86_64                                  | git-1.8.3.1-12.el7_4.x86_64                                  | git-1.8.3.1-12.el7_4.x86_64                                  | git-1.8.3.1-12.el7_4.x86_64                                  | git-1.8.3.1-6.el7_2.1.x86_64                              | git-1.8.3.1-12.el7_4.x86_64                                  |
| make                                            | make-3.82-23.el7.x86_64                                      | make-3.82-23.el7.x86_64                                      | make-3.81-23.el6.x86_64                                      | make-3.82-23.el7.x86_64                                      | make-3.82-23.el7.x86_64                                   | make-3.82-23.el7.x86_64                                      |
| netstat (net-tools)                             | net-tools-2.0-0.22.20131004git.el7.x86_64                    | net-tools-2.0-0.22.20131004git.el7.x86_64                    | net-tools-2.0-0.22.20131004git.el7.x86_64                    | net-tools-2.0-0.22.20131004git.el7.x86_64                    | net-tools-2.0-0.17.20131004git.el7.x86_64                 | net-tools-2.0-0.22.20131004git.el7.x86_64                    |
| ncurses-devel                                   | ncurses-devel-5.9-14.20130511.el7.x86_64                     | ncurses-devel-5.9-14.20130511.el7.x86_64                     | ncurses-devel-5.9-14.20130511.el7.x86_64                     | ncurses-devel-5.9-14.20130511.el7.x86_64                     | ncurses-devel-5.9-13.20130511.el7.x86_64                  | ncurses-devel-5.9-14.20130511.el7.x86_64                     |
| tftp-server                                     | tftp-server-5.2-13.el7.x86_64                                | tftp-server-5.2-13.el7.x86_64                                | tftp-server-5.2-13.el7.x86_64                                | tftp-server-5.2-22.el7.x86_64                                | tftp-server-5.2-13.el7.x86_64                             | tftp-server-5.2-13.el7.x86_64                                |
| zlib-devel(also,install 32-bit of this version) | zlib-devel-1.2.7-17.el7.x86_64                               | zlib-devel-1.2.7-17.el7.x86_64  zlib-devel-1.2.7-17.el7.i686 | zlib-devel-1.2.7-17.el7.x86_64                               | zlib-devel-1.2.7-17.el7.x86_64  zlib-devel-1.2.7-17.el7.i686 | zlib-devel-1.2.7-17.el7.x86_64                            | zlib-devel-1.2.7-17.el7.x86_64  zlib-devel-1.2.7-17.el7.i686 |
| zlib-devel-1.2.7-17.el7.i686                    | zlib-devel-1.2.7-17.el7.i686                                 | zlib-devel-1.2.7-17.el7.i686                                 |                                                              |                                                              |                                                           |                                                              |
| openssl-devel                                   | openssl-devel-1.0.2k-8.0.1.el7_3.1.x86_64                    | openssl-devel-1.0.2k-8.0.1.el7_3.1.x86_64                    | openssl-devel-1.0.2k-8.el7_3.1.x86_64                        | openssl-devel-1.0.2k-12.0.1.el7_3.1.x86_64                   | openssl-devel-1.0.1e-60.0.1.el7_3.1.x86_64                | openssl-devel-1.0.2k-12.0.1.el7_3.1.x86_64                   |
| flex                                            | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.37-3.el7.x86_64                                  | flex-2.5.37-3.el7.x86_64                                     |
| bison                                           | bison-3.0.4-1.el7.x86_64                                     | bison-3.0.4-1.el7.x86_64                                     | bison-3.0.4-1.el7.x86_64                                     | bison-3.0.4-1.el7.x86_64                                     |                                                           | bison-3.0.4-1.el7.x86_64                                     |
| libselinux                                      | libselinux-2.5.11.el7.x86_64                                 | libselinux-2.5.11.el7.x86_64                                 | libselinux-2.5.11.el7.x86_64                                 | libselinux-2.5.12.el7.x86_64                                 | libselinux-2.5-6.el7.x86_64                               | libselinux-2.5.12.el7.x86_64                                 |
| gnupg                                           |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| wget                                            | wget-1.14-15.el7_4.1.x86_64                                  | wget-1.14-15.el7_4.1.x86_64                                  | wget-1.14-15.el7_4.1.x86_64                                  | wget-1.14-15.el7_4.1.x86_64                                  | wget-1.14-13.el7.x86_64                                   | wget-1.14-15.el7_4.1.x86_64                                  |
| diffstat                                        | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.57-4.el7.x86_64                                | diffstat-1.57-4.el7.x86_64                                   |
| chrpath                                         | chrpath-0.16-0.el7.x86_64                                    | chrpath-0.16-0.el7.x86_64                                    | chrpath-0.16-0.el7.x86_64                                    | chrpath-0.16-0.el7.x86_64                                    | chrpath-0.13-14.el7.x86_64                                | chrpath-0.16-0.el7.x86_64                                    |
| socat                                           | socat-1.7.3.2-2.el6.x86_64                                   | socat-1.7.3.2-2.el6.x86_64                                   | socat-1.7.3.2-2.el6.x86_64                                   | socat-1.7.3.2-2.el6.x86_64                                   | socat-1.7.2.2-5.el7.x86_64                                | socat-1.7.3.2-2.el6.x86_64                                   |
| xterm                                           | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                                       | xterm-295-3.el7.x86_64                                    | xterm-295-3.el7.x86_64                                       |
| autoconf                                        | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                                  | autoconf-2.69-11.el7.noarch                               | autoconf-2.69-11.el7.noarch                                  |
| libtool                                         | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                             | libtool-2.4.2-22.el7_3.x86_64                                |
| tar                                             | tar-1.26-32.el7.x86_64                                       | tar-1.26-32.el7.x86_64                                       | tar-1.26-32.el7.x86_64                                       | tar-1.26-34.el7.x86_64                                       | tar-1.26-31.el7.x86_64                                    | tar-1.26-34.el7.x86_64                                       |
| unzip                                           | unzip-6.0-16.el7.x86_64                                      | unzip-6.0-16.el7.x86_64                                      | unzip-6.0-5.el6.x86_64                                       | unzip-6.0-19.el7.x86_64                                      | unzip-6.0-16.el7.x86_64                                   | unzip-6.0-19.el7.x86_64                                      |
| texinfo                                         | texinfo-5.1-4.el7.x86_64                                     | texinfo-5.1-4.el7.x86_64                                     | texinfo-5.1-4.el7.x86_64                                     | texinfo-5.1-4.el7.x86_64                                     | texinfo-5.1-4.el7.x86_64                                  | texinfo-5.1-5.el7.x86_64                                     |
| zlib1g-dev                                      |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| gcc-multilib                                    |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| build-essential                                 |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| libsdl1.2-dev                                   |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| libglib2.0-dev                                  |                                                              |                                                              |                                                              |                                                              |                                                           |                                                              |
| SDL-devel                                       | SDL-devel-1.2.15-14.el7.i686                                 | SDL-devel-1.2.15-14.el7.i686                                 | SDL-devel-1.2.15-14.el7.i686                                 | SDL-devel-1.2.15-14.el7.i686                                 | SDL-devel-1.2.15-14.el7.i686                              | SDL-devel-1.2.15-14.el7.i686                                 |
| glibc-devel                                     | glibc-devel-2.17-196.el7_4.2.x86_64 glibc-devel-2.17-196.el7_4.2.i686 | glibc-devel-2.17-196.el7_4.2.x86_64                          | glibc-devel-2.17-196.el7_4.2.x86_64 glibc-devel-2.17-196.el7_4.2.i686 | glibc-devel-2.17-222.el7_4.2.x86_64 glibc-devel-2.17-222.el7_4.2.i686 | glibc-devel-2.17-157.el7_3.4.x86_64                       | glibc-devel-2.17-222.el7_4.2.x86_64                          |
| glibc-devel-2.17-196.el7_4.2.i686               | glibc-devel-2.17-157.el7_3.4.i686                            | glibc-devel-2.17-222.el7_4.2.i686                            |                                                              |                                                              |                                                           |                                                              |
| 32-bit glibc                                    | glibc-2.17-196.el7_4.2.i686                                  | glibc-2.17-196.el7_4.2.i686                                  | glibc-2.17-196.el7_4.2.i686                                  | glibc-2.17-222.el7_4.2.x86_64                                | glibc-2.17-157.el7_3.4.x86_64                             | glibc-2.17-222.el7_4.2.x86_64                                |
| glibc-2.17-196.el7_4.2.x86_64                   | glibc-2.17-196.el7_4.2.x86_64                                | glibc-2.17-196.el7_4.2.x86_64                                | glibc-2.17-222.el7_4.2.x86_64                                | glibc-2.17-157.el7_3.4.i686                                  | glibc-2.17-222.el7_4.2.i686                               |                                                              |
| glib2-devel                                     | glib2-devel-2.50.3-3.el7.x86_64                              | glib2-devel-2.50.3-3.el7.x86_64                              | glib2-devel-2.50.3-3.el7.x86_64                              | glib2-devel-2.54.2-2.el7.x86_64                              | glib2-devel-2.46.2-4.el7.x86_64                           | glib2-devel-2.54.2-2.el7.x86_64                              |
| automake                                        | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                              | automake-1.13.4-3.el7.noarch                                 |
| screen                                          | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             | screen-4.1.0-0.25.20120314git3c2946.el7.x86_64               | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64          | screen-4.1.0-0.25.20120314git3c2946.el7.x86_64               |
| pax                                             | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                                        | pax-3.4-19.el7.x86_64                                     | pax-3.4-19.el7.x86_64                                        |
| gzip                                            | gzip-1.5-9.el7.x86_64                                        | gzip-1.5-9.el7.x86_64                                        | gzip-1.5-9.el7.x86_64                                        | gzip-1.5-10.el7.x86_64                                       | gzip-1.5-8.el7.x86_64                                     | gzip-1.5-9.el7.x86_64                                        |
| libstdc++                                       | libstdc++-4.8.5-11.el7.x86_64                                | libstdc++-4.8.5-16.el7_4.1.x86_64                            | libstdc++-4.8.5-16.el7_4.1.x86_64 libstdc++-4.8.5-16.el7_4.1.i686 | libstdc++-4.8.5-16.el7.x86_64                                | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686 | libstdc++-4.8.5-16.0.1.el7_4.1.i686 libstdc++-4.8.5-28.0.1.el7.x86_64 |
| libstdc++-4.8.5-11.el7.i686                     | libstdc++-4.8.5-16.el7_4.1.i686                              | libstdc++-4.8.5-16.el7.x86_65                                |                                                              |                                                              |                                                           |                                                              |
| g++ (gcc-c++)                                   | gcc-c++-4.8.5-11.el7.x86_64                                  | gcc-c++-4.8.5-16.el7_4.1.x86_64                              | gcc-c++-4.8.5-16.el7_4.1.x86_64                              | gcc-c++-4.8.5-16.el7.x86_64                                  | gcc-c++-4.8.5-11.el7.x86_64                               | gcc-c++-4.8.5-28.0.1.el7.x86_64                              |
| patch                                           | patch-2.7.1.8.el7.x86_64                                     | patch-2.7.1.8.el7.x86_64                                     | patch-2.7.1.8.el7.x86_64                                     | patch-2.7.1.8.el7.x86_64                                     | patch-2.7.1.8.el7.x86_64                                  | patch-2.7.1.8.el7.x86_64                                     |
| zlib                                            | zlib-1.2.7-17.el7.x86_64                                     | zlib-1.2.7-17.el7.x86_64                                     | zlib-1.2.3-29.el6.x86_64                                     | zlib-1.2.7-17.el7.x86_64                                     | zlib-1.2.7-17.el7.x86_64                                  | zlib-1.2.7-17.el7.x86_64                                     |
| zlib-1.2.7-17.el7.i686                          | zlib-1.2.7-17.el7.i686                                       | zlib-1.2.7-17.el7.i686                                       | zlib-1.2.7-17.el7.i686                                       | zlib-1.2.7-17.el7.i686                                       | zlib-1.2.7-17.el7.i686                                    |                                                              |

### Ubuntu

| Tool/Library                                    | Ubuntu 16.04.3 Desktop             | Ubuntu 16.04.03 server             |
| ----------------------------------------------- | ---------------------------------- | ---------------------------------- |
| kernel Version                                  | 4.13.0-32-generic                  | 4.4.0-87-generic                   |
| dos2unix                                        | tofrodos_1.7.13+ds-2.debian.tar.xz | tofrodos_1.7.13+ds-2.debian.tar.xz |
| ip (iproute)                                    | iproute2                           | iproute2                           |
| gawk                                            | gawk                               | gawk                               |
| xvfb                                            | xvfb                               | xvfb                               |
| gcc(for RHEL, use devtoolset-2)                 | gcc 5.4                            | gcc 5.4                            |
| git                                             | git 1.7.1 or above                 | git 1.7.1 or above                 |
| make                                            | make 4.1                           | make 4.1                           |
| netstat (net-tools)                             | net-tools                          | net-tools                          |
| ncurses-devel                                   | libncurses5-dev                    | libncurses5-dev                    |
| tftp-server                                     | tftpd                              | tftpd                              |
| zlib-devel(also,install 32-bit of this version) | i386/zliob1g-2ubuntu4-dev          | i386/zliob1g-2ubuntu4-dev          |
|                                                 |                                    |                                    |
| openssl-devel                                   | libssl-dev                         | libssl-dev                         |
| flex                                            | flex                               | flex                               |
| bison                                           | bison                              | bison                              |
| libselinux                                      | libselinux1                        | libselinux1                        |
| gnupg                                           | gnupg                              | gnupg                              |
| wget                                            | wget                               | wget                               |
| diffstat                                        | diffstat                           | diffstat                           |
| chrpath                                         | chrpath                            | chrpath                            |
| socat                                           | socat                              | socat                              |
| xterm                                           | xterm                              | xterm                              |
| autoconf                                        | autoconf                           | autoconf                           |
| libtool                                         | libtool                            | libtool                            |
| tar                                             | tar1.24                            | tar1.24                            |
| unzip                                           | unzip                              | unzip                              |
| texinfo                                         | texinfo                            | texinfo                            |
| zlib1g-dev                                      | zlib1g-dev                         | zlib1g-dev                         |
| gcc-multilib                                    | gcc-multilib                       | gcc-multilib                       |
| build-essential                                 | build-essential                    | build-essential                    |
| libsdl1.2-dev                                   | libsdl1.2-dev                      | libsdl1.2-dev                      |
| libglib2.0-dev                                  | libglib2.0-dev                     | libglib2.0-dev                     |
| SDL-devel                                       |                                    |                                    |
| glibc-devel                                     |                                    |                                    |
|                                                 |                                    |                                    |
| 32-bit glibc                                    |                                    |                                    |
|                                                 |                                    |                                    |
| glib2-devel                                     |                                    |                                    |
| automake                                        |                                    |                                    |
| screen                                          | screen                             | screen                             |
| pax                                             | pax                                | pax                                |
| gzip                                            | gzip                               | gzip                               |
| libstdc++                                       |                                    |                                    |
|                                                 |                                    |                                    |
| g++ (gcc-c++)                                   |                                    |                                    |
| patch                                           |                                    |                                    |
| zlib                                            |                                    |                                    |
|                                                 |                                    |                                    |

# README_content_v2018.01

=============================

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2018.1 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2018.1 Open Components Source Code (TAR/GZIP) file: 
-----------------------------------------------------------------------

	This file contains the source code of all the SW components shipped as 
part of the PetaLinux tool. It also contains the source code for all the 
SW packages, available at https://petalinux.xilinx.com/ that petaLinux tool packages
 in the project, when selected. This file is provide as part of legal requirement 
for your viewing only. It is not required to be downloaded for using 
the PetaLinux tool or BSPs.


Sample list of components in the files 1) and 2):

---------------------------------------------

		QEMU
	
		busybox
	
		mtd-utils
	
		libfdt
	
		dtc
	
		u-boot
	
		device-tree-generator
	
		iso-codes
	
		ca-certificates
	
		db
	
		bash
	
		Linux
	
		ATF
	
		XEN
	
		kconfig-frontends
	
		Note: more than 1000 other SW components.