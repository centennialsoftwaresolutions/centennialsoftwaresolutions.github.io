# 15 Minute Setup to Find, Change, Recompile and Test an ARM or x86 Linux Kernel Change in 12 Seconds

![tux_logo_1](tux_logo_1.png)

This post shows how to set up an efficient ARM or x86 Linux Kernel development environment in about 15 minutes using QEMU, Vim and cscope to find, change, recompile and test a Linux kernel change in 12 seconds (on my machine in a VirtualBox VM).

**<u><span>Environment I Used</span></u>**

-   [<u><span>T460</span></u>](http://www.zachpfeffer.com/single-post/2017/01/28/New-T460-System-Information)
    
-   Oracle VM VirtualBox Version 5.1.30 r118389 (Qt5.6.2) running on Windows 7 SP1
    
-   VM's configured with 4 GB of RAM and a 64 GB disk running Ubuntu 16.04.2.
    
-   If you need help setting up this environment click [<u><span>here</span></u>](http://www.zachpfeffer.com/single-post/2017/02/15/Installing-the-64-bit-PC-AMD64-desktop-image-of-Ubuntu-16041-LTS-Xenial-Xerus-in-Oracle-VM-VirtualBox-5114-running-in-Windows-7-Professional-Service-Pack-1-CurrentBuild-7601-on-a-ThinkPad-T460-model-20FNCTO1WW-with-an-IntelR-CoreTM-i7-6600U-CPU) (just install 16.04.02 instead of 16.04.01).
    

**<u><span>Setup</span></u>**

1\. Install Cscope using [[instructions](http://www.zachpfeffer.com/single-post/cscopevim)]

2\. Follow either the ARM \[[<u><span>arm-instructions</span></u>](https://www.centennialsoftwaresolutions.com/blog/build-the-linux-kernel-and-busybox-for-arm-and-run-them-on-qemu)\] and/or x86 \[[<u><span>x86-instructions</span></u>](https://www.centennialsoftwaresolutions.com/blog/build-the-linux-kernel-and-busybox-and-run-them-on-qemu)\] to build the Linux kernel and BusyBox and boot them on QEMU

3\. Open a terminal and type **vi ~/envset.sh**

4\. Create an environment, type **i** then paste:

...for ARM:

**export STAGE=$HOME/tla**

**export TOP=$STAGE/teeny-linux**

**export ARCH=arm**

**export CROSS\_COMPILE=arm-linux-gnueabi-**

**export KBUILD\_OUTPUT=$TOP/obj/linux-arm-versatile\_defconfig**

**export MAKEFLAGS=j2**

**export CSCOPE\_DB=$KBUILD\_OUTPUT/cscope.out**

...for x86 enter:

**export STAGE=$HOME/tl**

**export TOP=$STAGE/teeny-linux**

**export KBUILD\_OUTPUT=$TOP/obj/linux-x86-allnoconfig**

**export MAKEFLAGS=j2**

**export CSCOPE\_DB=$KBUILD\_OUTPUT/cscope.out**

5\. Type **:w** then **:q**

**<u><span>Recompile the Kernel and Cscope, Run Kernel</span></u>**

1\. Change into the kernel directory:

For ARM type **cd ~/tla/linux-4.10.6**

For x86 type **cd ~/tl/linux-4.10.6**

2\. Type **source ~/envset.sh**

3\. Type **make cscope** to build the cscope index

Note: rerun when source changes

4\. Type **make** to build the kernel

Note: rerun when source changes

5\. Run the kernel in QEMU

For ARM type:

```
qemu-system-arm -M versatilepb  \
-dtb $KBUILD_OUTPUT/arch/arm/boot/dts/versatile-pb.dtb \
-kernel $KBUILD_OUTPUT/arch/arm/boot/zImage \
-initrd $TOP/obj/initramfs.igz \
-nographic -append "earlyprintk=serial,ttyS0 console=ttyAMA0"
```

For x86 type:

```
qemu-system-x86_64 \
    -kernel $KBUILD_OUTPUT/arch/x86/boot/bzImage \
    -initrd $TOP/obj/initramfs.igz \
    -nographic -append "earlyprintk=serial,ttyS0 console=ttyS0"
```

6\. Type **Control-a x** to quit QEMU

**<u><span>Browse Code Quickly</span></u>**

1\. Open a new terminal

2\. Change into the kernel directory:

For ARM type **cd ~/tla/linux-4.10.6**

For x86 type **cd ~/tl/linux-4.10.6**

3\. Type **source ~/envset.sh**

4\. Type **vi init/main.c**

5\. Type **Control-\\** and:

**s** (symbol) to find all references to the token under cursor

**g** (global) find global definition(s) of the token under cursor

**c** (calls) find all calls to the function name under cursor

**t** (text) find all instances of the text under cursor

**e** (egrep) egrep search for the word under cursor

**f** (file) open the filename under cursor

**i** (includes) find files that include the filename under cursor

**d** (called) find functions that function under cursor calls

6\. Type **Control-t** to jump back (works for each jump forward)

**<u><span>Hack Code</span></u>**

Follow \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/set-up-fix-a-buffer-for-linux-kernel-coding-style-in-vim)\] to set up Vim to hack Linux kernel code

**<u><span>References</span></u>**

-   The Vim/Cscope tutorial @ \[[<u><span>link</span></u>](http://cscope.sourceforge.net/cscope_vim_tutorial.html)\]
    
-   Using Cscope on large projects (example: the Linux kernel) @ \[[<u><span>link</span></u>](http://cscope.sourceforge.net/large_projects.html)\]
    
-   Tux from \[[<u><span>link</span></u>](https://www.iconfinder.com/icons/367633/linux_tux_icon#size=128)\]