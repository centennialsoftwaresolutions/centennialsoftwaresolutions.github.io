# Light Up ZC706 LEDs Using Push Buttons with VHDL

![xilinx_logo_1](xilinx_logo_1.png)

This post shows how to use VHDL to connect SW7, SW9 and SW8 to LCR PL GPIO LEDS using VHDL.

This post picks up right after \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/post/create-a-zc706-vivado-project)\].

**<u><span>Prerequisites</span></u>**

This post assumes Vivado 2018.2 and the Digilent cable drivers have been installed.

**<u><span>Push Buttons</span></u>**

![push_buttons_2](push_buttons_2.png)

![buttons_diagram_3](buttons_diagram_3.png)

![buttons_chart_4](buttons_chart_4.png)

**<u><span>LEDs</span></u>**

![leds_on_board_5](leds_on_board_5.png)

![leds_diagram_6](leds_diagram_6.png)

![leds_chart_7](leds_chart_7.png)

Note: This table is correct. Table 1-28 on page 60 of the ZC706 Evaluation Board User Guide UG954 (v1.8) August 6, 2019 is not correct (GPIO\_LED\_CENTER's I/O Standard is not right)

**<u><span>Steps</span></u>**

Step 1: Right-click **Design Sources**

![design_sources_8](design_sources_8.png)

Step 2: Click **Add Sources...**

![add_scources_9](add_scources_9.png)

Step 3: (A) Click **Add or create design sources** and (B) click **Next >**

![add_or_create_design_sources_10](add_or_create_design_sources_10.png)

Step 4: Click **Create File**

![click_create_file_11](click_create_file_11.png)

Step 5: (A) Click the **down arrow** and click (B) **VHDL**

![click_vhdl_12](click_vhdl_12.png)

Step 6: (A) Enter **buttoned** as the **File name:** and (B) click **OK**

![enter_buttonled_filename_13](enter_buttonled_filename_13.png)

Step 7: Click **Finish**

![finish_buttonled_filename_14](finish_buttonled_filename_14.png)

Step 8: Define the module

A)

Enter in:

GPIO\_SW\_LEFT

GPIO\_SW\_CENTER

GPIO\_SW\_RIGHT

...and

GPIO\_LED\_LEFT

GPIO\_LED\_CENTER

GPIO\_LED\_RIGHT

...and mark the Direction of the 3 GPIO\_LED Port Names: **out**

B) Click **OK**

![define_module_15](define_module_15.png)

Step 9: Double click **buttonled**

![double_click_buttonled_16](double_click_buttonled_16.png)

You should see:

![buttonled_code_17](buttonled_code_17.png)

Step 10:

Enter the following between **begin** and **end Behavioral;**

GPIO_LED_LEFT <= GPIO_SW_LEFT;
GPIO_LED_CENTER <= GPIO_SW_CENTER;
GPIO_LED_RIGHT <= GPIO_SW_RIGHT;

buttonled.vhd should look like this:

![add_behaviors_18](add_behaviors_18.png)

Step 11: Click **save**

![save_changes_19](save_changes_19.png)

Step 12: Click **Open Elaborated Design**

![open_elaborated_design_20](open_elaborated_design_20.png)

Step 13: Click **OK**

![confirm_enter_elaborated_design_21](confirm_enter_elaborated_design_21.png)

You should see pop-up status windows like:

![status_window_22](status_window_22.png)

...and then:

![schematic_23](schematic_23.png)

Step 14: (A) Click **Window** and (B) click **I/O Ports**

![click_io_ports_24](click_io_ports_24.png)

Step 15: (A) Click **I/O Ports**, (B) fill in the **Package Pin** as listed and (C) set in the **I/O Std** to **LVCMOS15** for the **CENTER** ports and **LVCMOS25** for the other ports (as shown above)**:**

![change_io_std_25](change_io_std_25.png)

Step 16: Click **Run Synthesis**

![run_synthesis_26](run_synthesis_26.png)

Step 17: Click **Save**

![save_project_27](save_project_27.png)

Step 18: (A) Set **File name:** to **constraints0** and (B) click **OK**

