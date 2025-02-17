# Create a Versal PLM project and build it with Vitis Classic

This post shows how to create a Versal PLM with Vitis Classic (versions ≤2023.1, or 2023.2 when launched with the \`-classic\` command line argument). If you'd like to do this on the command line with XSCT, refer to [<u><span>this post</span></u>](https://www.centennialsoftwaresolutions.com/post/create-a-versal-plm-project-and-build-it) instead. After creating the PLM, follow the instructions in [<u><span>this next post</span></u>](https://www.centennialsoftwaresolutions.com/post/create-a-versal-boot-image-and-launch-plm-on-hardware) to create a bootable image from it and launch it on hardware.

## 1) Launch Vitis

```
$ source /tools/Xilinx/Vitis/2023.2/settings64.sh

$ vitis                  (versions 2023.1 and earlier)
$ vitis -classic         (versions 2023.2 and later)
```

## 2) Select your workspace directory and create a new application project

Click on Create Application Project and skip the welcome screen in the dialog that pops up.

![create_application_project_1](create_application_project_1.png)

![new_application_project_2](new_application_project_2.png)

Select the hardware platform. Use the dropdown box to select vck190 or other Xilinx dev kits; otherwise, use the ‘Browse’ button to pick the XSA file that you exported from Vitis or that your board’s manufacturer provided.

The Platform Name field will get filled in automatically; leave it at the default and click Next.

![platform_name_field_3](platform_name_field_3.png)

Enter an application project name – “plm” will work fine. The system project name will be automatically filled in.

Select versal\_cips\_0\_pspmc\_0\_psv\_pmc\_0 as the processor.

Leave other settings at the default and click next.

![enter_plm_4](enter_plm_4.png)

Click Next on the Domain page - no changes needed here.

![next_domain_page_5](next_domain_page_5.png)

Select “versal PLM” as the application template and click Finish.

![application_template_6](application_template_6.png)

## 1) Modify and build the PLM

Vitis will open the PLM project. Open xplm\_main.c from the left sidebar.

Add a new XPlmi\_Printf to distinguish this from the default PLM:

```
XPlmi_Printf(DEBUG_PRINT_ALWAYS, "This is my Vitis PLM!\n\r");
```

![modify_and_build_plm7](modify_and_build_plm_7.png)

Right click the “plm” project (the first child of “plm\_system”) and build it.

![build_project_8](build_project_8.png)

The console will show this when the build is finished:

![finished_build_9](finished_build_9.png)

The built PLM ELF will be present in the Vitis workspace directory at plm/Debug/plm.elf.

![plm_elf_10](plm_elf_10.png)

Next, follow the steps in [<u><span>this post</span></u>](https://www.centennialsoftwaresolutions.com/post/create-a-versal-boot-image-and-launch-plm-on-hardware) to pack this PLM into a boot image and boot it on hardware.

## References

Header image from https://www.xilinx.com/products/silicon-devices/acap/versal-ai-core.html#video