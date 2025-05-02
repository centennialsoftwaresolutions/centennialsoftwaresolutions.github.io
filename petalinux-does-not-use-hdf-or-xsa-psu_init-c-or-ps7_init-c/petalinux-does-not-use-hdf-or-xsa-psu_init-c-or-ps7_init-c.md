# PetaLinux does not use HDF or XSA psu_init.c or ps7_init.c

![xilinx_logo](xilinx_logo.png)

This post discusses how PetaLinux Tools does not use the psu_init.c or ps7_init.c from a Vivado exported HDF or XSA file, using one checked in to https://github.com/Xilinx/embeddedsw.git instead and the impact of this. This limitation is not explicitly laid out in at least UG1144 (v2020.2)  PetaLinux Tools Documentation Reference Guide [[link](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2020_2/ug1144-petalinux-tools-reference-guide.pdf)]

## The Problem

psu_init.c configures the Zyqn-7000 or Zynq UltraScale+ MPSoC based on a Vivado design. 

Xilinx uses a static psu_init.c checked into [[link](https://github.com/Xilinx/embeddedsw.git)] @ lib/sw_apps/zynqmp_fsbl/misc/zcu102/psu_init.c [[link](https://github.com/Xilinx/embeddedsw/blob/master/lib/sw_apps/zynqmp_fsbl/misc/zcu102/psu_init.c)] for the ZCU102 or lib/sw_apps/zynq_fsbl/misc/zc702/ps7_init.c for the ZC702 based on a Vivado design they created. 

The Vivado design Xilinx created and used to create psu_init.c is likely, not valid for other designs.

PetaLinux **will not pick up the psu_init.c** file inside exported HDF or XSA, it uses the checked-in one. This means PetaLinux is building with a processor configuration that does not match the configuration exported by Vivado.

This can cause many problems: not booting, "weird" behavior, and missing and "broken" peripherals.

If you are experiencing any of these ensure that you are using the psu_init.c from the exported design, not the one checked into git. 

## Check psu_init.c

The xsa file and the hdf file are zip files. On Linux you can:

```
[root@cad git]# unzip -l project-spec/hw-description/system.xsa
Archive:  project-spec/hw-description/system.xsa
E4FKkdXP57besTmQ17hYJGuu0YlhSqB2QgRlVfn1ub7KE=
  Length      Date    Time    Name
---------  ---------- -----   ----
 23581032  02-04-2021 00:29   design_1_wrapper.bit
      883  02-04-2021 00:29   sysdef.xml
   132272  02-04-2021 00:29   design_1.hwh
    83300  02-04-2021 00:29   design_1_bd.tcl
   911706  02-04-2021 00:29   psu_init.c
  1639391  02-04-2021 00:29   psu_init.h
   911060  02-04-2021 00:29   psu_init_gpl.c
  1638967  02-04-2021 00:29   psu_init_gpl.h
    51684  02-04-2021 00:29   psu_init.html
   873357  02-04-2021 00:29   psu_init.tcl
     1092  02-04-2021 00:29   xsa.xml
     1951  02-04-2021 00:29   xsa.json
---------                     -------
 29826695                     12 files
```

Pipe an extracted psu\_init.c and diff

```
unzip -p project-spec/hw-description/system.xsa psu_init.c | diff -u lib/sw_apps/zynqmp_fsbl/misc/zcu102/psu_init.c -
```

Get an approximation of the differences (I saw 4285)

```
unzip -p /scratch/zpfeffer/2021_02_04_plx/cerebral_bringup/project-spec/hw-description/system.xsa psu_init.c | diff -uw lib/sw_apps/zynqmp_fsbl/misc/zcu102/psu_init.c - | wc -l
```

## Check Build Output

Regardless of the HDF or XSA, PetaLinux will build with the checked0in psu\_init.c or ps7\_init.c:

```
aarch64-none-elf-gcc  -Wall -O0 -g3 -fmessage-length=0  -march=armv8-a -DARMA53_64 -Og -c ../misc/zcu102/psu_init.c -o ../misc/zcu102/psu_init.o -I../misc/zynq
mp_fsbl_bsp/psu_cortexa53_0/include -I. -I../misc/zcu102/a53 -I../misc/zcu102
```

...notice the source of the psu\_init.c file.

Regardless of the HDF or XSA, PetaLinux will set the board to zcu102:

```
echo "Compiling bsp"
Compiling bsp
make -C ../misc BOARD=zcu102 PROC=a53 A53_STATE=64 CROSS_COMP=
```

...notice the source of

## References

Xilinx logo from \[[<u><span>link</span></u>](https://twitter.com/xilinxinc)\]