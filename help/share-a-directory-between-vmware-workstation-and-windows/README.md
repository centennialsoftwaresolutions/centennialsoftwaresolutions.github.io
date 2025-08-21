# Share a Directory Between VMware Workstation and Windows

![vmware_workstation_logo_1](vmware_workstation_logo_1.png)

This post shows you how to share a directory between VMware Workstation and Windows.

**<u><span>Versions Used</span></u>**

-   VMware Workstation 15 Player
    
-   Windows 10 Professional
    

**<u><span>Steps</span></u>**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Click **Player > Manage > Virtual Machine Settings...**

![virtual_machine_settings_2](virtual_machine_settings_2.png)

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): 

A) Click the **Options** tab

B) Click **Shared Folders Disabled**

C) Click the **Enabled until next power off or suspend**

D) Click **Add...**

![disable_shared_folders_3](disable_shared_folders_3.png)

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Click **Next**

![add_shared_folder_wizard_4](add_shared_folder_wizard_4.png)

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4):

A) Click Browse

B) Browse to **This PC > Documents,** click **Make New Folder** and name it **shared**

C) Select **shared**

D) Click **OK**

![make_new_folder_5](make_new_folder_5.png)

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): Click **Next >**

![name_shared_folder_6](name_shared_folder_6.png)

Step [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6): 

A) Leave **Enable this share** checked

B) Click **Finish**

![enable_this_share_7](enable_this_share_7.png)

Step [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7): Click **OK**

![confirm_changes_8](confirm_changes_8.png)

**Step [#9](https://www.centennialsoftwaresolutions.com/blog/hashtags/9):** Look for **shared** on Linux at **/mnt/hgfs/**

**<u><span>References</span></u>**

From [https://docs.vmware.com](https://docs.vmware.com/): Enable a Shared Folder for a Virtual Machine @ [[link](https://docs.vmware.com/en/VMware-Workstation-Player-for-Windows/15.0/com.vmware.player.win.using.doc/GUID-D6D9A5FD-7F5F-4C95-AFAB-EDE9335F5562.html)]

From [https://en.wikipedia.org](https://en.wikipedia.org/wiki/VMware_Workstation_Player): VMWare Workstation Player Icon @ [[link](https://en.wikipedia.org/wiki/VMware_Workstation_Player)] 