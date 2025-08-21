# Run Hello World on a ZC702

![xilinx_logo_1](xilinx_logo_1.png)

This post shows how run **Hello World** on a Xilinx ZC702. It covers: creating a design in Vivado, exporting the design to the SDK and running Hello World on the dual-core ARM Cortex-A9 processor in the Zynq-7000.

**<u><span>Contains</span></u>**

Part I: Build a PS and Generate a Bitstream

Part II: Export Hardware Design and the Open SDK

Parr III: Set up the ZC702

Part IV: Set up the Terminal

Part V: Run HelloWorld

Part VI: Debug HelloWorld

**<u><span>Note</span></u>**

This write up follows the steps presented in **Zynq-7000 All Programmable SoC: Embedded Design Tutorial** and adds corrections, clarifications and additional information.

**<u><span>Versions</span></u>**

-   Vivado 2018.2 available @ \[[link](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/2018-2.html)\] (install the free WebPACK edition)
    
-   Windows 7 SP1
    

**<u><span>Part I: Build a PS and Generate a Bitstream</span></u>**

<u><span>Step 1</span></u>: Start Vivado 2018.2

A. Click Start

B. Click Vivado 2018.2

![click_vivado_2](click_vivado_2.png)

<u><span>Step 2</span></u>: Click **Create Project**

![create_project_3](create_project_3.png)

<u><span>Step 3</span></u>: Click **Next**

![next_on_new_project_4](next_on_new_project_4.png)

<u><span>Step 4</span></u>:

