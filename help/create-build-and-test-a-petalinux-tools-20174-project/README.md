# Create, Build and Test a PetaLinux Tools 2017.4 Project

![tux_logo](tux_logo.png)

This post lists the commands to create, configure and test a PetaLinux Tools project using PetaLinux Tools 2017.4.

**Before you Start**

If you haven't installed PetaLinux Tools 2017.4 go through [Download and Install Xilinx's 2017.4 PetaLinux Tools](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools)[.](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools)

This write up connects to a hw\_server to test the build. It uses a COM port to see output from the unit.

**Steps**

1\. Create a directory for all PetaLinux projects

```
mkdir /home/plc2/zach/prjs
cd /home/plc2/zach/prjs
```

2\. Copy an HDF to it

```
# Copy your HDF to prjs
cp /path/to/hdf/myproj.hdf /home/plc2/zach/prjs
```

3\. Set Up the Environment

```
source /home/plc2/zach/tools/opt/pkg/petalinux/settings.sh
source /home/plc2/zach/set_petalinux_env.sh
which make
which petalinux-create
```

You should see:

```
PetaLinux environment set to '/home/plc2/zach/tools/opt/pkg/petalinux'
INFO: Checking free disk space
INFO: Checking installed tools
INFO: Checking installed development libraries
INFO: Checking network and other services
prjs $ source /home/plc2/zach/set_petalinux_env.sh
prjs $ which make
/home/plc2/zach/tools/bin/make
prjs $ which petalinux-create
/home/plc2/zach/tools/opt/pkg/petalinux/tools/common/petalinux/bin/petalinux-create
```

4\. Create your project

```
petalinux-create --type project --template zynqMP --name myproj
```

You should see:

```
INFO: Create project: myproj
```

5\. Configure it with an HDF

```
cd myproj
petalinux-config --get-hw-description=../
# When prompted select < Exit > and < Yes >
```

You should see:

```
myproj $ petalinux-config --get-hw-description=../
INFO: Getting hardware description...
cp: omitting directory '/home/plc2/zach/prjs/myproj'
INFO: Rename myproj.hdf to system.hdf
[INFO] generating Kconfig for project
                                                                                
[INFO] menuconfig project
/home/plc2/zach/prjs/myproj/build/misc/config/Kconfig.syshw:30:warning: defaults for choice values not supported
/home/plc2/zach/prjs/myproj/build/misc/config/Kconfig:568:warning: config symbol defined without type
configuration written to /home/plc2/zach/prjs/myproj/project-spec/configs/config

*** End of the configuration.
*** Execute 'make' to start the build or try 'make help'.

[INFO] sourcing bitbake
[INFO] generating plnxtool conf
[INFO] generating meta-plnx-generated layer
~/zach/prjs/myproj/build/misc/plnx-generated ~/zach/prjs/myproj
~/zach/prjs/myproj
[INFO] generating machine configuration
[INFO] generating bbappends for project . This may take time ! 
~/zach/prjs/myproj/build/misc/plnx-generated ~/zach/prjs/myproj
~/zach/prjs/myproj
[INFO] generating u-boot configuration files
                                                                                
[INFO] generating kernel configuration files
[INFO] generating kconfig for Rootfs
Generate rootfs kconfig
[INFO] oldconfig rootfs
[INFO] generating petalinux-user-image.bb
myproj $ 
```

6\. Build it

```
petalinux-build
```

You should see after a few minutes:

