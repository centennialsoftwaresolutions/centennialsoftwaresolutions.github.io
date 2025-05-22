# Can't Boot to a Login, the Linux Kernel Appears to Hang at: bootconsole [earlycon0] disabled

![xilinx_logo_1](xilinx_logo_1.png)

This post provides a quick solution to a problem you may see booting the Linux kernel built using PetaLinux Tools 2018.2 on the Zynq-7000 of the ZC706.

## <u><span>Symptom</span></u>

After running:

**petalinux-boot --jtag --kernel --hw\_server-url TCP:localhost:3121**

The kernel log stops at **bootconsole \[earlycon0\] disabled**

**Example:**

![bootconsole_disabled_2](bootconsole_disabled_2.png)

## <u><span>Solution</span></u>

You need to program your FPGA. Using this command to boot:

**petalinux-boot --jtag --fpga --kernel --hw\_server-url TCP:localhost:3121**

## <u><span>Reference</span></u>

Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]