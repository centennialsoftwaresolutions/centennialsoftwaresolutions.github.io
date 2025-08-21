# Boost Hello, World on a ZCU102

![Boost_xilinx_logo](Boost_xilinx_logo.png)

This post shows how to compile and install Boost, compile the Boost "Hello, World!" project using the Xilinx SDK aarch64 toolchain, and run it on a ZCU102.

**<u><span># Prerequisites</span></u>**

-   Xilinx 2019.1 SDK installed in **/home/demo/xsdk/**
    
-   A ZCU102 + Cables
    
-   Running Ubuntu 16.04.5
    
-   A Xilinx account to get PetaLinux 2019.1 and the PetaLinux 2019.1 ZCU102 BSP
    

**<u><span># Get Boost</span></u>**

\# Go to https://boostorg.jfrog.io/ui/native/main/release/1.77.0/source/ 

\# Save boost\_1\_77\_0.tar.bz2 to ~/Downloads

\# Save boost\_1\_77\_0.tar.bz2.json to ~/Downloads

\# Check it

**cat ~/Downloads/boost\_1\_77\_0.tar.bz2.json**

{

"commit": "9d3f9bcd7d416880d4631d7d39cceeb4e8f25da0",

"file": "boost\_1\_77\_0.tar.bz2",

"sha256": "fc9f85fc030e233142908241af7a846e60630aa7388de9a5fafb1f3a26840854"

}

**sha256sum ~/Downloads/boost\_1\_77\_0.tar.bz2**

fc9f85fc030e233142908241af7a846e60630aa7388de9a5fafb1f3a26840854 /home/demo/Downloads/boost\_1\_77\_0.tar.bz2

**<u><span># Extract Boost</span></u>**

**mkdir -p ~/boost\_1\_77\_0** 

**tar -x -C ~/boost\_1\_77\_0 --strip-components=1 -f ~/Downloads/boost\_1\_77\_0.tar.bz2**

\# Check

**ls ~/boost\_1\_77\_0/**

**<u><span># Bootstrap Boost</span></u>**

**cd ~/boost\_1\_77\_0**

**./bootstrap.sh --with-libraries=program\_options,filesystem,thread,coroutine,date\_time,context,timer,system,regex,chrono,test,log,atomic,random,graph,serialization,stacktrace,iostreams**

\# You should see amongst the output: \# Bootstrapping is done. To build, run:

**echo 'using gcc : aarch64 : aarch64-linux-gnu-g++ ;' > ~/user-config.jam**

**export PATH=/home/demo/xsdk/SDK/2019.1/gnu/aarch64/lin/aarch64-linux/bin/:$PATH**

**./b2 -j8 toolset=gcc-aarch64 architecture=arm address-model=64 target-os=linux**

\# This ^^^ can take some time

\# Note the output:

\# The Boost C++ Libraries were successfully built!

\# The following directory should be added to compiler include paths:

\# /home/demo/boost\_1\_77\_0

\# The following directory should be added to linker library paths:

\# /home/demo/boost\_1\_77\_0/stage/lib

**mkdir ~/boost\_1\_77\_0\_install**

\# Install to a different directory

**./b2 -j32 install toolset=gcc-aarch64 --prefix=/home/demo/boost\_1\_77\_0\_install link=shared threading=multi runtime-link=shared architecture=arm address-model=64 target-os=linux**

**<u><span># Compile Hello, World</span></u>**

**cd ~/boost\_1\_77\_0/tools/build/example/hello/** 

**cd ..** 

**cd hello\_arm64/** 

**~/boost\_1\_77\_0/b2 toolset=gcc-aarch64 target-os=linux**

\# You should see: 

\# ...found 8 targets... 

\#...updating 5 targets... 

\# gcc.compile.c++ bin/gcc-aarch64/debug/hello.o 

\# gcc.link bin/gcc-aarch64/debug/hello 

#...updated 5 targets...

**readlink -f bin/gcc-aarch64/debug/hello** 

\# /home/demo/boost\_1\_77\_0/tools/build/example/hello\_arm64/bin/gcc-aarch64/debug/hello

**<u><span># Install PetaLinux Locally and Do a Build</span></u>**

\# Download and copy petalinux-v2019.1-final-installer.run to ~/Downloads

\# Download and copy xilinx-zcu102-v2019.1-final.bsp to ~/Downoads

**mkdir -p $HOME/petalinux**

**cd ~/Downloads**

**./petalinux-v2019.1-final-installer.run $HOME/petalinux/2019.1**

**mkdir -p ~/plxprjs**

**cd ~/plxprjs**

**source ~/petalinux/2019.1/settings.sh**

**petalinux-create -t project -s ~/Downloads/xilinx-zcu102-v2019.1-final.bsp**

**cd xilinx-zcu102-2019.1**

**petalinux-build**

**petalinux-boot --qemu --kernel**

[#Type](https://www.centennialsoftwaresolutions.com/blog/hashtags/Type) Ctrl-a x to exit QEMU

**<u><span># Test Boost Hello, World on a ZCU102</span></u>**

\# Insert an SD Card (there are better ways to do this, but this method works without minimal set up)

**cp ~/boost\_1\_77\_0/tools/build/example/hello\_arm64/bin/gcc-aarch64/debug/hello /media/demo/BDFD-EDD6/**

**cp ~/xsdk/SDK/2019.1/gnu/aarch64/lin/aarch64-linux/aarch64-linux-gnu/lib64/\* /media/demo/BDFD-EDD6/**

\# Plug the SD Card into a ZCU102

\# Connect a cable from the ZCU102's USB JTAG and a cable from ZCU102's USB UART

\# Set the ZCU102 to JTAG mode (Set all the switches on SW6 towards "ON C&K SDA04"

\# Turn on the ZCU102

\# Open another terminal and run

**screen /dev/ttyUSB0 115200**

\# In the original terminal

**cd ~/plxprjs/xilinx-zcu102-2019.1** **source ~/petalinux/2020.1/settings.sh** **petalinux-boot --jtag --kernel -v**

\# Or if you have a SmartLynq, you can download more quickly:

**petalinux-boot --jtag --kernel -v --hw\_server-url 10.0.0.2:3121**

At the prompt (user: root, password: root):

**LD\_LIBRARY\_PATH=/run/media/mmcblk0p1/ /run/media/mmcblk0p1/hello**

\# You'll see: \# Hello!

**<u><span># References</span></u>**

-   [<u><span>https://www.boost.org/doc/libs/1_77_0/more/getting_started/index.html</span></u>](https://www.boost.org/doc/libs/1_77_0/more/getting_started/index.html)
    
-   [<u><span>https://www.boost.org/doc/libs/1_77_0/tools/build/doc/html/index.html</span></u>](https://www.boost.org/doc/libs/1_77_0/tools/build/doc/html/index.html)
    
-   [<u><span>https://www.boost.org/build/doc/html/bbv2/tasks/crosscompile.html</span></u>](https://www.boost.org/build/doc/html/bbv2/tasks/crosscompile.html)
    
-   Xilinx logo from [<u><span>https://www.xilinx.com/etc.clientlibs/site/clientlibs/xilinx/site-all/resources/imgs/header/xilinx-header-logo.svg</span></u>](https://www.xilinx.com/etc.clientlibs/site/clientlibs/xilinx/site-all/resources/imgs/header/xilinx-header-logo.svg)
    
-   Boost logo from [<u><span>https://www.boost.org/</span></u>](https://www.boost.org/)