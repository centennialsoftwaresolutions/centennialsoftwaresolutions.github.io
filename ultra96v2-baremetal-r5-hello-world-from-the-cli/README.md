# Ultra96-V2: Bare-Metal R5 "Hello World" From the CLI

![xilinx_logo](xilinx_logo.png)

This post describes how to boot a "Hello World" application on the Ultra96v2's R5 processor over JTAG. The Xilinx Software Commandline Tool (XSCT) is used to allow this entire process to be done from the command line.

## Notes

A few variables will be used throughout the tutorial. Make sure to replace these with your own unique values.

-   <project\_name>: A name for your Vivado project
    
-   <project\_folder>: A folder you want to store your project in
    
-   <xilinx\_tools>: The folder you installed your Xilinx tools into
    
    ​	    Windows Default: C:/Xilinx
    
    ​	    Linux Default: /tools/xilinx

Another thing to be careful about is about using spaces in your <project\_name> and <project\_folder>. This can sometimes break Vivado and SDK.

If you are working through this tutorial on Windows, you want to make sure to use / as you directory seperater instead of \\. I've found the Xilinx tools to be picky about this.

## Prereqs

### Tutorials

This tutorial is a continuation of our "Ultra96v2: Booting a Baremetal Hello World on the A53 from the CLI" tutorial.

### Hardware

To run through this and subsequent tutorials, you will need some hardware.

