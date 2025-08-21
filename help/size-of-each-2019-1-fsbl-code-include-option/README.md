# Size of Each 2019.1 FSBL Code Include Option

![xilinx_logo](xilinx_logo.png)

This post lists the output of aarch64-none-elf-size fsbldebug.elf |tee "fsbldebug.elf.size" for each value of FSBL code include options in xfsbl\_config.h. Excluding these items may be required if you are trying to debug the FSBL since the default configuration will not build if debug is enabled.

**<u><span>Build Flags and Options Used</span></u>**

ARM v8 gcc compiler > Miscellaneous

set to:

\-c -fmessage-length=0 -MT"$@" -Og

standalone > zynqmp\_fsbl\_bsp

set to:

false

**<u><span>Sizes</span></u>**

| Set to 0U to  Include           | text   | data | bss   | dec    | hex   |
| :------------------------------ | :----- | :--- | :---- | :----- | :---- |
| None (All Excluded)             | 104004 | 5000 | 18744 | 127748 | 1f304 |
|                                 |        |      |       |        |       |
| FSBL_NAND_EXCLUDE_VAL           | 104004 | 5000 | 18744 | 127748 | 1f304 |
| Delta from None (All Excluded)  | 0      | 0    | 0     | 0      |       |
|                                 |        |      |       |        |       |
| FSBL_QSPI_EXCLUDE_VAL           | 112268 | 5016 | 19192 | 136476 | 2151c |
| Delta from None (All Excluded)  | 8264   | 16   | 448   | 8728   |       |
|                                 |        |      |       |        |       |
| FSBL_SD_EXCLUDE_VAL             | 117644 | 5040 | 21688 | 144372 | 2151c |
| Delta from None (All Excluded)  | 13640  | 40   | 2944  | 16624  |       |
|                                 |        |      |       |        |       |
| FSBL_SECURE_EXCLUDE_VAL         | 113764 | 5008 | 23928 | 142700 | 22d6c |
| Delta from None (All Excluded)  | 9760   | 8    | 5184  | 14952  |       |
|                                 |        |      |       |        |       |
| FSBL_BS_EXCLUDE_VAL             | 105364 | 5000 | 71864 | 182228 | 2c7d4 |
| Delta from None (All Excluded)  | 1360   | 0    | 53120 | 54480  |       |
|                                 |        |      |       |        |       |
| FSBL_EARLY_HANDOFF_EXCLUDE_VAL  | 104324 | 5000 | 18744 | 128068 | 1f444 |
| Delta from None (All Excluded)  | 320    | 0    | 0     | 320    |       |
|                                 |        |      |       |        |       |
| FSBL_WDT_EXCLUDE_VAL            | 105364 | 5016 | 18744 | 129124 | 1f864 |
| Delta from None (All Excluded)  | 1360   | 16   | 0     | 1376   |       |
|                                 |        |      |       |        |       |
| FSBL_PERF_EXCLUDE_VAL           | 104556 | 5008 | 18744 | 128308 | 1f534 |
| Delta from None (All Excluded)  | 552    | 8    | 0     | 560    |       |
|                                 |        |      |       |        |       |
| FSBL_A53_TCM_ECC_EXCLUDE_VAL    | 104068 | 5000 | 18744 | 127812 | 1f344 |
| Delta from None (All Excluded)  | 64     | 0    | 0     | 64     |       |
|                                 |        |      |       |        |       |
| FSBL_PL_CLEAR_EXCLUDE_VAL       | 104004 | 5000 | 18744 | 127748 | 1f304 |
| Delta from None (All Excluded)  | 0      | 0    | 0     | 0      |       |
|                                 |        |      |       |        |       |
| FSBL_USB_EXCLUDE_VAL            | 115100 | 5144 | 23160 | 143404 | 2302c |
| Delta from None (All Excluded)  | 11096  | 144  | 4416  | 15656  |       |
|                                 |        |      |       |        |       |
| FSBL_PROT_BYPASS_EXCLUDE_VAL    | 104004 | 5000 | 18744 | 127748 | 1f304 |
| Delta from None (All Excluded)  | 0      | 0    | 0     | 0      |       |
|                                 |        |      |       |        |       |
| FSBL_PARTITION_LOAD_EXCLUDE_VAL | 104004 | 5000 | 18744 | 127748 | 1f304 |
| Delta from None (All Excluded)  | 0      | 0    | 0     | 0      |       |
|                                 |        |      |       |        |       |
| FSBL_FORCE_ENC_EXCLUDE_VAL      | 104004 | 5000 | 18744 | 127748 | 1f304 |
| Delta from None (All Excluded)  | 0      | 0    | 0     | 0      |       |
|                                 |        |      |       |        |       |
| FSBL_DDR_SR_EXCLUDE_VAL         | 104260 | 5000 | 18744 | 128004 | 1f404 |
| Delta from None (All Excluded)  | 256    | 0    | 0     | 256    |       |

