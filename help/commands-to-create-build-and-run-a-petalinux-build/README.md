# Commands to Create, Build and Run a PetaLinux Build

![xilinx_logo](xilinx_logo.png)

This post just lists the commands used to create, build and run a PetaLinux build. It may be useful if you need to refer to a flow that worked. The commands were run using PetaLinux 2017.4.

**Before you Start**

Instructions to set up download and install PetaLinux Tools are[ here](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools).

**Commands**

Commands to rebuild

In one terminal:

\# Set up ENV

source /home/org/zach/tools/opt/pkg/petalinux/settings.sh

source /home/org/zach/set_petalinux_env.sh

which make

which petalinux-create

cd /home/org/zach/proj/proj2/

export DISPLAY=dummy; /opt/Xilinx/SDK/2017.4/bin/xsct robust-kernel.txt

\# Run again to ensure we can reset the target

export DISPLAY=dummy; /opt/Xilinx/SDK/2017.4/bin/xsct robust-kernel.txt

In another terminal:

minicom -o -w -C today.log

Rebuild

petalinux-build

You should see:

proj2 $ petalinux-build

[INFO] building project

[INFO] sourcing bitbake

INFO: bitbake petalinux-user-image

Loading cache: 100% |############################################| Time: 0:00:00

Loaded 3256 entries from dependency cache.

Parsing recipes: 100% |##########################################| Time: 0:00:01

Parsing of 2466 .bb files complete (2432 cached, 34 parsed). 3259 targets, 225 skipped, 0 masked, 0 errors.

NOTE: Resolving any missing task queue dependencies

Initialising tasks: 100% |#######################################| Time: 0:00:04

Checking sstate mirror object availability: 100% |###############| Time: 0:00:13

NOTE: Executing SetScene Tasks

NOTE: Executing RunQueue Tasks

NOTE: Tasks Summary: Attempted 2474 tasks of which 2469 didn't need to be rerun and all succeeded.

Summary: There was 1 WARNING message shown.

INFO: Copying Images from deploy to images

NOTE: Failed to copy built images to tftp dir: /tftpboot

[INFO] successfully built project

webtalk failed:PetaLinux statistics:extra lines detected:notsent_nofile!

webtalk failed:Failed to get PetaLinux usage statistics!

Commands to Create your Own Build

To create your own build

cd /home/org/zach/proj

\# Check your environment

source /home/org/zach/tools/opt/pkg/petalinux/settings.sh

source /home/org/zach/set_petalinux_env.sh

which make

which petalinux-create

\# Create a project

petalinux-create --type project --template zynqMP --name proj4

cd proj4

\# Get the HDF, stored in the directory above

petalinux-config --get-hw-description=../

\# Select S and E

\# done with petalinux-config --get-hw-description=../ *************

\# Build it

petalinux-build

\# This vvvv is not needed since we’re going to overwrite it, but its useful to see what PetaLinux is doing

petalinux-boot --jtag --kernel --tcl kernel.txt --hw_server-url 192.168.13.111:3121

cp ../proj/robust-kernel.txt .

vi robust-kernel.txt

\# http://vim.wikia.com/wiki/Search_and_replace

\#

