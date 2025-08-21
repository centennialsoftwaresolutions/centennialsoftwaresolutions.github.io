# 2017.4 vs 2018.1 PetaLinux Tools Reference Guide Diff

![xilinx_logo_1](xilinx_logo_1.png)

This post presents the differences of substance between the 2017.4 release of the PetaLinux Tools Reference Guide and the 2018.1 release.

**<u><span>Commentary</span></u>**

If you've been waiting for better PetaLinux Tools documentation before you learn how to use PetaLinux Tools, you should find something you can now use. You should use 2018.2.

**Note**: The differences between 2018.1 and 2018.2 are presented at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/are-hdf-files-going-away)\].

**<u><span>Differences</span></u>**

[#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1) - The reference to **meta-linaro-toolchain** removed.

![meta_linaro_toolchain_reference_removed_2](meta_linaro_toolchain_reference_removed_2.png)

[#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2) - The MicroBlaze toolchain is from Yocto.

![microblaze_toolchain_from_yocto_3](microblaze_toolchain_from_yocto_3.png)

[#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3) - RHEL 7.4 and CentOS 7.4 were added to the supported OSs list and the version of Ubuntu that is supported was changed from 16.04.1 to 16.04.3.

![rhel_and_centos_supported_os_4](rhel_and_centos_supported_os_4.png)

[#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4) - Packages and Linux Workstation Table Updates

<u><span>Summary</span></u>

Dropped:

-   python for all OSs
    
-   detoolset-2 from the table
    

Added:

-   gcc: **gcc-4.8.5-11.el7.x86\_64** for CentOS and RHEL
    
-   g++: **gcc-c++-4.8.5-11.el7.x86\_64** for CentOS and RHEL
    
-   32-bit glibc: **libc-2.17-157.el7\_3.4.i686** and **glibc-2.17-157.el7\_3.4.x86\_64** for CentOS and RHEL
    
-   libstdc++: **libstdc++-4.8.5-11.el7.x86\_64** and **libstdc++-4.8.5-11.el7.i686** for CentOS and RHEL
    

<u><span>Data</span></u>

![data_5](data_5.png)

![data_6](data_6.png)

![data_7](data_7.png)

![data_8](data_8.png)

[#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5) - A new Design Flow Overview table was added.

![new_design_flow_overview_added_9](new_design_flow_overview_added_9.png)

[#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6) - A clarification regarding PetaLinux BSP usage and installation: PetaLinux BSPs can be used to create your own BSPs: you don't need to create your own from scratch.

![clarification_of_petalinux_bsp_usage_10](clarification_of_petalinux_bsp_usage_10.png)

[#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7) - A clarification regarding NFS mounted.

![clarification_regarding_nfs_mounted_11](clarification_regarding_nfs_mounted_11.png)

[#8](https://www.centennialsoftwaresolutions.com/blog/hashtags/8) - References to Rev-B, Rev-C and Rev-D silicon have been removed.

![references_to_rev_b_c_and_d_removed_12](references_to_rev_b_c_and_d_removed_12.png)

[#9](https://www.centennialsoftwaresolutions.com/blog/hashtags/9) - A note that can be disregarded that HDF files are being depreciated. It can be disregarded because the note is removed in the 2018.2 release of the doc.

![disregard_hdf_files_13](disregard_hdf_files_13.png)

[#10](https://www.centennialsoftwaresolutions.com/blog/hashtags/10) - A note that the **Structure of PetaLinux Projects** is now listed in Appendix B, a note that says that how to compile PMUFW and ATF for the A53 is in Appendix C and a note that lists a doc that lists a doc that describes how to compile the FSBL to run on the R5.

![structure_of_petalinux_projects_moved_14](structure_of_petalinux_projects_moved_14.png)

[#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11) - A note was added that says you can't have select MicroBlaze if you're using Zynq or Zynq UltraScale+ (note: this should read: Zynq-7000 or Zynq UltraScale+ MPSoC).

![note_added_about_cant_select_microblaze_15](note_added_about_cant_select_microblaze_15.png)

[#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12) - zcu-reva and zcu104-revc have been added.

![zcu_reva_and_zcu104_revc_added_16](zcu_reva_and_zcu104_revc_added_16.png)

[#13](https://www.centennialsoftwaresolutions.com/blog/hashtags/13) - More HDF warnings that can be ignored.

![more_hdf_warnings_can_be_ignored_17](more_hdf_warnings_can_be_ignored_17.png)

[#14](https://www.centennialsoftwaresolutions.com/blog/hashtags/14) - Auto Config Settings documentation has been moved to Setting from Appendix C.

![auto_config_settings_documentation_moved_18](auto_config_settings_documentation_moved_18.png)

[#15](https://www.centennialsoftwaresolutions.com/blog/hashtags/15) - A clarification on what petalinux-build does.

![clarification_on_petalinux_build_19](clarification_on_petalinux_build_19.png)

[#16](https://www.centennialsoftwaresolutions.com/blog/hashtags/16) - A clarification on where the Linux binary images are stored.

![clarification_on_location_of_linux_binary_images_20](clarification_on_location_of_linux_binary_images_20.png)

[#17](https://www.centennialsoftwaresolutions.com/blog/hashtags/17) - **Troubleshooting** has been removed.

![troubleshooting_removed_21](troubleshooting_removed_21.png)

[#18](https://www.centennialsoftwaresolutions.com/blog/hashtags/18) - A **Build Optimizations** section has been added. See the doc for the full section. Only a snippet is given here.

![build_optimization_section_added_22](build_optimization_section_added_22.png)

[#19](https://www.centennialsoftwaresolutions.com/blog/hashtags/19) - A clarification on what --prebuilt 3 means (and what else you can pass: 1 and 2).

![clarification_on_prebuilt_3_23](clarification_on_prebuilt_3_23.png)

[#20](https://www.centennialsoftwaresolutions.com/blog/hashtags/20) - An additional note in the QEMU section that you build the system image with petalinux-build.

![additional_note_in_qemu_section_24](additional_note_in_qemu_section_24.png)

[#21](https://www.centennialsoftwaresolutions.com/blog/hashtags/21) - An example of a QEMU start up log has been added.

![qemu_start_up_log_added_25](qemu_start_up_log_added_25.png)

[#22](https://www.centennialsoftwaresolutions.com/blog/hashtags/22) - A way to boot a specific Linux image when booting with QEMU has been added.

![boot_specific_linux_image_with_qemu_added_26](boot_specific_linux_image_with_qemu_added_26.png)

[#23](https://www.centennialsoftwaresolutions.com/blog/hashtags/23) - A way to pass a dtb when booting QEMU has been added.

![way_to_pass_a_dtb_when_booting_with_qemu_added_27](way_to_pass_a_dtb_when_booting_with_qemu_added_27.png)

[#24](https://www.centennialsoftwaresolutions.com/blog/hashtags/24) - A clarification that in INITRAMFS mode the rootfw is included in kernel images.

![clarification_that_in_initramfs_mode_rootfw_included_28](clarification_that_in_initramfs_mode_rootfw_included_28.png)

[#25](https://www.centennialsoftwaresolutions.com/blog/hashtags/25) - The number of sub-steps listed in step 3 of **Copying Image Files** has been reduced.

![sub_steps_in_copying_image_files_reduced_29](sub_steps_in_copying_image_files_reduced_29.png)

[#26](https://www.centennialsoftwaresolutions.com/blog/hashtags/26) - A note about Zynq UltraScale+ MPSoC has been removed. Both instances are listed here.

![note_about_zynq_ultrascale_removed_1_30](note_about_zynq_ultrascale_removed_1_30.png)

![note_about_zynq_ultrascale_removed_2_31](note_about_zynq_ultrascale_removed_2_31.png)

[#27](https://www.centennialsoftwaresolutions.com/blog/hashtags/27) - A section on adding a Yocto layer has been added.

![adding_yocto_layers_section_added_32](adding_yocto_layers_section_added_32.png)

[#28](https://www.centennialsoftwaresolutions.com/blog/hashtags/28) - A section on adding an existing recipe into the rootfs has been added.

![adding_existing_recipe_section_added_33](adding_existing_recipe_section_added_33.png)

[#29](https://www.centennialsoftwaresolutions.com/blog/hashtags/29) - A section on adding a package group has also been added.

![adding_package_group_34](adding_package_group_34.jpg)

![added_package_group_cont_35](added_package_group_cont_35.png)

[#30](https://www.centennialsoftwaresolutions.com/blog/hashtags/30) - A whole section has been added describing the PetaLinux Menuconfig System, Settings and hardware/Linux interaction. A snippet is shown here.

![advanced_configurations_section_36](advanced_configurations_section_36.png)

[#31](https://www.centennialsoftwaresolutions.com/blog/hashtags/31) - A section on Configuring Project Components was added. A snippet is shown here.

![configuring_project_components_section_added_37](configuring_project_components_section_added_37.png)

[#32](https://www.centennialsoftwaresolutions.com/blog/hashtags/32) - The example that shows you how to add your own DTS entries has been updated. A snippet is shown here.

![updated_add_your_own_dts_entries_updated_38](updated_add_your_own_dts_entries_updated_38.png)

[#33](https://www.centennialsoftwaresolutions.com/blog/hashtags/33) - A write up on SDK Generation has been added. A snippet is shown here.

![sdk_generation_write_up_added_39](sdk_generation_write_up_added_39.png)

[#34](https://www.centennialsoftwaresolutions.com/blog/hashtags/34) - The write up for adding a e-SDK recipe has been removed. The original snippet is shown here.

![write_up_for_adding_e_sdk_removed_40](write_up_for_adding_e_sdk_removed_40.png)

[#35](https://www.centennialsoftwaresolutions.com/blog/hashtags/35) - Adding package groups was moved. The original snippet is shown here.

![adding_package_groups_moved_41](adding_package_groups_moved_41.png)

[#36](https://www.centennialsoftwaresolutions.com/blog/hashtags/36) - Additional sections for **Machine Support**, **SoC** (Its listed as SOC which is wrong) **Variant Support**, **Image Features** and **Migration** have been added. Snippets given.

![machine_support_section_added_42](machine_support_section_added_42.png)

![soc_variant_support_43](soc_variant_support_43.png)

![image_features_added_44](image_features_added_44.png)

![migration_section_added_45](migration_section_added_45.png)

[#37](https://www.centennialsoftwaresolutions.com/blog/hashtags/37) - Adding support for initramfs's larger than 2 GB and **Applying Patches to Components** has been removed.

![applying_patches_to_components_removed_46](applying_patches_to_components_removed_46.png)

**<u><span>References</span></u>**

-   The 2017.4 \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_4/ug1144-petalinux-tools-reference-guide.pdf)\] and 2018.1 \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_1/ug1144-petalinux-tools-reference-guide.pdf)\] versions of ug1144-petalinux-tools-refence-guide.pdf were compared using [<u><span>https://draftable.com</span></u>](https://draftable.com/)
    
-   Full diff at \[[<u><span>link</span></u>](https://draftable.com/compare/GaQUUoORQYIK)\]
    
-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]