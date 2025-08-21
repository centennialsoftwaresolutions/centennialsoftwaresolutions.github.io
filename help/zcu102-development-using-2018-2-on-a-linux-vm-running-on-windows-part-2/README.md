# ZCU102 Development Using 2018.2 on a Linux VM Running on Windows: Part 2

![xilinx_logo_1](xilinx_logo_1.png)

This post is part 2 of a series that contains everything you need to develop software for the ZCU102 using a Linux VM running on Windows 7.

Part 1 @ \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/zcu102-development-using-2018-2-on-a-linux-vm-running-on-windows)\] Covered:

-   The steps for installing an Ubuntu 16.04.3 ISO on a Oracle VirualBox VM and
    
-   Installing Xilinx Vivado 2018.2
    

Part 2 Covers:

-   Installing PetaLinux 2018.2 onto the Ubuntu 16.04.3 VM,
    
-   Building a custom image for the ZCU102's A53 cores and
    
-   Running the image on to the board over JTAG
    

**<u><span>Before you Continue</span></u>**

If you haven't completed part 1, please complete it @ \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/zcu102-development-using-2018-2-on-a-linux-vm-running-on-windows)\].

**<u><span>Machine</span></u>**

All of these commands were run in a VM that was running on Windows 7 SP1 running on a T460. See \[[<u><span>link</span></u>](http://www.zachpfeffer.com/single-post/2017/01/28/New-T460-System-Information)\] for more details.

**<u><span>Installing PetaLinux</span></u>**

1\. Type **sudo mkdir -p /opt/pkg/petalinux**

2\. Type **sudo chmod -R a+rwX /opt/pkg/petalinux**

3\. Type **sudo chown -R zpfeffer:zpfeffer /opt/pkg/petalinux**

4\. Type **cd ~/xpkgs**

5\. Type **./petalinux-v2018.2-final-installer.run /opt/pkg/petalinux**

**Note:** Step **5** will display:

**INFO: Checking installer checksum...** for a few minutes, then display:

**INFO: Extracting PetaLinux installer...** for a few minutes, then display:

```
LICENSE AGREEMENTS

PetaLinux SDK contains software from a number of sources.  Please review
the following licenses and indicate your acceptance of each to continue.

You do not have to accept the licenses, however if you do not then you may 
not use PetaLinux SDK.

Use PgUp/PgDn to navigate the license viewer, and press 'q' to close

Press Enter to display the license agreements
```

6\. Press **Enter**

7\. Press **PgDn** (or press **G** to skip to the end) and press **q**

8\. At **Do you accept Xilinx End User License Agreement? \[y/N\] >** type **y**

**Note:** at this point you should be presented with the **WebTalk Terms and Conditions**

8\. Press **q**

9\. At the **Do you accept Webtalk Terms and Conditions? \[y/N\] >** type **y**

**Note**: at this point you should be presented with the **Third\_Party\_Software\_End\_User\_License\_Agreement**

10\. Press **PgDn** (or press **G** to skip to the end) and press **q**

11\. At the **Do you accept Third Party End User License Agreement? \[y/N\] >** type **y**

**Note:** at this point you'll see:

```
INFO: Checking installation environment requirements...
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution
INFO: Installing PetaLinux...
```

...for a few minutes. Then **INFO: Checking PetaLinux installer integrity...** and **INFO: Installing PetaLinux SDK to "/opt/pkg/petalinux/."** followed by

```
................................................................................................................................................................................................................................................................................INFO: Installing aarch64 Yocto SDK to "/opt/pkg/petalinux/./components/yocto/source/aarch64"...
PetaLinux Extensible SDK installer version 2018.2
=================================================
You are about to install the SDK to "/opt/pkg/petalinux/components/yocto/source/aarch64". Proceed[Y/n]? Y
Extracting SDK................................done
Setting it up...
Extracting buildtools...
done
SDK has been successfully set up and is ready to be used.
Each time you wish to use the SDK in a new shell session, you need to source the environment setup script e.g.
 $ . /opt/pkg/petalinux/components/yocto/source/aarch64/environment-setup-aarch64-xilinx-linux
INFO: Installing arm Yocto SDK to "/opt/pkg/petalinux/./components/yocto/source/arm"...
PetaLinux Extensible SDK installer version 2018.2
=================================================
You are about to install the SDK to "/opt/pkg/petalinux/components/yocto/source/arm". Proceed[Y/n]? Y
Extracting SDK..............................done
Setting it up...
Extracting buildtools...
done
SDK has been successfully set up and is ready to be used.
Each time you wish to use the SDK in a new shell session, you need to source the environment setup script e.g.
 $ . /opt/pkg/petalinux/components/yocto/source/arm/environment-setup-cortexa9hf-neon-xilinx-linux-gnueabi
INFO: Installing microblaze_full Yocto SDK to "/opt/pkg/petalinux/./components/yocto/source/microblaze_full"...
PetaLinux Extensible SDK installer version 2018.2
=================================================
You are about to install the SDK to "/opt/pkg/petalinux/components/yocto/source/microblaze_full". Proceed[Y/n]? Y
Extracting SDK.............................done
Setting it up...
Extracting buildtools...
done
SDK has been successfully set up and is ready to be used.
Each time you wish to use the SDK in a new shell session, you need to source the environment setup script e.g.
 $ . /opt/pkg/petalinux/components/yocto/source/microblaze_full/environment-setup-microblazeel-v10.0-bs-cmp-re-mh-div-xilinx-linux
INFO: Installing microblaze_lite Yocto SDK to "/opt/pkg/petalinux/./components/yocto/source/microblaze_lite"...
PetaLinux Extensible SDK installer version 2018.2
=================================================
You are about to install the SDK to "/opt/pkg/petalinux/components/yocto/source/microblaze_lite". Proceed[Y/n]? Y
Extracting SDK.............................done
Setting it up...
Extracting buildtools...
done
SDK has been successfully set up and is ready to be used.
Each time you wish to use the SDK in a new shell session, you need to source the environment setup script e.g.
 $ . /opt/pkg/petalinux/components/yocto/source/microblaze_lite/environment-setup-microblazeel-v10.0-bs-cmp-re-ml-xilinx-linux
INFO: PetaLinux SDK has been installed to /opt/pkg/petalinux/.
```

You have succeeded if the last line reads **INFO: PetaLinux SDK has been installed to /opt/pkg/petalinux/.**

**<u><span>Change /bin/sh to bash</span></u>**

PetaLinux Tools 2018.2 requires /bin/sh to point to bash. Ubuntu 2018.2 points /bin/sh points to dash:

To change /bin/sh to bash:

```
zpfeffer@z:~/share/r20170427/aoctrl$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 Aug  3 22:12 /bin/sh -> dash
```

1\. Type **sudo ln -sf bash /bin/sh**

2\. Test it by typing **ls -l /bin/sh**

You should see:

```
zpfeffer@z:~/share/r20170427/aoctrl$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 Sep  6 14:48 /bin/sh -> bash
```

**Notes**

1\. You can reverse this by typing **sudo ln -sf dash /bin/sh**

2\. If you don't do this, PetaLinux Tools will output this in the next step:

```
zpfeffer@z:~/share/r20170427/aoctrl$ source /opt/pkg/petalinux/settings.sh 
PetaLinux environment set to '/opt/pkg/petalinux'
WARNING: /bin/sh is not bash! 
bash is PetaLinux recommended shell. Please set your default shell to bash.
```

**<u><span>Run PetaLinux</span></u>**

1\. Open a new terminal

2\. Type **source /opt/pkg/petalinux/settings.sh**

3\. You should see:

```
zpfeffer@z:~$ source /opt/pkg/petalinux/settings.sh 
PetaLinux environment set to '/opt/pkg/petalinux'
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution
```

**Changes to the Environment**

Here were the environment differences I saw. I also listed how I generated the differences:

```
zpfeffer@z:~$ env > env.before
zpfeffer@z:~$ source /opt/pkg/petalinux/settings.sh
PetaLinux environment set to '/opt/pkg/petalinux'
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution
zpfeffer@z:~$ env > env.after
zpfeffer@z:~$ diff -u env.before env.after 
--- env.before	2018-09-06 15:34:25.370000000 -0600
+++ env.after	2018-09-06 15:35:03.530000000 -0600
@@ -16,13 +16,14 @@
 USER=zpfeffer
 LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
 QT_ACCESSIBILITY=1
+PETALINUX_VER=2018.2
 XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
 XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
 SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
 SESSION_MANAGER=local/z:@/tmp/.ICE-unix/1589,unix/z:/tmp/.ICE-unix/1589
 DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path
 XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/usr/share/upstart/xdg:/etc/xdg
-PATH=/home/zpfeffer/bin:/home/zpfeffer/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
+PATH=/opt/pkg/petalinux/tools/linux-i386/petalinux/bin:/opt/pkg/petalinux/tools/common/petalinux/bin:/opt/pkg/petalinux/tools/linux-i386/gcc-arm-none-eabi-r5/bin:/opt/pkg/petalinux/tools/linux-i386/microblaze-xilinx-elf/bin:/opt/pkg/petalinux/tools/linux-i386/microblazeel-xilinx-linux-gnu/bin:/opt/pkg/petalinux/tools/linux-i386/gcc-arm-none-eabi/bin:/opt/pkg/petalinux/tools/linux-i386/gcc-arm-linux-gnueabi/bin:/opt/pkg/petalinux/tools/linux-i386/aarch64-none-elf/bin:/opt/pkg/petalinux/tools/linux-i386/aarch64-linux-gnu/bin:/home/zpfeffer/bin:/home/zpfeffer/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
 DESKTOP_SESSION=ubuntu
 QT_IM_MODULE=ibus
 QT_QPA_PLATFORMTHEME=appmenu-qt5
@@ -45,6 +46,7 @@
 LANGUAGE=en_US
 LIBGL_ALWAYS_SOFTWARE=1
 GNOME_DESKTOP_SESSION_ID=this-is-deprecated
+PETALINUX=/opt/pkg/petalinux
 XDG_SESSION_DESKTOP=ubuntu
 LOGNAME=zpfeffer
 QT4_IM_MODULE=xim
```

**Summary of env Changes**

<u><span>Variables Added</span></u>:

PETALINUX\_VER=2018.2

PETALINUX=/opt/pkg/petalinux

<u><span>Paths added (listed in order)</span></u>:

/opt/pkg/petalinux/tools/linux-i386/petalinux/bin

/opt/pkg/petalinux/tools/common/petalinux/bin

/opt/pkg/petalinux/tools/linux-i386/gcc-arm-none-eabi-r5/bin

/opt/pkg/petalinux/tools/linux-i386/microblaze-xilinx-elf/bin

/opt/pkg/petalinux/tools/linux-i386/microblazeel-xilinx-linux-gnu/bin

/opt/pkg/petalinux/tools/linux-i386/gcc-arm-none-eabi/bin

/opt/pkg/petalinux/tools/linux-i386/gcc-arm-linux-gnueabi/bin

/opt/pkg/petalinux/tools/linux-i386/aarch64-none-elf/bin

/opt/pkg/petalinux/tools/linux-i386/aarch64-linux-gnu/bin

**<u><span>Create a PetaLinux Tools Project Based on the 2018.2 ZCU102 BSP</span></u>**

1\. Type **mkdir ~/plxprjs**

2\. Type **cd ~/plxprjs/**

**Note:** You can create more projects in this directory, i.e. you'll cd into ~/plxprjs/ and type other petalinux-create for other projects.

3\. Type **petalinux-create -t project -s ~/xpkgs/xilinx-zcu102-v2018.2-final.bsp**

You'll see:

```
zpfeffer@z:~/plxprjs$ petalinux-create -t project -s ~/xpkgs/xilinx-zcu102-v2018.2-final.bsp 
INFO: Create project: 
INFO: Projects: 
INFO: 	* xilinx-zcu102-2018.2
INFO: has been successfully installed to /home/zpfeffer/plxprjs/
INFO: New project successfully created in /home/zpfeffer/plxprjs/
```

**How Long?**

On my machine the command took a little over 2 min:

```
zpfeffer@z:~/plxprjs$ time petalinux-create -t project -s ~/xpkgs/xilinx-zcu102-v2018.2-final.bsp
INFO: Create project: 
INFO: Projects: 
INFO: 	* xilinx-zcu102-2018.2
INFO: has been successfully installed to /home/zpfeffer/plxprjs/
INFO: New project successfully created in /home/zpfeffer/plxprjs/

real	2m27.683s
user	0m20.520s
sys	0m3.300s
```

**<u><span>Create Another Project</span></u>**

To try out creating another project in the same directory type **petalinux-create -t project -s ~/xpkgs/xilinx-zcu102-v2018.2-final.bsp -n alt\_xilinx-zcu102-v2018.2-final** in **~/plxprjs**

You'll see:

```
zpfeffer@z:~/plxprjs$ petalinux-create -t project -s ~/xpkgs/xilinx-zcu102-v2018.2-final.bsp -n alt_xilinx-zcu102-v2018.2-final
INFO: Create project: alt_xilinx-zcu102-v2018.2-final
INFO: New project successfully created in /home/zpfeffer/plxprjs/alt_xilinx-zcu102-v2018.2-final
zpfeffer@z:~/plxprjs$ ls
alt_xilinx-zcu102-v2018.2-final  xilinx-zcu102-2018.2
```

Just type **rm -rf alt\_xilinx-zcu102-v2018.2-final/** to delete it. The other project will not be impacted.

**<u><span>Build the Project</span></u>**

1\. Type **cd xilinx-zcu102-2018.2/**

2\. Type **petalinux-build**

You'll see:

```
zpfeffer@z:~/plxprjs/xilinx-zcu102-2018.2$ time petalinux-build 
[INFO] building project
[INFO] generating Kconfig for project
                                                                                
[INFO] oldconfig project
[INFO] sourcing bitbake
[INFO] generating plnxtool conf
[INFO] generating meta-plnx-generated layer
[INFO] generating bbappends for project . This may take time ! 
[INFO] generating u-boot configuration files
                                                                                
[INFO] generating kernel configuration files
[INFO] generating kconfig for Rootfs
[INFO] oldconfig rootfs
[INFO] generating petalinux-user-image.bb
INFO: bitbake petalinux-user-image
Loading cache: 100% |############################################| Time: 0:00:11
Loaded 3439 entries from dependency cache.
Parsing recipes: 100% |##########################################| Time: 0:01:45
Parsing of 2552 .bb files complete (2509 cached, 43 parsed). 3441 targets, 138 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
Initialising tasks: 100% |#######################################| Time: 0:01:21
Checking sstate mirror object availability: 100% |###############| Time: 0:01:09
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
WARNING: petalinux-user-image-1.0-r0 do_rootfs: [log_check] petalinux-user-image: found 1 warning message in the logfile:
[log_check] warning: %post(sysvinit-inittab-2.88dsf-r10.zcu102_zynqmp) scriptlet failed, exit status 1

NOTE: fsbl: compiling from external source tree /opt/pkg/petalinux/tools/hsm/data/embeddedsw
NOTE: pmu-firmware: compiling from external source tree /opt/pkg/petalinux/tools/hsm/data/embeddedsw
NOTE: Tasks Summary: Attempted 3149 tasks of which 2259 didn't need to be rerun and all succeeded.

Summary: There was 1 WARNING message shown.
INFO: Copying Images from deploy to images
INFO: Creating images/linux directory
NOTE: Failed to copy built images to tftp dir:  /tftpboot
[INFO] successfully built project

real	360m34.774s
user	0m45.960s
sys	0m2.576s
```

**How Long?**

On my machine the command took **over 6 hours** (see previous output)

**Build Warning**

The build warning **warning: %post(sysvinit-inittab-2.88dsf-r10.zcu102\_zynqmp) scriptlet failed** has been fully explored at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/analysis-of-warning-post-sysvinit-inittab-2-88dsf-r10-zcu102_zynqmp-scriptlet-failed)\]. It can be ignored.

**<u><span>Boot the Build</span></u>**

**Connect to JTAG**

See <u><span>Connecting Vivado to Digilent's USB-to-JTAG through VirtualBox</span></u> at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/connecting-vivado-to-digilent-s-usb-to-jtag-through-virtualbox)\] to connect to JTAG.

**Bring up Minicom**

See <u><span>Arg! Nothing I type shows up in the Minicom console!</span></u> at \[[<u><span>link</span></u>](http://www.zachpfeffer.com/single-post/Arg-Nothing-I-type-shows-up-in-the-Minicom-console)\]

**Boot**

1\. Type **petalinux-boot --jtag --u-boot -v**

**<u><span>References</span></u>**

-   <u><span>PetaLinux Tools Documentation: Reference Guide, UG1144 (v2018.2) June 6, 2018</span></u> at \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug1144-petalinux-tools-reference-guide.pdf)\]
    
-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]
    
-   <u><span>Free Online HTML Escape / Unescape Tool - </span></u> [<u><span>FreeFormatter.com</span></u>](http://freeformatter.com/) at \[[<u><span>link</span></u>](https://www.freeformatter.com/html-escape.html)\]
    
-   <u><span>Effective Linux Development Using PetaLinux Tools 2017.4</span></u> at \[[<u><span>link</span></u>](https://www.slideshare.net/ZachPfeffer/effective-linux-development-using-petalinux-tools-20174)\]
    
-   <u><span>ZCU102 Board User Guide (UG1182)</span></u> at \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/boards_and_kits/zcu102/ug1182-zcu102-eval-bd.pdf)\]
    
-   Many Xilinx Zynq UltraScale+ MPSoC ZCU102 Docs at \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation-navigation/design-hubs/dh0048-zcu102-evaluation-kit-hub.html)\]
    
-   <u><span>HTML Table Generator</span></u> at \[[<u><span>link</span></u>](https://www.tablesgenerator.com/html_tables)\]
    
-   ZCU102 BOM (zcu102-bom-rdf0404.zip) at \[[<u><span>link</span></u>](https://www.xilinx.com/member/forms/download/design-license.html?cid=473392&filename=zcu102-bom-rdf0404.zip)\] (sign-in required)
    
-   ZCU102 Board Schematics (zcu102-schematic-source-rdf0403.zip) at \[[<u><span>link</span></u>](https://www.xilinx.com/member/forms/download/design-license.html?cid=473360&filename=zcu102-schematic-source-rdf0403.zip)\] (sign-in required)
    
-   <u><span>ZCU102 Software Install and Board Setup</span></u> released June 2018 at \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/boards_and_kits/zcu102/2018_2/xtp435-zcu102-setup-c-2018-2.pdf)\]
    

**<u><span>Other</span></u>**

**Try to Build Outside a Project**

**Note:** if you type **petalinux-build** in the **~/plxprjs** directory you'll see:

```
zpfeffer@z:~/plxprjs$ petalinux-build
ERROR: You are not inside a PetaLinux project. Please specify a PetaLinux project!
Builds the project or the specified components.

Usage:
  petalinux-build [options]

Required:

Options:
  -h, --help                         show function usage
  -p, --project             path to PetaLinux SDK project.
                                     Default is working project.
  -c, --component         Specify the component
                                     it will build the specified component and its dependencies
                                     E.g. -c rootfs
                                     E.g. -c myapp
  -x, --execute    Specify a bitbake task of the component
				     To know the list tasks for a component:
				     E.g. -x do_listtasks
  -f, --force			     Force run a specific task ignoring the stamps
				     Force run has to be for a component or its tasks
				     E.g. -c myapp -f
				     E.g. -c myapp -x compile -f
  -v, --verbose                      Show compile messages verbose mode
  -s, --sdk                          Build SDK ==> do_populate_sdk
  -b, --buildfile  <.bb recipe>      Execute tasks from a specific .bb recipe directly.
				     WARNING: Does not handle any dependencies from other recipes.
```