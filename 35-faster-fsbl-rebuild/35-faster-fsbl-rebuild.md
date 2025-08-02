# 35% Faster FSBL Rebuild

![yocto_project_logo](yocto_project_logo.png)

This post shows how to rebuild the Xilinx Zynq MP First Stage Boot Loader (FSBL) from PetaLinux Tools 2017.4 in 35% less time with bitbake. It also shows hot to load it over JTAG and reviews commands that do not recompile the FSBL.

**Prerequisite**

-   An installation of PetaLinux Tools 2017.4 - [HOWTO](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools)
    
-   A PetaLinux Tools ZU+ project that's been built - [HOWTO](http://www.zachpfeffer.com/single-post/Create-Build-and-Test-a-PetaLinux-Tools-20174-Project)
    

**Fastest Way (bitbake) - 35% faster**

Get access to bitbake

```
source $PETALINUX_TOOLS_INSTALL_DIR/components/yocto/source/aarch64/environment-setup-aarch64-xilinx-linux
echo "Changing directory from $PWD to $PETALINUX_PROJS_DIR/$PETALINUX_PROJ_NAME"
cd $PETALINUX_PROJS_DIR/$PETALINUX_PROJ_NAME
source $PETALINUX_TOOLS_INSTALL_DIR/components/yocto/source/aarch64/layers/core/oe-init-build-env
export BB_ENV_EXTRAWHITE="$BB_ENV_EXTRAWHITE PETALINUX"
which bitbake
```

Make a change to:

```
components/plnx_workspace/fsbl/fsbl/src/xfsbl_main.c
```

...like:

```
	XFsbl_Printf(DEBUG_PRINT_ALWAYS,
                 "Release %d.%d   %s  -  %s\r\n",
                 SDK_RELEASE_YEAR, SDK_RELEASE_QUARTER,__DATE__,__TIME__);
	XFsbl_Printf(DEBUG_PRINT_ALWAYS,
                 "Hello!\n\r");
```

Rebuild

```
bitbake virtual/fsbl -c compile -C compile
```

Time taken on my machine:

```
real	1m21.337s
user	0m21.546s
sys	0m4.469s
```

"Package"

```
cp ../components/plnx_workspace/fsbl/fsbl/Release/fsbl.elf ../images/linux/zynqmp_fsbl.elf
```

Time taken on my machine:

```
real	0m0.004s
user	0m0.002s
sys	0m0.000s
```

Load the FSBL

```
connect -url tcp:localhost:3121

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

mwr 0xFFCA0038 0x1ff

targets -set -nocase -filter {name =~ "*MicroBlaze PMU*"}
dow /home/pfefferz/build/out/pmufw.elf
after 2000
con

targets -set -nocase -filter {name =~ "*APU*"}
mwr 0xffff0000 0x14000000
mwr 0xFD1A0104 0x501
after 2000
mwr 0xFD1A0104 0x0
after 2000
targets -set -nocase -filter {name =~ "*A53*#0"}

source /home/pfefferz/build/out/psu_init.tcl

dow /home/pfefferz/build/out/zynqmp_fsbl.elf
after 2000
con
```

See the results on a serial port

```
Xilinx Zynq MP First Stage Boot Loader
Release 2017.4   Jun  3 2018  -  21:43:02
Hello!
```

Total Time:1:21

**Fast Way (petalinux-build)**

Rebuild

```
petalinux-build -c bootloader -x compile -f
```

Time taken on my machine

```
real	1m34.931s
user	0m28.377s
sys	0m5.907s
```

Package

```
petalinux-build -c bootloader -x deploy -f
```

Time taken on my machine

```
real	0m44.025s
user	0m27.110s
sys	0m5.846s
```

Total Time: 2:19

**Ways that Do Not Recompile The FSBL**

```
petalinux-build -c bootloader
```

Comment

I feel that this is wrong. My expectation is that if a change is made to the FSBL source that this command should rebuild it.

**Reference**

Free Online HTML Escape / Unescape Tool - FreeFormatter.com @ [link](http://www.freeformatter.com/html-escape.html)