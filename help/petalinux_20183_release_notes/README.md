## 71653 - PetaLinux 2018.3 - Product Update Release Notes and Known Issues

## Title

71653 - PetaLinux 2018.3 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2018.3 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for the 2018.3 PetaLinux Release**  

This table contains supported BSPs for Zynq-7000, MicroBlaze, and Zynq UltraScale+ MPSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

**Note:** XY - Represents release year, Y - Represents release version.

| Platform                   | Variant                      | BSP Name                                       | BSP Description                                              |
| -------------------------- | ---------------------------- | ---------------------------------------------- | ------------------------------------------------------------ |
| **MicroBlaze**             | AC701                        | xilinx-ac701-v20XY.Z-final.bsp                 | This BSP contains two BSPs [AC701 lite, AC701 full].<br><br>**Hardware (AC701 lite):** Design contains MicroBlaze Processor, core peripherals UART_lite, Ethernet Lite, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br>AC701 lite contains the AXI Lite IPs UART_lite, Ethernet Lite etc. in contrast to AC701 Full.<br><br>**Hardware (AC701 full):** Design contains MicroBlaze Processor, core peripherals AXI UART16550, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, SPI flash, led_4bits.<br><br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | KC705                        | xilinx-kc705-v20XY.Z-final.bsp                 | This BSP contains two BSPs [KC705 lite, KC705 full].<br><br>**Hardware (KC705 lite):** Design contains MicroBlaze Processor, core peripherals UART_lite, Ethernet Lite, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br><br>**Hardware (KC705 full):** Design contains MicroBlaze Processor, core peripherals AXI UART16550, AXI 1G/2.5G Ethernet, AXI I2C, AXI GPIO, AXI DDR controller, Linear flash, led_8bits.<br><br>**Software:** fs-boot, u-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **MicroBlaze**             | KCU105                       | xilinx-kcu105-v20XY.Z-final.bsp                | This BSP contains:<br><br>**Hardware:** Design contains MicroBlaze Processor, core peripherals AXI I2C, AXI GPIO, AXI DDR controller, AXI QSPI, led_8bits, and AXI Ethernet IP.<br><br>**Software:** fs-boot, U-boot, Linux, device-tree, rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, fs-boot, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq-7000**              | ZC702                        | xilinx-zc702-v20XY.Z-final.bsp                 | This BSP contains:<br><br>**Hardware:** Design contains Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_4bits.<br><br>**Software:** FSBL, U-boot, Linux, device-tree (includes open-amp), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq-7000**              | ZC706                        | xilinx-zc706-v20XY.Z-final.bsp                 | This BSP contains:<br><br>**Hardware:** Design contains Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_4bits, dip_switches_4bits, gpio_sws_3bits.<br><br>**Software:** FSBL, U-boot, Linux, device-tree (includes open-amp), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq-7000**              | Avnet Digilent Zedboard      | avnet-digilent-zedboard-v20XY.Z-final.bsp      | This BSP contains:<br><br>**Hardware:** Design contains Zynq-7000 PS block (DDR, UART, SD, QSPI, Ethernet etc.) and AXI GPIO connected with led_8bits, btns_5bits, sws_8bits.<br><br>**Software:** FSBL, U-boot, Linux, device-tree (includes open-amp), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | ZCU102 production silicon    | xilinx-zcu102-v20XY.Z-final.bsp                | This BSP contains:<br><br>**Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.)<br><br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes open-amp, Xen), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, atf, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | ZCU102 ZU9 ES2 Rev 1.0       | xilinx-zcu102-zu9-es2-rev1.0-v20XY.Z-final.bsp | This BSP contains:<br><br>**Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.)<br><br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes open-amp, xen), rootfs (minimal packages).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, atf, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | ZCU104 V2 production silicon | xilinx-zcu104-v20XY.Z-final-v2.bsp             | This BSP contains:<br><br>**Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br><br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes open-amp, xen), vcu-control software, rootfs (minimal packages which includes additional SW packages like GStreamer, OpenMAX, V4L2, libdrm and vcu-examples).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, atf, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ MPSoC** | ZCU106 V2 production silicon | xilinx-zcu106-v20XY.Z-final-v2.bsp             | This BSP contains:<br><br>**Hardware:** Design contains Zynq UltraScale+ MPSoC PS block (DDR, UART, SD, QSPI, Ethernet, PCIe, DP, USB, SATA etc.), VCU DDR4 Controller (PL DDR) and VCU IP.<br><br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes open-amp, xen), vcu-control software, rootfs (minimal packages which includes additional SW packages like GStreamer, OpenMAX, V4L2, libdrm and vcu-examples).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, atf, u-boot, Linux and rootfs for booting u-boot and Linux. |
| **Zynq UltraScale+ RFSoC** | ZCU111 production silicon    | xilinx-zcu111-v20XY.Z-final.bsp                | This BSP contains:<br><br>**Hardware:** Design contains Zynq UltraScale+ RFSoC PS block (DDR, UART, SD, QSPI, Ethernet, DP, USB, SATA etc) and rf_data_converters, sd_fec_dec, adc_sink, dac_source, axi_gpio, axi_intc IP's.<br><br>**Software:** FSBL, PMUFW, ATF, U-boot, Linux, device-tree (includes open-amp,xen), rfdc-drivers, rootfs (minimal packages which includes RDFC example applications).<br>**Pre-built Images:** Ready to test images bitstream, FSBL, PMUFW, atf, u-boot, Linux and rootfs for booting u-boot and Linux. |

