# Install 64bit Ubuntu 16.04.3 on a VirtualBox 5.2.12 Managed Virtual Machine Running on Windows 7 SP1

![ubuntu_logo_1](ubuntu_logo_1.png)

This post shows you how to install 64-bit Ubuntu 16.04.3 on a VirtualBox 5.2.12 managed virtual machine running on Windows 7 SP1.

Click \[[<u><span>here</span></u>](https://www.centennialsoftwaresolutions.com/blog/download-and-install-virtualbox-5-2-12-and-the-virtualbox-extension-pack-on-windows-7-pro-sp1)\] if you need to know how to download VirtualBox 5.2.12 and install it on Windows 7 SP1.

**<u><span>Create the Virtual Machine</span></u>**

**1.** Create a folder called **isos** in **C:\\**

If you need help creating a folder on Windows 7 SP1 click \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/create-a-folder-in-c-in-windows-7-sp1)\] for instructions.

**2.** Download Ubuntu 16.04.3 (filename: ubuntu-16.04.3-desktop-amd64.iso, size 1.47 GB) at \[[<u><span>link</span></u>](http://old-releases.ubuntu.com/releases/16.04.3/ubuntu-16.04.3-desktop-amd64.iso)\] to **C:\\isos**

**3.** Run VirtualBox

![run_virtualbox_2](run_virtualbox_2.png)

A) Click the Windows icon

B) Type **VirtualBox**

C) Click **Oracle VM VirtualBox**

**4.** Click **New**

![click_new_3](click_new_3.png)

**5.** Set **Name and operating system**

![set_name_and_operating_system_4](set_name_and_operating_system_4.png)

A) Set **Name:** to **myproject-ubuntu-16.04.3-desktop-amd64-5GB-RAM-100GB-Disk**

B) Set **Type:** to **Linux**

C) Set **Version: to Ubuntu (64-bit)**

**Note:** if you don't see **Ubuntu (64-bit)** you may need to enable virtualization technology in your BIOS, click \[[<u><span>here</span></u>](http://www.zachpfeffer.com/single-post/2017/02/15/Installing-the-64-bit-PC-AMD64-desktop-image-of-Ubuntu-16041-LTS-Xenial-Xerus-in-Oracle-VM-VirtualBox-5114-running-in-Windows-7-Professional-Service-Pack-1-CurrentBuild-7601-on-a-ThinkPad-T460-model-20FNCTO1WW-with-an-IntelR-CoreTM-i7-6600U-CPU)\] for instructions on a T460 that may help you enable this in the BIOS of your computer.

D) Click **Next**

**6.** Set Memory size to **5120 MB** by (A) typing **5120** into the **MB field** and (B) clicking **Next**

![set_memory_size_5](set_memory_size_5.png)

**7.** (A) Leave **Create a virtual hard disk now** selected and (B) click **Create**

![select_create_virtual_hard_disk_now_6](select_create_virtual_hard_disk_now_6.png)

**8.** (A) Select **VMDK (Virtual Machine Disk)** and (B) click **Next**

![select_virtual_machine_disk_7](select_virtual_machine_disk_7.png)

**Note:** VMDK files can be used on other virtual machines and products: VMware, Parallels Desktop, Sun xVM, QEMU, SUSE Studio, Norton GHOST and ILookIX and the .NET DiscUtils Open Source C# library.

**9.** (A) Leave **Dynamically allocated** selected and (B) click **Next**

![dynamically_allocated_selected_8](dynamically_allocated_selected_8.png)

**10.** (A) Set the size of the disk to **100 GB** (it won't use 100 GB right away because the disk grows dynamically) and (B) click **Create**

![set_disk_size_to_100_gigs_9](set_disk_size_to_100_gigs_9.png)

**<u><span>Install Ubuntu on the Virtual Machine</span></u>**

**1.** Open the virtual machine's settings window

![open_virtual_machine_settings_window_10_and_between_33_and_34](open_virtual_machine_settings_window_10_and_between_33_and_34.png)

A) Select **myproject-ubuntu-16.04.3-desktop-amd64-5GB-RAM-100GB-Disk**

B) Right-click on **myproject-ubuntu-16.04.3-desktop-amd64-5GB-RAM-100GB-Disk**

C) Select **Settings...**

**2.** Tell the virtual machine where the Ubuntu ISO is

![tell_vm_where_ubuntu_iso_is_11](tell_vm_where_ubuntu_iso_is_11.png)

A) Select **Storage**

B) Click **Empty**

C) Click on the disc drop down

D) Select **Choose Virtual Optical Disk File...**

**3.** Find the Ubuntu ISO

![find_ubuntu_iso_12](find_ubuntu_iso_12.png)

A) Select **C:\\**

B) Double-click **isos**

**4.** Select the ISO

![select_iso_13](select_iso_13.png)

A) Select the **ubuntu-16.04.3-desktop-amd64.iso** file

B) Click **Open**

**5.** Check the settings and click OK

![check_settings_14](check_settings_14.png)

A) Check under **Controller: IDE**

B) Check the **Location**

C) Click **OK**

**6.** With **myproject-ubuntu-16.04.3-desktop-amd64-5GB-RAM-100GB-Disk** Click **Start**

