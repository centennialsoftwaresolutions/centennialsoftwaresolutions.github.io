# SD Card Access from Ubuntu 16.04.3 on VirtualBox on Windows 7

![oracle_virtualbox_logo_1](oracle_virtualbox_logo_1.png)

This post shows how to access an SD card via a USB reader from Ubuntu 16.04.3 running in a virtual machine hosted by VirtualBox version 5.2.12 r122591 (Qt5.6.2) running on Windows 7 SP1. It also covers accessing the SD card from a terminal, ejecting the card and unmounting the SD card reader.

**<u><span>Prerequisites</span></u>**

-   Install VirtualBox on Windows \[[<u><span>instructions</span></u>](http://www.zachpfeffer.com/single-post/2017/02/15/Installing-the-64-bit-PC-AMD64-desktop-image-of-Ubuntu-16041-LTS-Xenial-Xerus-in-Oracle-VM-VirtualBox-5114-running-in-Windows-7-Professional-Service-Pack-1-CurrentBuild-7601-on-a-ThinkPad-T460-model-20FNCTO1WW-with-an-IntelR-CoreTM-i7-6600U-CPU)\] (closely matches versions)
    
-   A USB SD card reader, like an IOGEAR GUH287 at \[[<u><span>link</span></u>](https://www.amazon.com/IOGEAR-USB-Card-Reader-GUH287/dp/B00330OVIG)\]
    
-   Ubuntu is running in the virtual machine
    

![sd_card_reader_top_2](sd_card_reader_top_2.jpg)

![sd_card_reader_bottom_3](sd_card_reader_bottom_3.jpg)

**<u><span>Install the SD Card Reader and the SD Card</span></u>**

1\. In the VirtualBox window running Ubuntu (A) click **Devices**, (B) click **USB** and note the devices.

![usb_settings_virtualbox_4](usb_settings_virtualbox_4.jpg)

2\. Plug the SD card reader into the computer

![plug_sd_card_reader_into_computer_5](plug_sd_card_reader_into_computer_5.jpg)

3\. In the VirtualBox window running Ubuntu (A) click **Devices**, (B) click **USB** and (C) click **Genesys USB Reader** or whatever new device came up. This captures the USB card reader. You'll **hear** Windows eject the device (with a da dum) and then **hear** Windows enumerate the VirtualBox driver (da da!) if this is the first time you've plugged this device in.

![new_usb_device_6](new_usb_device_6.png)

You should see a **checkmark** next to the reader after (A) clicking **Devices** and (B) clicking **USB**:

![device_checkmark_7](device_checkmark_7.jpg)

4\. Insert an SD card into the reader.

![sd_card_inserted_8](sd_card_inserted_8.jpg)

5\. A window will pop up if the SD card has been formatted so that Ubuntu can read it. Note the name of the window.

![sd_card_window_9](sd_card_window_9.png)

**<u><span>Access the SD Card from a Terminal</span></u>**

1\. (A) Right-click on the Ubuntu desktop and (B) click **<u><span>Open Terminal</span></u>**

![open_terminal_10](open_terminal_10.png)

2\. In the terminal type **ls /media/pfefferz/C002-DEEF/**

![access_sd_card_through_console_11](access_sd_card_through_console_11.png)

Now you can dd, cp, etc...

**<u><span>Eject the SD Card</span></u>**

Click here to eject the SD card:

![eject_sd_card_12](eject_sd_card_12.png)

**<u><span>Unmount the SD Card Reader</span></u>**

To unmount the SD card reader (A) click **Devices**, (B) **USB** and (C) **Genesys USB Reader \[9744\]**.

![unmount_sd_card_reader_13](unmount_sd_card_reader_13.png)

**<u><span>Reference</span></u>**

VirtualBox logo from \[[<u><span>link</span></u>](https://linux.systeminside.net/como-instalar-y-configurar-virtualbox/)\]