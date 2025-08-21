# Using device tree overlays with Linux/Petalinux

This post will show you how to use device tree overlays in Linux, and discusses Petalinux-specific configuration requirements and bugs.

Device tree overlays consist of one or more device tree fragments that can be dynamically loaded and unloaded at runtime (changes get reflected immediately). This is in contrast to the base device tree, which is generated during the Petalinux build process and embedded into the Linux image at build time.

Device tree overlays get compiled into .dtbo files, and at runtime you can apply the device tree fragments in the dtbo files on top of the base device tree which Linux loaded from image.ub.

Read the article ["Creating device tree overlays"](https://www.centennialsoftwaresolutions.com/post/creating-device-tree-overlays) for instructions on generating a dtbo file.

## Loading and unloading the overlay in Linux

This example assumes you are using an overlay to add a single EEPROM to the device tree (described in [<u><span>"Creating device tree overlays"</span></u>](https://www.centennialsoftwaresolutions.com/post/creating-device-tree-overlays)<u><span>)</span></u>. The mechanism and commands are identical regardless of what you're trying to add to the device tree; only the contents of the .dtbo file will differ.

Copy the dtbo file onto the FPGA. At this point, /sys will not contain any structures related to the EEPROM. Then, load the device tree overlay:

```
$ cd /sys/kernel/config/device-tree/overlays/
$ ls
  => nothing here
$ mkdir bar
$ cd bar
$ ls
  => dtbo, path, status
$ cat status
  => unapplied
$ cat ~/eeprom.dtbo >dtbo
$ cat status
  => applied
```

For each fragment in the overlay file, Linux will have attached the contents of \_\_overlay\_\_ to the target node specified in the fragment.

The device tree fragment in the overlay specified the EEPROM as being compatible with the at24 driver, and therefore Linux will ask the at24 driver to probe for the EEPROM. The probe will succeed and the driver will fully initialize. Linux will also update the structures it exposes in /sys/class/i2c-dev and other relevant /sys folders.

To unload the overlay, just delete the 'bar' folder created in /sys/kernel/config/device-tree/overlays. This change will also be reflected immediately; everything which was created in /sys/class/i2c-dev and in other /sys folders will disappear. Note, you need to use rmdir to delete the folder, not rm -r:

```
$ cd /sys/kernel/config/device-tree/overlays/
$ ls
  => bar
$ rmdir bar
$ ls
  => nothing here
```

## Prerequisite for target labels / symbols

If you use the 'target' property ("/amba/i2c@ff010000/i2c-mux@70/i2c@3") to specify the fragment targets, everything should work as expected. However, if you use the 'target-path' property (<&eeprom\_i2c\_bus>), the kernel may print an error like this when you cat ~/eeprom.dtbo >dtbo:

```
[   99.026101] OF: resolver: no symbols in root of device tree.
[   99.031778] OF: resolver: overlay phandle fixup failed: -22
[   99.037356] create_overlay: Failed to create overlay (err=-22)
```

When Linux loads an overlay which specifies the target-path property as "/amba/i2c@ff010000/i2c-mux@70/i2c@3", it knows where to insert the fragment contents into the base device tree (at that path). However, if you specify the target as a label, at runtime Linux does not know which location that label was referring to. In the base device tree source, channel 3 of the mux did have the label attached to it:

```
eeprom_i2c_bus: i2c@3 {
```

But when dtc compiles the base device tree it strips out label information. The overlay specifies its target as being the node with the label "eeprom\_i2c\_bus," but the base device tree which Linux is using does not contain any information on what node that label refers to. Therefore, Linux can't apply the overlay onto the base device tree.

Passing the -@ flat to dtc will make it retain information about labels when generating a dtb file, which will allow Linux to figure out at runtime what device tree node a label was referring to. You can read more about this mechanism in the Raspberry Pi documentation page linked at the bottom of the article. However, as a person trying to use device tree overlays, simply passing the -@ flag to dtc when compiling the base device tree will allow labels to work.

## Petalinux config

There are a few relevant config flags in Petalinux, described below. The Petalinux Reference Guide may contain more information on these depending on which version of Petalinux you are using.

The device tree contains information about both the PS and PL. Petalinux uses the BSP and Vivado export files to generate a device tree for the PS and PL, then combines them into a single system.dts file which you can find in the images/linux folder after creating a build. Additionally, hardware connected to the FPGA will have its own device tree structure that you must specify in .dtsi files, and Petalinux will integrate these into the system.dtb file. The system.dtb file gets packed into image.ub (which itself might get packed into BOOT.BIN). During boot, U-Boot copies the device tree to a specific location in memory, and Linux reads the device tree from memory when booting.

\- CONFIG\_SUBSYSTEM\_DEVICETREE\_FLAGS (renamed to CONFIG\_SUBSYSTEM\_DEVICETREE\_COMPILER\_FLAGS somewhere around 2020) can be set to "-@". In Petalinux 2019.1, the default value of this option is "" (empty). Somewhere between 2019.1 and 2021.2, the default changed to "-@". Note: this option has no effect in Petalinux 2019.1 due to a bug in Petalinux.

\- CONFIG\_SUBSYSTEM\_DTB\_OVERLAY can be used to change the normal combined (PS and PL) system.dtb that Petalinux generates into a system.dtb which only contains the PS device tree, and an additional pl.dtbo file. Enabling this option should add -@ to the dtc flags.

\- CONFIG\_SUBSYSTEM\_FPGA\_MANAGER: FPGA manager is an FPGA vendor-agnostic Linux framework to allow PL bitstreams to be loaded/changed at runtime from within Linux. Enabling this option should result in Petalinux passing the -@ flag to dtc when compiling the PS device tree. Enabling this option may interfere with, override, or be a prerequisite for the previous two config options. The exact behavior may depend on the Petalinux version.

Notably, if you are using Petalinux 2019.1, and you have PL dtsi files which you include in the build, and you do not want to use FPGA Manager, then by using just the config flags there is no way to have Petalinux pass the -@ flag to dtc. However, there are a few workarounds for this issue which can allow you to use target labels with 2019.1.

## References

\- https://www.raspberrypi.org/documentation/computers/configuration.html#part2 

\- https://joshis1.github.io/embedded_linux/2020/04/01/Linux-Device-tree-overlay.html 

\- Petalinux reference manuals

\- The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]