[#VI](https://pfefferz.wixsite.com/website-2/blog/hashtags/VI) command to change the dir :%s/proj/proj4/gc

\# Test the build

\# start a minicom in another terminal

minicom -o -w -C 20180309.log

\# Program the build over JTAG

export DISPLAY=dummy; /opt/Xilinx/SDK/2017.4/bin/xsct robust-kernel.txt

\# Save boot to proj3_no_change_boot.txt

\# Now update kernel config and add dtsi

cp /home/org/zach/proj/proj2/project-spec/meta-user/recipes-bsp/device-tree/files/system-user.dtsi project-spec/meta-user/recipes-bsp/device-tree/

\# if you try and run this, when export DISPLAY=dummy has been set it will fail. You need to open a new window and re-run the set up

petalinux-config -c kernel

[#Has](https://pfefferz.wixsite.com/website-2/blog/hashtags/Has) an errror in petalinux-config-error1.txt, when I tried to run: export DISPLAY=dummy; /opt/Xilinx/SDK/2017.4/bin/xsct robust-kernel.txt in the same window so open a new window and run: /opt/Xilinx/SDK/2017.4/bin/xsct robust-kernel.txt

https://docs.google.com/document/d/1_c7PBGFRP5CZPkle1pk6b-3xH0t9iG-cuj-BFOwSMSg/edit?usp=sharing

[#Reset](https://pfefferz.wixsite.com/website-2/blog/hashtags/Reset) env (to unset dummy) - open a new window:

cd /home/org/zach/proj

source /home/org/zach/tools/opt/pkg/petalinux/settings.sh

source /home/org/zach/set_petalinux_env.sh

which make

which petalinux-create

cd proj3

\# Configure the Linux kernel

petalinux-config -c kernel

petalinux-build

**robust-kernel.txt**

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

\# Works ^^^^

\# 0001_1100_000

\# 00_011_100_000

\# mask_write 0xFFCA0038 0x1C0 0x1C0

\# This ^ looks wrong, try vvv

[#1_1111_111](https://pfefferz.wixsite.com/website-2/blog/hashtags/1_1111_111)

[#0xFFCA0038](https://pfefferz.wixsite.com/website-2/blog/hashtags/0xFFCA0038) - jtag_sec (CSU) Register Description

mwr 0xFFCA0038 0x1ff

targets -set -nocase -filter {name =~ "*MicroBlaze PMU*"}

puts stderr "INFO: Downloading ELF file to the target."

dow "/home/org/zach/proj/proj2/images/linux/pmufw.elf"

after 2000

con

\# Works ^^^^

\# at this point the PMU is running

targets -set -nocase -filter {name =~ "*APU*"}

[#0xffff0000](https://pfefferz.wixsite.com/website-2/blog/hashtags/0xffff0000)

[#Write](https://pfefferz.wixsite.com/website-2/blog/hashtags/Write) 0x14000000 to what looks like the reset vector

mwr 0xffff0000 0x14000000

[#0xFD1A0104](https://pfefferz.wixsite.com/website-2/blog/hashtags/0xFD1A0104) - CRF_APB - Software Controlled APU MPCore Resets

\# 0x0101_0000_0001

\# 0x0_1_0_1_0_0_0_0_0_0_0_1

\# acpu0_reset - APU core0 system reset

\# apu_l2_reset - L2 Cache reset

\# acpu0_pwron_reset - APU core0 POR reset.

[#mask_write](https://pfefferz.wixsite.com/website-2/blog/hashtags/mask_write) 0xFD1A0104 0x501 0x0

mwr 0xFD1A0104 0x501

after 2000

mwr 0xFD1A0104 0x0

after 2000

targets -set -nocase -filter {name =~ "*A53*#0"}

source /home/org/zach/proj/proj2/project-spec/hw-description/psu_init.tcl

\# After this ^^^ DDR timings have been set up

puts stderr "INFO: Downloading ELF file to the target."

dow "/home/org/zach/proj/proj2/images/linux/zynqmp_fsbl.elf"

after 2000

con

\# At this point, fsbl is running

after 4000; stop; catch {stop}; psu_ps_pl_isolation_removal; psu_ps_pl_reset_config

targets -set -nocase -filter {name =~ "*A53*#0"}

dow -data "/home/org/zach/proj/proj2/images/linux/Image" 0x00080000

after 2000

targets -set -nocase -filter {name =~ "*A53*#0"}

dow -data "/home/org/zach/proj/proj2/images/linux/system.dtb" 0x1407f000

after 2000

[#Works](https://pfefferz.wixsite.com/website-2/blog/hashtags/Works)

targets -set -nocase -filter {name =~ "*A53*#0"}

puts stderr "INFO: Downloading ELF file to the target."

dow "/home/org/zach/proj/proj2/build/misc/linux-boot/linux-boot.elf"

after 2000

[#Works](https://pfefferz.wixsite.com/website-2/blog/hashtags/Works)

targets -set -nocase -filter {name =~ "*A53*#0"}

puts stderr "INFO: Downloading ELF file to the target."

dow "/home/org/zach/proj/proj2/images/linux/bl31.elf"

after 2000

[#works](https://pfefferz.wixsite.com/website-2/blog/hashtags/works)

con

**Reference**

- Logo via[ https://twitter.com/xilinxinc](http://twitter.com/xilinxinc) at[ link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png) 
- The log is also available at[ link](http://docs.google.com/document/d/17rSjAcPPJHi2wau-dXn2r8POW7AvOydlQcA-QGVDJmw/edit?usp=sharing) 
- robust-kernel.txt is available at[ link](http://docs.google.com/document/d/1rDrPq6urqG_5F1dQ_znyVQpg7HG6XWAqixRkDezHgGU/edit?usp=sharing)