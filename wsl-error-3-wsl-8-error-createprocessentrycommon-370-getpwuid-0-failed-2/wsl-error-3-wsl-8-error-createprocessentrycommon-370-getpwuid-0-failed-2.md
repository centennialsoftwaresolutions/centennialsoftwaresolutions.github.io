# wsl error: <3>WSL (8) ERROR: CreateProcessEntryCommon:370: getpwuid(0) failed 2

![Tux_on_windows_logo](Tux_on_windows_logo.png)

This post shows a workaround to get WSL working again if you see an effort that starts with "Processing fstab with mount -a failed."

## Steps

After running:

```
wsl
```

If you see:

```
Processing fstab with mount -a failed.

<3>WSL (8) ERROR: CreateProcessEntryCommon:370: getpwuid(0) failed 2
<3>WSL (8) ERROR: CreateProcessEntryCommon:374: getpwuid(0) failed 2
<3>WSL (8) ERROR: CreateProcessEntryCommon:577: execvpe /bin/sh failed 2
<3>WSL (8) ERROR: CreateProcessEntryCommon:586: Create process not expected to return
```

Run:

```
wsl --list
```

If you see **docker-desktop-data** set as the default:

```
Windows Subsystem for Linux Distributions:
docker-desktop-data (Default)
docker-desktop
Debian
```

Run:

```
wsl -s Debian
```

You should see the following:

```
The operation completed successfully.
```

Now you can run:

```
wsl
```

And wsl should run:

```
username@LAPTOP-3MCNKKJO:/mnt/c/Users/Zach Pfeffer$
```

## Computer Configuration

```
wsl --status
# Default Distribution: docker-desktop-data
# Default Version: 2

wsl -v
# WSL version: 1.2.5.0
# Kernel version: 5.15.90.1
# WSLg version: 1.0.51
# MSRDC version: 1.2.3770
# Direct3D version: 1.608.2-61064218
# DXCore version: 10.0.25131.1002-220531-1700.rs-onecore-base2-hyp
# Windows version: 10.0.19045.2846
```

## References

bash fails on WSL2: filesystem mounting error [#5923](https://www.centennialsoftwaresolutions.com/blog/hashtags/5923)

https://github.com/microsoft/WSL/issues/5923 

docker-desktop-data isn't a Linux distro (?) so it should not be settable as a default distro by wsl2 [#8727](https://www.centennialsoftwaresolutions.com/blog/hashtags/8727)

https://github.com/microsoft/WSL/issues/8727 

Windows 10 Logo

[https://commons.wikimedia.org/wiki/File:Windows_logo_-_2012_%28dark_blue%29.svg](https://commons.wikimedia.org/wiki/File:Windows_logo_-_2012_(dark_blue).svg) 

Tux Logo

Tux (mascot). (2023, April 10). In *Wikipedia*. https://en.wikipedia.org/wiki/Tux_(mascot) 

[https://en.wikipedia.org/wiki/Tux_%28mascot%29#/media/File:Tux.png](https://en.wikipedia.org/wiki/Tux_(mascot)#/media/File:Tux.png) 