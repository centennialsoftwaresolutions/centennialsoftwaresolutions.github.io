# Zynq-7000 + AXI Slave with Interrupt Hello World on a ZC702

![xilinx_logo_1](xilinx_logo_1.png)

This post lists step-by-step instructions for creating an AXI slave with an interrupt using Vivado HLS, integrating the slave into a Zynq-7000 system using Vivado, writing a driver that exercises the AXI slave and responds to the interrupt and running everything on a ZC702.

**<u><span>Versions Used</span></u>**

-   Xilinx Vivado 2018.2 & SDK 2018.2
    
-   Xilinx Vivado HLS 2018.2
    
-   ZC702 Rev 1.1
    
-   Windows 7 SP1
    

**<u><span>Before you Start</span></u>**

Review the ZC702 JTAG and serial port set up instructions @ \[[link](https://www.centennialsoftwaresolutions.com/blog/set-up-the-jtag-and-serial-port-on-the-zc702)\]. These instructions are also reviewed below.

**<u><span>Contents</span></u>**

Part 1: Create an AXI Slave with an Interrupt Using Vivado HLS

Part 2: Create the Vivado Project

Part 3: Add the axi\_lite Repo to the UP Catalog

Part 4: Create the Zynq-7000 in IP Integrator

Part 5: Connect the HLS Interrupt Line to Zynq

Part 6: Create a Top-Level HDL Wrapper

Part 7: Synthesize and Generate the Bitstream

Part 8: Export the Design and Open the SDK

Part 9: Install the USB-to-UART Driver and Get the COM Assignment

Part 10: Create the Test App and BSP

Part 11: Test Debug Run + Further Config

Part 12: Test the AXI Module and the Interrupt

**<u><span>Part 1: Create an AXI Slave with an Interrupt Using Vivado HLS</span></u>**

Step 1: Start Vivado HLS 2018.2

A. Click **Windows**

B. Click **Xilinx Design Tools**

C. Click **Vivado 2018.2**

D. Click **Vivadi HLS 2018.2**

![vivado_hls_2018_1_2](vivado_hls_2018_1_2.png)

Step 2: Click **Open Example Project**

![open_example_project_3](open_example_project_3.png)

Step 3:

A. Expand **Design Examples**

B. Click **axi\_lite**

C. Click **Next**

![open_axi_light_4](open_axi_light_4.png)

Step 4:

A. Set **Location** to **C:\\vivadoprjs\\axislaveint**

B. Click **Finish**

![set_project_location_5](set_project_location_5.png)

You should see:

![project_homepage_6](project_homepage_6.png)

Step 5: Click **Run C Synthesis**

![run_c_synthesis_7](run_c_synthesis_7.png)

After a little bit (1 min on my T460 \[[<u><span>link</span></u>](https://www.zachpfeffer.com/single-post/2017/01/28/New-T460-System-Information)\]) you should see **Finished C synthesis.** in the **Console**

![finished_c_synthesis_8](finished_c_synthesis_8.png)

Step 6: Click **Export RTL**

![export_rtl_9](export_rtl_9.png)

Step 7:

A. Click the **Vivado synthesis, place and route** checkbox

B. Click **OK**

![synthesis_place_and_route_10](synthesis_place_and_route_10.png)

After a little bit (3 min on my T460) you should see **Finished export RTL.** in the **Console**

![finished_export_rtl_11](finished_export_rtl_11.png)

Step 8: Close Vivado HLS

A. Click **File**

B. Click **Exit**

![exit_project_12](exit_project_12.png)

**<u><span>Part 2: Create the Vivado Project</span></u>**

Step 1: Start Vivado

![start_vivado_13](start_vivado_13.png)

Step 2: Click **Create Project**

![create_project_14](create_project_14.png)

Step 3: Click **Next**

![next_create_new_project_15](next_create_new_project_15.png)

Step 4:

A. Set **Project name** to zynqsys

B: Set **Project location** to C:/vivadoprjs/axislaveint (created above)

C. Click the **Create project subdirectory** checkbox

D. Click **Next**

![name_project_16](name_project_16.png)

Step 5:

A. Select **RTL Project**

B. Check the **Do not specify sources at this time** check box

C. Click **Next**

![set_rtl_project_17](set_rtl_project_17.png)

Step 6:

A. Click **Boards**

B. Type **ZC702**

C. Click on the **ZYNQ-7 ZC702 Evaluation Board** box

D. Click **Next**

![find_zc702_18](find_zc702_18.png)

Step 7: Click **Finish**

![new_project_summary_19](new_project_summary_19.png)

You should see:

![project_homepage_20](project_homepage_20.png)

**<u><span>Part 3: Add the axi_lite Repo to the UP Catalog</span></u>**

Step 1: Click **IP Catalog**

![ip_catolog_21](ip_catolog_21.png)

Step 2:

A. Right-click on **Vivado Repository**

B. Click **Add Repository...**

![add_repository_22](add_repository_22.png)

Step 3:

A. Expand the directory tree and click on **C:\\vivadoprjs\\axislaveint\\axi\_lite\\proj\_axi\_lite\\solution1\\impl\\ip**

B. Click **Select**

![select_ip_folder_23](select_ip_folder_23.png)

C. Click **OK**

![confirm_add_repository_24](confirm_add_repository_24.png)

You should see **Example** under **User Repository / VIVADO HLS IP**:

![see_example_25](see_example_25.png)

**<u><span>Part 4: Create the Zynq-7000 in IP Integrator</span></u>**

Step 1: Click **Create Block Design**

![create_block_design_26](create_block_design_26.png)

Step 2: Use defaults, click **OK**

![use_defaults_27](use_defaults_27.png)

Step 3: Click **+**

![click_add_28_use_again](click_add_28_use_again.png)

Step 4:

A. Type **Zynq**

B. Double-click on **ZYNQ7 Processing System**

![add_zynq_processing_system_29](add_zynq_processing_system_29.png)

Step 5: Click **Run Block Automation**

![run_block_automation_30](run_block_automation_30.png)

Step 6: Use defaults, click **OK**

![use_defaults_31](use_defaults_31.png)

You should see:

![processing_system_diagram_32](processing_system_diagram_32.png)

**<u><span>Part 4: Connect the AXI Slave with Interrupt from HLS to Zynq-7000</span></u>**

Step 1: Click **+**

![click_add_28_use_again](click_add_28_use_again.png)

Step 2:

A. Type **Example**

B. Double-click on **Example**

![add_example_33](add_example_33.png)

Your screen should look similar to:

![project_screen_34](project_screen_34.png)

Step 3: Click Run Connection Automation

![run_connection_automation_35](run_connection_automation_35.png)

Step 4: Use defaults, click **OK**

![use_defaults_connection_automation_36](use_defaults_connection_automation_36.png)

Your screen should look something like:

![connection_screen_example_37](connection_screen_example_37.png)

**<u><span>Part 5: Connect the HLS Interrupt Line to Zynq</span></u>**

Step 1: Double click the ZYNQ block

![double_click_zynq_block_38](double_click_zynq_block_38.png)

Step 2: Enable IRQ\_F2P\[15:0\]

A. Click **Interrupts**

B. Check the **Fabric Interrupts** checkbox

C. Expand the **Fabric Interrupts** drop-down

D. Expand the **PL-PS Interrupt Ports**

E. Check the **IRQ\_F2P\[15:0\] checkbox**

F. Click **OK**

![check_irq_f2p_39](check_irq_f2p_39.png)

You should then see the IRQ\_F2P\[0:0\] port on Zynq:

![irq_port_added_40](irq_port_added_40.png)

Step 3: Connect IRQ\_F2P\[0:0\] to example\_0 interrupt

A. Click and hold mouse button on IRQ\_F2P\[0:0\]

B: Drag and release mouse button on interrupt

![connect_irq_to_interrupt_41](connect_irq_to_interrupt_41.png)

You should see:

![irq_to_interrupt_connection_42](irq_to_interrupt_connection_42.png)

**<u><span>Part 6: Create a Top-Level HDL Wrapper</span></u>**

A. Click **Sources**

B. Right-click **design\_1 (design\_1.bd) (1)**

C. Click **Create HDL Wrapper...**

![create_hdl_wrapper_43](create_hdl_wrapper_43.png)

D. Leave Let Vivado manage wrapper and auto-update, click **OK**

![let_vivado_manage_wrapper_44](let_vivado_manage_wrapper_44.png)

After a little time you should see:

![hdl_wrapper_45](hdl_wrapper_45.png)

**<u><span>Part 7: Synthesize and Generate the Bitstream</span></u>**

Step 1: Click **Run Synthesis**

![run_synthesis_46](run_synthesis_46.png)

Step 2: Use defaults, click **OK**

![launch_runs_defaults_47_use_again](launch_runs_defaults_47_use_again.png)

You'll see the status in the upper right corner.

A sample of the output:

![running_synth_design_48](running_synth_design_48.png)

Step 3:

Wait approximately 1 to 5 min until you see **Synthesis Complete** in the upper right corner...

![synthesis_complete_49](synthesis_complete_49.png)

...and click **OK** to Run Implementation:

![run_implementation_50](run_implementation_50.png)

Step 4: Use defaults, click **OK**

![use_defaults_for_runs_51](use_defaults_for_runs_51.png)

Again, you'll see status in the upper right:

![initializing_design_52](initializing_design_52.png)

Step 5:

Wait approximately 1 to 5 min until you see **Implementation Complete** in the upper right corner...

![implementation_complete_53](implementation_complete_53.png)

A. Select **Generate Bitstream**

B. Click **OK**

![generate_bitstream_54](generate_bitstream_54.png)

Step 6: Use defaults, click **OK**

![launch_runs_defaults_47_use_again](launch_runs_defaults_47_use_again.png)

Again, you should see the status in the upper right:

![running_write_bitstream_55](running_write_bitstream_55.png)

Step 7: Click **Cancel**

![bitstream_generation_completed_56](bitstream_generation_completed_56.png)

You may see this window pop-up:

![feedback_request_57](feedback_request_57.png)

Feel free to send feedback, set a reminder or click **No**. If you click **No** you may see:

![touchpoint_survey_dialog_58](touchpoint_survey_dialog_58.png)

...click **OK** to dismiss.

**<u><span>Part 8: Export the Design and Open the SDK</span></u>**

Step 1:

A. Click **File**

B. Click **Export**

C. Click **Export Hardware...**

![export_hardware_59](export_hardware_59.png)

Step 2:

A. Click the **Include bitstream** checkbox

B. Click **OK**

![export_include_bitstream_60](export_include_bitstream_60.png)

Step 3:

A. Click **File**

B. Click **Launch SDK**

![launch_sdk_61](launch_sdk_61.png)

Note: you can open the workspace directly from the SDK by opening the SDK and specifying C:\\vivadoprjs\\axislaveint\\zynqsys\\zynqsys.sdk as the workspace.

Step 4: Use defaults, click **OK**

![use_defaults_to_launch_sdk_62](use_defaults_to_launch_sdk_62.png)

You should see:

![sdk_project_screen_63](sdk_project_screen_63.png)

Note the Base Address of **example\_0**:

A. Scroll down

B. Look for example\_0

![example_0_64](example_0_64.png)

**<u><span>Part 9: Install the USB-to-UART Driver and Get the COM Assignment</span></u>**

Steps:

A. Goto \[[link](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)\] for the Silicon Labs CP210x USB to UART Bridge VCP Drivers

B. Download and unzip the correct installer for your OS

C. Install the driver (I did not need to restart on Windows 7 SP1)

D. Click **Windows**

E. Click **Devices and Printers**

![click_devices_and_printers_65](click_devices_and_printers_65.png)

F. You should see Silicon Labs CP210x USB to UART BridgeG.

G. Note the COM port # (you'll need this later)

![silicon_labs_cp210_bridge_66](silicon_labs_cp210_bridge_66.png)

**<u><span>Part 8: Configure the Board to Boot from JTAG, Connect it to the PC and Power it On</span></u>**

![set_sw16_to_jtag_67](set_sw16_to_jtag_67.png)

For the rest of the jumpers see the high-resolution photo of the board in the correct state at \[[link](https://photos.app.goo.gl/DddmM8T5QkTXwA7u5)\]. Step 2: Connect a **Micro-B to Type-A** (host connection) USB cable from U23 (Diglent USB JTAG interface) to the host PC

U23:

![u23_68](u23_68.png)

Micro-B connector:

![micro_b_connector_69](micro_b_connector_69.png)

Type-A connector:

![type_a_connector_70](type_a_connector_70.png)

Step 3: Connect a **Mini-B to Type-A** (host connection) USB cable from J17 (CP2103GM USB-to\_UART Bridge) to the host PC.

J17:

![connect_mini_b_type_a_j17_71](connect_mini_b_type_a_j17_71.png)

Mini-B connector:

![mini_b_connector_72](mini_b_connector_72.png)

Type-A connector:

![type_a_connector_73](type_a_connector_73.png)

Step 4: Turn on the board

![turn_on_board_74](turn_on_board_74.png)

**<u><span>Part 10: Create the Test App and BSP</span></u>**

Step 1:

A. Click **File**

B. Click **New**

C. Click **Application Project**

![new_application_project_75](new_application_project_75.png)

Step 2:

A. Type **testaxislaveint** into **Project name:**

B. Ensure the **Board Support Package: Create New** radio button is clicked and the name given is **testaxislaveint\_bsp**

C. Click **Next**

![textaxislaveint_name_76](textaxislaveint_name_76.png)

Step 3:

A. Click **Hello World**

B. Click **Finish**

![hello_world_77](hello_world_77.png)

You should see:

![testaxislaveint_project_page_78](testaxislaveint_project_page_78.png)

**<u><span>Part 11: Test Debug Run + Further Config</span></u>**

_These instructions allow debug to be set up more easily than entering in the details manually. After running a debug session, the Debug Configuration is fixed up to reset the FPGA and program the bitstream. The debugger COM port is also configured so that output can be read and the steps to test it and see_ **_Hello World_** _are listed._

Step 1:

A. Right-click **testaxislaveint**

B. Click **Debug As**

C. Click **Launch on Hardware (System Debugger)**

![launch_system_debugger_on_hardware_79](launch_system_debugger_on_hardware_79.png)

Step 2: Click **OK** (if you see this)

![click_ok_save_and_launch_80](click_ok_save_and_launch_80.png)

If you see this message click **Yes**. We'll handle this in the next part.

![fpga_configuration_confirm_81](fpga_configuration_confirm_81.png)

...click **Yes**.

![confirm_perspective_switch_82](confirm_perspective_switch_82.png)

You should see the Debug Perspective display the code broken on init\_platform():

A. Debug context on main()

B. helloworld.c on init\_platform()

![debug_perspective_breakpoint_main_83](debug_perspective_breakpoint_main_83.png)

Step 3:

A. Click **Run**

B. Click **Debug Configurations...**

![debug_configurations_84](debug_configurations_84.png)

Step 4:

A. Ensure **System Debugger using Debug\_testaxislave on Local** is selected (it should be)

B. Click the **Reset entire system** checkbox

C. Click the **Program FPGA** checkbox

D. Click **Apply**

E. Click **Close**

![configure_system_debugger_85](configure_system_debugger_85.png)

Step 5: Configure Debug View COM

A. Click **SDK Terminal**

B. Click the **'+'** (Connect to serial port.)

![click_sdk_terminal_86](click_sdk_terminal_86.png)

Step 6: Set Debug View COM settings

A. Enter the COM# from above

B. Click **OK**

![enter_com9_87](enter_com9_87.png)

Step 7: Make sure you see **Hello World** on the console

A. Click on the bug

![click_bug_icon_88](click_bug_icon_88.png)

B. Click **OK**

![confirm_debug_session_start_89](confirm_debug_session_start_89.png)

C. Wait for the system to hit the breakpoint on main()

![wait_for_system_to_hit_the_breakpoint_90](wait_for_system_to_hit_the_breakpoint_90.png)

D. Click **Resume**

![resume_91](resume_91.png)

E. Wait until you see exit():

F. Click on **SDK Terminal**

G. Observe **Hello World**

![observe_hello_world_92](observe_hello_world_92.png)

**<u><span>Part 12: Test the AXI Module and the Interrupt</span></u>**

Step 1: Click on the **C/C++** view

![click_on_c_cplusplus_view_93](click_on_c_cplusplus_view_93.png)

Step 2:

A. Expand **testaxislaveint**

B. Expand **src**

![expand_src_94](expand_src_94.png)

Step 3:

A. Right-click on **src**

B. Hover over **New**

C. Click **File**

![click_file_95_use_again](click_file_95_use_again.png)

D. Type **testexample.c**

E. Click **Finish**

![type_testexample_c_96_use_again](type_testexample_c_96_use_again.png)

F. Copy and paste the following code into **testexample.c**

```
#include  <stdlib.h>
#include "xil_printf.h"
#include "xparameters.h" // Parameter definitions for processor peripherals
#include "xscugic.h"	 // Processor interrupt controller device driver
#include "xexample.h" 	 // Device driver for HLS HW block

/* Example instance */
XExample example;

/* Interrupt Controller Instance */
XScuGic scugic;

volatile static int run_example = 0;
volatile static int result_available_from_example = 0;

void example_start(void *InstancePtr)
{
	XExample *example_instance = (XExample *) InstancePtr;

	XExample_InterruptEnable(example_instance, 1);
	XExample_InterruptGlobalEnable(example_instance);
	XExample_Start(example_instance);
}

void example_isr(void *InstancePtr)
{
	XExample *example_instance = (XExample *) InstancePtr;

	//Disable the global interrupt
	XExample_InterruptGlobalDisable(example_instance);

	//Disable the local interrupt
	XExample_InterruptDisable(example_instance, 0xffffffff);

	// clear the local interrupt
	XExample_InterruptClear(example_instance, 1);

	result_available_from_example = 1;

	// restart the core if it should run again
	if (run_example) {
		example_start(example_instance);
	}
}

static int connect_interrupt(void)
{
	//This functions sets up the interrupt on the Arm
	int status;

	XScuGic_Config *scugic_cfg = XScuGic_LookupConfig(XPAR_SCUGIC_SINGLE_DEVICE_ID);
	if (scugic_cfg == NULL) {
		xil_printf("Interrupt Configuration Lookup Failed\n\r");
		return XST_FAILURE;
	}

	status = XScuGic_CfgInitialize(&scugic, scugic_cfg, scugic_cfg->CpuBaseAddress);
	if(status != XST_SUCCESS) {
		return status;
	}

	status = XScuGic_SelfTest(&scugic);
	if(status != XST_SUCCESS) {
		return status;
	}

	Xil_ExceptionInit();

	Xil_ExceptionRegisterHandler(XIL_EXCEPTION_ID_INT,
			(Xil_ExceptionHandler) XScuGic_InterruptHandler, &scugic);

	Xil_ExceptionEnable();

	status = XScuGic_Connect(&scugic, XPAR_FABRIC_EXAMPLE_0_INTERRUPT_INTR,
			(Xil_InterruptHandler) example_isr, &example);
	if(status != XST_SUCCESS) {
		return status;
	}

	XScuGic_Enable(&scugic, XPAR_FABRIC_EXAMPLE_0_INTERRUPT_INTR);
	return XST_SUCCESS;
}

static int setup(void)
{
	int status;

	status = XExample_Initialize(&example, XPAR_XEXAMPLE_0_DEVICE_ID);
	if (status != XST_SUCCESS)
	{
		print("Failed XExample_Initialize()\r\n");
		return XST_FAILURE;
	}

	return XST_SUCCESS;
}

int add_w_interrupt(u8 a, u8 b, u8 *c)
{
	while(!XExample_IsIdle(&example));

	/* Reset available flag */
	result_available_from_example = 0;

	/* set the output to 0 */
	while(!XExample_IsReady(&example));
	XExample_Set_c_i(&example, 0);

	while(!XExample_IsReady(&example));
	XExample_Set_a(&example, a);

	while(!XExample_IsReady(&example));
	XExample_Set_b(&example, b);

	/* start the block */
	example_start(&example);

	/* wait until its done */
	while(!result_available_from_example);

	if (!XExample_Get_c_o_vld(&example))
		return XST_FAILURE;

	*c = XExample_Get_c_o(&example);

	return XST_SUCCESS;
}

int add_w_poll(u8 a, u8 b, u8 *c)
{
	while(!XExample_IsIdle(&example));

	/* set the output to 0 */
	while(!XExample_IsReady(&example));
	XExample_Set_c_i(&example, 0);

	while(!XExample_IsReady(&example));
	XExample_Set_a(&example, a);

	while(!XExample_IsReady(&example));
	XExample_Set_b(&example, b);

	/* start the block */
	XExample_Start(&example);

	/* wait until its done */
	while(!XExample_IsDone(&example));

	if (!XExample_Get_c_o_vld(&example))
		return XST_FAILURE;

	*c = XExample_Get_c_o(&example);

	return XST_SUCCESS;
}

enum interrupt_or_poll {
	INTERRUPT,
	POLL
};

static char *iorp_str[] =
{
		"Interrupt",
		"Poll"
};

int test(u8 a, u8 b, enum interrupt_or_poll iorp)
{
	int status;

	u8 c;
	char *str;

	if (iorp == INTERRUPT)
		str = iorp_str[0];
	else
		str = iorp_str[1];

	if (iorp == INTERRUPT)
		status = add_w_interrupt(a, b, &c);
	else
		status = add_w_poll(a, b, &c);

	if (status != XST_SUCCESS) {
		xil_printf("Failed to add in %s mode\r\n", str);
		return status;
	}

	u8 c_cpu = a + b;
	if (c != c_cpu) {
		xil_printf("FAILED: add(%u, %u) returned %u, which doesn't equal %u\r\n", a, b, c, c_cpu);
		return XST_FAILURE;
	}

	return XST_SUCCESS;
}

int test_interrupt(u8 a, u8 b)
{
	return test(a, b, INTERRUPT);
}

int test_poll(u8 a, u8 b)
{
	return test(a, b, POLL);
}

int test_all(void)
{
	int i, j;

	xil_printf("Test adding all values in %s mode: ", iorp_str[0]);
	for (i = 0; i < 0x100; i++)
		for (j = 0; j < 0x100; j++)
			if (test_interrupt(i, j) != XST_SUCCESS)
				return XST_FAILURE;
	xil_printf("PASSED\r\n");

	xil_printf("Test adding all values in %s mode: ", iorp_str[1]);
	for (i = 0; i < 0x100; i++)
		for (j = 0; j < 0x100; j++)
			if (test_poll(i, j) != XST_SUCCESS)
				return XST_FAILURE;
	xil_printf("PASSED\r\n");

	xil_printf("Test adding all values where modes switch off: ");
	for (i = 0; i < 0x100; i++) {
		for (j = 0; j < 0x100; j++) {
			if (test_poll(i, j) != XST_SUCCESS)
				return XST_FAILURE;
			if (test_interrupt(i, j) != XST_SUCCESS)
				return XST_FAILURE;
		}
	}
	xil_printf("PASSED\r\n");

	xil_printf("Test adding all values where modes switch off pseudo randomly: ");
	for (i = 0; i < 0x100; i++) {
		for (j = 0; j < 0x100; j++) {
			if (rand() % 2) {
				if (test_poll(i, j) != XST_SUCCESS)
					return XST_FAILURE;
			} else {
				if (test_interrupt(i, j) != XST_SUCCESS)
					return XST_FAILURE;
			}
		}
	}
	xil_printf("PASSED\r\n");
}

int testexample(void)
{
	int status;

	status = setup();
	if (status != XST_SUCCESS)
		return XST_FAILURE;

	status = connect_interrupt();
	if (status != XST_SUCCESS)
		return XST_FAILURE;

	xil_printf("Test 1+2 in %s mode: ", iorp_str[0]);
	if (test_interrupt(1, 2) != XST_SUCCESS)
		return XST_FAILURE;
	xil_printf("PASSED\r\n");

	xil_printf("Test 1+2 in %s mode: ", iorp_str[1]);
	if (test_poll(1, 2) != XST_SUCCESS)
		return XST_FAILURE;
	xil_printf("PASSED\r\n");

	if (test_all() != XST_SUCCESS)
		return XST_FAILURE;

	return XST_SUCCESS;
}
```

Step 6:

A. Right-click on **src**

B. Hover over **New**

C. Click **File**

![click_file_95_use_again](click_file_95_use_again.png)

Step 7:

A. Type **testexample.h**

B. Click **Finish**

![type_testexample_c_96_use_again](type_testexample_c_96_use_again.png)

Step 8: Copy and paste the following code into **testexample.h**

Step 9: Update **helloworld.c**

A. Double-click **helloworld.c**

![double_click_helloworld_c_97](double_click_helloworld_c_97.png)

B. Insert **testexample();** after print("Hello World\\n\\r"); and [#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) "test example.h" after [#include](https://www.centennialsoftwaresolutions.com/blog/hashtags/include) "xil\_printf.h"

![insert_testexample_h_98](insert_testexample_h_98.png)

C. Click save-all

![save_all_99](save_all_99.png)

Step 10: Run it

A. Click on the bug

![click_bug_icon_100](click_bug_icon_100.png)

If you see **WARNING** pop-up this click **OK**

![confirm_start_debug_session_101](confirm_start_debug_session_101.png)

B. Click **Yes** to confirm the switch to the Debug perspective

![confirm_debug_perspective_switch_102](confirm_debug_perspective_switch_102.png)

C. You should see execution stopped at main(

![execution_stopped_at_main_103](execution_stopped_at_main_103.png)

D. Click **Resume**

![resume_104](resume_104.png)

E. You should see all of the tests passing

![all_tests_passing_105](all_tests_passing_105.png)

**<u><span>References</span></u>**

-   2018.2 UG871 High-Level Synthesis (code at p.240-243) \[[link](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_2/ug871-vivado-high-level-synthesis-tutorial.pdf)\]
    
-   Free Online HTML Escape / Unescape @ \[[link](https://www.freeformatter.com/html-escape.html)\]
    
-   Xilinx logo found via [https://twitter.com/xilinxinc](https://twitter.com/xilinxinc) at \[[link](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]