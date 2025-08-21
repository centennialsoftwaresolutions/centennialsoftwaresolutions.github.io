# Add an embeddedsw Driver to a 2019.1 BSP From the Command Line

![Xilinx_logo](Xilinx_logo.png)

This post demonstrates how you can manually add an **embeddedsw** driver to an XSDK FSBL BSP.

**<u><span>Steps</span></u>**

XP=~/xsdk/SDK/2019.1

WS=~/plxprjs/testfsbl

HD=~/plxprjs/xilinx-zcu102-2019.1/project-spec/hw-description/system.hdf

\# Create the workspace directory

mkdir -p $WS

\# Create HW from the HDF

$XP/bin/xsct -eval "setws $WS; createhw -name hw0 -hwspec $HD"

\# Create the FSBL

$XP/bin/xsct -eval "setws $WS; createapp -name fsbl -app {Zynq MP FSBL} -proc psu\_cortexa53\_0 -hwproject hw0 -os standalone"

\# Build the FSBL

$XP/bin/xsct -eval "setws $WS; projects -build"

\# Copy the driver into the right directory

cp -R $XP/data/embeddedsw/XilinxProcessorIPLib/drivers/spi\_v4\_4 $WS/fsbl\_bsp/psu\_cortexa53\_0/libsrc/

\# Build it (you'll see errors)

$XP/bin/xsct -eval "setws $WS; projects -build"

\# Why does this work?

cat $WS/fsbl\_bsp/Makefile

\# BSP\_MAKEFILES := $(wildcard $(PROCESSOR)/libsrc/\*/src/Makefile)

This line ^^^^ simply includes Makefiles that are in the \_right\_ location

**<u><span>Note</span></u>**

You will need to manually set defines for your build. For this example:

\# XPAR\_XSPI\_NUM\_INSTANCES

\# XPAR\_SPI\_0\_DEVICE\_ID

\# XPAR\_SPI\_0\_BASEADDR

\# XPAR\_SPI\_0\_FIFO\_EXIST

\# XPAR\_SPI\_0\_SLAVE\_ONLY

\# XPAR\_SPI\_0\_NUM\_SS\_BITS

\# XPAR\_SPI\_0\_NUM\_TRANSFER\_BITS

\# XPAR\_SPI\_1\_DEVICE\_ID

\# XPAR\_SPI\_1\_BASEADDR

\# XPAR\_SPI\_1\_FIFO\_EXIST

\# XPAR\_SPI\_1\_SLAVE\_ONLY

\# XPAR\_SPI\_1\_NUM\_SS\_BITS

\# XPAR\_SPI\_1\_NUM\_TRANSFER\_BITS

\# Example from design:

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1054:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_DEVICE\_ID 0U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1055:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_BASEADDR 0xA0000000U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1056:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_HIGHADDR 0xA000FFFFU

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1057:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_FIFO\_DEPTH 16U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1058:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_FIFO\_EXIST 1U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1059:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_SPI\_SLAVE\_ONLY 0U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1060:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_NUM\_SS\_BITS 1U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1061

:#define XPAR\_SPI\_0\_NUM\_TRANSFER\_BITS 8U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1062:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_SPI\_MODE 0U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1063:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_TYPE\_OF\_AXI4\_INTERFACE 0U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1064:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_AXI4\_BASEADDR 0U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1065

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_AXI4\_HIGHADDR 0U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1066:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_XIP\_MODE 0U

fsbl\_bsp/psu\_cortexa53\_0/include/xparameters.h:1067:

[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define) XPAR\_SPI\_0\_USE\_STARTUP 0U

**<u><span>Reference</span></u>**

-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]