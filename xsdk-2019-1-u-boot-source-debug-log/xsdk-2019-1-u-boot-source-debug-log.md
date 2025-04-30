# XSDK 2019.1 U-Boot Source Debug Log

![Xilinx_logo](Xilinx_logo.png)

This post list a log of the steps I followed to source code debug U-Boot on a ZCU102.

**<u><span>Steps</span></u>**

The steps came from [https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/18842557/Debug+U-boot].

**<u><span>Setup</span></u>**

I ran all of this from the same machine running Ubuntu 16.04.5 and 2019.1

demo@ubuntu:~/plxprjs/xilinx-zcu102-2019.1$ lsb\_release -a

No LSB modules are available.

Distributor ID: Ubuntu

Description: Ubuntu 16.04.5 LTS

Release: 16.04

Codename: xenial

**<u><span>Log</span></u>**

I did a full build of the 2019.1 PetaLinux BSP for the ZCU102:

```
petalinux-build
```

I connected a UART to /dev/ttyUSB0

```
screen /dev/ttyUSB0 115200
```

I JTAG booted U-Boot:

```
petalinux-boot --jtag --u-boot -v --hw_server-url 10.0.0.2:3121 
```

I let U-Boot boot and noted **reloc off**:

```
# reloc off   = 0x000000006fd6a000
```

I launched devshell, cd'd into the temp directory, noted the version of U-Boot the build was using, where it was located, and checked out a copy of it:

```
petalinux-build -c u-boot -x devshell
cd build/tmp/work/plnx_zynqmp-xilinx-linux/u-boot-xlnx/v2019.01-xilinx-v2019.1+gitAUTOINC+d895ac5e94-r0/git
git remote -v
# origin https://github.com/Xilinx/u-boot-xlnx.git (fetch)
# origin https://github.com/Xilinx/u-boot-xlnx.git (push)
git log
# commit d895ac5e94815d4b45dcf09d4752c5c2334a51db
# type exit in devshell
# New window
cd ~/
git clone https://github.com/Xilinx/u-boot-xlnx.git
cd u-boot-xlnx/
# /home/demo/u-boot/u-boot-xlnx
git checkout d895ac5e94815d4b45dcf09d4752c5c2334a51db
# Other window
```

I configured U-Boot to use an external tree:

```
petalinux-config
# Choose Linux Components Selection
# Choose u-boot (u-boot-xlnx)
# Choose External u-boot local source settings # < this will show up now
# Choose ext-local-src, set to: /home/demo/u-boot/u-boot-xlnx
petalinux-build
```

I launched xsct:

```
cd /tools/Xilinx/SDK/2019.1/bin
./xsct
```

I connected to the target in xsct:

```
connect -host 10.0.0.2 -port 3121
```

I ran memmap:

```
targets -set -nocase -filter {name =~ "*A53*#0"}
memmap -reloc 0x000000006fd6a000 -file /home/demo/plxprjs/xilinx-zcu102-2019.1/build/tmp/work/zcu102_zynqmp-xilinx-linux/u-boot-xlnx/v2019.01-xilinx-v2019.1+git999-r0/u-boot-xlnx-v2019.01-xilinx-v2019.1+git999/u-boot
```

I launched xsdk and configured the debug connection to my SmartLynq:

Host 10.0.0.2

Port 3121

Use symbol server

I created a Debug profile to attach to a running program.

I hard rebooted the ZCU102 and pressed pause as U-Boot was booting.

I was then able to see U-Boot source and set line break points. I was able to hard the target and see U-Boot working.

**<u><span>References</span></u>**

-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]