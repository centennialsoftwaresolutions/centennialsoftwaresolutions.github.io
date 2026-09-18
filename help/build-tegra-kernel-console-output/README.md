# jetson_39.2.1 Linux for Tegra (L4T) make Console Output Reference

## Sync source 
```
$ cd <install-path>/Linux_for_Tegra/source
./source_sync.sh -k -t jetson_39.2.1
```

## Get toolchain
```
mkdir $HOME/l4t-gcc
cd $HOME/l4t-gcc
wget https://developer.nvidia.com/downloads/embedded/L4T/r38_Release_v2.0/release/x-tools.tbz2
tar xf x-tools.tbz2
export CROSS_COMPILE=$HOME/l4t-gcc/x-tools/aarch64-none-linux-gnu/bin/aarch64-none-linux-gnu-
```

## Make outputs
`make -C kernel` console output from clean: [make-Ckernel.out](make-Ckernel.out)

`make -C kernel` console output after building: [make-Ckernel-alreadybuilt.out](make-Ckernel-alreadybuilt.out) 

`make -C kernel clean` console output after full buid: [make-Ckernel-clean-alreadybuilt.out](make-Ckernel-clean-alreadybuilt.out)

## Make install outputs
```
demo-user@demo:~/Downloads/Linux_for_Tegra/source$ 

export INSTALL_MOD_PATH=/home/demo-user/Downloads/Linux_for_Tegra/rootfs
sudo -E make install -C kernel
cp kernel/kernel-noble/arch/arm64/boot/Image /home/demo-user/Downloads/Linux_for_Tegra/kernel/Image
```
output: [sudo_-E_make_install_-C_kernel.out](sudo_-E_make_install_-C_kernel.out)

## Make output tree modules
```
demo-user@demo:~/Downloads/Linux_for_Tegra/source$ 

export CROSS_COMPILE=$HOME/l4t-gcc/x-tools/aarch64-none-linux-gnu/bin/aarch64-none-linux-gnu-
export KERNEL_HEADERS=$PWD/kernel/kernel-noble
export kernel_name=noble
make modules
```
output: [make_modules.out](make modules.out)
