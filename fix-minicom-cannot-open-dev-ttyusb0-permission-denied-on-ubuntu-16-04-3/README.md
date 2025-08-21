# Fix minicom: cannot open /dev/ttyUSB0: Permission denied on Ubuntu 16.04.3

![ubuntu_logo_1](ubuntu_logo_1.png)

This post presents a solution to minicom: cannot open /dev/ttyUSB0: Permission denied that was verified on Ubuntu 16.04.3.

**<u><span>Symptom</span></u>**

When you type: **minicom** you see **minicom: cannot open /dev/ttyUSB0: Permission denied**

**<u><span>A Solution on Ubuntu 16.04.3</span></u>**

1\. Type **sudo adduser $USER dialout**

2\. Log out

3\. Log in

**<u><span>References</span></u>**

-   Ubuntu logo from \[[link](https://assets.ubuntu.com/v1/57a889f6-ubuntu-logo112.png)\]
    
-   <u><span>Serial port terminal &gt; Cannot open /dev/ttyS0: Permission denied</span></u> at \[[link](https://askubuntu.com/questions/210177/serial-port-terminal-cannot-open-dev-ttys0-permission-denied)\]