# What's the difference between XSCT and XSDB?

![amd_logo](amd_logo.png)

**What's the difference between XSCT and XSDB?** Dive into the essentials of XSDB and XSCT with this post. We cover key differences, commands, installation guides, and usage tips, including help commands. It's crafted as a quick reference and a repository for crucial documentation, ensuring you have the right tools at your fingertips for efficient workflow.

This information is accurate as of Vivado and Vitis release 22.04.1

## <u><span>What's the difference between XSCT and XSDB?</span></u>

**XSDB**, short for **Xilinx System Debugger**, offers a **command line interface** that is both interactive and scriptable, making it user-friendly for developers. Its primary function is to facilitate debugging processes.

Similarly, the Xilinx Software Command-line Tool (**XSCT**) provides interactive, scriptable **command-line access** to the suite of Xilinx development tools. It enables users to execute all the operations available in the **Eclipse-based Vitis interface** but from the convenience of a shell environment.

## <u><span>xsct Commands</span></u>

| changebsp           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/changebsp |
| ------------------- | ------------------------------------------------------------ |
| configapp           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/configapp |
| createapp           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/createapp |
| createbsp           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/createbsp |
| createhw            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/createhw |
| createlib           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/createlib |
| deleteprojects      | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/deleteprojects |
| getprojects         | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/getprojects |
| getws               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/getws  |
| hsi close_hw_design | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/hsi-close_hw_design |
| hsi close_sw_design | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/hsi-close_sw_design |
| hsi open_hw_design  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/hsi-open_hw_design |
| hsi open_sw_design  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/hsi-open_sw_design |
| importprojects      | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/importprojects |
| importsources       | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/importsources |
| setws               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/setws  |
| toolchain           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/toolchain |
| updatehw            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/updatehw |

## <u><span>xsdb Commands</span></u>

Note: The documentation lists these under **xsct**

| backtrace              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/backtrace |
| ---------------------- | ------------------------------------------------------------ |
| bpadd                  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/bpadd  |
| bpdisable              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/bpdisable |
| bpenable               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/bpenable |
| bplist                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/bplist |
| bpremove               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/bpremove |
| bpstatus               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/bpstatus |
| breakpoints            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/breakpoints |
| bt                     | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/bt     |
| categories             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/categories |
| closebsp               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/closebsp |
| closehw                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/closehw |
| commands               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/commands |
| con                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/con    |
| configbsp              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/configbsp |
| configparams           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/configparams |
| connect                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/connect |
| connections            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/connections |
| device                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/device |
| device authjtag        | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/device-authjtag |
| device program         | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/device-program |
| device status          | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/device-status |
| dis                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/dis    |
| disconnect             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/disconnect |
| dow                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/dow    |
| download               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/download |
| fpga                   | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/fpga   |
| gdbremote connect      | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/gdbremote-connect |
| gdbremote disconnect   | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/gdbremote-disconnect |
| getaddrmap             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/getaddrmap |
| getdrivers             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/getdrivers |
| getlibs                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/getlibs |
| getos                  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/getos  |
| getperipherals         | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/getperipherals |
| hsi                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/hsi    |
| init_ps                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/init_ps |
| ipi                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/ipi    |
| jtag                   | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag   |
| jtag claim             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-claim |
| jtag device_properties | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-device_properties |
| jtag disclaim          | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-disclaim |
| jtag frequency         | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-frequency |
| jtag lock              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-lock |
| jtag sequence          | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-sequence |
| jtag servers           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-servers |
| jtag skew              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-skew |
| jtag targets           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-targets |
| jtag unlock            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtag-unlock |
| jtagterminal           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/jtagterminal |
| loadhw                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/loadhw |
| loadipxact             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/loadipxact |
| locals                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/locals |
| mask_poll              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mask_poll |
| mask_write             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mask_write |
| mb_drrd                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mb_drrd |
| mb_drwr                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mb_drwr |
| mbprofile              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mbprofile |
| mbtrace                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mbtrace |
| mdm_drrd               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mdm_drrd |
| mdm_drwr               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mdm_drwr |
| memmap                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/memmap |
| memory                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/memory |
| miscellaneous          | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/miscellaneous |
| mrd                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mrd    |
| mwr                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/mwr    |
| nxt                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/nxt    |
| nxti                   | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/nxti   |
| openbsp                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/openbsp |
| openhw                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/openhw |
| osa                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/osa    |
| petalinux              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/petalinux |
| plm                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/plm    |
| plm copy-debug-log     | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/plm-copy-debug-log |
| plm log                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/plm-log |
| plm set-debug-log      | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/plm-set-debug-log |
| plm set-log-level      | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/plm-set-log-level |
| pmc                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/pmc    |
| print                  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/print  |
| profile                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/profile |
| projects               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/projects |
| readjtaguart           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/readjtaguart |
| regenbsp               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/regenbsp |
| registers              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/registers |
| removelib              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/removelib |
| repo                   | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/repo   |
| reset                  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/reset  |
| rrd                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/rrd    |
| rst                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/rst    |
| running                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/running |
| rwr                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/rwr    |
| sdk                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/sdk    |
| setdriver              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/setdriver |
| setlib                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/setlib |
| setosversion           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/setosversion |
| stapl                  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/stapl  |
| stapl config           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/stapl-config |
| stapl start            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/stapl-start |
| stapl stop             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/stapl-stop |
| state                  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/state  |
| stop                   | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/stop   |
| stp                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/stp    |
| stpi                   | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/stpi   |
| stpout                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/stpout |
| streams                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/streams |
| svf                    | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/svf    |
| svf con                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/svf-con |
| svf config             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/svf-config |
| svf delay              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/svf-delay |
| svf dow                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/svf-dow |
| svf generate           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/svf-generate |
| svf mwr                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/svf-mwr |
| svf rst                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/svf-rst |
| svf stop               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/svf-stop |
| targets                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/targets |
| tfile                  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile  |
| tfile close            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-close |
| tfile copy             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-copy |
| tfile fsetstat         | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-fsetstat |
| tfile fstat            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-fstat |
| tfile ls               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-ls |
| tfile lstat            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-lstat |
| tfile mkdir            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-mkdir |
| tfile open             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-open |
| tfile opendir          | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-opendir |
| tfile read             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-read |
| tfile readdir          | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-readdir |
| tfile readlink         | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-readlink |
| tfile realpath         | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-realpath |
| tfile remove           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-remove |
| tfile rename           | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-rename |
| tfile rmdir            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-rmdir |
| tfile roots            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-roots |
| tfile setstat          | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-setstat |
| tfile stat             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-stat |
| tfile symlink          | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-symlink |
| tfile user             | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-user |
| tfile write            | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/tfile-write |
| unloadhw               | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/unloadhw |
| updatemss              | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/updatemss |
| verify                 | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/verify |
| version                | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/version |
| xsdbserver disconnect  | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/xsdbserver-disconnect |
| xsdbserver start       | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/xsdbserver-start |
| xsdbserver stop        | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/xsdbserver-stop |
| xsdbserver version     | https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/xsdbserver-version |