**Note**: The "[sstate cache file](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate-rel-v2018.3.tar.gz)" (sstate-rel-v2018.3.tar.gz) can be found on the Xilinx download area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2018.3_README.tar.gz) (sstate\_rel\_2018.3\_README) file that outlines the procedure to use "sstate cache".  

Refer to the attached file "[2018.3\_PetaLinux\_Packages\_List](https://www.xilinx.com/Attachment/2018.3_PetaLinux_Package_List.xlsx)" for software package versions tested on host machines, which is required for PetaLinux installation tools.

[README](https://www.xilinx.com/Attachment/README_content_v2018.3.txt) for downloads area.  

**PetaLinux 2018.3 contains the following build collateral:**

| Component                      | Git Repo                                                     | Git Branches          | Git Tags                 | Commit ID                                                    | Comments                                                     |
| ------------------------------ | ------------------------------------------------------------ | --------------------- | ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **FSBL**                       | git://github.com/Xilinx/embeddedsw.git                       | release-2018.3        | xilinx-v2018.3           | 5b3764e8eb42e543f411f6ec3ed31c7112c6e178                     | FSBL for Zynq-7000 is at `embeddedsw/lib/sw_apps/zynq_fsbl`.<br>FSBL for Zynq UltraScale+ is at `embeddedsw/lib/sw_apps/zynqmp_fsbl`. |
| **PMU Firmware**               | git://github.com/Xilinx/embeddedsw.git                       | release-2018.3        | xilinx-v2018.3           | 5b3764e8eb42e543f411f6ec3ed31c7112c6e178                     | PMU for Zynq UltraScale+ Firmware is at `embeddedsw/lib/sw-apps/zynqmp_pmufw`. |
| **Device-tree**                | git://github.com/Xilinx/device-tree-xlnx.git                 | master                | xilinx-v2018.3           | b7466bbeeede15ec72143e3c3466e067589821a1                     | —                                                            |
| **Linux**                      | git://github.com/Xilinx/linux-xlnx.git                       | xlnx_rebase_v4.14     | xlnx_rebase_v4.14_2018.3 | eeab73d1207d6fc2082776c954eb19fd7290bfbe                     | Linux Kernel rebase version 4.14                             |
| **U-Boot**                     | git://github.com/Xilinx/u-boot-xlnx.git                      | master                | xilinx-v2018.3           | d8fc4b3b70bccf1577dab69f6ddfd4ada9a93bac                     | U-Boot Version v2018.01                                      |
| **QEMU**                       | git://github.com/Xilinx/qemu.git                             | master                | xilinx-v2018.3           | f70bd86859c7a1a075ac864b4765168f821f1aae                     | —                                                            |
| **Xen**                        | git://github.com/Xilinx/xen.git                              | xilinx/release-2018.3 | xilinx-v2018.3           | b2edf52680415daa9cb7db0d8999faca299cd13c                     | Xen Version 4.14                                             |
| **ARM-Trusted-Firmware (ATF)** | git://github.com/Xilinx/arm-trusted-firmware.git             | master                | xilinx-v2018.3           | 08560c36ea5b6f48b962cb4bd9a79b35bb3d95ce                     | ATF is based on upstream version 1.5                         |
| **Yocto**                      | git://github.com/Xilinx/meta-xilinx.git<br>git://github.com/Xilinx/meta-xilinx-tools.git<br>git://github.com/Xilinx/meta-petalinux.git | rel-v2018.3           | No Tags                  | 7922f16dfa5308fb5419a80f513bb07c0384f95e<br>b286943d7d468e9ff10b9f9662767e8c71f104d1<br>254edec8368c3d30676135365734abe06e596881 | Yocto 2.4.3 Rocko                                            |
| **qemu-devicetrees**           | git://github.com/Xilinx/qemu-devicetrees.git                 | branch/xilinx-v2018.3 | xilinx-v2018.3           | e3e40b8829894a479c7d7380fc8137886645dda8                     | —                                                            |
| **OpenAMP**                    | git://github.com/Xilinx/open-amp.git                         | master                | xilinx-v2018.3           | 4dfe2ac14745e4a24d7319c634d5f9d2f3e328c6                     | —                                                            |
| **libmetal**                   | git://github.com/Xilinx/libmetal.git                         | master                | xilinx-v2018.3           | 82e26fb31b996011cd78c90689d1332e1f88fedf                     | —                                                            |
| **VCU OpenMax IL**             | git://github.com/Xilinx/vcu-omx-il.git                       | master                | xilinx-v2018.3           | cf4b031ac88c7889e4f29ac7fc8ca7592bf12144                     | —                                                            |
| **VCU Control Software**       | git://github.com/Xilinx/vcu-ctrl-sw.git                      | master                | xilinx-v2018.3           | 1cb5281d319ea4f3c0eb5514864c80d95e78fe6e                     | —                                                            |
| **VCU Firmware**               | git://github.com/Xilinx/vcu-firmware.git                     | master                | xilinx-v2018.3           | d01951905e1aedb179d838a6b86016f34e2f4966                     | —                                                            |
| **VCU Modules**                | git://github.com/Xilinx/vcu-modules.git                      | master                | xilinx-v2018.3           | f6a9093ec32ee97a2df065aee8b8e676c2024f01                     | —                                                            |
| **GStreamer OpenMax IL**       | git://github.com/Xilinx/gst-omx.git                          | xilinx-master         | xilinx-v2018.3           | b2dce0a04ea34b762149ffa5a0ea66abe00d7c88                     | GStreamer version 1.12.2                                     |
| **GStreamer Plugins-Base**     | git://github.com/Xilinx/gst-plugins-base.git                 | master-rel-1.12.2     | xilinx-v2018.3           | 71745a77db2c246aee48526c00813788f5efa710                     | —                                                            |
| **GStreamer Plugins-Bad**      | git://github.com/Xilinx/gst-plugins-bad.git                  | master-rel-1.12.2     | xilinx-v2018.3           | 9ad719a38c40403446b2ce2d3c1a4f35c5ab06b6                     | —                                                            |
| **GStreamer Plugins-Good**     | git://github.com/Xilinx/gst-plugins-good.git                 | master-rel-1.12.2     | xilinx-v2018.3           | d2c7cf8d752de84c30f9675572037e0250cd3c6d                     | —                                                            |
| **GCC**                        | —                                                            | —                     | —                        | —                                                            | MB compiler version 7.3<br>ARM 7.3                           |

**2018.3 Release Notes for Open Source components wiki page:**

Covers details for below components changes (new features/fixes) in a particular release.  

https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/56524900/2018.3+Release+Notes+for+Open+Source+Components

**2018.3 New Features:**  

**PetaLinux**

-   Added support for using the trim version of XSCT tools to build components such as FSBL, PMUFW etc.,.
-   Added support for Programmable Logic (PL) device tree overlay.  
    
-   Added support for FPGA Manager utilities.  
    
-   PetaLinux now uses only versionless drivers from [https://github.com/Xilinx/embeddedsw](https://github.com/Xilinx/embeddedsw) which means that <plnx-proj-root>/components/plnx\_workspace will no longer have fsbl/pmu-firmware/fs-boot directories.  
    For more details refer to (UG1144). It is now similar to other open source components like U-boot and Linux.  
    
-   SDFEC Design Example is part of the ZCU111 PetaLinux BSP.  
    
-   Added support for RHEL 7.5 and CentOS 7.5 build host.

**GPU MALI-400**

-   Added Wayland compositor and GBM buffer management support in MALI user space libraries for 32 and 64 bit mode.
-   Added support for Displayless EGL rendering for MALI binaries.  
    

**2018.3 Bug Fixes:**

**PetaLinux**

-   Fixed RFDC build issues when using a custom ZCU111 HDF on top of xilinx-zcu111-v20XY.Z-final.bsp.  
    
-   Linux reboot command does not work when TRACE port is present in the design.  
    
-   Fixed do\_populate\_sysroot task for petalinux-user-image recipe.  
    
-   PetaLinux installer fails to installs when /tmp directory has restricted access.  
    
-   PetaLinux FIT image does not boot when image.ub size is larger on a ZC702 board.  
    
-   Linux hangs when using lower 36-bit physical memory from petalinux-config option.  
    
-   Fix for boot login console taking more than 8 minutes with 2018.2 based rootfs.  
    

**GPU MALI-400**

-   Fixed YUV format issue where the TEX\_WIDTH is being interpreted differently than expected.

**Known Issues for 2018.3:**  

| Linux/Baremetal | Components       | Description                                                  | Work-around / Xilinx Answer                                  | To be fixed version |
| --------------- | ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------- |
| Linux           | Yocto/PetaLinux  | 2018.x Yocto/PetaLinux: Ubuntu 18.04.x LTS support           | [Xilinx Answer 71448](https://www.xilinx.com/support/answers/71448.html) |                     |
| Linux           | PetaLinux        | Zynq UltraScale+ MPSoC: How to enable UHS (SD 3.0) support for ZCU102 and ZCU106 evaluation board PetaLinux BSPs | [Xilinx Answer 69978](https://www.xilinx.com/support/answers/69978.html) |                     |
| Linux           | XSDK             | 2017.x-2018.x Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle | [Xilinx Answer 69143](https://www.xilinx.com/support/answers/69143.html) |                     |
| Linux           | Yocto, PetaLinux | 2018.x Zynq UltraScale+ MPSoC: Yocto or PetaLinux throws warnings when the build do_rootfs task completes | [Xilinx Answer 71110](https://www.xilinx.com/support/answers/71110.html) |                     |
| Linux           | Drivers          | 2018.1-2018.3 Zynq UltraScale+ MPSoC: PetaLinux Warm-Restart BSP fails to wakeup Ethernet when FPD is off | [Xilinx Answer 71028](https://www.xilinx.com/support/answers/71028.html) |                     |
| Linux           | FSBL             | 2018.x Zynq UltraScale+ MPSoC: How to achieve SATA performance in Linux | [Xilinx Answer 71584](https://www.xilinx.com/support/answers/71584.html) |                     |
| Linux           | FSBL             | 2018.x Zynq UltraScale+ MPSoC: How to make SMMU work with SATA IP | [Xilinx Answer 71790](https://www.xilinx.com/support/answers/71790.html) |                     |
| Linux           | PMUFW            | 2018.2/3 Ultra96: PetaLinux BSP image does not shut down the board completely when using Matchbox desktop GUI power button or single press power button on board | [Xilinx Answer 71722](https://www.xilinx.com/support/answers/71722.html) |                     |
| Linux           | PetaLinux        | 2017.x-2018.3 Zynq-7000: Cannot boot Zynq-7000 PetaLinux images individually in legacy flow | [Xilinx Answer 71231](https://www.xilinx.com/support/answers/71231.html) | 2019.1              |
| Linux           | PetaLinux        | 2018.1-2018.3 Zynq UltraScale+ MPSoC: ARM Trusted Firmware hangs when UART0 is disabled in PetaLinux | [Xilinx Answer 71743](https://www.xilinx.com/support/answers/71743.html) | 2019.1              |
| Linux           | Drivers          | 2018.3 Zynq UltraScale+ MPSoC: Linux v4l2 mem2mem driver transcode fails when source buffer to mem2mem has different byte alignment restrictions | [Xilinx Answer 71780](https://www.xilinx.com/support/answers/71780.html) | 2019.1              |
| Linux           | PetaLinux        | 2018.3 Ultra96: PetaLinux FIT image(image.ub) fails to load at u-boot via USB boot mode | [Xilinx Answer 71781](https://www.xilinx.com/support/answers/71781.html) | 2019.1              |
| Linux           | PMUFW            | 2018.x Zynq UltraScale+ MPSoC: APU Only Restart fails after Power Off Suspend (POS) | [Xilinx Answer 71766](https://www.xilinx.com/support/answers/71766.html) | 2019.1              |
| Linux           | Drivers          | 2018.3 LogiCORE Video Mixer Linux Driver - Why do I see the Red and Blue colors swapped when setting the IP GUI configuration and the video format in the device tree for RGB and BGR? | [Xilinx Answer 71802](https://www.xilinx.com/support/answers/71802.html) | 2019.1              |
| Linux           | VCU-GStreamer    | 2018.3 Zynq UltraScale+ MPSoC VCU - Why does GStreamer crash when trying to decode some transport stream (TS) files? | [Xilinx Answer 71809](https://www.xilinx.com/support/answers/71809.html) | 2019.1              |
| Linux           | VCU              | 2018.3 Zynq UltraScale+ MPSoC VCU - Why does the display freeze after about 10 minutes of decoding and displaying some H.264 streams that are missing the start code in the first NAL unit? | [Xilinx Answer 71810](https://www.xilinx.com/support/answers/71810.html) | 2019.1              |
| Linux           | VCU              | 2018.3 Zynq UltraScale+ MPSoC VCU - Why does the VCU Decoder Control Software always output 10-bit data? | [Xilinx Answer 71811](https://www.xilinx.com/support/answers/71811.html) | 2019.1              |
| Linux           | VCU              | 2018.3 Zynq UltraScale+ MPSoC VCU - Why does the VCU Encoder take more time when using CONST_QP mode than it does in VBR mode? | [Xilinx Answer 71812](https://www.xilinx.com/support/answers/71812.html) | 2019.1              |
| Linux           | VCU              | 2018.3 Zynq UltraScale+ MPSoC VCU - Why does the VCU Control Software Decoder Example application hang while decoding streams which contain errors? | [Xilinx Answer 71813](https://www.xilinx.com/support/answers/71813.html) | 2019.1              |
| Linux           | PetaLinux        | 2018.3 PetaLinux: Menuconfig GUI does not come up when you run the petalinux-config -c kernel command multiple times on VM | [Xilinx Answer 71814](https://www.xilinx.com/support/answers/71814.html) | 2019.1              |
| Linux           | Device-tree      | 2018.3 Zynq UltraScale+ MPSoC: DTG sub nodes for 10G/25G Ethernet Subsystem design with multicore does not work with same node label | [Xilinx Answer 71817](https://www.xilinx.com/support/answers/71817.html) | 2019.1              |
| Linux           | GStreamer        | 2018.x Zynq UltraScale+ MPSoC: Yocto or PetaLinux returns warnings when the build gstd do_configure task completes | [Xilinx Answer 71830](https://www.xilinx.com/support/answers/71830.html) | 2019.1              |
| Linux           | VCU              | 2018.3 Zynq UltraScale+ MPSoC VCU - Why does the VCU produce bad quality output when the LambdaCtrlMode = DYNAMIC_LDA or AUTO_LDA? | [Xilinx Answer 71871](https://www.xilinx.com/support/answers/71871.html) | 2019.1              |
| Linux           | Yocto, PetaLinux | 2018.3 Zynq UltraScale+ MPSoC/RFSoC: PetaLinux/Yocto fails to build FSBL component with fatal error: psu_init.h: No such file or directory | [Xilinx Answer 71921](https://www.xilinx.com/support/answers/71921.html) | 2019.1              |
| Linux           | VCU              | 2018.3 Zynq UltraScale+ MPSoC VCU - Why am I getting a "Channel creation failed" error when using the LOW_DELAY_P mode with HEVC multi-stream encoding? | [Xilinx Answer 71934](https://www.xilinx.com/support/answers/71934.html) | 2019.1              |
| Linux           | VCU              | 2018.3 Zynq UltraScale+ MPSoC VCU - Why does the IDR not repeat when the IDR picture frequency is 1 and the GOP Length is 1? | [Xilinx Answer 71987](https://www.xilinx.com/support/answers/71987.html) | 2019.1              |
| Linux           | VCU              | 2018.3 Zynq UltraScale+ MPSoC VCU - Why do I see "blocky" results when decoding non-compliant stream where the max_dec_frame_buffering is larger than the MaxDpbSize? | [Xilinx Answer 71991](https://www.xilinx.com/support/answers/71991.html) | 2019.1              |
| Linux           | VCU              | 2018.3 Zynq UltraScale+ MPSoC VCU - Why do I see a bitrate of 1.55Mbps when using CBR Rate Control Mode with a Target Bit Rate of 1 Mbps and using a GOP Length of 12? | [Xilinx Answer 71993](https://www.xilinx.com/support/answers/71993.html) | 2019.1              |

# README_content_v2018.3

=============================

Contents in the download area
=============================
 In the download area along with the PetaLinux tool installer and BSPs for various HW.
 The following content is also available for download:


1.	PetaLinux 2018.3 License and copyrights info (TAR/GZIP) file:
-----------------------------------------------------------------------

	This file contains the copyright headers of all the SW components shipped
 as part of the PetaLinux tool. It also contains the copyright headers for all 
the SW packages, available at https://petalinux.xilinx.com/ that 
petaLinux tool packages in the project, when selected. This file is provide as part
 of legal requirement for your viewing only. It is not required to be downloaded
 for using the PetaLinux tool or BSPs.

​	


2.	 PetaLinux 2018.3 Open Components Source Code (TAR/GZIP) file: 
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

# 2018.3_PetaLinux_Package_List

## Linux Distribution OS details:

1. RHEL Server:  Infrastructure Server
2. RHEL Workstation : Development and Creative workstation.
3. CentOS Server (From Everything.ISO): Infrastructure server.
4. CentOS Workstation (From Everything.ISO): Development and Creative workstation.
5. Ubuntu 16.04.04 Desktop.
6. Ubuntu 16.04.04 Server.

### Note: 

1. Empty packages are not installed means assuming these are default from Linux Distribution.

## Tool/Library Versions

### RHEL/CentOS versions

| Library/Package | CentOS 7.2 (workstation)                     | CentOS 7.2 (server)                              | CentOS 7.3 (workstation)                     | CentOS 7.3 (server)                              | CentOS 7.4 (workstation)                     | CentOS 7.4 (server)                              | CentOS 7.5 (workstation)                                     | CentOS 7.5 (server)                              | RHEL 7.2 (workstation)                       | RHEL 7.2 (server)                                | RHEL 7.3 (workstation)                       | RHEL 7.3 (Server)                                | RHEL 7.4 (workstation)                   | RHEL 7.4 (server)                                | RHEL 7.5 (workstation)                                       | RHEL 7.5 (server)                                |
| --------------- | -------------------------------------------- | ------------------------------------------------ | -------------------------------------------- | ------------------------------------------------ | -------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | -------------------------------------------- | ------------------------------------------------ | -------------------------------------------- | ------------------------------------------------ | ---------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ |
| dos2unix        | dos2unix                                     | dos2unix                                         | dos2unix                                     | dos2unix                                         | dos2unix                                     | dos2unix                                         | dos2unix                                                     | dos2unix                                         | dos2unix                                     | dos2unix                                         | dos2unix                                     | dos2unix                                         | dos2unix                                 | dos2unix                                         | dos2unix                                                     | dos2unix                                         |
| ip              | iproute                                      | iproute                                          | iproute                                      | iproute                                          | iproute                                      | iproute                                          | iproute                                                      | iproute                                          | iproute                                      | iproute                                          | iproute                                      | iproute                                          | iproute                                  | iproute                                          | iproute                                                      | iproute                                          |
| gawk            | gawk                                         | gawk                                             | gawk                                         | gawk                                             | gawk                                         | gawk                                             | gawk                                                         | gawk                                             | gawk                                         | gawk                                             | gawk                                         | gawk                                             | gawk                                     | gawk                                             | gawk                                                         | gawk                                             |
| gcc             | gcc.x86_64 0:4.8.5-28.el7_5.1                | gcc.x86_64 0:4.8.5-28.el7_5.1                    | gcc.x86_64 0:4.8.5-28.el7_5.1                | gcc.x86_64 0:4.8.5-28.el7_5.1                    | gcc.x86_64 0:4.8.5-28.el7_5.1                | gcc.x86_64 0:4.8.5-28.el7_5.1                    | gcc.x86_64 0:4.8.5-36.0.1.el7                                | gcc.x86_64 0:4.8.5-28.el7_5.1                    | gcc.x86_64 0:4.8.5-36.0.1.el7                | gcc.x86_64 0:4.8.5-36.0.1.el7                    | gcc.x86_64 0:4.8.5-36.0.1.el7                | gcc.x86_64 0:4.8.5-36.0.1.el7                    | gcc.x86_64 0:4.8.5-36.0.1.el7            | gcc.x86_64 0:4.8.5-36.0.1.el7                    | gcc.x86_64 0:4.8.5-36.0.1.el7                                | gcc.x86_64 0:4.8.5-36.0.1.el7                    |
| g++             | g++                                          | g++                                              | g++                                          | g++                                              | g++                                          | g++                                              | g++                                                          | g++                                              | g++                                          | g++                                              | g++                                          | g++                                              | g++                                      | g++                                              | g++                                                          | g++                                              |
| git             | git.x86_64 0:1.8.3.1-14.el7_5                | git.x86_64 0:1.8.3.1-20.el7                      | git.x86_64 0:1.8.3.1-14.el7_5                | git.x86_64 0:1.8.3.1-20.el7                      | git.x86_64 0:1.8.3.1-14.el7_5                | git.x86_64 0:1.8.3.1-20.el7                      | git.x86_64 0:1.8.3.1-14.el7_5                                | git.x86_64 0:1.8.3.1-14.el7_5                    | libtool.x86_64 0:2.4.2-22.el7_3              | git.x86_64 0:1.8.3.1-20.el7                      | git.x86_64 0:1.8.3.1-20.el7                  | git.x86_64 0:1.8.3.1-20.el7                      | git.x86_64 0:1.8.3.1-20.el7              | git.x86_64 0:1.8.3.1-20.el7                      | git.x86_64 0:1.8.3.1-14.el7_5                                | git.x86_64 0:1.8.3.1-20.el7                      |
| make            | make                                         | make                                             | make                                         | make                                             | make                                         | make                                             | make                                                         | make                                             | make                                         | make                                             | make                                         | make                                             | make                                     | make                                             | make                                                         | make                                             |
| ncurses devel   | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4 | ncurses-devel-5.9-14.20130511.el7_4              | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4 | ncurses-devel-5.9-14.20130511.el7_4              | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4 | ncurses-devel-5.9-14.20130511.el7_4              | ncurses-devel-5.9-14.20130511.el7_4                          | ncurses-devel-5.9-14.20130511.el7_4              | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4 | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4     | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4 | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4     | ncurses-devel-5.9-14.20130511.el7_4      | ncurses-devel.x86_64 0:5.9-14.20130511.el7_4     | ncurses-devel-5.9-14.20130511.el7_4                          | ncurses-devel-5.9-14.20130511.el7_4              |
| tftp server     | tftp-server                                  | tftp-server                                      | tftp-server                                  | tftp-server                                      | tftp-server                                  | tftp-server                                      | tftp-server                                                  | tftp-server                                      | tftp-server                                  | tftp-server                                      | tftp-server                                  | tftp-server                                      | tftp-server                              | tftp-server                                      | tftp-server                                                  | tftp-server                                      |
| openssl devel   | openssl-devel.x86_64 1:1.0.2k-12.el7         | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         | openssl-devel.x86_64 1:1.0.2k-12.el7         | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         | openssl-devel.x86_64 1:1.0.2k-12.el7         | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         | openssl-devel.x86_64 1:1.0.2k-12.0.3.el7                     | openssl-devel.x86_64 1:1.0.2k-12.el7             | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7     | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7     | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7 | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         | openssl-devel.x86_64 1:1.0.2k-12.0.3.el7                     | openssl-devel.x86_64 1:1.0.2k-16.0.1.el7         |
| zlib devel      | zlib-devel.x86_64 0:1.2.7-17.el7             | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7             | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7             | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7                             | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-18.el7             | zlib-devel.x86_64 0:1.2.7-18.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7             | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7         | zlib-devel.x86_64 0:1.2.7-17.el7                 | zlib-devel.x86_64 0:1.2.7-17.el7                             | zlib-devel.x86_64 0:1.2.7-17.el7                 |
| flex            | flex                                         | flex                                             | flex                                         | flex                                             | flex                                         | flex                                             | flex                                                         | flex                                             | flex                                         | flex                                             | flex                                         | flex                                             | flex                                     | flex                                             | flex                                                         | flex                                             |
| bison           | bison                                        | bison                                            | bison                                        | bison                                            | bison                                        | bison                                            | bison                                                        | bison                                            | bison                                        | bison                                            | bison                                        | bison                                            | bison                                    | bison                                            | bison                                                        | bison                                            |
| libselinux      | libselinux                                   | libselinux                                       | libselinux                                   | libselinux                                       | libselinux                                   | libselinux                                       | libselinux                                                   | libselinux                                       | libselinux                                   | libselinux                                       | libselinux                                   | libselinux                                       | libselinux                               | libselinux                                       | libselinux                                                   | libselinux                                       |
| gnupg           | gnupg                                        | gnupg                                            | gnupg                                        | gnupg                                            | gnupg                                        | gnupg                                            | gnupg                                                        | gnupg                                            | gnupg                                        | gnupg                                            | gnupg                                        | gnupg                                            | gnupg                                    | gnupg                                            | gnupg                                                        | gnupg                                            |
| wget            | wget                                         | wget                                             | wget                                         | wget                                             | wget                                         | wget                                             | wget                                                         | wget                                             | wget                                         | wget                                             | wget                                         | wget                                             | wget                                     | wget                                             | wget                                                         | wget                                             |
| diffstat        | diffstat.x86_64 0:1.57-4.el7                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7                                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7                 | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7             | diffstat.x86_64 0:1.57-4.el7                     | diffstat.x86_64 0:1.57-4.el7                                 | diffstat.x86_64 0:1.57-4.el7                     |
| chrpath         | chrpath.x86_64 0:0.16-0.el7                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7                                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7                  | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7              | chrpath.x86_64 0:0.16-0.el7                      | chrpath.x86_64 0:0.16-0.el7                                  | chrpath.x86_64 0:0.16-0.el7                      |
| socat           | socat.x86_64 0:1.7.3.2-2.el7                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7                                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7                 | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7             | socat.x86_64 0:1.7.3.2-2.el7                     | socat.x86_64 0:1.7.3.2-2.el7                                 | socat.x86_64 0:1.7.3.2-2.el7                     |
| xterm           | xterm.x86_64 0:295-3.el7                     | xterm.x86_64 0:295-3.el7                         | xterm.x86_64 0:295-3.el7                     | xterm.x86_64 0:295-3.el7                         | xterm.x86_64 0:295-3.el7                     | xterm.x86_64 0:295-3.el7                         | xterm.x86_64 0:295-3.el7                                     | xterm.x86_64 0:295-3.el7                         | xterm.x86_64 0:295-3.el7                     | xterm.x86_64 0:295-3.el7                         | xterm.x86_64 0:295-3.el7                     |                                                  | xterm.x86_64 0:295-3.el7                 | xterm.x86_64 0:295-3.el7                         | xterm.x86_64 0:295-3.el7                                     | xterm.x86_64 0:295-3.el7                         |
| libtool         | libtool.x86_64 0:2.4.2-22.el7_3              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3                              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3              | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3          | libtool.x86_64 0:2.4.2-22.el7_3                  | libtool.x86_64 0:2.4.2-22.el7_3                              | libtool.x86_64 0:2.4.2-22.el7_3                  |
| autoconf        | autoconf.noarch 0:2.69-11.el7                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7                                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7                | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7            | autoconf.noarch 0:2.69-11.el7                    | autoconf.noarch 0:2.69-11.el7                                | autoconf.noarch 0:2.69-11.el7                    |
| tar             | tar                                          | tar                                              | tar                                          | tar                                              | tar                                          | tar                                              | tar                                                          | tar                                              | tar                                          | tar                                              | tar                                          | tar                                              | tar                                      | tar                                              | tar                                                          | tar                                              |
| unzip           | unzip                                        | unzip                                            | unzip                                        | unzip                                            | unzip                                        | unzip                                            | unzip                                                        | unzip                                            | unzip                                        | unzip                                            | unzip                                        | unzip                                            | unzip                                    | unzip                                            | unzip                                                        | unzip                                            |
| texinfo         | texinfo.x86_64 0:5.1-5.el7                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7                                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7                   | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7               | texinfo.x86_64 0:5.1-5.el7                       | texinfo.x86_64 0:5.1-5.el7                                   | texinfo.x86_64 0:5.1-5.el7                       |
| zlib1g-dev      |                                              |                                                  |                                              |                                                  |                                              |                                                  |                                                              |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |                                                              |                                                  |
| gzip            | gzip                                         | gzip                                             | gzip                                         | gzip                                             | gzip                                         | gzip                                             | gzip                                                         | gzip                                             | gzip                                         | gzip                                             | gzip                                         | gzip                                             | gzip                                     | gzip                                             | gzip                                                         | gzip                                             |
| libsdl1.2-dev   |                                              |                                                  |                                              |                                                  |                                              |                                                  |                                                              |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |                                                              |                                                  |
| automake        | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                     | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                     | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                     | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7                            | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                     | automake-1.13.4-3.el7.noarch                 | automake-1.13.4-3.el7.noarch                     | automake-1.13.4-3.el7.noarch             | automake-1.13.4-3.el7.noarch                     | automake-1.13.4-3.el7.noarch                                 | automake-1.13.4-3.el7.noarch                     |
| libglib2.0-dev  | glib2-devel.x86_64 0:2.54.2-2.el7            | glib2-devel.x86_64 0:2.54.2-2.el7                | glib2-devel.x86_64 0:2.54.2-2.el7            | glib2-devel.x86_64 0:2.54.2-2.el7                | glib2-devel.x86_64 0:2.54.2-2.el7            | glib2-devel.x86_64 0:2.54.2-2.el7                | glib2-devel.x86_64 0:2.54.2-2.el7 or glib2-devel.x86_64 0:2.56.1-2.el7 | glib2-devel.x86_64 0:2.54.2-2.el7                | glib2-devel.x86_64 0:2.54.2-2.el7            | glib2-devel.x86_64 0:2.56.1-2.el7                | glib2-devel.x86_64 0:2.56.1-2.el7            | glib2-devel.x86_64 0:2.56.1-2.el7                | glib2-devel.x86_64 0:2.56.1-2.el7        | glib2-devel.x86_64 0:2.56.1-2.el7                | glib2-devel.x86_64 0:2.54.2-2.el7 or glib2-devel.x86_64 0:2.56.1-2.el7 | glib2-devel.x86_64 0:2.56.1-2.el7                |
| pax             | pax                                          | pax                                              | pax                                          | pax                                              | pax                                          | pax                                              | pax                                                          | pax                                              | pax                                          | pax                                              | pax                                          | pax                                              | pax                                      | pax                                              | pax                                                          | pax                                              |
| patch           | patch.x86_64 0:2.7.1-10.el7_5                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5                                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5                | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5            | patch.x86_64 0:2.7.1-10.el7_5                    | patch.x86_64 0:2.7.1-10.el7_5                                | patch.x86_64 0:2.7.1-10.el7_5                    |
| gcc-c++         | gcc-c++.x86_64 0:4.8.5-36.0.1.el7            | gcc-c++.x86_64 0:4.8.5-28.el7_5.1                | gcc-c++.x86_64 0:4.8.5-28.0.1.el7_5.1        | gcc-c++.x86_64 0:4.8.5-28.el7_5.1                | gcc-c++.x86_64 0:4.8.5-28.el7_5.1            | gcc-c++.x86_64 0:4.8.5-28.el7_5.1                | gcc-c++.x86_64 0:4.8.5-28.0.1.el7_5.1 or gcc-c++.x86_64 0:4.8.5-36.0.1.el7 | gcc-c++.x86_64 0:4.8.5-28.el7_5.1                | gcc-c++.x86_64 0:4.8.5-36.0.1.el7            | gcc-c++.x86_64 0:4.8.5-36.0.1.el7                | gcc-c++.x86_64 0:4.8.5-36.0.1.el7            | gcc-c++.x86_64 0:4.8.5-36.0.1.el7                | gcc-c++.x86_64 0:4.8.5-36.0.1.el7        | gcc-c++.x86_64 0:4.8.5-36.0.1.el7                | gcc-c++.x86_64 0:4.8.5-28.0.1.el7_5.1 or gcc-c++.x86_64 0:4.8.5-36.0.1.el7 | gcc-c++.x86_64 0:4.8.5-36.0.1.el7                |
| screen          |                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                          | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |                                                              | screen.x86_64 0:4.1.0-0.25.20120314git3c2946.el7 |
| python          |                                              |                                                  |                                              |                                                  |                                              |                                                  |                                                              |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |                                                              |                                                  |
| build-essential |                                              |                                                  |                                              |                                                  |                                              |                                                  |                                                              |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |                                                              |                                                  |
| gcc-multilib    |                                              |                                                  |                                              |                                                  |                                              |                                                  |                                                              |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |                                                              |                                                  |
| libglib2.0-dev  |                                              |                                                  |                                              |                                                  |                                              |                                                  |                                                              |                                                  |                                              |                                                  |                                              |                                                  |                                          |                                                  |                                                              |                                                  |

### Ubuntu

| Library/Package | Ubuntu 16.04.4 (workstation) | Ubuntu 16.04.4  (server) |
| --------------- | ---------------------------- | ------------------------ |
| dos2unix        | dos2unix                     | dos2unix                 |
| ip              | iproute                      | iproute                  |
| gawk            | gwk:1:4.1.3+dfsg-0.1         | gawk                     |
| gcc             | gcc                          | gcc                      |
| g++             | g++                          | g++                      |
| git             | git                          | git                      |
| make            | make                         | make                     |
| ncurses devel   | ncurses-devel                | libncurses-dev           |
| tftp server     | tftp-server                  | tftp-server              |
| openssl devel   | openssl-devel                | openssl                  |
| zlib devel      | zlib-devel                   | zlib-devel               |
| flex            | flex                         | flex                     |
| bison           | bison                        | bison                    |
| libselinux      | libselinux                   | libselinux               |
| gnupg           | gnupg                        | gnupg                    |
| wget            | wget                         | wget                     |
| diffstat        | diffstat                     | diffstat                 |
| chrpath         | chrpath                      | chrpath                  |
| socat           | 1.7.3.1-1                    | socat                    |
| xterm           | xterm                        | xterm                    |
| libtool         | libtool                      | libtool                  |
| autoconf        | autoconf                     | autoconf                 |
| tar             | tar                          | tar                      |
| unzip           | unzip                        |                          |
| texinfo         | texinfo                      | unzip                    |
| zlib1g-dev      |                              | zlib1g-dev               |
| gzip            | gzip                         | gzip                     |
| libsdl1.2-dev   |                              | libsdl1.2-dev            |
| automake        | automake                     | automake                 |
| libglib2.0-dev  | libglib2.0-dev               | glib2-devel              |
| pax             | pax                          | pax                      |
| patch           | patch                        | patch                    |
| gcc-c++         | gcc-c++                      | gcc-c++                  |
| screen          |                              | screen                   |
| python          |                              | python                   |
| build-essential |                              | build-essential          |
| gcc-multilib    |                              | gcc-multilib             |
| libglib2.0-dev  |                              | libglib2.0-dev           |