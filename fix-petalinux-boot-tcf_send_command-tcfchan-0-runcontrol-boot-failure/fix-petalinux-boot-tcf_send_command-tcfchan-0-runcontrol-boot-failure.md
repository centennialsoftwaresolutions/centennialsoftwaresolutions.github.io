# Fix petalinux-boot “tcf_send_command tcfchan#0 RunControl” Boot Failure on ZC706

![xilinx_logo](xilinx_logo.png)

This post shows a way to fix a petalinux-boot problem whose symptom is a `tcf_send_command tcfchan#0 RunControl` message during boot.

**<u><span>Symptom</span></u>**

After typing `petalinux-boot --jtag --fpga --u-boot --hw_server-url TCP:localhost:3121` on a ZC706

...you see:

{% raw %}
```tcl
INFO: Downloading ELF file: /home/zpfeffer/plxprjs/xilinx-zc706-2019.1/images/linux/zynq_fsbl.elf to the target.
Already stopped                                
  invoked from within
"::tcf::eval -progress {apply {{msg} {puts $msg}}} {tcf_send_command tcfchan#0 RunControl suspend s e JTAG-jsn-JTAG-SMT2-210251A07C1B-4ba00477-0.0}"
  (procedure "::tcf::send_command" line 4)
  invoked from within
"::tcf::send_command $chan RunControl suspend s e [list $ctx]"
  (procedure "stop" line 14)
  invoked from within
"stop"
  (file "/tmp/tmp.8l9aVwfZRt" line 16)
INFO: The XSDB log is as follows
100%  12MB  1.7MB/s 00:07  
mctrlval=30800100
Downloading Program -- /home/zpfeffer/plxprjs/xilinx-zc706-2019.1/images/linux/zynq_fsbl.elf
​	section, .text: 0x00000000 - 0x000114d7
​	section, .handoff: 0x000114d8 - 0x00011523
​	section, .init: 0x00011524 - 0x0001152f
​	section, .fini: 0x00011530 - 0x0001153b
​	section, .rodata: 0x0001153c - 0x00011b83
​	section, .data: 0x00011b88 - 0x00014c77
​	section, .mmu_tbl: 0x00018000 - 0x0001bfff
​	section, .init_array: 0x0001c000 - 0x0001c003
​	section, .fini_array: 0x0001c004 - 0x0001c007
​	section, .rsa_ac: 0x0001c008 - 0x0001d03f
​	section, .bss: 0x0001d040 - 0x0001f271
​	section, .heap: 0x0001f272 - 0x0002127f
​	section, .stack: 0xffff0000 - 0xffffd3ff
100%  0MB  0.4MB/s 00:00  
Setting PC to Program Start Address 0x00000000
Successfully downloaded /home/zpfeffer/plxprjs/xilinx-zc706-2019.1/images/linux/zynq_fsbl.elf
```
{% endraw %}

**<u><span>Fix</span></u>**

Open the Xilinx SDK and disable the breakpoints. Rerun petalinux-boot.

**<u><span>Reference</span></u>**

Xilinx logo from https://twitter.com/xilinxinc 
