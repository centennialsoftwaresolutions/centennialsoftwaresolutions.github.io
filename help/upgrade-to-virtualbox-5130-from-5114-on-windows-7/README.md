# Upgrade to VirtualBox 5.1.30 from 5.1.14 on Windows 7

![virtualbox_version_update_1](virtualbox_version_update_1.png)

Overview

This post gives step-by-step instructions for upgrading VirtualBox from 5.1.14 to 5.1.30.

Before starting

You may want t completely restart your Windows machine before attempting this.

Steps

1\. Click the link: http://download.virtualbox.org/virtualbox/5.1.30/VirtualBox-5.1.30-118389-Win.exe.

2\. Save the file to C:\\Users\\your\_username\\Documents\\Installers

3\. [Double-click](http://en.wikipedia.org/wiki/Double-click) it.

4\. Click **Run**

![run_virtualbox_update_2](run_virtualbox_update_2.png)

5\. Click **Run** again

![confirm_run_virtualbox_installer_3](confirm_run_virtualbox_installer_3.png)

6\. Click **Next**

![next_on_virtualbox_setup_4](next_on_virtualbox_setup_4.png)

7\. Click on the **VirtualBox Application** box and select **Entire feature will be installed on local hard drive** the click **Next**

![entire_feature_will_be_installed_on_local_hard_drive_5](entire_feature_will_be_installed_on_local_hard_drive_5.png)

8\. Click **Next** again

![click_next_on_custom_setup_6](click_next_on_custom_setup_6.png)

9\. The next step warns that the installation may reset the network device. Don't worry, the network reset will occur during install after you click **Yes** (and Install in the next step)

![warning_network_interfaces_7](warning_network_interfaces_7.png)

10\. Before clicking **Install**:

-   Save any work that relies on a network connection
    
-   Close VirtualBox if its still open
    

![install_virtualbox_update_8](install_virtualbox_update_8.png)

10.a If you didn't close VirtualBox you'll see a window that says that its still open. Close VirtualBox and click **Retry**.

![retry_install_9](retry_install_9.png)

10.b There may additional files still in use. The installer may list a few numbers. These are PIDs.

![files_in_use_10](files_in_use_10.png)

10.c To figure out what to close you can type Control-Alt-Delete. Click the **Processes** tab. Click **View** then click **Select Columns...**

![select_columns_11](select_columns_11.png)

10.d Select the PID (Process Identifier) checkbox

![process_identifier_check_12](process_identifier_check_12.png)

Back in Windows Task Manager, make sure the **Show processes from all users** checkbox is checked. find the numbers listed (1868, 5604, 7084 in the example above). You can click on the PID column to sort the numbers. For each number click **End Process**

If any PID is a SYSTEM PID you may get an Access is denied error

![access_is_denied_13](access_is_denied_13.png)

If you get this, stop the installation, reboot the computer and try again.

11\. Click Finish and open Oracle VM VirtualBox

Notes

Difference between 5.1.14 and 5.1.30 detailed at: [https://www.virtualbox.org/wiki/Changelog-5.1](http://www.virtualbox.org/wiki/Changelog-5.1).