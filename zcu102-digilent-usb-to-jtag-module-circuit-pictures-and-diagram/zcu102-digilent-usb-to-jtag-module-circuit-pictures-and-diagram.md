# ZCU102 Digilent USB-to-JTAG Module, Circuit, Pictures and Diagram

![xilinx_logo_1](xilinx_logo_1.png)

This post contains details about the ZCU102's USB-to-JTAG Digilent module, the circuit its used in, a picture of the components on the board and a diagram of the resultant JTAG chain.

**<u><span>Overview</span></u>**

The ZCU102 allows JTAG to be used over USB with a Digilent USB JTAG-to-USB module.

The module is available at \[[<u><span>link</span></u>](https://store.digilentinc.com/jtag-smt2-nc-surface-mount-programming-module/)\].

Info from the ZCU102 BOM:

-   Reference designation on board: **U21**
    
-   Device: **USB Module**
    
-   Package: **DIGILENT\_USB\_JTAG\_2\_NC**
    
-   Manufactured and distributed by **Digilent**
    
-   Manufacturer part number: **JTAG-SMT2-NC**
    
-   Distributor part number: **410-308P**
    

**<u><span>Circuit</span></u>**

![circuit_diagram_2](circuit_diagram_2.png)

**Board**

![board_j2_and_u21_3](board_j2_and_u21_3.webp)

![board_x2_4](board_x2_4.webp)

JTAG\_TDI, JTAG\_TMS and JTAG\_TCK also route to J6, U48 and the Zynq UltraScale+ MPSoC as seen at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/diagram-of-the-zcu102-jtag-chain)\].

When used without FMC cards, the JTAG chain from the DIGILENT\_USB\_JTAG\_2\_NC looks like:

![jtag_chain_5](jtag_chain_5.png)

Diagram available at \[[<u><span>link</span></u>](https://drive.google.com/open?id=1qhvHiXUlf03x5rUsxRKqzL9QNyOPYsuV)\].

**References**

-   <u><span>ZCU102 BOM</span></u> ([<u><span>zcu102-bom-rdf0404.zip</span></u>](http://zcu102-bom-rdf0404.zip/)) at \[[<u><span>link</span></u>](https://www.xilinx.com/member/forms/download/design-license.html?cid=473392&filename=zcu102-bom-rdf0404.zip)\] (sign-in required)
    
-   <u><span>ZCU102 Board Schematics</span></u> ([<u><span>zcu102-schematic-source-rdf0403.zip</span></u>](http://zcu102-schematic-source-rdf0403.zip/)) at \[[<u><span>link</span></u>](https://www.xilinx.com/member/forms/download/design-license.html?cid=473360&filename=zcu102-schematic-source-rdf0403.zip)\] (sign-in required)
    
-   ZCU102 Layout (bug: see \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/0-kb-zcu102-board-and-gerber-file-archives-sept-8th-2018)\])
    
-   <u><span>Allegro Viewer</span></u> at \[[<u><span>link</span></u>](https://www.cadence.com/content/cadence-www/global/en_US/home/tools/allegro-downloads-contact.html)\] (needed to view layout files)
    
-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]