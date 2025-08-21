# XCVC1902-2MSEVSVA2197 At-A-Glance

![AMD Logo](amd_logo_1)

Note: This post covers XCVC1902-1MSEVSVA2197, which differs from the current chip XCVC1902-2MSEVSVA2197 used on the EK-VCK190-G only in speed grade (old: -1, new -2)

## XCVC1902-2MSEVSVA2197 At-A-Glance (XCVC1902-1MSEVSVA2197)

This post is an XCVC1902-2MSEVSVA2197 at-a-glance (XCVC1902-1MSEVSVA2197). This part is featured on the first Versal™ AI Core series evaluation kit (EK-VCK190-G $13,195.00) [https://www.xilinx.com/products/boards-and-kits/vek280.html](https://www.xilinx.com/products/boards-and-kits/vck190.html) and lists XCVC1902-1MSEVSVA2197 info and links to key information and documents.

Click [ https://www.centennialsoftwaresolutions.com/post/xcvc1902-1msevsva2197-decoded ] if you need a XCVE2802-2MSEVSVH1760 at-a-glance. This part is featured on the AMD Versal™ AI Edge Series VEK280 Evaluation Kit (EK-VEK280-PP-G).

It includes:

- XCVC1902-1MSEVSVA2197 Ordering Information Decode
- XCVC1902-1MSEVSVA2197 Resources
- XCVC1902-1MSEVSVA2197 Maximum I/O
- XCVC1902-1MSEVSVA2197 I/O Overview
- XCVC1902-1MSEVSVA2197 Voltage
- XCVC1902-1MSEVSVA2197 Vivado Part Number
- XCVC1902-1MSEVSVA2197 Physical Layout
- XCVC1902-1MSEVSVA2197 PL System Perspective
- XCVC1902-1MSEVSVA2197 Boot
- XCVC1902-1MSEVSVA2197 Software Development

## XCVC1902-1MSEVSVA2197 Ordering Information Decode

From Figure 3: Versal Device Ordering Information 

https://docs.xilinx.com/v/u/en-US/ds950-versal-overview#page=35 

![Decoding XCVC1902-1MSEVSVA2197 ](versal_device_ordering_info_2)

(1) All packages have Pb-free bumps.

## XCVC1902-1MSEVSVA2197 Resources

From Table 4: Versal AI Core Series https://docs.xilinx.com/v/u/en-US/ds950-versal-overview#page=5 

![VC1902 Resources](versal_ai_core_series_3)

## XCVC1902-1MSEVSVA2197 Maximum I/O

From Table 5: Versal AI Core Series: Device-Package Combinations and Maximum I/O  [https://docs.xilinx.com/v/u/en-US/ds950-versal-overview#page%20=6](https://docs.xilinx.com/v/u/en-US/ds950-versal-overview#page =6) 

![XCVC1902-1MSEVSVA2197 Device Package](package_combo_and_maximum_4)

- XPIO DDR: 186
- XPIO DDR+PL: 462 (276 XPIO PL)
- HDIO (high-density I/O): 44
- MIO (multiplex I/O): 78
  - https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/Multiplexed-I/O-Signals-and-Pins 
- GTY: 44
  - Versal ACAP GTY and GTYP Transceivers Architecture Manual (AM002) @ https://docs.xilinx.com/r/en-US/am002-versal-gty-transceivers 
    - GTY Description @ https://docs.xilinx.com/r/en-US/am002-versal-gty-transceivers/Features 
  - 26.5625 Max Gb/s, 1.2 Min Gb/s , https://www.xilinx.com/support/documents/data_sheets/ds957-versal-ai-core.pdf#page=58 
- GTYP: 0

## XCVC1902-1MSEVSVA2197 I/O Overview

From [https://docs.xilinx.com/v/u/en-US/ds950-versal-overview#page%20=28](https://docs.xilinx.com/v/u/en-US/ds950-versal-overview#page =28) 

![Versal I/O overview](io_overview_5)

## XCVC1902-1MSEVSVA2197 Voltage

From: https://www.xilinx.com/support/documents/data_sheets/ds957-versal-ai-core.pdf#page=7 (DS957)

The specified portion of the Vivado design tools device selection code includes speed grade (-3, -2, -1), operating voltages (HP, MP, MHP, MM, LP, LHP, LLI), temperature grade, (-i, -e, -

m), and maximum static power screen (-S, -L).

From: https://docs.xilinx.com/v/u/en-US/ds950-versal-overview#page=35 (DS950)

![XCVC1902-1MSEVSVA2197 Voltage](voltage_information_6)

## XCVC1902-1MSEVSVA2197 Vivado Part Number

From Table 4:  Available Speed Grades and Operating Voltages

https://www.xilinx.com/support/documents/data_sheets/ds957-versal-ai-core.pdf#page=6 

![XCVC1902-1MSEVSVA2197 Vivado Part Number](available_speed_grades_7)

The XCVC1902-1MSEVSVA2197 Vivado Part # is vc1902-vsva2197-1MP-e-S

![Vivado part listing: XCVC1902-1MSEVSVA2197: I/O Pin Count, ...](part_to_gtpe2_8)

![Vivado part listing: XCVC1902-1MSEVSVA2197: Gb Transceivers,...](gb_transceivers_to_gthe4_transceivers_9)

![Vivado part listing: XCVC1902-1MSEVSVA2197: GTHE4,...](gthe4_to_mmcm_10)

![Vivado part listing: XCVC1902-1MSEVSVA2197: MMCMs,...](mmcm_to_ref_operating_temps_11)

![Vivado part listing: XCVC1902-1MSEVSVA2197: Max Operating Temperature,...](max_operating_temps_to_max_operating_voltage_12)

Overdrive mode (0.88V)

Standard drive mode (0.70V)

From https://www.xilinx.com/support/documents/data_sheets/ds957-versal-ai-core.pdf#page=2 

- VCCINT: Programmable logic primary power supply
- VCC_PSLP: PS low-power domain (LPD) power supply
- VCC_PSFP: PS full-power domain (FPD) power supply
- VCC_CPM5: CPM5 primary power supply 
  - [ CPM5 is the acronym for Coherency for PCIe® with CXL Cache Coherency  https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/Summary-of-Hardware-Options ]
- VCC_PMC: PMC primary power supply 
  - [ platform management controller (PMC) https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/Overview?tocId=KryN1l2X_toCsPfsx_LwbA ]
- VCC_SOC: Network on Chip (NoC) and DDR memory controller power supply 
- VCC_IO: XPIO power supply
  - https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/I/O-Buffer-Pin-Banks 
  - 
- VCC_RAM: PL RAM and clocking network power supply

## XCVC1902-1MSEVSVA2197 PL XPIO Info

From https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/I/O-Buffer-Pin-Banks 

![XPIO Description](io_buffer_pin_banks_13)

## XCVC1902-1MSEVSVA2197 Physical Layout

From https://docs.xilinx.com/v/u/en-US/ds950-versal-overview#page=12 

![Versal Physical Layout](physical_layout_14)

From https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/PL-Block-Diagram 

## XCVC1902-1MSEVSVA2197 PL System Perspective

![Versal PL Perspective](pl_system_perspective_15)

## XCVC1902-1MSEVSVA2197 Boot

https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/Non-Secure-Boot-Flow 

https://docs.xilinx.com/r/en-US/am011-versal-acap-trm/Secure-Boot-Flow 

## XCVC1902-1MSEVSVA2197 Software Development

https://docs.xilinx.com/r/en-US/ug1304-versal-acap-ssdg 

## References To Items Used In This Post

Logo from https://library.amd.com/media/ (requires a password)