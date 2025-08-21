# Warning: petalinux-config deletes files

![xilinx_logo](xilinx_logo.png)

This post shares a warning that you may lose your work if you run petalinux-config --get-hw-description in an existing PetaLinux project.

As of 2019.1 running petalinux-config --get-hw-description deletes meta-user/recipes-bsp/device-tree/files/\*.dtsi. It deletes these files without asking if petalinux should delete them.

No warning is given in UG1144 (v2019.1) May 22, 2019

PetaLinux Tools Documentation Reference Guide \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2019_1/ug1144-petalinux-tools-reference-guide.pdf)\]

No warning is given in petalinux-config --help as seen here:

```
Sync hardware description from Vivado export to PetaLinux BSP project:
  $ cd <Vivado_Export_to_SDK_Directory>
  $ petalinux-config --get-hw-description
  It will sync up the HDF/DSA file  from <Vivado_Export_to_SDK_Directory>
  to project-spec/hw-description/ directory.

Sync hardware description inside PetaLinux project but outside Vivado export to SDK directory:
  $ petalinux-config --get-hw-description=<Vivado_Export_to_SDK_Directory>
```

Also, petalinux-config gives the impression that you should use it to keep a PetaLinux project in sync with a hardware design. However, if you do, you will lose work as stated. This differs from the behavior of the SDK, which will update the platform without removing user's work.

## References

Xilinx logo from \[[<u><span>link</span></u>](https://twitter.com/xilinxinc)\]