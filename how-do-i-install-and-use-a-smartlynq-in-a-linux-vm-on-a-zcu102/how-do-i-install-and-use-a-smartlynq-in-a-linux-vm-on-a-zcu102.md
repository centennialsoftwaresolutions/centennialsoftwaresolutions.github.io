# How do I install and use a SmartLynq in a Linux VM on a ZCU102?

![xilinx_logo_1](xilinx_logo_1.png)

This post shows how to install and use a SmartLynq on a ZCU102 from Vivado 2019.1 running on a Ubuntu 16.04.5 VM managed by VMWare Workstation 14 Player running on Windows 10 Pro.

I also demonstrate that using a SmartLynq results in a 3x speed up over using the JTAG-to-USB device from Digilent.

**<u><span>Assumptions</span></u>**

You've install Vivado 2019.1 onto a Ubuntu 16.04.5 VM managed by VMWare Workstation 14 Player running on Windows 10 Pro

**<u><span>Steps</span></u>**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Connect the SmartLynq USB cable

![connect_smartlynq_usb_2](connect_smartlynq_usb_2.jpg)

You should see something like:

![smartlynq_display_3](smartlynq_display_3.jpg)

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Connect to the Xilinx Smart JTAG Cable

![connect_to_jtag_cable_4](connect_to_jtag_cable_4.png)

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Run Vivado

![run_vivado_5](run_vivado_5.png)

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): Click **Open Hardware Manager**

![open__hardware_manager_6](open__hardware_manager_6.png)

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): Click **Open target**

![open_target_7](open_target_7.png)

Step [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6): Click **Open New Target...**

![open_new_target_8](open_new_target_8.png)

Step [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7): Click **Next >**

![click_next_on_dialouge_box_9](click_next_on_dialouge_box_9.png)

Step [#8](https://www.centennialsoftwaresolutions.com/blog/hashtags/8): (A) Select **Remote server**, (B) use 10.0.0.2 as shown on the SmartLynq, and (C) click Next >

![set_server_settings_10](set_server_settings_10.png)

Step [#9](https://www.centennialsoftwaresolutions.com/blog/hashtags/9): Click OK to update if you see this

![confirm_cable_edit_11](confirm_cable_edit_11.png)

You should see:

![smartlynq_firmware_updating_12](smartlynq_firmware_updating_12.png)

...and:

![updating_smartlynq_firmware_13](updating_smartlynq_firmware_13.png)

...and on the SmartLynq:

![smartlynq_display_14](smartlynq_display_14.jpg)

Step [#10](https://www.centennialsoftwaresolutions.com/blog/hashtags/10): Connect the SmartLynq to the ZCU102

![connect_smartlynq_to_zcu102_15](connect_smartlynq_to_zcu102_15.jpg)

![zcu102_connection_to_smartlynq_16](zcu102_connection_to_smartlynq_16.jpg)

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11): Note the **Hardware server** address

![hardware_server_adress_17](hardware_server_adress_17.png)

Step [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12): (A) Select **60000000 (7 0's)** then you should be able to (B) **click Next >**

![set_jtag_clock_frequency_18](set_jtag_clock_frequency_18.png)

Step [#13](https://www.centennialsoftwaresolutions.com/blog/hashtags/13): Click **Finish**

![finish_hardware_target_setup_19](finish_hardware_target_setup_19.png)

You should see:

![hardware_target_loading_20](hardware_target_loading_20.png)

...and finally:

![target_setup_compleat_21](target_setup_compleat_21.png)

Step [#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14): Test using a PetaLinux ZCU102 load:

Step #: Install PetaLinux 2019.1

mkdir -p $HOME/petalinux

cd ~/Downloads

./petalinux-v2019.1-final-installer.run $HOME/petalinux/2019.1

Step #: Build the xilinx-zcu102-v2019.1-final.bsp

mkdir -p ~/plxprjs

cd ~/plxprjs

source ~/petalinux/2019.1/settings.sh

petalinux-create -t project -s ~/Downloads/xilinx-zcu102-v2019.1-final.bsp

cd xilinx-zcu102-2019.1/

petalinux-build

petalinux-boot --qemu --kernel

Step #: Load it

time petalinux-boot --jtag --kernel --hw\_server-url 10.0.0.2:3121

I got:

**real 0m51.708s**

user 0m3.221s

sys 0m4.290s

**<u><span>Test Using the JTAG-to-USB Connection</span></u>**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Disconnect the SmartLynq

![disconnect_smartlynq_22](disconnect_smartlynq_22.jpg)

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Connect the UART-to-USB and JTAG-to-USB

![connect_uart_and_jtag_cables_23](connect_uart_and_jtag_cables_23.jpg)

![connect_to_usb_hub_24](connect_to_usb_hub_24.jpg)

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Click OK

![confirm_devices_connected_25](confirm_devices_connected_25.png)

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): Select **Future Device Digilent USB Device**

![selected_future_device_digilent_usb_device_26](selected_future_device_digilent_usb_device_26.png)

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): Click **Open New Target...**

![open_new_target_27](open_new_target_27.png)

Step [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6) Click **Next >**

![next_on_hardwaare_target_28](next_on_hardwaare_target_28.png)

Step [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7): (1) Select **Local server** and (2) click **Next >**

![select_local_server_29](select_local_server_29.png)

You should see:

![successful_hardware_target_30](successful_hardware_target_30.png)

Step [#8](https://www.centennialsoftwaresolutions.com/blog/hashtags/8): Run:

**time petalinux-boot --jtag --kernel**

I see:

**real 3m15.098s**

user 0m2.742s

sys 0m1.524s

**<u><span>References</span></u>**

-   Used [<u><span>https://www.bricelam.net/ImageResizer/</span></u>](https://www.bricelam.net/ImageResizer/) to batch resize pictures
    
-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]