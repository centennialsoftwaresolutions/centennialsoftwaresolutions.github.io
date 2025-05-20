# Connect the Xilinx SDK to the TCF Agent Running on a Target Running a PetaLinux BSP

![xilinx_logo](xilinx_logo.png)

This post shows how to connect the Xilinx SDK to the TCF Agent running on a target running a PetaLinux BSP.

**<u><span>Assumptions</span></u>**

These steps assume: minicom has been installed and set up, Vivado has been installed, the Xilinx SDK has been installed, a PetaLinux BSP has been built and the JTAG, serial and Ethernet ports have been connected between the target and the host. In addition, in this case, Linux was running in a VM and the Ethernet cable from the target was connected to a USB connector with an Ethernet port built-in.

Click https://www.centennialsoftwaresolutions.com/post/2018-2-2-xilinx-linux-dev-for-the-zc706-on-win7-sp1-via-virtualbox-6-0-10 for help satisfying these assumptions.

**<u><span>Steps</span></u>**

Step [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1): Open a new window on the host and type **minicom**

Step [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2): Open a new window on the host and type:

**mkdir ~/plxprjs**

**cd ~/plxprjs/**

**source /opt/pkg/petalinux/2019.1/settings.sh**

**cd ~/plxprjs/xilinx-zc706-2019.1/**

**petalinux-boot --jtag --fpga --u-boot --hw_server-url TCP:localhost:3121**

...and let the target boot

Step [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3): Log in to the target using **root** for user and **root** for password

Step [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4): Type on the target: **ifconfig eth0 192.168.2.2**

Step [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5): In the VM enable the Ethernet USB device 

Step [#6](https://www.centennialsoftwaresolutions.com/blog/hashtags/6): Type on the host to get interface name: **ifconfig**

Step [#7](https://www.centennialsoftwaresolutions.com/blog/hashtags/7): Type on the host: **sudo ifconfig enx000ec6df71ef 192.168.2.3** 

Step [#8](https://www.centennialsoftwaresolutions.com/blog/hashtags/8): From the target test the connection to the host: **ping 192.168.2.3**

Step [#9](https://www.centennialsoftwaresolutions.com/blog/hashtags/9): From the host test the connection to the target: **ping 192.168.2.2** 

If you can’t ping try:

**sudo ifconfig enx000ec6df71ef down**

**sudo ifconfig enx000ec6df71ef up**

Step [#10](https://www.centennialsoftwaresolutions.com/blog/hashtags/10): In the SDK create a helloworld app using Processor Type **ps7_cortex_a9** and set the **OS Platform** to **linux**

Step [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11): In the SDK, expand **Linux TCF Agent** in the lower-left corner **Target Connections** window

Step [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12): In the SDK, double click **Linux Agent [default]** and set the “**Host**” (which is actually the target) to **192.168.2.2** and leave **Port** set to **1534**. Click **Test Connection** and make sure the connection works. Click **OK** to close.

Step [#13](https://www.centennialsoftwaresolutions.com/blog/hashtags/13): Right-click on hello and click **Debug As > Launch on Hardware (System Debugger)** and step through your code. You’ll see the output in the **minicom** window.

**Reference**

Xilinx logo from https://twitter.com/xilinxinc 