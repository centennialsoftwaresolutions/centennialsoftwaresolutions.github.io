# SWUpdate a BOOT.bin

![yocto_project_logo](yocto_project_logo.png)

This post shows a way to write a fallback BOOT.bin to QSPI using SWUpdate

**Requirements**

-   This posts uses PetaLinux Tools 2017.4 and Swupdate v2017.1.0.
    
-   If you need help installing PetaLinux Tools 2017.4 take a look: [here](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools).
    
-   This post also requires SWUpdate running on the target.
    
-   If you need help installing SWUpdate into a build using PetaLinux Tools look: [here](http://www.zachpfeffer.com/single-post/Integrate-SWUpdate-into-a-PetaLinux-Project).
    

**Steps**

1\. Create a bootimage.bif

```
image : {
        [bootloader,destination_cpu=a53-0]/home/pfefferz/build/out/zynqmp_fsbl.elf
        [pmufw_image]/home/pfefferz/build/out/pmufw.elf
        [destination_cpu=a53-0, exception_level=el-3, trustzone] /home/pfefferz/build/out/bl31.elf
        [destination_cpu=a53-0, exception_level=el-2] /home/pfefferz/build/out/u-boot.elf
        [load=0x03000000]/home/pfefferz/build/out/uImage.bin
        [load=0x1407f000]/home/pfefferz/build/out/system.dtb
        [load=0x01000000]/home/pfefferz/build/out/uramdisk.image.gz
}
```

2\. Create BOOT.bin

```
$PATH_TO_XSCT/bootgen -log trace -arch zynqmp -image bootimage.bif -w -o BOOT.bin
```

sw-description

```
software =
{ 
	version = "0.1";

	hardware-compatibility: [ "1.0" ]; 
 
	stable:
	{
		alt:
		{

 	       		images: (
       	       		{
				filename = "BOOT.bin.new";
                        	device = "/dev/mtd3";
               		}
			);
		};
		main:
		{
			images: (
                	{
				filename = "BOOT.bin.orig";
                        	device = "/dev/mtd4";
                	}
			);
		};
        };
}
```

3\. Create demo BOOT.bins is you need to

```
cp BOOT.bin BOOT.bin.orig
cp BOOT.bin BOOT.bin.new
```

```
CONTAINER_VER="1.0"
PRODUCT_NAME="my-software"
FILES="sw-description \
       BOOT.bin.new \
       BOOT.bin.orig"
pushd $PETALINUX_BUILD_OUT
for i in $FILES;do
        echo $i;done | cpio -ov -H crc > ${PRODUCT_NAME}_${CONTAINER_VER}.swu
```

```
mkdir testcpio
cd testcpio
cpio -idv < ../*.swu
```

You can extract the cpio archive with this to check it:

4\. Update ./project-spec/meta-user/recipes-bsp/device-tree/files/system-user.dtsi to create the partitions

```
		spi@ff0f0000 {
			u-boot,dm-pre-reloc;
			compatible = "xlnx,zynqmp-qspi-1.0";
			status = "okay";
			clock-names = "ref_clk", "pclk";
			interrupts = <0x0 0xf 0x4>;
			interrupt-parent = <0x4>;
			reg = <0x0 0xff0f0000 0x0 0x1000 0x0 0xc0000000 0x0 0x8000000>;
			#address-cells = <0x1>;
			#size-cells = <0x0>;
			#stream-id-cells = <0x1>;
			iommus = <0x7 0x873>;
			power-domains = <0x16>;
			clocks = <0x3 0x35 0x3 0x1f>;

			flash@0 {
				compatible = "jedec,spi-nor";
				#address-cells = <0x1>;
				#size-cells = <0x1>;
				reg = <0x0>;
				spi-tx-bus-width = <0x4>;
				spi-rx-bus-width = <0x4>;
				spi-max-frequency = <0x55d4a80>;

				partition@bootbin1 {
					label = "bootbin1";
					reg = <0x0 0x1540000>;
				};

				partition@bootbin2 {
					label = "bootbin2";
					reg = <0x1540000 0x1540000>;
				};
			};
		};
```

5\. Rebuild the device-tree

```
petalinux-build -c device-tree
petalinux-build
```

Note: the first build lets you check the device-tree. The second does everything else.

6\. Transfer **my-software\_1.0.swu** to the target

7\. Program the main image with

```
swupdate_unstripped -v -H"0.1":"1.0" -i ~/my-software_1.0.swu -e stable,main
```

8\. Program the alternative image with

```
swupdate_unstripped -v -H"0.1":"1.0" -i ~/my-software_1.0.swu -e stable,alt
```

Note, if you see:

```
software set: stable mode: alt
[NOTIFY] : SWUPDATE running :  [searching_for_image] : Searching image: check -H0.1:1.0 into -H0.1:1.0

[NOTIFY] : SWUPDATE failed [0] ERROR core/swupdate.c : install_from_file : 318 : Image Software cannot be
 read...exiting !
```

```
swupdate_unstripped -vi -H"0.1":"1.0" ~/my-software_1.0.swu -e stable,alt
```

You may be trying to call swupdate with the -**i** in the wrong place. This will cause the above error: 9\. Once you have the main and alt BOOT.bin programmed to test that the first BOOT.bin was booted, you should see in XSCT:

```
xsct% mrd 0XFFCA0010
FFCA0010:   00000000
```

10\. To test that the second BOOT.bin was booted erase the first 32 kB of the mtd3 from the target with:

```
mtd_debug erase /dev/mtd3 0x0 0x80000
```

Reset the device.

Now you should see the following in XSCT:

```
xsct% mrd 0XFFCA0010
FFCA0010:   000002A8
```

**References**

-   Free Online HTML Escape / Unescape Tool - FreeFormatter.com @ [link](http://www.freeformatter.com/html-escape.html)
    
-   The Xilinx + Yocto + DENX graphic is an amalgamation of [Xilinx](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png), [Yocto](http://www.yoctoproject.org/docs/2.0/yocto-project-qs/yocto-project-qs.html) and DENX icons.