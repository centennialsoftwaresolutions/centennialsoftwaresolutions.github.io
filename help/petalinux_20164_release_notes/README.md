# 68370 - PetaLinux 2016.4 - Product Update Release Notes and Known Issues



## Title

68370 - PetaLinux 2016.4 - Product Update Release Notes and Known Issues

## Description

This Answer Record acts as the release notes for PetaLinux 2016.4 and contains links to information about resolved issues and updated collateral contained in this release.

## Solution

**PetaLinux 2016.4 contains the following build collateral:**

| Component                  | Tag/Branch     | Comments                                   |
| :------------------------- | :------------- | :----------------------------------------- |
| Device-tree                | xilinx-v2016.4 |                                            |
| Linux                      | xilinx-v2016.4 | Kernel Version 4.6                         |
| U-boot                     | xilinx-v2016.4 | U-boot Version 2016.07                     |
| Xen                        | xilinx-v2016.4 |                                            |
| ARM-Trusted-Firmware (ATF) | xilinx-v2016.4 | ATF is based on upstream version 1.2       |
| GCC                        |                | - MB compiler version 5.2.1<br>- ARM 5.2.1 |
| YOCTO                      |                | Krogoth (2.1)                              |

**BSPs supported for 2016.4 PetaLinux Release**

This table contains supported BSPs for Zynq, MicroBlaze, Zynq UltraScale+ MPSoC.

| Platform               | Variant                             | BSP Name                                       |
| :--------------------- | :---------------------------------- | :--------------------------------------------- |
| Zynq                   | ZC702                               | xilinx-zc702-v2016.4-final.bsp                 |
| Zynq                   | ZC706                               | xilinx-zc706-v2016.4-final.bsp                 |
| Zynq                   | ZEDBOARD                            | avnet-digilent-zedboard-v2016.4-final.bsp      |
| MicroBlaze             | KC705                               | xilinx-kc705-v2016.4-final.bsp                 |
| MicroBlaze             | AC701                               | xilinx-ac701-v2016.4-final.bsp                 |
| MicroBlaze             | KCU105                              | xilinx-kcu105-axi-full-v2016.4-final.bsp       |
| Zynq UltraScale+ MPSoC | ZCU102 ZU9 ES1 silicon              | xilinx-zcu102-v2016.4-final.bsp                |
| Zynq UltraScale+ MPSoC | ZCU102 ZU9 ES2 silicon Rev1.0 board | xilinx-zcu102-zu9-es2-rev1.0-v2016.4-final.bsp |

**Note**: The "[sstate cache file](https://www.xilinx.com/member/forms/download/xef.html?filename=sstate-rel-v2016.4.tar.gz&amp%3bakdm=1)" (sstate-rel-v2016.4.tar.gz) in the Xilinx download area is not a compressed file. Please use the "-xvf" option to extract the sstate-rel-v2016.4.tar.gz file.
This tar file contains a README file that outlines the procedure to use "sstate cache".

**PetaLinux 2016.4 New Features:**

