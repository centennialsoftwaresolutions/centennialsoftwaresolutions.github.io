# Launching Vivado from Windows and Linux

![xilinx_logo_1](xilinx_logo_1.png)

This post lists how to launch Vivado on Windows and Linux from icons and from the command line.

This info is located in **Vivado Design Suite User Guide Design Flows Overview UG892 (v2018.2) June 6, 2018** at \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug892-vivado-design-flows-overview.pdf)\].

**<u><span>Launch Vivado</span></u>**

**Launch 2018.2 Vivado on Windows**

-   Click **Start > All Programs > Xilinx Design Tools > Vivado 2018.2 > Vivado 2018.2**
    
-   or double click **Vivado IDE Desktop Icon**
    
-   or click **Start**, type **vivado**
    

**Launch 2018.2 Vivado from CMD on Windows**

1.  Type **cd PRJDIR** (the directory with the **xpr** file)
    
2.  Type **C:\\Xilinx\\Vivado\\2018.2\\settings64.bat**
    
3.  Type **vivado**
    

You should see something like:

\*\*\*\*\*\* Vivado v2018.2 (64-bit)

\*\*\*\* SW Build 2258646 on Thu Jun 14 20:03:12 MDT 2018

\*\*\*\* IP Build 2256618 on Thu Jun 14 22:10:49 MDT 2018

\*\* Copyright 1986-2018 Xilinx, Inc. All Rights Reserved.

start\_gui

Then the Vivado window popping up.

**Launch 2018.2 Vivado on Linux**

1.  Type **cd PRJDIR** (the directory with the **xpr** file)
    
2.  Type **source /opt/Xilinx/Vivado/2018.2/settings64.sh**
    
3.  Type **vivado prj.xpr**
    

Replace **prj.xpr** with your **xpr** project file or leave the xpr file out to just launch Vivado.

You should see:

\*\*\*\*\*\* Vivado v2018.2 (64-bit)

\*\*\*\* SW Build 2258646 on Thu Jun 14 20:02:38 MDT 2018

\*\*\*\* IP Build 2256618 on Thu Jun 14 22:10:49 MDT 2018

\*\* Copyright 1986-2018 Xilinx, Inc. All Rights Reserved.

start\_gui

Then the Vivado window popping up.

**Launch Vivado IDE from Tcl Shell**

-   Type **start\_gui**
    

**Start Vivado Tcl Shell**

-   Type **vivado -mode tcl**
    

**Run a TCL Script then Exit**

-   Type **vivado -mode batch -source SCRIPT**
    

**<u><span>Reference</span></u>**

Xilinx logo found via https://twitter.com/xilinxinc at [[link](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)]  