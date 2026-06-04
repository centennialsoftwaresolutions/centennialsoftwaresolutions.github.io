Tested on: Ubuntu 24.04.2:

```
lsb_release -a
```

Output:

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 24.04.2 LTS
Release:	24.04
Codename:	noble
```

Steps

List where `xfce4` will be installed from:

```
sudo apt update
apt policy xfce4
apt policy xfce4-goodies
```
Get it:
```
sudo apt update
sudo apt install xfce4
sudo apt install xfce4-goodies 
```
Select `lightdm` on the config screen terminal pop-up. 

Reboot:

```
sudo systemctl reboot 
```
At the login screen, switch to XFCE.

Get `xfce4-terminal` and switch to it from Gnome Terminal:

```
sudo apt update
sudo apt install xfce4-terminal
sudo update-alternatives --config x-terminal-emulator
```
Note: xfce4-terminal does come in with xfce4-goodies:

```
apt-cache rdepends xfce4-terminal
```

Output:

```
xfce4-terminal
Reverse Depends:
  task-xfce-desktop
  xubuntu-desktop-minimal
  xubuntu-desktop
  xfce4-goodies
```

Make sure we're using `X11`, not `Wayland`:

```
loginctl
loginctl show-session c2 -p Type
```
Install `xrdp`:
```
sudo apt update
sudo apt install xrdp
sudo adduser xrdp ssl-cert
echo "xfce4-session" > ~/.xsession
sudo systemctl restart xrdp
sudo systemctl enable xrdp
```
Disable suspend at the kernel:

```
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

Use `unmask` to re-enable. 

If you see in dmesg:

```
[13050.392304] i915 0000:00:02.0: [drm] *ERROR* Failed to probe lspcon
[13050.392308] i915 0000:00:02.0: [drm] *ERROR* LSPCON init failed on port D
```

Turn off DRM (Direct Rendering Manager) polling:

```
sudo vi /etc/default/grub
```

Use:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash drm_kms_helper.poll=0"
```

```
sudo update-grub
```

Reboot:

```
sudo systemctl reboot
```

Get the `IP` address of the computer for RDP connect:

```
ip a
```

