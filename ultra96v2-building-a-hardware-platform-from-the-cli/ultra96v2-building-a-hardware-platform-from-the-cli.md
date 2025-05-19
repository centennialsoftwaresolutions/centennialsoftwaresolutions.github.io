# Ultra96-V2: Building A Hardware Platform from the CLI

![xilinx_logo](xilinx_logo.png)

This post describes how to build a hardwre platform for the Ultra96v2 board in Xilinx Vivado. This will allow you to use Xilinx SDK to target software applications at your hardware. The Xilinx Vivado CLI TCL interface is used to allow the entire process to be done from the command line.

## Notes

A few variables will be used throughout the tutorial. Make sure to replace these with your own unique values.

-   <project\_name>: A name for your Vivado project
    
-   <project\_folder>: A folder you want to store your project in
    
-   <xilinx\_tools>: The folder you installed your Xilinx tools into
    
    ​	     Windows Default: C:/Xilinx
    
    ​	     Linux Default: /tools/xilinx



Another thing to be careful about using spaces in your <project\_name> and <project\_folder>. This can sometimes break Vivado and SDK.

If you are working through this tutorial on Windows, you want to make sure to use / as you directory seperater instead of \\. I've found the Xilinx tools to be picky about this.

## Prereqs

### Hardware

To run through this and subsequent tutorials, you will need some hardware.

-   Ultra96v2 ([AES-ULTRA96-V2-G](https://www.avnet.com/shop/us/products/avnet-engineering-services/aes-ultra96-v2-g-3074457345638646173/?aka_re=1))
    
-   Ultra96 USB-to-JTAG/UART Pod ([AES-ACC-U96-JTAG](https://www.avnet.com/shop/us/products/avnet-engineering-services/aes-acc-u96-jtag-3074457345635355958/))
    
-   96Boards/Ultra96 compliant power supply kit ([AES-ACC-U96-4APWR](https://www.avnet.com/shop/emea/products/avnet-engineering-services/aes-acc-u96-4apwr-3074457345636156710/))
    

### Software

To run through this and subsequent tutorials, you will need some software.

-   A Xilinx Vivado 2019.1 WebPACK install
    
-   A Xilinx SDK 2019.1 install
    

## Tutorial

### Adding the Ultra96v2 to Vivado

A board definition file (BDF) is required for Vivado to target projects at the Ultra96v2. The BDF for the Ultra96v2 is available from Avnet via their github.

To add the BDF to Vivado:

-   Download the Avnet BDF repo
    
-   Via the browser, download [https://github.com/Avnet/bdf/archive/master.zip](https://github.com/Avnet/bdf/archive/master.zip)
    
-   Extract the zip file
    
-   Via git on the command line, git clone [<u><span>https://github.com/Avnet/bdf.git</span></u>](https://github.com/Avnet/bdf.git)
    

To add the BDF to Vivado

-   The BDF for the Ultra96v2 is located in the ultra96v2 subfolder of the repo
    
-   Copy the ultra96v2 folder to the board\_files directory of you Xilinx Vivado install.
    
-   This is located in <xilinx\_tools>/Vivado/2019.1/data/boards/board\_files inside your Xilinx Tools folder
    

## Launch The Vivado TCL Console

We will now launch the Vivado TCL Console. This allows us to run and control Vivado without the GUI..

To launch the Vivado TCL console, invoke the vivado binary with the -mode tcl flag. Make sure to change the commands to point at your Vivado install location.

We will also start Vivado with the -nojournal and -nolog flags to prevent it from dropping runtime files in the directory it is invoked from. If you want these logs, leave off these two arguments

Example:

```
<xilinx_tools>/Vivado/2019.1/bin/vivado -mode tcl -nojournal -nolog
```

For the rest of the tutorial, all of the commands will be run in this Vivado TCL Console.

## Creating a project

First we have to instruct Vivado to create at project targeting the Ultra96v2. Note that the second commands reference to current\_project is a Vivado TCL function, not something you need to fill in.

```
create_project <project_name> {<project_folder>} -part xczu3eg-sbva484-1-e
set_property board_part em.avnet.com:ultra96v2:part0:1.0 [current_project]
```

## Block Design

Next we will create a block design in the project and make the required connections.

We will make use of block design automation to simplify this process.

```
# create the block design
create_bd_design "design_1"

# add the Zynq US+ Processor Configuration Wizard (PCW) ip to the block design
startgroup
create_bd_cell -type ip -vlnv xilinx.com:ip:zynq_ultra_ps_e:3.3 zynq_ultra_ps_e_0
endgroup

# use block design automation to set default setup
apply_bd_automation -rule xilinx.com:bd_rule:zynq_ultra_ps_e -config {apply_board_preset "1" }  [get_bd_cells zynq_ultra_ps_e_0]

# connect the PL clock to the AXI clocks
connect_bd_net [get_bd_pins zynq_ultra_ps_e_0/pl_clk0] [get_bd_pins zynq_ultra_ps_e_0/maxihpm0_fpd_aclk]
connect_bd_net [get_bd_pins zynq_ultra_ps_e_0/pl_clk0] [get_bd_pins zynq_ultra_ps_e_0/maxihpm1_fpd_aclk]

# Validate the design for errors
validate_bd_design

# Save the resulting design
save_bd_design
```

## Creating an HDL wrapper

Next, we will create a Hardware Descrpition Language (HDL) wrapper for the block design. This allows the block design to serve as the top level module in the Vivado project.

```
# create the HDL wrapper
make_wrapper -files [get_files {<project_folder>/<project_name>.srcs/sources_1/bd/design_1/design_1.bd}] -top
# Add the HDL wrapper to the project
add_files -norecurse {<project_folder>/<project_name>.srcs/sources_1/bd/design_1/hdl/design_1_wrapper.v}
```

## Build the Project

We will now build our project. We will launch an implmentation run and have it generate a bitstream file. This will run all the steps leading up to this as well.

```
# launch the implementation run w/bitstream generation
launch_runs impl_1 -to_step write_bitstream -jobs 4

# wait for the run to complete
wait_on_run impl_1
```

Note that this process can take some time.

## Export the Hardware Platform

Now we will output the Hardware Platform from our newly built project

```
# create a folder to store the Hardware Platform in
file mkdir {<project_folder>/<project_name>.sdk}
```

```
file copy -force 
{<project_folder>/<project_name>.runs/impl_1/design_1_wrapper.sysdef} {<project_folder>/<project_name>.sdk/design_1_wrapper.hdf}
```