# Swift PetaLinux 2023.1 Installation on Ubuntu 22.04.1 Made Easy

![amd_logo](amd_logo.png)

Slash installation time in half! Discover the essential packages and bash shell setup needed for seamless PetaLinux 2023.1 installation and execution on Ubuntu 22.04.1. Skip the trial and error – our concise guide shares precise steps, sparing you from multiple reinstallation attempts.

## <u><span>Swift PetaLinux 2023.1 Installation on Ubuntu 22.04.1 Made Easy: Steps</span></u>

\# Install missing packages before installing PetaLinux Tools:

```
sudo apt-get update
sudo apt-get install gawk
sudo apt-get install gcc
sudo apt-get install xterm autoconf libtool texinfo zlib1g-dev gcc-multilib build-essential
sudo apt-get install zlib1g 
sudo apt-get install ncurses-bin
sudo apt-get install ncurses-dev
```

\# Run the installer:

```
~/Xilinx_Unified_2023.1_0507_1903/xsetup
```

\# Before running PetaLinux, change the shell:

```
sudo ln -sf bash /bin/sh
# Reverse using: sudo ln -sf dash /bin/sh
```

Note: You'll only need this once unless you reset it.

\# Test that PetaLinux 2023.1 Runs

```
source ~/tools/amd/PetaLinux/2023.1/tool/settings.sh
petalinux-create --help
```

## <u><span>On Error</span></u>

On package error, run this to delete PetaLinux and try again:

```
rm -rf /home/demouser/tools/amd/.xinstall/PetaLinux_2023.1/
rm -rf /home/demouser/tools/amd/PetaLinux/
```

## <u><span>References</span></u>

Logo from https://library.amd.com/media/ (requires a password)