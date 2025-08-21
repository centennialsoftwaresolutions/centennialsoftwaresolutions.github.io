# Resolving PetaLinux Tools 2018.2 installation error: tar: .: Cannot utime: Operation not permitted

![xilinx_logo_1](xilinx_logo_1.png)

This post shows you how to resolve: **tar: .: Cannot utime: Operation not permitted**

**tar: .: Cannot change mode to rwxr-xr-x: Operation not permitted**

**tar: Exiting with failure status due to previous errors** during a PetaLinux Tools 2018.2 Installation.

Here is the complete error:

```
zpfeffer@z:~/xpkgs$ ./petalinux-v2018.2-final-installer.run /opt/pkg/petalinux
INFO: Checking installer checksum...
INFO: Extracting PetaLinux installer...

LICENSE AGREEMENTS

PetaLinux SDK contains software from a number of sources.  Please review
the following licenses and indicate your acceptance of each to continue.

You do not have to accept the licenses, however if you do not then you may 
not use PetaLinux SDK.

Use PgUp/PgDn to navigate the license viewer, and press 'q' to close

Press Enter to display the license agreements
Do you accept Xilinx End User License Agreement? [y/N] > y
Do you accept Webtalk Terms and Conditions? [y/N] > y
Do you accept Third Party End User License Agreement? [y/N] > y
INFO: Checking installation environment requirements...
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution
INFO: Installing PetaLinux...
INFO: Checking PetaLinux installer integrity...
INFO: Installing PetaLinux SDK to "/opt/pkg/petalinux/."
................................................................................................................................................................................................................................................................................tar: .: Cannot utime: Operation not permitted
tar: .: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Exiting with failure status due to previous errors
*********************************************
ERROR: Failed to install PetaLinux SDK into "/opt/pkg/petalinux/."
*********************************************

Please refer to the PetaLinux Tools Installation Guide.

Check the troubleshooting guide at the end of that manual, and if you are
unable to resolve the issue please contact customer support with file:
   /home/zpfeffer/xpkgs/petalinux_installation_log
```

To fix it, check who owns /opt/pkg/petalinux:

1\. Type **cd /opt/pkg**

2\. Type **ls -l**

If you see **root** listed as the owner and **root** listed as the group this fix will work:

```
zpfeffer@z:/opt/pkg$ ls -l .
total 4
drwxrwxrwx 5 root root 4096 Aug 31 14:32 petalinux
```

3\. Type **cd petalinux/**

4\. Type **rm -rf \***

5\. Type **cd ..**

6\. Type **sudo chown -R zpfeffer:zpfeffer /opt/pkg/petalinux**

7\. Type **ls -l**

You should see:

```
zpfeffer@z:/opt/pkg$ ls -l
total 4
drwxrwxrwx 2 zpfeffer zpfeffer 4096 Aug 31 14:52 petalinux
```

8\. Now re-run: **./petalinux-v2018.2-final-installer.run /opt/pkg/petalinux** as the user you set.

**<u><span>Reference</span></u>**

Xilinx logo found via https://twitter.com/xilinxinc at [[link](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)]  