A. Set **Project name** to **helloworld** (always use a name without spaces \[[moreinfo](https://www.centennialsoftwaresolutions.com/blog/xilinx-sdk-internal-error-the-folder-c-metadata-is-read-only)\])

B. Set **Project location** to **C:/vivadoprjs** (keep paths less than 200 chars)

C. **Check** the **Create project subdirectory** checkbox

D. Click **Next**

![set_project_name_5](set_project_name_5.png)

<u><span>Step 5</span></u>:

A. Select the **RTL Project** radio button if its not selected

B. Check the **Do not specify source at this time** checkbox

C. Click **Next**

![select_rtl_project_6](select_rtl_project_6.png)

<u><span>Step 6</span></u>:

A. Click **Boards**

B. Type **ZC702**

C. Click the **ZYNQ-7 ZC702 Evaluation Board**

D. Click **Next**

![select_zc702_7](select_zc702_7.png)

<u><span>Step 7</span></u>: Click **Finish**

![finish_new_project_8](finish_new_project_8.png)

<u><span>Text Listed, More Info and Links to Docs</span></u>

New Project Summary

A new RTL project named 'helloworld' will be created.

The default part and product family for the new project:

Default Board: ZYNQ-7 ZC702 Evaluation Board

Default Part: xc7z020clg484-1 [[speedgrade and part # decode](https://www.xilinx.com/support/documentation/data_sheets/ds190-Zynq-7000-Overview.pdf) (datasheet p.23)]

Product: Zynq-7000 [[product page](https://www.xilinx.com/products/silicon-devices/soc/zynq-7000.html)]

Family: Zynq-7000

Package: clg484 [[Pinout Files](https://www.xilinx.com/support/package-pinout-files/zynq7000-pkgs.html) & [Packaging and Pinout](https://www.xilinx.com/support/documentation/user_guides/ug865-Zynq-7000-Pkg-Pinout.pdf) p.79]

Speed Grade: -1 

<u><span>Step 8</span></u>: Click **Create Block Design**

![create_block_design_9](create_block_design_9.png)

<u><span>Step 9</span></u>: Use defaults and click **OK**

![use_block_design_defaults_10](use_block_design_defaults_10.png)

<u><span>Step 10</span></u>: Click + to add IP (or Ctrl-I)

![add_ip_11](add_ip_11.png)

<u><span>Step 11</span></u>:

A. Type **Zynq**

B. Double click on **ZYNQ7 Processing System**

![find_zynq_processing_system_12](find_zynq_processing_system_12.png)

You'll see the **Xilinx LogiCORE™ IP Processing System 7 core** \[[doc](https://www.xilinx.com/support/documentation/ip_documentation/processing_system7/v5_5/pg082-processing-system7.pdf)\]:

![zynq_block_13](zynq_block_13.png)

Interfaces:

M\_AXI\_GP0\_ACLK (**input**, global clock, all signals sampled on rising edge of the global clock)

DDR

FIXED\_IO

M\_AXI\_GP0

FCLK\_CLK0 (**output**, fabric aka PL clock, clock for the PL)

FCLK\_RESET0\_N

<u><span>Step 12</span></u>: Click **Run Block Automation**

![run_block_automation_14](run_block_automation_14.png)

<u><span>Step 13</span></u>: Use defaults and click **OK**

![use_block_automation_defaults_15](use_block_automation_defaults_15.png)

You'll see:

![block_automation_result_16](block_automation_result_16.png)

<u><span>Step 14</span></u>: Connect the PL clock (FCLK\_CLK0) to the global clock (M\_AXI\_GP0\_ACLK)

A. Click and hold on FCLK\_CLK0

B. Drag the connection to M\_AXI\_GP0\_ACLK and release mouse button

![connect_pl_to_global_clock_17](connect_pl_to_global_clock_17.png)

You should see:

![connection_successful_18](connection_successful_18.png)

<u><span>Step 15</span></u>: Create an HDL Wrapper

A. Click **Sources**

B. Click **Hierarchy**

C. Right-click **design\_1 (design\_1.bd)**

D. Click **Create HDL Wrapper...**

![create_hdl_wrapper_19](create_hdl_wrapper_19.png)

<u><span>Step 16</span></u>:

A. Leave or select **Let Vivado manage wrapper and auto-update**

B. Click **OK**

![let_vivado_manage_wrapper_20](let_vivado_manage_wrapper_20.png)

Step 17:

A. Click to expand **design\_1\_wrapper (design\_1\_wrapper.v)(1)**

B. Right-click on **design\_1\_i: design\_1 (design\_1.bd)(1)**

C. Click **Generate Output Products...**

![generate_output_products_21](generate_output_products_21.png)

<u><span>Step 18</span></u>:

A. Leave selected or select **Out of context per IP**

B. Leave **Number of jobs** at 2

C. Click **Generate**

![set_output_products_22](set_output_products_22.png)

<u><span>Step 19</span></u>: Click **OK** and let the operation complete

![confirm_generate_output_products_23](confirm_generate_output_products_23.png)

<u><span>Step 20</span></u>: Click **Run Synthesis**

![run_synthesis_24](run_synthesis_24.png)

<u><span>Step 21</span></u>: Use the defaults and click **OK**

![use_runs_defaults_25](use_runs_defaults_25.png)

Wait for **synth\_design** to complete

![running_synth_design_26](running_synth_design_26.png)

<u><span>Step 22</span></u>:

A. Leave selected or select **Run Implementation**

B. Click **OK**

![synthesis_completed_27](synthesis_completed_27.png)

<u><span>Step 23</span></u>: Use the defaults and click **OK**

![use_run_defaults_28_use_again](use_run_defaults_28_use_again.png)

Wait for the operation to complete:

![initializing_design_29](initializing_design_29.png)

![running_opt_design_30](running_opt_design_30.png)

![running_route_design_31](running_route_design_31.png)

Complete:

![implementation_complete_32](implementation_complete_32.png)

<u><span>Step 23</span></u>:

A. Select **Generate Bitstream**

B. Click **OK**

![implementation_completed_33](implementation_completed_33.png)

<u><span>Step 24</span></u>: Use the defaults and click **OK**

![use_run_defaults_28_use_again](use_run_defaults_28_use_again.png)

Wait for the operation to complete:

![running_write_bitstream_34](running_write_bitstream_34.png)

Complete:

![write_bitstream_complete_35](write_bitstream_complete_35.png)

Step 25: Click **Cancel**

![bitstream_generation_completed_36](bitstream_generation_completed_36.png)

**<u><span>Part II: Export Hardware Design and the Open SDK</span></u>**

<u><span>Step 1</span></u>:

A. Click **File**

B. Click **Export**

C. Click **Export Hardware**

![export_hardwear_37](export_hardwear_37.png)

<u><span>Step 2</span></u>:

A. Click the **Include bitstream** checkbox

B. Leave **<Local to Project>**

C. Click **OK**

![export_options_38](export_options_38.png)

<u><span>Step 3</span></u>:

A. Click **File**

B. Click **Launch SDK**

![launch_sdk_39](launch_sdk_39.png)

<u><span>Step 4</span></u>: Use defaults and click **OK**

![use_sdk_defaults_40](use_sdk_defaults_40.png)

<u><span>Step 5</span></u>:

A. Click **File**

B. Click **Application Project**

![seelct_application_project_41](seelct_application_project_41.png)

<u><span>Step 6</span></u>:

A. Type **HelloWorld** for **Project name**

B. See **HelloWorld\_bsp** autopopulate

C. Click **Next**

![select_project_name_42](select_project_name_42.png)

<u><span>Step 7</span></u>:

A. Ensure **Hello World** is selected (it should be)

B. Click **Finish**

![select_hello_world_43](select_hello_world_43.png)

You should see:

![project_files_44](project_files_44.png)

**<u><span>Part III: Set up the ZC702</span></u>**

Step 1: Set SW16 to JTAG mode [[mode documentation](https://www.xilinx.com/support/documentation/boards_and_kits/zc702_zvik/ug850-zc702-eval-bd.pdf) see p.16]

![set_sw16_to_jtag_45](set_sw16_to_jtag_45.png)

For the rest of the jumpers see the high-resolution photo of the board in the correct state at \[[link](https://photos.app.goo.gl/DddmM8T5QkTXwA7u5)\].

<u><span>Step 2</span></u>: Connect a **Micro-B to Type-A** (host connection) USB cable from U23 (Diglent USB JTAG interface) to the host PC

U23:

![u23_46](u23_46.png)

Micro-B connector:

![micro_b_connector_47](micro_b_connector_47.png)

Type-A connector:

![type_a_connector_48](type_a_connector_48.png)

<u><span>Step 3</span></u>: Connect a **Mini-B to Type-A** (host connection) USB cable from J17 (CP2103GM USB-to\_UART Bridge) to the host PC.

J17:

![j17_49](j17_49.png)

Mini-B connector:

![mini_b_connector_50](mini_b_connector_50.png)

Type-A connector:

![type_a_connector_51](type_a_connector_51.png)

<u><span>Step 4</span></u>: Power on the board (you'll need to power on the board to see the USB-to-UART device in the next step).

![turn_board_on_52](turn_board_on_52.png)

**<u><span>Part IV: Set up the Terminal</span></u>**

Step 1: Install the Silicon Labs CP210x USB to UART Bridge VCP Drivers

A. Goto [[link](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)]

B. Download and unzip the correct installer

C. Install the driver (I did not need to restart on Windows 7 SP1)

D. Click Windows

E. Click Devices and Printers

![devices_and_printers_53](devices_and_printers_53.png)

F. You should see Silicon Labs CP210x USB to UART Bridge

G. Note the COM port (you'll need this later)

![note_com_port_54](note_com_port_54.png)

<u><span>Step 2</span></u>:

A. Click **Window**

B. Click **Show View**

C. Click **Other**

![click_show_view_55](click_show_view_55.png)

<u><span>Step 3</span></u>:

A. Expand **Terminal**

B. Click **Terminal**

C. Click **OK**

![click_terminal_56](click_terminal_56.png)

Step 4: Click **Settings**

![click_settings_57](click_settings_57.png)

<u><span>Step 5</span></u>:

A. Use the COM port listed in Devices and Printers (or type it in: COM9 for instance)

B. Click OK

![enter_com_port_58](enter_com_port_58.png)

**<u><span>Part V: Run HelloWorld</span></u>**

<u><span>Step 1</span></u>: Run Debug once

A. Right click **HelloWorld**

B. Click **Debug As**

C. Click **Launch on Hardware (System Debugger)**

![launch_on_hardware_59](launch_on_hardware_59.png)

D. Click **Yes**

![fpga_configuration_60](fpga_configuration_60.png)

E. Click **Yes**

![confirm_perspective_switch_61](confirm_perspective_switch_61.png)

<u><span>Step 2</span></u>:

A. Click **Run**

B. Click **Run Configurations...**

![run_configurations_62](run_configurations_62.png)

<u><span>Step 3</span></u>:

A. Make sure **System Debugger using Debug\_HelloWorld.elf on Local** is selected

B. Check the **Reset entire system** check box

C. Check the **Program FPGA** check box

D. Ensure the **Run ps7\_init** check box is checked

E. Ensure the **Run ps7\_post\_config** is checked

F. Click **Apply**

G. Click **Run**

![config_system_debugger_63](config_system_debugger_63.png)

H. Switch back to the C/C++ View

![switch_back_to_c_c++_view_64](switch_back_to_c_c++_view_64.png)

You should see:

![hello_world_65](hello_world_65.png)

<u><span>Step 4</span></u>: Run the program again

A. Click **Run**

B. Click **Run** (this will use the Run Config you set up previously)

![run_again_66](run_again_66.png)

C. Click **OK**

![confirm_debug_relaunch_67](confirm_debug_relaunch_67.png)

You should see another **Hello World**:

![hello_world_again_68](hello_world_again_68.png)

**<u><span>Part VI: Debug HelloWorld</span></u>**

<u><span>Step 1</span></u>: Click to disconnect Run terminal

![click_disconnect_69](click_disconnect_69.png)

<u><span>Step 2</span></u>:

A. Click **Run**

B. Click **Debug Configurations...**

![debug_configurations_70](debug_configurations_70.png)

<u><span>Step 3</span></u>:

A. Make sure **System Debugger using Debug\_HelloWorld.elf on Local** is selected

B. Make sure the **Reset entire system** check box is checked

C. Make sure the**Program FPGA** check box is checked

D. Ensure the **Run ps7\_init** check box is checked

E. Ensure the **Run ps7\_post\_config** is checked

F. Click **Apply** if anything changed (the Apply button will be grayed out if no changes were needed).

G. Click **Debug**

![configure_debug_options_71](configure_debug_options_71.png)

H. Click **Yes**

![confirm_perspective_switch_72](confirm_perspective_switch_72.png)

You should see:

![debug_screen_73](debug_screen_73.png)

<u><span>Step 4</span></u>: Connect the serial port

A. Click **SDK Terminal**

B. Click the **'+'** (Connect to serial port.)

![connect_to_serial_port_74](connect_to_serial_port_74.png)

C. Use these settings and click **OK**

![use_serial_port_75](use_serial_port_75.png)

You should see:

![connected_to_com9_76](connected_to_com9_76.png)

<u><span>Step 5</span></u>: Click **Resume (F8)**

![resume_program_77](resume_program_77.png)

You should see:

![hello_world_78](hello_world_78.png)

<u><span>Step 6</span></u>: Restart Debug

A. Click **Run**

B. Click **Debug** (this will use the Debug Config you set up previously)

![click_debug_79](click_debug_79.png)

C. Click **OK**

![debug_session_relaunch_80](debug_session_relaunch_80.png)

You should again see:

![debug_screen_81](debug_screen_81.png)

Note: to disconnect the debuggers serial port click here:

![disconnect_debuggers_serial_port_82](disconnect_debuggers_serial_port_82.png)

You should see:

![com9_disconnected_83](com9_disconnected_83.png)

**<u><span>References</span></u>**

-   2018.2 Zynq-7000 All Programmable SoC: Embedded Design Tutorial (UG1165) @ \[[link](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug1165-zynq-embedded-design-tutorial.pdf)\] (p.15 to 30)
    
-   Xilinx logo found via [https://twitter.com/xilinxinc](https://twitter.com/xilinxinc) at \[[link](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]