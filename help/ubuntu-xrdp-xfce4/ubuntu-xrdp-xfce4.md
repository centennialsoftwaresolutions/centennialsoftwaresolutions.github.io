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
5. Delete the GNOME portal and install the generic GTK/XFCE portals 

```
sudo apt remove xdg-desktop-portal-gnome -y
sudo apt install xdg-desktop-portal-gtk xdg-desktop-portal-xapp -y
```

6. Tell Ubuntu what our graphical environment is. Connect remote sessions directly to Ubuntu's native systemd so we can use snaps and GNOME terminal. Give the remote screen to the background service so terminal windows appear on our screen instead of the physical monitor. Start the lightweight desktop.

```
cat << 'EOF' > ~/.xsession
export XDG_SESSION_TYPE=x11 #
export XDG_CURRENT_DESKTOP=XFCE #
export XDG_RUNTIME_DIR=/run/user/$UID
export DBUS_SESSION_BUS_ADDRESS="unix:path=$XDG_RUNTIME_DIR/bus"
# Force background services (like gnome-terminal-server) to see remote screen
dbus-update-activation-environment --systemd DISPLAY
exec xfce4-session
EOF
```
6. Log off and log back on. Use a faster terminal.  

```
sudo apt install xfce4-terminal -y
sudo update-alternatives --set x-terminal-emulator /usr/bin/xfce4-terminal.wrapper
```

7. Get the IP of the Ubuntu computer to connect to from Windows.

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

