# Quickly Build 2020.2 ZCU102

Sans network.

# Get ZCU102 PetaLinux 2020.2 downloads

An AMD account sign-in is required.

- Prebuilt images

  - https://amd-ax-dlf.entitlenow.com/dl/ul/2020/11/20/R210411061/xilinx-zynqmp-common-v2020.2.tar.gz?hash=agBbLk9_8uN05Ozmq6_uCg&expires=1761118950&filename=xilinx-zynqmp-common-v2020.2.tar.gz

- Need:

  - PetaLinux Tools 2020.2
    - https://amd-ax-dl.entitlenow.com/dl/ul/2020/11/20/R210411071/petalinux-v2020.2-final-installer.run?hash=IRZG-6s7Ut_W8q81qmctBw&expires=1761118812&filename=petalinux-v2020.2-final-installer.run
  - ZCU102 BSP
    - https://amd-ax-dlf.entitlenow.com/dl/ul/2020/11/20/R210411040/xilinx-zcu102-v2020.2-final.bsp?hash=raXY_DbHkq61PcYE-KDFbw&expires=1761118886&filename=xilinx-zcu102-v2020.2-final.bsp

- Speeds up Builds

  - SSTATE_CACHE ( set SSTATE_DIR in ) ( Shared-State Cache ) 
    - https://amd-ax-dl.entitlenow.com/dl/ul/2020/11/20/R210411015/sstate_aarch64_2020.2.tar.gz?hash=d1sL1SpdVqJ5HiBaDg2TEA&expires=1761169967&filename=sstate_aarch64_2020.2.tar.gz

  - Downloads ( set DL_DIR )
    - https://amd-ax-dl.entitlenow.com/dl/ul/2020/11/20/R210411002/downloads_2020.2.tar.gz?hash=klwo-7Hmm0D3AHKLRwx13A&expires=1761120510&filename=downloads_2020.2.tar.gz

- Reference
  - Licenses and Source Code
    - https://amd-ax-dlf.entitlenow.com/dl/ul/2020/11/20/R210411060/xilinx-zcu102-2020.2.tar.gz?hash=1RLdZLneUUGrl2QEIw6N0g&expires=1761119205&filename=xilinx-zcu102-2020.2.tar.gz

# Install PetaLinux Tools

```
mkdir -p ~/petalinux-v2020.2/

chmod +x petalinux-v2020.2-final-installer.run

./petalinux-v2020.2-final-installer.run --log petalinux_install_log_$(date +%F_%H-%M-%S).txt -d ~/petalinux-v2020.2/  -p "aarch64 arm microblaze_lite microblaze_full"

# Enter q y Enter q y Enter q y Enter
```

# Switch /bin/sh to bash

```
sudo dpkg-reconfigure dash
# Select No

# Check
ls -l /bin/sh
```

# Extract the ZCU102 BSP

```
source ~/petalinux-v2020.2/settings.sh

mkdir -p ~/zcu102-v2020.2
cd ~/zcu102-v2020.2

petalinux-create -t project -n zcu102 -s xilinx-zcu102-v2020.2-final.bsp 

# May take a little time to complete 
# INFO: New project successfully created in /home/demouser/zcu102-v2020.2/zcu102 to come up

cd ~/zcu102-v2020.2/zcu102
```

# Use local downloads and the sstate cache

```
cd ~/zcu102-v2020.2/zcu102

# Get env:
petalinux-build -c -e > bitbake.env.orig # A hack to access bitbake directly

cat <<'EOF' >> project-spec/meta-user/conf/petalinuxbsp.conf

# Disable all network access.

# Use shared local caches
DL_DIR = "/home/demouser/petalinux-v2020.2/downloads"
SSTATE_DIR = "/home/demouser/petalinux-v2020.2/sstate_aarch64_2020.2"

# Absolutely disable any network fetch
BB_NO_NETWORK = "1"

# Redirect any remote fetch attempts to local mirrors
PREMIRRORS = "\
    git://.*/.* file:///home/demouser/petalinux-v2020.2/downloads/ \n \
    ftp://.*/.* file:///home/demouser/petalinux-v2020.2/downloads/ \n \
    http://.*/.* file:///home/demouser/petalinux-v2020.2/downloads/ \n \
    https://.*/.* file:///home/demouser/petalinux-v2020.2/downloads/ \
"

# Redirect sstate lookups to local cache only
SSTATE_MIRRORS = "\
    file://.* file:///home/demouser/petalinux-v2020.2/sstate_aarch64_2020.2/PATH;downloadfilename=PATH \
"

# ==========================================================
# End offline configuration
# ==========================================================

EOF


# Check
petalinux-build -c -e > bitbake.env.next2
```

# Use Every Core

```
cat <<'EOF' >> project-spec/meta-user/conf/petalinuxbsp.conf

BB_NUMBER_THREADS = "8"
PARALLEL_MAKE = "-j8"

EOF
```

# Use CCache

Speeds up compile times by 30-70%.

This will cause a full rebuild the first time its run.

```
sudo apt install ccache

cat <<'EOF' >> project-spec/meta-user/conf/petalinuxbsp.conf

INHERIT += "ccache"
CCACHE_DIR = "/home/demouser/yocto-cache/ccache"

EOF
```

# Build

```
source ~/petalinux-v2020.2/settings.sh
cd ~/zcu102-v2020.2/zcu102
petalinux-build
```

