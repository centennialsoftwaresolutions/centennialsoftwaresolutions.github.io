# Resize a Virtual Machine Hard Disk in VMware Workstation 16 and Ubuntu 22.04.1 LTS

![VMware_workstation_logo_1](C:VMware_workstation_logo_1.png)

This post shows step-by-step how to resize a Virtual Machine Hard Disk in VMware Workstation 16 and Ubuntu 22.04.1 LTS.

## <u><span>Prereqs</span></u>

You'll need the sudo password in your Ubuntu install

## <u><span>Expand the Disk in VMware Workstation 16</span></u>

Launch **VMware Workstation Pro**

![Launch_Vmware_2](Launch_Vmware_2.png)

Find the VM that needs a larger hard disk.

![VM_large_hard_disk_3](VM_large_hard_disk_3.png)

Double-click the **Hard Disk (SCSI)** and click **Expand...**

![Hard_disk_expand_4](Hard_disk_expand_4.png)

Increase the **Maximum disk size (GB)** and click **Expand** (this may take a moment - it took my computer 10 minutes).

![Max_disc_size_5](Max_disc_size_5.png)

Click **OK**:

![disc_successful_expansion_6](disc_successful_expansion_6.png)

**Note**: you may need to move the disk from, for example, C:\\Users\\Zach Pfeffer\\Documents\\Virtual Machines\\vmwaredisk-20230708-vivado\_22.04.1-on-ubuntu\_22.04.01\\vmwaredisk-20230708-vivado\_22.04.1-on-ubuntu\_22.04.01.vmdk to a disk with more room. See [<u><span>How to Permanently Mount an External Drive as a Folder on Windows 10</span></u>](https://www.centennialsoftwaresolutions.com/post/how-to-permanently-mount-an-external-drive-as-a-folder-on-windows-10) to ensure this location persists.

## <u><span>Expand the Disk In Ubuntu</span></u>

Power on the virtual machine and boot Ubuntu completely

![Ubuntu_launch_7](Ubuntu_launch_7.png)

Run **disks**

![Run_discs_8](Run_discs_8.png)

Select the drive, select the partition, click the gear:

![select_gear_9](select_gear_9.png)

Click **Resize...**

![Click_resize_10](Click_resize_10.png)

Drag the slider to the right and click **Resize**

![Resize_11](Resize_11.png)

## Versions

In PowerShell:

Windows version:

```
systeminfo | findstr /B /C:"OS Name" /B /C:"OS Version"
```

Output:

```
OS Name:                   Microsoft Windows 10 Pro
OS Version:                10.0.19045 N/A Build 19045
```

VMware Workstation version:

```
Get-WmiObject -Class Win32_Product | where vendor -eq "VMware, Inc." | select Name, Version
```

Output:

```
Name               Version
----               -------
VMware Workstation 16.2.4
```

In a terminal on Ubuntu:

```
lsb_release -a
```

Output:

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy
```

### This post showed how to resize a Virtual Machine Hard Disk in VMware Workstation 16 and Ubuntu 22.04.1 LTS.

## <u><span>References</span></u>

VMware Workstation 16 Logo from: https://commons.wikimedia.org/wiki/File:Vmware_workstation_16_icon.svg 