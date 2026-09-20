# Setup xfce and xrdp on NVIDIA AGX Orin jetson_39.2.1

## 1. Install xfce4

```
sudo apt update && sudo apt install xfce4 xfce4-goodies -y # select lightdm
```

## 2. System > Users disable auto login

## 3. Power off

## 4. Power on

## 5. See the login screen come up. 

## 6. Click the Ubuntu circle and select xfce.

## 7. Login 

You should see a background with squiggles and a mouse.

## 8. Set up xrdp

```
sudo apt update
sudo apt install xrdp -y
sudo systemctl status xrdp # Should see active
```

output:

```
● xrdp.service - xrdp daemon
     Loaded: loaded (/usr/lib/systemd/system/xrdp.service; enabled; preset: enabled)
     Active: active (running) since Sun 2026-09-20 15:59:38 UTC; 3min 56s ago
       Docs: man:xrdp(8)
             man:xrdp.ini(5)
    Process: 2521 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)
    Process: 2530 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=0/SUCCESS)
   Main PID: 2534 (xrdp)
      Tasks: 1 (limit: 74773)
     Memory: 1.2M (peak: 2.1M)
        CPU: 28ms
     CGroup: /system.slice/xrdp.service
             └─2534 /usr/sbin/xrdp

Sep 20 15:59:36 tegra-ubuntu systemd[1]: Starting xrdp.service - xrdp daemon...
Sep 20 15:59:36 tegra-ubuntu xrdp[2530]: [INFO ] address [0.0.0.0] port [3389] mode 1
Sep 20 15:59:37 tegra-ubuntu xrdp[2530]: [INFO ] listening to port 3389 on 0.0.0.0
Sep 20 15:59:37 tegra-ubuntu xrdp[2530]: [INFO ] xrdp_listen_pp done
Sep 20 15:59:37 tegra-ubuntu systemd[1]: xrdp.service: Can't open PID file /run/xrdp/xrdp.pid (yet?) after start: No such file or directory
Sep 20 15:59:38 tegra-ubuntu systemd[1]: Started xrdp.service - xrdp daemon.
Sep 20 15:59:39 tegra-ubuntu xrdp[2534]: [INFO ] starting xrdp with pid 2534
Sep 20 15:59:39 tegra-ubuntu xrdp[2534]: [INFO ] address [0.0.0.0] port [3389] mode 1
Sep 20 15:59:39 tegra-ubuntu xrdp[2534]: [INFO ] listening to port 3389 on 0.0.0.0
Sep 20 15:59:39 tegra-ubuntu xrdp[2534]: [INFO ] xrdp_listen_pp done

```

## 9. Add xrdp to ssl-cert group

```
sudo adduser xrdp ssl-cert
sudo systemctl restart xrdp
```

output:

```
orin@tegra-ubuntu:~$ sudo adduser xrdp ssl-cert
sudo systemctl restart xrdp
info: Adding user `xrdp' to group `ssl-cert' ...
```

## 10. Install the firewall

```
sudo apt install ufw
sudo ufw allow 3389/tcp
```

output:

```
Rules updated
Rules updated (v6)
```

## 11. Install xfce

```
sudo apt install xfce4 xfce4-goodies -y # Duplicate 
sudo apt install dbus-x11 -y
```

## 12. Remove GNOME

```
sudo apt remove xdg-desktop-portal-gnome -y
sudo apt install xdg-desktop-portal-gtk xdg-desktop-portal-xapp -y
```

```
sudo vi /etc/xrdp/startwm.sh
```

Use:

```
#!/bin/sh
unset DBUS_SESSION_BUS_ADDRESS
unset XDG_RUNTIME_DIR
exec dbus-launch --exit-with-session xfce4-session
```

```
rm -f ~/.xsession ~/.Xauthority ~/.vnc/xstartup
```


```
sudo systemctl restart xrdp
```

## 13. Reboot again

```
sudo systemctl reboot
```

output:

```
Broadcast message from root@tegra-ubuntu on pts/1 (Sun 2026-09-20 16:09:41 UTC):

The system will reboot now!

```

## 14. Login via USB

```
demo-user@demo:~/Downloads/Linux_for_Tegra$ 

ssh -t orin@192.168.55.1 

```

output:

```
orin@192.168.55.1's password: 
Welcome to Ubuntu 24.04.4 LTS (GNU/Linux 6.8.12-1021-tegra aarch64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

Expanded Security Maintenance for Applications is not enabled.

311 updates can be applied immediately.
256 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

34 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm

Last login: Sun Sep 20 16:11:36 2026 from 192.168.55.100

```

## 15. Get IP for VNC

```
ifconfig # Likely 192.168.137.146
```

output:

```
orin@tegra-ubuntu:~$ ifconfig
end0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.137.146  netmask 255.255.255.0  broadcast 192.168.137.255
        inet6 fe80::c770:25e5:6dd:abcc  prefixlen 64  scopeid 0x20<link>
        ether 4c:bb:47:a4:0d:25  txqueuelen 1000  (Ethernet)
        RX packets 23  bytes 6241 (6.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 61  bytes 7003 (7.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

l4tbr0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.55.1  netmask 255.255.255.0  broadcast 0.0.0.0
        inet6 fe80::341d:6bff:fea5:fbd5  prefixlen 64  scopeid 0x20<link>
        inet6 fe80::1  prefixlen 64  scopeid 0x20<link>
        ether 36:1d:6b:a5:fb:d5  txqueuelen 1000  (Ethernet)
        RX packets 148  bytes 17992 (17.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 195  bytes 27907 (27.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 55  bytes 7597 (7.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 55  bytes 7597 (7.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

usb0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::38af:79ff:fe69:4919  prefixlen 64  scopeid 0x20<link>
        ether 3a:af:79:69:49:19  txqueuelen 1000  (Ethernet)
        RX packets 161  bytes 19528 (19.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 218  bytes 40904 (40.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlP1p1s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 50:2e:91:95:8d:87  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

## 16. Set up RDP using 192.168.137.146 and orin
