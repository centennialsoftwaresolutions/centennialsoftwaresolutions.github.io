# Ubuntu 20.04.3 LTS and VMware issues

When initially installing the latest version of VWware in Ubuntu 20.04.3 you may encounter some issues that prevent VMware from running properly. I encountered the error "Cannot open /dev/vmmon: No such file or directory" error when powering on a VM for the first time.

NOTE: Below are the instructions from VMware that work, but each time the kernel on the host machine gets updated you are likely to re-encounter this issue or one very similar to it. In my case, a small update and my virtual machine which was previously working fine became corrupted leaving me no other option but to rebuild from scratch. I ended up switching the host machine to Windows to avoid it in the future. VMware has issues running on a Ubuntu host machine right out of the "box" due to its secure boot features which can be disabled. This is a decent work around, but not sure it's worth the extra effort unless you've have no other options.

**Symptoms**  

-   Powering on a virtual machine on Linux hosts that boots from UEFI with secure boot enabled fails
    
-   You see the error: Cannot open /dev/vmmon: No such file or directory. Please make sure that the kernel module \`vmmon' is loaded
    

Purpose The article provide steps to sign VMware drivers on Linux host with secure boot enabled, so that VMware Workstation can run VMs successfully.

Cause On Linux host with secure mode enabled, it is not allowed to load any unsigned drivers. Due to this, VMware drivers, such as vmmon and vmnet, are not able to be loaded which prevents virtual machine to power on.

Resolution 

**Notes**:

-   Workstation does not ship vmmon.ko and vmnet.ko in the bundle currently. The two modules are built during the installation or the first launch of workstation.
    
-   During the installation if the host provides the proper kernel headers and gcc, these two modules will be built silently. The progress is logged into /tmp/vmware-root/vmware-PID.log.
    
-   When workstation is first launched, a dialog will pop up to ask you for the usable kernel headers and/or gcc. These two modules will be built with window showing the progress and log printed on terminal.
    
-   Ensure to have the Host OS updated with the latest patches.
    

To correct the issue with secure boot enabled:  

1.  Generate a key pair using the openssl to sign vmmon and vmnet modules: $openssl req -new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=VMware/" Replace MOK with the name of the file you want for the key.
    
2.  Sign the modules using the generated key by running these commands: $sudo /usr/src/linux-headers-\`uname -r\`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmmon) $sudo /usr/src/linux-headers-\`uname -r\`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmnet)
    

-   Import the public key to the system's MOK list by running this command: $mokutil --import MOK.der
    
-   Confirm a password for this MOK enrollment request.
    
-   Reboot your machine. Follow the instructions to complete the enrollment from the UEFI consol.