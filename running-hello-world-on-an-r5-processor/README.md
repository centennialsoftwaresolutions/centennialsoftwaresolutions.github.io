# Running "Hello World" on an Ultra96-V2's R5 Processor

![xilinx_logo_1](xilinx_logo_1.png)

Before performing these steps, its required that the following tutorials have been followed and completed.  

 https://www.centennialsoftwaresolutions.com/post/runnng-barebones-apps-on-the-ultra96-v2-cortex-a53-processor?gclid=EAIaIQobChMI7qLL1r_b5AIVzR-tBh3q1AugEAAYASAAEgIxtfD_BwE 

This guide will simply do a "Hello World" program targeting the R5 processor.  The R5 software will be run from within the SDK so make sure switch SW3 is set correctly to run from the JTAG/Serial port.

1.) Create a new Application Project

**File->New->Application Project**

2.) Select a Project Name and R5 processor. Note that a new BSP will need to be created if one hasnt been created for the R5. Select Next to continue.

![application_project_paremeters_2](application_project_paremeters_2.png)

3.) Select the Hello World template and select Finish to continue.

![hello_world_template_3](hello_world_template_3.png)

4.) Open the R5 BSP just created and double click on the system.mss file to open it and select "Modify this BSP's Settings"

![modify_bsp_settings_4](modify_bsp_settings_4.png)

5.) Click on standalone and change the STDIN and STDOUT ports to "psu\_uart\_1".

![change_to_psu_uart_1_5](change_to_psu_uart_1_5.png)

6.) The BSP should be rebuilt which can be seen in the "SDK Log Window"

![bsp_rebuilding_6](bsp_rebuilding_6.png)

7.) Make sure your Ultra96 is powered on, the Power ON Button(SW4) has been pushed (should hear fans running) and the USB is connected.

8.) Add your PC COM Port to the SDK Terminal Window.

![add_pc_com_port_7](add_pc_com_port_7.png)

![connected_to_com4_8](connected_to_com4_8.png)

9.) Select your R5\_HelloWorld Application Project and then Right Click->Run As->Launch On Hardware (System Debugger).

10.) Verify Serial Port Output.

![verify_serial_port_output_9](verify_serial_port_output_9.png)

11.) Congrats. Feel free to experiment with other R5 templates.

<u><span>Reference</span></u>

-   Xilinx logo clipped from [<u><span>xilinx.com</span></u>](http://xilinx.com/)