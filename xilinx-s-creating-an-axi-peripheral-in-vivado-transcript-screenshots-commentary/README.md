# Xilinx's "Creating an AXI Peripheral in Vivado": Transcript, Screenshots & Commentary

![video_start_1](video_start_1.png)

This post presents a transcript + screenshots of "Creating an AXI Peripheral in Vivado" from Xilinx. It is intended to reinforce learning how to create an AXI peripheral in Vivado and provide a reference to the steps presented. Corrections and tips have also been included to further aid learning. In addition, some screens have been zoomed and cropped to make certain actions more clear.

The original video can be found \[[<u><span>here</span></u>](https://www.xilinx.com/video/hardware/creating-an-axi-peripheral-in-vivado.html)\]\[[<u><span>YouTube</span></u>](https://www.youtube.com/watch?time_continue=50&v=8hzzVhPw6uw)\].

**<u><span>You Will Learn How To:</span></u>**

-   Use the **Create and Package IP** feature of Vivado
    
-   Create an AXI slave that echos registers writes
    
-   Run the auto testbench to verify the IP
    
-   Import the IP into a Micro Blaze design
    
-   Test reads and writes from code running on the MicroBlaze using SDK
    

**<u><span>Transcript, Screenshots and Commentary</span></u>**

(00:03) Hello and welcome to this Vivado QuickTake video

![viado_quicktake_2](viado_quicktake_2.png)

Note: the title presented, "Packaging Custom IP for use with IP Integrator" does not line up with the title listed on the site hosting the video.

(0:08) In this video you'll learn how to create an AXI peripheral to which custom logic can be added to create a customer IP using the **create and package** IP feature of Vivado.

![creating_axi_peripheral_3](creating_axi_peripheral_3.png)

![what_you_will_learn_4](what_you_will_learn_4.png)

(0:21) This training assumes that you are familiar with designing IP subsystems in IP integrator. You can watch some of the quick take videos on IP Integrator as shown on this slide:

![prerequisites_and_assumptions_5](prerequisites_and_assumptions_5.png)

Note: here are the links to the videos:

-   [<u><span>https://www.xilinx.com/video/hardware/ip-subsystems-vivado-ip-integrator.html</span></u>](https://www.xilinx.com/video/hardware/ip-subsystems-vivado-ip-integrator.html)
    
-   [<u><span>https://www.xilinx.com/video/hardware/ip-integrator-advanced-user-tips.html</span></u>](https://www.xilinx.com/video/hardware/ip-integrator-advanced-user-tips.html)
    

(00:32) In this Quick Take video we'll **<u><span> create a new project in Vivado using the create and package IP</span></u>** feature, we will then **<u><span>create a slave AXI peripheral</span></u>**. We'll **<u><span>create a test-bench </span></u>** and **<u><span>necessary drivers</span></u>** for the peripheral for developing a software application in SDK. We'll **<u><span>simulate the AXI peripheral in Vivado</span></u>** to ensure that the registers of the AXI peripheral can be written and read from using an AXI bus functional simulation model. Then we'll **<u><span>create a MicroBlaze processor based system</span></u>** in which we will **<u><span>add this custom IP</span></u>**. The **<u><span>design will be then implemented</span></u>** and the **<u><span>bitstream will be generated</span></u>**. We'll then **<u><span> export the hardware to SDK</span></u>** and **<u><span>create a test application and generate an ELF</span></u>**. Finally, we'll **<u><span>launch our application on the target board: KC705</span></u>** and **<u><span>verify its functionality</span></u>**.

![agenda_6](agenda_6.png)

(1:18) We start our design by launching Vivado and creating a new project from the Quick Start page. We'll name the project and specify the location where the project will be saved. We'll skip some of the other options for adding existing RTL IP constraints to the project at this time as everything needed for this project will be generated later.

**<u><span>Create a New Project</span></u>**

Step: click **Create New Project**

![create_new_project_7](create_new_project_7.png)

Step: click **Next**

![next_new_project_8](next_new_project_8.png)

Note: in the video the user taps **Enter** on the keyboard to go to the **Next >** screen

Step: enter a **Project name,** axi\_peripheral in this case and click **Next**

![enter_project_name_9](enter_project_name_9.png)

Step: click **Next**

![rtl_project_10](rtl_project_10.png)

Step: click **Next**

![next_on_new_sources_11](next_on_new_sources_11.png)

Step: click **Next**

![next_on_ip_12](next_on_ip_12.png)

Step: click **Next**

![next_on_constraints_13](next_on_constraints_13.png)

(1:51) We select boards in the default part page. Vivado is board-aware and it knows the physical connections present on our target board. It can thus generate the appropriate physical and timing constraints where our target board based on the interfaces that we choose in our design, we select the KC705 target board here.

Step: click **Boards**

![click_boards_14](click_boards_14.png)

Step: click **Kintex-7 KC705 Evaluation Platform**

![click_kintex_7_kc705_15](click_kintex_7_kc705_15.png)

Step: click **Next**

![next_on_boards_16](next_on_boards_16.png)

(2:13) Lets review the summary screen to make sure that all the options have been entered correctly and click finish.

Step: click **Finish**

![new_project_summary_17](new_project_summary_17.png)

Output: the **Create Project** status bar pops up

![create_project_status_bar_18](create_project_status_bar_18.png)

Output: the **Create Project** pop-up shows **Creating project...**

![creating_project_19](creating_project_19.png)

Output: the **Create Project** pop-up shows: **Initializing project...**

![initlizing_axi_project_between_19_and_20](initlizing_axi_project_between_19_and_20.png)

(02:19) Once the project has been created, we launch the **create and package IP** feature. Using this feature, you can either package a new IP or you can create a custom AXI peripheral to which your logic can then be added to make your own custom IP.

**<u><span>Create and Package IP</span></u>**

Step: click **Tools** > **Create and Package IP...**

![create_and_package_ip_20](create_and_package_ip_20.png)

Step: click **Next**

![create_and_package_new_ip_next_21](create_and_package_new_ip_next_21.png)

(2:35) When you launch the create an IP package feature in a new project, you have two choices: (1) you either package a preexisting project directory or you can create a new AXI4 peripheral. We choose the creating a new AXI peripheral and click next.

Step: click **Create a new AXI4 peripheral**

![create_new_axi4_peripheral_22](create_new_axi4_peripheral_22.png)

Step: click **Next**

![next_new_axi4_peripheral_23](next_new_axi4_peripheral_23.png)

(2:53) In the next page we can specify a several options such as name, version, display name, description, and the location where the IP will be created. Once the IP is created, you can search for the IP in the IP catalog using the name given to this peripheral. Also note down the IP location. This is where the IP repository is created.

Step: click **Next**

![set_ip_name_and_location_24](set_ip_name_and_location_24.png)

(03:18) On the add interfaces page you choose the number of interfaces that you want the AXI peripheral to have. Interfaces can be added by clicking the plus sign and deleted by selecting the delete icon. Notice that the components symbol also gets updated as you add and delete interfaces. Several properties of the AXI4 peripheral can be specified on this page. You can specify the name of the AXI interface in the name field. You can choose the type of AXI4 protocol desired. The choices are light, full and stream. You can specify whether the interface is created in a master mode or a slave mode. You can also specify the data width for the interface and the number of registers desired. Currently the number of registers supported by this feature for AXI Lite interfaces between 4 to 512. For the purposes of this video, we'll go with the default values.

**<u><span>Demonstration of How to Add and Remove an AXI Interface (Not Required for These Steps)</span></u>**

Step: click **+** to add an interface

![plus_to_add_interface_25](plus_to_add_interface_25.png)

Output: a new AXI slave interface pops up after clicking **+**

![new_axi_slave_interface_26](new_axi_slave_interface_26.png)

Step: click **X** to remove an interface

![x_remove_interface_27](x_remove_interface_27.png)

Output: the new interface disappears after clicking the **X** to remove an interface

![new_interface_removed_28](new_interface_removed_28.png)

Output: pop up tool-tip text on **Interface Type**

![interface_type_pop_up_tool_tip_29](interface_type_pop_up_tool_tip_29.png)

Output: the **Interface Type** options: **Lite**, **Full** and **Stream**

![interface_type_options_30](interface_type_options_30.png)

Output: the **Interface Mode** options: **Master** and **Slave**

![interface_mode_options_31](interface_mode_options_31.png)

Output: the tool-tip text of **Interface Type:**

-   Lite : Simple, non-burst control register style interface
    
-   Full : Burst Capable, high-throughput memory mapped interface
    
-   Stream: Burst Capable, high-throughput streaming interface
    

Note: For more details on the AXI4 specification click here (TBD get link)

![interface_type_tool_tip_32](interface_type_tool_tip_32.png)

Output: the tool-tip text of **Data Width (Bits)**

![data_width_tool_tip_33](data_width_tool_tip_33.png)

(4:09) Click next to get to the by summary page...

**<u><span>Continue Creating and Packaging a New AXI Peripheral</span></u>**

Step: click **Next**

![next_creating_packaging_axi_peripheral_34](next_creating_packaging_axi_peripheral_34.png)

(4:10) ...where you can either add the IP to the repository or edit the IP further to create a custom IP. You can also create a test-bench to verify the AXI4 peripheral using an AXI bus functional simulation model or you can test the IP in hardware by using the **JTAG-to-AXI IP core**. In this case we will select the verify peripheral IP using AXI4 BFM simulation interface option...

Output: the default **create a customer IP** screen pops up

![create_customer_ip_screen_35](create_customer_ip_screen_35.png)

Step: click **Verify peripheral IP using AXI4 BFM Simulation interface**

![verify_peripheral_ip_using_axi4_bfm_simulation_interface_36](verify_peripheral_ip_using_axi4_bfm_simulation_interface_36.png)

(4:32) ...and click on finish to create the AXI peripheral.

Step: click **Finish**

![finish_create_peripheral_37](finish_create_peripheral_37.png)

Output: a **Creating new peripheral...** window pops up

![creating_new_peripheral_38](creating_new_peripheral_38.png)

(04:34) As you notice, a block design is created and an AXI peripheral is instantiated unconnected to the AXI bus functional model.

Output: a **Opening BFM IPI demonstration design...** status window pops up

![opening_bfm_ipi_demonstration_design_39](opening_bfm_ipi_demonstration_design_39.png)

Output: **create\_bd\_design** output on the Tcl Console

![create_bd_design_on_console_40](create_bd_design_on_console_40.png)

Output: the diagram starts to populate, **ACLK**, **ARESETN** and **myip\_0** are added

![diagram_starts_populating_41](diagram_starts_populating_41.png)

Output: the diagram continues to populate, **master\_0** is added

![master_0_added_42](master_0_added_42.png)

Output: ACLK is connected to m\_axi\_lite\_aclk & s00\_axi\_aclk and ARESETN is connected to s00\_axi\_aresetn & m\_axi\_lite\_aresetn

![aclk_aresetn_connecting_43](aclk_aresetn_connecting_43.png)

Output: additional Tcl Console output about **/myip\_0/S00\_AXI/S00\_AXI\_reg** being mapped into **/master\_0/Data\_lite** at **0x44A00000**

![console_myip_mapped_to_master_44](console_myip_mapped_to_master_44.png)

Output: additional Tcl Console about VHDL and bd file for the BFM being written out.

![hierarchical_elaboration_completed_45](hierarchical_elaboration_completed_45.png)

Output: Create Peripheral pop-up reports: **Generate IP 'myip\_v1\_0\_bfm\_1\_myip\_0\_0'...**

![generate_ip_myip_myip_46](generate_ip_myip_myip_46.png)

Output: Create Peripheral pop-up reports: **Generate IP 'myip\_v1\_0\_bfm\_1\_master\_0\_0'...**

![generateing_ip_myip_master_47](generateing_ip_myip_master_47.png)

Output: Create Peripheral pop-up reports: **Running xelab...** (note: xelab is the simulator compiler. See \[[<u><span>UG900</span></u>](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2015_3/ug900-vivado-logic-simulation.pdf)\] p.120 for more info)

![running_xelab_48](running_xelab_48.png)

Output: Create Peripheral pop-up reports: **Launching simulation for 'myip\_v1\_0\_tb\_behav'...**

![launching_simulation_for_myip_49](launching_simulation_for_myip_49.png)

Output: xsim starts to run

![xsim_starts_to_run_50](xsim_starts_to_run_50.png)

(05:01) The design is then elaborated and simulation is launched. The test-bench that is created with this design, exercises the bus functional model (BFM) to generate several read and write transactions. Those transactions can then be verified in the simulation window as well as on the Tcl console where the result of read/write transactions are written out.

Output: xsim running, current time reported.

![xsim_running_current_time_reported_51](xsim_running_current_time_reported_51.png)

Output: xsim done

![xsim_done_52](xsim_done_52.png)

**<u><span>How to Format Objects as Hex</span></u>**

Demo step: click a bus in the **Objects** window

![click_bus_in_objects_window_53](click_bus_in_objects_window_53.png)

Demo step: click Radix, Hexadecimal

![radix_hexadecimal_54](radix_hexadecimal_54.png)

Output: see the hex values in the Objects window

![see_hex_values_55](see_hex_values_55.png)

(5:23) Take a moment to look at the waveform window and also the TCL console to verify that write and read operations took place alright.

**<u><span>How to Format Signals as Hex</span></u>**

Step: select **signals** > select **Radix** > select **Hexadecimal**

![signals_radix_hexadecimal_56](signals_radix_hexadecimal_56.png)

Output: signals in hex

![output_signals_in_hex_57](output_signals_in_hex_57.png)

**<u><span>How to Zoom Fit</span></u>**

Step: TBD

![step_tdb_58](step_tdb_58.png)

Output: zoomed version

![output_zoomed_version_59](output_zoomed_version_59.png)

(5:35) You will notice several statements in the Tcl console showing the data written to the peripheral and the data read out from it.

Output: the Tcl console data

![tcl_console_data_60](tcl_console_data_60.png)

Output: start of the Tcl console data

![start_of_tcl_console_data_61](start_of_tcl_console_data_61.png)

Output: end of the Tcl console data

![end_of_tcl_console_data_62](end_of_tcl_console_data_62.png)

(05:44) If adding custom logic to this peripheral is desired, you can add your custom logic to this peripheral at this time. The peripheral can then be repackaged to turn it into a custom IP.

Step: add custom logic: TBD

![add_custom_logic_tbd_63](add_custom_logic_tbd_63.png)

(6:00) At this point we can close the simulation and exit Project. Click okay to exit from Vivado.

**<u><span>How to Exit Vivado</span></u>**

Step: Click File > Exit

![file_exit_64](file_exit_64.png)

Step: click OK to complete exiting Vivado

![ok_exit_vivado_65](ok_exit_vivado_65.png)

**<u><span>Create a MicroBlaze system in Vivado and Connect our Custom AXI Peripheral</span></u>**

(6:18) Next one we'll create a new Vivado project to create a MicroBlaze based system in which we will instantiate the AXI peripheral that we just created. Again, like before we'll create a Vivado project using the default settings and making sure that we target it to the KC705 board.

Step: click **Create New Project**

![create_new_project_66](create_new_project_66.png)

Click **Next**

![create_new_vivado_project_next_67](create_new_vivado_project_next_67.png)

Step: enter **microblaze\_system** as the **Project name:** and click **Next**

![name_project_microblaze_system_68](name_project_microblaze_system_68.png)

Step: leave **RTL Project** selected and click **Next**

![microblaze_rtl_project_69](microblaze_rtl_project_69.png)

Step: click **Next**

![microblaze_next_add_scources_70](microblaze_next_add_scources_70.png)

Step: click **Next**

![microblaze_next_add_ip_71](microblaze_next_add_ip_71.png)

Step: click **Next**

![microblaze_next_add_constraints_72](microblaze_next_add_constraints_72.png)

Step: click Boards

![microblaze_click_boards_73](microblaze_click_boards_73.png)

Step: click **Kintex-7 KC705 Evaluation Platform**

![microblaze_click_kintex_7_74](microblaze_click_kintex_7_74.png)

Step: click **Next**

![microblaze_click_next_on_boards_75](microblaze_click_next_on_boards_75.png)

(06:54) Take a moment to review the new project summary page to ensure that all the products settings have been entered correctly and click finish.

Step: after review, click **Next**

![microblaze_system_project_created_76](microblaze_system_project_created_76.png)

Output: a **Create Project** status window pops up

![microblaze_create_project_window_77](microblaze_create_project_window_77.png)

Output: the **Create Project** window displays **Initializing project**

![microblaze_initializing_project_78](microblaze_initializing_project_78.png)

(7:08) Once the projects created we need to create a block design.

**<u><span>Create an IP Integrator Block Design</span></u>**

Step: click **Create Block Design**

![create_block_design_79](create_block_design_79.png)

(7:13) We give a name to the block design and click okay.

![create_block_design_80](create_block_design_80.png)

(7:34) In the block design canvas we instantiate a MicroBlaze processor.

![instantiate_microblaze_processor_81](instantiate_microblaze_processor_81.png)

![select_microblaze_block_design_82](select_microblaze_block_design_82.png)

![adding_ip_83](adding_ip_83.png)

![microblaze_ip_added_84](microblaze_ip_added_84.png)

(7:49) Notice that as the processor is instantiated in the design canvas designers assistance becomes available to us. Click on the link to use the block automation. In the run block automation dialogue box we'll increase the depth of the memory to 32 kilobyte and let all the other remaining options to their default value.

![run_block_automation_85](run_block_automation_85.png)

![set_32kb_local_memory_86](set_32kb_local_memory_86.png)

![block_automation_setup_complete_87](block_automation_setup_complete_87.png)

![running_automation_88](running_automation_88.png)

(08:17) Once the basic subsystem is created, we can instantiate the AXI4 peripheral that we had created earlier.

![basic_subsystem_created_89](basic_subsystem_created_89.png)

(8:22) To make the AXI peripheral available in the IP catalog, we need to add the repository containing this IP to the Vivado project. We do this by clicking on project settings under project manager and then selecting the IP icon in the left panel.

**<u><span>Make our Customer Peripheral Available</span></u>**

![project_settings_90](project_settings_90.png)

![general_project_settings_91](general_project_settings_91.png)

![add_repository_92](add_repository_92.png)

![select_ip_repo_93](select_ip_repo_93.png)

(8:37) Click on IP repository and then browse to the repository called IP repo and click select.

![ip_repo_added_94](ip_repo_added_94.png)

![ok_project_settings_95](ok_project_settings_95.png)

(8:42) As soon as the IP repository is added to the project, you can see the AXI peripherial called **myip** that was created earlier.

![add_ip_to_block_design_96](add_ip_to_block_design_96.png)

![myip_v1.0_97](myip_v1.0_97.png)

![select_myip_v1.0_98](select_myip_v1.0_98.png)

![adding_ip_99](adding_ip_99.png)

![add_ip_100](add_ip_100.png)

(08:54) Let's instantiate this IP now along with a UART Lite IP in the design. The UART Lite is the accessory to monitor communication between the hardware and software in the terminal window in SDK.  

![axi_uartlite_101](axi_uartlite_101.png)

![adding_ip_102](adding_ip_102.png)

![uartlite_added_103](uartlite_added_103.png)

(9:06) You will notice that designers assistance is available again, which we can use to make quick connections of the newly instantiated IP to the MicroBlaze subsystem. I mentioned earlier Vivado is board aware and knows the interfaces present on the KC705 board.

![click_board_part_interfaces_104](click_board_part_interfaces_104.png)

(9:23) As we use designers assistance to make connection to the different interfaces on the board, you will notice that the interfaces that are using the design show up in the connected interfaces folder in the board interface window.

![run_connection_automation_105](run_connection_automation_105.png)

![dk_wiz_106](dk_wiz_106.png)

![connection_automation_for_sys_diff_clock_107](connection_automation_for_sys_diff_clock_107.png)

![clocking_wizard_108](clocking_wizard_108.png)

![initiate_clock_connection_automation_109](initiate_clock_connection_automation_109.png)

![running_connection_automation_110](running_connection_automation_110.png)

![clock_connection_automation_complete_111](clock_connection_automation_complete_111.png)

![run_connection_automation_for_clk_wiz_1_112](run_connection_automation_for_clk_wiz_1_112.png)

![select_clock_wizard_reset_113](select_clock_wizard_reset_113.png)

![connection_automation_for_clock_reset_114](connection_automation_for_clock_reset_114.png)

![run_connection_automation_for_rst_clk_wiz_1_115](run_connection_automation_for_rst_clk_wiz_1_115.png)

![run_connection_automation_reset_116](run_connection_automation_reset_116.png)

![connection_automation_for_myip_0_117](connection_automation_for_myip_0_117.png)

![run_connection_automation_for_myip_0_118](run_connection_automation_for_myip_0_118.png)

(10:07) We only need to use the clock reset on the UART interfaces in this design. Use all of the items that are connection automation link to complete the connectivity of the design.

![running_connection_automation_119](running_connection_automation_119.png)

![myip_0_connected_120](myip_0_connected_120.png)

(10:21) With the design now complete let's make sure that the memory mapping for all the slaves in the design has been done correctly. As the slaves are instantiated in the design IP integrator assigns the memory to each of these automatically. This memory mapping can be changed their desire. In this case, we'll leave the default memory map.

![address_editor_121](address_editor_121.png)

(10:39) At this point, we're ready to validate the design.

![validate_design_122](validate_design_122.png)

![validating_design_123](validating_design_123.png)

(10:43) Validating runs design rule checks on the design running DRC successful, and there are no design errors in this case.

![validation_successful_124](validation_successful_124.png)

(10:51) We can tidy up the design and generate an optimum layout of the design by clicking on regenerate layout.

![regenerate_layout_125](regenerate_layout_125.png)

![cleaned_up_design_126](cleaned_up_design_126.png)

(10:55) At this time, we can save the block design.

![save_block_design_127](save_block_design_127.png)

![block_design_saved_128](block_design_saved_128.png)

(11:01) With a block design now complete regenerate outward products and create a top level wrapper file that instantiates a block design in it.

![sources_129](sources_129.png)

![sources_page_130](sources_page_130.png)

![processor_subsystem_131](processor_subsystem_131.png)

![right_click_processor_subsystem_132](right_click_processor_subsystem_132.png)

![generate_output_products_133](generate_output_products_133.png)

![output_products_to_be_generated_134](output_products_to_be_generated_134.png)

![generate_products_135](generate_products_135.png)

![managing_output_products_136](managing_output_products_136.png)

![create_hdl_wrapper_137](create_hdl_wrapper_137.png)

![let_vivado_manage_wrapper_and_auto_update_138](let_vivado_manage_wrapper_and_auto_update_138.png)

![processor_subsystem_bd_139](processor_subsystem_bd_139.png)

![processor_subsystem_wrapper_140](processor_subsystem_wrapper_140.png)

(11:18) Now we need to implement the design, which kind of be done by clicking on generate bitstream street, which will take the design to synthesis, implementation and finally generate midstream.

![click_processor_subsystem_wrapper_between_140_141](click_processor_subsystem_wrapper_between_140_141.png)

![click_processor_subsystem_wrapper_141](click_processor_subsystem_wrapper_141.png)

![generate_bitstream_142](generate_bitstream_142.png)

![no_implementation_results_available_143](no_implementation_results_available_143.png)

![external_port_reset_144](external_port_reset_144.png)

(11:33) Generating bitstream may take several minutes.

![log_running_vivado_145](log_running_vivado_145.png)

![log_running_2_146](log_running_2_146.png)

![log_running_3_147](log_running_3_147.png)

![log_runnning_4_148](log_runnning_4_148.png)

![log_running_5_149](log_running_5_149.png)

(11:44) After a bitstream has been generated, open the implemented design.

![open_implemented_design_150](open_implemented_design_150.png)

![opening_implemented_design_151](opening_implemented_design_151.png)

![reading_netlist_152](reading_netlist_152.png)

![initilizing_device_153](initilizing_device_153.png)

![loading_netlist_view_154](loading_netlist_view_154.png)

![implemented_design_open_155](implemented_design_open_155.png)

(11:50) Once the implemented design is open, run a timing summary report to make sure that all constraints were met.

**<u><span>Run a Timing Summary to Make Sure Constraints were Met</span></u>**

![report_timing_summary_156](report_timing_summary_156.png)

![report_timing_summary_window_157](report_timing_summary_window_157.png)

![report_timing_summary_running_158](report_timing_summary_running_158.png)

![timing_summary_159](timing_summary_159.png)

(12:09) Take a moment to look at any set up our hold-time violations.

![look_for_hold_time_violations_160](look_for_hold_time_violations_160.png)

(12:17) In this case everything is good...

![no_violations_all_good_161](no_violations_all_good_161.png)

(12:19) ...so we need to export the hardware so we can develop our software application. To do this, we'll export the hardware by selecting export hardware for Sdk.

**<u><span>Export Vivado Hardware to SDK</span></u>**

![minimize_timing_summary_162](minimize_timing_summary_162.png)

![export_hardware_for_sdk_163](export_hardware_for_sdk_163.png)

![export_hardware_for_sdk_window_164](export_hardware_for_sdk_window_164.png)

![check_launch_sdk_165](check_launch_sdk_165.png)

![confirm_export_166](confirm_export_166.png)

(12:44) While exporting the design, we selected the option to launch SDK, so SDK launches with a new window.

![sdk_launching_167](sdk_launching_167.png)

![xilinx_sdk_launched_168](xilinx_sdk_launched_168.png)

![importing_hardware_specification_169](importing_hardware_specification_169.png)

![hw_platform_0_hardware_platform_specification_170](hw_platform_0_hardware_platform_specification_170.png)

![sdk_window_maximized_171](sdk_window_maximized_171.png)

(12:58) In SDK we'll create an empty application project to which we can add some code to exercise the AXI port peripheral on the KC705 target hardware. Lets create an empty application first by creating a new application project and a specifying a name for the project.

**Create a New SDK Project**

![new_application_project_172](new_application_project_172.png)

![name_application_project_173](name_application_project_173.png)

(13:13) In the template space, select to empty application and click **Finish**

![select_empty_application_174](select_empty_application_174.png)

![finish_new_project_setup_175](finish_new_project_setup_175.png)

![project_loading_176](project_loading_176.png)

![project_loading_177](project_loading_177.png)

![project_loading_178](project_loading_178.png)

![project_loading_179](project_loading_179.png)

(13:23) While creating the empty application, SDK creates a selftest application for the AXI peripheral, which we created in Vivado earlier.

![test_peripheral_180](test_peripheral_180.png)

![test_peripheral_bsp_181](test_peripheral_bsp_181.png)

![myip.c_182](myip.c_182.png)

(13:37) This self-test functions need to be called by our custom application code. So essentially what we'll be doing here is just add a few lines of code in our application to call the function that performs the self-test of the IP. The self-test routine, called myip\_selftest, basically writes four bytes of data and reads back those data bytes.

![myip_selftest.c_183](myip_selftest.c_183.png)

(14:00) So we'll add a new file. We'll call this file main.c. In this file is where we will add a few lines of code...

![new_file_184](new_file_184.png)

![finish_new_file_185](finish_new_file_185.png)

Note: the following file was created by the video creator not by the tool. This means you'll need to type this info in.

![info_to_type_in_186](info_to_type_in_186.png)

(14:16) ...to call the function that was created earlier for exercising our AXI peripheral IP.

![myip_selftest.c_187](myip_selftest.c_187.png)

![myip.h_188](myip.h_188.png)

(14:23) Now we are ready to compile this code.

![click_clean_189](click_clean_189.png)

**Click:**

![start_cleaning_190](start_cleaning_190.png)

**Output:**

![operation_in_progress_191](operation_in_progress_191.png)

![build_console_1_192](build_console_1_192.png)

![build_console_2_193](build_console_2_193.png)

![build_console_3_194](build_console_3_194.png)

![build_console_4_195](build_console_4_195.png)

![build_console_6_197](build_console_6_197.png)

![build_console_5_196](build_console_5_196.png)

![build_console_7_198](build_console_7_198.png)

![build_console_between_7_8](build_console_between_7_8.png)

![build_console_8_199](build_console_8_199.png)

![build_console_9_200](build_console_9_200.png)

![build_console_10_201](build_console_10_201.png)

![build_console_11_202](build_console_11_202.png)

![build_console_12_203](build_console_12_203.png)

![build_console_13_204](build_console_13_204.png)

![build_console_14_205](build_console_14_205.png)

![build_console_15_206](build_console_15_206.png)

![build_console_16_207](build_console_16_207.png)

![build_console_17_208](build_console_17_208.png)

![build_console_18_209](build_console_18_209.png)

![build_console_19_210](build_console_19_210.png)

![build_console_20_211](build_console_20_211.png)

![build_console_21_212](build_console_21_212.png)

![build_console_22_213](build_console_22_213.png)

![build_console_23_214](build_console_23_214.png)

![build_console_24_215](build_console_24_215.png)

![build_console_25_216](build_console_25_216.png)

![build_console_26_217](build_console_26_217.png)

![build_cosnole_27_218](build_cosnole_27_218.png)

![build_console_28_219](build_console_28_219.png)

![build_console_29_220](build_console_29_220.png)

![build_console_30_221](build_console_30_221.png)

![build_console_31_222](build_console_31_222.png)

![build_console_32_223](build_console_32_223.png)

![build_console_33_224](build_console_33_224.png)

![build_console_34_225](build_console_34_225.png)

![build_console_35_226](build_console_35_226.png)

![build_console_36_227](build_console_36_227.png)

![build_console_37_228](build_console_37_228.png)

![build_console_38_229](build_console_38_229.png)

![build_console_39_230](build_console_39_230.png)

![build_console_40_231](build_console_40_231.png)

![build_console_41_232](build_console_41_232.png)

![build_console_42_233](build_console_42_233.png)

![build_console_43_234](build_console_43_234.png)

![build_console_44_235](build_console_44_235.png)

![build_console_45_236](build_console_45_236.png)

Note: linker running

![build_console_46_237](build_console_46_237.png)

![build_console_47_238](build_console_47_238.png)

![build_console_48_239](build_console_48_239.png)

![build_console_49_240](build_console_49_240.png)

![build_console_50_241](build_console_50_241.png)

![build_console_51_242](build_console_51_242.png)

![build_console_52_243](build_console_52_243.png)

Note: the **Binaries** node pops up coincident with **Build Finished** (took 1s.556ms)

![binaries_node_244](binaries_node_244.png)

(14:44) Once compilation has done, take a to look at the console for any warnings or errors that may have been flagged during the process.  

![click_console_between_244_245](click_console_between_244_245.png)

(14:47) In this case, it appears that everything is good, so we'll connect the monitor to monitor the communication between the hardware and the software.

Click:

![click_settings_24_5](click_settings_24_5.png)

Click:

![connection_type_serial_246](connection_type_serial_246.png)

Click:

![confirm_terminal_settings_247](confirm_terminal_settings_247.png)

(15:10) With the monitor connected...

![terminal_1_248](terminal_1_248.png)

(15:14) ...we're ready to program the FPGA.

Click:

![program_fpga_249](program_fpga_249.png)

(15:19) Make sure that the bitstream selected is the correct bitstream for the project.

![ensure_correct_bitstream_250](ensure_correct_bitstream_250.png)

Output:

![program_fpga_1_251](program_fpga_1_251.png)

![program_fpga_2_252](program_fpga_2_252.png)

![program_fpga_3_253](program_fpga_3_253.png)

![operation_in_progress_254](operation_in_progress_254.png)

![initlizing_bitstream_with_elf_data_255](initlizing_bitstream_with_elf_data_255.png)

(15:32) Programming the FPGA may take a minute or so.

Output:

![configuring_fpga_with_bitstream_256](configuring_fpga_with_bitstream_256.png)

...and:

![auto_discovered_257](auto_discovered_257.png)

![fpga_configuration_complete_258](fpga_configuration_complete_258.png)

Output: there is a recompile of the source files whose output matches the output above. The output is not shown again here.

(15:37) Now that the FPGA has been programmed we can launch the ELF file onto the hardware. To do this, we'll select the application code that we just created and launch it on hardware.

![launch_on_hardware_259](launch_on_hardware_259.png)

(16:00) Well, the bottom right of the window, you can see that the code is being launched on hardware:

![code_launching_260](code_launching_260.png)

(16:07) ...and on the terminal you will see the results of the cell test that was performed.

Click:

![maximize_terminal_1_261](maximize_terminal_1_261.png)

Output:

![output_262](output_262.png)

(16:14) The terminal window shows that four write transactions were performed ...

![4_write_transactions_performed_263](4_write_transactions_performed_263.png)

(16:17) ...followed by four read transactions...

![4_read_transactions_264](4_read_transactions_264.png)

(16:18)...and the data for the write and read matches.

(16:32) So in this QuickTake Video, we have created a new AXI peripheral, simulated it using an AXI bus functional model and then verified ts functionality on a KC705 board in a MicroBlaze based design. We have seen how the create and package IP functionality in Vivado allows you to create a master or a slave AXI peripheral, which can be used to create a custom IP.

![video_summary_265](video_summary_265.png)

(16:53) Thanks for watching the Quick Take video.

![video_thank_you_266](video_thank_you_266.png)

![xilinx_video_end_267](xilinx_video_end_267.png)

**<u><span>Tools Used</span></u>**

-   Temi @ \[[<u><span>link</span></u>](https://www.temi.com/)\] was used to transcribe the audio
    
-   The audio was captured using Audacity \[[<u><span>link</span></u>](https://www.audacityteam.org/download/)\]