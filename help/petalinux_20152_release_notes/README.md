# 55776 - Release Notes and Known Issues for PetaLinux 2013.04 and later tool versions



## Title



55776 - Release Notes and Known Issues for PetaLinux 2013.04 and later tool versions

## Description



This answer record contains the Release Notes and Known Issues for PetaLinux and includes the following:

- General Information
- Known and Resolved Issues
- Revision History

PetaLinux Product Page:

https://www.xilinx.com/products/design-tools/embedded-software/petalinux-sdk.html

## Solution



**General Information**

Supported Operating Host Systems can be found in the following three locations:

- PetaLinux Tools User Guide Installation Guide ([UG976](https://www.xilinx.com/support/documentation/sw_manuals/petalinux2014_2/ug976-petalinux-installation.pdf)) (PetaLinux 2013.04 to 2014.2)
- PetaLinux Tools Documentation Reference Guide ([UG1144](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1144-petalinux-tools-reference-guide.pdf)) (PetaLinux 2014.4 and later)
- PetaLinux Tools Documentation Workflow Tutorials([UG1156](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1156-petalinux-tools-workflow-tutorial.pdf)) (PetaLinux 2014.4 to 2017.4)
- PetaLinux Tools Documentation PetaLinux Command Line Reference ([UG1157](https://www.xilinx.com/cgi-bin/docs/rdoc?v=latest%3bd=ug1157-petalinux-tools-command-line-guide.pdf)) (PetaLinux 2014.4 to 2020.1)

For a complete archive of PetaLinux documentation, please see [(Xilinx Answer 62896)](https://adaptivesupport.amd.com/s/article/62896)

**Version Table**

This table correlates the PetaLinux version to the corresponding ISE/Vivado tools release version with which it was tested.

| PetaLinux Version | ISE / Vivado Tools Version                                   |
| ----------------- | ------------------------------------------------------------ |
| 2012.12           | 14.4 / 2012.4                                                |
| 2013.04           | 14.5 / 2013.1                                                |
| 2013.10           | 14.7 / 2013.3 / 2014.1 For patch see [(Xilinx Answer 59809)](https://adaptivesupport.amd.com/s/article/59809) |
| 2014.2            | 2014.2                                                       |
| 2014.4            | 2014.3 / 2014.4                                              |
| 2015.2            | 2015.1 / 2015.2                                              |
| 2015.2.1          | 2015.1 / 2015.2 / 2015.2.1                                   |
| 2015.4            | 2015.4                                                       |
| 2016.1            | 2016.1                                                       |
| 2016.2            | 2016.2                                                       |
| 2016.3            | 2016.3                                                       |
| 2016.4            | 2016.4                                                       |
| 2017.1            | 2017.1                                                       |
| 2017.2            | 2017.2                                                       |
| 2017.3            | 2017.3                                                       |
| 2017.4            | 2017.4                                                       |
| 2018.1            | 2018.1                                                       |
| 2018.2            | 2018.2                                                       |
| 2018.3            | 2018.3                                                       |
| 2019.1            | 2019.1                                                       |
| 2019.2            | 2019.2                                                       |
| 2020.1            | 2020.1                                                       |
| 2020.2            | 2020.2                                                       |
| 2021.1            | 2021.1                                                       |

**General Guidance**

The table below provides Answer Records for general guidance when using PetaLinux.

| Answer Record                                                | Title                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [(Xilinx Answer 54756)](https://adaptivesupport.amd.com/s/article/54756) | Can I Read the PetaLinux EULA Prior to Installation?         |
| [(Xilinx Answer 53871)](https://adaptivesupport.amd.com/s/article/53871) | Why is my PetaLinux Tool Consuming Two License Seats Instead of Just One? |
| [(Xilinx Answer 53752)](https://adaptivesupport.amd.com/s/article/53752) | Are Pre-Built Demos Available for PetaLinux?                 |
| [(Xilinx Answer 55778)](https://adaptivesupport.amd.com/s/article/55778) | Licensing - Why Does My FLEXnet License Not Work Properly When SELinux Is Enabled? |

**Known and Resolved Issues**:

The following table provides known issues for PetaLinux, starting with the 2013.04 version.

**Note:** The "Version Found" column lists the version the issue was first discovered.

The problem might also exist in earlier versions, but no specific testing has been performed to verify earlier versions.

| Answer Record                                                | Title                                                        | Version Found |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------- |
| [(Xilinx Answer 55781)](https://adaptivesupport.amd.com/s/article/55781) | When Debugging My System with QEMU, the Ethernet Device Fails | 2013.04       |
| [(Xilinx Answer 55782)](https://adaptivesupport.amd.com/s/article/55782) | When Debugging with QEMU, Network Accesses Cause QEMU To Hang | 2013.04       |
| [(Xilinx Answer 58611)](https://adaptivesupport.amd.com/s/article/58611) | Kernel Hangs During Boot on ES Zynq Board                    | 2013.10       |
| [(Xilinx Answer 58612)](https://adaptivesupport.amd.com/s/article/58612) | Boot Fails When Attempting to Use FIT Image with QEMU        | 2013.10       |
| [(Xilinx Answer 58613)](https://adaptivesupport.amd.com/s/article/58613) | UBOOT Hangs When Victim DCACHE Is Enabled in KC705 BSP       | 2013.10       |
| [(Xilinx Answer 60970)](https://adaptivesupport.amd.com/s/article/60970) | Device Tree Generator Does Not Generate Device Nodes for All IP | 2014.2        |
| [(Xilinx Answer 60971)](https://adaptivesupport.amd.com/s/article/60971) | Duplicate Device Tree Nodes Generated When M_AXI_DC and M_AXI_DP Are on Same AXI Interconnect | 2014.2        |
| [(Xilinx Answer 60972)](https://adaptivesupport.amd.com/s/article/60972) | MicroBlaze D-Cache in Writeback Mode Causes No Output in FS-BOOT Application | 2014.2        |
| [(Xilinx Answer 60973)](https://adaptivesupport.amd.com/s/article/60973) | petalinux-config Does Not Read Vivado-Exported XML If HDF File Already Exists | 2014.2        |
| [(Xilinx Answer 60974)](https://adaptivesupport.amd.com/s/article/60974) | FSBL Component Does Not Update PS7_INIT.C and PS7_INIT.H When Importing New Hardware Definition | 2014.2        |
| [(Xilinx Answer 63191)](https://adaptivesupport.amd.com/s/article/63191) | U-Boot Compilation Fails When Using The Latest Mainline U-Boot Source | 2014.4        |
| [(Xilinx Answer 63192)](https://adaptivesupport.amd.com/s/article/63192) | AC701 Designs Do Not Properly Update Board Firmware with the upgrade-firmware Application | 2014.4        |
| [(Xilinx Answer 63193)](https://adaptivesupport.amd.com/s/article/63193) | QEMU Cannot Boot the Kernel from U-Boot                      | 2014.4        |
| [(Xilinx Answer 64976)](https://adaptivesupport.amd.com/s/article/64976) | Only CPU0 Comes Up When Booting Linux on Zynq-7000 Devices   | 2015.2        |
| [(Xilinx Answer 65276)](https://adaptivesupport.amd.com/s/article/65276) | PetaLinux 2015.2.1 - Product Update Release Notes and Known Issues | 2015.2        |
| [(Xilinx Answer 66107)](https://adaptivesupport.amd.com/s/article/66107) | PetaLinux 2015.4 - Product Update Release Notes and Known Issues | 2015.4        |
| [(Xilinx Answer 67156)](https://adaptivesupport.amd.com/s/article/67156) | PetaLinux 2016.1 - Product Update Release Notes and Known Issues | 2016.1        |
| [(Xilinx Answer 67409)](https://adaptivesupport.amd.com/s/article/67409) | PetaLinux 2016.2 - Product Update Release Notes and Known Issues | 2016.2        |
| [(Xilinx Answer 68057)](https://adaptivesupport.amd.com/s/article/68057) | PetaLinux 2016.3 - Product Update Release Notes and Known Issues | 2016.3        |
| [(Xilinx Answer 68370)](https://adaptivesupport.amd.com/s/article/68370) | PetaLinux 2016.4 - Product Update Release Notes and Known Issues | 2016.4        |
| [(Xilinx Answer 69074)](https://adaptivesupport.amd.com/s/article/69074) | PetaLinux 2017.1 - Product Update Release Notes and Known Issues | 2017.1        |
| [(Xilinx Answer 69372)](https://adaptivesupport.amd.com/s/article/69372) | PetaLinux 2017.2 - Product Update Release Notes and Known Issues | 2017.2        |
| [(Xilinx Answer 69952)](https://adaptivesupport.amd.com/s/article/69952) | PetaLinux 2017.3 - Product Update Release Notes and Known Issues | 2017.3        |
| [(Xilinx Answer 70277)](https://adaptivesupport.amd.com/s/article/70277) | PetaLinux 2017.4 - Product Update Release Notes and Known Issues | 2017.4        |
| [(Xilinx Answer 70896)](https://adaptivesupport.amd.com/s/article/70896) | PetaLinux 2018.1 - Product Update Release Notes and Known Issues | 2018.1        |
| [(Xilinx Answer 71201)](https://adaptivesupport.amd.com/s/article/71201) | PetaLinux 2018.2 - Product Update Release Notes and Known Issues | 2018.2        |
| [(Xilinx Answer 71653)](https://adaptivesupport.amd.com/s/article/71653) | PetaLinux 2018.3 - Product Update Release Notes and Known Issues | 2018.3        |
| [(Xilinx Answer 72293)](https://adaptivesupport.amd.com/s/article/72293) | PetaLinux 2019.1 - Product Update Release Notes and Known Issues | 2019.1        |
| [(Xilinx Answer 72950)](https://adaptivesupport.amd.com/s/article/72950) | PetaLinux 2019.2 - Product Update Release Notes and Known Issues | 2019.2        |
| [(Xilinx Answer 73686)](https://adaptivesupport.amd.com/s/article/73686) | PetaLinux 2020.1 - Product Update Release Notes and Known Issues | 2020.1        |
| [(Xilinx Answer 75775)](https://adaptivesupport.amd.com/s/article/75775) | PetaLinux 2020.2/3 - Product Update Release Notes and Known Issues | 2020.2/3      |
| [(Xilinx Answer 76526)](https://adaptivesupport.amd.com/s/article/76526) | PetaLinux 2021.1 - Product Update Release Notes and Known Issues | 2021.1        |

**Revision History**

| Date       | Description                                   |
| ---------- | --------------------------------------------- |
| 04/30/2013 | Initial release                               |
| 12/02/2013 | Updated for PetaLinux 2013.10                 |
| 01/28/2014 | Updated PetaLinux naming taxonomy             |
| 06/04/2014 | Updated for PetaLinux 2014.2 release          |
| 12/19/2014 | Updated for PetaLinux 2014.4 release          |
| 07/14/2015 | Updated for PetaLinux 2015.2 release          |
| 08/31/2015 | Updated for PetaLinux 2015.2.1 update release |
| 12/14/2015 | Updated for PetaLinux 2015.4 release          |
| 12/21/2016 | Updated for PetaLinux 2016.4 release          |
| 05/03/2017 | Updated for PetaLinux 2017.1 release          |
| 06/29/2017 | Updated for PetaLinux 2017.2 release          |
| 10/18/2017 | Updated for PetaLinux 2017.3 release          |
| 12/22/2017 | Updated for PetaLinux 2017.4 release          |
| 04/23/2018 | Updated for PetaLinux 2018.1 release          |
| 06/18/2018 | Updated for PetaLinux 2018.2 release          |
| 12/10/2018 | Updated for PetaLinux 2018.3 release          |
| 05/29/2019 | Updated for PetaLinux 2019.1 release          |
| 10/31/2019 | Updated for PetaLinux 2019.2 release          |
| 06/03/2020 | Updated for PetaLinux 2020.1 release          |
| 11/24/2020 | Updated for PetaLinux 2020.2/3 release        |
| 06/16/2021 | Updated for PetaLinux 2021.1 release          |