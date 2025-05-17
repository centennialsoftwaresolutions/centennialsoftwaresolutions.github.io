# VHDL to Gates and Routing on an FPGA with Vivado

![xilinx_logo_1](xilinx_logo_1.png)

This post shows how to examine the gates and routing used to implement a VHDL design and set of constraints on the Zynq-7000 of a ZC706.

This post picks up right after \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/post/light-up-zc706-leds-using-push-buttons-with-vhdl)\]

**<u><span>Steps</span></u>**

Step 1: Examine the source for functionality

A) Click **PROJECT MANAGER**

B) Expand **Design Sources (1)**

C) Double-click buttonled**(Behavioral) (buttonled.vhd)**

D) Click on **buttonled.vhd**

D) Examine source

![examine_source_2](examine_source_2.png)

Here is the source in text:

Port ( GPIO_SW_LEFT : in STD_LOGIC;
       GPIO_SW_CENTER : in STD_LOGIC;
       GPIO_SW_RIGHT : in STD_LOGIC;
       GPIO_LED_LEFT : out STD_LOGIC;
       GPIO_LED_CENTER : out STD_LOGIC;
       GPIO_LED_RIGHT : out STD_LOGIC);

end buttonled;

architecture Behavioral of buttonled is

begin
    GPIO_LED_LEFT <= GPIO_SW_LEFT;
    GPIO_LED_CENTER <= GPIO_SW_CENTER;
    GPIO_LED_RIGHT <= GPIO_SW_RIGHT;
end Behavioral;

Step 2: Examine the constraints for pin and drive strength assignments

A) Expand **Constraints (1)**

B) Expand **constrs\_1 (1)**

C) Double-click **constrints0.xdc (target)**

D) Examine constraints

![examine_constraints_3](examine_constraints_3.png)

Here are the constraints in text:

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

Step 3: Examine the schematic and device view for the entire buttonled.vhd circuit

A) Click on **buttonled.vhd**

![click_buttonled_vhd_4](click_buttonled_vhd_4.png)

B) Expand **RTL ANALYSIS**

C) Expand **Open Elaborated Design**

D) Click **Schematic**

E) Click on the white space above the schematic

![click_on_white_space_5](click_on_white_space_5.png)

Step 4: Examine the Device view while in **RTL ANALYSIS**

A) Ensure you did Step 3 (make sure you clicked on the white space in the schematic view)

B) Click **Window**

C) Click **Device**

![click_device_6](click_device_6.png)

D) Click the **Float** icon

![click_float_icon_7](click_float_icon_7.png)

E) Place the Device window on a new screen

F) Click **Auto-fit Selection** so there's a box around it

G) Click Routing Resources so there's a box around it

H) Click **Maximize**

![maximize_window_8](maximize_window_8.png)

Now when you click on an element in the schematic, the Device window will automatically zoom there.

I) Click GPIO\_SW\_CENTER in the schematic

![click_gipo_sw_center_9](click_gipo_sw_center_9.png)

You should see the Device view jump to:

![device_view_switch_10](device_view_switch_10.png)

Note: this is the pad on K15 that GPIO\_SW\_CENTER maps to.

J) Click on the connection between GPIO\_SW\_CENTER and the I port of GPIO\_SW\_CENTER\_IBUF\_inst

![click_connection_11](click_connection_11.png)

You should see the Device view jump to:

![device_view_switch_12](device_view_switch_12.png)

(K1) Click and drag (K2) to zoom in

![click_drag_k2_13](click_drag_k2_13.png)

You should see:

![k15_connection_switch_14](k15_connection_switch_14.png)

Notice the connection pointed at by the green arrow.

Here is the rest of the circuit in the RTL ANALYSIS view:

GPIO\_SW\_CENTER\_IBUF\_inst:

![gpio_sw_center_ibuf_inst_15](gpio_sw_center_ibuf_inst_15.png)

![k15_display_16](k15_display_16.png)

The connection between the O of GPIO\_SW\_CENTER\_IBUF\_inst and the I of GPIO\_LED\_CENTER\_OBUF\_inst:

![i_and_o_connection_17](i_and_o_connection_17.png)

![i_and_o_display_connection_18](i_and_o_display_connection_18.png)

Zoomed in at **Start**:

![zoom_in_on_start_19](zoom_in_on_start_19.png)

Zoomed in at the **End**:

![zoom_in_on_end_20](zoom_in_on_end_20.png)

GPIO\_LED\_CENTER\_OBUF\_inst

![gpio_led_center_obuf_inst_21](gpio_led_center_obuf_inst_21.png)

![gpio_led_center_obuf_inst_display_22](gpio_led_center_obuf_inst_display_22.png)

The connection between the O of GPIO\_LED\_CENTER\_OBUF\_inst and GPIO\_LED\_CENTER:

![center_obuf_and_center_connection_23](center_obuf_and_center_connection_23.png)

![center_obuf_and_center_connection_display_24](center_obuf_and_center_connection_display_24.png)

...and GPIO\_LED\_CENTER:

![gpio_led_center_25](gpio_led_center_25.png)

![gpio_led_center_display_26](gpio_led_center_display_26.png)

Step 5: Examine the Device view while in IMPLEMENTATION

Note: you will see all the routing in this view

A) Click **IMPLEMENTATION**

![clickl_implementation_27](clickl_implementation_27.png)

B) Click **Window**

C) Click **Device**

![click_device_28](click_device_28.png)

D) Click **Float**

![click_float_29](click_float_29.png)

E) Place the Device window on a new screen

F) Click **Auto-fit Selection** so there's a box around it

G) Click **Routing Resources** so there's a box around it

H) Click **Maximize**

![click_maximize_30](click_maximize_30.png)

You should see:

![maximized_window_31](maximized_window_31.png)

Here is the actual routing:

![routing_32](routing_32.png)

![ilogic_x1y340_33](ilogic_x1y340_33.png)

![board_overveiw_1_34](board_overveiw_1_34.png)

![overveiw_switchbox_rioi_inter_35](overveiw_switchbox_rioi_inter_35.png)

![overveiw_center_inter_r_36](overveiw_center_inter_r_36.png)

![larger_overveiw_37](larger_overveiw_37.png)

![switchbox_center_inter_l_38](switchbox_center_inter_l_38.png)

![travel_down_39](travel_down_39.png)

...then travel down:

![continue_traveling_down_40](continue_traveling_down_40.png)

...to the end:

![the_end_41](the_end_41.png)

![switchbox_center_inter_l_42](switchbox_center_inter_l_42.png)

![switchbox_center_inter_r_43](switchbox_center_inter_r_43.png)

![switchbox_center_inter_r_44](switchbox_center_inter_r_44.png)

![board_path_45](board_path_45.png)

![switchbox_rioi_inter_46](switchbox_rioi_inter_46.png)

![board_path_47](board_path_47.png)

![ologic_xiy236_48](ologic_xiy236_48.png)

...and finaly

![final_result_49](final_result_49.png)

**<u><span>Reference</span></u>**

-   Xilinx logo from [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc)