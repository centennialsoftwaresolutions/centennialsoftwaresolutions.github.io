# Breaking Down a Bitbake Line: The 'do_compile' Step for Xilinx Linux with petalinux-build

![yocto_project_logo](yocto_project_logo.png)

This post shows a single line of bitbake output decoded, specifically the do\_compile step of the Xilinx Linux kernel as started via petalinux-build.

## A Single Line of Bitbake Output

0: linux-xlnx-6.1.5-xilinx-v2023.1+gitAUTOINC+716921b6d7-r0 do\_compile - 1m43s (pid 412225)

## Decoded

**0**: This is the task number or ID. When you run bitbake, and it starts building various tasks, each task is assigned a unique ID. This makes identifying and tracking tasks easier, especially if you need to diagnose build issues.

**linux-xlnx-6.1.5-xilinx-v2023.1+gitAUTOINC+716921b6d7-r0**: This is the name and version of the recipe being built.

**linux-xlnx**: The recipe name. This indicates a Linux kernel recipe specifically tailored for Xilinx devices.

**6.1.5**: The base version of the Linux kernel being used.

**xilinx-v2023.1**: A custom version tag; a Xilinx-specific revision based on the 2023.1 release.

**+gitAUTOINC+716921b6d7**: A bitbake-specific suffix:

**gitAUTOINC**: Indicates that the recipe fetches sources from a git repository, and the version is automatically determined from the latest commit.

**716921b6d7**: A shortened git commit hash; the exact commit from which the source was fetched.

**\-r0**: Revision number of the recipe. The number after -r denotes the revision. If the recipe is updated or patched, this number will increment.

**do\_compile**: This indicates the task being performed for the recipe. In Yocto/OpenEmbedded, the build process is divided into several tasks, such as fetching (do\_fetch), patching (do\_patch), configuring (do\_configure), compiling (do\_compile), installing (do\_install), and packaging (do\_package), among others. The do\_compile task, is responsible for compiling the source code.

**\- 1m43s**: This is the time taken to complete the do\_compile task or the time it has taken up to this point. In this case, it took 1 minute and 43 seconds.

**(pid 412225)**: This indicates the Process ID (PID) associated with the task. This is useful for debugging or tracking the task in the system's process list.

## <u><span>Related</span></u>

bitbake linux-xlnx:do\_listtasks

```
do_assemble_fitimage                  
do_assemble_fitimage_initramfs        
do_build                              Default task for a recipe - depends on all other normal tasks required to 'build' a recipe
do_build_without_rm_work              
do_bundle_initramfs                   Combines an initial ramdisk image and kernel together to form a single image
do_checkuri                           Validates the SRC_URI value
do_clean                              Removes all output files for a target
do_cleanall                           Removes all output files, shared state cache, and downloaded source files for a target
do_cleansstate                        Removes all output files and shared state cache for a target
do_compile                            Compiles the source in the compilation directory
do_compile_kernelmodules              Compiles loadable modules for the Linux kernel
do_config_analysis                    
do_configure                          Configures the source by enabling and disabling any build-time and configuration options for the software being built
do_deploy                             Writes deployable output files to the deploy directory
do_deploy_setscene                    Writes deployable output files to the deploy directory (setscene version)
do_deploy_source_date_epoch           
do_deploy_source_date_epoch_setscene   (setscene version)
do_devshell                           Starts a shell with the environment set up for development/debugging
do_diffconfig                         Compares the old and new config files after running do_menuconfig for the kernel
do_fetch                              Fetches the source code
do_install                            Copies files from the compilation directory to a holding area
do_kernel_checkout                    Checks out source/meta branches for a linux-yocto style kernel
do_kernel_configcheck                 Validates the kernel configuration for a linux-yocto style kernel
do_kernel_configme                    Assembles the kernel configuration for a linux-yocto style kernel
do_kernel_generate_rsa_keys           
do_kernel_link_images                 Creates a symbolic link in arch/$arch/boot for vmlinux and vmlinuz kernel images
do_kernel_metadata                    
do_kernel_version_sanity_check        
do_listtasks                          Lists all defined tasks for a target
do_menuconfig                         Runs 'make menuconfig' for the kernel
do_package                            Analyzes the content of the holding area and splits it into subsets based on available packages and files
do_package_qa                         Runs QA checks on packaged files
do_package_qa_setscene                Runs QA checks on packaged files (setscene version)
do_package_setscene                   Analyzes the content of the holding area and splits it into subsets based on available packages and files (setscene version)
do_package_write_rpm                  Creates the actual RPM packages and places them in the Package Feed area
do_package_write_rpm_setscene         Creates the actual RPM packages and places them in the Package Feed area (setscene version)
do_packagedata                        Creates package metadata used by the build system to generate the final packages
do_packagedata_setscene               Creates package metadata used by the build system to generate the final packages (setscene version)
do_patch                              Locates patch files and applies them to the source code
do_populate_lic                       Writes license information for the recipe that is collected later when the image is constructed
do_populate_lic_setscene              Writes license information for the recipe that is collected later when the image is constructed (setscene version)
do_populate_sysroot                   Copies a subset of files installed by do_install into the sysroot in order to make them available to other recipes
do_populate_sysroot_setscene          Copies a subset of files installed by do_install into the sysroot in order to make them available to other recipes (setscene version)
do_prepare_recipe_sysroot             
do_pydevshell                         Starts an interactive Python shell for development/debugging
do_rm_work                            Removes work files after the build system has finished with them
do_rm_work_all                        Top-level task for removing work files after the build system has finished with them
do_savedefconfig                      Creates a minimal Linux kernel configuration file
do_shared_workdir                     
do_shared_workdir_setscene             (setscene version)
do_sizecheck                          Checks the size of the kernel image against KERNEL_IMAGE_MAXSIZE (if set)
do_strip                              Strips unneeded sections out of the Linux kernel image
do_symlink_kernsrc                    
do_transform_kernel                   
do_uboot_assemble_fitimage            
do_uboot_generate_rsa_keys            
do_unpack                             Unpacks the source code into a working directory
do_validate_branches                  Ensures that the source/meta branches are on the locations specified by their SRCREV values for a linux-yocto style kernel
```

Per [<u><span>https://www.yoctoproject.org/logos-and-guidelines/</span></u>](https://www.yoctoproject.org/logos-and-guidelines/) **the** _"Yocto Project and all related marks and logos are trademarks of The Linux Foundation. This website is not, in any way, endorsed by the Yocto Project or The Linux Foundation."_