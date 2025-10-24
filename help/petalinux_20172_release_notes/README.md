# 69372 - PetaLinux 2017.2 - Product Update Release Notes and Known Issues



## Title

69372 - PetaLinux 2017.2 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2017.2 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**BSPs supported for 2017.2 PetaLinux Release**

This table contains supported BSPs for Zynq-7000, MicroBlaze, Zynq UltraScale+ MPSoC available on the Embedded Development [download page](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).



| Platform               | Variant                   | BSP Name                   |
| :--------------------- | :------------------------ | :------------------------- |
| Zynq-7000              | ZC702                     | ZC702 BSP                  |
| Zynq-7000              | ZC706                     | ZC706 BSP                  |
| Zynq-7000              | ZEDBOARD                  | ZED BSP                    |
| MicroBlaze             | AC701                     | AC701 BSP                  |
| MicroBlaze             | KCU105                    | KCU105                     |
| MicroBlaze             | KC705                     | KC705 BSP                  |
| Zynq UltraScale+ MPSoC | ZCU102 production silicon | ZCU102 BSP (prod-silicon)  |
| Zynq UltraScale+ MPSoC | ZCU102 ZU9 ES2 Rev 1.0    | ZCU102-ZU9-ES2 Rev 1.0 BSP |



BSPs for earlier boards with ES Silicon can be found at:



