# PetaLinux 2018.1 in Docker

![Xilinx_logo](Xilinx_logo.png)

This post describes how to install and run Docker and build PetaLinux 2018.1 in a Docker container. It starts by listing where to get Ubuntu 18.04.5 and some of the settings needed if you run everything in a VM.

**<u><span>Get Ubuntu 18.04.5</span></u>**

Go to https://releases.ubuntu.com/18.04.5/

Download ubuntu-18.04.5-desktop-amd64.iso (2.0 GB)

…or click:

[https://releases.ubuntu.com/18.04.5/ubuntu-18.04.5-desktop-amd64.iso ](https://releases.ubuntu.com/18.04.5/ubuntu-18.04.5-desktop-amd64.iso) 

**<u><span>Create a VM (with VirtualBox or VMware Workstation)</span></u>**

Create a VM with:

-   200 GB Disk,
    
-   16 GB RAM,
    
-   4 processors,
    
-   2 cores per processor,
    
-   all virtualization enabled
    

Install Ubuntu 18.04.5 on the VM

**<u><span>Install Docker</span></u>**

Install and configure Docker to run without sudo by running:

```
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

Run:

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Ignore:

```
gpg: WARNING: unsafe ownership on homedir '/home/demo/.gnupg'
Run (for x86_64/amd64):
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Run:

```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Type Y at:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  docker-ce-rootless-extras docker-scan-plugin git git-man liberror-perl pigz
Suggested packages:
  aufs-tools cgroupfs-mount | cgroup-lite git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk gitweb git-cvs git-mediawiki
  git-svn
Recommended packages:
  slirp4netns
The following NEW packages will be installed:
  containerd.io docker-ce docker-ce-cli docker-ce-rootless-extras docker-scan-plugin git git-man liberror-perl pigz
0 upgraded, 9 newly installed, 0 to remove and 286 not upgraded.
Need to get 101 MB of archives.
After this operation, 440 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Run:

```
sudo groupadd docker
sudo usermod -aG docker ${USER}
newgrp docker
```

Reboot the VM

**<u><span>Run Docker "Hello, World!" and Test Ubuntu Boot</span></u>**

Run:

```
docker run hello-world
```

You should see (excerpt) :

```
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

Run:

```
docker run -it ubuntu bash
```

You should see:

```
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
16ec32c2132b: Pull complete 
Digest: sha256:82becede498899ec668628e7cb0ad87b6e1c371cb8a1e597d83a47fac21d6af3
Status: Downloaded newer image for ubuntu:latest
root@935032f70557:/#
```

To quit type: exit like:

```
root@935032f70557:/# exit
```

See an error?

If you see:

```
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create": dial unix /var/run/docker.sock: connect: permission denied.
```

Run:

```
sudo systemctl restart docker
```

You may see the error above if you ran:

```
docker run hello-world 
```

…before running:

```
sudo groupadd docker
sudo usermod -aG docker ${USER}
newgrp docker
```

**<u><span>Create a Dockerfile for PetaLinux 2018.1 and Build the Container</span></u>**

Create the Dockerfile

```
mkdir -p ~/plxdocker
cat << 'DOCKERFILE' > ~/plxdocker/Dockerfile
FROM ubuntu:16.04
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -y update
RUN apt-get -y install apt-utils
RUN apt-get install -y locales locales-all
ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

RUN apt-get -y install dialog
RUN apt-get -y install git
RUN apt-get -y install sudo
RUN apt-get -y install vim # not strictly necessary
RUN apt-get -y install nano # not strictly necessary
RUN apt-get -y install cpio # useful
RUN apt-get -y install locales
RUN apt-get -y install libgtk2.0-0 # fixes an issue running the SDK when the FSBL is built
RUN apt-get -y install python3 dos2unix iproute2 gawk xvfb git make net-tools libncurses5-dev tftpd lib32z1 libssl-dev flex bison libselinux1 gnupg wget diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib build-essential libsdl1.2-dev libglib2.0-dev libsdl-dev build-essential gcc-multilib glib2.0 automake screen pax gzip libtool-bin
RUN apt-get -y install vim
ARG UNAME=docker
ARG UID=1000
ARG GID=1000
RUN groupadd -g $GID -o $UNAME
RUN adduser --disabled-password --gecos '' --uid $UID --gid $GID docker
RUN adduser docker sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER docker
WORKDIR /home/docker
RUN mkdir ~/Downloads
ENV DEBIAN_FRONTEND teletype
DOCKERFILE
```

Build the container

```
cd ~/plxdocker
docker build --build-arg UID=$(id -u) --build-arg GID=$(id -g) -t plxdocker .
```

**<u><span>Create an Instance of the Container and Launch It</span></u>**

Create the Docker instance

```
cd ~
mkdir -p plxdocker_build_artifacts
docker run -it \
--name plxdocker_instance1 \
-v "$(pwd)"/plxdocker_build_artifacts:/build_artifacts:Z \
-v plxdocker_volume:/home/docker \
plxdocker
# Use Ctrl-p-q to quit running in Docker instance
```

You only need to run this command (docker run -it...) once. This command will also start the container. I've intentionally used two different storage mechanisms to demonstrate how to connect a volume: **plxdocker\_volume:/home/docker** and a bind point **"$(pwd)"/plxdocker\_build\_artifacts:/build\_artifacts:Z**

Also, **plxdocker\_instance1** could be named **plxdocker\_instance2** or something else. **plxdocker\_volume** could be **plxdocker\_volume2** or something else.

Test the bind point, run in the container

```
touch ~/plxdocker_build_artifacts/test.txt
```

Run on the host:

```
ls /build_artifacts/
```

You should see **test.txt**

FYI, to delete the container

```
docker stop plxdocker_instance1
docker rm plxdocker_instance1
```

FYI, to delete the docker volume

```
docker volume rm plxdocker_volume
```

Open a new terminal and run to get another "terminal" into the container instance

```
docker exec -it plxdocker_instance1 bash
```

**Get PetaLinux Tools 2018.1 and the ZCU102 BSP and Copy them Into the Container**

Go to:

https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools/archive.html 

...and click Archive.

Click 2018.1

Download to ~/Downloads on the host:

https://www.xilinx.com/member/forms/download/xef.html?filename=xilinx-zcu102-v2018.1-final.bsp ZCU102 BSP (prod-silicon) (BSP - 598.21MB)

MD5 SUM Value : cea5f11761e7f38cbfcf0a07a19094e0

Download to ~/Downloads on the host:

https://www.xilinx.com/member/forms/download/xef.html?filename=petalinux-v2018.1-final-installer.run 

PetaLinux 2018.1 Installer (TAR/GZIP - 6.21GB)

MD5 SUM Value : f4e97b16a180c5f4407f729280a71062

Copy the files into the container instance

```
docker cp  ~/Downloads/petalinux-v2018.1-final-installer.run plxdocker_instance1:/home/docker/Downloads
docker cp  ~/Downloads/xilinx-zcu102-v2018.1-final.bsp plxdocker_instance1:/home/docker/Downloads
```

**<u><span>Install PetaLinux 2018.1, Build the ZCU102 BSP, and test It with QEMU</span></u>**

Inside the Docker instance Install PetaLinux 2018.1

```
mkdir -p $HOME/petalinux 
cd ~/Downloads 
./petalinux-v2018.1-final-installer.run $HOME/petalinux/2018.1
# Enter,q,y,Enter,q,y,Enter,q,y,Enter,
```

Ignore (duplicates removed)

```
/tmp/tmp.KmoLfsa92P/./tools/common/petalinux/utils/petalinux-env-check: line 219: [: =: unary operator expected
/tmp/tmp.KmoLfsa92P/./tools/common/petalinux/utils/petalinux-env-check: line 302: [: ==: unary operator expected
/tmp/tmp.KmoLfsa92P/./tools/common/petalinux/utils/petalinux-env-check: line 304: [: ==: unary operator expected
/tmp/tmp.KmoLfsa92P/./tools/common/petalinux/utils/petalinux-env-check: line 306: [: ==: unary operator expected
/tmp/tmp.KmoLfsa92P/./tools/common/petalinux/utils/petalinux-env-check: line 251: [: =: unary operator expected
INFO: Checking installed development libraries
/tmp/tmp.KmoLfsa92P/./tools/common/petalinux/utils/petalinux-env-check: line 388: [: ==: unary operator expected
```

The last line should be

```
INFO: PetaLinux SDK has been installed to /home/docker/petalinux/2018.1/.
```

Create the project

```
mkdir -p ~/plxprjs 
cd ~/plxprjs 
source ~/petalinux/2018.1/settings.sh 
petalinux-create -t project -s ~/Downloads/xilinx-zcu102-v2018.1-final.bsp
```

Ignore the same as above

```
 # /tmp/tmp.KmoLfsa92P/./tools/common/petalinux/utils/petalinux-env-check: line 219: [: =: unary operator expected
# The last line will be: 
 # INFO: New project successfully created in /home/docker/plxprjs/
```

Build the BSP

```
cd xilinx-zcu102-2018.1 
petalinux-build 
# You'll likely see an error around:
# 2: fsbl-2018.1+gitAUTOINC+aaa566bc3f-r0 do_configure - 35s (pid 71210)
# If you do, run petalinux-build again
petalinux-build 
```

You should see the final line:

```
[INFO] successfully built project
```

Test booting U-Boot

```
petalinux-boot --qemu --u-boot 
```

Type Ctrl-a x to quit

Test booting the kernel

```
petalinux-boot --qemu --kernel # boots the kernel
```

Type Ctrl-a x to quit

**<u><span>References</span></u>**

-   The Xilinx graphic is from \[[link](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]