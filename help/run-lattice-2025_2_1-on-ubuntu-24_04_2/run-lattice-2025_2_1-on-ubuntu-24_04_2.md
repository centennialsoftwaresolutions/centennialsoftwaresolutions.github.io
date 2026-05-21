# Run Lattice 2025.2.1 on Ubuntu OS: Ubuntu 24.04.2 LTS x86_64 

### **1. Lattice Propel Builder**

Get **Propel Builder** from [this link](https://www.google.com/search?q=https://www.latticesemi.com/FileExplorer%3Fmedia%3D%7BE3C923A8-9146-40B3-BBA5-19EED5329266%7D%26document_id%3D55142) @ [Lattice Propel Design Environment](https://www.latticesemi.com/en/Products/DesignSoftwareAndIP/FPGAandLDS/LatticePropel).

* **Size:** 3.5 GB
* **md5sum:** `5eb219ccd78ce215878def74d5847d1f`

**Installation Commands:**

```bash
unzip ~/Downloads/Propel_2025.2.1_lin.zip
cat Propel_2025.2.1_lin.md5 
# 979c45119bdabe5f89f1fb4a9277d8b1  Propel_2025.2.1_lin.run
md5sum Propel_2025.2.1_lin.run 
# 979c45119bdabe5f89f1fb4a9277d8b1  Propel_2025.2.1_lin.run
./Propel_2025.2.1_lin.run
# Accept defaults

```

**Install Log:**

```text
[77] Warning: libpng warning: iCCP: known incorrect sRGB profile
[77] Warning: libpng warning: iCCP: cHRM chunk does not match sRGB
[94] Warning: libpng warning: iCCP: known incorrect sRGB profile
[94] Warning: libpng warning: iCCP: cHRM chunk does not match sRGB
[110] Warning: libpng warning: iCCP: known incorrect sRGB profile
[110] Warning: libpng warning: iCCP: cHRM chunk does not match sRGB
*TargetAvailable: 865.19 GB, TargetRequired: 11.08 GB, TargetPath: /home/demo/lscc/propel/2025.2.1, Mount: /
*TempAvailable: 865.19 GB, TempRequired: 256.00 MB, TempPath: /tmp, Mount: /
perform  operation: Mkdir
/home/demo/lscc/propel
perform  operation: Mkdir
/home/demo/lscc/propel/2025.2.1
perform com.latticesemi.esdk operation: Extract
installer://com.latticesemi.esdk/2025.2.1.0content.7z, /home/demo/lscc/propel/2025.2.1
perform com.latticesemi.esdk operation: Extract
installer://com.latticesemi.esdk/2025.2.1.0embeddedsw.7z, /home/demo/lscc/propel/2025.2.1
perform com.latticesemi.esdk operation: Extract
installer://com.latticesemi.esdk/2025.2.1.0pge.7z, /home/demo/lscc/propel/2025.2.1
perform com.latticesemi.esdk operation: Extract
installer://com.latticesemi.esdk/2025.2.1.0questasim.7z, /home/demo/lscc/propel/2025.2.1
perform com.latticesemi.esdk operation: Extract
installer://com.latticesemi.esdk/2025.2.1.0sdk.7z, /home/demo/lscc/propel/2025.2.1
perform com.latticesemi.esdk operation: Extract
installer://com.latticesemi.esdk/2025.2.1.0templates.7z, /home/demo/lscc/propel/2025.2.1
perform com.latticesemi.esdk operation: Extract
installer://com.latticesemi.esdk/2025.2.1.0tools.7z, /home/demo/lscc/propel/2025.2.1
perform com.latticesemi.esdk operation: License

perform com.latticesemi.systembuilder operation: Extract
installer://com.latticesemi.systembuilder/2025.2.1.0builder.7z, /home/demo/lscc/propel/2025.2.1
perform com.latticesemi.systembuilder operation: License

```

---

### **2. Propel Licensing & Initial Execution**

Request a free license from [this link](https://www.latticesemi.com/Support/Licensing/DiamondAndiCEcube2SoftwareLicensing/PropelLicense) under **Lattice Propel** from **Request Free License** @ [https://www.latticesemi.com/en/Support/Licensing.aspx](https://www.latticesemi.com/en/Support/Licensing.aspx)

**Get MAC Address:**

```bash
ip link
ip link | grep link/ether | awk '{print $2}' | tr -d ':'
# 8cdcd42eff11
# 8cdcd42eff10
# 8cb87e53fea8

```

Create or save the **license.dat** to `~/lscc/propel/2025.2.1/builder/rtf/bin/lin64/../../license/`

```bash
vi ~/lscc/propel/2025.2.1/builder/rtf/bin/lin64/../../license/license.dat 

```

**Invoke Builder:**

```bash
~/lscc/propel/2025.2.1/launch_builder.sh

```

**See Error:**

```text
/home/demo/lscc/propel/2025.2.1
/home/demo/lscc/propel/2025.2.1/builder/rtf/bin/lin64/propelbldwrap
[12:15:03.963 qt.qpa.plugin <info>] unknown:0 - Could not load the Qt platform plugin "xcb" in "" even though it was found.
[12:15:03.963  <fatal>] unknown:0 - This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: xcb.

/home/demo/lscc/propel/2025.2.1/launch_builder.sh: line 6: 25725 Aborted                 (core dumped) $base_path/builder/rtf/bin/lin64/propelbldwrap -gui

```

---

### **3. Lattice Radiant Installation**

Get **Radiant** from [this link](https://www.google.com/search?q=https://www.latticesemi.com/FileExplorer%3Fmedia%3D%7BCE860723-F195-4CBC-BAC6-D9187D33821C%7D%26document_id%3D55141) @ [Lattice Propel Design Environment](https://www.latticesemi.com/en/Products/DesignSoftwareAndIP/FPGAandLDS/Radiant).

* **Size:** 5.9 GB
* **md5sum:** `5eb219ccd78ce215878def74d5847d1f`

Extract and start install:

```bash
unzip ~/Downloads/2025.2.1.321.0_Radiant_lin.zip 
# Archive:  /home/demo/Downloads/2025.2.1.321.0_Radiant_lin.zip
#   inflating: 2025.2.1.321.0_Radiant_lin.run  

md5sum ~/Downloads/2025.2.1.321.0_Radiant_lin.zip 
# 87747c228cbd2c067eeb521c797e81bc  /home/demo/Downloads/2025.2.1.321.0_Radiant_lin.zip

md5sum 2025.2.1.321.0_Radiant_lin.run 
# cf58e4c527a5db02e51986d1112a9491  2025.2.1.321.0_Radiant_lin.run

chmod +x 2025.2.1.321.0_Radiant_lin.run 

```

**Install Log:**

```text
demo@demo:~/Desktop$ ./2025.2.1.321.0_Radiant_lin.run 
[64] Warning: libpng warning: iCCP: known incorrect sRGB profile
[76] Warning: libpng warning: iCCP: known incorrect sRGB profile
[88] Warning: libpng warning: iCCP: known incorrect sRGB profile
[99] Warning: libpng warning: iCCP: known incorrect sRGB profile
[111] Warning: libpng warning: iCCP: known incorrect sRGB profile
[123] Warning: libpng warning: iCCP: known incorrect sRGB profile
[135] Warning: libpng warning: iCCP: known incorrect sRGB profile
[146] Warning: libpng warning: iCCP: known incorrect sRGB profile
[158] Warning: libpng warning: iCCP: known incorrect sRGB profile
*TargetAvailable: 841.69 GB, TargetRequired: 12.88 GB, TargetPath: /home/demo/lscc/radiant/2025.2.1, Mount: /
*TempAvailable: 841.69 GB, TempRequired: 256.00 MB, TempPath: /tmp, Mount: /
perform  operation: Mkdir
/home/demo/lscc/radiant
perform  operation: Mkdir
/home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0bin.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0cae_library.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0content.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0data.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0docs.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0examples.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0ip.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0ispfpga.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0scripts.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0synpbase.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: Extract
installer://com.latticesemi.base/2025.2.0.0tcltk.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.base operation: License

perform com.latticesemi.uaplatform operation: Extract
installer://com.latticesemi.uaplatform/2025.2.0.0cae_library.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.uaplatform operation: Extract
installer://com.latticesemi.uaplatform/2025.2.0.0ispfpga.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.questasim.tool operation: Extract
installer://com.latticesemi.questasim.tool/2025.2.0.0cae_library.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.questasim.tool operation: Extract
installer://com.latticesemi.questasim.tool/2025.2.0.0questasim.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.programmerng operation: Extract
installer://com.latticesemi.programmerng/2025.2.0.0programmer.7z, /home/demo/lscc/radiant/2025.2.1
perform com.latticesemi.device.je5d00 operation: Extract
installer://com.latticesemi.device.je5d00/2025.2.0.0ispfpga.7z, /home/demo/lscc/radiant/2025.2.1

```

---

### **4. Radiant Licensing**

Get Radiant license @ [https://www.latticesemi.com/Support/Licensing/DiamondAndiCEcube2SoftwareLicensing/Radiant](https://www.latticesemi.com/Support/Licensing/DiamondAndiCEcube2SoftwareLicensing/Radiant)

**Get MAC & Save License:**

```bash
ip link | grep link/ether | awk '{print $2}' | tr -d ':'

vi ~/lscc/radiant/2025.2.1/bin/lin64/../../license/license.dat

```

---

### **5. Fix Radiant and Propel Errors**

Run the following commands to apply workarounds and install required dependencies:

```bash
# Workaround
mv ~/lscc/radiant/2025.2/bin/lin64/gnu/libstdc++.so.6 ~/lscc/radiant/2025.2.1/bin/lin64/gnu/libstdc++.so.6.bak
mv ~/lscc/propel/2025.2.1/sdk/bin/lin64/libstdc++.so.6 ~/lscc/propel/2025.2.1/sdk/bin/lin64/libstdc++.so.6.bak

# For at least make
sudo apt-get install build-essential 

# Install required libs
sudo apt update
sudo apt install libxcb-xinerama0 libxcb-cursor0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-render-util0 libxcb-xkb1 libxkbcommon-x11-0 -y
sudo apt install libdbus-1-3 -y
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install libgl1:i386 libgl1-mesa-dri:i386 libglu1-mesa:i386

# Check system library
~/lscc/radiant/2025.2/bin/lin64/check_systemlibrary_radiant.bash 
cat ./check_systemlibrary.log
grep 'is missing' ./check_systemlibrary.log | awk '{print $1}' | while IFS= read -r missing_app; do sudo apt install -y "$missing_app"; done

# Install libs you need that check_systemlibrary_radiant.bash fails to catch
sudo apt install -y libusb-0.1-4
sudo apt install -y lsb-release
sudo apt install -y lsb-base
sudo apt install -y mesa-utils
sudo apt install -y libgl1
sudo apt install -y libglu1-mesa

# 

```

---

### **6. Launch Applications**

**Launch Builder:**

```bash
~/lscc/propel/2025.2.1/launch_builder.sh # Builder project file: *.sbx 

```

**Launch Radiant:**

```bash
~/lscc/radiant/2025.2.1/bin/lin64/radiant # Radiant project file: *.rdf

```

**Launch SDK (Propel):**

```bash
~/lscc/propel/2025.2.1/launch_propel.sh

```

---

### **7. Install USB Drivers**

```bash
sudo groupadd plugdev
sudo usermod -aG plugdev demo # username
sudo ~/lscc/radiant/2025.2/data/vmdata/udevsetup_ubuntu

```

*Note: Log off, log on.*

---

### **8. System Info from neofetch**

```text
demo@demo:~/Desktop$ neofetch --stdout
demo@demo 
--------- 
OS: Ubuntu 24.04.2 LTS x86_64 
Host: HP Z840 Workstation 
Kernel: 6.17.0-23-generic 
Uptime: 13 hours, 31 mins 
Packages: 1721 (dpkg), 13 (snap) 
Shell: bash 5.2.21 
Resolution: 3840x2160 
DE: Xfce 4.18 
WM: Xfwm4 
WM Theme: Default 
Theme: Greybird [GTK2], Adwaita [GTK3] 
Icons: elementary-xfce-dark [GTK2], Adwaita [GTK3] 
Terminal: xfce4-terminal 
Terminal Font: Monospace 12 
CPU: Intel Xeon E5-2697 v4 (72) @ 3.600GHz 
GPU: NVIDIA Quadro K4200 
Memory: 3288MiB / 257814MiB 

```