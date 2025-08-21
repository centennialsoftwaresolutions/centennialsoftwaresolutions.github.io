# LoRaWAN - Connecting Your Device To The Things Network

![board_overveiw_1](board_overveiw_1.jpg)

This post shows how to connect a LoRaWAN device to The Things Network (TTN). It expands on the earlier post, [**LoRaWAN On ATSAMR34 Platform and External I2C EEPROM with Device EUI**](https://www.centennialsoftwaresolutions.com/post/lorawan-on-atsamr34-platform-and-external-i2c-eeprom-with-device-eui). 

## **<u><span>Introduction</span></u>**

The Things Network (TTN) provides a set of open tools and an open network to build your IoT application. Using the TTN we will demonstrate how to connect your LoRaWAN device to a global IoT network and send data.

We use our LoRaWAN device from the earlier post, [**LoRaWAN On ATSAMR34 Platform and External I2C EEPROM with Device EUI**](https://www.centennialsoftwaresolutions.com/post/lorawan-on-atsamr34-platform-and-external-i2c-eeprom-with-device-eui).  We also need a LoRaWAN gateway to forward the LoRa packets over the backhaul to the Internet and the TTN network.

![lorawan_flowchart_2](lorawan_flowchart_2.jpg)

The following steps are used to connect to the TTN.

**<u><span>Step 1:</span></u>** Create your TTN account.

**<u><span>Step 2:</span></u>** Register your Gateway on TTN.

**<u><span>Step 3:</span></u>** Add your Application.

**<u><span>Step 4:</span></u>** Register your Device.

**<u><span>Step 5:</span></u>** Join with Over The Air Authentication (OTAA).

**<u><span>Step 6:</span></u>** Send data from your device to your TTN application.

## **<u><span>Materials and Tools</span></u>**

This demonstration was created and run using the following OS environment, tools, and materials.  Please refer to the earlier post, [**LoRaWAN On ATSAMR34 Platform and External I2C EEPROM with Device EUI**](https://www.centennialsoftwaresolutions.com/post/lorawan-on-atsamr34-platform-and-external-i2c-eeprom-with-device-eui), for details on setting up your device for this example.

-   MultiTech Conduit MTCDT-L4N1-246A-915-US LoRaWAN / LTE Gateway

-   **<u><span>Materials/Tools from the earlier post [</span></u>**[**<u><span>link</span></u>**](https://www.centennialsoftwaresolutions.com/post/lorawan-on-atsamr34-platform-and-external-i2c-eeprom-with-device-eui)**<u><span>] are listed below:</span></u>**

    -   Windows 10 Pro, Version 10.0.19041 Build 19041SAM R34 Xplained Pro Evaluation Kit (DM32011) \[[link](https://www.microchip.com/DevelopmentTools/ProductDetails/dm320111)\] **Note:** This post does not require connection to The Things Network. However, you may be interested in testing the LoRaWAN capability of the board by following the kit’s Quick Start Guide \[[link](https://ww1.microchip.com/downloads/en/DeviceDoc/30010200A.pdf)\]
        
    -   Tera Term, Version 4.105 \[[link](https://osdn.net/projects/ttssh2/releases/)\]
        
    -   Microchip’s 24AA025E64 EEPROM, 8-pin SOIC \[[link](https://www.microchip.com/wwwproducts/en/24AA025E64)\]
        
    -   Spark Fun’s 8-Pin SOIC to DIP adapter. This tiny PCB adapter and instruction guidelines and materials to mount the 24AA025E64 to the adapter can be found here \[[link](https://learn.sparkfun.com/tutorials/8-pin-soic-to-dip-adapter-hookup-guide?_ga=2.150190390.1037117880.1606680306-2016783257.1598037336&_gac=1.115759476.1606680306.Cj0KCQiAqo3-BRDoARIsAE5vnaJQCsx0WossOA6U7ry-2oneJXFEFonztYYO1IqUNQw3VuF-Qk8nE3UaAhotEALw_wcB)\]
        
    -   Microchip Studio for AVR and SAM Devices, Version 7.0.2542 \[[link](https://www.microchip.com/mplab/microchip-studio)\]
        
    -   Atmel (Microchip) ASF, version 3.49.1 **Note:** The ASF is part of the Microchip Studio installation
        

## **<u><span>Step 1:</span></u>** Create Your TTN Account

A) Go to The Things Network homepage [https://www.thethingsnetwork.org/] and select SignUp from the menu options.

![create_ttn_account_3](create_ttn_account_3.jpg)

B) Enter your information to set up the account.

![account_set_up_4](account_set_up_4.jpg)

C) TTN will email you an account activation. Activate your account by clicking the Activate account button in the email.

![verify_account_5](verify_account_5.jpg)

D) Enter the TTN Console to proceed to the next step.

![enter_ttn_console_6](enter_ttn_console_6.jpg)

## **<u><span>Step 2:</span></u>** Register your Gateway

There are many choices and manufacturers for LoRaWAN Gateway hardware. A list of gateways can be found here \[[<u><span>link</span></u>](https://www.thethingsnetwork.org/docs/gateways/start/list.html)\]. We use a MultiTech Conduit gateway with a cellular backend as a Legacy Packet Forwarder with TTN configuration instructions here \[[<u><span>link</span></u>](https://www.thethingsnetwork.org/docs/gateways/multitech/)\]. Follow the manufacturer's instructions from your gateway’s manual to configure it to forward packets to TTN. The Things Network has configuration instructions here \[[<u><span>link</span></u>](http://www.thethingsnetwork.org/docs/gateways/registration.html)\].

A) Select the “Gateways” to register your gateway.

![select_gateways_7](select_gateways_7.jpg)

B) Provide your gateway’s information to register it on TTN. This demonstration configures the gateway as a legacy packet forwarder, so this checkbox is selected.

![gateway_information_8](gateway_information_8.jpg)

The TTN uses the gateway's Extended Unique Identifier (EUI) to register gateways that are operating as a legacy packet forwarder. This information can be accessed from your gateway's WebUI as shown below for our Multitech gateway.

![extended_unique_identifier_9](extended_unique_identifier_9.jpg)

## **<u><span>Step 3:</span></u>** Add your Application

The following steps will show how to hook your device's data packets to a TTN application that you register. _Note: A follow-up post will expand on building applications for the TTN._

![add_application_10](add_application_10.jpg)

B) Enter a unique Application ID and a Description for the application as shown below. Select the handler depending on your region. Finish by clicking the **_Add application_** button.

![application_information_11](application_information_11.jpg)

C) TTN Console registers your application and assigns it a unique Application EUI.

![registered_application_12](registered_application_12.jpg)

## **<u><span>Step 4</span></u>**: Register your device

A) Select the **_register device_** link to register your device. This enables your device to send data to your application.

![register_device_13](register_device_13.jpg)

B) The TTN provides the screen shown below to register our device.

![register_device_screen_14](register_device_screen_14.jpg)

Device registration requires the user to enter a unique device identifier of our choice and the Device EUI of our device. The Application EUI and Key of our TTN application are stored in the device.

C) Before filling in this information we return to our ATSAMR34 device used in the earlier post, [**<u><span>LoRaWAN On ATSAMR34 Platform and External I2C EEPROM with Device EUI</span></u>**](https://www.centennialsoftwaresolutions.com/post/lorawan-on-atsamr34-platform-and-external-i2c-eeprom-with-device-eui). Remember in this device application, the Device EUI from external EEPROM is displayed and the user is prompted to enter the Application (Join) EUI and Application Key.

Below is the Tera Term printout of the device. Here we see our Device EUI is **0004a30b000527fa**.

![find_device_eui_15](find_device_eui_15.jpg)

D) Copy the Device EUI to the TTN Device registration page along with a unique device identification, we’ll use **ttn\_demo\_01**. Finish by clicking the **Register** button.

![enter_device_eui_16](enter_device_eui_16.jpg)

TTN registers the device to this application and provides an Application Key that is unique between this TTN application and our device. This information will be added to the device in the next step.

![device_register_17](device_register_17.jpg)

## **<u><span>Step 5:</span></u>** Join with Over The Air Authentication (OTAA)

Now that our device is registered in our TTN application we can add the Application EUI and Key information to our device and proceed with joining via OTAA.

Note below that TTN has provided a convenient way to copy the EUI and Key to the clipboard by clicking the icon on the right.

![copy_eui_and_key_18](copy_eui_and_key_18.jpg)

A) Copy the App EUI and Key to your device at the Tera Term prompts as shown below.

![copy_eui_and_key_to_tera_term_19](copy_eui_and_key_to_tera_term_19.jpg)

B) Move to the Data tab on the TTN devices page. This page displays LoRaWAN activity from this registered device.

![go_to_data_tab_20](go_to_data_tab_20.jpg)

C) In our example, we’re using the NA915 Band, sub-band 2. _Select the appropriate frequency plan for your location \[_[_<u><span>link</span></u>_](https://www.thethingsnetwork.org/docs/lorawan/frequencies-by-country.html)_\]._ In Tera Term Select **4** for **Select Band.** We then select **2** for **NA915** then **2** for sub-band. The device will then send an OTAA Join request to the example application on TTN.

![send_otaa_join_rwquest_21](send_otaa_join_rwquest_21.jpg)

D) Note the successful join in the device's Tera Term terminal output (above), along with the Join packet displayed on the TTN’s registered device (below).

![successful_join_22](successful_join_22.jpg)

## **<u><span>Step 6:</span></u>** Send data from your device to your TTN application

After the device has successfully joined we can send LoRaWAN data packets to our TTN application.

A) Select **2** for **Send Data** in Tera Term. Repeat the selection to send more packets.

![select_send_data_23](select_send_data_23.jpg)

B) The data packets can be seen following the OTAA Join Request packet on TTN.

![data_packets_confirm_24](data_packets_confirm_24.jpg)

## **<u><span>Summary</span></u>**

In this post, we've shown how to use The Things Network for your IoT device testing. Using the ATSAMR34 device we created from the earlier post \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/post/lorawan-on-atsamr34-platform-and-external-i2c-eeprom-with-device-eui)\], we registered this device on TTN then demonstrated the OTAA join and successful transmission of LoRaWAN packets. A follow-up post will expand on building applications for the TTN.