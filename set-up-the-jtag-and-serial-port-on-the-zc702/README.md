# Set up the JTAG and Serial Port on the ZC702

![xilinx_logo_1](xilinx_logo_1.png)

This post shows you how to connect the JTAG and serial port of the ZC702, where to get the USB-to-serial port driver and how to configure the SDK to see the serial port output.

**<u><span>Versions Used</span></u>**

-   SDK 2018.2
    
-   ZC702 Rev 1.1
    
-   Windows 7 SP1
    

**<u><span>Set up the ZC702</span></u>**

Step 1: Set SW16 to JTAG mode [[mode documentation](https://www.xilinx.com/support/documentation/boards_and_kits/zc702_zvik/ug850-zc702-eval-bd.pdf) see p.16]

![set_sw16_to_jtag_2](set_sw16_to_jtag_2.png)

For the rest of the jumpers see the high-resolution photo of the board in the correct state at \[[<u><span>link</span></u>](https://photos.app.goo.gl/DddmM8T5QkTXwA7u5)\].

<u><span>Step 2</span></u>: Connect a **Micro-B to Type-A** (host connection) USB cable from U23 (Diglent USB JTAG interface) to the host PC

U23:

![u23_3](u23_3.png)

Micro-B connector:

![micro_b_connector_4](micro_b_connector_4.png)

Type-A connector:

![type_a_connector_5](type_a_connector_5.png)

<u><span>Step 3</span></u>: Connect a **Mini-B to Type-A** (host connection) USB cable from J17 (CP2103GM USB-to\_UART Bridge) to the host PC.

J17:

![j17_6](j17_6.png)

Mini-B connector:

![mini_b_connector_7](mini_b_connector_7.png)

Type-A connector:

![type_a_connector_8](type_a_connector_8.png)

**<u><span>Part II: Set up the Terminal</span></u>**

<u><span>Step 1</span></u>: Install the Silicon Labs CP210x USB to UART Bridge VCP Drivers

A. Goto [[link](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)]

B. Download and unzip the correct installer

C. Install the driver (I did not need to restart on Windows 7 SP1)

D. Click Windows

E. Click Devices and Printers

![devices_and_printers_9](devices_and_printers_9.png)

F. You should see Silicon Labs CP210x USB to UART Bridge

G. Note the COM port (you'll need this later)

![note_com_port_10](note_com_port_10.png)

<u><span>Step 2</span></u>:

A. Click **Window**

B. Click **Show View**

C. Click **Other**

![window_other_11](window_other_11.png)

<u><span>Step 3</span></u>:

A. Expand **Terminal**

B. Click **Terminal**

C. Click **OK**

![click_terminal_12](click_terminal_12.png)

Step 4: Click **Settings**

![click_settings_13](click_settings_13.png)

<u><span>Step 5</span></u>:

A. Use the COM port listed in Devices and Printers

B. Click OK

![use_com_port_14](use_com_port_14.png)

Step 6: Turn on the board

![turn_on_board_15](turn_on_board_15.png)

**<u><span>Part III: Switch Between Run and Debug View, Set Up Debug View</span></u>**

<u><span>Step 1</span></u>: Click to disconnect Run terminal (if you're connected in Run mode)

![click_disconnect_16](click_disconnect_16.png)

<u><span>Step 2</span></u>: Enter Debugging in the SDK

<u><span>Step 3</span></u>: Connect the serial port

A. Click **SDK Terminal**

B. Click the **'+'** (Connect to serial port.)

![connect_to_serial_port_17](connect_to_serial_port_17.png)

C. Use these settings and click **OK**

![use_settings_18](use_settings_18.png)

**<u><span>References</span></u>**

-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]