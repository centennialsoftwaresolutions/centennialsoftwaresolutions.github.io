# Configure Linux for Non-ARP UDP Communication with an Embedded Target

![tux_transparent](tux_transparent.png)

This post answers, "How do I configure Linux Linux for Non-ARP UDP Communication with an Embedded Target?"

**Introduction**

Learn to configure a Linux system to connect with an embedded target that lacks ARP over UDP support. This guide simplifies the process for seamless communication.

**Prerequisites**

-   Linux system access with 'sudo' privileges.
    

**Configuration Overview**

-   Target IP: 172.16.30.1, MAC: 5e:ea:50:05:1a:b5
    
-   Host IP: 172.16.30.2, MAC: 5e:e0:06:50:05:ee
    

**Quick Setup Steps**

1.  **Hardware Connection** Connect the Linux host and embedded target using an Ethernet cable.
    
2.  **Power On** Activate the embedded target.
    
3.  **Identify \[interface\]** Open terminal, run ifconfig, and note the Ethernet interface (e.g., ens33).
    
4.  **Configure MAC Address**  
    
    -   Disable interface: sudo ifconfig **\[interface\]** down
        
    -   Set MAC address: sudo ifconfig **\[interface\]** hw ether 5e:e0:06:50:05:ee
        
    -   Enable interface: sudo ifconfig **\[interface\]** up
        

1.  **Assign IP Address:** Assign IP via terminal: sudo ifconfig **\[interface\]** 172.16.30.2 netmask 255.255.255.0
    
2.  **Update ARP Table:** Add static ARP entry: sudo arp -i **\[interface\]** -s 172.16.30.1 5e:ea:50:05:1a:b5
    
3.  **Verify Configuration** Check ARP mapping with arp -a.
    

**Conclusion** With these steps, your Linux system will be ready to interface with an embedded target that doesn't support ARP over UDP, ensuring smooth communication and operation.

**Additional Info On ARP**

The ARP table facilitates the translation between IP addresses and MAC addresses for local network communication. The table is accessed whenever a device needs to establish a direct communication link with another device on the same local network.

**References**

-   Tux from \[[<u><span>link</span></u>](https://www.iconfinder.com/icons/367633/linux_tux_icon#size=128)\]