- PetaLinux includes full Yocto build flow at backend. For more details please refer [(UG1144)](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1144-petalinux-tools-reference-guide.pdf), [(UG1156)](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1156-petalinux-tools-workflow-tutorial.pdf) and [(UG1157)](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1157-petalinux-tools-command-line-guide.pdf).
- Added BSPs for ZCU102 Rev1.0 board with ES2 silicon.
- PMU Firmware is built by PetaLinux tools.
- PetaLinux tool users will have the ability to opt out of having PetaLinux tools to build PMU Firmware.
- Added [Linux Power Management](https://www.wiki.xilinx.com/Zynq+UltraScale+MPSoC+Power+Management+-+Linux+Kernel#Linux Kernel Power Management-CPU Idle) support to power off individual CPU cores when they are in idle state.



**PetaLinux**

| Answer Record Number                                         | Answer Record Title                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Xilinx Answer 68449](https://adaptivesupport.amd.com/s/article/68449) | 2016.4 PetaLinux: Migrating U-boot configs from 2016.3 PetaLinux project to 2016.4 PetaLinux Yocto based project |
| [Xilinx Answer 68446](https://adaptivesupport.amd.com/s/article/68446) | 2016.4 PetaLinux: Migrating Kernel configs from 2016.3 PetaLinux project to 2016.4 PetaLinux Yocto based project |
| [Xilinx Answer 68440](https://adaptivesupport.amd.com/s/article/68440) | 2016.4 PetaLinux: Migrating Applications from 2016.3 PetaLinux project to 2016.4 PetaLinux Yocto based project |
| [Xilinx Answer 68441](https://adaptivesupport.amd.com/s/article/68441) | 2016.4 PetaLinux: Migrating modules from 2016.3 PetaLinux project to 2016.4 PetaLinux Yocto based project |

**Yocto**

None

 

**FSBL**

None

 

**U-boot**

None

 

**Linux Drivers**

| Answer Record Number                                         | Answer Record Title                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [Xilinx Answer 68409](https://adaptivesupport.amd.com/s/article/68409) | Zynq UltraScale+ MPSoC: 2016.4 Linux support for GEM 100BT and 10BT |

**Known Issues for 2016.4:**

| Linux/Standalone | Application | Description                                                  | Work-around                                                  | To be fixed version |
| :--------------- | :---------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :------------------ |
| Linux            | PetaLinux   | Zynq UltraScale+ MPSoC: 2016.4 PetaLinux fails with "ERROR: Nothing PROVIDES 'virtual/bootloader'" | [Xilinx Answer 68394](https://adaptivesupport.amd.com/s/article/68394) | 2017.1              |
| Linux            | U-boot      | Zynq UltraScale+ MPSoC: U-boot can't be compiled in PetaLinux if there is no SDIO peripheral in MPSoC design | [Xilinx Answer 68393](https://adaptivesupport.amd.com/s/article/68393) | 2017.1              |
| Linux            | Device-tree | Zynq UltraScale+ MPSoC: 2016.4 PetaLinux - failed to generate memory node in system-conf.dtsi | [Xilinx Answer 68390](https://adaptivesupport.amd.com/s/article/68390) | 2017.1              |
| Linux            | OpenAmp     | Zynq UltraScale+ MPSoC: 2016.4 FreeRTOS_SetupTickInterrupt didn't disable timer irq before it initialize the GIC | [Xilinx Answer 68398](https://adaptivesupport.amd.com/s/article/68398) | 2017.1              |
| Linux            | U-boot      | Zynq UltraScale+ MPSoC: 2016.4 U-Boot support for GEM 100BT and 10BT | [Xilinx Answer 68392](https://adaptivesupport.amd.com/s/article/68392) | 2017.1              |
| Linux            | PetaLinux   | 2016.3 PetaLinux: Missing "/dev/shm" in ZC706 pre-built image | [Xilinx Answer 68412](https://adaptivesupport.amd.com/s/article/68412) | 2017.1              |
| Linux            | PetaLinux   | 2016.4 PetaLinux: Build generates unused device-tree system.dts files | [Xilinx Answer 68422](https://adaptivesupport.amd.com/s/article/68422) | 2017.1              |
| Linux            | PetaLinux   | 2016.4 PetaLinux: TMPDIR is not changing if the PetaLinux project is created without using -n option in MicroBlaze | [Xilinx Answer 68423](https://adaptivesupport.amd.com/s/article/68423) | 2017.1              |
| Linux            | PMUFW       | 2016.4 Zynq UltraScale+ MPSoC: PMUFW build failed without "ENABLE_PM" macro | [Xilinx Answer 68424](https://adaptivesupport.amd.com/s/article/68424) | 2017.1              |
| Linux            | PetaLinux   | 2016.4 PetaLinux: Is PMU firmware is still pointing to pre-built images when we run petalinux-package command | [Xilinx Answer 68372](https://adaptivesupport.amd.com/s/article/68372) | 2017.1              |
| Linux            | PetaLinux   | 2016.4 PetaLinux: sftp-server not starting when dropbear and openssh are both included | [Xilinx Answer 68435](https://adaptivesupport.amd.com/s/article/68435) | 2017.1              |
| Linux            | PetaLinux   | 2016.4 PetaLinux: FIT image generation is failing If user selects initrd in petalinux-config | [Xilinx Answer 68436](https://adaptivesupport.amd.com/s/article/68436) | 2017.1              |
| Linux            | PetaLinux   | 2016.4 PetaLinux: External kernel source with "petalinux-config -c kernel" ends up with errors "merge_config.sh is missing". | [Xilinx Answer 68437](https://adaptivesupport.amd.com/s/article/68437) | 2017.1              |
| Linux            | ATF         | 2016.4 SDK - ATF sources that were included with SDK are not the same used in PetaLinux. | [Xilinx Answer 68474](https://adaptivesupport.amd.com/s/article/68474) | 2017.1              |
| Linux            | PetaLinux   | Zynq UltraScale+ MPSoC: 2016.4 PetaLinux ZCU102 ES2 Rev1.0 Evaluation board unable to boot from SD card | [Xilinx Answer 68522](https://adaptivesupport.amd.com/s/article/68522) | 2017.1              |
| Linux            | PetaLinux   | 2016.3/2016.4 PetaLinux/Yocto: Linux reboot command causing board to hang | [Xilinx Answer 68514](https://adaptivesupport.amd.com/s/article/68514) | 2017.1              |
| Linux            | PetaLinux   | 2016.4 PetaLinux install tool size and BSP size are larger than 2016.3 | None                                                         | None                |