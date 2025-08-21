# (LoRa) Guppy Care and Feeding

![lora_chart_1](lora_chart_1.png)

This post shows how work with the digital Matter Guppy geo-location tag for LoRaWAN™ IoT networks on a Multi-Tech MultiConnect® Conduit™ Access Point, model **MTCAP-915**, MachineQ LoRaWAN gateway. It doesn't list every step.

**<u><span>Prerequisites</span></u>**

To use a Guppy you must be able to setup and configure a LoRa gateway and setup and configure LoRa nodes (a.k.a. end-devices in the LoRaWAN 1.0.2 spec) on a LoRaWAN network.

See \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/machineq-gateway-setup)\] for setting up a Multi-Tech MultiConnect® Conduit™ Access Point model MTCAP-915 MachineQ LoRaWAN gateway.

See \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/install-and-uninstall-the-guppy-lorawan-configuration-tool)\] for installing the Guppy LoRaWAN Configuration Tool.

**<u><span>Configure the Guppy</span></u>**

1\. Connect the Guppy

2\. Starting with the default:

![default_config_tool_2](default_config_tool_2.jpg)

![default_config_tool_3](default_config_tool_3.jpg)

![default_config_tool_4](default_config_tool_4.jpg)

![default_config_tool_5](default_config_tool_5.jpg)

![default_config_tool_6](default_config_tool_6.jpg)

...use these settings:

Set **Region** to **US 915**

Set **Min Data Rate** to **15** and Max Data Rate to **15**

Set **Heartbeat Tx** to **10** min

Set **In Trip Tx** to **1** s

Set **Trip End Timeout** to **10** s (Update: Set this to 60 s)

Set **Wakeup Threshold** to **1**

Set **Wakeup Count** to **1**

Set **Disable Wake Filter** to **True**

Settings should look like this:

![new_config_settings_7](new_config_settings_7.jpg)

![new_config_settings_8](new_config_settings_8.jpg)

![new_config_settings_9](new_config_settings_9.jpg)

![new_config_settings_10](new_config_settings_10.jpg)

3\. Click the **Program Parameters** checkbox and click **Start**

![start_with_program_paremeters_11](start_with_program_paremeters_11.jpg)

You should see:

![programming_firmware_12](programming_firmware_12.jpg)

4\. After the status bar stops and you hear a bell (if your sound is up) click **Stop**

![stop_program_13](stop_program_13.jpg)

You should see your settings in the **Existing** column.

5\. Unplug the Guppy.

**<u><span>MachineQ Node Provisioning for the Guppy</span></u>**

Use the following info to select the correct device profile configuration template:

-   LoraWan specification version (Lorawan MAC layer): 1.0, 1.0.1 and 1.0.2)
    
-   Device Class: A, B or C
    
-   RF Region: FCC USA/ ETSI Europe
    
-   Device transmit power
    

For the Guppy this translates to **LoRaWAN 1.0.2**, Class **A**, RF Region **FCC** and transmit power **20 dBm**

Use this device profile: **LoRaWAN 1.0.2-class A-20dBm-FCC**

**Steps:**

1\. Sign into mQCentral at \[[<u><span>link</span></u>](https://mqcentral.machineq.net/)\]

![mqcentral_log_in_14](mqcentral_log_in_14.png)

![machineq_login_data_15](machineq_login_data_15.png)

2\. Click **Devices**

![click_devices_16](click_devices_16.jpg)

3\. Click **ADD A DEVICE**

![add_a_device_17](add_a_device_17.jpg)

4\. Fill in the following fields and click **SUBMIT**

Stars are per-device and found on the stickers included in the Guppy package

![fill_in_fields_18](fill_in_fields_18.jpg)

5\. Click **Details** (you may not see the device connected, you'll need to move it around a wait 10 seconds)

![click_details_19](click_details_19.jpg)

6\. Move the unit and wait 10 secs

7\. Refresh the mQCentral window

8\. Scroll down and you should see a stream:

![stream_of_data_20](stream_of_data_20.jpg)

9\. Expand one of the **Data** entries by clicking on the triangle beside the entry:

![expand_data_entries_21](expand_data_entries_21.jpg)

10\. Copy **PayloadHex**

![copy_payloadhex_22](copy_payloadhex_22.jpg)

11\. Paste into UplinkDecoder at \[[<u><span>link</span></u>](https://www.oemserver.com/tools/GuppyLoRaWAN/UplinkDecoder.html)\]

![past_payloadhex_into_uplinkdecoder_23](past_payloadhex_into_uplinkdecoder_23.jpg)

As you refresh the window, more messages will pop up if you move the unit.

To get additional data from the Guppy, set **Enable Tilt / Triggers** to **Enabled** in the Guppy LoRaWAN Configuration Tool 1.9:

![payloadhex_24](payloadhex_24.jpg)

Decoded:

![decoded_25](decoded_25.jpg)

The full list of messages is hosted at \[[<u><span>link</span></u>](https://support.digitalmatter.com/support/solutions/articles/16000066132-guppy-lorawan-integration)\] which links to the actual doc at \[[<u><span>link</span></u>](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/16024374732/original/Guppy%20LoRaWAN%20Integration%201.3.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJ2JSYZ7O3I4JO6DA%2F20190102%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20190102T065038Z&X-Amz-Expires=300&X-Amz-Signature=6f1fe969bc1d8086d2f9d3f975621aa65377ac7ce0980e94dda8574537aad53e&X-Amz-SignedHeaders=Host&response-content-type=application%2Fpdf)\].