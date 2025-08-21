# Change the Boot Mode of the Xilinx Zynq UltraScale+ MPSoC from XSCT

![xilinx_logo](xilinx_logo.png)

This post show you how to change the boot mode of the Zynq UltraScale+ MPSoC from XSCT.

**TL;DR**

The following sequence changes to JTAG boot mode:

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x0100 
rst -system
```

**Thanks!**

Big thanks to Krishna Chaitanya ([LinkedIn](http://www.linkedin.com/in/krishna-chaitanya-p-34686a3a/)) for sharing this awesome method!

**Motivation**

Being able to change the boot mode remotely helps debug. Typically, the user will change boot from from whatever it is to JTAG Boot to load a custom build.

By writing the new boot mode to BOOT\_MODE\_USER (CRL\_APB) Register @ 0xff5e0200 and triggering a software reset, the MPSoC will use the mode you wrote, not the mode of the strapping pins.

**Sequences**

Here are sequences for each boot mode:

JTAG

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x0100 
rst -system
```

Quad-SPI (24b)

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x1100 
rst -system
```

Quad-SPI (32b)

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x2100 
rst -system
```

SD0 (2.0)

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x3100 
rst -system
```

NAND

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x4100 
rst -system
```

SD1 (2.0)

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x5100 
rst -system
```

eMMC (1.8V)

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x6100 
rst -system
```

USB (2.0)

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x7100 
rst -system
```

PJTAG (MIO [#0](https://www.centennialsoftwaresolutions.com/blog/hashtags/0))

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x8100 
rst -system
```

PJTAG (MIO [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1))

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0x9100 
rst -system
```

SD1 LS (3.0)

```
targets -set -nocase -filter {name =~ "*PSU*"}
stop
mwr  0xff5e0200 0xe100 
rst -system
```

**References**

-   Zynq UltraScale+ MPSoC Register Reference @ [link](http://www.xilinx.com/html_docs/registers/ug1087/ug1087-zynq-ultrascale-registers.html)
    
-   CSS Tables @ [link](http://www.w3schools.com/css/css_table.asp)
    

Boot Modes

| Boot Mode      | Mode Pins [3:0] | Pin Location | Non-Secure | Secure | Signed | CSU Mode | Description                                                  |
| :------------- | :-------------- | :----------- | :--------- | :----- | :----- | :------- | :----------------------------------------------------------- |
| PS JTAG        | 0000            | JTAG         | Yes        | No     | No     | Slave    | PSJTAG interface, PS dedicated pins.                         |
| Quad-SPI (24b) | 0001            | MIO[12:0]    | Yes        | Yes    | Yes    | Master   | 24-bit addressing (QSPI24).                                  |
| Quad-SPI (32b) | 0010            | MIO[12:0]    | Yes        | Yes    | Yes    | Master   | 32-bit addressing (QSPI32).                                  |
| SD0 (2.0)      | 0011            | MIO[25:13]   | Yes        | Yes    | Yes    | Master   | SD 2.0.                                                      |
| NAND           | 0100            | MIO[25:09]   | Yes        | Yes    | Master | Master   | Requires 8-bit data bus width.                               |
| SD1 (2.0)      | 0101            | MIO[51:38]   | Yes        | Yes    | Yes    | Master   | SD 2.0.                                                      |
| eMMC (1.8V)    | 0110            | MIO[22:13]   | Yes        | Yes    | Yes    | Master   | eMMC version 4.5 at 1.8V.                                    |
| USB0 (2.0)     | 0111            | MIO[52:63]   | Yes        | Yes    | Yes    | Slave    | USB 2.0 only.                                                |
| PJTAG (MIO #0) | 1000            | MIO[29:26]   | Yes        | No     | No     | Slave    | PJTAG connection 0 option.                                   |
| PJTAG (MIO #1) | 1001            | MIO[15:12]   | Yes        | No     | No     | Slave    | PJTAG connection 1 option.                                   |
| SD1 LS (3.0)   | 1110            | MIO[51:39]   | Yes        | Yes    | Yes    | Master   | "SD 3.0 with a required SD 3.0 compliant voltage level shifter. |

Table is available [here](http://drive.google.com/file/d/1oHgbB3fgOkniFJ1nVzL85juNY9vhlLTW/view?usp=sharing) as an Excel.

0xff5e0200 Documentation

BOOT\_MODE\_USER (CRL\_APB) Register

_Description_

| Register Name    | BOOT_MODE_USER                 |
| ---------------- | ------------------------------ |
| Relative Address | 0x00000200                     |
| Absolute Address | 0xFF5E0200 (CRL_APB)           |
| Width            | 20                             |
| Type             | mixed                          |
| Reset Value      | 0x00000000                     |
| Description      | Software controlled BOOT MODE. |

_BOOT\_MODE\_USER (CRL\_APB) Register Bit-Field Summary_

| Field Name    | Bits  | Type | Reset Value | Description                                                  |
| :------------ | :---- | :--- | :---------- | :----------------------------------------------------------- |
| Reserved      | 19:16 | rw   | 0x0         | reserved                                                     |
| alt_boot_mode | 15:12 | rw   | 0x0         | Alternative Boot Mode value that can be put into the [boot_mode] field. |
| Reserved      | 11:9  | rw   | 0x0         | reserved                                                     |
| use_alt       | 8     | rw   | 0x0         | Used to control which value is in the [boot_mode] field. 0: POR reset value. 1: Software value [alt_boot_mode] bit field. |
| Reserved      | 7:4   | rw   | 0x0         | reserved                                                     |
| boot_mode     | 3:0   | ro   | 0           | Boot Mode values from the mode pins captured at POR until software asserts the [use_alt] bit. Once that happens, this bit field will contain the [alt_boot_mode] value written by software. Since the initial value is defined from the Boot Mode pins, the reset value is listed as 'X. |