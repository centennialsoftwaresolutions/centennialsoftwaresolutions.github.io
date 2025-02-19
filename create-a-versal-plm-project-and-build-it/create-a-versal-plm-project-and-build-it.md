# Create a Versal PLM project and build it with XSCT

This post describes creating and building a Versal PLM project from the command line with XSCT. If you'd like to do it graphically with Vitis, refer to [<u><span>this post</span></u>](https://www.centennialsoftwaresolutions.com/post/create-a-versal-plm-project-and-built-it-with-vitis-classic) instead. After creating the PLM, follow the instructions in [<u><span>this next post</span></u>](https://www.centennialsoftwaresolutions.com/post/create-a-versal-boot-image-and-launch-plm-on-hardware) to create a bootable image from it and launch it on hardware.

First, launch xsct and create a workspace for the new project

```
$ mkdir /home/user/plmws
$ source /tools/Xilinx/Vitis/2023.2/settings64.sh
$ xsct% cd /home/user/plmws
% setws .
```

Next, create the PLM application project with your xsa

```
% app create -name plm -hw /path/to/xsa_file.xsa -template "versal PLM" -os standalone -proc psv_pmc_0
```

This will create 3 folders:

-   plm (contains the PLM application project, named plm because that’s what was specified as the “-name” arg above)
    
-   plm\_system (contains the system project)
    
-   another folder containing the platform project (name varies based on the xsa)
    

Finally, build the PLM

```
% app build -name plm
```

The file "plm/debug/plm.elf" now exists.

You can edit the PLM source code and rebuild it. For example:

```
vim &lt;platform_project_folder&gt;/psv_pmc_0/standalone_domain/bsp/psv_pmc_0/libsrc/xilplmi_v1_9/src/xplmi.c
```

In XPlmi\_PrintPlmBanner(): on line 235, add a new print:

```
XPlmi_Printf(DEBUG_PRINT_ALWAYS, "This is my custom PLM\n\r");
```

Rebuild the PLM by running "app build -name plm" in xsct.

```
strings plm/debug/plm.elf | grep This
=&gt; "This is my custom PLM" is found in the executable
```

References: https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/2037088327/Versal+Platform+Loader+and+Manager