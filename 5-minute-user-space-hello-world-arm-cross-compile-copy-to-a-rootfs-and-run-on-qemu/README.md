# 5 Minute User Space "Hello, World!" ARM Cross Compile, Copy to a RootFS and Run on QEMU

![tux_logo_1](tux_logo_1.png)

This post shows you how to write a user space Hello, World! program, cross-compile it for ARM, copy into a Root FS and run the new Root FS on QEMU.

**<u><span>Before you Start</span></u>**

Read and follow the ARM instructions listed in **15 Minute Setup to Find, Change, Recompile and Test an ARM or x86 Linux Kernel Change in 12 Seconds** at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/15-minute-setup-to-find-change-recompile-and-test-an-arm-or-x86-linux-kernel-change-in-12-seconds)\]

**<u><span>Steps</span></u>**

**Create helloworld.c**

1\. Type **cd ~/tla/linux-4.10.6**

2\. Type **mkdir -p helloworld**

3\. Type **cd helloworld**

4\. Type **vi helloworld.c** and enter:

```
#include <stdio.h>                                                              
                                                                                
int main(int argc, char *argv[])                                                
{                                                                               
        printf("Hello, World!\n");                                              
}  
```

5\. Save the file with **:w** and quit with **:q**

**Compile It**

1\. Type **cd ~/tla/linux-4.10.6**

2\. Type **cd helloworld**

3\. Type **arm-linux-gnueabi-gcc helloworld.c -o helloworld -static**

4\. Type **ls -l**

You should see the new exe

```
zpfeffer@z:~/tla/linux-4.10.6/helloworld$ ls -l
total 572
-rwxrwxr-x 1 zpfeffer zpfeffer 579368 Jan  4 23:09 helloworld
-rw-rw-r-- 1 zpfeffer zpfeffer     85 Jan  4 23:09 helloworld.c
```

**Copy helloworld to the Rootfs Staging Area and repack the RootFS**

1\. Type **cd ~/tla/linux-4.10.6**

2\. Type **source ~/envset.sh**

3\. Type **cd helloworld**

4\. Type **cp -av helloworld $TOP/initramfs/arm-busybox**

5\. Create the initramfs

```
cd $TOP/initramfs/arm-busybox
find . | cpio -H newc -o > ../initramfs.cpio
cd ..
cat initramfs.cpio | gzip > $TOP/obj/initramfs.igz
```

**Boot QEMU and Run helloworld**

1\. Type

```
STAGE=$HOME/tla
TOP=$STAGE/teeny-linux
qemu-system-arm -M versatilepb  \
    -dtb $TOP/obj/linux-arm-versatile_defconfig/arch/arm/boot/dts/versatile-pb.dtb \
    -kernel $TOP/obj/linux-arm-versatile_defconfig/arch/arm/boot/zImage \
    -initrd $TOP/obj/initramfs.igz \
    -nographic -append "earlyprintk=serial,ttyS0 console=ttyAMA0"
```

2\. After boot type **ls /usr/bin** check that helloworld is in /usr/bin

You should see:

```
/ # ls /usr/bin/
[            du           last         pgrep        smemcap      unix2dos
[[           dumpleases   less         pkill        softlimit    unlink
awk          eject        logger       pmap         sort         unlzma
basename     env          logname      printf       split        unlzop
beep         envdir       lpq          pscan        strings      unshare
blkdiscard   envuidgid    lpr          pstree       sum          unxz
bunzip2      expand       lsof         pwdx         sv           unzip
bzcat        expr         lspci        readlink     svc          uptime
bzip2        fgconsole    lsusb        realpath     tac          users
cal          find         lzcat        renice       tail         uudecode
chpst        flock        lzma         reset        tcpsvd       uuencode
chrt         fold         lzopcat      resize       tee          vlock
chvt         free         man          rpm2cpio     telnet       volname
cksum        ftpget       md5sum       runsv        test         wall
clear        ftpput       mesg         runsvdir     tftp         wc
cmp          fuser        microcom     rx           time         wget
comm         groups       mkfifo       script       timeout      which
crontab      hd           mkpasswd     seq          top          who
cryptpw      head         nc           setkeycodes  tr           whoami
cut          helloworld   nmeter       setsid       traceroute   whois
dc           hexdump      nohup        setuidgid    traceroute6  xargs
deallocvt    hostid       nsenter      sha1sum      truncate     xz
diff         id           nslookup     sha256sum    tty          xzcat
dirname      install      od           sha3sum      ttysize      yes
dos2unix     ipcrm        openvt       sha512sum    udpsvd
dpkg         ipcs         passwd       showkey      unexpand
dpkg-deb     killall      patch        shuf         uniq
```

3\. Run helloworld by typing **helloworld**

You should see:

```
/ # helloworld 
Hello, World!
```

4\. Type **Control-a x** to quit QEMU

**<u><span>References</span></u>**

-   HTML escape from \[[<u><span>link</span></u>](https://www.freeformatter.com/html-escape.html)\]
    
-   Tux from \[[<u><span>link</span></u>](https://www.iconfinder.com/icons/367633/linux_tux_icon#size=128)\]