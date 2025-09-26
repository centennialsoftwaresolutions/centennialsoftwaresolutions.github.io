# Fix "ERROR: libtinfo.so.5 (libtinfo.so.5) is required by meta-xilinx-tools."

# Environment

Saw this while trying to run `petalinux-build` from **PetaLinux 2025.1** installed on **Ubuntu 24.04.3**

# Fix

Run these commands from [How to install libtinfo5 on Ubuntu24.04](https://askubuntu.com/questions/1531760/how-to-install-libtinfo5-on-ubuntu24-04):

```
sudo apt update
wget http://security.ubuntu.com/ubuntu/pool/universe/n/ncurses/libtinfo5_6.3-2ubuntu0.1_amd64.deb
sudo apt install ./libtinfo5_6.3-2ubuntu0.1_amd64.deb
```

## Fix Output

```
Hit:1 https://cli.github.com/packages stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu noble-security InRelease                                         
Hit:3 http://us.archive.ubuntu.com/ubuntu noble InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
72 packages can be upgraded. Run 'apt list --upgradable' to see them.
--2025-09-26 19:44:00--  http://security.ubuntu.com/ubuntu/pool/universe/n/ncurses/libtinfo5_6.3-2ubuntu0.1_amd64.deb
Resolving security.ubuntu.com... 185.125.190.83, 91.189.91.83, 185.125.190.81, ...
Connecting to security.ubuntu.com|185.125.190.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100086 (98K) [application/vnd.debian.binary-package]
Saving to: ‘libtinfo5_6.3-2ubuntu0.1_amd64.deb’

libtinfo5_6.3-2ubuntu0.1_amd64.deb              100%[======================================================================================================>]  97.74K   249KB/s    in 0.4s    

2025-09-26 19:44:01 (249 KB/s) - ‘libtinfo5_6.3-2ubuntu0.1_amd64.deb’ saved [100086/100086]

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'libtinfo5' instead of './libtinfo5_6.3-2ubuntu0.1_amd64.deb'
The following NEW packages will be installed:
  libtinfo5
0 upgraded, 1 newly installed, 0 to remove and 72 not upgraded.
Need to get 0 B/100 kB of archives.
After this operation, 557 kB of additional disk space will be used.
Get:1 /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/libtinfo5_6.3-2ubuntu0.1_amd64.deb libtinfo5 amd64 6.3-2ubuntu0.1 [100 kB]
Selecting previously unselected package libtinfo5:amd64.
(Reading database ... 372039 files and directories currently installed.)
Preparing to unpack .../libtinfo5_6.3-2ubuntu0.1_amd64.deb ...
Unpacking libtinfo5:amd64 (6.3-2ubuntu0.1) ...
Setting up libtinfo5:amd64 (6.3-2ubuntu0.1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.6) ...
N: Download is performed unsandboxed as root as file '/home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/libtinfo5_6.3-2ubuntu0.1_amd64.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

```

# Original Error Message

```
demo@demo:~/zcu102_petalinux/xilinx-zcu102-xsct-2025.1$ petalinux-build 
[INFO] Building project
[INFO] Extracting yocto SDK to components/yocto. This may take time!
[INFO] Bitbake is not available, some functionality may be reduced.
[INFO] Using HW file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/project-spec/hw-description/system.xsa
[INFO] Getting Platform info from HW file
[INFO] Generating Kconfig for project
[INFO] Silentconfig project
[INFO] Generating kconfig for rootfs
[INFO] Silentconfig rootfs
[INFO] Generating configuration files
[INFO] Adding user layers
[INFO] Generating machine conf file
[INFO] Generating plnxtool conf file
[INFO] Generating workspace directory
NOTE: Starting bitbake server...
NOTE: Started PRServer with DBfile: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/build/cache/prserv.sqlite3, Address: 127.0.0.1:38327, PID: 16785
INFO: Specified workspace already set up, leaving as-is
INFO: Enabling workspace layer in bblayers.conf
[INFO] bitbake petalinux-image-minimal
NOTE: Started PRServer with DBfile: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/build/cache/prserv.sqlite3, Address: 127.0.0.1:44987, PID: 16847
WARNING: XSCT has been deprecated. It will still be available for several releases. In the future, it's recommended to start new projects with SDT workflow.
ERROR: /usr/bin/gcc
 version gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


ERROR: libtinfo.so.5 (libtinfo.so.5) is required by meta-xilinx-tools.
This library must be installed before the build system can use xsct.  It is often part of an ncurses5 package.

Summary: There was 1 WARNING message.
Summary: There were 2 ERROR messages, returning a non-zero exit code.
[ERROR] Command bitbake petalinux-image-minimal failed
```