![start_virtual_machine_15_and_between_35_and_36](start_virtual_machine_15_and_between_35_and_36.png)

**Possible Error**

If you see this error (click the triangle to expand the error message):

![unable_to_allocate_and_lock_memory_error_16](unable_to_allocate_and_lock_memory_error_16.png)

Close some other programs to free up at least 5 GB of memory.

To check how much memory you have free

A) Press Control-Alt-Delete

B) Click **Start Task Manager**

![start_task_manager_17](start_task_manager_17.jpg)

Check available memory by (A) making sure **Available** memory is over 5 GB

![ensure_available_memory_above_5_gigs_18](ensure_available_memory_above_5_gigs_18.png)

Close the Task Manage by (B) selecting **File** and clicking Exit **Task Manager**

To "clear" the error and try again (A) click File then (B) click **Close...** then

![select_close_19](select_close_19.png)

(A) select **Power off the machine** and (B) click **OK**

![select_power_off_the_machine_20](select_power_off_the_machine_20.png)

**7.** Start the install

![start_install_21](start_install_21.png)

A) Close the Auto capture keyboard notification

B) Close the mouse pointer integration

C) Click Install Ubuntu

**8.** Click **Continue** on the **Preparing to install Ubuntu screen**

![continue_preparing_to_install_ubuntu_22](continue_preparing_to_install_ubuntu_22.png)

**9.** (A) Leave **Erase disk and install** Ubuntu selected and (B) click **Install Now**

![erase_disk_and_install_23](erase_disk_and_install_23.png)

**10.** Click **Continue on the Write the changes to disks?** prompt

![write_the_changes_to_disk_24](write_the_changes_to_disk_24.png)

**11.** (A) Type where you're from and (B) click **Continue**

![type_where_your_from_25](type_where_your_from_25.png)

**12.** Specify the Keyboard layout

![specify_keyboard_loadout_26](specify_keyboard_loadout_26.png)

A) Click, hold and grab the window to increase the size

B) Select your keyboard layout

C) Select your language

D) Click **Continue**

**13.** Fill in the **Who are you?** screen

![fill_in_credentials_27](fill_in_credentials_27.png)

A) Fill in **You name** with your name

B) Fill in **Your computer's name** with the name of the computer

C) Fill in **Pick a username** with a username you'd like to use

D) Enter a password in the **Choose a password** field

E) Enter the same password in the **Confirm your password** field

F) Ensure **Require my password to log in** is selected

G) Click **Continue**

**14.** Wait and monitor the install screens

A screen:

![welcome_to_ubuntu_screen_28](welcome_to_ubuntu_screen_28.png)

Another screen:

![find_even_more_software_29](find_even_more_software_29.png)

**15.** Click **Restart Now**

![restart_now_30](restart_now_30.png)

**16.** Press ENTER

![press_enter_31](press_enter_31.png)

**17.** Let the machine boot reboot to the first screen and select power off

![select_power_off_32](select_power_off_32.png)

A) Click **File**

B) Click **Close...**

**18.** Power off

![power_off_33](power_off_33.png)

A) Select **Power off the machine**

B) Select **OK**

**<u><span>Remove the ISO and Start the Virtual Machine</span></u>**

**1.** Open the virtual machine's settings window

![open_virtual_machine_settings_window_10_and_between_33_and_34](open_virtual_machine_settings_window_10_and_between_33_and_34.png)

A) Select **myproject-ubuntu-16.04.3-desktop-amd64-5GB-RAM-100GB-Disk**

B) Right-click on **myproject-ubuntu-16.04.3-desktop-amd64-5GB-RAM-100GB-Disk**

C) Select **Settings...**

**2.** Remove the disk

![remove_the_disk_34](remove_the_disk_34.png)

A) Select **Storage**

B) Select **ubuntu-16.04.3-desktop-amd64**

C) Click the CD icon drop down

D) Click **Remove Disk from Virtual Drive**

**3.** Click **OK**

![remove_disk_from_virtual_drive_35](remove_disk_from_virtual_drive_35.png)

**4.** With **myproject-ubuntu-16.04.3-desktop-amd64-5GB-RAM-100GB-Disk** Click **Start**

![start_virtual_machine_15_and_between_35_and_36](start_virtual_machine_15_and_between_35_and_36.png)

You should see:

![login_screen_36](login_screen_36.png)

**5.** Enter your password and press **ENTER**

After about 30 sec's you should see:

![ubuntu_home_screen_37](ubuntu_home_screen_37.png)

Congratulations! You've installed 64-bit Ubuntu 16.04.3 on a VirtualBox 5.2.12 managed virtual machine running on Windows 7 SP1.

**<u><span>Share and Like</span></u>**

**Share** and **like** this if you think other people would find it useful!

**<u><span>References</span></u>**

-   **VMDK** on **Wikipedia** at \[[<u><span>link</span></u>](https://en.wikipedia.org/wiki/VMDK)\]
    
-   Ubuntu logo from \[[<u><span>link</span></u>](https://assets.ubuntu.com/v1/57a889f6-ubuntu-logo112.png)\]