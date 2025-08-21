# 2019.1 FSBL Command Line Option Decode Example: aarch64-none-elf-gcc ... "../src/xfsbl_main.c"

![xilinx_logo](xilinx_logo.png)

This post shows how to decode what each command-line option used in aarch64-none-elf-gcc -DARMA53\_64 -Wall -O0 -g3 -I"/home/demo/xsdk/fsblws/ZCU102\_hw\_platform" -c -fmessage-length=0 -MT"src/xfsbl\_main.o" -Og -I../../fsbldebug\_bsp/psu\_cortexa53\_0/include -MMD -MP -MF"src/xfsbl\_main.d" -MT"src/xfsbl\_main.o" -o "src/xfsbl\_main.o" "../src/xfsbl\_main.c" means. It also lists links to resources for related command line options. It also lists where to find **aarch64-none-elf-gcc** in the Vivado/SDK install and how to find the version so that the correct documentation can be consulted.

**<u><span>Command Line</span></u>**

aarch64-none-elf-gcc -DARMA53\_64 -Wall -O0 -g3 -I"/home/demo/xsdk/fsblws/ZCU102\_hw\_platform" -c -fmessage-length=0 -MT"src/xfsbl\_main.o" -Og -I../../fsbldebug\_bsp/psu\_cortexa53\_0/include -MMD -MP -MF"src/xfsbl\_main.d" -MT"src/xfsbl\_main.o" -o "src/xfsbl\_main.o" "../src/xfsbl\_main.c"

**<u><span>Expanded</span></u>**

aarch64-none-elf-gcc

\-DARMA53\_64 -Wall

\-O0

\-g3

\-I"/home/demo/xsdk/fsblws/ZCU102\_hw\_platform"

\-c

\-fmessage-length=0

\-MT"src/xfsbl\_main.o"

\-Og

\-I../../fsbldebug\_bsp/psu\_cortexa53\_0/include

\-MMD

\-MP

\-MF"src/xfsbl\_main.d"

\-MT"src/xfsbl\_main.o"

\-o "src/xfsbl\_main.o"

"../src/xfsbl\_main.c"

**<u><span>Table</span></u>**

| Component                                                    | Description                                                  |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| aarch64-none-elf-gcc                                         | aarch64-none-elf-gcc  (GCC) 8.2.0                            |
| -DARMA53_64                                                  | https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Preprocessor-Options.html#Preprocessor-Options        -D name    Predefine  name as a macro, with definition 1.        ARMA53_64 is used  in the FSBL, like (xfsbl_handoff.c)        if (XGet_Zynq_UltraMp_Platform_info() == (u32)(0X2U))    { XFsbl_Printf(DEBUG_GENERAL,"Exit from FSBL. \n\r");    #ifdef ARMA53_64    XFsbl_Out32(0xFFFC0000U,  0x14000000U);    #else    XFsbl_Out32(0xFFFC0000U,  0xEAFFFFFEU);    #endif    XFsbl_Exit(0xFFFC0000U,  XFSBL_HANDOFFEXIT);    }  else {    /**    * Exit from FSBL    */    XFsbl_HandoffExit(0U,  XFSBL_NO_HANDOFFEXIT);    } |
| -Wall                                                        | https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Warning-Options.html#Warning-Options        all the  warnings about constructions that some users consider questionable |
| -O0                                                          | https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Optimize-Options.html#Optimize-Options        Reduce  compilation time and make debugging produce the expected results. This is the  default. |
| -g3                                                          | https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Debugging-Options.html#Debugging-Options          Level 3  includes extra information, such as all the macro definitions present in the  program. Some debuggers support macro expansion when you use -g3. |
| -I"/home/demo/xsdk/fsblws/ZCU102_hw_platform"                |                                                              |
| -c                                                           | -c Compile and assemble,  but do not link.                   |
| -fmessage-length=0                                           | Try to format  error messages so that they fit on lines of about n characters. If n is zero,  then no line-wrapping is done; each error message appears on a single line.  This is the default for all front ends. |
| -MT"src/xfsbl_main.o"                                        | See below.                                                   |
| -Og                                                          | https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Optimize-Options.html#Optimize-Options        -Og    Optimize  debugging experience. -Og enables optimizations that do not interfere with  debugging. It should be the optimization level of choice for the standard  edit-compile-debug cycle, offering a reasonable level of optimization while  maintaining fast compilation and a good debugging experience. |
| -I../../fsbldebug_bsp/psu_cortexa53_0/include  -MMD -MP -MF"src/xfsbl_main.d" | https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Directory-Options.html#index-I        Add the  directory dir to the list of directories to be searched for header files  during preprocessing. |
| -MMD                                                         | https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Preprocessor-Options.html#Preprocessor-Options        -MMD    Like -MD  except mention only user header files, not system header files.        -MD is  equivalent to -M -MF file, except that -E is not implied. |
| -MP                                                          | This option  instructs CPP to add a phony target for each dependency other than the main  file, causing each to depend on nothing. |
| -MF"src/xfsbl_main.d"                                        | When used with  -M or -MM, specifies a file to write the dependencies to. |
| -MT"src/xfsbl_main.o"                                        | https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Preprocessor-Options.html#Preprocessor-Options        Change the  target of the rule emitted by dependency generation. |
| -o  "src/xfsbl_main.o"                                       | -o <file> Place the output into  <file>.                     |
| "../src/xfsbl_main.c"                                        | aarch64-none-elf-gcc  [options] file...                      |

**<u><span>Find the Version of aarch64-none-elf-gcc in the SDK install inside Vivado</span></u>**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Run:

**find /tools/Xilinx/ -name aarch64-none-elf-gcc**

You should see:

/tools/Xilinx/SDK/2019.1/gnu/aarch64/lin/aarch64-none/bin/aarch64-none-elf-gcc

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Run:

**/tools/Xilinx/SDK/2019.1/gnu/aarch64/lin/aarch64-none/bin/aarch64-none-elf-gcc --version**

You should see:

aarch64-none-elf-gcc (GCC) **8.2.0**

Copyright (C) 2018 Free Software Foundation, Inc.

This is free software; see the source for copying conditions. There is NO

warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

**<u><span>Resources</span></u>**

GCC 8.4.0 Option Summary \[[<u><span>link</span></u>](https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Option-Summary.html#Option-Summary)\]

GCC 8.4.0 Option Index \[[<u><span>link</span></u>](https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/Option-Index.html#Option-Index)\]

GCC 8.4.0 AArch64 Options \[[<u><span>link</span></u>](https://gcc.gnu.org/onlinedocs/gcc-8.4.0/gcc/AArch64-Options.html#AArch64-Options)\]

**<u><span>References</span></u>**

-   HTML Tables generator \[[<u><span>link</span></u>](https://www.tablesgenerator.com/html_tables)\]
    
-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]