# Make Sure the ZC706 Hardware is Working

This post shows how to ensure the ZC706 hardware is working by running the Built-In Self-Test.

It follows UG961, the ZC706 Getting Started Guide, adding links and pictures to make it easier for others to "check-out" the board quickly.

**Hardware Needed**

All of these items are included in the ZC706 Kit.

-   ZC706 evaluation board with the Zynq-7000 XC7Z045 FFG900-2 AP SoC part
    
    ![zc706_board_top_1](zc706_board_top_1.jpg)
    
    ![zc706_bottom_right_corner_2](zc706_bottom_right_corner_2.jpg)
    
    ![zc706_top_right_corner_3](zc706_top_right_corner_3.jpg)
    
    ![zc706_top_left_corner_4](zc706_top_left_corner_4.jpg)
    
    ![zc706_bottom_left_corner_5](zc706_bottom_left_corner_5.jpg)
    
-   USB to Type-A to Mini-B cable (for UART)
    
    ![usb_cable_6](usb_cable_6.jpg)
    
    ![mini_b_cable_7](mini_b_cable_7.jpg)
    
    ![uart_port_8](uart_port_8.jpg)
    
-   Digilent JTAG USB Type-A to Micro-B cable
    

![digilent_jtag_usb_cable_9](digilent_jtag_usb_cable_9.jpg)

![jtag_cable_10](jtag_cable_10.jpg)

TODO: is there something special about this cable?

-   AC power adapter (12 VDC)
    

![ac_power_adaptor_port_11](ac_power_adaptor_port_11.jpg)

![wall_plug_12](wall_plug_12.jpg)

-   TeraTerm Pro terminal or alternative
    

TeraTerm is available at \[[<u><span>link</span></u>](https://osdn.net/projects/ttssh2/)\]. Version 4.99 was used in this post. Its available at \[[<u><span>link</span></u>](https://osdn.net/projects/ttssh2/downloads/69613/teraterm-4.99.exe/)\]. I selected the **Standard install**. This installed:

Destination location:

C:\\Program Files (x86)\\teraterm

Setup type:

Standard installation

Selected components:

Tera Term & Macro

TTSSH

CygTerm+

TTProxy

Additional Plugins

TTXResizeMenu (VT-Window size can be changed from preset)

TTXttyrec (ttyrec format record data can be recorded or playback)

Start Menu folder:

Tera Term

Additional tasks:

Create Tera Term shortcut to Desktop

Create Tera Term shortcut to Quick Launch

**Note**: When I tried to download Tera Term Pro from the link listed in the Getting Started Guide \[[<u><span>link</span></u>](http://www.ayera.com/teraterm/)\] from Ayera Technologies on July 4th 2018 (Version 3.1.3) I got the following error:

![ayera_webpage_error_13](ayera_webpage_error_13.png)

-   USB-UART drivers from Silicon Labs
    

More to come...

**Reference**

ZC706 Getting Started Guide, UG961 (v6.0.1) January 28, 2015 \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/boards_and_kits/zc706/2014_4/ug961-zc706-GSG.pdf)\]