# Enable socat Using Petainux 2019.1 and Test it on the ZCU102

![Xilinx_logo](Xilinx_logo.png)

- This post shows how to enable socat in a PetaLinux 2019.1 build and test it on the ZCU102. Essential commands are **bolded**.

  **Prereqs**

  \# PetaLinux 2019.1 installed to ~/petalinux/2019.1

  \# Have a ZCU102

  \# Know how to JTAG boot it

  \#

  \# See for instructions on installing and JTAG booting a ZCU102: 

  \# https://www.centennialsoftwaresolutions.com/post/zcu102-development-using-2018-2-on-a-linux-vm-running-on-windows-part-2

  \# …and: 

  \# https://www.centennialsoftwaresolutions.com/post/zcu102-development-using-2018-2-on-a-linux-vm-running-on-windows

  **Steps**

  \# Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Download the 2019.1 ZCU102 BSP from:

  https://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-zcu102-v2019.1-final.bsp

  to:

  ~/Downloads

  \# Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): 

  **mkdir ~/plxbsps**

  **cd ~/plxbsps**

  **cp ~/Downloads/xilinx-zcu102-v2019.1-final.bsp .**

  **md5sum xilinx-zcu102-v2019.1-final.bsp**

  \# You should see:

  \# 2189911c4ac9c33f170cdced96472ba7 xilinx-zcu102-v2019.1-final.bsp

  **rm ~/Downloads/xilinx-zcu102-v2019.1-final.bsp**

  \# Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3):

  **mkdir ~/plxprjs**

  **cd ~/plxprjs/**

  **source ~/petalinux/2019.1/settings.sh**

  \# You should see:

  \# PetaLinux environment set to '/home/demo/petalinux/2019.1'

  \# INFO: Checking free disk space

  \# INFO: Checking installed tools

  \# INFO: Checking installed development libraries

  \# INFO: Checking network and other services

  \# WARNING: No tftp server found - please refer to "PetaLinux SDK Installation Guide" for its impact and solution

  **petalinux-create -t project -s ~/plxbsps/xilinx-zcu102-v2019.1-final.bsp** **cd xilinx-zcu102-2019.1/**

  **petalinux-build**

  \# The last line should be:

  \# [INFO] successfully built project

  \# Do a test boot

  \# Turn the board on in JTAG boot mode, etc.

  \# Start COM port a.k.a. start serial port

  screen /dev/ttyUSB0 115200

  \# use Ctrl-a d to detach 

  \# Use to find the PID (the second number): 

  \# ps aux | grep USB 

  \# Use to reattach

  \# screen -x 78434

  \# Boot with USB JTAG 

  petalinux-boot --jtag --kernel -v

  \# Or SmartLynq (5x faster observed empirically)

  petalinux-boot --jtag --kernel -v --hw_server-url 10.0.0.2:3121

  \# In the com port you should see a log in prompt

  \# Use root for the username and root for the password 

  [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4) Enable socat

  **cd ~/plxprjs/xilinx-zcu102-2019.1**

  **vi ~/plxprjs/xilinx-zcu102-2019.1/project-spec/meta-user/recipes-core/images/petalinux-image-full.bbappend**

  **# Add**

  **# IMAGE_INSTALL_append = " socat"**

  touch start

  **petalinux-config -c rootfs**

  **# Select user packages > [ ] socat** 

  **# Type Y to include, save (accept the default path) and exit.**

  \# The last two lines should be:

  configuration written to /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/configs/rootfs_config

  *** End of the configuration.

  *** Execute 'make' to start the build or try 'make help'.

  [INFO] generating petalinux-user-image.bb

  [INFO] successfully configured rootfs

  [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5) Look at what files changed

  \# Diff

  diff -u /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/configs/rootfs_config.old /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/configs/rootfs_config

  --- /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/configs/rootfs_config.old 2021-05-27 20:25:51.393044501 -0600

  +++ /home/demo/plxprjs/xilinx-zcu102-2019.1/project-spec/configs/rootfs_config 2021-06-14 12:15:39.020369681 -0600

  @@ -562,7 +562,7 @@

   \#

   \# socat 

   \#

  -# CONFIG_socat is not set

  +CONFIG_socat=y

   \# CONFIG_socat-dev is not set

   \# CONFIG_socat-dbg is not set

  \# See files that have changed:

  find . -type f -cnewer start -printf "%T+\t%p\n" | sort

  2021-05-27+20:25:51.3930445010 ./project-spec/configs/rootfs_config.old

  2021-05-27+20:25:51.5047445520 ./build/config.log.old

  2021-06-14+12:14:44.8449248330 ./build/conf/plnxtool.conf

  2021-06-14+12:14:44.9532281830 ./build/misc/plnx-generated/plnxgen.json

  2021-06-14+12:14:46.4477671490 ./build/cache/bb_persist_data.sqlite3

  2021-06-14+12:14:46.5959327960 ./build/conf/bblayers.conf

  2021-06-14+12:14:46.6119507040 ./build/bitbake-cookerdaemon.log

  2021-06-14+12:14:46.7280805360 ./build/misc/rootfs_config/Kconfig.user

  2021-06-14+12:14:46.7561118750 ./build/misc/rootfs_config/Kconfig

  2021-06-14+12:15:39.0203696810 ./project-spec/configs/rootfs_config

  2021-06-14+12:15:39.1000318210 ./project-spec/meta-plnx-generated/recipes-core/images/petalinux-user-image.bb

  2021-06-14+12:15:39.1318966760 ./build/config.log

  2021-06-14+12:15:39.1358797830 ./.petalinux/usage_statistics_token

  2021-06-14+12:15:39.1597784250 ./.petalinux/usage_statistics

  \# Look for socat:

  cat ./build/conf/plnxtool.conf | grep -C3 socat

  cat ./build/misc/plnx-generated/plnxgen.json | grep -C3 socat

  cat ./build/conf/bblayers.conf | grep -C3 socat

  cat ./build/misc/rootfs_config/Kconfig.user | grep -C3 socat

  cat ./build/misc/rootfs_config/Kconfig | grep -C3 socat

  cat ./project-spec/meta-plnx-generated/recipes-core/images/petalinux-user-image.bb | grep -C3 socat

  \# ...or:

  for file in $(find . -type f -cnewer start -printf "%T+\t%p\n" | sort | awk '{print $2}'); do  echo $file; cat $file | grep -C3 socat; done

  ./project-spec/configs/rootfs_config.old

  \# CONFIG_rsync-dbg is not set

  \#

  \# socat 

  \#

  \# CONFIG_socat is not set

  \# CONFIG_socat-dev is not set

  \# CONFIG_socat-dbg is not set

  \#

  \# subversion 

  ./build/config.log.old

  rsync-dev (rsync-dev) [N/y/?] 

  rsync-dbg (rsync-dbg) [N/y/?] 

  *

  \* socat 

  *

  socat (socat) [N/y/?] 

  socat-dev (socat-dev) [N/y/?] 

  socat-dbg (socat-dbg) [N/y/?] 

  *

  \* subversion 

  *

  ./build/conf/plnxtool.conf

  ./build/misc/plnx-generated/plnxgen.json

  ./build/cache/bb_persist_data.sqlite3

  ./build/conf/bblayers.conf

  ./build/bitbake-cookerdaemon.log

  ./build/misc/rootfs_config/Kconfig.user

   

  endmenu

  menu "user packages " 

  config socat 

    bool "socat"

    help

   

  endmenu

  ./build/misc/rootfs_config/Kconfig

    help

   

  endmenu

  menu "socat " 

  config socat 

    bool "socat"

    help

    Multipurpose relay for bidirectional data transfer

   

  config socat-dev 

    bool "socat-dev"

    help

   

  config socat-dbg 

    bool "socat-dbg"

    help

   

  endmenu

  ./project-spec/configs/rootfs_config

  \# CONFIG_rsync-dbg is not set

  \#

  \# socat 

  \#

  CONFIG_socat=y

  \# CONFIG_socat-dev is not set

  \# CONFIG_socat-dbg is not set

  \#

  \# subversion 

  ./project-spec/meta-plnx-generated/recipes-core/images/petalinux-user-image.bb

   mtd-utils \

   canutils \

   openssh-sftp-server \

   socat \

   pciutils \

   run-postinsts \

   udev-extraconf \

  ./build/config.log

  ./.petalinux/usage_statistics_token

  ./.petalinux/usage_statistics

  [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6) Build socat

  touch start2

  **petalinux-build**

  \# See files that have changed:

  find . -type f -cnewer start2 -not -path "./build/*" -printf "%T+\t%p\n" | sort

  find . -type f -cnewer start2 -printf "%T+\t%p\n" | sort | grep socat

  \# Many lines, like:

  \# ./build/tmp/deploy/rpm/aarch64/socat-1.7.3.2-r0.aarch64.rpm

  [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7) Test

  **petalinux-boot --jtag --kernel -v**

  \# or with SmartLynq

  petalinux-boot --jtag --kernel -v --hw_server-url 10.0.0.2:3121

  \# In the console:

  **socat -V**

  \# socat by Gerhard Rieger and contributors - see www.dest-unreach.org

  \# socat version 1.7.3.2 on May 23 2019 01:36:30 

  **References**

  - The Xilinx graphic is from [[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)]