This list was generated with this command and then transposed with Google Sheets:

```
<span><span>xsdb% help xsct allcommands                                                                                                   unknown command or category "xsct allcommands": must be ...</span></span>
```

This list was generated with this command and then transposed with Google Sheets:

```
xsdb% help xsct allcommands                                                  unknown command or category "xsct allcommands": must be ...
```

Google Sheet with this info: https://docs.google.com/spreadsheets/d/1eXjRYJJsxTR3DK3z7FW4F0aOBflYe0jEzrFge6Zo0zo/edit?usp=sharing

## <u><span>Documentation</span></u>

### XSCT

Xilinx Software Command-Line Tool Reference Guide UG1208 (v2019.1) May 22, 2019

https://docs.xilinx.com/v/u/en-US/ug1208-xsct-reference-guide

Cached: https://drive.google.com/file/d/1Ypd-aaT7COpVTwzErdatRw8Rjw8NTspq/view?usp=drive_link 

Vitis Unified Software Platform Documentation: Embedded Software Development (UG1400) - 636 pages - snapshot on 2024-01-28

https://docs.xilinx.com/r/en-US/ug1400-vitis-embedded/XSCT-Commands

Cached: https://drive.google.com/file/d/1YvAOMlEh654nrctlZ0n0L0-vaIulV-pe/view?usp=drive_link

### XSDB

Debugging Guest Applications with QEMU, XSDB, and XSCT

https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/821985347/Debugging+Guest+Applications+with+QEMU+XSDB+and+XSCT 

Cached: https://drive.google.com/file/d/1Z011GMpEOMygvT5aotIDG5S9DNhMcdcK/view?usp=sharing

## <u><span>Example Install location</span></u>

### XSCT

/home/demouser/tools/amd//Vitis/2023.1/bin/xsct

### XSDB

/home/demouser/tools/amd//Vitis/2023.1/bin/xsdb

## <u><span>Start</span></u>

### XSCT

```
source ~/tools/amd/Vitis/2022.1/settings64.sh
xsct
```

Output:

```
rlwrap: warning: your $TERM is 'xterm-256color' but rlwrap couldn't find it in the terminfo database. Expect some problems.                                                                                ****** Xilinx Software Commandline Tool (XSCT) v2022.1.0
  **** SW Build 3524075 on 2022-04-13-17:42:45
    ** Copyright 1986-2022 Xilinx, Inc. All Rights Reserved.
xsct%
```

### XSDB

```
source ~/tools/amd/Vitis/2022.1/settings64.sh
xsdb
```

Output:

```
rlwrap: warning: your $TERM is 'xterm-256color' but rlwrap couldn't find it in the terminfo database. Expect some problems.                                                                                
****** Xilinx System Debugger (XSDB) v2022.1
  **** Build date : Apr 18 2022-16:10:31
    ** Copyright 1986-2022 Xilinx, Inc. All Rights Reserved.
xsdb%
```

## <u><span>Exit</span></u>

### XSCT

```
exit
```

### XSDB

```
exit
```

## <u><span>Help</span></u>

### XSCT

```
xsct -help
demouser@fpgadev:~/Desktop$ xsct -help
rlwrap: warning: your $TERM is 'xterm-256color' but rlwrap couldn't find it in the terminfo database. Expect some problems.
Usage: xsct [options] [tclscript] [tclargs]                                     Options:
  -interactive
Enter interactive mode after -eval or running script.
  -help
Display this help message.
  -no-ini
Do not load xsct.ini
  -quiet
Start XSCT in silent mode
  -eval tclcommand
Execute &lt;tclcommand&gt; then exit
  -eclipseargs &lt;eclipse arguments&gt;
Any other arguments that should be passed to Eclipse.
This should follow all other XSCT arguments.
  -vmargs &lt;java vm arguments&gt;
Any other arguments that should be passed to Java VM.
This should follow all other XSCT arguments.
```

### XSDB

```
xsdb -help
demouser@fpgadev:~/Desktop$ xsdb -help
rlwrap: warning: your $TERM is 'xterm-256color' but rlwrap couldn't find it in the terminfo database. Expect some problems.
Usage: xsdb [options] [tclscript] [tclargs]                                     
Options:
  -interactive
Enter interactive mode after -eval or running script.
  -help
Display this help message.
  -no-ini
Do not load xsdb.ini
  -quiet
Start XSDB in silent mode
  -eval tclcommand
Execute &lt;tclcommand&gt; then exit
```