# Stop typing make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- O=... when building the Linux kernel

![tux_logo_1](tux_logo_1.png)

This post shows you stop typing **make ARCH=arm CROSS\_COMPILE=arm-linux-gnueabi- O=... -j2** and just type **make** when building the Linux kernel.

**<u><span>Versions Used</span></u>**

linux-4.10.6 from https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.10.6.tar.xz

GNU Make 4.1 Built for x86\_64-pc-linux-gnu (type **make --version** to list this)

**<u><span>Steps</span></u>**

Instead of typing:

**make ARCH=arm CROSS\_COMPILE=arm-linux-gnueabi- O=$TOP/obj/linux-arm-versatile\_defconfig -j2**

You can set **ARCH**, **CROSS\_COMPILE,** the output directory (**O**) and the number of make jobs (**\-j2**) using environment variables (bash):

Type the following in your terminal:

**export ARCH=arm**

**export CROSS\_COMPILE=arm-linux-gnueabi-**

**export KBUILD\_OUTPUT=$TOP/obj/linux-arm-versatile\_defconfig**

**export MAKEFLAGS=j2**

Then you can just type **make**

**<u><span>References</span></u>**

GNU Make @ \[[<u><span>link</span></u>](https://www.gnu.org/software/make/manual/make.pdf)\]