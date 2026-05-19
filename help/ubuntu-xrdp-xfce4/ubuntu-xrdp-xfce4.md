# RDP Connect Windows to Ubuntu

Connect to Ubuntu 24.04 from Windows using a custom resolution unsupported by the Ubuntu monitor. This is not supported by the built-in remote connection.

# Hardware

Windows is sharing an internet connection with the Ubuntu computer it's connected to.  Specifically, Windows is acting like a router, sharing an Ethernet port connected to a Netgear ProSafe 24 Port Gigabit Switch JGS524 v2, aka a multi-port network splitter. The switch is connected to an Ethernet port on the Ubuntu computer.   

# Install and Configure

1. Refresh Ubuntu's "software menu," install the remote desktop program `xrdp,` and make sure it starts.

```
sudo apt update
sudo apt install xrdp -y
sudo systemctl status xrdp # Should see active
```
2. Grant `xrdp` permission to read security certificates, allowing `xrdp` to encrypt your remote connection so no one can spy on your screen or keystrokes. Turn xrdp off and back on so it'll recognize the new security permissions.

```
sudo adduser xrdp ssl-cert
sudo systemctl restart xrdp
```
3. Open the networking "door" 3389 and allow the TCP communication method xrdp uses to communicate.

```
sudo ufw allow 3389/tcp
```
4. Install the core XFCE lightweight graphical desktop environment, `xfce4`, and additional tools for that desktop (such as taskbar widgets, a system monitor, a screenshot tool, and volume controls). Also, install the background communication system that the remote desktop program relies on to pass messages between different graphical apps, such as menus, the taskbar, and clickable icons. 

```
sudo apt install xfce4 xfce4-goodies -y
sudo apt install dbus-x11 -y
```
5. Bypass Ubuntu's default desktop when I log in remotely. Instead, start the background communication system, `dbus-launch`,  make sure `dbus-launch` closes when I leave the session, and use it to load the lightweight desktop, `xfce4`. Then turn the remote desktop program off and immediately back on so `xrdp` reads .xsession when the connection loads into XFCE.
```
echo "exec dbus-launch --exit-with-session xfce4-session" > ~/.xsession
sudo systemctl restart xrdp
```
6. Get the IP of the Ubuntu computer to connect to from Windows.
```
ip a # Get the IP
```
7. On Windows, run:
```
mstsc.exe # aka Remote Desktop Connection
```
8. Configure with the GUI ands connect.

# Versions Tested

## Ubuntu

```
demo@demo:~/Desktop$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 24.04.2 LTS
Release:	24.04
Codename:	noble
```

## xrdp

```
demo@demo:~/Desktop$ apt policy xrdp
xrdp:
  Installed: 0.9.24-4
  Candidate: 0.9.24-4
  Version table:
 *** 0.9.24-4 500
        500 http://archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status
```

## dbus-x11

```
demo@demo:~/Desktop$ apt policy dbus-x11
dbus-x11:
  Installed: 1.14.10-4ubuntu4.1
  Candidate: 1.14.10-4ubuntu4.1
  Version table:
 *** 1.14.10-4ubuntu4.1 500
        500 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.14.10-4ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
```

## xfce4

```
demo@demo:~/Desktop$ apt policy xfce4
xfce4:
  Installed: 4.18
  Candidate: 4.18
  Version table:
 *** 4.18 500
        500 http://archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status
```

