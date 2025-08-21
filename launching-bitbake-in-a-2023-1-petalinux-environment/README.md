# Launching Bitbake in a 2023.1 PetaLinux Environment: A Guide Post-petalinux-build.

![amd_logo](amd_logo.png)

This post shows how to launch bitbake from a 2023.1 PetaLinux environment after a successful petalinux-build of xilinx-zcu102-v2023.1-05080224.bsp.

PetaLinux Tools installed under ~/tools/amd

ZCU102 PetaLinux project created under ~/work/baseaddr/

## <u><span>Enable and Launch Bitbake</span></u>

```
source ~/tools/amd/PetaLinux/2023.1/tool/settings.sh
cd ~/work/baseaddr/xilinx-zcu102-2023.1
source components/yocto/environment-setup-cortexa72-cortexa53-xilinx-linux
source components/yocto/layers/poky/oe-init-build-env
export PROOT=/home/demouser/work/baseaddr/xilinx-zcu102-2023.1
export BB_ENV_PASSTHROUGH_ADDITIONS="$BB_ENV_PASSTHROUGH_ADDITIONS PETALINUX PROOT"
bitbake -s
```

Related solution at https://support.xilinx.com/s/question/0D54U00006ussErSAI/petalinux-20231-fresh-project-bitbake-parse-error-with-ostree-recipe-in-metaopenembedded?language=en_US&t=1694320777163 

## <u><span>References</span></u>

Logo from https://library.amd.com/media/ (requires a password)