# Hacking the 2018.2 PetaLinux Tools Installer

![xilinx_logo_1](xilinx_logo_1.png)

This post shows some ways to hack petalinux-v2018.2-final-installer.run

**<u><span>Hacks</span></u>**

**Pull Out the Bash Script**

```
awk '1;/^##__PLNXSDK_FOLLOWS__/{if (NR>1) exit}' petalinux-v2018.2-final-installer.run > petalinux.sh
```

**Print the Line Where the Tarball Starts**

```
awk '/^##__PLNXSDK_FOLLOWS__/ { print NR + 1; exit 0; }' petalinux-v2018.2-final-installer.run
```

**Extract the Tarball from the Installer to the Current Directory**

```
tail -n +$(awk '/^##__PLNXSDK_FOLLOWS__/ { print NR + 1; exit 0; }' petalinux-v2018.2-final-installer.run) petalinux-v2018.2-final-installer.run | tar -xvJ
```

**Install PetaLinux Tools**

**Note**: this sequence assumes your executing from the directory of the extracted the built-in tarball

1\. Type:

```
touch petalinux_installation_log
export PLNXINSTALLLER=petalinux-v2018.2-final-installer.run
export PLNXINSTALLDIR=/opt/pkg/petalinux
export PLNXINSTALL_LOG=petalinux_installation_log
tools/common/petalinux/utils/petalinux-install
```

2\. Type **Control-C**

3\. PetaLinux will then install

**<u><span>References</span></u>**

-   **Awk One-Liners Explained, Part I: File Spacing, Numbering and Calculations** at \[[<u><span>link</span></u>](http://www.catonmat.net/blog/awk-one-liners-explained-part-one/)\]
    
-   man awk, awk --version is **GNU Awk 4.1.3, API: 1.1 (GNU MPFR 3.1.4, GNU MP 6.1.0)**
    
-   Answer to **awk + print lines from the first line until match word** on **StackExchange** at \[[<u><span>link</span></u>](https://unix.stackexchange.com/questions/170661/awk-print-lines-from-the-first-line-until-match-word)\]
    
-   **Awk** at \[[<u><span>link</span></u>](http://www.grymoire.com/Unix/Awk.html)\]
    
-   **How to Write AWK Commans and Scripts** at \[[<u><span>link</span></u>](https://www.lifewire.com/write-awk-commands-and-scripts-2200573)\]
    
-   Xilinx logo found via [<u><span>https://twitter.com/xilinxinc</span></u>](https://twitter.com/xilinxinc) at \[[<u><span>link</span></u>](https://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]