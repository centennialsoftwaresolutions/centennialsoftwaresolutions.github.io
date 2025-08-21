# What port is the tcf-agent listening on?

![Xilinx_logo](Xilinx_logo.png)

This post shows how to check what port the tcf-agent is listening on.

Commands were run on a ZCU102 booting a 2019.1 PetaLinux built image.ub.

**<u><span>Result</span></u>**

tcf-agent is running on 1534/tcp and 1534/udp in this example.

**<u><span>Commands</span></u>**

**netstat -tuln**

\# Active Internet connections (only servers)

\# Proto Recv-Q Send-Q Local Address Foreign Address State

\# tcp 0 0 0.0.0.0:21 0.0.0.0:\* LISTEN

\# tcp 0 0 0.0.0.0:22 0.0.0.0:\* LISTEN

\# tcp 0 0 0.0.0.0:23 0.0.0.0:\* LISTEN

\# tcp 0 0 0.0.0.0:1534 0.0.0.0:\* LISTEN

\# tcp 0 0 :::22 :::\* LISTEN

\# udp 0 0 0.0.0.0:1534 0.0.0.0:\*

**fuser 21/tcp**

\# 2418

**ps | grep 2418**

\# 2418 root 0:00 /usr/sbin/inetd

\# 2465 root 0:00 grep 2418

**fuser 22/tcp**

\# 2411

**ps | grep 2411**

\# 2411 root 0:00 /usr/sbin/dropbear -r /etc/dropbear/dropbear\_rsa\_host\_key -p 22 -w

\# 2468 root 0:00 grep 2411

**fuser 23/tcp**

\# 2418

**ps | grep 2418**

\# 2418 root 0:00 /usr/sbin/inetd

\# 2473 root 0:00 grep 2418

**fuser 1534/tcp**

\# 2436

**ps | grep 2436**

\# 2436 root 0:00 /usr/sbin/tcf-agent -d -L- -l0

\# 2478 root 0:00 grep 2436

**fuser 1534/udp**

\# 2436

**ps | grep 2436**

\# 2436 root 0:00 /usr/sbin/tcf-agent -d -L- -l0

\# 2483 root 0:00 grep 2436

**<u><span>Reference</span></u>**

-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]