# Add a disk to an Ubuntu VirtualBox VM

![oracle_virtualbox_logo_1](oracle_virtualbox_logo_1.png)

This post shows you how to add a new SATA disk to a Oracle VirtualBox Version 5.1.30 r118389 (Qt5.6.2) VM and install it in Ubuntu 16.04.2.

**Steps**

Create Disk File

1\. Right-click on the VM you'd like to add a disk to:

![right_click_vm_to_add_disk_2](right_click_vm_to_add_disk_2.png)

2\. Click **Settings...**

![click_settings_3](click_settings_3.png)

3\. Click **Storage**

![click_storage_4](click_storage_4.png)

4\. (1) Click on **Controller: SATA** and (2) click on the the **'+' disk icon**

![controller_sata_add_disk_5](controller_sata_add_disk_5.png)

5\. Click **Create new disk**

![create_new_disk_6](create_new_disk_6.png)

6\. Select **VMDK (Virtual Machine Disk)**

![select_virtual_machine_disk_7](select_virtual_machine_disk_7.png)

**VMDK** description below.

7\. (1) Click on **Dynamically allocated** and (2) click **Next**

![click_dynamically_allocated_8](click_dynamically_allocated_8.png)

8\. (1) Name the disk, (2) Select a size and (2) click **Create**

![name_disk_and_select_size_9](name_disk_and_select_size_9.png)

9\. Click OK

![click_ok_10](click_ok_10.png)

10\. Note the SATA Port the disk is on:

![note_sata_port_disk_is_on_11](note_sata_port_disk_is_on_11.png)

11\. Click **Start** to start the VM

![click_start_to_start_vm_12](click_start_to_start_vm_12.png)

Partition

12\. In Ubuntu, (1) right click on the desktop and (2) click **Open Terminal**

![click_open_terminal_13](click_open_terminal_13.png)

13\. Type

```
dmesg | grep sd
```

Look for the **sd** that matches the size of the disk you created; its **sdc** here:

![look_for_sd_that_matches_size_14](look_for_sd_that_matches_size_14.png)

14\. Install gparted. At the command line type:

```
sudo apt-get install gparted
```

Type 'Y' when prompted.

Note: this command is safe to run if its already installed. If its installed you'll see:

![command_safe_to_run_if_installed_15](command_safe_to_run_if_installed_15.png)

15\. Install gksu. At the command line type:

```
sudo apt install gksu
```

If you need to install it, type 'Y' when prompted.

You'll see something similar to:

![installing_gksu_command_line_16](installing_gksu_command_line_16.png)

16\. At the command line type this to start GParted:

```
gksudo gparted
```

17\. (1) Enter your sudo password and (2) click OK

![enter_sudo_password_17](enter_sudo_password_17.png)

18\. Click the **/dev/sda** drop down

![click_dev_sda_drop_down_18](click_dev_sda_drop_down_18.png)

19\. Click what you saw in dmesg (sdc here)

![click_what_was_in_dmesg_19](click_what_was_in_dmesg_19.png)

20\. (1) Click **Device** and (2) **Create Partition Table...**

![create_partition_table_20](create_partition_table_20.png)

21\. (1) Leave as msdos and (2) click Apply

![leave_as_msdos_21](leave_as_msdos_21.png)

22\. Click the Create a new partition in the selected unallocated space **'+' file icon**

![create_a_new_partition_22](create_a_new_partition_22.png)

23\. Leave everything as is and click **Add**

![leave_as_is_and_click_add_23](leave_as_is_and_click_add_23.png)

24\. Click the **Apply All Operations** green checkbox

![apply_all_operations_24](apply_all_operations_24.png)

25\. Click **Apply** again

![click_apply_again_25](click_apply_again_25.png)

You should see **All operations successfully completed**

![all_operations_successfully_completed_26](all_operations_successfully_completed_26.png)

26\. Click **Close**

![click_close_27](click_close_27.png)

27\. Quit GParted: (1) Select **GParted** and click (2) **Quit**

![quit_gparted_28](quit_gparted_28.png)

Mounting

28\. Create a mount point

At the command line type:

```
sudo mkdir /hdd2
```

At the command line type:

```
gksu gedit /etc/fstab
```

30\. (1) Enter your sudo password and (2) click OK:

![enter_sudo_password_29](enter_sudo_password_29.png)

31\. Enter this as the last line:

```
/dev/sdc1    /hdd2    ext4    defaults    0    0
```

It should look similar to:

![add_new_line_30](add_new_line_30.png)

32\. Click Save

![click_save_31](click_save_31.png)

33\. Click the 'x' to close

![click_save_32](click_save_32.png)

34\. Mount now

At the command line type:

```
sudo mount -a
```

35\. Change the user so you can read/write:

At the command line type:

```
sudo chown -R pfefferz:pfefferz /hdd2
```

36\. Test it

At the command line type:

```
touch /hdd2/test.txt
```

Then at the command line type:

```
ls /hdd2
```

![test_virtual_drive_33](test_virtual_drive_33.png)

Test Mount at Boot

37\. Reboot: (1) click the **gear** and (2) click **Shut Down...**

![click_shut_down_34](click_shut_down_34.png)

38\. Click the reboot button:

![click_reboot_button_35](click_reboot_button_35.png)

39\. After rebooting, test it

At the command line type:

```
touch /hdd2/test-after-reboot.txt
```

Then at the command line type:

```
ls /hdd2
```

You should see your test.txt:

![test_txt_36](test_txt_36.png)

**References**

-   The VirtualBox logo is from [https://www.virtualbox.org/](http://www.virtualbox.org/)
    
-   "5.2. Disk image files (**VDI**, **VMDK**, **VHD**, **HDD**)" @ [link](http://www.virtualbox.org/manual/ch05.html)
    
-   InstallingANewHardDrive from Ubuntu @ [link](http://help.ubuntu.com/community/InstallingANewHardDrive)
    

**Supporting Excerpts**

From Ch5 of the VirtualBox online manual:

_VirtualBox supports four variants of disk image files:_

-   _Normally, VirtualBox uses its own container format for guest hard disks -- Virtual Disk Image (_**_VDI_**_) files. In particular, this format will be used when you create a new virtual machine with a new disk._
    
-   _VirtualBox also fully supports the popular and open_ **_VMDK_** _container format that is used by many other virtualization products, in particular, by VMware.\[26\]_
    
-   _VirtualBox also fully supports the_ **_VHD_** _format used by Microsoft._
    
-   _Image files of Parallels version 2 (_**_HDD_** _format) are also supported.\[27\] For lack of documentation of the format, newer formats (3 and 4) are not supported. You can however convert such image files to version 2 format using tools provided by Parallels._
    

_There are two options of how to create a disk image:_ **_fixed-size_** _or_ **_dynamically_** _allocated._

-   _If you create a_ **_fixed-size_** _image, an image file will be created on your host system which has roughly the same size as the virtual disk's capacity. So, for a 10G disk, you will have a 10G file. Note that the creation of a fixed-size image can take a long time depending on the size of the image and the write performance of your hard disk._
    
-   _For more flexible storage management, use a_ **_dynamically_** _allocated image. This will initially be very small and not occupy any space for unused virtual disk sectors, but will grow every time a disk sector is written to for the first time, until the drive reaches the maximum capacity chosen when the drive was created. While this format takes less space initially, the fact that VirtualBox needs to expand the image file consumes additional computing resources, so until the disk file size has stabilized, write operations may be slower than with fixed size disks. However, after a time the rate of growth will slow and the average penalty for write operations will be negligible._