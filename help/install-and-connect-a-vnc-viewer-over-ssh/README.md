# Install and Connect to a VNC Viewer over SSH

![tight_vnc_logo_1](tight_vnc_logo_1.png)

This post shows how to install and setup a VNC connection over an SSH tunnel.

**1.** Log in to the server over SSH. You can set up something like this in .ssh/config:

```
Host *
  ServerAliveInterval 60

Host snoopy
  HostName xxx.xxx.xxx.xxx
  User plc2
  IdentityFile ~/.ssh/keys/key1/openssh.key1.priv
```

**2.** Install tightvncserver

```
sudo apt-get install vncserver
sudo apt install xfce4 xfce4-goodies tightvncserver
```

**3.** Start the vncserver:

```
vncserver -geometry 1280x1024
```

... and set the password

```
vncpasswd
```

**4.** Note the display:

It may be:

name:1

or

name:2

etc...

**5\.** Set up ssh port forwarding.

If you have a display on name:1 then you'll use 5901, if you have a display on name:2 you'll use port 5902

A general note from [link:](http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html)

```
ssh -L x:localhost:y snoopy
```

Means "Start an SSH connection to snoopy, and also listen on port x on my machine, and forward any connections there to port y on snoopy."

Specifically if you're connecting to a display name:1 on snoopy you'll use:

```
ssh -L 5901:localhost:5901 snoopy
```

```
ssh -L 5901:localhost:5901 snoopy
```

If you're connecting to a name:2 you'll use:

**6.** Install vncviewer on the computer you're connecting to the server

```
sudo apt-get update
sudo apt-get install vncviewer
```

**7.** Now call

```
vncviewer
```

And specify

```
localhost:5901
```

**References**

-   Tightvnc logo is from **link**.