# Zynq-7000 + AXI Slave Hello World

![xilinx_logo_1](xilinx_logo_1.png)

This post shows how to create a Xilinx Zynq-7000 + AXI slave in Vivado 2018.2 and read/write the AXI slave from the ARM9 of the Zynq-7000 using bare-metal code built with the SDK on the ZC702.

**<u><span>Versions Used</span></u>**

Xilinx Vivado 2018.2 & SDK 2018.2

ZC702 Rev 1.1

Windows 7 SP1

**<u><span>Before you Start</span></u>**

Review ZC702 JTAG and serial port set up instructions @ \[[link](https://www.centennialsoftwaresolutions.com/blog/set-up-the-jtag-and-serial-port-on-the-zc702)\]. These instructions are also reviewed below.

**<u><span>Contents</span></u>**

Part 1: Create the Vivado Project

Part 2: Create the AXI Slave IP and Add it to the Repo

Part 3: Create the Zynq-7000 in IP Integrator

Part 4: Connect the AXI Slave

Part 5: Build the Bitstream (to Program the FPGA)

Part 6: Export the Design and Open the SDK

Part 7: Install the USB-to-UART Driver and Get the COM Assignment

Part 8: Configure the Board to Boot from JTAG, Connect it to the PC and Power it On

Part 9: Create the Test App and BSP

Part 10: Test Debug Run + Further Config

Part 11: Test the AXI module

**<u><span>Part 1: Create the Vivado Project</span></u>**

Step 1: Start Vivado

![start_vivado_2](start_vivado_2.png)

Step 2: Click **Create Project**

![create_project_3](create_project_3.png)

Step 3: Click Next

![next_on_create_new_project_4](next_on_create_new_project_4.png)

Step 4:

A. Set **Project name** to axislave

B: Set **Project location** to C:/vivadoprjs (create C:/vivadoprjs if it doesn't exist)

C. Click the **Create project subdirectory** checkbox

D. Click **Next**

![set_project_name_5](set_project_name_5.png)

Step 5:

A. Select **RTL Project**

B. Check the **Do not specify sources at this time** check box

C. Click **Next**

![select_rtl_project_6](select_rtl_project_6.png)

Step 6:

A. Click **Boards**

B. Type **ZC702**

C. Click on the **ZYNQ-7 ZC702 Evaluation Board** box

D. Click **Next**

![select_zc702_board_7](select_zc702_board_7.png)

Step 7: Click **Finish**

![finish_new_project_8](finish_new_project_8.png)

**<u><span>Part 2: Create the AXI Slave IP and Add it to the Repo</span></u>**

Step 1:

A. Click **Tools**

B. Click **Create and Package New IP...**

![create_and_package_new_ip_9](create_and_package_new_ip_9.png)

Step 2: Click **Next**

![next_on_new_ip_10](next_on_new_ip_10.png)

Step 3:

A. Select **Create a new AXI4 peripheral**

B. Click **Next**

![create_new_axi4_peripheral_11](create_new_axi4_peripheral_11.png)

Step 4:

A. Use defaults except, set IP location to: C:/vivadoprjs/axislave/ip\_repo

B. Click Next

![set_ip_location_12](set_ip_location_12.png)

Step 5: Use defaults, click **Next**

![use_defaults_for_axi4_13](use_defaults_for_axi4_13.png)

Step 6: Use defaults, click **Finish**

![use_defaults_14](use_defaults_14.png)

**<u><span>Part 3: Create the Zynq-7000 in IP Integrator</span></u>**

Step 1: Click **Create Block Design**

![create_block_design_15](create_block_design_15.png)

Step 2: Use defaults, click **OK**

![use_block_design_defaults_16](use_block_design_defaults_16.png)

Step 3: Click **+**

![click_plus_17_use_again](click_plus_17_use_again.png)

Step 4:

A. Type **Zynq**

B. Double-click on **ZYNQ7 Processing System**

![find_zynq7_processing_system_18](find_zynq7_processing_system_18.png)

Step 5: Click **Run Block Automation**

![run_block_automation_19](run_block_automation_19.png)

Step 6: Use defaults, click **OK**

![use_block_automation_defaults_20](use_block_automation_defaults_20.png)

You should see:

![zynq7_processing_system_block_21](zynq7_processing_system_block_21.png)

**<u><span>Part 4: Connect the AXI Slave</span></u>**

Step 1: Click **+**

![click_plus_17_use_again](click_plus_17_use_again.png)

Step 2:

A. Type **myIP**

B. Double-click **myip\_v1.0**

![find_myip_22](find_myip_22.png)

Step 3: Click **Run Connection Automation**

![run_connection_automation_23](run_connection_automation_23.png)

Step 4: Use defaults, click **OK**

![use_connection_automation_defaults_24](use_connection_automation_defaults_24.png)

You should see:

![diagram_25](diagram_25.png)

Step 5: Click **Sources**

![click_sources_26](click_sources_26.png)

Step 6:

A. Right-click **design\_1 (design\_1.bd)**

B. Click **Create HDL Wrapper...**

![create_hdl_wrapper_27](create_hdl_wrapper_27.png)

Step 7: Use default, click **OK**

![use_hdl_wrapper_defaults_28](use_hdl_wrapper_defaults_28.png)

You should see:

![design_1_wrapper_29](design_1_wrapper_29.png)

Step 8:

A. Click to expand **design\_1\_wrapper (design\_1\_wrapper.v)(1)**

B. Right-click on **design\_1\_i: design\_1 (design\_1.bd)(1)**

C. Click **Generate Output Products...**

![generate_output_products_30](generate_output_products_30.png)

<u><span>Step 7</span></u>:

A. Leave selected or select **Out of context per IP**

B. Leave **Number of jobs** at 2

C. Click **Generate**

![set_generate_output_products_paremeters_31](set_generate_output_products_paremeters_31.png)

<u><span>Step 8</span></u>: Click **OK** and let the operation complete

![let_operation_complete_32](let_operation_complete_32.png)

**<u><span>Part 5: Build the Bitstream (to Program the FPGA)</span></u>**

Step 1: Click **Run Synthesis**

![run_synthesis_33](run_synthesis_33.png)

Step 2: Use defaults, click **OK**

![use_run_defaults_34](use_run_defaults_34.png)

You'll see the status in the upper right corner:

![running_multiple_block_runs_35](running_multiple_block_runs_35.png)

Step 3:

Wait approximately 1 to 5 min until you see **Synthesis Complete** in the upper right corner...

![synthesis_complete_36](synthesis_complete_36.png)

...and click **OK** to Run Implementation:

![ok_to_run_implementation_37](ok_to_run_implementation_37.png)

Step 4: Use defaults, click **OK**

![use_run_defaults_38](use_run_defaults_38.png)

Again, you'll see status in the upper right:

![initializing_design_39](initializing_design_39.png)

Step 5:

Wait approximately 1 to 5 min until you see **Implementation Complete** in the upper right corner...

![implementation_complete_40](implementation_complete_40.png)

A. Select **Generate Bitstream**

B. Click **OK**

![select_generate_bitstream_41](select_generate_bitstream_41.png)

Step 6: Use defaults, click **OK**

![use_defaults_42](use_defaults_42.png)

Again, you should see the status in the upper right:

![runnning_write_bitstream_43](runnning_write_bitstream_43.png)

Step 7: Click **Cancel**

![bitstream_generation_completed_44](bitstream_generation_completed_44.png)

You may see this window pop-up:

![feedback_request_45](feedback_request_45.png)

Feel free to send feedback, set a reminder or click **No**. If you click **No** you may see:

![touchpoint_survey_dialog_46](touchpoint_survey_dialog_46.png)

...click **OK** to dismiss.

**<u><span>Part 6: Export the Design and Open the SDK</span></u>**

Step 1:

A. Click **File**

B. Click **Export**

C. Click **Export Hardware...**

![export_hardware_47](export_hardware_47.png)

Step 2:

A. Click the **Include bitstream** checkbox

B. Click **OK**

![include_bitstream_48](include_bitstream_48.png)

Step 3:

A. Click **File**

B. Click **Launch SDK**

![launch_sdk_49](launch_sdk_49.png)

Note: you can open up the workspace from the SDK by launching the SDK and selecting C:\\vivadoprjs\\axislave\\axislave.sdk as the workspace.

Step 4: Use defaults, click **OK**

![use_sdk_defaults_50](use_sdk_defaults_50.png)

Step 5: After the SDK launches, note the Base Addr of myip\_0:

![note_base_adress_51](note_base_adress_51.png)

**<u><span>Part 7: Install the USB-to-UART Driver and Get the COM Assignment</span></u>**

Steps:

A. Goto \[[link](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)\] for the Silicon Labs CP210x USB to UART Bridge VCP Drivers

B. Download and unzip the correct installer for your OS

C. Install the driver (I did not need to restart on Windows 7 SP1)

D. Click **Windows**

E. Click **Devices and Printers**

![click_devices_and_printers_52](click_devices_and_printers_52.png)

F. You should see Silicon Labs CP210x USB to UART BridgeG. Note the COM port (you'll need this later)

![find_silicon_labs_cp210_53](find_silicon_labs_cp210_53.png)

**<u><span>Part 8: Configure the Board to Boot from JTAG, Connect it to the PC and Power it On</span></u>**

Step 1: Set SW16 to JTAG mode [[mode documentation](https://www.xilinx.com/support/documentation/boards_and_kits/zc702_zvik/ug850-zc702-eval-bd.pdf) see p.16]

![set_sw16_to_jtag_54](set_sw16_to_jtag_54.png)

For the rest of the jumpers see the high-resolution photo of the board in the correct state at \[[link](https://photos.app.goo.gl/DddmM8T5QkTXwA7u5)\]. Step 2: Connect a **Micro-B to Type-A** (host connection) USB cable from U23 (Diglent USB JTAG interface) to the host PC

Step 2: Connect a **Micro-B to Type-A** (host connection) USB cable from U23 (Diglent USB JTAG interface) to the host PC

U23:

![u23_55](u23_55.png)

Micro-B connector:

![micro_b_connector_56](micro_b_connector_56.png)

Type-A connector:

![type_a_connector_57](type_a_connector_57.png)

Step 3: Connect a **Mini-B to Type-A** (host connection) USB cable from J17 (CP2103GM USB-to\_UART Bridge) to the host PC.

J17:

![j17_58](j17_58.png)

Mini-B connector:

![micro_b_connector_59](micro_b_connector_59.png)

Type-A connector:

![type_a_connector_60](type_a_connector_60.png)

Step 4: Turn on the board

![turn_on_board_61](turn_on_board_61.png)

**<u><span>Part 9: Create the Test App and BSP</span></u>**

Step 1:

A. Click **File**

B. Click **New**

C. Click **Application Project**

![click_application_project_62](click_application_project_62.png)

Step 2:

A. Type testaxislave

B. Ensure the **Board Support Package: Create New** radio button is clicked and the name given is **testaxislave\_bsp**

C. Click **Next**

![name_application_project_test_axi_slave_63](name_application_project_test_axi_slave_63.png)

Step 3:

A. Click **Hello World**

B. Click **Finish**

![click_hello_world_64](click_hello_world_64.png)

**<u><span>Part 10: Test Debug Run + Further Config</span></u>**

_These instructions allow debug to be set up more easily than entering in the details manually. After running a debug session, the Debug Configuration is fixed up to reset the FPGA and program the bitstream. The debugger COM port is also configured so that output can be read and the steps to test it and see_ **_Hello World_** _are listed._

Step 1:

A. Right-click **testaxislave**

B. Click **Debug As**

C. Click **Launch on Hardware (System Debugger)**

![launch_system_debugger_65](launch_system_debugger_65.png)

Step 2: Click **OK**

![confirm_perspective_switch_66](confirm_perspective_switch_66.png)

If you see this message click Yes. We'll handle this in the next part.

![fpga_configuration_67](fpga_configuration_67.png)

You should see the Debug Perspective display the code broken on init\_platform():

A. Debug context on main()

B. helloworld.c on init\_platform()

![debug_perspective_broken_code_68](debug_perspective_broken_code_68.png)

Step 3:

A. Click **Run**

B. Click **Debug Configurations...**

![debug_configurations_69](debug_configurations_69.png)

Step 4:

A. Ensure **System Debugger using Debug\_testaxislave** is selected (it should be)

B. Click the **Reset entire system** checkbox

C. Click the **Program FPGA** checkbox

D. Click **Apply**

E. Click **Close**

![setup_system_debugger_70](setup_system_debugger_70.png)

Step 5: Configure Debug View COM

A. Click **SDK Terminal**

B. Click the **'+'** (Connect to serial port.)

![connect_sdk_terminal_to_serial_port_between_70_and_71](connect_sdk_terminal_to_serial_port_between_70_and_71.png)

Step 6: Set Debug View COM settings

A. Enter the COM# from above

B. Click **OK**

![set_com9_71](set_com9_71.png)

Step 7: Make sure you see Hello World on the console

Click on the bug

![click_bug_icon_72](click_bug_icon_72.png)

Step 8: Click **OK**

![confirm_launch_debug_session_73](confirm_launch_debug_session_73.png)

Step 9: Wait for the system to hit the breakpoint on main()

![wait_for_system_to_hit_breakpoint_74](wait_for_system_to_hit_breakpoint_74.png)

Step 10: Click Resume

![resume_75](resume_75.png)

...and wait until you see exit():

![wait_until_you_see_exit_76](wait_until_you_see_exit_76.png)

Step 11: Click on SDK Terminal...

![click_sdk_terminal_77](click_sdk_terminal_77.png)

...to see Hello World:

![see_hello_world_78](see_hello_world_78.png)

**<u><span>Part 11: Test the AXI module</span></u>**

Step 1: Click on the C/C++ view

![click_on_c_c++_view_79](click_on_c_c++_view_79.png)

Step 2: Show myip tests

A. Right-click on **design\_1\_wrapper\_hw\_platform**

B. Click **Refresh**

![refresh_80](refresh_80.png)

Step 3:

A. Expand **design\_1\_wrapper\_hw\_platform, drivers, myip\_v1\_0, src**

B. Double click on **myip\_selftest.c**

![double_click_myip_selftest_81](double_click_myip_selftest_81.png)

Step 4: Select **XStatus MYIP\_Reg\_SelfTest(void \* baseaddr\_p)**

![select_xstatus_82](select_xstatus_82.png)

Step 5:

A. Click **Edit**

B. Click **Copy**

![copy_83](copy_83.png)

Step 6:

A. Expand testaxislave

B. Expand src

C. Double-click helloworld.c

![double_click_helloworld_84](double_click_helloworld_84.png)

Step 7:

A. Press **ENTER** to make room

B. Click **Edit**

C. Click **Paste**

![click_paste_85](click_paste_85.png)

Step 8: Get the base address of myip\_0

A. Double-click the system.hdf file

B. Note the address (it won't let you copy-paste it)

![note_adress_system_hdl_86](note_adress_system_hdl_86.png)

Step 9:

A. Double-click on helloworld.c

B. Fix up the code so it reads: **MYIP\_Reg\_SelfTest(0x43c00000);**

![fix_helloworld_c_87](fix_helloworld_c_87.png)

Step 10: Click the **bug** to restart debugging

![click_bug_to_restart_debugging_88](click_bug_to_restart_debugging_88.png)

Step 11: Click **OK**

![click_ok_89](click_ok_89.png)

Step 12: Click **OK**

![confirm_relaunch_debugging_90](confirm_relaunch_debugging_90.png)

Step 13: Click **Yes**

![confirm_perspective_switch_91](confirm_perspective_switch_91.png)

You should see the code stopped at the breakpoint on main()

![code_stopped_on_breakpoint_92](code_stopped_on_breakpoint_92.png)

Step 14: Click **Resume**

![click_resume_93](click_resume_93.png)

You should see:

![slave_register_passed_94](slave_register_passed_94.png)

**<u><span>References</span></u>**

-   Xilinx logo found via [https://twitter.com/xilinxinc](https://twitter.com/xilinxinc) at \[[link](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]