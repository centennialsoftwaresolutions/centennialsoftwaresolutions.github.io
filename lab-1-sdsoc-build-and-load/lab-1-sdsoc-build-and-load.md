# Lab 1 SDSoC Build and Load

![sdsoc_logo_1](sdsoc_logo_1.jpg)

This post is my run through of SDSoC Lab 1 Tutorial at \[[<u><span>link</span></u>](https://github.com/Xilinx/SDSoC-Tutorials/blob/master/getting-started-tutorial/lab-1-introduction-to-the-sdsoc-development-environment.md)\].

**<u><span>Prerequisites</span></u>**

-   Install SDSoC on Linux using a free 60-day trial and launch it \[[<u><span>instructions</span></u>](https://www.centennialsoftwaresolutions.com/blog/install-sdsoc-on-ubuntu-16-04-3)\]
    
-   Have a ZC702 (I used a ZC702 Rev 1.1)
    

**<u><span>Notes</span></u>**

Use the Zynq-7000 on the ZC702 or the ZedBoard available at \[[<u><span>link</span></u>](https://www.xilinx.com/products/boards-and-kits/ek-z7-zc702-g.html)\] and \[[<u><span>link</span></u>](https://store.digilentinc.com/zedboard-zynq-7000-arm-fpga-soc-development-board/)\] to play around with SDSoC.

The ZC702 is $895.00 and the ZedBoard is $449.00.

The key benefit is that you'll only need **2 GB** of host memory to build images for the board.

If you use a Zynq UltraScale+ MPSoC on a ZCU102 (available at \[[<u><span>link</span></u>](https://www.xilinx.com/products/boards-and-kits/ek-u1-zcu102-g.html)\]), you'll need **14 GB** of host memory and $2495.00 for the board.

This advice applies to other situations where you'd like to use a Arm + FPGA fabric. Also long as you don't need a hypervisor or the performance, the Zynq-7000 is a good, economical **and fast** platform for development (Zynq-7000 projects build in much less time).

**<u><span>Steps</span></u>**

1\. Click **Create SDx project**

![create_sdx_project_2](create_sdx_project_2.png)

2\. Keep **Application** selected and click **Next >**

![application_selected_3](application_selected_3.png)

3\. Name your project **lab1,** keep **Use default location** clicked and click **Next >**

![name_project_lab1_4](name_project_lab1_4.png)

**Note**: You can use any 3 to 40 character sequence of a-z, A-Z, 0-9, \_ and -

**Note2**: In a regex: \[a-zA-Z0-9\_ -\]{3,40}

4\. (A) Select the **zc702** and (B) click **Next**

![select_zc702_5](select_zc702_5.png)

5\. Accept defaults and click **Next** on the **System configuration** window

![accept_defaults_6](accept_defaults_6.png)

6\. (A) Select **Matrix Multiplication and Addition** and (B) click **Finish**

![matrix_multiplication_and_addition_7](matrix_multiplication_and_addition_7.png)

You should see:

![project_workspace_8](project_workspace_8.png)

At this point I diverge from the tutorial a little.

7\. Click **build** (this step will take a significant amount of time).

![click_build_9](click_build_9.png)

Note: this step took 1h:24m:29s.132ms, the entire output is \[[<u><span>here</span></u>](https://docs.google.com/document/d/1AhUyuAvUozG3Rk4_e-k5CW116Ce_9TDCqoxt2MTHePQ/edit?usp=sharing)\].

If you need help accessing an SD card from in Ubuntu running on VirtualBox, running on Windows 7 click \[[<u><span>here</span></u>](https://www.centennialsoftwaresolutions.com/blog/sd-card-access-from-ubuntu-16-04-3-on-virtualbox-on-windows-7)\].

8\. To copy the files to the SD card...

Type **cd ~**

Type **cd workspace/lab1/Debug/sd\_card**

Type **ls**

You should see:

![lisk_contents_of_sd_card_10](lisk_contents_of_sd_card_10.png)

ls

BOOT.BIN

image.ub

lab1.elf

README.txt

After replacing pfefferz with your path, type **cp -f \* /media/pfefferz/C002-DEEF/**

Type **ls -l /media/pfefferz/C002-DEEF/** to check that the files were copied

9\. Eject the SD card

![eject_sd_card_11](eject_sd_card_11.png)

10\. Set up minicom

Close SDx and everything else (you'll need to log out and back in)

Type **sudo apt-get install minicom**

Type **sudo adduser $USER dialout**

Log out, (A) click the gear icon, (B) click **Log Out...**

![log_out_12](log_out_12.png)

![log_out_screen_13](log_out_screen_13.png)

Log in, type your password and hit enter

![log_into_ubuntu_14](log_into_ubuntu_14.png)

Open a terminal and type **sudo minicom -s**

At this screen:

![configuration_screen_15](configuration_screen_15.png)

Hit the down arrow until you hit **Serial port setup**

![serial_port_setup_16](serial_port_setup_16.png)

Press **Enter**

At this screen type **F** to turn off **Hardware Flow Control** and type **A**, changing the serial device to **/dev/ttyUSB0**

![serial_port_setup_screen_17](serial_port_setup_screen_17.png)

Things should look like:

![serial_port_setup_settings_18](serial_port_setup_settings_18.png)

Press **Enter** to return to the previous menu

Press down until you get to **Save setup as dfl**

![save_setup_as_dfl_19](save_setup_as_dfl_19.png)

Press **Enter**

You should see:

![configuration_saved_between_19_and_20](configuration_saved_between_19_and_20.png)

Press down until you get to **Exit from Minicom**

![exit_from_minicom_20](exit_from_minicom_20.png)

Press **Enter**

11\. Set up the board

Plug the SD card in

Push it in:

![plug_in_sd_card_21](plug_in_sd_card_21.jpg)

...till it clicks

![sd_card_fully_plugged_in_22](sd_card_fully_plugged_in_22.jpg)

Set SW16 to boot from the SD card:

![set_sw16_to_sd_card_boot_23](set_sw16_to_sd_card_boot_23.jpg)

Plug in the USB UART:

![plug_in_usb_uart_24](plug_in_usb_uart_24.jpg)

![usb_cable_plugged_in_25](usb_cable_plugged_in_25.jpg)

12\. If you're running this in a virtual machine, managed by VirtualBox, then capture the USB UART in VirtualBox by (A) clicking **Devices**, (B) clicking **USB** and (C) clicking **Silicon Labs CP2103 USB to UART Bridge Controller \[0100\]**

![click_usb_to_uart_for_26](click_usb_to_uart_for_26.png)

13\. Run minicom by typing **minicom** in a terminal

Note: exit minicom by typing **Control-a x**

You should see

![minicom_27](minicom_27.png)

14\. Power on the ZC702

![power_on_zc702_28](power_on_zc702_28.jpg)

![zc702_powered_on_29](zc702_powered_on_29.jpg)

You should see output in the minicom terminal end with:

![output_in_minicom_terminal_30](output_in_minicom_terminal_30.png)

Full output is \[[<u><span>here</span></u>](https://docs.google.com/document/d/1vJCOU3q8UvSZXjPg3RFywyreXuI8b9xTKY-l-nl1Qoo/edit?usp=sharing)\].

15\. Type **/mnt/lab1.elf**

You should see the :

![test_passed_31](test_passed_31.png)

Congratulations! You completed Lab 1 of the SDSoC tutorial on the ZC702.

Share this post if you feel like it would benefit others!

**<u><span>Reference</span></u>**

SDSoC Environment Tutorial: Introduction - Lab 1: Introduction to the SDSoC Development Environment at \[[<u><span>link</span></u>](https://github.com/Xilinx/SDSoC-Tutorials/blob/master/getting-started-tutorial/lab-1-introduction-to-the-sdsoc-development-environment.md)\]