-   Ultra96v2 ([AES-ULTRA96-V2-G](https://www.avnet.com/shop/us/products/avnet-engineering-services/aes-ultra96-v2-g-3074457345638646173/?aka_re=1))
    
-   Ultra96 USB-to-JTAG/UART Pod ([AES-ACC-U96-JTAG](https://www.avnet.com/shop/us/products/avnet-engineering-services/aes-acc-u96-jtag-3074457345635355958/))
    
-   96Boards/Ultra96 compliant power supply kit ([AES-ACC-U96-4APWR](https://www.avnet.com/shop/emea/products/avnet-engineering-services/aes-acc-u96-4apwr-3074457345636156710/))
    

## Software

To run through this and subsequent tutorials, you will need some software.

-   A Xilinx Vivado 2019.1 install
    
-   A Xilinx SDK 2019.1 install
    

## Tutorial

### Launch Hardware Server

Once we finish setting up our project we will want to run it on a device. We will need to launch Xilinx Hardware Server to do this. Let's do thin now.

To launch hardware server run the following from a shell prompt:

<xilinx\_tools>/SDK/bin/hw\_server

### Launching XSCT (Xilinx Software Comandline Tool)

We will now launch XSCT. XSCT allows us to run and control SDK without the GUI.

## Windows

To launch XSCT on Windows we will run the batch script. This can either be opened from the file explorer or run from a command prompt.

<xilinx\_tools>/SDK/2019.1/bin/xsct.bat

## Linux

To launch XSCT on Linux we will run the xsct binary.

<xilinx\_tools>/SDK/2019.1/bin/xsct

For the rest of the tutorial, unless specified, all of the commands will be run in xsct

### Creating a Board Support Package (BSP)

We will now create a BSP for our device. This will allow us to create applications targeting the R5 processing system of the Zynq UltraScale+ MPSoC.

createbsp -name standalone_bsp_1 -proc psu_cortexr5_0 -hwproject hw_platform_0

The default BSP has the uart output configured for psu_uart_0 instead of psu_uart_1. In order to see output, we have to change this setting.

configbsp -bsp standalone_bsp_1 -append stdin "psu_uart_1" configbsp -bsp standalone_bsp_1 -append stdout "psu_uart_1"

To save these changed, we have to update the bsp's mss file.

updatemss -mss standalone_bsp_1/system.mss

### Creating an Application Project

Now that our BSP in created, we can use it to target a example application at the R5. We will now create a example "Hello World" application.

createapp -name Hello\_Ultra96\_r5 -app "Hello World" -bsp standalone\_bsp\_1 -hwproject hw\_platform\_0 -lang "c" -proc psu\_cortexr5\_0

Note

The lang parameter selects the target language for the example project. Valid options for this are c and c++.

### Fixing Broken UART

When targetting Ultra96v2 board, xsct sets a incorrect parameter in the xparameters.h header file which prevents the UART from working correct.

To fix this, we need to change a couple of values.

In <project\_folder>/<project\_name>.sdk/standalone\_bsp\_1/psu\_cortexr5\_0/include/xparameters.h, change the lines

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) STDIN\_BASEADDRESS 0xFF000000 

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) STDOUT\_BASEADDRESS 0xFF000000

to

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) STDIN\_BASEADDRESS 0xFF010000 

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) STDOUT\_BASEADDRESS 0xFF010000

### Build all Projects

Before programming the Ultra96v2, we will need to build everything we have created.

To run a build:

projects -build

### Connect to Hardware Server

Now we need to connect to the hardware server instance that we launched earlier.

connect

To connect to a hardware server instance on another machine, use

connect -host <host name/ip> -port <port num>

### Reset the System

Now we will reset the Ultra96v2 board to a clean slate.

\# load the Zynq US+ utilities into the working environment source <xilinx\_tools>/SDK/2019.1/scripts/sdk/util/zynqmp\_utils.tcl \# set our jtag device to point to the APU targets -set -nocase -filter {name =~"APU\*" && jtag\_cable\_name =~ "Avnet USB-to-JTAG/UART Pod V1 1234-oj1A"} -index 1 \# reset the system rst -system \# wait 3 seconds before proceeding after 3000

### Connecting to The Serial Terminal

Before we program the "Hello World" program on the R5, we want to open our serial terminal.

Connect your serial terminal to the Ultra96v2 UART. Settings: Baud rate: 115200

### Programming the R5

Now we will program the R5.

\# set our jtag target to be the RPU

targets -nocase -filter {name =~"RPU*" && jtag_cable_name =~ "Avnet USB-to-JTAG/UART Pod V1 1234-oj1A"} -index 1

\# enable split mode

enable_split_mode

\# set our jtag target to be the APU

targets -set -nocase -filter {name =~"APU*" && jtag_cable_name =~ "Avnet USB-to-JTAG/UART Pod V1 1234-oj1A"} -index 1

\# load the Vivado hardware design and set the memory map for the APU jtag target

loadhw -hw hw_platform_0/system.hdf -mem-ranges [list {0x80000000 0xbfffffff} {0x400000000 0x5ffffffff} {0x1000000000 0x7fffffffff}]

\# disable memory access protection for dow, mrd and mwr commands

configparams force-mem-access 1

\# set our jtag target to point to the APU

targets -set -nocase -filter {name =~"APU*" && jtag_cable_name =~ "Avnet USB-to-JTAG/UART Pod V1 1234-oj1A"} -index 1

\# load the psu_init tcl into our working environment

source hw_platform_0/psu_init.tcl

\# initalize the A53 CPU

psu_init

\# load the fsbl tcl into our working environment

source <xilinx_tools>/SDK/2019.1/scripts/sdk/util/fsbl.tcl

\# wait for 1 sec

after 1000

\# Send a PL power up request to the PMU

psu_ps_pl_isolation_removal

\# wait for 1 sec

after 1000

psu_ps_pl_reset_config

catch {psu_protection}

\# set our jtag target to core 0 of the R5 processor

targets -set -nocase -filter {name =~"*R5*0" && jtag_cable_name =~ "Avnet USB-to-JTAG/UART Pod V1 1234-oj1A"} -index 1

\# reset the processor

rst -processor

\# wait for fsbl to complete

catch {XFsbl_TcmEccInit R5_0}

\# download our compiled "Hello World" application

dow Hello_Ultra96_r5/Debug/Hello_Ultra96_r5.elf

\# turn memory access protection back on

configparams force-mem-access 0

\# set our jtag target to core 0 of the A53 processor

targets -set -nocase -filter {name =~"*A53*0" && jtag_cable_name =~ "Avnet USB-to-JTAG/UART Pod V1 1234-oj1A"} -index 1

\# run the Hello World application

con

### Result

You should see the text "Hello World" outputted on you serial terminal.