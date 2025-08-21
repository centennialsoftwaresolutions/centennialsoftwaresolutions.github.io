# Why do I need to run "Create HDL Wrapper..."

![xilinx_logo_1](xilinx_logo_1.png)

This post lists why a Vivado IP integrator a block diagram must be wrapped in an HDL wrapper, short answer: "because a BD (block design) cannot be synthesized directly."

In Vivado IP integrator a block diagram must be wrapped in an HDL wrapper.

Why?

From **Designing IP Subsystems Using IP Integrator** on p149 Xilinx provides this answer:

"The top-level HDL wrapper around the block design is needed because a BD (block design) source cannot be synthesized directly."

**<u><span>Supporting Documentation</span></u>**

_UG994 p.83_

![supporting_docs_2](supporting_docs_2.png)

_UG994 p.84_

![create_hdl_wrapper_dialog_box_3](create_hdl_wrapper_dialog_box_3.png)

_UG994 p.149_

![top_level_4](top_level_4.png)

_UG994 p.149_

![explanation_5](explanation_5.png)

**<u><span>References</span></u>**

-   Designing IP Subsystems Using IP Integrator UG994 (v2017.4) \[[<u><span>link</span></u>](http://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_4/ug994-vivado-ip-subsystems.pdf)\]
    
-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]