**<u><span>Default (not buildable)</span></u>**

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_NAND\_EXCLUDE\_VAL (0U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_QSPI\_EXCLUDE\_VAL (0U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_SD\_EXCLUDE\_VAL (0U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_SECURE\_EXCLUDE\_VAL (0U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_BS\_EXCLUDE\_VAL (0U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_EARLY\_HANDOFF\_EXCLUDE\_VAL (1U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_WDT\_EXCLUDE\_VAL (0U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_PERF\_EXCLUDE\_VAL (1U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_A53\_TCM\_ECC\_EXCLUDE\_VAL (1U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_PL\_CLEAR\_EXCLUDE\_VAL (1U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_USB\_EXCLUDE\_VAL (1U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_PROT\_BYPASS\_EXCLUDE\_VAL (1U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_PARTITION\_LOAD\_EXCLUDE\_VAL (0U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_FORCE\_ENC\_EXCLUDE\_VAL (0U)

**[#define](https://www.centennialsoftwaresolutions.com/blog/hashtags/define)** FSBL\_DDR\_SR\_EXCLUDE\_VAL (1U)

Error:

```
Building target: fsbldebug.elf
Invoking: ARM v8 gcc linker
aarch64-none-elf-gcc -n -Wl,-T -Wl,../src/lscript.ld -L../../fsbldebug_bsp/psu_cortexa53_0/lib -o "fsbldebug.elf"  ./src/psu_init.o ./src/xfsbl_authentication.o ./src/xfsbl_board.o ./src/xfsbl_bs.o ./src/xfsbl_csu_dma.o ./src/xfsbl_ddr_init.o ./src/xfsbl_dfu_util.o ./src/xfsbl_exit.o ./src/xfsbl_handoff.o ./src/xfsbl_hooks.o ./src/xfsbl_image_header.o ./src/xfsbl_initialization.o ./src/xfsbl_main.o ./src/xfsbl_misc.o ./src/xfsbl_misc_drivers.o ./src/xfsbl_nand.o ./src/xfsbl_partition_load.o ./src/xfsbl_plpartition_valid.o ./src/xfsbl_qspi.o ./src/xfsbl_rsa_sha.o ./src/xfsbl_sd.o ./src/xfsbl_translation_table.o ./src/xfsbl_usb.o   -Wl,--start-group,-lxil,-lgcc,-lc,--end-group -Wl,--start-group,-lxilffs,-lxil,-lgcc,-lc,--end-group -Wl,--start-group,-lxilsecure,-lxil,-lgcc,-lc,--end-group -Wl,--start-group,-lxilpm,-lxil,-lgcc,-lc,--end-group
/tools/Xilinx/SDK/2019.1/gnu/aarch64/lin/aarch64-none/bin/../lib/gcc/aarch64-none-elf/8.2.0/../../../../aarch64-none-elf/bin/ld: address 0xfffeadc8 of fsbldebug.elf section `.dup_data' is not within region `psu_ocm_ram_0_S_AXI_BASEADDR'
makefile:36: recipe for target 'fsbldebug.elf' failed
/tools/Xilinx/SDK/2019.1/gnu/aarch64/lin/aarch64-none/bin/../lib/gcc/aarch64-none-elf/8.2.0/../../../../aarch64-none-elf/bin/ld: address 0xfffeadc8 of fsbldebug.elf section `.dup_data' is not within region `psu_ocm_ram_0_S_AXI_BASEADDR'
/tools/Xilinx/SDK/2019.1/gnu/aarch64/lin/aarch64-none/bin/../lib/gcc/aarch64-none-elf/8.2.0/../../../../aarch64-none-elf/bin/ld: address 0xfffeadc8 of fsbldebug.elf section `.dup_data' is not within region `psu_ocm_ram_0_S_AXI_BASEADDR'
/tools/Xilinx/SDK/2019.1/gnu/aarch64/lin/aarch64-none/bin/../lib/gcc/aarch64-none-elf/8.2.0/../../../../aarch64-none-elf/bin/ld: address 0xfffeadc8 of fsbldebug.elf section `.dup_data' is not within region `psu_ocm_ram_0_S_AXI_BASEADDR'
/tools/Xilinx/SDK/2019.1/gnu/aarch64/lin/aarch64-none/bin/../lib/gcc/aarch64-none-elf/8.2.0/../../../../aarch64-none-elf/bin/ld: address 0xfffeadc8 of fsbldebug.elf section `.dup_data' is not within region `psu_ocm_ram_0_S_AXI_BASEADDR'
/tools/Xilinx/SDK/2019.1/gnu/aarch64/lin/aarch64-none/bin/../lib/gcc/aarch64-none-elf/8.2.0/../../../../aarch64-none-elf/bin/ld: section .handoff_params VMA [00000000fffe9e00,00000000fffe9e87] overlaps section .dup_data VMA [00000000fffe9a00,00000000fffeadc7]
collect2: error: ld returned 1 exit status
make: *** [fsbldebug.elf] Error 1
```

**<u><span>References</span></u>**

-   SDK - How to debug FSBL code \[[<u><span>link</span></u>](https://www.xilinx.com/support/answers/71671.html)\]
    
-   Zynq UltraScale+ FSBL <u><span>[</span></u>[<u><span>link</span></u>](https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/18842019/Zynq+UltraScale+FSBL#ZynqUltraScale+FSBL-I%E2%80%99munabletodebugFSBLinVitis.AnychangeinoptimizationsusedbyFSBL)<u><span>]</span></u>
    
-   ZynqMP FSBL Build Failure with FSBL\_DEBUG\_INFO <u><span>[</span></u>[<u><span>link</span></u>](https://forums.xilinx.com/t5/Embedded-Development-Tools/ZynqMP-FSBL-Build-Failure-with-FSBL-DEBUG-INFO/td-p/984427)<u><span>]</span></u>
    
-   text, data and bss: Code and Data Size Explained \[[<u><span>link</span></u>](https://mcuoneclipse.com/2013/04/14/text-data-and-bss-code-and-data-size-explained/)\]
    
-   HTML Tables generator \[[<u><span>link</span></u>](https://www.tablesgenerator.com/html_tables)\]
    
-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]