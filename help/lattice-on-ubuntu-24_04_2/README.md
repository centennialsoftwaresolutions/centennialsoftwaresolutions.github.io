# Log of Lattice Propel and Radiant 2025.2.1 Install on Ubuntu 24.04.2

<u>**Install Propel**</u>

Downloaded **Lattice Propel 2025.2.1 64-bit for Linux** from [link](https://www.latticesemi.com/view_document?document_id=55142) on [page](https://www.latticesemi.com/en/Products/DesignSoftwareAndIP/FPGAandLDS/LatticePropel).

Unzipped and checked MD5:

```
demo@demo:~/Desktop$ 
unzip ~/Downloads/Propel_2025.2.1_lin.zip 

Archive:  /home/demo/Downloads/Propel_2025.2.1_lin.zip
 extracting: Propel_2025.2.1_lin.md5  
  inflating: Propel_2025.2.1_lin.run  

demo@demo:~/Desktop$ 
md5sum Propel_2025.2.1_lin.run

979c45119bdabe5f89f1fb4a9277d8b1  Propel_2025.2.1_lin.run

demo@demo:~/Desktop$ 
cat Propel_2025.2.1_lin.md5 
979c45119bdabe5f89f1fb4a9277d8b1  Propel_2025.2.1_lin.run
```

Ran the installer and used all defaults:

```
chmod +x Propel_2025.2.1_lin.run 
./Propel_2025.2.1_lin.run
```

Got NIC (aka link/ether):

```
ip addr
```

Requested a **Lattice Propel node-locked license** from [link](https://www.latticesemi.com/Support/free-software-license) after logging in with my account.

Saved the emailed `license.dat` to `~/lscc/propel/2025.2.1/license/`.

**<u>Install Radiant</u>**

Downloaded **Radiant 2025.2.1 64-bit for Linux** from [link](https://www.latticesemi.com/view_document?document_id=55141) on [page](https://www.latticesemi.com/en/Products/DesignSoftwareAndIP/FPGAandLDS/Radiant).

Unzipped:

```
chmod +x 2025.2.1.321.0_Radiant_lin.run 
./2025.2.1.321.0_Radiant_lin.run 
```

Requested a Lattice Radiant node-locked license from [link](https://www.latticesemi.com/Support/free-software-license) after logging in with my account.

Saved the emailed `license.dat` to `~/lscc/propel/2025.2.1/builder/rtf/license`/.

**<u>Handle Missing Libs</u>**

Check Radiant libs:

```
cd ~/lscc/radiant/2025.2.1/bin/lin64/
source ./check_systemlibrary_radiant.bash 
grep 'is missing' ./check_systemlibrary.log 
```

Install missing:

```
sudo apt install libjpeg-dev 
sudo apt install libxcb-xinput0 
sudo apt install libxcb-xinerama0
sudo apt install libxcb-cursor0
sudo apt install libusb-0.1-4

```

Check Propel libs:

```
cd ~/lscc/propel/2025.2.1
source check_systemlibrary_propel.bash
grep 'is missing' ./check_systemlibrary.log 
```

Install missing:

```
sudo apt install libxcb-util-dev 
sudo apt install libxcb-xkb-dev 
sudo apt install libxcb-xinput-dev 
sudo apt install libxkbcommon-dev 
sudo apt install build-essential 
```

**<u>Install USB Drivers</u>**

```
sudo groupadd plugdev
sudo usermod -aG plugdev demo-user # username
sudo ~/lscc/radiant/2025.2.1/data/vmdata/udevsetup_ubuntu
```

**<u>Apply Workarounds</u>** 

```
mv ~/lscc/radiant/2025.2.1/bin/lin64/gnu/libstdc++.so.6 ~/lscc/radiant/2025.2.1/bin/lin64/gnu/libstdc++.so.6.bak

mv ~/lscc/propel/2025.2.1/sdk/bin/lin64/libstdc++.so.6 ~/lscc/propel/2025.2.1/sdk/bin/lin64/libstdc++.so.6.bak
```

<u>**Test**</u>

```
~/lscc/propel/2025.2.1/launch_builder.sh
```

