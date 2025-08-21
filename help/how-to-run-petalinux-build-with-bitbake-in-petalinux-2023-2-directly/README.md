# How to Run petalinux-build with BitBake in PetaLinux 2023.1 and 2023.2 Directly

![AMD logo](AMD_Logo.png)

Run a sequence like this to run petalinux-build with BitBake:

```
cd ~/plxprjs/zcu102_0
source ~/amd/2023.2/PetaLinux/settings.sh
export PROOT=${PWD}
source components/yocto/environment-setup-cortexa72-cortexa53-xilinx-linux 
source components/yocto/layers/poky/oe-init-build-env 
export PATH=${XSCT_TOOLCHAIN}/bin:$PATH
export BB_ENV_PASSTHROUGH_ADDITIONS="$BB_ENV_PASSTHROUGH_ADDITIONS PETALINUX PROOT"
bitbake petalinux-image-minimal
```

For Zynq-7000, use:

```
export PROOT=${PWD}
source components/yocto/environment-setup-cortexa9t2hf-neon-xilinx-linux-gnueabi 
source components/yocto/layers/poky/oe-init-build-env 
export PATH=${XSCT_TOOLCHAIN}/bin:$PATH
export BB_ENV_PASSTHROUGH_ADDITIONS="$BB_ENV_PASSTHROUGH_ADDITIONS PETALINUX PROOT"
bitbake petalinux-image-minimal
```