```
myproj $ petalinux-build
[INFO] building project
[INFO] sourcing bitbake
INFO: bitbake petalinux-user-image
Parsing recipes: 100% |##########################################| Time: 0:00:53
Parsing of 2466 .bb files complete (0 cached, 2466 parsed). 3259 targets, 225 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies
Initialising tasks: 100% |#######################################| Time: 0:00:04
Checking sstate mirror object availability: 100% |###############| Time: 0:00:14
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
fsbl-2017.4+gitAUTOINC+77448ae629-r0 do_compile: NOTE: fsbl: compiling from external source tree /home/plc2/zach/tools/opt/pkg/petalinux/tools/hsm/data/embeddedsw
pmu-firmware-2017.4+gitAUTOINC+77448ae629-r0 do_compile: NOTE: pmu-firmware: compiling from external source tree /home/plc2/zach/tools/opt/pkg/petalinux/tools/hsm/data/embeddedsw
NOTE: Tasks Summary: Attempted 2474 tasks of which 1877 didn't need to be rerun and all succeeded.

Summary: There was 1 WARNING message shown.
INFO: Copying Images from deploy to images
INFO: Creating images/linux directory
NOTE: Failed to copy built images to tftp dir:  /tftpboot
[INFO] successfully built project
myproj $ 
```

7\. Test it

