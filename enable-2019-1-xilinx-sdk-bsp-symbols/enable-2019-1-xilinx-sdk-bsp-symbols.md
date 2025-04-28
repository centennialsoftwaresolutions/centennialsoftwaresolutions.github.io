# Enable 2019.1 Xilinx SDK BSP Symbols

![Xilinx_logo_1](Xilinx_logo_1.png)

This post shows how to enable symbols in a 2019.1 Xilinx BSP.

Remember! You can enable syms in the fsbl or the fsbl\_bsp, but not both.

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Right-click on **fsbl\_bsp** and click **Board Support Package Settings**.

![Board_support_package_settings_2](Board_support_package_settings_2.png)

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Click **standalone** and set **zynqmp\_fsbl\_bsp** to **false**.

![Set_zynqmp_fsbl_bsp_false_3](Set_zynqmp_fsbl_bsp_false_3.png)

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Click **psu\_cortexta53\_0**, click on **\-g -Wall -Wextra -Os -flto -ffat-lto-objects**.

![Click_on_wall_wextra_4](Click_on_wall_wextra_4.png)

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): Set:

**\-g -Wall -Wextra -Os -flto -ffat-lto-objects**

…to

**\-g -Wall -Wextra -Og**

...and click **OK**

![Set_wall_wextra_os_to_og_5](Set_wall_wextra_os_to_og_5.png)

You should see the BSP recompile automatically:

![Bsp_recompile_6](Bsp_recompile_6.png)

You should see the complete build fail if you haven't turned off features in the fsbl:

![Compile_build_fail_7](Compile_build_fail_7.png)

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): Go into **xfsbl\_config.h** and set all of these:

![Xfsbl_config_h_settings_8](Xfsbl_config_h_settings_8.png)

...to **1U** to turn off code:

![Set_to_1u_9](Set_to_1u_9.png)

Step [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6): Click **Save All**. The **FSBL** should auto recompile.

![Save_all_recompile_10](Save_all_recompile_10.png)

Step [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7): To test put a breakpoint in **xil\_printf** (which is in the BSP)

![Xil_printf_breakpoint_11](Xil_printf_breakpoint_11.png)

**<u><span>References</span></u>**

-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]