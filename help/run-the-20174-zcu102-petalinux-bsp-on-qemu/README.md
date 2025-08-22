# Run the 2017.4 ZCU102 PetaLinux BSP on QEMU

![xilinx_logo](xilinx_logo.png)

This post lists the steps to run the ZCU102 PetaLinux BSP on QEMU and rebuild it.

**Prerequisites**

PetaLinux 2017.4 installed. If you need help click [here](http://www.zachpfeffer.com/single-post/Download-and-Install-Xilinxs-20174-PetaLinux-Tools).

**Steps**

**1.** Download ZCU102 BSP (prod-silicon) from [link](http://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html).

You may also be able to get the BSP directly at [direct link](http://xilinx.entitlenow.com/AXMetrics/retrieveProduct?token=Bl4Aa%2Fi3WhrqYAGHzdAQezvPaLNAPWsKOmAIZiVSzAa%2BLifsKswBZJxuq3s%2B3%2BVJeGVrGVISDEnlP%2BosiAYnAa1wD7MTlnE%2Fd8Z%2FfSNDGKquXmsiYpz2U%2BsmFyhlXPHxn6iYGJ5o3VbZfOQTEKjSTLdD3n6FfHF3qOSqT9BSx%2BT3XsKxMnajOKlLctBmi1TFghe0xNb0leUTQ4mRbi9Tr829MWYb58FSENI%2B9HgzRBgSeLQBM7TKo9QdbiLdBuNXqT1yFe27BuEJ9a4awx3tgFumZAn3CUfB&akdm=1&archive=209898193&filename=xilinx-zcu102-v2017.4-final.bsp).

**2.** cd into the directory you download the BSP to.

**3.** Setup the PetaLinux Tools environment:

```
LOCALTOOLS=$HOME/tools
source $LOCALTOOLS/opt/pkg/petalinux/settings.sh
source $HOME/set_petalinux_env.sh
which make
which petalinux-create
```

**4.** Create the PetaLinux Tools project based on the BSP

```
petalinux-create -t project -s xilinx-zcu102-v2017.4-final.bsp --name zcu102qemu
```

This command took about 15 seconds on my machine

**5.** Boot it on QEMU

```
cd zcu102qemu
petalinux-boot --qemu --prebuilt 3
```

After a minute or two you should see:

```
xilinx-zcu102-2017_4 login:
```

Type: root as the username and root as the password.

A [log](http://docs.google.com/document/d/1qhee_o8ttoYcbqpoZtlqTKx9lrlZARAWK2ELgzLFZmo/edit?usp=sharing) of this boot.

**6.** Exit QEMU

To exit QEMU type _Control-a c_ then type _quit_

Control-a c enters the monitor (you can type Control-a c again to exit the monitor and get back to the emulated session).

**Rebuild and rerun the BSP**

**1.** Enter the directory and type petalinux-build

```
cd zcu102qemu # if you're not in the directory 
petalinux-build
```

**2.** Run petalinux-boot with the **\--kernel** option

```
petalinux-boot --qemu --kernel
```

A [log](http://docs.google.com/document/d/1-Q5ccM6rp_R7cLVr95pvKlpv2SKJpzsOwIqkDRxy0kQ/edit?usp=sharing) of this boot.

**References**

-   PetaLinux Tools Documentation Reference Guide [UG1144](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_4/ug1144-petalinux-tools-reference-guide.pdf) (v2017.4) December 20, 2017
    
-   PetaLinux Tools Documentation Workflow Tutorial [UG1156](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_4/ug1156-petalinux-tools-workflow-tutorial.pdf) (v2017.4) December 20, 2017
    
-   Logo via [https://twitter.com/xilinxinc](http://twitter.com/xilinxinc) at [link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)
    

**Watch Out!**

After you rebuild the PetaLinux BSP I had to use:

```
petalinux-boot --qemu --kernel
```

If I used:

```
petalinux-boot --qemu --prebuilt 3
```

**It Didn't Work!** Here's the [boot log](http://docs.google.com/document/d/1N0CB_5985z_tT70u24YqQe0je4agfuIrloHGUUnPTDw/edit?usp=sharing).

Here's the dump.

**I get the following dumps when I try to boot:**

```
[   62.310538] [drm] Initialized xilinx_drm 1.0.0 20130509 on minor 0
[   62.497637] xilinx-dp-snd-card dp_snd_card: ASoC: CPU DAI (null) not registered
[   62.961746] input: gpio-keys as /devices/platform/gpio-keys/input/input0
[   84.328745] INFO: rcu_sched self-detected stall on CPU
[   84.336132] 	3-...: (1 GPs behind) idle=5fd/140000000000001/0 softirq=1060/1061 fqs=683 
[   84.357279] 	 (t=5250 jiffies g=199 c=198 q=20)
[   84.384635] Task dump for CPU 3:
[   84.386828] swapper/0       R  running task        0     1      0 0x00000002
[   84.388343] Call trace:
[   84.393291] [] dump_backtrace+0x0/0x198
[   84.405347] [] show_stack+0x14/0x20
[   84.425668] [] sched_show_task+0x94/0xf0
[   84.445268] [] dump_cpu_task+0x40/0x50
[   84.472441] [] rcu_dump_cpu_stacks+0xb4/0xe8
[   84.494474] [] rcu_check_callbacks+0x67c/0x860
[   84.498875] [] update_process_times+0x34/0x60
[   84.500659] [] tick_sched_handle.isra.4+0x38/0x48
[   84.503103] [] tick_sched_timer+0x44/0x90
[   84.506154] [] __hrtimer_run_queues+0xf0/0x178
[   84.529447] [] hrtimer_interrupt+0x98/0x1c8
[   84.539123] [] arch_timer_handler_phys+0x30/0x40
[   84.549398] [] handle_percpu_devid_irq+0x78/0x128
[   84.650834] [] generic_handle_irq+0x24/0x38
[   84.726778] [] __handle_domain_irq+0x5c/0xb8
[   84.805371] [] gic_handle_irq+0x64/0xc0
[   84.909658] Exception stack(0xffffffc87b89bb40 to 0xffffffc87b89bc70)
[   84.971321] bb40: 0000000000000003 ffffffc87ffa52b8 0000000000000000 0000000000000002
[   85.058601] bb60: 0000000000000002 0000000000000007 ffffff8009defd10 000000002ac727c8
[   85.207979] bb80: 0000000000030d40 00003d0900000000 0000000000000000 00000000003d0900
[   85.289827] bba0: 003d090000000000 0000000000000000 0000000000000008 ffffffffffffffff
[   85.378687] bbc0: 0000000000000000 0000000000000000 0000000000000000 ffffffc87ffb1900
[   85.479265] bbe0: ffffff8009d47478 ffffffc87ffb1908 ffffff8009d20800 0000000000000001
[   85.596200] bc00: ffffff80080ed308 0000000000000000 0000000000000008 ffffff8009d47000
[   85.666183] bc20: ffffff8009d47344 ffffffc87b89bc70 ffffff80081009f4 ffffffc87b89bc70
[   85.816256] bc40: ffffff8008100a34 0000000080000145 0000000000000001 ffffff80080ed308
[   85.950545] bc60: ffffffffffffffff ffffff80081009f4
[   86.059564] [] el1_irq+0xb0/0x140
[   86.143504] [] smp_call_function_many+0x264/0x2c8
[   86.226604] [] on_each_cpu+0x34/0x60
[   86.274338] [] clock_was_set+0x1c/0x28
[   86.373049] [] do_settimeofday64+0x100/0x180
[   86.456172] [] rtc_hctosys+0x8c/0xe0
[   86.550850] [] do_one_initcall+0x38/0x128
[   86.607418] [] kernel_init_freeable+0x140/0x1e0
[   86.701020] [] kernel_init+0x10/0x100
[   86.778705] [] ret_from_fork+0x10/0x50
[  147.351094] INFO: rcu_sched self-detected stall on CPU
[  147.364936] INFO: rcu_sched detected stalls on CPUs/tasks:
[  147.365288] 	3-...: (1 GPs behind) idle=5fd/140000000000001/0 softirq=1060/1061 fqs=2514 
[  147.365486] 	(detected by 0, t=21006 jiffies, g=199, c=198, q=20)
[  147.365612] Task dump for CPU 3:
[  147.365664] swapper/0       R  running task        0     1      0 0x00000002
[  147.365704] Call trace:
[  147.365763] [] __switch_to+0x8c/0xa0
[  147.365995] [] 0xffffff8009d23430
[  148.222087] 	3-...: (1 GPs behind) idle=5fd/140000000000001/0 softirq=1060/1061 fqs=2516 
[  148.300671] 	 (t=21016 jiffies g=199 c=198 q=20)
[  148.378602] Task dump for CPU 3:
[  148.480228] swapper/0       R  running task        0     1      0 0x00000002
[  148.563999] Call trace:
[  148.650765] [] dump_backtrace+0x0/0x198
[  148.728525] [] show_stack+0x14/0x20
[  148.813458] [] sched_show_task+0x94/0xf0
[  148.889095] [] dump_cpu_task+0x40/0x50
[  148.984756] [] rcu_dump_cpu_stacks+0xb4/0xe8
[  149.047552] [] rcu_check_callbacks+0x67c/0x860
[  149.119980] [] update_process_times+0x34/0x60
[  149.230191] [] tick_sched_handle.isra.4+0x38/0x48
[  149.323680] [] tick_sched_timer+0x44/0x90
[  149.385389] [] __hrtimer_run_queues+0xf0/0x178
[  149.493899] [] hrtimer_interrupt+0x98/0x1c8
[  149.563370] [] arch_timer_handler_phys+0x30/0x40
[  149.641834] [] handle_percpu_devid_irq+0x78/0x128
[  149.735388] [] generic_handle_irq+0x24/0x38
[  149.834536] [] __handle_domain_irq+0x5c/0xb8
[  149.937284] [] gic_handle_irq+0x64/0xc0
[  149.982910] Exception stack(0xffffffc87b89bb40 to 0xffffffc87b89bc70)
[  150.063405] bb40: 0000000000000003 ffffffc87ffa52b8 0000000000000000 0000000000000002
[  150.146709] bb60: 0000000000000002 0000000000000007 ffffff8009defd10 000000002ac727c8
[  150.203564] bb80: 0000000000030d40 00003d0900000000 0000000000000000 00000000003d0900
[  150.279696] bba0: 003d090000000000 0000000000000000 0000000000000008 ffffffffffffffff
[  150.381964] bbc0: 0000000000000000 0000000000000000 0000000000000000 ffffffc87ffb1900
[  150.470097] bbe0: ffffff8009d47478 ffffffc87ffb1908 ffffff8009d20800 0000000000000001
[  150.568152] bc00: ffffff80080ed308 0000000000000000 0000000000000008 ffffff8009d47000
[  150.637674] bc20: ffffff8009d47344 ffffffc87b89bc70 ffffff80081009f4 ffffffc87b89bc70
[  150.733976] bc40: ffffff8008100a34 0000000080000145 0000000000000001 ffffff80080ed308
[  150.831628] bc60: ffffffffffffffff ffffff80081009f4
[  150.955855] [] el1_irq+0xb0/0x140
[  151.044109] [] smp_call_function_many+0x264/0x2c8
[  151.122832] [] on_each_cpu+0x34/0x60
[  151.224703] [] clock_was_set+0x1c/0x28
[  151.299286] [] do_settimeofday64+0x100/0x180
[  151.353907] [] rtc_hctosys+0x8c/0xe0
[  151.412735] [] do_one_initcall+0x38/0x128
[  151.529715] [] kernel_init_freeable+0x140/0x1e0
[  151.597700] [] kernel_init+0x10/0x100
[  151.664533] [] ret_from_fork+0x10/0x50
[  210.362420] INFO: rcu_sched self-detected stall on CPU
[  210.442747] 	3-...: (1 GPs behind) idle=5fd/140000000000001/0 softirq=1060/1061 fqs=4363 
[  210.522330] 	 (t=36760 jiffies g=199 c=198 q=20)
[  210.612413] Task dump for CPU 3:
[  210.678056] swapper/0       R  running task        0     1      0 0x00000002
[  210.797579] Call trace:
[  210.869474] [] dump_backtrace+0x0/0x198
[  210.978337] [] show_stack+0x14/0x20
[  211.065191] [] sched_show_task+0x94/0xf0
[  211.116193] [] dump_cpu_task+0x40/0x50
[  211.206489] [] rcu_dump_cpu_stacks+0xb4/0xe8
[  211.283350] [] rcu_check_callbacks+0x67c/0x860
[  211.414408] [] update_process_times+0x34/0x60
[  211.505845] [] tick_sched_handle.isra.4+0x38/0x48
[  211.584325] [] tick_sched_timer+0x44/0x90
[  211.711243] [] __hrtimer_run_queues+0xf0/0x178
[  211.770994] [] hrtimer_interrupt+0x98/0x1c8
[  211.847067] [] arch_timer_handler_phys+0x30/0x40
[  211.889386] [] handle_percpu_devid_irq+0x78/0x128
[  211.961093] [] generic_handle_irq+0x24/0x38
[  212.043286] [] __handle_domain_irq+0x5c/0xb8
[  212.151305] [] gic_handle_irq+0x64/0xc0
[  212.203371] Exception stack(0xffffffc87b89bb40 to 0xffffffc87b89bc70)
[  212.288716] bb40: 0000000000000003 ffffffc87ffa52b8 0000000000000000 0000000000000002
[  212.376533] bb60: 0000000000000002 0000000000000007 ffffff8009defd10 000000002ac727c8
[  212.465214] bb80: 0000000000030d40 00003d0900000000 0000000000000000 00000000003d0900
[  212.537591] bba0: 003d090000000000 0000000000000000 0000000000000008 ffffffffffffffff
[  212.670528] bbc0: 0000000000000000 0000000000000000 0000000000000000 ffffffc87ffb1900
[  212.769139] bbe0: ffffff8009d47478 ffffffc87ffb1908 ffffff8009d20800 0000000000000001
[  212.864755] bc00: ffffff80080ed308 0000000000000000 0000000000000008 ffffff8009d47000
[  212.945381] bc20: ffffff8009d47344 ffffffc87b89bc70 ffffff80081009f4 ffffffc87b89bc70
[  212.992652] bc40: ffffff8008100a34 0000000080000145 0000000000000001 ffffff80080ed308
[  213.119559] bc60: ffffffffffffffff ffffff80081009f4
[  213.213894] [] el1_irq+0xb0/0x140
[  213.308705] [] smp_call_function_many+0x264/0x2c8
[  213.453974] [] on_each_cpu+0x34/0x60
[  213.490962] [] clock_was_set+0x1c/0x28
[  213.578731] [] do_settimeofday64+0x100/0x180
[  213.645997] [] rtc_hctosys+0x8c/0xe0
[  213.682877] [] do_one_initcall+0x38/0x128
[  213.770479] [] kernel_init_freeable+0x140/0x1e0
[  213.843347] [] kernel_init+0x10/0x100
[  213.911153] [] ret_from_fork+0x10/0x50
```