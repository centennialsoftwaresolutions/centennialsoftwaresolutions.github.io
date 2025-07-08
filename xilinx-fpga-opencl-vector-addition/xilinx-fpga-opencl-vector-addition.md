# Xilinx FPGA OpenCL Vector Addition WIP

![sdsoc_environment_1](sdsoc_environment_1.jpg)

Warning

This post is a work in progress.

Everything works until you see:

## **<u><span>!!!Problem!!!</span></u>**

Using SDx 2018.2.

**<u><span>Supported Boards</span></u>**

This example states that it runs on **Zynq UltraScale+ MPSoC** on the **ZCU102** board (available for $2,495.00 \[[<u><span>here</span></u>](https://www.xilinx.com/products/boards-and-kits/ek-u1-zcu102-g.html)\]) and the **Zynq UltraScale+ MPSoC EV** of the **ZCU104** (available for $895.00 \[[<u><span>here</span></u>](https://www.xilinx.com/products/boards-and-kits/zcu104.html)\]) and **ZCU106** (available for $1,995.00 \[[<u><span>here</span></u>](https://www.xilinx.com/products/boards-and-kits/zcu106.html)\]).

**<u><span>Prerequisites</span></u>**

-   You have a ZCU102
    
-   You have install SDSoC 2018.2 - see \[[<u><span>instructions</span></u>](https://www.centennialsoftwaresolutions.com/blog/lab-1-sdsoc-build-and-load)\] if you need help installing SDSoC 2018.2
    

**<u><span>Steps</span></u>**

1\. Make sure you have **git**

Type **sudo apt-get install git**

2\. (A) Click the **New Project** drop down then (B) click **SDx Project...**

![sdx_project_2](sdx_project_2.png)

3\. Leave the **Application** radio button selected and click **Next >**

![leave_application_radio_button_3](leave_application_radio_button_3.png)

4\. (A) Name the project **vectoradd** and (B) click **Next >**

![name_project_vectoradd_4](name_project_vectoradd_4.png)

5\. (A) Select the **ZCU102** and (B) click **Next >**

![select_zcu102_5](select_zcu102_5.png)

6\. Accept the defaults on the **System configuration** page and click **Next >**

![default_system_configuration_6](default_system_configuration_6.png)

7\. Click **SDx Examples...**

![sdx_examples_7](sdx_examples_7.png)

_Warning!!! Before you do the next step, you must have git installed. If you do not, close SDx, install it (see above for the command, relaunch SDx and follow the instructions to here)_

8\. Click the **Download** button

![download_8](download_8.png)

You should see:

![downloading_sdsoc_examples_9](downloading_sdsoc_examples_9.png)

...and:

![sdsoc_examples_downloaded_10](sdsoc_examples_downloaded_10.png)

9\. (A) Scroll down, (B) select **Vector Addition (CL)** and (C) click **OK**

![vector_addition_11](vector_addition_11.png)

10\. Click **Finish**

![finish_12](finish_12.png)

## **<u><span>!!!Problem!!!</span></u>**

Step 11 does not work, project will not build

11\. (A) Click **vectoradd** the (B) click the **hammer icon** to build

![vectoradd_13](vectoradd_13.png)

Problem:

Out of the box you'll get:

make: \*\*\* No rule to make target 'clean'. Stop. vectoradd C/C++ Problem

**<u><span>Workaround 1 (didn't work)</span></u>**

To work around this (A) right click on **vectoradd** and (B) click **C/C++ Build Settings**

![c_cplusplus_build_settings_14](c_cplusplus_build_settings_14.png)

(A) Click Settings then (B) remove **sdsoc\_make\_clean Debug**

![remove_sdsoc_clean_debug_15](remove_sdsoc_clean_debug_15.png)

...then click **OK**

![ok_16](ok_16.png)

**<u><span>Workaround 2 (didn't work)</span></u>**

(A) Click **C/C++ Build** then (B) click the **Clean** checkbox off

![uncheck_clean_checkbox_17](uncheck_clean_checkbox_17.png)

After clicking it off, click OK:

![click_ok_18](click_ok_18.png)

**<u><span>References</span></u>**

-   An example from Xilinx of performing vector addition using OpenCL at \[[<u><span>link</span></u>](https://github.com/Xilinx/SDSoC_Examples/tree/master/ocl/getting_started/hello_vadd_ocl)\]
    
-   SDSoC logo from \[[<u><span>link</span></u>](https://www.origin.xilinx.com/content/xilinx/en/products/boards-and-kits/ek-u1-zcu102-g/_jcr_content/mainParsys/xilinxtabs2/tab-hardware/xilinxcolumns_325b/column2/xilinxincludedproduc.img.jpg/1528405722461.jpg)\]
    

**<u><span>Notes</span></u>**

**Difference between the Zynq UltraScale+ MPSoC (CG and EG) and the Zynq UltraScale+ MPSoC EV**

The ZCU102 has a Zynq UltraScale+ MPSoC **EG**, the ZCU104 and ZCU106 have **Zynq UltraScale+ MPSoC EV**'s.

From \[[<u><span>link</span></u>](https://www.xilinx.com/products/silicon-devices/soc/zynq-ultrascale-mpsoc.html#productAdvantages)\] the EV is the EG + "an integrated H.264 / H.265 video codec capable of simultaneous encode and decode up to 4Kx2K (60fps)"