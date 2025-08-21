# How do I run the Xilinx SDK 2019.1 from the command line on Linux?

![xilinx_logo_1](xilinx_logo_1.png)

- This post shows how to run the Xilinx SDK from the command line. It also shows you how to run the SDK in batch mode.

  **Steps**

  Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Open a terminal

  Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Figure out whether you're running csh or bash by typing:

  **ps -p $$**

  You should see something like:

     PID TTY          TIME CMD

    2729 pts/1    00:00:00 bash

  Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Find settings64.sh or settings64.csh

  **find / -name "settings\*sh"**

  You should see something like:

  /tools/Xilinx/SDK/2019.1/settings64.sh

  /tools/Xilinx/SDK/2019.1/settings64.csh

  Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): If you're running bash type:

  **source /tools/Xilinx/SDK/2019.1/settings64.sh**

  **xsdk**

  ...or csh type:

  **source /tools/Xilinx/SDK/2019.1/settings64.csh**

  **xsdk**

  Note: this runs:

  /tools/Xilinx/SDK/2019.1/eclipse/lnx64.o/eclipse -vmargs -Xms64m -Xmx4G -Dorg.eclipse.swt.internal.gtk.cairoGraphics=false &

  You can also use this to start in batch mode:

   **xsdk -batch -source test.tcl**

  ...and to get help:

  **xsdk -help** 

  **You should see:**

  Display Options:

    -help

  ​	Help -- just display this message and quit.

    -version

  ​	Display Version and quit.

    -batch

  ​	SDK Tcl Batch Mode.

    -wait

  ​	Wait for SDK to complete.

  Options:

    -workspace <Workspace location>

  ​	Specify the Workspace directory for SDK projects

    -hwspec <hardware specification file>

  ​	Specify the XML file to load.

    -bit <bitstream file>

  ​	Specify the Bitstream file to use for programming FPGA

    -bmm <bmm file>

  ​	Specify the BMM file to use for BRAM initialization

    -batch -source <tcl script file>

  ​	Specify tcl Script file to execute all commands in SDK batch mode

    {-lp <repository_path>}

  ​	Add <repository_path> to the list of Driver/OS/Library search directories.

    -eclipseargs <eclipse arguments>

  ​	Any other arguments that should be passed to Eclipse.

  ​	This should follow all other SDK arguments.

    -vmargs <java vm arguments>

  ​	Any other arguments that should be passed to Java VM.

  ​	This should follow all other SDK arguments.

  **References**

  - **How do I check which shell I am using?** [[link](https://askubuntu.com/questions/590899/how-do-i-check-which-shell-i-am-using)]
  - UG1138 (v2019.1) May 22, 2019 **Generating Basic Software Platforms Reference Guide** [[link](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2019_1/ug1138-generating-basic-software-platforms.pdf)]
  - **Using SDK Batch Mode** (from 2014.3, could not find newer) [[link](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2014_3/SDK_Doc/concepts/sdk_c_batch_mode.htm)]
  - **2014.4 - SDK - How to create SDK projects using SDK in Batch mode** [[link](https://www.xilinx.com/support/answers/63384.html)]
  - The Xilinx graphic is from [[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)] 

   