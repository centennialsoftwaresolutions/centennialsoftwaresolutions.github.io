# Build an Environment to Debug Device Tree Generation

![xilinx_logo](xilinx_logo.png)

This is a quick post that lists all of the commands to set up an environment to debug device tree generation.

**<u><span>Versions Used</span></u>**

Vivado 2019.1, Ubuntu 16.04.3, git version 2.7.4

**<u><span>Commands</span></u>**

```
mkdir ~/tmp2
cd ~/tmp2 
git clone https://github.com/Xilinx/device-tree-xlnx
# Open a new terminal
mkdir ~/tmp3
cd ~/tmp3
# Vivado is at /tools/Xilinx/Vivado/2019.1/bin/vivado
source /tools/Xilinx/Vivado/2019.1/settings64.sh 
vivado -mode tcl
# You should see:
# xilinxuser@xu:~/tmp3$ vivado -mode tcl
#
# ****** Vivado v2019.1 (64-bit)
#   **** SW Build 2552052 on Fri May 24 14:47:09 MDT 2019
#   **** IP Build 2548770 on Fri May 24 18:01:18 MDT 2019
#     ** Copyright 1986-2019 Xilinx, Inc. All Rights Reserved.
#
# Vivado%
hsi::open_hw_design /home/xilinxuser/tmp/xc7z015_rev2_wrapper.hdf
# You should see:
# INFO: [Hsi 55-1698] elapsed time for repository loading 1 seconds
# xc7z015_rev2_wrapper
hsi::set_repo_path /home/xilinxuser/tmp2/device-tree-xlnx
set processor [hsi::get_cells * -filter {IP_TYPE==PROCESSOR}]
set processor [lindex $processor 0]
hsi::create_sw_design sw1 -proc $processor -os device_tree
hsi::generate_target {dts} -dir dtg_out
ls ~/tmp3/dtg_out/
```

**<u><span>References</span></u>**

-   HTML Escape Tool \[[<u><span>link</span></u>](https://www.freeformatter.com/html-escape.html)\]
    
-   Generating Basic Software Platforms Reference Guide UG1138 (v2019.1) May 22, 2019 \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2019_1/ug1138-generating-basic-software-platforms.pdf)\]
    
-   Debugging Issues in the Device Tree Generation PetaLinux \[[<u><span>link</span></u>](https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/18841693/HSI+debugging+and+optimization+techniques#HSIdebuggingandoptimizationtechniques-DebuggingHSIissuesintheDeviceTreeGeneratorinPetalinux:)\]
    
-   Xilinx logo from [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc)