# SSH Directly to a Machine You'd Normally Need to SSH Into a Server to Get To

![open_ssh_logo](open_ssh_logo.gif)

This post lists the steps needed to connect to an ssh server **beyond** an ssh server you have to connect to, to to get to it from a Linux host using OpenSSH.

**Note**

**remote.server.com** is the server you ssh into to ssh into the other server

**sshbeyondremote.server.com** is the server you ssh into from remote.server.com

Replace these names with the names you use when you apply these steps.

**Steps**

1\. ssh into **remote.server.com** from **your machine**

2\. Edit ~/.ssh/authorized\_keys and add the public part of **~/.ssh/keys/key1/openssh.keyforremote.priv**

3\. ssh into **sshbeyondremote.server.com** from **remote.server.com**

4\. Edit ~/.ssh/authorized\_keys and add the public part of **~/.ssh/keys/key1/openssh.keyforsshbeyondremote.priv**

5\. Log out of **sshbeyondremote.server.com**

6\. Check that **AllowTcpForwarding yes** in **/etc/ssh/sshd\_config** on **remote.server.com**

Note, you may have the following:

```
Match Group SSHTunnel_RemoteAccessGroup
	AllowTcpForwarding yes
	PermitOpen=sshbeyondremote.server.com:22
```

Big, big warning: you have to ensure that you use the same **case** in /etc/ssh/sshd\_config and in ~/.ssh/config if you use PermitOpen. This seems like a bug because DNS names are case insensitive. If you don't do this you may see:

```
channel 9: open failed: administratively prohibited: open failed
```

7\. From **your machine** add the following to **~/.ssh/config**

```
Host *
  ServerAliveInterval 60

Host remote.server.com
  HostName remote.server.com
  Port 10022
  User useronremote
  IdentityFile ~/.ssh/keys/key1/openssh.keyforremote.priv
  LocalForward 2222 sshbeyondremote.server.com:22

Host sshbeyondremote
  Hostname localhost
  Port 2222
  User useronsshbeyondremote
  IdentityFile ~/.ssh/keys/key1/openssh.keyforsshbeyondremote.priv
```

8\. Now you should be able to run this from **your machine**:

```
ssh sshbeyondremote
```

**References**

-   There's a good write up about local, remote and dynamic port forwarding from [help.ubuntu.com](http://help.ubuntu.com/) @ [link](http://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding).
    
-   Image from [https://www.openssh.com/](http://www.openssh.com/)
    

**Versions**

Version of the OpenSSH client:

```
OpenSSH_7.2p2 Ubuntu-4ubuntu2.4, OpenSSL 1.0.2g  1 Mar 2016
```

```
OpenSSH_7.6p1 Debian-4, OpenSSL 1.0.2n  7 Dec 2017
```

Version of the OpenSSH server: