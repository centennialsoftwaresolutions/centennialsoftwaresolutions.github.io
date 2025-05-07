# PetaLinux 2019.1 on Debian 10.3 Running on VMWare Workstation 14 Player Debug Log

![xilinx_logo](xilinx_logo.png)

This post lists the steps I took to bring up PetaLinux 2019.1 on Debian 10.3 running on VMWare Workstation 14 Player.

The log shows:

How to fix: "E: Unable to locate package"  on Debian 10.3

How to fix: "E: Unable to locate package zlib1g:i386" on Debian 10.3

How to install PetaLinux Tools 2019.1 into HOME

How to fix: "/mnt/hgfs/shared/petalinux-v2019.1-final-installer.run: line 140: /tmp/tmp.D0y1BqZe6j/petalinux-env-check: No such file or directory

ERROR: Failed to extract Petalinux installer..."

How to fix: "ERROR: You are missing the following system tools required by PetaLinux: - libtool"

How to fix: "WARNING: /bin/sh is not bash!" when your shell is set to bash

How to fix: "ERROR: Failed to generate /home/demo/plxprjs/xilinx-zc706-2019.1/build/misc/config/Kconfig.syshw" after typing **petalinux-build**

How to fix: "[INFO] generating Kconfig for project

couldn't read file "/home/demo/plxprjs/xilinx-zc706-2019.1/build/misc/config/hw-description/hw-description.tcl": no such file or directory"

How to fix: 

./xsct: line 194: 20320 Segmentation fault      "$RDI_BINROOT"/unwrapped/"$RDI_PLATFORM$RDI_OPT_EXT"/rlwrap -rc -b "(){}[],+= & ^%$#@"";|\\" -f "$HDI_APPROOT"/scripts/xsct/xsdb/cmdlist -H "$LOG_FILE" "$RDI_BINROOT"/loader -exec rdi_xsct "${RDI_ARGS[@]}"

...when running xsct directly

How to fix: hang at "[INFO] generating bbappends for project . This may take time !" Note: this one is fixed by using at least 4 GB of RAM in the VM and 4 cores.  

See kernel hang at: "hrtimer: interrupt took 66668558 ns" and continue...

**Part A: Make Sure Packages can be Installed**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Typed: **sudo apt-get install dos2unix**

I saw:

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Unable to locate package dos2unix

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Consulted "How to Add a Package Repository to Debian" @ [[link](https://linuxhint.com/how-to-add-a-package-repository-to-debian/)] 

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Typed: **sudo nano /etc/apt/sources.list**

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3).1: Added this line **in bold**:

deb http://security.debian.org/debian-security buster/updates main

deb-src http://security.debian.org/debian-security buster/updates main

**deb http://ftp.us.debian.org/debian buster main contrib non-free**

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3).2 Saved the file and exited. 

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): Typed: **sudo apt-get update**

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4).1: I now see:

```
demo@debian:~/plxprjs/xilinx-zc706-2019.1$ sudo apt-get update
Hit:1 http://security.debian.org/debian-security buster/updates InRelease
Get:2 http://ftp.us.debian.org/debian buster InRelease [121 kB]
Get:3 http://ftp.us.debian.org/debian buster/main i386 Packages [7,863 kB]
Get:4 http://ftp.us.debian.org/debian buster/main amd64 Packages [7,906 kB]
Get:5 http://ftp.us.debian.org/debian buster/main Translation-en [5,968 kB]
Get:6 http://ftp.us.debian.org/debian buster/contrib i386 Packages [46.4 kB]
Get:7 http://ftp.us.debian.org/debian buster/contrib amd64 Packages [50.5 kB]
Get:8 http://ftp.us.debian.org/debian buster/contrib Translation-en [44.5 kB]
Get:9 http://ftp.us.debian.org/debian buster/non-free amd64 Packages [87.7 kB]
Get:10 http://ftp.us.debian.org/debian buster/non-free i386 Packages [76.2 kB]
Get:11 http://ftp.us.debian.org/debian buster/non-free Translation-en [88.8 kB]
Fetched 22.3 MB in 5s (4,236 kB/s)                                
Reading package lists... Done
```

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): Type: **sudo apt-get install dos2unix**

You should now see:

```
demo@debian:~/plxprjs/xilinx-zc706-2019.1$ sudo apt-get install dos2unix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dos2unix
0 upgraded, 1 newly installed, 0 to remove and 45 not upgraded.
Need to get 391 kB of archives.
After this operation, 1,339 kB of additional disk space will be used.
Get:1 http://ftp.us.debian.org/debian buster/main amd64 dos2unix amd64 7.4.0-1 [391 kB]
Fetched 391 kB in 1s (558 kB/s)  
Selecting previously unselected package dos2unix.
(Reading database ... 71059 files and directories currently installed.)
Preparing to unpack .../dos2unix_7.4.0-1_amd64.deb ...
Unpacking dos2unix (7.4.0-1) ...
Setting up dos2unix (7.4.0-1) ...
Processing triggers for man-db (2.8.5-2) ...
```

**Part B: Try to use the Packages that Xilinx Lists for Ubuntu 16.04.5 in the PetaLinux Tools Documentation Reference Guide**

On page 11 of UG1144 (v2019.1) May 22, 2019 www.xilinx.com

PetaLinux Tools Documentation Reference Guide at [[link](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2019_1/ug1144-petalinux-tools-reference-guide.pdf)] it lists the following (I've removed the -dev which looks like a typo):

**sudo apt-get install -y gcc git make net-tools libncurses5-dev tftpd zlib1g-dev libssl-dev flex bison libselinux1 gnupg wget diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib build-essential zlib1g:i386 screen pax gzip**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Typed: ^^^ 

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1).1: I saw:

E: Unable to locate package zlib1g:i386

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Consulted [[https://wiki.debian.org/Multiarch/HOWTO](https://wiki.debian.org/Multiarch/HOWTO)]

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Typed: 

**sudo dpkg --add-architecture i386**

**sudo apt-get update**

**sudo apt-get install -y gcc git make net-tools libncurses5-dev tftpd zlib1g-dev libssl-dev flex bison libselinux1 gnupg wget diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib build-essential zlib1g:i386 screen pax gzip**

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3).1. I saw that this ^^^ worked, i.e. I was able to install **zlib1g:i386**

**Part C: Make Sure the Shell Is BASH**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Typed: **echo $SHELL**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1).1: I saw:

**/bin/bash**

**Part D: Install PetaLinux Tools 2019.1 into $HOME**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Typed

**mkdir -p $HOME/petalinux**

**/mnt/hgfs/shared/petalinux-v2019.1-final-installer.run $HOME/petalinux/2019.1**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1).1: Observed:

```
INFO: Checking installation environment requirements...

Please refer to the PetaLinux Tools Installation Guide.

Check the troubleshooting guide at the end of that manual, and if you are
unable to resolve the issue please contact customer support with file:
   /home/demo/petalinux_installation_log

/mnt/hgfs/shared/petalinux-v2019.1-final-installer.run: line 140: /tmp/tmp.D0y1BqZe6j/petalinux-env-check: No such file or directory
ERROR: Failed to extract Petalinux installer...
```

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1).2: Examined log. Typed:

**cat /home/demo/petalinux_installation_log**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1).2.1: /home/demo/petalinux_installation_log did report anything new. It contained the output listed above.

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Consulted [https://forums.xilinx.com/t5/Embedded-Linux/Petalinux-installation-error-on-ubuntu-VM/td-p/987948] It says you need gawk

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2).1: Type the following to install gawk

**sudo apt-get install gawk**

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2).2: Saw gawk successfully installed

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Reran:

**/mnt/hgfs/shared/petalinux-v2019.1-final-installer.run $HOME/petalinux/2019.1**

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3).1: Observed:

```
demo@debian:~$ /mnt/hgfs/shared/petalinux-v2019.1-final-installer.run $HOME/petalinux/2019.1
INFO: Checking installation environment requirements...
WARNING: This is not a supported OS
INFO: Checking free disk space
INFO: Checking installed tools
ERROR: You are missing the following system tools required by PetaLinux:

 - libtool
Please check PetaLinux installation guide - required tools and libraries package section for detailed information

INFO: Checking installed development libraries
Please install them with your operating system package manager, and try again
WARNING: Please install required packages.

Please refer to the PetaLinux Tools Installation Guide.

Check the troubleshooting guide at the end of that manual, and if you are
unable to resolve the issue please contact customer support with file:
   /home/demo/petalinux_installation_log
```

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): Consulted [[https://forums.xilinx.com/t5/Embedded-Linux/PetaLinux-doesn-t-see-libtool-so-it-won-t-run/td-p/765603](https://forums.xilinx.com/t5/Embedded-Linux/PetaLinux-doesn-t-see-libtool-so-it-won-t-run/td-p/765603)]

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4).1:  The post suggests that the error message does not report the correct package. You actually need libtool-bin

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4).2: Type:

**sudo apt-get install libtool-bin**

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4).2.1: Saw libtool-bin successfully installed

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): Reran:

/mnt/hgfs/shared/petalinux-v2019.1-final-installer.run $HOME/petalinux/2019.1

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5).1: Accepted the license agreements (Press: Enter,q,y,q,y)

Saw the following output that suggests the install went okay:

```
demo@debian:~$ /mnt/hgfs/shared/petalinux-v2019.1-final-installer.run $HOME/petalinux/2019.1
INFO: Checking installation environment requirements...
WARNING: This is not a supported OS
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
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
INFO: Installing PetaLinux...
INFO: Checking PetaLinux installer integrity...
INFO: Installing PetaLinux SDK to "/home/demo/petalinux/2019.1/."
INFO: Installing aarch64 Yocto SDK to "/home/demo/petalinux/2019.1/./components/yocto/source/aarch64"...
INFO: Installing arm Yocto SDK to "/home/demo/petalinux/2019.1/./components/yocto/source/arm"...
INFO: Installing microblaze_full Yocto SDK to "/home/demo/petalinux/2019.1/./components/yocto/source/microblaze_full"...
INFO: Installing microblaze_lite Yocto SDK to "/home/demo/petalinux/2019.1/./components/yocto/source/microblaze_lite"...
INFO: PetaLinux SDK has been installed to /home/demo/petalinux/2019.1/.
```

**Part E: Build a BSP to Check Install**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Typed:

**mkdir -p ~/plxprjs**

**cd ~/plxprjs**

**source ~/petalinux/2019.1/settings.sh**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1).1: I saw:

```
demo@debian:~/plxprjs$ source ~/petalinux/2019.1/settings.sh
PetaLinux environment set to '/home/demo/petalinux/2019.1'
WARNING: /bin/sh is not bash!
bash is PetaLinux recommended shell. Please set your default shell to bash.
WARNING: This is not a supported OS
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
```

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Point /bin/sh to bash. Typed:

**sudo ln -sf bash /bin/sh**

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Test it. Typed:

**ls -l /bin/sh**

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3).1: I now see:

```
lrwxrwxrwx 1 root root 4 Nov 23 00:38 /bin/sh -> bash
```

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): Re-source settings. Type:

**source ~/petalinux/2019.1/settings.sh**

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4).1: Now I see: 

```
PetaLinux environment set to '/home/demo/petalinux/2019.1'
WARNING: This is not a supported OS
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
```

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4).2: Will ignore: 

```
WARNING: This is not a supported OS
```

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): Typed:

petalinux-create -t project -s /mnt/hgfs/shared/xilinx-zc706-v2019.1-final.bsp

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5).1: I see:

```
INFO: Create project:
INFO: Projects:
INFO: 	* xilinx-zc706-2019.1
INFO: has been successfully installed to /home/demo/plxprjs/
INFO: New project successfully created in /home/demo/plxprjs/
```

Step [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6): Typed:

**cd xilinx-zc706-2019.1/**

**petalinux-build**

Step [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6).1: I see:

```
[INFO] building project
environment: line 100: rsync: command not found
environment: line 101: rsync: command not found
environment: line 102: rsync: command not found
[INFO] generating Kconfig for project
ERROR: Failed to generate /home/demo/plxprjs/xilinx-zc706-2019.1/build/misc/config/Kconfig.syshw
ERROR: Failed to Kconfig project
ERROR: Failed to build project
```

Step [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6).2: Fix rsync. Type:

**sudo apt-get install rsync**

Step [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7): Typed:

**petalinux-build**

Step [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7).1: I see:

```
[INFO] building project
[INFO] generating Kconfig for project
ERROR: Failed to generate /home/demo/plxprjs/xilinx-zc706-2019.1/build/misc/config/Kconfig.syshw
ERROR: Failed to Kconfig project
ERROR: Failed to build project
```

Step [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7).2: Examined build/build.log

```
[INFO] building project
[INFO] generating Kconfig for project
package require hsi FAILED:
invalid command name "hsi::create_dt_node"
    while executing
"hsi::create_dt_node -help"
    (in namespace eval "::hsi::help" script line 6)
    invoked from within
"namespace eval ::hsi::help {
    variable version 0.1

    ::xsdb::setcmdmeta {hsi create_dt_node} categories {hsi}
    ::xsdb::setcmdmeta {hsi create..."
    (file "/home/demo/petalinux/2019.1/tools/xsct/scripts/xsct/hsi/hsihelp.tcl" line 25)
    invoked from within
"source /home/demo/petalinux/2019.1/tools/xsct/scripts/xsct/hsi/hsihelp.tcl"
    ("package ifneeded hsi::help 0.1" script)ERROR: Failed to generate /home/demo/plxprjs/xilinx-zc706-2019.1/build/misc/config/Kconfig.syshw
ERROR: Failed to Kconfig project
ERROR: Failed to build project
```

Step [#8](https://www.centennialsoftwaresolutions.com/blog/hashtags/8): Installed libncurses5:

**sudo apt-get install libncurses5**

Step [#9](https://www.centennialsoftwaresolutions.com/blog/hashtags/9): Reran:

**cd ..**

**rm -rf xilinx-zc706-2019.1**

**petalinux-create -t project -s /mnt/hgfs/shared/xilinx-zc706-v2019.1-final.bsp**

Step [#9](https://www.centennialsoftwaresolutions.com/blog/hashtags/9).1: Saw: 

```
INFO: Create project:
INFO: Projects:
INFO: 	* xilinx-zc706-2019.1
INFO: has been successfully installed to /home/demo/plxprjs/xilinx-zc706-2019.1/
INFO: New project successfully created in /home/demo/plxprjs/xilinx-zc706-2019.1/
```

Step [#10](https://www.centennialsoftwaresolutions.com/blog/hashtags/10): Ran:

**petalinux-build**

Step [#10](https://www.centennialsoftwaresolutions.com/blog/hashtags/10).1: Saw:

```
[INFO] building project
[INFO] generating Kconfig for project
ERROR: Failed to generate /home/demo/plxprjs/xilinx-zc706-2019.1/build/misc/config/Kconfig.syshw
ERROR: Failed to Kconfig project
ERROR: Failed to build project
```

Step [#10](https://www.centennialsoftwaresolutions.com/blog/hashtags/10).2: Examine build/build.log:

```
[INFO] building project
[INFO] generating Kconfig for project
couldn't read file "/home/demo/plxprjs/xilinx-zc706-2019.1/build/misc/config/hw-description/hw-description.tcl": no such file or directory
ERROR: Failed to generate /home/demo/plxprjs/xilinx-zc706-2019.1/build/misc/config/Kconfig.syshw
ERROR: Failed to Kconfig project
ERROR: Failed to build project
```

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11): Investigate running xsct directly. Typed:

**cd ~/petalinux/2019.1/tools/xsct/bin/**

**./xsct**

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11).1: Saw:

```
./xsct: line 194: 20320 Segmentation fault      "$RDI_BINROOT"/unwrapped/"$RDI_PLATFORM$RDI_OPT_EXT"/rlwrap -rc -b "(){}[],+= & ^%$#@"";|\\" -f "$HDI_APPROOT"/scripts/xsct/xsdb/cmdlist -H "$LOG_FILE" "$RDI_BINROOT"/loader -exec rdi_xsct "${RDI_ARGS[@]}"
```

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11).2: Consulted [https://wiki.archlinux.org/index.php/Xilinx_Vivado#xsct,_xsdb,_xmd,_and_tclsh_segfault]

 

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11).3: Installed rlwrap. Typed:

**sudo apt-get install rlwrap**

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11).4: Check rlwrap's path. Typed:

**which rlwrap**

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11).4.1: Saw:

/usr/bin/rlwrap

Step 11.5: Edit xsct. Typed:

**vi +194 xsct**

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11).5.1: Changed(in **bold**)

​       **"$RDI_BINROOT"/unwrapped/"$RDI_PLATFORM$RDI_OPT_EXT"/**rlwrap -rc -b "(){}[],+= & ^%$#@"";|\\" -f "$HDI_APPROOT"/scripts/xsct/xsdb/cmdlist -H "$LOG_FILE" "$RDI_BINROOT"/loader -exec rdi_xsct "${RDI_ARGS[@]}"

​       to:

​        **/usr/bin/**rlwrap -rc -b "(){}[],+= & ^%$#@"";|\\" -f "$HDI_APPROOT"/scripts/xsct/xsdb/cmdlist -H "$LOG_FILE" "$RDI_BINROOT"/loader -exec rdi_xsct "${RDI_ARGS[@]}"

Step [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12): Retested. Typed

**cd ~/plxprjs**

**source ~/petalinux/2019.1/settings.sh**

**rm -rf xilinx-zc706-2019.1/**

**petalinux-create -t project -s /mnt/hgfs/shared/xilinx-zc706-v2019.1-final.bsp**

Step [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12).1: Saw:

```
INFO: Create project:
INFO: Projects:
INFO: 	* xilinx-zc706-2019.1
INFO: has been successfully installed to /home/demo/plxprjs/
INFO: New project successfully created in /home/demo/plxprjs/
```

Step [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12).1.1: Rebuild. Typed:

**cd xilinx-zc706-2019.1/**

**petalinux-build**

Step [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12).1.2: Saw a hang at:

[INFO] generating bbappends for project . This may take time !

Step [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12).1.3: Typed **Ctrl-C** and looked at build/build.log

```
NOTE: Reconnecting to bitbake server...
Traceback (most recent call last):
  File "/home/demo/petalinux/2019.1/components/yocto/source/arm/layers/core/bitbake/bin/bitbake-layers", line 103, in <module>
    ret = main()
  File "/home/demo/petalinux/2019.1/components/yocto/source/arm/layers/core/bitbake/bin/bitbake-layers", line 71, in main
    tinfoil.prepare(True)
  File "/home/demo/petalinux/2019.1/components/yocto/source/arm/layers/core/bitbake/lib/bb/tinfoil.py", line 397, in prepare
    extrafeatures)
  File "/home/demo/petalinux/2019.1/components/yocto/source/arm/layers/core/bitbake/lib/bb/main.py", line 464, in setup_bitbake
    server_connection = bb.server.process.connectProcessServer(sockname, featureset)
  File "/home/demo/petalinux/2019.1/components/yocto/source/arm/layers/core/bitbake/lib/bb/server/process.py", line 474, in connectProcessServer
    sock.connect(os.path.basename(sockname))
KeyboardInterrupt
NOTE: Reconnecting to bitbake server...
```

Step [#13](https://www.centennialsoftwaresolutions.com/blog/hashtags/13): Give the VM at least 4 cores. Gave it 6 for good measure and tried again. Typed:

**cd ~/plxprjs**

**source ~/petalinux/2019.1/settings.sh**

**rm -rf xilinx-zc706-2019.1/**

**sudo vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other # Mount shared**

**petalinux-create -t project -s /mnt/hgfs/shared/xilinx-zc706-v2019.1-final.bsp**

**cd xilinx-zc706-2019.1/**

**petalinux-build**

Step [#13](https://www.centennialsoftwaresolutions.com/blog/hashtags/13).1: This ^^^ also failed appeared to hang. Increased cores to 12. Typed:

**cd ~/plxprjs**

**source ~/petalinux/2019.1/settings.sh**

**rm -rf xilinx-zc706-2019.1/**

**sudo vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other # Mount shared**

**petalinux-create -t project -s /mnt/hgfs/shared/xilinx-zc706-v2019.1-final.bsp**

**cd xilinx-zc706-2019.1/**

**petalinux-build**

Step [#13](https://www.centennialsoftwaresolutions.com/blog/hashtags/13).2: Saw it stuck. Killed with Ctrl-C. Typed

**ps auxf**

Step [#13](https://www.centennialsoftwaresolutions.com/blog/hashtags/13).2.1: Examined excerpt: 

demo       3554  0.3  1.8 363576 13460 ?        S    02:08   1:38 /home/demo/petalinux/2019.1/components/yoct

demo       3569  0.0  0.0      0     0 ?        Z    02:08   0:26  \_ [Cooker] <defunct>

demo       3570  0.3  0.0      0     0 ?        Z    02:08   1:57  \_ [Parser-1:2] <defunct>

demo       3572  0.2  0.0      0     0 ?        Z    02:08   1:04  \_ [Parser-1:3] <defunct>

demo       3573  2.1  0.0      0     0 ?        Z    02:08  11:07  \_ [Parser-1:4] <defunct>

demo       3574  0.2  0.0      0     0 ?        Z    02:08   1:23  \_ [Parser-1:5] <defunct>

demo       3575  0.1  0.0      0     0 ?        Z    02:08   0:44  \_ [Parser-1:6] <defunct>

demo       3576  0.5  0.0      0     0 ?        Z    02:08   2:52  \_ [Parser-1:7] <defunct>

Step [#13](https://www.centennialsoftwaresolutions.com/blog/hashtags/13).2.2: Killed Cooker. Typed:

**kill -9 3554**

Step [#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14): Consulted [https://forums.xilinx.com/t5/Embedded-Linux/Infinite-time-for-petalinux-build/td-p/810478] 

Step [#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14).1: Needed more RAM: Used 16 GB.Retested after setting VM to use 16 GB of RAM. Typed:

**cd ~/plxprjs**

**source ~/petalinux/2019.1/settings.sh**

**cd xilinx-zc706-2019.1/**

**petalinux-build**

**petalinux-boot --qemu --kernel**

Step [#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14).1.1: Observed a successful build.

Step [#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14).1.2: Observed the log of boot.

Step [#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14).1.2.1: The build appeared to hang around: hrtimer: interrupt took 66668558 ns

Run /init as init process

udevd[797]: starting version 3.2.5

random: udevd: uninitialized urandom read (16 bytes read)

random: udevd: uninitialized urandom read (16 bytes read)

random: udevd: uninitialized urandom read (16 bytes read)

udevd[798]: starting eudev-3.2.5

urandom_read: 1 callbacks suppressed

random: udevd: uninitialized urandom read (16 bytes read)

hrtimer: interrupt took 66668558 ns

Step [#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14).1.2.2: I needed to wait a few minutes. Then I saw the build continue:

random: dd: uninitialized urandom read (512 bytes read)

IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

macb e000b000.ethernet eth0: link up (100/Full)

IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

random: dropbearkey: uninitialized urandom read (32 bytes read)

random: dropbearkey: uninitialized urandom read (32 bytes read)

random: dropbearkey: uninitialized urandom read (32 bytes read)

random: dropbear: uninitialized urandom read (32 bytes read)

PetaLinux 2019.1 xilinx-zc706-2019_1 /dev/ttyPS0

xilinx-zc706-2019_1 login:

Used root as the username and root as the password

Step [#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14).1.2.3: Observed the full log:

```
demo@debian:~/plxprjs/xilinx-zc706-2019.1$ petalinux-boot --qemu --kernel
INFO: sourcing build tools
INFO: The image provided is a zImage
environment: line 1458: bc: command not found
INFO: Set QEMU tftp to /home/demo/plxprjs/xilinx-zc706-2019.1/images/linux
INFO: TCP PORT is free
INFO: Starting arm QEMU
INFO:  qemu-system-aarch64 -M arm-generic-fdt-7series -machine linux=on   -serial /dev/null -serial mon:stdio -display none -kernel /home/demo/plxprjs/xilinx-zc706-2019.1/build/qemu_image.elf -gdb tcp::9000 -dtb /home/demo/plxprjs/xilinx-zc706-2019.1/images/linux/system.dtb  -net nic,vlan=1 -net user,vlan=1,tftp=/home/demo/plxprjs/xilinx-zc706-2019.1/images/linux -net nic -device loader,addr=0xf8000008,data=0xDF0D,data-len=4 -device loader,addr=0xf8000140,data=0x00500801,data-len=4 -device loader,addr=0xf800012c,data=0x1ed044d,data-len=4 -device loader,addr=0xf8000108,data=0x0001e008,data-len=4 -device loader,addr=0xF8000910,data=0xF,data-len=0x4
qemu-system-aarch64: -net nic,vlan=1: 'vlan' is deprecated. Please use 'netdev' instead.
qemu-system-aarch64: warning: vlan 0 is not connected to host network
rom: requested regions overlap (rom bootloader. free=0x0000000000a6c5f0, addr=0x0000000000000000)
```

...continues with the kernel boot:

```
Booting Linux on physical CPU 0x0
Linux version 4.19.0-xilinx-v2019.1 (oe-user@oe-host) (gcc version 8.2.0 (GCC)) #1 SMP PREEMPT Mon Nov 23 18:10:16 UTC 2020
CPU: ARMv7 Processor [410fc090] revision 0 (ARMv7), cr=10c5387d
CPU: PIPT / VIPT nonaliasing data cache, VIPT nonaliasing instruction cache
OF: fdt: Machine model: Zynq ZC706 Development Board
bootconsole [earlycon0] enabled
Memory policy: Data cache writealloc
cma: Reserved 16 MiB at 0x3f000000
random: get_random_bytes called from start_kernel+0x80/0x3c4 with crng_init=0
percpu: Embedded 16 pages/cpu @(ptrval) s35916 r8192 d21428 u65536
Built 1 zonelists, mobility grouping on.  Total pages: 260608
Kernel command line: console=ttyPS0,115200 earlyprintk
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 1000608K/1048576K available (6144K kernel code, 204K rwdata, 1608K rodata, 13312K init, 132K bss, 31584K reserved, 16384K cma-reserved, 245760K highmem)
Virtual kernel memory layout:
    vector  : 0xffff0000 - 0xffff1000   (   4 kB)
    fixmap  : 0xffc00000 - 0xfff00000   (3072 kB)
    vmalloc : 0xf0800000 - 0xff800000   ( 240 MB)
    lowmem  : 0xc0000000 - 0xf0000000   ( 768 MB)
    pkmap   : 0xbfe00000 - 0xc0000000   (   2 MB)
    modules : 0xbf000000 - 0xbfe00000   (  14 MB)
      .text : 0x(ptrval) - 0x(ptrval)   (7136 kB)
      .init : 0x(ptrval) - 0x(ptrval)   (13312 kB)
      .data : 0x(ptrval) - 0x(ptrval)   ( 205 kB)
       .bss : 0x(ptrval) - 0x(ptrval)   ( 133 kB)
rcu: Preemptible hierarchical RCU implementation.
rcu: 	RCU restricting CPUs from NR_CPUS=4 to nr_cpu_ids=2.
	Tasks RCU enabled.
rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
NR_IRQS: 16, nr_irqs: 16, preallocated irqs: 16
efuse mapped to (ptrval)
slcr mapped to (ptrval)
L2C: platform modifies aux control register: 0x00000000 -> 0x30400000
L2C: DT/platform modifies aux control register: 0x00000000 -> 0x30400000
L2C-310 errata 588369 769419 enabled
L2C-310 full line of zeros enabled for Cortex-A9
L2C-310 cache controller enabled, 8 ways, 64 kB
L2C-310: CACHE_ID 0x00000000, AUX_CTRL 0x00000000
zynq_clock_init: clkc starts at (ptrval)
Zynq clock init
global-timer: non support for this cpu version.
Failed to initialize '/amba/timer@f8f00200': -38
clocksource: ttc_clocksource: mask: 0xffff max_cycles: 0xffff, max_idle_ns: 826992825 ns
sched_clock: 16 bits at 35kHz, resolution 28357ns, wraps every 929205421ns
timer #0 at (ptrval), irq=16
Console: colour dummy device 80x30
Calibrating delay loop... 587.36 BogoMIPS (lpj=2936832)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
CPU: Testing write buffer coherency: ok
CPU0: Spectre v2: using BPIALL workaround
CPU0: thread -1, cpu 0, socket 0, mpidr 80000000
Setting up static identity map for 0x100000 - 0x100060
rcu: Hierarchical SRCU implementation.
smp: Bringing up secondary CPUs ...
CPU1: thread -1, cpu 1, socket 0, mpidr 80000001
CPU1: Spectre v2: using BPIALL workaround
smp: Brought up 1 node, 2 CPUs
SMP: Total of 2 processors activated (1159.16 BogoMIPS).
CPU: All CPU(s) started in SVC mode.
devtmpfs: initialized
VFP support v0.3: implementor 41 architecture 3 part 30 variant 9 rev 0
clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
futex hash table entries: 512 (order: 3, 32768 bytes)
pinctrl core: initialized pinctrl subsystem
NET: Registered protocol family 16
DMA: preallocated 256 KiB pool for atomic coherent allocations
cpuidle: using governor menu
hw-breakpoint: debug architecture 0x4 unsupported.
zynq-ocm f800c000.ocmc: ZYNQ OCM pool: 256 KiB @ 0x(ptrval)
zynq-pinctrl 700.pinctrl: zynq pinctrl initialized
e0001000.serial: ttyPS0 at MMIO 0xe0001000 (irq = 25, base_baud = 992063) is a xuartps
console [ttyPS0] enabled
console [ttyPS0] enabled
bootconsole [earlycon0] disabled
bootconsole [earlycon0] disabled
GPIO IRQ not connected
XGpio: gpio@41200000: registered, base is 1020
GPIO IRQ not connected
XGpio: gpio@41210000: registered, base is 1017
GPIO IRQ not connected
XGpio: gpio@41220000: registered, base is 1013
vgaarb: loaded
SCSI subsystem initialized
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
media: Linux media interface: v0.10
videodev: Linux video capture interface: v2.00
pps_core: LinuxPPS API ver. 1 registered
pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
PTP clock support registered
EDAC MC: Ver: 3.0.0
FPGA manager framework
Advanced Linux Sound Architecture Driver Initialized.
clocksource: Switched to clocksource ttc_clocksource
NET: Registered protocol family 2
tcp_listen_portaddr_hash hash table entries: 512 (order: 0, 6144 bytes)
TCP established hash table entries: 8192 (order: 3, 32768 bytes)
TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
TCP: Hash tables configured (established 8192 bind 8192)
UDP hash table entries: 512 (order: 2, 16384 bytes)
UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
NET: Registered protocol family 1
RPC: Registered named UNIX socket transport module.
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
hw perfevents: no interrupt-affinity property for /pmu@f8891000, guessing.
hw perfevents: enabled with armv7_cortex_a9 PMU driver, 1 counters available
workingset: timestamp_bits=30 max_order=18 bucket_order=0
jffs2: version 2.2. (NAND) (SUMMARY)  © 2001-2006 Red Hat, Inc.
bounce: pool size: 64 pages
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
io scheduler mq-deadline registered
io scheduler kyber registered
dma-pl330 f8003000.dmac: Loaded driver for PL330 DMAC-241330
dma-pl330 f8003000.dmac: 	DBUFF-256x8bytes Num_Chans-8 Num_Peri-4 Num_Events-16
brd: module loaded
loop: module loaded
m25p80 spi0.0: found n25q512a13, expected n25q512a
m25p80 spi0.0: n25q512a13 (131072 Kbytes)
3 fixed-partitions partitions found on MTD device spi0.0
Creating 3 MTD partitions on "spi0.0":
0x000000000000-0x000000e00000 : "boot"
0x000000e00000-0x000000e20000 : "bootenv"
0x000000e20000-0x0000018a0000 : "kernel"
libphy: Fixed MDIO Bus: probed
CAN device driver interface
libphy: MACB_mii_bus: probed
Marvell 88E1149R e000b000.ethernet-ffffffff:07: attached PHY driver [Marvell 88E1149R] (mii_bus:phy_addr=e000b000.ethernet-ffffffff:07, irq=POLL)
macb e000b000.ethernet eth0: Cadence GEM rev 0x00020118 at 0xe000b000 irq 27 (00:0a:35:00:1e:53)
e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ehci-pci: EHCI PCI platform driver
usbcore: registered new interface driver usb-storage
chipidea-usb2 e0002000.usb: e0002000.usb supply vbus not found, using dummy regulator
chipidea-usb2 e0002000.usb: Linked as a consumer to regulator.0
ULPI transceiver vendor/product ID 0x0424/0x0004
ULPI integrity check: passed.
ci_hdrc ci_hdrc.0: EHCI Host Controller
ci_hdrc ci_hdrc.0: new USB bus registered, assigned bus number 1
ci_hdrc ci_hdrc.0: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 6 ports detected
i2c /dev entries driver
cdns-i2c e0004000.i2c: 400 kHz mmio e0004000 irq 22
si570 1-005d: registered, current frequency 148500000 Hz
i2c i2c-0: Added multiplexed i2c bus 1
i2c i2c-0: Added multiplexed i2c bus 2
cdns-i2c e0004000.i2c: timeout waiting on completion
i2c i2c-0: Added multiplexed i2c bus 3
i2c i2c-0: Added multiplexed i2c bus 4
cdns-i2c e0004000.i2c: timeout waiting on completion
rtc-pcf8563 5-0051: pcf8563_write_block_data: err=-110 addr=0e, data=03
rtc-pcf8563 5-0051: pcf8563_probe: write error
rtc-pcf8563: probe of 5-0051 failed with error -5
i2c i2c-0: Added multiplexed i2c bus 5
i2c i2c-0: Added multiplexed i2c bus 6
i2c i2c-0: Added multiplexed i2c bus 7
i2c i2c-0: Added multiplexed i2c bus 8
pca954x 0-0074: registered 8 multiplexed busses for I2C switch pca9548
cdns-i2c e0004000.i2c: timeout waiting on completion
ucd9000 8-0065: Failed to read device ID
ucd9000: probe of 8-0065 failed with error -110
cdns-wdt f8005000.watchdog: Xilinx Watchdog Timer at (ptrval) with timeout 10s
EDAC MC: ECC not enabled
Xilinx Zynq CpuIdle Driver started
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
sdhci-pltfm: SDHCI platform and OF driver helper
mmc0: SDHCI controller on e0100000.mmc [e0100000.mmc] using ADMA 64-bit
ledtrig-cpu: registered to indicate activity on CPUs
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
fpga_manager fpga0: Xilinx Zynq FPGA Manager registered
NET: Registered protocol family 10
Segment Routing with IPv6
sit: IPv6, IPv4 and MPLS over IPv4 tunneling driver
NET: Registered protocol family 17
can: controller area network core (rev 20170425 abi 9)
NET: Registered protocol family 29
can: raw protocol (rev 20170425)
can: broadcast manager protocol (rev 20170425 t)
can: netlink gateway (rev 20170425) max_hops=1
Registering SWP/SWPB emulation handler
of-fpga-region fpga-full: FPGA Region probed
hctosys: unable to open rtc device (rtc0)
of_cfs_init
of_cfs_init: OK
ALSA device list:
  No soundcards found.
Warning: unable to open an initial console.
Freeing unused kernel memory: 13312K
Run /init as init process
udevd[797]: starting version 3.2.5
random: udevd: uninitialized urandom read (16 bytes read)
random: udevd: uninitialized urandom read (16 bytes read)
random: udevd: uninitialized urandom read (16 bytes read)
udevd[798]: starting eudev-3.2.5
urandom_read: 1 callbacks suppressed
random: udevd: uninitialized urandom read (16 bytes read)
hrtimer: interrupt took 66668558 ns
random: dd: uninitialized urandom read (512 bytes read)
IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
macb e000b000.ethernet eth0: link up (100/Full)
IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
random: dropbearkey: uninitialized urandom read (32 bytes read)
random: dropbearkey: uninitialized urandom read (32 bytes read)
random: dropbearkey: uninitialized urandom read (32 bytes read)
random: dropbear: uninitialized urandom read (32 bytes read)

PetaLinux 2019.1 xilinx-zc706-2019_1 /dev/ttyPS0

xilinx-zc706-2019_1 login: root
Password:
root@xilinx-zc706-2019_1:~#
```

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15): Now lower cores to 4 and memory to 4 GB (4096). Type:

**cd ~/plxprjs**

**source ~/petalinux/2019.1/settings.sh**

**cd xilinx-zc706-2019.1/**

**petalinux-build -x mrproper**

**petalinux-build**

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15).1: With 4GB I get to here:

[INFO] generating bbappends for project . This may take time !

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15).1.1: Typed: **top**

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15).1.2: Observed:

```
demo@debian:~$ top

top - 13:01:26 up 5 min,  1 user,  load average: 4.09, 2.37, 1.03
Tasks: 174 total,   5 running, 169 sleeping,   0 stopped,   0 zombie
%Cpu(s): 82.0 us, 17.9 sy,  0.0 ni,  0.1 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3923.5 total,   1577.0 free,   1711.4 used,    635.1 buff/cache
MiB Swap:    766.0 total,    766.0 free,      0.0 used.   1972.6 avail Mem

   PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
  2684 demo      20   0  485780 308536   4224 R  99.7   7.7   2:55.14 Parser-1:2
  2686 demo      20   0  484156 307148   4224 R  98.7   7.6   2:57.52 Parser-1:4
  2687 demo      20   0  489464 312596   4224 R  98.7   7.8   2:57.80 Parser-1:5
  2685 demo      20   0  487848 310352   4224 R  90.7   7.7   2:55.34 Parser-1:3
   591 root      20   0  604848 127880  32732 S   4.7   3.2   0:12.39 Xorg
  2667 demo      20   0  275912 171516   4544 S   4.0   4.3   0:12.19 Cooker
```

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15).2: This ^^^ will take about 10 minutes

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15).3: The build takes about 1 hour with 4 GB RAM and 4 cores.

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15).3.1: Observed build output:

```
At the end of the build you should see:
[INFO] building project
[INFO] generating Kconfig for project
[INFO] silentconfig project
[INFO] sourcing bitbake
[INFO] generating plnxtool conf
[INFO] generating meta-plnx-generated layer
[INFO] generating bbappends for project . This may take time ! 
[INFO] generating u-boot configuration files
[INFO] generating kernel configuration files
[INFO] generating user layers
[INFO] generating kconfig for Rootfs
[INFO] silentconfig rootfs
[INFO] generating petalinux-user-image.bb
INFO: bitbake petalinux-user-image
WARNING: Host distribution "debian-10" has not been validated with this version of the build system; you may possibly experience unexpected failures. It is recommended that you use a tested distribution.
Parsing recipes: 100% |#######################################################################| Time: 0:03:35
Parsing of 2777 .bb files complete (0 cached, 2777 parsed). 3812 targets, 162 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
Initialising tasks: 100% |####################################################################| Time: 0:00:08
Checking sstate mirror object availability: 100% |############################################| Time: 0:00:15
Sstate summary: Wanted 890 Found 683 Missed 414 Current 0 (76% match, 0% complete)
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
NOTE: Tasks Summary: Attempted 3233 tasks of which 2251 didn't need to be rerun and all succeeded.

Summary: There was 1 WARNING message shown.
INFO: Copying Images from deploy to images
INFO: Creating images/linux directory
NOTE: Failed to copy built images to tftp dir:  /tftpboot
[INFO] successfully built project
```

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15).3.2: Type to boot:

**petalinux-boot --qemu --kernel**

Step [#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15).3.2: Logged in with a user name of **root** and a password of **root** 

**Reference** 

The Xilinx graphic is from [[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)] 