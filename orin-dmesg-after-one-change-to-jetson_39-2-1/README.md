# Build L4T with one change, flash it, and get dmesg right after boot

```
cd ~/Downloads/Linux_for_Tegra
# Make a change:
vi ./source/kernel/kernel-noble/init/main.c
      pr_notice("%s", linux_banner);
      pr_notice("Hello, kernel!\n");

cd ~/Downloads/Linux_for_Tegra/source
export CROSS_COMPILE=$HOME/l4t-gcc/x-tools/aarch64-none-linux-gnu/bin/aarch64-none-linux-gnu-
make -C kernel

```

```
make: Entering directory '/home/demo-user/Downloads/Linux_for_Tegra/source/kernel'
================================================================================
Building kernel-noble sources
================================================================================
make \
	ARCH=arm64 \
	-C /home/demo-user/Downloads/Linux_for_Tegra/source/kernel/kernel-noble  \
	LOCALVERSION=-1021-tegra \
	defconfig
make[1]: Entering directory '/home/demo-user/Downloads/Linux_for_Tegra/source/kernel/kernel-noble'
*** Default configuration is based on 'defconfig'
#
# No change to .config
#
make[1]: Leaving directory '/home/demo-user/Downloads/Linux_for_Tegra/source/kernel/kernel-noble'
make -j 16 \
	ARCH=arm64 \
	-C /home/demo-user/Downloads/Linux_for_Tegra/source/kernel/kernel-noble  \
	LOCALVERSION=-1021-tegra \
	--output-sync=target Image
  CALL    scripts/checksyscalls.sh
  CC      init/main.o
  AR      init/built-in.a
  AR      built-in.a
  AR      vmlinux.a
  LD      vmlinux.o
  OBJCOPY modules.builtin.modinfo
  GEN     modules.builtin
  GEN     .vmlinux.objs
  MODPOST vmlinux.symvers
  UPD     include/generated/utsversion.h
  CC      init/version-timestamp.o
  KSYMS   .tmp_vmlinux0.kallsyms.S
  AS      .tmp_vmlinux0.kallsyms.o
  LD      .tmp_vmlinux1
  NM      .tmp_vmlinux1.syms
  KSYMS   .tmp_vmlinux1.kallsyms.S
  AS      .tmp_vmlinux1.kallsyms.o
  LD      .tmp_vmlinux2
  NM      .tmp_vmlinux2.syms
  KSYMS   .tmp_vmlinux2.kallsyms.S
  AS      .tmp_vmlinux2.kallsyms.o
  LD      vmlinux
  NM      System.map
  SORTTAB vmlinux
  OBJCOPY arch/arm64/boot/Image
make -j 16 \
	ARCH=arm64 \
	-C /home/demo-user/Downloads/Linux_for_Tegra/source/kernel/kernel-noble  \
	LOCALVERSION=-1021-tegra \
	--output-sync=target dtbs
make -j 16 \
	ARCH=arm64 \
	-C /home/demo-user/Downloads/Linux_for_Tegra/source/kernel/kernel-noble  \
	LOCALVERSION=-1021-tegra \
	--output-sync=target modules
  CALL    scripts/checksyscalls.sh
  MODPOST Module.symvers
================================================================================
Kernel Image: /home/demo-user/Downloads/Linux_for_Tegra/source/kernel/kernel-noble/arch/arm64/boot/Image
Kernel sources compiled successfully.
================================================================================
make: Leaving directory '/home/demo-user/Downloads/Linux_for_Tegra/source/kernel'

```

```
# Install the new kernel
cd ~/Downloads/Linux_for_Tegra/source
export INSTALL_MOD_PATH=/home/demo-user/Downloads/Linux_for_Tegra/rootfs
sudo -E make install -C kernel
cp kernel/kernel-noble/arch/arm64/boot/Image /home/demo-user/Downloads/Linux_for_Tegra/kernel/Image
```

output:

[sudo_-E_make_install_-C_kernel.out](sudo_-E_make_install_-C_kernel.out)

```
# Try to power off, force recovery, and power on:
cd ~/Downloads/Linux_for_Tegra
./tools/board_automation/boardctl -t thor-jetson recovery
```

This ^^^ returns an error.

Do it manually: from power off, press and hold the middle button, power on while still holding the middle button, press the right button while holding the middle button, wait a few seconds after you see the Ethernet light. Release both buttons.    

```
# Flash
cd ~/Downloads/Linux_for_Tegra
sudo ./flash.sh jetson-agx-orin-devkit internal
```
# dmesg
[dmesg-after-code-change.out](dmesg-after-code-change.out)
