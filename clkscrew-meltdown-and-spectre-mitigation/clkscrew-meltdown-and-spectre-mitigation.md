# CLKSCREW, Meltdown and Spectre Mitigation

![meltdown_and_spectre_logos](meltdown_and_spectre_logos.png)

This post presents a very short summary of CLKSCREW, Meltdown and Spectre mitigation strategies, links to each paper and a link to KAISER.

**Shared Needs**

CLKSCREW, Meltdown and Spectre \_all\_ rely on counting CPU clocks. CLKSCREW also relies on the ability for one core to modify frequency and voltage that impacts another core (which may be running a trusted OS).

**Summary of Mitigations Presented in Each Papers**

Meltdown

Apply the [KAISER](http://en.wikipedia.org/wiki/Kernel_page-table_isolation) patch to the Linux kernel and patches that accomplish the same thing for Windows and MacOS. This patch removes kernel mappings in userspace process, stopping Meltdown.

Spectre

No good mitigation strategy is listed, apart from disabling speculative execution.

CLKSCREW

Randomize the timing of sensitive code or better: compile code with checksum integrity and execution redundancy.

**Papers**

Spectre

[https://spectreattack.com/spectre.pdf](http://spectreattack.com/spectre.pdf) 

Meltdown

[https://meltdownattack.com/meltdown.pdf](http://meltdownattack.com/meltdown.pdf) 

CLKSCREW

[https://www.usenix.org/system/files/conference/usenixsecurity17/sec17-tang.pdf](http://www.usenix.org/system/files/conference/usenixsecurity17/sec17-tang.pdf) 

**Reference**

Images from [https://meltdownattack.com/](http://meltdownattack.com/) 