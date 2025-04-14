# How to Permanently Mount an External Drive as a Folder on Windows 10

![Windows_10_logo_1](Windows_10_logo_1.png)

This post shows screenshots corresponding to the steps to permanently mount an external drive as a folder on Windows 10.

## Steps

\# **"Create an empty folder**. You need to create a new empty folder and store it on an NTFS or ReFS drive."

![Create_empty_folder_2](Create_empty_folder_2.png)

\# "In the search box on the taskbar, enter Computer Management..."

![Computer_manegement_3](Computer_manegement_3.png)

\# "...and select **Disk Management**."

![Disk_management_4](Disk_management_4.png)

On my [<u><span>system</span></u>](https://www.zachpfeffer.com/single-post/2020/08/24/new-lenovo-p52-thinkpad-system-information) I see **Connecting to Virtual Disk Service...** for 10's of seconds:

![Connecting_to_virtual_disk_service_5](Connecting_to_virtual_disk_service_5.png)

\# Plug in the external drive

\# Right-click on the drive and select **Change Drive Letter and Paths...**

![Change_drive_letter_and_paths_6](Change_drive_letter_and_paths_6.png)

\# Click **Add**

![Add_7](Add_7.png)

\# Click **Browse...**, click the empty folder (**Tools**), and click **OK**

![Browse_tools_ok_8](Browse_tools_ok_8.png)

...click OK again.

![Ok_again_9](Ok_again_9.png)

\# Browse to the directory and create Test Folder

![Create_test_folder_10](Create_test_folder_10.png)

## Testing Samsung Portable SSD T5 Eject and Reinsert

\# Close the explorer window to the folder, right-click on the **Eject** icon, and click on **Eject Portable SSD T5** (the name of your drive may be different).

![Eject_portable_SSD_T5_11](Eject_portable_SSD_T5_11.png)

I saw:

![Safe_to_remove_hardware_12](Safe_to_remove_hardware_12.png)

If I was browsing the drive I saw the following:

![Device_currently_in_use_13](Device_currently_in_use_13.png)

When I tried to click on the folder where the disk was mounted, I saw:

![Error_tools_unavalible_14](Error_tools_unavalible_14.png)

...plugging the external drive back in made it available.

If the drive was plugged in and I slept the computer, then I unplugged the drive, I caused the same "unavailable error."

If I was exploring the drive and then disconnected it, I saw the "unavailable error."

If the drive was disconnected, I slept the computer, reconnected it while the computer was asleep, and then woke the computer up, the drive was available.

## References

Mount a drive as a folder with Disk Management

https://learn.microsoft.com/en-us/windows-server/storage/disk-management/assign-a-mount-point-folder-path-to-a-drive 

Windows 10 Logo

[https://commons.wikimedia.org/wiki/File:Windows_logo_-_2012_%28dark_blue%29.svg](https://commons.wikimedia.org/wiki/File:Windows_logo_-_2012_(dark_blue).svg) 