7.1 Connect to your COM port via [minicom](http://linux.die.net/man/1/minicom)

```
minicom -o -w -C 20180308.log
```

Note: type Control-A then type X to quit

**\-o**: skip init code

**\-w**: turns line-wrap on at startup by default

**\-C** filename: open capture at start up

Note from minicom [man](http://linux.die.net/man/1/minicom):

Minicom keeps it's configuration files in one directory, usually /var/lib/minicom, /usr/local/etc or /etc. To find out what default directory minicom has compiled in, issue the command minicom -h.

```
# Machine-generated file - use "minicom -s" to change parameters.
pu port             /dev/ttyUSB0
pu statusline       disabled
pu rtscts           No 
```

Here's the output on my machine:

7.2 Test the build via jtag with

```
petalinux-boot --jtag --kernel --hw_server-url 192.168.13.111:3121
```

Note: even though it says --kernel, this command downloads the following binaries:

PMUFW, FSBL, A Linux FIT image, the Device Tree Binary, a "light boot loader," compiled by PetaLinux (called linux-boot.elf) and Arm Trusted Firmware (called bl31.elf).

You should see a kernel dmesg output on the com port and a log in prompt:

```
[    4.530003] random: fast init done
[    4.697392] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[    4.714325] EXT4-fs (mmcblk0p2): recovery complete
[    4.719142] EXT4-fs (mmcblk0p2): mounted filesystem with ordered data mode. Opts: (null)

PetaLinux 2017.4 myproj /dev/ttyPS0

myproj login: 
```

Log in with root, password is root.

8\. Fix JTAG Boot a second, third, fourth time...

The jtag boot command only works once for me. To build something a little more robust I created the following.

8.1 Output the XSCT TCL commands that PetaLinux Tools uses

```
petalinux-boot --jtag --kernel --tcl kernel.txt --hw_server-url 192.168.13.111:3121
```

This will output:

```
connect -url 192.168.13.111:3121
targets -set -nocase -filter {name =~ "*PSU*"}
mask_write 0xFFCA0038 0x1C0 0x1C0
targets -set -nocase -filter {name =~ "*MicroBlaze PMU*"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/plc2/zach/prjs/myproj/images/linux/pmufw.elf"
after 2000
con
targets -set -nocase -filter {name =~ "*APU*"}
mwr 0xffff0000 0x14000000
mask_write 0xFD1A0104 0x501 0x0
targets -set -nocase -filter {name =~ "*A53*#0"}

source /home/plc2/zach/prjs/myproj/project-spec/hw-description/psu_init.tcl
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/plc2/zach/prjs/myproj/images/linux/zynqmp_fsbl.elf"
after 2000
con
after 4000; stop; catch {stop}; psu_ps_pl_isolation_removal; psu_ps_pl_reset_config
targets -set -nocase -filter {name =~ "*A53*#0"}
dow -data "/home/plc2/zach/prjs/myproj/images/linux/Image" 0x00080000
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
dow -data "/home/plc2/zach/prjs/myproj/images/linux/system.dtb" 0x1407f000
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/plc2/zach/prjs/myproj/build/misc/linux-boot/linux-boot.elf"
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/plc2/zach/prjs/myproj/images/linux/bl31.elf"
after 2000
con
exit
puts stderr "INFO: Saving XSDB commands to kernel.txt. You can run 'xsdb kernel.txt' to execute"
```

Change the script to the following:

```
connect -url 192.168.13.111:3121

targets -set -nocase -filter {name =~ "*PSU*"}
stop
rst -system
after 2000
targets -set -nocase -filter {name =~ "*PMU*"}
stop
rst -system
after 2000
targets -set -nocase -filter {name =~ "*PSU*"}
stop
rst -system
after 2000
# Works ^^^^

# 0001_1100_000
# 00_011_100_000
# mask_write 0xFFCA0038 0x1C0 0x1C0
# This ^ looks wrong, try vvv
#1_1111_111
#0xFFCA0038 - jtag_sec (CSU) Register Description
mwr 0xFFCA0038 0x1ff
targets -set -nocase -filter {name =~ "*MicroBlaze PMU*"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/plc2/zach/prjs/myproj/images/linux/pmufw.elf"
after 2000
con
# Works ^^^^

# at this point the PMU is running
targets -set -nocase -filter {name =~ "*APU*"}
#0xffff0000
#Write 0x14000000 to what looks like the reset vector
mwr 0xffff0000 0x14000000
#0xFD1A0104 - CRF_APB - Software Controlled APU MPCore Resets
# 0x0101_0000_0001
# 0x0_1_0_1_0_0_0_0_0_0_0_1
# acpu0_reset - APU core0 system reset
# apu_l2_reset - L2 Cache reset
# acpu0_pwron_reset - APU core0 POR reset.
#mask_write 0xFD1A0104 0x501 0x0
mwr 0xFD1A0104 0x501
after 2000
mwr 0xFD1A0104 0x0
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
source /home/plc2/zach/prjs/myproj/project-spec/hw-description/psu_init.tcl
# After this ^^^ DDR timings have been set up

puts stderr "INFO: Downloading ELF file to the target."
dow "/home/plc2/zach/prjs/myproj/images/linux/zynqmp_fsbl.elf"
after 2000
con
# At this point, fsbl is running

after 4000; stop; catch {stop}; psu_ps_pl_isolation_removal; psu_ps_pl_reset_config
targets -set -nocase -filter {name =~ "*A53*#0"}
dow -data "/home/plc2/zach/prjs/myproj/images/linux/Image" 0x00080000
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}
dow -data "/home/plc2/zach/prjs/myproj/images/linux/system.dtb" 0x1407f000
after 2000
#Works

targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/plc2/zach/prjs/myproj/build/misc/linux-boot/linux-boot.elf"
after 2000
#Works

targets -set -nocase -filter {name =~ "*A53*#0"}
puts stderr "INFO: Downloading ELF file to the target."
dow "/home/plc2/zach/prjs/myproj/images/linux/bl31.elf"
after 2000
#works
con
```

8.2 Boot with

```
export DISPLAY=dummy; /opt/Xilinx/SDK/2017.4/bin/xsct robust-kernel.txt
```

8.3 If things still don't work, you get an error about cores being powered down, then run xsct and paste in each command.

```
export DISPLAY=dummy; /opt/Xilinx/SDK/2017.4/bin/xsct
```

**Suggestions to Xilinx**

1\. Fix needing to set DISPLAY=dummy for xsct to run from the command line

You should not need to set a DISPLAY variable to run a command line tool:

```
export DISPLAY=dummy; /opt/Xilinx/SDK/2017.4/bin/xsct
```

Please fix this ASAP.

**References**

-   Tux from [link](http://en.wikipedia.org/wiki/Tux) (found via Google image search)
    
-   PetaLinux Tools Documentation Reference Guide [UG1144](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_4/ug1144-petalinux-tools-reference-guide.pdf) (v2017.4)
    
-   PetaLinux Tools Documentation Workflow Tutorial [UG1156](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_4/ug1156-petalinux-tools-workflow-tutorial.pdf) (v2017.4)