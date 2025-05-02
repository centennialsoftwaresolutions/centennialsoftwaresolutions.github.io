# Install VirtualBox Extension Pack to enable USB2.0 and USB3.0 in Guest O/S.



## 1\. Prerequisites

This post assumes that Virtual Box is already installed on a Windows 10 PC. My version is 6.1.

This post shows how to solve the following problems: You can't select anything other than USB1.1, selecting anything other than USB1.1 shows and error at the bottom of the screen, or the USB2 and USB3 options don't appear in the menu at all.

![usb_selection_screen_error_1](usb_selection_screen_error_1.png)

and the Guest O/S only sees a 1.1 controller:

![1.1_controller_2](1.1_controller_2.png)

You need to download the Oracle VM VirtualBox Extension Pack. Follow this link.

[Downloads – Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads)

On that page select the **All supported platforms** link in the section about the Extension Pack.

![vmware_download_page_3](vmware_download_page_3.png)

## 2\. Run the Extension Pack

Once you have completed the download you can either navigate to the download and launch it with Windows Explorer (and skip to section 3 below), OR navigate to File->Preferences and click on **Preferences...** (or just press Ctrl-G).

![click_preferences_4](click_preferences_4.png)

This will open the VirtualBox - Preferences window. In that window select **Extensions** from the menu on the left, then click on the **ADD** button on the right.

![add_extensions_5](add_extensions_5.png)

This will open the file navigator. Navigate to and select the Extensions pack that you just downloaded. Click **Open**.

![open_extensions_pack_6](open_extensions_pack_6.png)

## 3\. Extension Pack Wizard

In the popup VirtualBox - Question: Click **Install**.

![install_pack_7](install_pack_7.png)

This will switch to Windows UAC. (Which I can't get a good screen shot for). Click on OK in the UAC.

Then in the VirtualBox - Information window Click **OK**.

![confirm_installation_8](confirm_installation_8.png)

## 4\. Final

You can configure you guest to USB3.

![configure_guest_usb3_9](configure_guest_usb3_9.png)

Your Guest O/S should now see the USB2 and USB3 controllers.

![guest_sees_usb2_and_3_10](guest_sees_usb2_and_3_10.png)