![change_filename_to_constraints_28](change_filename_to_constraints_28.png)

Step 19: Accept the defaults and click **OK**

![accept_defaults_29](accept_defaults_29.png)

You should see some status in the upper right corner:

![running_synth_design_30](running_synth_design_30.png)

Step 20: Click **OK** to Run Implementation

![run_implementation_31](run_implementation_31.png)

Step 21: Accept defaults and click **OK**

![accept_defaults_32](accept_defaults_32.png)

You should see the status of **Implementation** in the upper right corner:

![implementation_33](implementation_33.png)

Note: implementation will take longer than synthesis

Step 22: (A) Select **Generate Bitstream** and (B) click **OK**

![select_generate_bitstream_34](select_generate_bitstream_34.png)

Step 23: Accept defaults and click **OK**

![accept_defaults_32](accept_defaults_32.png)

You will see the status of **Generate Bitstream** in the upper right corner

![status_genetate_bitstream_35](status_genetate_bitstream_35.png)

Note: This will take a little bit of time to complete (not as much as Implementation)

Step 24: (A) Click **Open Hardware Manager** and (B) click **OK**

![open_hardware_manager_36](open_hardware_manager_36.png)

Step 25:

Plug the power supply into the board:

![plug_power_supply_into_board_37](plug_power_supply_into_board_37.png)

Plug the Micro-B end of a Micro-B to Standard-A USB cable into the Digilent USB-to-JTAG interface:

![plug_micro_b_into_board_38](plug_micro_b_into_board_38.png)

Plug the Standard-A end of a Micro-B to Standard-A USB cable into the computer

![plug_standard_a_into_computer_39](plug_standard_a_into_computer_39.png)

Power on the ZC706

![power_on_zc706_40](power_on_zc706_40.png)

Step 26: Click **Open target**

![click_open_target_41](click_open_target_41.png)

Step 27: Click **Auto Connect**

![auto_connect_42](auto_connect_42.png)

Step 28: Click **Program device**

![program_device_43](program_device_43.png)

Step 29: Click **Program**

![click_program_44](click_program_44.png)

You should see:

![programming_device_45](programming_device_45.png)

Now when you press SW7, SW9 and SW 8, the PL LEDs will light up as seen here:

**<u><span>Extra</span></u>**

To see the constraints that get saved:

A) Click **PROJECT MANAGEMENT**

B) Expand **Constraints (1)**

C) Double click on **constraints0.xdc (target)**

D) Examine

![check_constraints_saved_46](check_constraints_saved_46.png)

Here is the content of constraints0.xdc as text:

set_property PACKAGE_PIN G2 [get_ports GPIO_LED_CENTER]
set_property PACKAGE_PIN Y21 [get_ports GPIO_LED_LEFT]
set_property PACKAGE_PIN W21 [get_ports GPIO_LED_RIGHT]
set_property PACKAGE_PIN K15 [get_ports GPIO_SW_CENTER]
set_property PACKAGE_PIN AK25 [get_ports GPIO_SW_LEFT]
set_property PACKAGE_PIN R27 [get_ports GPIO_SW_RIGHT]
set_property IOSTANDARD LVCMOS15 [get_ports GPIO_LED_CENTER]
set_property IOSTANDARD LVCMOS25 [get_ports GPIO_LED_LEFT]
set_property IOSTANDARD LVCMOS25 [get_ports GPIO_LED_RIGHT]
set_property IOSTANDARD LVCMOS15 [get_ports GPIO_SW_CENTER]
set_property IOSTANDARD LVCMOS25 [get_ports GPIO_SW_LEFT]
set_property IOSTANDARD LVCMOS25 [get_ports GPIO_SW_RIGHT]

**<u><span>References</span></u>**

-   Xilinx ZC706 User Guide \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/boards_and_kits/zc706/ug954-zc706-eval-board-xc7z045-ap-soc.pdf)\] (no login required)
    
-   Xilinx ZC706 Schematics \[[<u><span>link</span></u>](https://www.xilinx.com/member/forms/download/design-license.html?cid=396436&filename=zc706-schematic-xtp215.zip)\] (login required)
    
-   Xilinx logo from [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc)