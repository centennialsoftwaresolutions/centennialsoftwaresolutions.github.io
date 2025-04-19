# Set up LXC for Vitis, Vivado, and Petalinux development

## **Introduction**

Linux Containers (LXC) is a containerization system like Docker. If you use Linux as the primary/native OS on your computer, LXC is a great way to run Ubuntu containers to use with Xilinx tools.

### **LXC/containers vs. virtual machines**

Compared to a virtual machine, containers are much more lightweight.

A VM requires you to preemptively split your resources (CPU, memory, disk) between the host OS and the VM. If you allocate more resources to the VM, they're always taken away from the host, even if the VM is idling or not fully utilizing them. Builds in a VM will always be slower since the VM can't utilize the full compute power of your hardware. Additionally, graphical performance & responsiveness in VMs is usually poor. Window management is generally painful since everything running in the VM is bounded into the VM window, and the host treats the VM display as one window. Shared clipboard (copy/paste) can work but is often finicky.

LXC containers share the host OS's kernel. Processes running inside the container can utilize all the CPU & RAM on your computer as if they were running natively on your host kernel. And when the container is idle, it doesn't use any extra resources from the host. Disk space is also dynamically shared; there's no overhead like with a VM. Additionally, graphical performance is snappy and responsive with X11 sharing into the container. Window management, clipboard sharing, and even audio integrate perfectly, just as if you were running everything natively without a container.

### **LXC vs. Docker**

Docker is another containerization tool. Compared to LXC, Docker is more focused on creating _reproducible_ and disposable (often short-lived) containers. LXC treats containers more like a VM - each container is an individual "machine" which you can configure as you need. It does support some automation, but not to the extent that Docker does. LXC containers are often more permanent; they persist through reboots just like a VM or your native OS does. That said, Docker is also a viable option - the feature sets of both tools do have quite a bit of overlap.

## **Technical overview**

"LXC" is split into two parts: LXC, the low-level library, and LXD, the command line interface. The LXD executable binary is named "lxc" - so you type "lxc <command>" in your terminal, but that's actually running LXD, which uses LXC under the hood.

LXC supports privileged and unprivileged containers. We'll use unprivileged containers, which map the UIDs/GIDs of processes in the container to different (high-numbered) UIDs/GIDs on the host. A privileged container does not do that remapping, which means that UID 0 (root) on the container is also root on the host.

An LXC Ubuntu container can install & run Petalinux out of the box because Petalinux is a command line tool. Adding display forwarding (for Vitis & Vivado) requires changing the container configuration file.

The Xilinx toolkits take up a lot of disk space. Instead of installing the tools into the container, it's better to install them onto your host (native) filesystem and share that folder read-only into the container. We'll also set up another shared folder as a scratch/work directory which is R/W accessible from both the host and the container.

## **Installation**

The LXC/LXD installation process may vary based on which Linux distribution you're running on the host.

First, we'll need to create the subuid and subgid files and reboot. These files set up UID/GID mapping for unprivileged containers - the "1000000" means that UID 0 in the container will be UID 1000000 in the host, UID 1000 in the container will be UID 1001000 in the host, etc.

```
echo root:1000000:1000000000 | sudo tee /etc/subuid
echo root:1000000:1000000000 | sudo tee /etc/subgid
sudo systemctl reboot
```

After the reboot, you can install lxd and enable it - shown here for Arch Linux:

```
sudo pamcan -S lxd
   (this also pulls in "lxc" and "lxcfs" as dependencies)
sudo systemctl enable --now lxd.socket
```

As the final step, add yourself to the "lxd" group to allow using the "lxc" command without sudo:

```
sudo usermod -a -G lxd ${USER}
```

Log out and log back in to apply the group change.

Note: [<u><span>As the Arch Wiki warns</span></u>](https://wiki.archlinux.org/title/LXD#Accessing_LXD_as_an_unprivileged_user), technically anyone added to the lxd group is root equivalent.

_For reference, here are the complete steps to purge the LXC/LXD config and do a "clean install" on Arch Linux._

```
sudo systemctl disable --now lxd.socket lxd.service
sudo systemctl disable --now lxdfs.service
sudo pacman -Rs lxd lxc lxcfs

sudo rm /etc/subuid /etc/subgid

echo root:1000000:1000000000 | sudo tee /etc/subuid
echo root:1000000:1000000000 | sudo tee /etc/subgid

sudo systemctl reboot

sudo rm -f /etc/lxc/default.conf /etc/default/lxc
sudo rm -rf ~/.config/lxc /var/lib/lxd /var/log/lxd /var/cache/lxd /var/lib/lxcfs

sudo pacman -S lxd
sudo systemctl enable --now lxd.socket
```

## **Initial LXD setup**

Run "lxd init" as root:

```
$ sudo su
# lxd init
```

We'll use the defaults for all but two options:

-   Use "dir" as the storage backend, which puts the container filesystems directly on your host OS's filesystem (at /var/lib/lxd/containers/<containerName>/rootfs)
    
-   If you don't have IPv6 connectivity to the internet, disable IPv6 for the container by entering "none" when prompted for an IPv6 address. Otherwise, you may run into networking issues.
    

The final output of lxd init should look like this:

```
Would you like to use LXD clustering? (yes/no) [default=no]:
Do you want to configure a new storage pool? (yes/no) [default=yes]:
Name of the new storage pool [default=default]:
Name of the storage backend to use (dir, lvm, btrfs) [default=btrfs]: dir
Would you like to connect to a MAAS server? (yes/no) [default=no]:
Would you like to create a new local network bridge? (yes/no) [default=yes]:
What should the new bridge be called? [default=lxdbr0]:
What IPv4 address should be used? (CIDR subnet notation, “auto” or “none”) [default=auto]:
What IPv6 address should be used? (CIDR subnet notation, “auto” or “none”) [default=auto]: none
Would you like the LXD server to be available over the network? (yes/no) [default=no]:
Would you like stale cached images to be updated automatically? (yes/no) [default=yes]:
Would you like a YAML "lxd init" preseed to be printed? (yes/no) [default=no]:
```

lxd init will create an "lxdbr0" interface in your host OS's network configuration. That bridge shares internet access into the containers.

## **Create a container**

You should now be able to launch an Ubuntu container and run commands in it:

```
$ lxc launch ubuntu:20.04
Creating the instance
Instance name is: delicate-ocelot
Starting delicate-ocelot

=> If the container fails to start, see the troubleshooting section below

$ lxc exec delicate-ocelot bash

root@delicate-ocelot:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.6 LTS"

root@delicate-ocelot:~# su ubuntu

ubuntu@delicate-ocelot:/root$ cd

ubuntu@delicate-ocelot:~$ id -u
1000

ubuntu@delicate-ocelot:~$ id -g
1000
```

Meanwhile, in the host OS:

```
$ ps aux | grep bash
1000000   530550  0.0  0.0   8968  3968 pts/1    Ss   14:41   0:00 bash
1001000   531033  0.0  0.0  10004  4736 pts/1    S+   14:41   0:00 bash
```

Processes from the container run as normal processes in the host kernel, but with high UIDs (1000000 for root's shell and 1001000 for ubuntu's shell).

Once you exit the shell in the container, it'll continue to run in the background - but it will use ~0 resources from the host while idling.

```
$ lxc list 
+-----------------+---------+-----------------------+-----------+-----------+ 
|      NAME       |  STATE  |         IPV4          |   TYPE    | SNAPSHOTS | 
+-----------------+---------+-----------------------+-----------+-----------+ 
| delicate-ocelot | RUNNING | 10.209.202.39 (eth0)  | CONTAINER | 0         | 
+-----------------+---------+-----------------------+-----------+-----------+
```

Since this will be our permanent Ubuntu 20.04 container used for Xilinx tools, let's give it a better name - like "petalinux20." Either rename it or delete the container and create a new one with a name specified.

```
$ lxc stop delicate-ocelot
$ lxc rename delicate-ocelot xilinx2004
$ lxc start xilinx2004

OR

$ lxc stop delicate-ocelot
$ lxc delete delicate-ocelot
$ lxc launch ubuntu:20.04 xilinx2004
```

Next, we'll configure this container for Xilinx development.

### **Troubleshooting: Container fails to start**

The container fails to start, and LXC tells you to look at the log. The first error line in the log is like:

```
No such file or directory - Failed to create cgroup at_mnt 24()
```

This is an issue with migration to cgroupv2. On the host system, modify the bootloader configuration to add this to your host kernel cmdline:

```
systemd.unified_cgroup_hierarchy=false
```

Reboot and try again. The container which failed to start will still exist, so you can attempt to "start" that container instead of running "launch" again (which will create a new container):

```
lxc start containerName
```

### **Troubleshooting: Container has no LAN or Internet access**

You have Docker installed on your computer. From inside the container, you can't ping anything on your LAN or the internet.

This is because Docker changes the iptables configuration to block forwarded packets by default. See https://linuxcontainers.org/lxd/docs/master/howto/network_bridge_firewalld/#prevent-connectivity-issues-with-lxd-and-docker for more details.

The fix:

```
sudo iptables -I DOCKER-USER -i lxdbr0 -o INTERFACE -j ACCEPT
sudo iptables -I DOCKER-USER -o lxdbr0 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
```

In the first line, change INTERFACE with the network interface your computer uses to connect to the LAN / Internet - e.g., enp5s0, wlp6s0. This fix will be effective immediately; a reboot isn't required.

## **Configuration part 1: Shared folders**

First, we'll add two shared folders into the container.

While the Xilinx tools (Vitis to a lesser extent, Vivado, and especially Petalinux) can be finicky about running on non-officially-supported OSs, my experience has been that the installers will run on pretty much any Linux system. So we have two options here:

-   Install all the Xilinx tools from the host OS, into /tools/Xilinx. Then, share /tools/Xilinx as a read-only folder into your container(s).
    
-   Make /tools/Xilinx a read-write shared folder into your container. Run the Xilinx installers inside the container. At this point, the Xilinx programs are installed into /tools/Xilinx (which is shared into the container but really exists on your host filesystem). You can reconfigure the share to be read-only at this point.
    

Refer to our installation guides for [<u><span>Vitis/Vivado</span></u>](https://www.css-techhelp.com/post/installing-vitis-vivado-in-ubuntu) and [<u><span>Petalinux</span></u>](https://www.css-techhelp.com/post/installing-petalinux-2023-1-in-ubuntu). The steps to install Vitis/Vivado/Petalinux in an Ubuntu container with a shared folder are the exact same as the steps to install on native Ubuntu - so you can follow those instructions with no modification required. If you choose to install inside the container, finish all of these LXC configuration steps first - you'll need to set up the container's GUI before you can run the Xilinx Unified Installer.

Aside from /tools/Xilinx, we'll also share a "scratch"/workdir folder into the container.

Open up the container's configuration file:

```
lxc config edit xilinx2004
```

This will open a YAML file in your $EDITOR. LXD will verify the configuration file syntax & validity when you exit - if you mess something up, it'll print an error and let you go back to the editor to fix the config file.

About halfway down the configuration, you'll see a line like this:

```
devices: {}
```

We'll start by adding two shared folders here. First, remove the "{}". Change the devices entry to look like this (replacing YOURUSER with your actual user):

```
devices:
  sf_work:
    path: /work
    source: /home/YOURUSER/work
    type: disk
    shift: "true"
  sf_xilinx:
    path: /tools/Xilinx
    source: /tools/Xilinx
    type: disk
```

Exit your editor; LXC should exit without printing anything. The changes are applied immediately; you don't need to restart the container.

sf\_work and sf\_xilinx are the shared folder devices' names - it doesn't matter what you name them. "path" is the mount location in the container, and "source" is the location on your host machine's filesystem. The sf\_work device will mount "/home/YOURUSER/work" from the host machine into "/work" in the container.

Finally, shift: "true" makes LXC automatically shift UIDs when accessing the filesystem in the container. The root & ubuntu users in the container have UID 1000000 and 1001000, so they have no permission to write to these files on the host filesystem. Since the xilinx share doesn't have shift: "true," you won't be able to write to /tools/Xilinx from inside the container. But since the work shared folder does have shift: "true," when the "ubuntu" user in the container tries to write to /work in the container, LXC will translate that to UID 1000 on the host so that permissions will allow writing.

Note: The shift filesystem will only work if your user's UID/GID on the host are 1000/1000 (because it blindly translates the container's "ubuntu" user uid/gid of 1000/1000 onto the host). Additional configuration may be required if your uid on the host is not 1000.

Let's verify that this worked:

```
$ lxc exec xilinx2004 bash

root@xilinx2004:~# ls /tools/Xilinx/
DocNav  Model_Composer  PetaLinux  SharedData  Vitis  Vitis_HLS  Vivado  xic

root@xilinx2004:~# ls -ld /tools/Xilinx/
drwxr-xr-x 11 nobody nogroup 4096 May 23 18:48 /tools/Xilinx/

root@xilinx2004:~# touch /tools/Xilinx/foo
touch: cannot touch '/tools/Xilinx/foo': Permission denied

root@xilinx2004:~# su ubuntu

ubuntu@xilinx2004:/root$ ls /work
arm  css  ubuntu-isos  xilinx
=> these are the files I have in ~/work on the host

ubuntu@petalinux20:/root$ touch /work/foo
=> the new "foo" file is also visible in the host filesystem

ubuntu@petalinux20:/root$ ls -ld /work
drwxr-xr-x 7 ubuntu ubuntu 4096 May 23 23:40 /work
```

That example assumes you already have Xilinx tools installed in /tools/Xilinx on the host. If you plan on installing Xilinx tools from within the container, add shift: "true" to the xilinx shared device configuration. Then follow the steps to install [<u><span>Vitis/Vivado</span></u>](https://www.css-techhelp.com/post/installing-vitis-vivado-in-ubuntu) or [<u><span>Petalinux</span></u>](https://www.css-techhelp.com/post/installing-petalinux-2023-1-in-ubuntu) in the container.

## **Configuration part 2: Share X11 into the container**

If you only need to use Petalinux, the container is already ready to use. If you want to use Vitis or Vivado, you'll need to set up GUI sharing.

These steps will work whether you're using X11 or Wayland on the host (if you're using Wayland, this will share the XWayland session into the container). _It's also possible to directly share a Wayland session into the container, but I couldn't get that working with Xilinx tools v2023.1 in Ubuntu 20.04._

First, find the $DISPLAY number on the host:

```
echo $DISPLAY
```

If you're using native X11 on the host, this will probably be ":0"

If you're using Wayland on the host, this will probably be ":1" (for the XWayland session)

Next, stop the container and edit the config file to add two devices: a GPU and the X11 socket:

```
lxc stop xilinx2004
lxc config edit xilinx2004
```

```
devices:
  sf_work:
    ...
  sf_xilinx:
    ...
  mygpu:
    type: gpu
  Xsocket:
    bind:  container
    type: proxy
    connect: unix:@/tmp/.X11-unix/X?
    listen: unix:@/tmp/.X11-unix/X0
    security.uid: "1000"
    security.gid: "1000"
```

The first device, named mygpu (you can name it whatever you want), shares your GPU into the container.

The second device, named Xsocket (you can name it whatever you want), shares the X11 (or XWayland) socket from the host into the container.

One or two changes are required:

-   In the "connect" part of Xsocket, change "X**?**" to "X0" or "X1" based on the $DISPLAY number that was checked earlier.
    
-   If your uid/gid on the host are not 1000/1000, change security.uid and security.gid to match.
    

You need to make one other change while in the configuration: add "environment.DISPLAY: :0" into the "config" section, like:

```
config:
  environment.DISPLAY: :0
  ... (preexisting config members)
```

Save the configuration file and restart the container:

```
lxc start xilinx2004
```

Verify that the display sharing works with glxgears or xclock/xeyes/etc.:

```
lxc exec xilinx2004 bash

root@xilinx2004:~# xeyes
root@xilinx2004:~# xclock
root@xilinx2004:~# glxgears
```

The xeyes/xclock/glxgears windows should open up normally on your host OS, just like if you were running them without using a container!

As a final test, launch Vitis or Vivado:

```
lxc exec xilinx2004 bash

root@xilinx2004:~# su ubuntu

ubuntu@xilinx2004:/root$ /tools/Xilinx/Vitis/2023.1/
```

Vitis launches normally. The Vitis windows integrate into the taskbar and alt-tab menu on your host. Clipboard copy/paste works.

## **Bonus: Configuration part 3: Sound**

While not necessary to use Vitis/Vivado, we can also share PulseAudio into the container to get sound - so any beeps or dings emitted by Vitis/Vivado in the container will play through the speakers on your host.

_This also works if you're running PipeWire on the host, no changes are required._

This is implemented like X11: add a line to the "config" section of the configuration file, and add a socket device to the "device" section.

```
lxc stop xilinx2004
lxc config edit xilinx2004
```

```
config:
  environment.PULSE_SERVER: unix:/pulse
  ... (preexisting config)
devices:
  PAsocket:
    bind: container
    connect: unix:/run/user/1000/pulse/native
    gid: "1000"
    listen: unix:/pulse
    mode: "0777"
    security.gid: "1000"
    security.uid: "1000"
    type: proxy
    uid: "1000"
  ... (preexisting devices)
```

Adjust "security.uid," "security.gid," and the UID in the "connect" path to match your uid/gid on the host. The "uid" and "gid" properties are for the uid/gid of the ubuntu user in the container.

```
lxc start xilinx2004
lxc exec xilinx2004 bash

root@xilinx2004:~# sudo apt install pulseaudio pavucontrol

root@xilinx2004:~# pacat </dev/random
=> this will play *LOUD* static on your host's speakers
```

You can use the "pavucontrol" graphical utility to adjust audio configuration (this works in the container and the host - the container connects directly to the hosts's PulseAudio server so everything integrates natively, as if there wasn't even a container in play).

## **Reference: Useful lxc commands**

-   lxc list
    
    -   List all containers which exist on this system
    
-   lxc {stop,start,restart} <containerName>
    
    -   Manage container run state
    
-   lxc delete <containerName>
    
    -   Delete a stopped container
    
-   lxc exec <containerName> <command>
    
    -   Run command in container
    
-   lxc config edit <containerName>
    
    -   Open the container's config in your $EDITOR. It'll be checked for syntax & validity when you exit the editor. Some config changes require you to stop the container first.
        

<u><span>References</span></u>

-   LXC logo image from [<u><span>https://linuxcontainers.org/</span></u>](https://linuxcontainers.org/)
    
-   [<u><span>ArchWiki - Linux Containers</span></u>](https://wiki.archlinux.org/title/Linux_Containers)
    
-   [<u><span>ArchWiki - LXD</span></u>](https://wiki.archlinux.org/title/LXD)
    
-   [<u><span>blog.simos.info - Running X11 software in LXD containers</span></u>](https://blog.simos.info/running-x11-software-in-lxd-containers/)