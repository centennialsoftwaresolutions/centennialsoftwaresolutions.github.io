# Vivado Command Line Options From vivado -help

![amd_vivado_graphic](amd_vivado_graphic.png)

This post lists Vivado command line options from Vivado v2023.1.

```
demouser@fpgadev:~/Desktop$ vivado -help
vivado

Description: 
Vivado v2023.1 (64-bit)
SW Build 3865809 on Sun May  7 15:04:56 MDT 2023
IP Build 3864474 on Sun May  7 20:36:21 MDT 2023
Tool Version Limit: 2023.05
Copyright 1986-2022 Xilinx, Inc. All Rights Reserved.
Copyright 2022-2023 Advanced Micro Devices, Inc. All Rights Reserved.
SharedData Build 3865790 on Sun May 07 13:33:03 MDT 2023


Syntax: 
vivado  [-mode <arg>] [-init] [-source <arg>] [-nojournal] [-appjournal]
        [-journal <arg>] [-nolog] [-applog] [-log <arg>] [-version]
        [-tclargs <arg>] [-tempDir <arg>] [-robot <arg>] [-verbose] [<project>]

Usage: 
  Name           Description
  --------------------------
  [-mode]        Invocation mode, allowed values are 'gui', 'tcl', and 
                 'batch'
                 Default: gui
  [-init]        Source vivado.tcl file
  [-source]      Source the specified Tcl file
  [-nojournal]   Do not create a journal file
  [-appjournal]  Open journal file in append mode
  [-journal]     Journal file name
                 Default: vivado.jou
  [-nolog]       Do not create a log file
  [-applog]      Open log file in append mode
  [-log]         Log file name
                 Default: vivado.log
  [-version]     Output version information and exit
  [-tclargs]     Arguments passed on to tcl argc argv
  [-tempDir]     Temporary directory name.
  [-robot]       Robot JAR file name.
  [-verbose]     Suspend message limits during command execution
  [<project>]    Load the specified project (.xpr) or design checkpoint 
                 (.dcp) file

Categories: 
```