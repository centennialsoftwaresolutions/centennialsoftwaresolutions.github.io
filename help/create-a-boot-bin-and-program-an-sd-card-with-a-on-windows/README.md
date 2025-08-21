# Create a BOOT.bin, Program an SD Card and Boot a ZC706 using Windows 7

![xilinx_logo_1](xilinx_logo_1.png)

This post shows you how to create a BOOT.bin with a Hello World bare-metal application and a bitstream created in \[[<u><span>Run Hello World on a ZC702</span></u>](https://www.centennialsoftwaresolutions.com/blog/run-hello-world-on-a-zc702)\], how to program the BOOT.bin onto the SD Card using Windows (copy it to the SD card) and how to boot the ZC702 from the SD card and see output from the serial port.

**<u><span>Before you Start</span></u>**

**_A. Generate bitstreams, Hello World Binaries and Test Everything_**

This post assumes you've generated the bitstreams, Hello World binaries and have tested everything as listed in \[[<u><span>Run Hello World on a ZC702</span></u>](https://www.centennialsoftwaresolutions.com/blog/run-hello-world-on-a-zc702)\], but on the on the ZC706. All of the instructions are the same except 2 things:

1\. You select the **ZC706** board instead of the ZC702

2\. You need to connect the UART-to-USB and JTAG-to-USB cables to:

![board_cable_ports_2](board_cable_ports_2.jpg)

**_B. Get a License_**

The ZC706 has a XC7Z045-2FFG900 C SoC. This chip is not support in WebPACK ( see \[[<u><span>link</span></u>](https://www.xilinx.com/products/design-tools/vivado/vivado-webpack.html#architecture)\]) like the chip on the ZC702. You can get a 30-day license at \[[<u><span>link</span></u>](https://www.xilinx.com/support/licensing_solution_center.html)\].

**<u><span>Versions Used</span></u>**

-   2018.2 Vivado and SDK
    
-   Windows 7 SP1
    
-   Rufus 3.5 @ \[[<u><span>link</span></u>](https://github.com/pbatard/rufus/releases/download/v3.5/rufus-3.5.exe)\]
    

**<u><span>Create Boot Image</span></u>**

The following picks up after the last step listed in [[Run Hello World on a ZC702](https://www.centennialsoftwaresolutions.com/blog/run-hello-world-on-a-zc702)]

Step 1: Create the first stage boot loader (FSBL) that will load the bitstream and the helloworld.elf.

A. Click **File**

B. Click **New**

C. Click **Application Project**

![click_application_project_3](click_application_project_3.jpg)

D. Type **fsbl**

E. Ensure the rest of the fields match the picture and click **Next >**

![name_project_fsbl_4](name_project_fsbl_4.jpg)

F. Click **Zynq FSBL**

G. Click **Finish**

![click_zynq_fsbl_5](click_zynq_fsbl_5.jpg)

Step 2: Create the BOOT.bin

A. Select **fsbl**

![select_fsbl_6](select_fsbl_6.jpg)

B. Click **Xilinx**

C. Click **Create Boot Image**

![click_create_boot_image_7](click_create_boot_image_7.jpg)

D. Ensure that the picture below matches (your paths may be different) and click **Add**

![ensure_picture_matches_8](ensure_picture_matches_8.jpg)

E. Browse to **helloworld.elf** in C:\\zc706vivado\\helloworld\\helloworld.sdk\\helloworld\\Debug or similar and **select it**

F. Click **Open**

![browse_to_helloworld_elf_9](browse_to_helloworld_elf_9.jpg)

G. Ensure that this image matches yours (again paths may be a little different) and click **OK**

![ensure_image_matches_10](ensure_image_matches_10.jpg)

H. Click **Create Image**

![click_create_image_11](click_create_image_11.jpg)

I. You should see Build Finished (took ...ms)

J. ...and Bootgen command execution is done.

![build_finished_12](build_finished_12.jpg)

**<u><span>Prepare the SD Card and Copy the BOOT.bin</span></u>**

Step 1: Insert into a SD card reader/writer on your PC the SD card that came with the ZC706 (see \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/zc706-unboxing)\]) or find an 8 GB SanDisk class 4 card:

![sd_card_13](sd_card_13.jpg)

Step 2: Format the SD card

A. Right-click the **SD card**

B. Select **Format...**

![format_sd_card_14](format_sd_card_14.jpg)

C. Click **Start**

![start_formatting_15](start_formatting_15.jpg)

D. Click **OK**

![confirm_format_16](confirm_format_16.jpg)

E. Click **OK** again

![format_complete_17](format_complete_17.jpg)

F. Click **Close**

![close_format_18](close_format_18.jpg)

Step 3: Copy the BOOT.bin to the SD card

A. Browse to the **BOOT.bin**

B. Right-click on **BOOT.bin**

C. Select **Copy**

![](https://static.wixstatic.com/media/3b5532_78ef35fcd041450f9853b859f724b300~mv2.jpg/v1/fill/w_740,h_424,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/3b5532_78ef35fcd041450f9853b859f724b300~mv2.jpg)

D. Click the **SD card**

E. Right-click in the **empty area of the SD explorer**

F. Click **Paste**

![past_boot_to_sd_card_20](past_boot_to_sd_card_20.jpg)

G. You should see:

![boot_bin_in_sd_card_21](boot_bin_in_sd_card_21.jpg)

Step 4: Eject the SD card

A. Right-click on the **SD card**

B. Click **Eject**

![eject_sd_card_22](eject_sd_card_22.jpg)

Step 5: Make sure the ZC706 is off and plug the SD card into the ZC706

A. Off:

![zc706_off_23](zc706_off_23.jpg)

Step 6: Set the board to SD boot mode

![set_board_to_boot_24](set_board_to_boot_24.jpg)

Step 7: Ensure the UART connection is connected to the computer

A. Connect the Mini-B port of Mini-B to Type-A USB cable to the port marked "UART"

![connect_mini_b_to_usb_25](connect_mini_b_to_usb_25.png)

B. Connect the Type-A port of Mini-B to Type-A USB cable to the port marked "UART"

![connect_usb_to_computer_26](connect_usb_to_computer_26.png)

Step 8: Set up the terminal on the SDK

This was covered in [[Run Hello World on a ZC702](https://www.centennialsoftwaresolutions.com/blog/run-hello-world-on-a-zc702)]

Step 9: Power on the ZC706

A. Move the switch from:

![zc706_off_23](zc706_off_23.jpg)

B. To:

![turn_board_on_27](turn_board_on_27.jpg)

You should see **Hello World** on the console:

![hello_world_console_28](hello_world_console_28.jpg)

...and the DONE LED green which indicates that the FPGA was successfully programmed by the FSBL

![done_led_green_29](done_led_green_29.jpg)

**<u><span>References</span></u>**

-   Zynq-7000 All Programmable SoC ZC706 Evaluation Kit Getting Started Guide UG961 (v6.0.1) January 28, 2015 @ \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/boards_and_kits/zc706/2014_4/ug961-zc706-GSG.pdf)\]
    
-   ZC706 Evaluation Board for the Zynq-7000 XC7Z045 SoC User Guide UG954 (v1.7) July 1, 2018 @ \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/boards_and_kits/zc706/ug954-zc706-eval-board-xc7z045-ap-soc.pdf)\]
    
-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]