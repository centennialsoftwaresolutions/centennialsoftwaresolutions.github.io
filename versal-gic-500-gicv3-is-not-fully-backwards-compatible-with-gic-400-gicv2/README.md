# Versal GIC-500 / GICv3 is not fully backwards compatible with UltraScale+ GIC-400 / GICv2

Versal has an ARM GIC-500 (Global Interrupt Controller) connected to its APU. The GIC-500 implements the ARM GICv3 standard.

UltraScale+, on the other hand, has a GIC-400 connected to its APU. The GIC-400 implements the ARM GICv2 standard.

If you read through the ARM GICv3 and GIC-500 documentation, there are some references to “backwards compatibility” or “legacy operation.” They describe a feature that would allow GICv2 code to run on platforms with a GICv3. This implies that interrupt code written for UltraScale+’s GIC-400/GICv2 could run unmodified on Versal.

That is not the case. This article covers the limitations of backwards compatibility and where backwards compatibility does work.

The GIC-500 TRM states (r1p1 section 2.3.4 / page 32):

> You can configure the Distributor part of the GIC-500 at build time to support limited backwards compatibility with GICv2. If this support is configured, the Distributor resets to backwards compatibility mode.

> The ARE setting in GICD\_CTLR, which disables backwards compatibility, is programmable when backwards compatibility support is configured.

That section also describes a few limitations to backwards compatibility – but they’re minor limitations. Based on those limitations most US+ interrupt code should only require minor changes to work on Versal.

The backwards compatibility option in GIC-500 is configurable when the silicon is built (see GIC-500 TRM r1p1 section 1.5 / page 19 – “GICv2 backwards compatibility support”). If enabled, the GIC will be in backwards compatibility mode by default after POR, and the ARE\_S / ARE\_NS bits in the GICD\_CTLR register will both be 0 (GIC-500 TRM r1p1 page 42 “In backwards compatibility mode, where ARE = 0” and pages 43-45 (paraphrased) “The reset value of GICD\_CTLR… ARE\_S/NS being set means no GICv2 backwards compatibility support included.”)

We can verify this on Versal. If you probe GICD\_CTLR (0x00F9000000) after boot, the register value is 0x1. The ARE\_S and ARE\_NS bits are not set, meaning that backwards compatibility is enabled in silicon and currently active.

(For comparison, if you try this on Versal QEMU, the register will read 0x30 – both ARE bits are set, meaning that backwards compatibility is not supported. This is because the QEMU implementation of GIC-500 does not support backwards compatibility.)

After confirming that backwards compatibility is supported and enabled on Versal, you may try to run UltraScale+ interrupt code on Versal, and, even if you patch the code to work around the few limitations described in GIC-500 TRM section 2.3.4, you will likely find that it doesn’t work.

This is because of a more major limitation in the backwards compatibility support:

“You can configure **the Distributor part** of the GIC-500 at build time to support limited backwards compatibility with GICv2.”

_Only the distributor part of the GIC-500 supports backwards compatibility._

This is due to the way the GIC is structured in the system. A hint is available here: https://lore.kernel.org/linux-arm-kernel/20220211235513.cplmvgfuwe3dhzbs@nearby/

> No, this description is for the architecture as a whole. ARE being disabled _int the GIC_ doesn’t mean it is disabled overall, and the CPU is free to implement the CPU interface by any mean it wants as long as it communicates with the GIC using the Stream Protocol.

The GIC-500 does not implement all of GICv3. Interrupt handling is spread across two parts – the GIC itself and a CPU interface. The CPU interface is silicon that is physically located inside the A72 CPU cores. Backwards compatibility only applies to the distributor part of the GIC-500; it doesn’t affect the CPU interface.

If the ARE\_S/NS bits are zero, then the GICD\_\* registers (for the distributor in the GIC-500) will support backwards compatibility and UltraScale+ / GICv2 / GIC-400 code that uses GICD\_\* registers will work on Versal / GICv3 / GIC-500 (as long as you patch it for the few limitations described in GIC-500 TRM section 2.3.4). But other register blocks such as GICC\_\*, GICH\_\*, GICV\_\* are implemented in the CPU interface, not in the GIC-500 – in fact, you won’t even find any referenecs to GICC/GICH/GICV in the GIC-500 TRM. Backwards compatibility mode in the GIC-500 will not affect these, and any code that touches these registers will have to be updated when you migrate from UltraScale+ to Versal.

## References

ARM GIC-500 TRM (DDI 0516E) r1p1

https://documentation-service.arm.com/static/5e9085b8c8052b1608761814

ARM GICv3 Architecture Specification (IHI 0069A)

https://documentation-service.arm.com/static/6012f824773bb020e3de7aad

AMD/Xilinx Versal TRM (AM011)

https://docs.xilinx.com/r/en-US/am011-versal-acap-trm

AMD/Xilinx UltraScale+ TRM (UG1085)

https://docs.xilinx.com/r/en-US/ug1085-zynq-ultrascale-trm