- ZCU102 ES1 Rev D BSP - [Headstart Lounge](https://www.xilinx.com/member/zcu102_headstart.html)
- ZCU102 ES2 Rev D BSP - [EA Lounge](https://www.xilinx.com/member/zcu102_ea.html)



**Note**: The "[sstate cache file](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate-rel-v2017.2.tar.gz&akdm=1)" (sstate-rel-v2017.2.tar.gz) can be found on the Xilinx download area along with an associated [README](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate_rel_2017.2_README&akdm=1) file that outlines the procedure to use "sstate cache".

Refer to the attached file "2017.2-PetaLinux-Packages-List" for software package versions tested on host machines, which is required for PetaLinux installation tools.

**PetaLinux 2017.2 contains the following build collateral:**

| Component                  | Git repo                                                     | Branches/Tag   | Commit ID                                  | Comments                                                     |
| :------------------------- | :----------------------------------------------------------- | :------------- | :----------------------------------------- | :----------------------------------------------------------- |
| FSBL                       | git://github.com/Xilinx/embeddedsw.git                       | xilinx-v2017.2 | "33ee700baafc0868aee2d984724f1a916f93107d" | FSBL for Zynq7000 is at `embeddedsw/lib/sw_apps/zynq_fsbl`<br>FSBL for Zynq UltraScale+ is at `embeddedsw/lib/sw_apps/zynqmp_fsbl` |
| PMU Firmware               | git://github.com/Xilinx/embeddedsw.git                       | xilinx-v2017.2 | "e9ea9a1fef3afaca0fbaa1250507d4f9f7080f06" | PMU for Zynq UltraScale+ Firmware is at `embeddedsw/lib/sw-apps/zynqmp_pmufw` |
| Device-tree                | git://github.com/Xilinx/device-tree-xlnx.git                 | xilinx-v2017.2 | "43551819a116e862d8cc796755f81586ecaca666" |                                                              |
| Linux                      | git://github.com/Xilinx/linux-xlnx.git                       | xilinx-v2017.2 | "5d029fdc257cf88e65500db348eda23040af332b" | Kernel Version 4.9                                           |
| U-Boot                     | git://github.com/Xilinx/u-boot-xlnx.git                      | xilinx-v2017.2 | "5290eb544b8659d957d3b8fd2ba890e9575007e4" | U-Boot Version 2017.01                                       |
| QEMU                       | git://github.com/Xilinx/qemu.git                             | xilinx-v2017.2 | "4987c78c6c7cf370ba1c456f67278df6daae6bbc" |                                                              |
| Xen                        | git://github.com/Xilinx/xen.git                              | xilinx-v2017.2 | "ba8ea4d7d843673f494e6cc277f119441ec7f77c" |                                                              |
| ARM-Trusted-Firmware (ATF) | git://github.com/Xilinx/arm-trusted-firmware.git             | xilinx-v2017.2 | "0d9d51a17f7ba2c1e5864e196047a170d341796e" | ATF is based on upstream version 1.3                         |
| Yocto                      | git://github.com/Xilinx/meta-xilinx.git<br>git://github.com/Xilinx/meta-xilinx-tools.git<br>git://github.com/Xilinx/meta-petalinux.git | rel-v2017.2    |                                            | Yocto 2.2 Morty                                              |
| qemu-devicetrees           | git://github.com/Xilinx/qemu-devicetrees.git                 | xilinx-v2017.2 | "f20f92ccd95245b88ffbf25f819a1669d2f37443" |                                                              |
| OpenAMP                    | git://github.com/Xilinx/open-amp.git                         | xilinx-v2017.2 | "d859dc047a93f2ce01d230f6bff0f3236201d9d4" |                                                              |
| libmetal                   | git://github.com/Xilinx/libmetal.git                         | xilinx-v2017.2 | "6b697b77a37c96e1e0105dcc3a4231e24e7f3949" |                                                              |
| GCC                        |                                                              |                |                                            | MB compiler version 6.2<br>ARM 6.2                           |

**Wiki Updates:**

Covers details for Linux Kernel, Device drivers, U-boot and DTG changes (new features/fixes) in a particular release.

**2017.2 Linux and DTG release notes wiki page:**



http://www.wiki.xilinx.com/2017.2+Linux+and+DTG+Release+Notes

**2017.2 U-Boot release notes wiki page :**





http://www.wiki.xilinx.com/2017.2+U-boot+Release+Notes



**PetaLinux 2017.2 New Features:**



**PetaLinux**



- None
- For more details please see [(UG1144)](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1144-petalinux-tools-reference-guide.pdf), [(UG1156)](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1156-petalinux-tools-workflow-tutorial.pdf) and [(UG1157)](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1157-petalinux-tools-command-line-guide.pdf).

**Yocto**



- None





**FSBL**



- None



**U-boot**



- Provide ondie-ECC NAND support in u-boot

**Device-tree**



- None



**ARM-Trusted Firmware (ATF)**





- None



**FreeRTOS**



- None



**PMU Firmware (PMUFW)**



- None



**Power Management**



- None



**Standalone**



- Float Support in R5 Bare Metal BSP



**Linux Drivers**



- None



**Known Issues for 2017.2:**

| Linux/Standalone | Application | Description                                                  | Work-around           | To be fixed version |
| :--------------- | :---------- | :----------------------------------------------------------- | :-------------------- | :------------------ |
| Linux            | PetaLinux   | 2017.1/2 Zynq UltraScale+ MPSoC: PetaLinux fails to build PMU Firmware on CentOS 7.2/3 | (Xilinx Answer 69293) | 2017.3              |
| Linux            | PetaLinux   | 2017.1/2 Zynq UltraScale+ MPSoC: PetaLinux QEMU boot without pmufw options issues wrong arguments to QEMU | (Xilinx Answer 69400) | 2017.3              |
| Linux            | XEN         | 2017.1/2 Zynq UltraScale+ MPSoC: XEN LWIP echo server application doesn't work on EL1-NS DomU guest. | (Xilinx Answer 69398) | 2017.3              |
| Linux            | Drivers     | 2017.1/2 Zynq UltraScale+ MPSoC: Linux SATA Suspend/Resume calls doesn't work when FPD is off | (Xilinx Answer 69385) | 2017.3              |
| Linux            | Drivers     | 2017.1/2 Zynq UltraScale+ MPSoC: Linux Power Management Ethernet does not work after suspend-resume cycle | (Xilinx Answer 69101) | 2017.3              |
| Linux            | Drivers     | 2017.1/2 Zynq UltraScale+ MPSoC: Linux AXI Ethernet 1000Basex and SGMII ping does not work after doing ifdown eth0 and ifup eth0 | (Xilinx Answer 69388) | 2017.3              |
| Linux            | Drivers     | 2017.1/2 Zynq UltraScale+ MPSoC: Linux MACB MDIO support for single MAC managing multiple PHYs | (Xilinx Answer 69132) | 2017.3              |
| Linux            | PetaLinux   | 2017.1/2 PetaLinux: Symbolic links are added to the kernel source tree when external source is selected in petalinux-config | (Xilinx Answer 69373) | 2017.3              |
| Linux            | PetaLinux   | 2017.1/2 Zynq UltraScale+ MPSoC: PetaLinux Kernel is configured differently when remote or external source is selected in petalinux-config | (Xilinx Answer 69387) | 2017.3              |
| Linux            | U-boot      | 2017.1/2 Zynq UltraScale+ MPSoC: U-Boot support to load encrypted bitstream | (Xilinx Answer 69383) | 2017.3              |
| Linux            | U-boot      | 2017.2 Zynq UltraScale+ MPSoC: U-boot 'sf test' command failed for QSPI x4 at 100Mhz | (Xilinx Answer 69381) | 2017.3              |
| Linux            | U-boot      | 2017.2 Zynq UltraScale+ MPSoC: U-boot takes too long to copy the Linux images from QSPI to DDR | (Xilinx Answer 69382) | 2017.3              |
| Linux            | PetaLinux   | 2017.1/2 Zynq UltraScale+ MPSoC: DFU utility not detected or enabled in PetaLinux U-boot and Linux | (Xilinx Answer 69378) | 2017.3              |
| Linux            | Drivers     | 2017.1/2 Zynq UltraScale+ MPSoC: Linux USB controller in 3.0 Host Mode fails to resume suspended USB 2.0 device | (Xilinx Answer 69375) | 2017.3              |
| Linux            | Drivers     | 2017.1/2 Zynq UltraScale+ MPSoC: Linux USB-UVC playback works only once | (Xilinx Answer 69374) | 2017.3              |
| Linux            | PetaLinux   | 2017.1/2 Zynq UltraScale+ MPSoC: PetaLinux fails to build PMU Firmware when UART is not enabled in Vivado design | (Xilinx Answer 69406) | 2017.3              |
| Linux            | PetaLinux   | 2017.1/2 PetaLinux: GIT Version control files committed for PetaLinux project causes build error | (Xilinx Answer 69415) | 2017.3              |
| Linux            | PetaLinux   | 2016.4/2017.1 PetaLinux: Static IP assignment in PetaLinux menu config "Subsystem AUTO Hardware Settings" not working | (Xilinx Answer 69119) | 2017.3              |
| Linux            | PetaLinux   | 2016.4/2017.1 MicroBlaze: PetaLinux ssh command failed to connect to MicroBlaze boards from host machine | (Xilinx Answer 69121) | 2017.3              |
| Linux            | PetaLinux   | 2016.4 PetaLinux: Build (petalinux-build) failure when using ddr3 in the Kintex design | (Xilinx Answer 69106) | 2017.3              |
| Linux            | PetaLinux   | 2017.1 PetaLinux: Xen images built by PetaLinux do not work as expected | (Xilinx Answer 69105) | 2017.3              |
| Linux            | PetaLinux   | 2017.1 Zynq UltraScale+ MPSoC: PetaLinux fails to build and configure U-Boot | (Xilinx Answer 69112) | 2017.3              |
| Linux            | Drivers     | 2017.1/2 Zynq UltraScale+ MPSoC: Linux kernel crash from EDAC driver | (Xilinx Answer 69433) | 2017.3              |
| Linux            | Drivers     | 2017.1/2 Zynq UltraScale+ MPSoC: Linux Watch Dog Timer (WDT) driver does not reset after reset-on-timeout is kicked off | (Xilinx Answer 69423) | 2017.3              |
| Linux            | Device-tree | 2017.1/2 Zynq UltraScale+ MPSoC: Linux hangs when accessing PL peripheral generated by yocto | (Xilinx Answer 69587) | 2018.1              |
| Linux            | PetaLinux   | 2017.1/2 Zynq UltraScale+ MPSoC: PetaLinux PSS_REF_CLK binding issue | (Xilinx Answer 69395) | 2017.3              |
| Linux            | PetaLinux   | 2016.4-2017.2 Kintex UltraScale+: PetaLinux build error when using DDR3 in the Kintex design | (Xilinx Answer 69106) | 2017.3              |
| Linux            | PetaLinux   | 2017.1/2 Zynq UltraScale+ MPSoC: PetaLinux fails to build and configure U-Boot | (Xilinx Answer 69112) | 2017.3              |
| Linux            | PetaLinux   | 2017.1/2 PetaLinux: Xen images built by PetaLinux do not work as expected | (Xilinx Answer 69105) | 2017.3              |
| Linux            | XSDK        | 2017.1-2017.3 Zynq UltraScale+ MPSoC: Connecting XSDB to Linux CPU idle | (Xilinx Answer 69143) | 2017.4              |

# 2017.2-Petalinux-Packages-List

## Tool/Library Versions

### RHEL/CentOS versions

| Tool/Library                                                 | CentOS 7.2                                                  | CentOS 7.3                                                   | CentOS 6.7                                                   | CentOS 6.8                                                   | RHEL 7.2                                                  | RHEL 7.3                                                     | RHEL 6.7                                                     | RHEL 6.8                                                     |
| ------------------------------------------------------------ | ----------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| kernel Version                                               | 3.10.0-514.21.2.el7.x86_64                                  | 3.10.0-514.el7.x86_64                                        | 2.6.32-573.el6.x86_64                                        | 2.6.32-642.el6.x86_64                                        | 3.10.0-327.el7.x86_64                                     | 3.10.0-514.el7.x86_64                                        |                                                              | 2.6.32-642.el6.x86_64                                        |
| python                                                       | python 3.4.0                                                | python 3.4.0                                                 | python 3.4.0                                                 | python 3.4.0                                                 | python 3.4.0                                              | python 3.4.0                                                 | python 3.4.0                                                 | python 3.4.0                                                 |
| dos2unix                                                     | dos2unix-6.0.3-4.el7.x86_64                                 | dos2unix-3.1-37.el6.x86_64                                   | dos2unix-3.1-37.el6.x86_64                                   | dos2unix-3.1-37.el6.x86_64                                   | dos2unix-6.0.3-4.el7.x86_64                               | dos2unix-6.0.3-4.el7.x86_64                                  | dos2unix-3.1-37.el6.x86_64                                   | dos2unix-3.1-37.el6.x86_64                                   |
| ip (iproute)                                                 | iproute-3.10.0-74.0.1.el7.x86_64                            | iproute-3.10.0-74.el7.x86_64                                 | iproute-2.6.32-54.el6.x86_64                                 | iproute-2.6.32-54.el6.x86_64                                 | iproute-3.10.0-74.0.1.el7.x86_64                          | iproute-3.10.0-74.0.1.el7.x86_64                             | iproute-2.6.32-54.0.1.el6.x86_64                             | iproute-2.6.32-54.0.1.el6.x86_64                             |
| gawk                                                         | gawk-4.0.2-4.el7.x86_64                                     | gawk-4.0.2-4.el7.x86_64                                      | gawk-3.1.7-10.el6_7.3.x86_64                                 | gawk-3.1.7-10.el6_7.3.x86_64                                 | gawk-4.0.2-4.el7.x86_64                                   | gawk-4.0.2-4.el7.x86_64                                      | gawk-3.1.7-10.el6_7.3.x86_64                                 | gawk-3.1.7-10.el6_7.3.x86_64                                 |
| xvfb                                                         | xorg-x11-server-Xvfb-1.17.2-22.el7.x86_64                   | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                     | xorg-x11-server-Xvfb-1.17.4-9.5.el6.centos.x86_64            | xorg-x11-server-Xvfb-1.17.4-9.5.el6.centos.x86_64            | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                  | xorg-x11-server-Xvfb-1.15.0-7.el7.x86_64                     | xorg-x11-server-Xvfb-1.17.4-9.5.el6.centos.x86_64            | xorg-x11-server-Xvfb-1.17.4-9.5.el6.centos.x86_64            |
| gcc(for RHEL,  use devtoolset-2)                             | gcc-4.8.5-11.el7.x86_64                                     | gcc-4.8.5-11.el7.x86_64                                      | gcc-4.4.7-18.el6.x86_64                                      | gcc-4.4.7-18.el6.x86_64                                      | gcc-4.8.5-11.el7.x86_64                                   | gcc-4.8.5-11.el7.x86_64                                      | gcc-4.4.7-18.el6.x86_64                                      | gcc-4.4.7-18.el6.x86_64                                      |
| git                                                          | git-1.8.3.1-6.el7_2.1.x86_64                                | git-1.8.3.1-6.el7_2.1.x86_64                                 | git-1.7.1-8.el6.x86_64                                       | git-1.7.1-8.el6.x86_64                                       | git-1.8.3.1-6.el7_2.1.x86_64                              | git-1.8.3.1-6.el7_2.1.x86_64                                 | git-1.7.1-8.el6.x86_64                                       | git-1.7.1-8.el6.x86_64                                       |
| make                                                         | make-3.82-23.el7.x86_64                                     | make-3.82-23.el7.x86_64                                      | make-3.81-23.el6.x86_64                                      | make-3.81-23.el6.x86_64                                      | make-3.82-23.el7.x86_64                                   | make-3.82-23.el7.x86_64                                      | make-3.81-23.el6.x86_64                                      | make-3.81-23.el6.x86_64                                      |
| netstat (net-tools)                                          | net-tools-2.0-0.17.20131004git.el7.x86_64                   | net-tools-2.0-0.20150915git.4.mga6.x86_64                    | net-tools-1.60-114.el6.x86_64                                | net-tools-1.60-110.el6_2.x86_64                              | net-tools-2.0-0.17.20131004git.el7.x86_64                 | net-tools-2.0-0.17.20131004git.el7.x86_64                    | net-tools-1.60-114.el6.x86_64                                | net-tools-1.60-114.el6.x86_64                                |
| ncurses-devel                                                | ncurses-devel-5.9-13.20130511.el7.x86_64                    | ncurses-devel-5.9-13.20130511.el7.x86_64                     | ncurses-devel-5.7-4.20090207.el6.x86_64                      | ncurses-devel-5.7-4.20090207.el6.x86_64                      | ncurses-devel-5.9-13.20130511.el7.x86_64                  | ncurses-devel-5.9-13.20130511.el7.x86_64                     | ncurses-devel-5.7-4.20090207.el6.x86_64                      | ncurses-devel-5.7-4.20090207.el6.x86_64                      |
| tftp-server                                                  | tftp-server-5.2-13.el7.x86_64                               | tftp-server-0.49-8.el6.x86_64                                | tftp-server-0.49-8.el6.x86_64                                |                                                              | tftp-server-5.2-13.el7.x86_64                             | tftp-server-5.2-13.el7.x86_64                                |                                                              |                                                              |
| zlib-devel(also,install  32-bit of this version)             | zlib-devel-1.2.7-17.el7.x86_64 zlib-devel-1.2.7-17.el7.i686 | zlib-devel-1.2.7-17.el7.x86_64                               | zlib-devel-1.2.3-29.el6.x86_64                               | zlib-devel-1.2.3-29.el6.x86_64                               | zlib-devel-1.2.7-17.el7.x86_64                            | zlib-devel-1.2.7-17.el7.x86_64 zlib-devel-1.2.7-17.el7.i686  | zlib-devel-1.2.3-29.el6.x86_64                               | zlib-devel-1.2.3-29.el6.x86_64                               |
| openssl-devel                                                | openssl-devel-1.0.1e-60.0.1.el7_3.1.x86_64                  | openssl-devel-1.0.1e-60.el7.x86_64                           | openssl-devel-1.0.1e-57.el6.x86_64                           | openssl-devel-1.0.1e-57.el6.x86_64                           | openssl-devel-1.0.1e-60.el7_3.1.x86_64                    | openssl-devel-1.0.1e-60.0.1.el7_3.1.x86_64                   | openssl-devel-1.0.1e-57.el6.x86_64                           | openssl-devel-1.0.1e-57.el6.x86_64                           |
| flex                                                         | flex-2.5.37-3.el7.x86_64                                    | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.35-9.el6.x86_64                                     | flex-2.5.35-9.el6.x86_64                                     | flex-2.5.37-3.el7.x86_64                                  | flex-2.5.37-3.el7.x86_64                                     | flex-2.5.35-9.el6.x86_64                                     | flex-2.5.35-9.el6.x86_64                                     |
| bison                                                        | bison-2.7-4.el7.x86_64                                      | bison-2.7-4.el7.x86_64                                       | bison-2.4.1-5.el6.x86_64                                     | bison-2.4.1-5.el6.x86_64                                     | bison-2.7-4.el7.x86_64                                    |                                                              | bison-2.4.1-5.el6.x86_64                                     | bison-2.4.1-5.el6.x86_64                                     |
| libselinux                                                   | libselinux-2.5-6.el7.x86_64                                 | libselinux-2.5-6.el7.x86_64                                  | libselinux-2.0.94-7.el6.x86_64                               | libselinux-2.0.94-7.el6.x86_64                               | libselinux-2.5-6.el7.x86_64                               | libselinux-2.5-6.el7.x86_64                                  | libselinux-2.0.94-7.el6.x86_64                               | libselinux-2.0.94-7.el6.x86_64                               |
| gnupg                                                        | gnupg-1.4.21                                                | gnupg-1.4.21                                                 | gnupg-1.4.13-2.1.x86_64.rpm                                  | gnupg-1.4.13-2.1.x86_64.rpm                                  | gnupg-1.4.21                                              |                                                              |                                                              |                                                              |
| wget                                                         | wget-1.14-13.el7.x86_64                                     | wget-1.14-13.el7.x86_64                                      | wget-1.12-10.el6.x86_64                                      | wget-1.12-10.el6.x86_64                                      | wget-1.14-13.el7.x86_64                                   | wget-1.14-13.el7.x86_64                                      | wget-1.12-10.el6.x86_64                                      | wget-1.12-10.el6.x86_64                                      |
| diffstat                                                     | diffstat-1.57-4.el7.x86_64                                  | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.51-2.el6.x86_64                                   | diffstat-1.51-2.el6.x86_64                                   | diffstat-1.57-4.el7.x86_64                                | diffstat-1.57-4.el7.x86_64                                   | diffstat-1.51-2.el6.x86_64                                   | diffstat-1.51-2.el6.x86_64                                   |
| chrpath                                                      | chrpath-0.13-14.el7.x86_64                                  | chrpath-0.13-14.el7.x86_64                                   | chrpath-0.13-7.el6.x86_64                                    | chrpath-0.13-7.el6.x86_64                                    | chrpath-0.13-14.el7.x86_64                                | chrpath-0.13-14.el7.x86_64                                   | chrpath-0.13-7.el6.x86_64                                    | chrpath-0.13-7.el6.x86_64                                    |
| socat                                                        | socat-1.7.2.2-5.el7.x86_64                                  | socat-1.7.2.2-5.el7.x86_64                                   | socat-1.7.2.3-1.el6.x86_64                                   | socat-1.7.1.3-1.el6.rf.x86_64                                | socat-1.7.2.2-5.el7.x86_64                                | socat-1.7.2.2-5.el7.x86_64                                   | socat-1.7.2.3-1.el6.x86_64                                   | socat-1.7.2.3-1.el6.x86_64                                   |
| xterm                                                        | xterm-295-3.el7.x86_64                                      | xterm-295-3.el7.x86_64                                       | xterm-253-1.el6.x86_64                                       | xterm-253-1.el6.x86_64                                       | xterm-295-3.el7.x86_64                                    | xterm-295-3.el7.x86_64                                       | xterm-253-1.el6.x86_64                                       | xterm-253-1.el6.x86_64                                       |
| autoconf                                                     | autoconf-2.69-11.el7.noarch                                 | autoconf-2.69-11.el7.noarch                                  | autoconf-2.63-5.1.el6.noarch                                 | autoconf-2.63-5.1.el6.noarch                                 | autoconf-2.69-11.el7.noarch                               | autoconf-2.69-11.el7.noarch                                  | autoconf-2.63-5.1.el6.noarch                                 | autoconf-2.63-5.1.el6.noarch                                 |
| libtool                                                      | libtool-2.4.2-22.el7_3.x86_64                               | libtool-2.4.2-21.el7_2.x86_64                                | libtool-2.2.6-15.5.el6.x86_64                                | libtool-2.2.6-15.5.el6.x86_64                                | libtool-2.4.2-22.el7_3.x86_64                             | libtool-2.4.2-22.el7_3.x86_64                                | libtool-2.2.6-15.5.el6.x86_64                                | libtool-2.2.6-15.5.el6.x86_64                                |
| tar                                                          | tar-1.26-31.el7.x86_64                                      | tar-1.26-31.el7.x86_64                                       | tar-1.23-15.el6_8.x86_64                                     | tar-1.23-14.el6.x86_64                                       | tar-1.26-31.el7.x86_64                                    | tar-1.26-31.el7.x86_64                                       | tar-1.23-14.el6.x86_64                                       | tar-1.23-14.el6.x86_64                                       |
| unzip                                                        | unzip-6.0-16.el7.x86_64                                     | unzip-6.0-16.el7.x86_64                                      | unzip-6.0-5.el6.x86_64                                       | unzip-6.0-5.el6.x86_64                                       | unzip-6.0-16.el7.x86_64                                   | unzip-6.0-16.el7.x86_64                                      | unzip-6.0-5.el6.x86_64                                       | unzip-6.0-5.el6.x86_64                                       |
| texinfo                                                      | texinfo-5.1-4.el7.x86_64                                    | texinfo-5.1-4.el7.x86_64                                     | texinfo-4.13a-8.el6.x86_64                                   | texinfo-4.13a-8.el6.x86_64                                   | texinfo-5.1-4.el7.x86_64                                  | texinfo-5.1-4.el7.x86_64                                     | texinfo-4.13a-8.el6.x86_64                                   | texinfo-4.13a-8.el6.x86_64                                   |
| zlib1g-dev                                                   |                                                             |                                                              |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |
| gcc-multilib                                                 |                                                             |                                                              |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |
| build-essential                                              |                                                             |                                                              |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |
| libsdl1.2-dev                                                |                                                             |                                                              |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |
| libglib2.0-dev                                               |                                                             |                                                              |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |
| SDL-devel                                                    | SDL-devel-1.2.15-14.el7.x86_64                              | SDL-devel-1.2.15-14.el7.x86_64                               | SDL-devel-1.2.14-7.el6_7.1.x86_64                            | SDL-devel-1.2.14-7.el6_7.1.x86_64                            | SDL-devel-1.2.15-14.el7.x86_64                            | SDL-devel-1.2.15-14.el7.i686                                 | SDL-devel-1.2.14-7.el6_7.1.x86_64                            | SDL-devel-1.2.14-7.el6_7.1.x86_64                            |
| glibc-devel                                                  | glibc-devel-2.17-157.el7_3.4.x86_64                         | glibc-devel-2.17-157.el7_3.4.i686 glibc-devel-2.17-157.el7_3.4.x86_64 | glibc-devel-2.12-1.209.el6_9.2.x86_64                        | glibc-devel-2.12-1.209.el6_9.2.x86_64                        | glibc-devel-2.17-157.el7_3.4.x86_64                       | glibc-devel-2.17-157.el7_3.4.x86_64 glibc-devel-2.17-157.el7_3.4.i686 | glibc-devel-2.12-1.209.0.3.el6_9.2.x86_64 glibc-devel-2.12-1.209.0.3.el6_9.2.i686 | glibc-devel-2.12-1.209.0.3.el6_9.2.x86_64 glibc-devel-2.12-1.209.0.3.el6_9.2.i686 |
| 32-bit glibc                                                 | glibc-2.17-157.el7_3.4.i686 glibc-2.17-157.el7_3.4.x86_64   | glibc-2.17-157.el7_3.4.i686 glibc-2.17-157.el7_3.4.x86_64    | glibc-2.12-1.209.el6_9.2.x86_64 glibc-2.12-1.209.el6_9.2.i686 | glibc-2.12-1.209.el6_9.2.x86_64 glibc-2.12-1.209.el6_9.2.i686 | glibc-2.17-157.el7_3.4.x86_64 glibc-2.17-157.el7_3.4.i686 | glibc-2.17-157.el7_3.4.x86_64 glibc-2.17-157.el7_3.4.i686    | glibc-2.12-1.209.0.3.el6_9.2.x86_64 glibc-2.12-1.209.0.3.el6_9.2.i686 | glibc-2.12-1.209.0.3.el6_9.2.x86_64 glibc-2.12-1.209.0.3.el6_9.2.i686 |
| glib2-devel                                                  | glib2-devel-2.46.2-4.el7.x86_64                             | glib2-devel-2.46.2-4.el7.x86_64                              | glib2-devel-2.28.8-9.el6.x86_64                              | glib2-devel-2.28.8-9.el6.x86_64                              | glib2-devel-2.46.2-4.el7.x86_64                           | glib2-devel-2.46.2-4.el7.x86_64                              | glib2-devel-2.28.8-9.el6.x86_64                              | glib2-devel-2.28.8-9.el6.x86_64                              |
| automake                                                     | automake-1.13.4-3.el7.noarch                                | automake-1.13.4-3.el7.noarch                                 | automake-1.11.1-4.el6.noarch                                 | automake-1.11.1-4.el6.noarch                                 | automake-1.13.4-3.el7.noarch                              | automake-1.13.4-3.el7.noarch                                 | automake-1.11.1-4.el6.noarch                                 | automake-1.11.1-4.el6.noarch                                 |
| screen                                                       | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64            | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             | screen-4.0.3-19.el6.x86_64                                   | screen-4.0.3-19.el6.x86_64                                   | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64          | screen-4.1.0-0.23.20120314git3c2946.el7_2.x86_64             | screen-4.0.3-19.el6.x86_64                                   | screen-4.0.3-19.el6.x86_64                                   |
| pax                                                          | pax-3.4-19.el7.x86_64                                       |                                                              | pax-3.4-10.1.el6.x86_64                                      | pax-3.4-10.1.el6.x86_64                                      | pax-3.4-19.el7.x86_64                                     | pax-3.4-19.el7.x86_64                                        | pax-3.4-10.1.el6.x86_64                                      | pax-3.4-10.1.el6.x86_64                                      |
| gzip                                                         | gzip-1.5-8.el7.x86_64                                       | gzip-1.5-8.el7.x86_64                                        | gzip-1.3.12-24.el6.x86_64                                    | gzip-1.3.12-24.el6.x86_64                                    | gzip-1.5-8.el7.x86_64                                     | gzip-1.5-8.el7.x86_64                                        | gzip-1.3.12-24.el6.x86_64                                    | gzip-1.3.12-24.el6.x86_64                                    |
| devtoolset-2                                                 |                                                             |                                                              | devtoolset-2-2.1-4.el6.noarch                                | devtoolset-2-2.1-4.el6.noarch                                |                                                           |                                                              | devtoolset-2-2.1-4.el6.noarch                                | devtoolset-2-2.1-4.el6.noarch                                |
| libz.so.1                                                    |                                                             | libz.so.1                                                    |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |
| libstdc++                                                    | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686   | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686    | libstdc++-4.4.7-18.el6.i686                                  | libstdc++-4.4.7-18.el6.i686                                  | libstdc++-4.8.5-11.el7.x86_64 libstdc++-4.8.5-11.el7.i686 | libstdc++-4.8.5-11.el7.i686                                  |                                                              |                                                              |
| g++ (gcc-c++)                                                | gcc-c++-4.8.5-11.el7.x86_64                                 | gcc-c++-4.8.5-11.el7.x86_64                                  | gcc-c++-4.4.7-18.el6.x86_64                                  | gcc-c++-4.4.7-18.el6.x86_64                                  | gcc-c++-4.8.5-11.el7.x86_64                               | gcc-c++-4.8.5-11.el7.x86_64                                  | gcc-c++-4.4.7-18.el6.x86_64                                  | gcc-c++-4.4.7-18.el6.x86_64                                  |
| patch                                                        | patch-2.7.1-8.el7.x86_64                                    | patch-2.7.1-8.el7.x86_64                                     | patch-2.6-6.el6.x86_64                                       | patch-2.6-6.el6.x86_64                                       | patch-2.7.1-8.el7.x86_64                                  | patch-2.7.1-8.el7.x86_64                                     | patch-2.6-6.el6.x86_64                                       | patch-2.6-6.el6.x86_64                                       |
| lsb_release                                                  |                                                             |                                                              |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |
| zlib                                                         | zlib-1.2.7-17.el7.x86_64 zlib-1.2.7-17.el7.i686             | zlib-1.2.7-17.el7.x86_64 zlib-1.2.7-17.el7.i686              | zlib-1.2.3-29.el6.x86_64 zlib-1.2.3-29.el6.i686              | zlib-1.2.3-29.el6.x86_64 zlib-1.2.3-29.el6.i686              | zlib-1.2.7-17.el7.x86_64 zlib-1.2.7-17.el7.i686           | zlib-1.2.7-17.el7.x86_64 zlib-1.2.7-17.el7.i686              | zlib-1.2.3-29.el6.x86_64 zlib-1.2.3-29.el6.i686              | zlib-1.2.3-29.el6.x86_64 zlib-1.2.3-29.el6.i686              |
|                                                              |                                                             |                                                              |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |
| **Note:** The entries marked green were not installed. Top row kernel version is shipped from distribution |                                                             |                                                              |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |
|                                                              |                                                             |                                                              |                                                              |                                                              |                                                           |                                                              |                                                              |                                                              |

### Ubuntu

| Tool/Library                                                 | Ubuntu 16.04.1 LTS Server          | Ubuntu 16.04.1 LTS Desktop         |
| ------------------------------------------------------------ | ---------------------------------- | ---------------------------------- |
| kernel Version                                               |                                    | 4.4.0-21-generic                   |
| python                                                       | python 3.4.0                       | python 3.4.0                       |
| dos2unix                                                     | tofrodos_1.7.13+ds-2.debian.tar.xz | tofrodos_1.7.13+ds-2.debian.tar.xz |
| ip (iproute)                                                 | iproute2                           | iproute2                           |
| gawk                                                         | gawk                               | gawk                               |
| xvfb                                                         | xvfb                               | xvfb                               |
| gcc(for RHEL,  use devtoolset-2)                             | gcc 4.8                            | gcc 4.8                            |
| git                                                          | git 1.7.1 or above                 | git 1.7.1 or above                 |
| make                                                         | make 3.81                          | make 3.81                          |
| netstat (net-tools)                                          | net-tools                          | net-tools                          |
| ncurses-devel                                                | libncurses5-dev                    | libncurses5-dev                    |
| tftp-server                                                  | tftpd                              | tftpd                              |
| zlib-devel(also,install  32-bit of this version)             | i386/zliob1g-2ubuntu4-dev          | i386/zliob1g-2ubuntu4-dev          |
| openssl-devel                                                | libssl-dev                         | libssl-dev                         |
| flex                                                         | flex                               | flex                               |
| bison                                                        | bison                              | bison                              |
| libselinux                                                   | libselinux1                        | libselinux1                        |
| gnupg                                                        | gnupg                              | gnupg                              |
| wget                                                         | wget                               | wget                               |
| diffstat                                                     | diffstat                           | diffstat                           |
| chrpath                                                      | chrpath                            | chrpath                            |
| socat                                                        | socat                              | socat                              |
| xterm                                                        | xterm                              | xterm                              |
| autoconf                                                     | autoconf                           | autoconf                           |
| libtool                                                      | libtool                            | libtool                            |
| tar                                                          | tar1.24                            | tar1.24                            |
| unzip                                                        | unzip                              | unzip                              |
| texinfo                                                      | texinfo                            | texinfo                            |
| zlib1g-dev                                                   | zlib1g-dev                         | zlib1g-dev                         |
| gcc-multilib                                                 | gcc-multilib                       | gcc-multilib                       |
| build-essential                                              | build-essential                    | build-essential                    |
| libsdl1.2-dev                                                | libsdl1.2-dev                      | libsdl1.2-dev                      |
| libglib2.0-dev                                               | libglib2.0-dev                     | libglib2.0-dev                     |
| SDL-devel                                                    |                                    |                                    |
| glibc-devel                                                  |                                    |                                    |
| 32-bit glibc                                                 |                                    |                                    |
| glib2-devel                                                  |                                    |                                    |
| automake                                                     |                                    |                                    |
| screen                                                       | screen                             | screen                             |
| pax                                                          | pax                                | pax                                |
| gzip                                                         | gzip                               | gzip                               |
| devtoolset-2                                                 |                                    |                                    |
| libz.so.1                                                    |                                    |                                    |
| libstdc++                                                    |                                    |                                    |
| g++ (gcc-c++)                                                |                                    |                                    |
| patch                                                        |                                    |                                    |
| lsb_release                                                  |                                    |                                    |
| zlib                                                         |                                    |                                    |
|                                                              |                                    |                                    |
| **Note:** The entries marked green were not installed. Top row kernel version is shipped from distribution |                                    |                                    |

