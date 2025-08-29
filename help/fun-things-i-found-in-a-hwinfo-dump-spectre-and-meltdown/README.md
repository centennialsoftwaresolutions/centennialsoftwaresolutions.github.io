# Fun things I found in a hwinfo dump: spectre and meltdown!

![meltdown_specter_logos](meltdown_specter_logos.png)

\>> cpu.1: cpuinfo

----- /proc/cpuinfo -----

 processor  : 0

 vendor_id  : GenuineIntel

 cpu family  : 6

 model    : 60

 model name  : Intel(R) Core(TM) i5-4570 CPU @ 3.20GHz

 stepping  : 3

 microcode  : 0x16

 cpu MHz    : 3192.839

 cache size  : 6144 KB

 physical id  : 0

 siblings  : 4

 core id    : 0

 cpu cores  : 4

 apicid    : 0

 initial apicid  : 0

 fpu    : yes

 fpu_exception  : yes

 cpuid level  : 13

 wp    : yes

 flags    : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm xsaveopt dtherm ida arat pln pts

 bugs    : cpu_meltdown spectre_v1 spectre_v2

 bogomips  : 6385.67

 clflush size  : 64

 cache_alignment  : 64

 address sizes  : 39 bits physical, 48 bits virtual

 power management:



Reference

Images from[ https://meltdownattack.com/](http://meltdownattack.com/)

More Info



[Go to: http://www.linuxintro.org/wiki/Hwinfo to get more info on using hwinfo](http://www.linuxintro.org/wiki/Hwinfo)