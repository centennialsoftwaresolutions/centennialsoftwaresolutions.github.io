# Build a Faster Python 3

![python_logo](python_logo.png)

This post lists the commands to build Python 3.5.2 on Ubuntu with Profile Guided Optimization and install the result into a local directory.

**Steps**

[#Open](https://www.centennialsoftwaresolutions.com/blog/hashtags/Open) a terminal

mkdir -p ~/fastpython3/src

mkdir -p ~/fastpython3/install

cd ~/fastpython3/src

wget https://www.python.org/ftp/python/3.5.2/Python-3.5.2.tgz

tar -zxvf Python-3.5.2.tgzcd Python-3.5.2/

./configure --prefix=${HOME}/fastpython3/install/

make profile-opt

make install

export PATH="${HOME}/fastpython3/install/bin:${PATH}"

which python

**Validated On**

Validated on a Virtual Machine called fresh-ubuntu-16.04.3-desktop-amd64-4GB-RAM-100GB-Disk with 4GB RAM and a 100 GB VMDK, dynamically allocated disk, running a fresh install of Ubuntu 16.04.3, with no updates but with host-extensions installed, on VirtualBox Version 5.2.12 r122591 (Qt5.6.2) on Windows 7 SP1.