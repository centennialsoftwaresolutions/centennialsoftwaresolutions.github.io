# Flashing QSPI over JTAG on Zynq without using GUI

This post describes how to put a BOOT.BIN into QSPI over JTAG, on the console instead of with the graphical program\_flash tool.

If you want to use the Xilinx SDK GUI tool, see step 9 of [<u><span>this post</span></u>](https://www.centennialsoftwaresolutions.com/post/bare-metal-application-boot-from-flash-on-the-xilinx-zynq-7000-of-the-zc702).

You still need to have the Xilinx SDK or Vitis installed for the console process. These steps have been tested on 2021.2 (currently the newest release) and are also confirmed to work on older versions at least as far back as 2018.1.

On older versions of the Xilinx toolkit, the hw\_server and program\_flash tools are in the SDK's bin folder:

```
$ cd /tools/Xilinx/SDK/2018.1/bin   # your installation may be in a different location
$ ls
xsct     xsdk     hw_server     bootgen     program_flash     ...
```

On newer versions, they're in Vitis's bin folder:

```
$ cd /tools/Xilinx/Vitis/2021.2/bin
$ ls
xsct     xsdk     hw_server     bootgen     program_flash     ...
```

**Prerequisites:**

You will need the file you want to put into the flash (usually a BOOT.BIN), as well as the FSBL ELF.

-   If you're using Petalinux: Petalinux will create the FSBL ELF in the images/linux folder, as either zynq\_fsbl.elf or zynqmp\_fsbl.elf.
    
-   For Xilinx dev boards such as the ZC702 and ZCU102, you can get the ELF from the Petalinux BSP that Xilinx provides. After [<u><span>extracting the BSP</span></u>](https://www.centennialsoftwaresolutions.com/post/extracting-a-petalinux-bsp), the pre-built/linux/images folder will contain the ELF (again, it'll be named either zynq\_fsbl.elf or zynqmp\_fsbl.elf).
    
-   Other boards / SOMs may also include a pre-built FSBL in their BSP.
    
-   If you're not using Petalinux, you can build the FSBL manually ([<u><span>Xilinx page</span></u>](https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/18841798/Build+FSBL), [<u><span>Centennial post on building it through the command line</span></u>](https://www.centennialsoftwaresolutions.com/post/command-line-2019-1-xilinx-fsbl-rebuild-and-test), [<u><span>Centennial post on building it in Vitis</span></u>](https://www.centennialsoftwaresolutions.com/post/fsbl-creation-and-source-debug-in-xilinx-vitis-2019-2))
    

The program\_flash tool loads the FSBL onto the Zynq over JTAG and uses that FSBL to operate on the QSPI. **You will need to set the physical boot mode pins to JTAG and reset the system**. Using the CRL\_APB.BOOT\_MODE\_USER register as a workaround will not work.

You will also need to know which type of QSPI you have.

-   On the ZCU102, the QSPI is in the dual parallel configuration. The help output of the program\_flash utility contains a list of all the supported flash types - for the ZCU102 (Zynq MPSoC) we need to use "qspi\_dual\_parallel" as the flash type.
    
-   program\_flash can also operate on non-Zynq FPGAs. In that scenario, you'll need to know the exact part number of the flash on your board. Run "./program\_flash -partlist" to have program\_flash list the names of all the supported QSPI chips.
    

**Programming the QSPI:**

First, start the Xilinx hardware server. You can do this in two ways from the SDK's bin folder:

```
./hw_server
```

or

```
./xsct
% connect
```

Resulting in:

```
The hardware server will print, in both cases:
INFO: hw_server application started
INFO: To connect to this hw_server instance use url: TCP:127.0.0.1:3121
```

In another terminal, run the program\_flash tool:

```
./program_flash \
 -f /path/to/your/BOOT.BIN \
 -fsbl /path/to/your/zynq[mp]_fsbl.elf \
 -flash_type qspi_dual_parallel \
 -offset 0 \
 -cable type xilinx_tcf url tcp:localhost:3121
```

You'll need to adjust all of these arguments to match your system's configuration.

The -offset argument (bytes) lets you place the BOOT.BIN into an arbitrary location in the QSPI.

Additionally, you can add two more arguments:

-   \-blank\_check will verify that the erase operation was successful.
    
-   \-verify will read back the contents of QSPI and check that the BOOT.BIN was written correctly.
    

It's possible to run program\_flash within xsct, so that you don't need two terminals:

```
./xsct
% connect
% exec program_flash -f /path/to/your/BOOT.BIN ... (all other args)
```

One issue with this method is that the logs that program\_flash writes to the console won't be visible in real-time. Instead, all the output will be printed at once when program\_flash exits.

Alternatively, you could run hw\_server and move it to the background with ctrl-z bg.