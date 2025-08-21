# Xilinx BSP Documentation

![xilinx_logo](xilinx_logo.png)

This post lists a link to Xilinx's "BSP documentation." It also lists links to the "embeddedsw" git where all of the "standalone code" is committed upon release and adds links to the various subdirectories in embeddedsw. I wrote this because a Google search of "Xilinx BSP Documentation" does not yield accurate links.

**<u><span>BSP Documentation</span></u>**

Xilinx BSP Documentation is at \[[<u><span>link</span></u>](https://github.com/Xilinx/embeddedsw/blob/master/lib/bsp/standalone/doc/standalone.pdf)\]

**<u><span>embeddedsw git repo on github</span></u>**

https://github.com/Xilinx/embeddedsw

Here's a copy of https://github.com/Xilinx/embeddedsw/blob/master/README.txt from June 8th 2019 with links:

```
embeddedsw.git - repo for standalone software

The standalone software is divided into following directories:
	- lib [link]
		contains bsp, software apps and software services
	- license.txt [link]
		contains information about the various licenses and copyrights
	- doc/ChangeLog [link]
		Contains change log information for releases
	- XilinxProcessorIPLib/drivers [link]
		contains all drivers
	- ThirdParty [link]
		software from third party like light weight IP stack
	- mcap/linux [link]
		software for using MCAP interface on Ultra Scale boards to
		program 2nd level bitstream

Every driver, sw_apps and sw_services has one or more of these sub-directories:
1. data		- contains tcl, mdd, testapp tcl or header files used in SDK
2. doc		- documentation of source code in form of pdf or html 
3. examples	- illustrating different use cases of driver
4. src		- driver interface code implementing functionality of IP

<repo>
|-ThirdParty [link]
|	|- bsp
|		|- freertos1-_xilinx [link]
|			|- data [link]
|			|- src [link]
|				|- License [link] [license.txt]
|				|- Source [link]
|	|- sw_services [link]
|		|- libmetal [link]
|		|- lwip141 [link]
|		|- lwip202 [link]
|		|- openamp [link]
|
|-XilinxProcessorIPLib
|	|- drivers [link]
|		|- avbuf [link]
|		|- ...
|		|- ...
|		|- zdma [link]
|
|-doc [link]
|-lib [link]
|	|- bsp
|		|- standalone [link]
|			|- data [link] 
|			|- doc [link]
|			|- src [link]
|				|- arm [link]
|					|- common [link]
|					|- cortexa53 [link] (Actually ARMv8)
|					|- cortexa9 [link]
|					|- cortexr5 [link]
|           	|- common [link] (no longer listed)
|				|- microblaze [link] (no longer listed)
|				|- profile [link] (no longer listed)
|	|- sw_apps [link]
|		|- ddr_self_refresh [link]
|		|- ....
|		|- ....
|		|- ....
|		|- ....
|		|- zynqmp_fsbl [described below] [link]
|		|- zynqmp_pmufw [described below] [link]
|	|- sw_services [link]
|		|- xilffs [link]
|		|- xilflash [link]
|		|- xilfpga [link]
|		|- xilisf [link]
|		|- xilmfs [link]
|		|- xilpm [link]
|		|- xilrsa [link]
|		|- xilsecure [link]
|		|- xilskey [link]
|
|	Note - All these are libraries and utilize drivers
|
|-mcap
|	|-linux [link]


Building FSBL from git:
==============================
FSBL(zynq_fsbl [link]/zynqmp_fsbl [link]) has 3 directories.
	1. data - It contains files for SDK
	2. src  - It contains the FSBL source files
	3. misc - It contains miscellaneous files required to
		  compile FSBL.
		  For zynq (zynq_fsbl), builds for zc702, zc706, zed are supported.
		  It also contains the ps7_init_gpl.[c/h] with gpl
		  header in respective board directories.
		  For zynqmp (zynqmp_fsbl), builds for zcu102,zcu102-es2 board are
		  supported.
		  


How to compile FSBL:
	Zynq:
	Please refer to the steps in Readme.txt which is at lib/sw_apps/zynq_fsbl/misc/ directory [link]

	ZynqMP
	Please refer to the steps in Readme.txt which is at lib/sw_apps/zynqmp_fsbl/misc/ directory [link]

Building PMUFW from git:
==============================
Please refer to the steps in Readme.txt which is at lib/sw_apps/zynqmp_pmufw/misc/ directory [link]
```

**<u><span>References</span></u>**

-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]