# Extracting a Petalinux BSP and booting the pre-built FSBL / U-Boot / Linux

A Petalinux BSP is simply a gzipped tar file that contains a preconfigured Petalinux project. A BSP may (and the Xilinx BSPs do) also contain precompiled copies of build outputs that you would get from running petalinux-build in that project.

If you just need to get a "default" FSBL, U-Boot, or Linux running on a board, extracting the BSP and booting the pre-built components is a faster and easier alternative to creating a new Petalinux project from the BSP and doing petalinux-build.

```
$ tar -xzf xilinx-zcu102-2021.2-final.bsp
$ ls
xilinx-zcu102-2021.2

$ cd xilinx-zcu102-2021.2
$ ls
components config.project hardware pre-built project-spec README README.hw

$ ls pre-built/linux/images
bl31.bin BOOT.BIN system.dtb u-boot.elf system.bit zynqmp_fsbl.elf ... etc.

$ petalinux-boot --jtag --pre-built <BOOT_LEVEL>
(see help output for --pre-built for info on booting to FSBL / U-Boot / Linux)
```