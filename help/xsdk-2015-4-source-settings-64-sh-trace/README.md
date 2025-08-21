# XSDK 2015.4 source settings64.sh Trace

This post shows an XSDK 2015.4 source [settings64.sh](http://settings64.sh/) trace. Other script sourcing and environment changes are in **bold**.

## Trace Created With

```
set -x
source /opt/Xilinx/SDK/2015.4/settings64.sh
```

## XSDK 2015.4 source settings64.sh Trace

```
+ source /opt/Xilinx/SDK/2015.4/settings64.sh
```

```
++ /opt/Xilinx/SDK/2015.4/.settings64-Software_Development_Kit.sh
```

```
+++ '[' -n /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin ']'
```

```
+++ export PATH=/opt/Xilinx/SDK/2015.4/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/arm/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_be/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_le/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-linux-gnueabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-linux/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-none/bin:/opt/Xilinx/SDK/2015.4/gnu/armr5/lin/gcc-arm-none-eabi/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

```
+++ PATH=/opt/Xilinx/SDK/2015.4/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/arm/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_be/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_le/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-linux-gnueabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-linux/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-none/bin:/opt/Xilinx/SDK/2015.4/gnu/armr5/lin/gcc-arm-none-eabi/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

```
++ source /opt/Xilinx/Vivado_HLS/2015.4/.settings64-Vivado_High_Level_Synthesis.sh
```

```
+++ '[' -n /opt/Xilinx/SDK/2015.4/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/arm/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_be/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_le/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-linux-gnueabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-linux/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-none/bin:/opt/Xilinx/SDK/2015.4/gnu/armr5/lin/gcc-arm-none-eabi/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin ']'
```

```
+++ export PATH=/opt/Xilinx/Vivado_HLS/2015.4/bin:/opt/Xilinx/SDK/2015.4/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/arm/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_be/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_le/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-linux-gnueabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-linux/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-none/bin:/opt/Xilinx/SDK/2015.4/gnu/armr5/lin/gcc-arm-none-eabi/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

```
+++ PATH=/opt/Xilinx/Vivado_HLS/2015.4/bin<span>:/opt/Xilinx/SDK/2015.4/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/arm/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_be/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_le/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-linux-gnueabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-linux/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-none/bin:/opt/Xilinx/SDK/2015.4/gnu/armr5/lin/gcc-arm-none-eabi/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

```
++ source /opt/Xilinx/Vivado/2015.4/.settings64-Vivado.sh
```

```
+++ export XILINX_VIVADO=/opt/Xilinx/Vivado/2015.4
```

```
+++ XILINX_VIVADO=/opt/Xilinx/Vivado/2015.4
```

```
+++ '[' -n /opt/Xilinx/Vivado_HLS/2015.4/bin:/opt/Xilinx/SDK/2015.4/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/arm/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_be/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_le/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-linux-gnueabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-linux/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-none/bin:/opt/Xilinx/SDK/2015.4/gnu/armr5/lin/gcc-arm-none-eabi/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin ']'
```

```
+++ export PATH=/opt/Xilinx/Vivado/2015.4/bin:/opt/Xilinx/Vivado_HLS/2015.4/bin:/opt/Xilinx/SDK/2015.4/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/arm/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_be/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_le/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-linux-gnueabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-linux/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-none/bin:/opt/Xilinx/SDK/2015.4/gnu/armr5/lin/gcc-arm-none-eabi/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

```
+++ PATH=/opt/Xilinx/Vivado/2015.4/bin:/opt/Xilinx/Vivado_HLS/2015.4/bin:/opt/Xilinx/SDK/2015.4/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/arm/lin/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_be/bin:/opt/Xilinx/SDK/2015.4/gnu/microblaze/linux_toolchain/lin64_le/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-linux-gnueabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch32/lin/gcc-arm-none-eabi/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-linux/bin:/opt/Xilinx/SDK/2015.4/gnu/aarch64/lin/aarch64-none/bin:/opt/Xilinx/SDK/2015.4/gnu/armr5/lin/gcc-arm-none-eabi/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

```
+++ export LD_LIBRARY_PATH=/opt/Xilinx/Vivado/2015.4/lib/lnx64.o
```

```
+++ LD_LIBRARY_PATH=/opt/Xilinx/Vivado/2015.4/lib/lnx64.o
```

![sdk_logo](sdk_logo.png)