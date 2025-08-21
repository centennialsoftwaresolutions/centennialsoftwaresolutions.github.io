# Create a ZCU102 PS in Vivado 2019.1

![xilinx_logo_1](xilinx_logo_1.png)

This post shows how to create a ZCU102 PS (Processor Subsystem) in Vivado 2019.1 that allows you to "run code" on the Zynq UltraScale+ MPSoC.

**<u><span>Steps</span></u>**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Install Vivado 2019.1 with the SDK option

Follow the steps at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/post/install-the-2019-1-vivado-hl-design-edition-and-xilinx-sdk)\]

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Start Vivado

On Windows 7: (A) click **Start**, (B) click **All Programs**

![all_programs_2](all_programs_2.png)

(C) click **Xilinx Design Tools**, (D) click **Vivado 2019.1**, and (E) click **Vivado 2019.1**

![vivado_2019.1_3](vivado_2019.1_3.png)

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Click **Create Project**

![create_project_4](create_project_4.png)

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): Click **Next >**

![next_new_project_5](next_new_project_5.png)

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): Set the Project Name and Location

A) Project name: **ps**

B) Project location **C:/vivadoprjs**

C) Leave checked: **Create project subdirectory**

D) Click **Next >**

![set_project_parameters_6](set_project_parameters_6.png)

Step [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6): Specify the Project Type

A) Leave **RTL Project** selected

B) Leave **Do not specify sources at this time** selected

C) Click **Next >**

![set_rtl_project_7](set_rtl_project_7.png)

Step [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7): Specify the board

A) Click **Boards**

B) Type **ZCU102**

C) Click inside the **Zynq UltraScale+ ZCU102 Evaluation Board** box (so it turns blue)

D) Click **Next >**

![select_zcu102_8](select_zcu102_8.png)

Step [#8](https://www.centennialsoftwaresolutions.com/blog/hashtags/8): Click **Finish**

![finish_project_setup__9](finish_project_setup__9.png)

Note: Here is the text of this window:

The default part and product family for the new project:
Default Board: Zynq UltraScale+ ZCU102 Evaluation Board
Default Part: xczu9eg-ffvb1156-2-e
Product: Zynq UltraScale+
Family: Zynq UltraScale+ MPSoCs
Package: ffvb1156 
Speed Grade: -2

_Related docs_: See \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/user_guides/ug1075-zynq-ultrascale-pkg-pinout.pdf#page128)\] for package info, see \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/selection-guides/zynq-ultrascale-plus-product-selection-guide.pdf#page=6)\] for part selection

Step [#9](https://www.centennialsoftwaresolutions.com/blog/hashtags/9): Create a Block Design

A) Click **Create Block Design**

B) Use default Design name: **design\_1**

C) Click **OK**

![create_block_design_1_10](create_block_design_1_10.png)

Step [#10](https://www.centennialsoftwaresolutions.com/blog/hashtags/10): Add the Zynq UltraScale+ MPSoC to the Block Design

A) Click **+**

B) Type **zynq**

C) Double-click **Zynq UltraScale+ MPSoC**

![select_zynq_ultrascale_mpsoc_11](select_zynq_ultrascale_mpsoc_11.png)

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11): Click Run Block Automation

![run_block_automation_1_12](run_block_automation_1_12.png)

Step [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12): 

A) Leave **All Automation** and **zynq\_ultra\_ps\_e\_0** checked

B) Leave **Apply Board Preset** checked

C) Click **OK**

![apply_board_preset_13](apply_board_preset_13.png)

Step [#13](https://www.centennialsoftwaresolutions.com/blog/hashtags/13): 

A) Double click the **Zynq UltraScale+ MPSoC** block

![double_click_zynq_ultrascale_block_14](double_click_zynq_ultrascale_block_14.png)

B) Click **PS-PL Configuration**

C) Expand **PS-PL Interfaces**

D) Expand **Master Interface**

E) Uncheck **AXI HPM0 FPD**

F) Uncheck **AXI HPM1 FPD**

G) Click **OK**

![uncheck_axi_hpm0_and_m1_15](uncheck_axi_hpm0_and_m1_15.png)

Step [#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14): Create an HDL Wrapper

A) Right-click **design\_1 (design\_1.bd)**

B) Click **Create HDL Wrapper...**

![create_hdl_wrapper__16](create_hdl_wrapper__16.png)

C) Leave **Let Vivado manage wrapper and auto-update** selected

D) Click **OK**

![let_vivado_manage_wrapper_17](let_vivado_manage_wrapper_17.png)

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15): Generate Output Products

A) Expand **design\_1\_wrapper (design\_1)wrapper.v) (1)**

B) Right-click **design\_1\_i : design\_1 (design\_1.bd) (1)**

C) Click **Generate Output Products...**

![generate_output_products_18](generate_output_products_18.png)

D) Click **Generate**

![click_generate_19](click_generate_19.png)

You should see:

![managing_output_products_20](managing_output_products_20.png)

E) Observe Generate Output Products status

F) Click OK

![observe_generate_output_products_21](observe_generate_output_products_21.png)

G) Wait until the status says **Ready**

![status_ready_22](status_ready_22.png)

Step [#16](https://www.centennialsoftwaresolutions.com/blog/hashtags/16): Export the hardware to the SDK

A) Click **File**

B) Click **Export**

C) Click **Export Hardware...**

![export_hardware_23](export_hardware_23.png)

D) Leave **Include bitstream** unchecked

E) Click **OK**

![dont_include_bitstream_24](dont_include_bitstream_24.png)

Step [#17](https://www.centennialsoftwaresolutions.com/blog/hashtags/17): Launch the SDK

A) Click **File**

B) Click **Launch SDK**

![launch_sdk_25](launch_sdk_25.png)

C) Click **OK**

![confirm_launch_sdk_26](confirm_launch_sdk_26.png)

You should see:

![importing_hardwear_specification_27](importing_hardwear_specification_27.png)

Followed by:

![sdk_launched_28](sdk_launched_28.png)

**<u><span>References</span></u>**

-   Zynq UltraScale+ MPSoC: Embedded Design Tutorial (UG1209) @ \[[link](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2019_1/ug1209-embedded-design-tutorial.pdf)\]
    
-   Xilinx logo found via \[[link](https://twitter.com/xilinxinc)\]