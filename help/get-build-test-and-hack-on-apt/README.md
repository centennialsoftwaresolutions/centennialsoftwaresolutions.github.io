# Get, Build, Test and Hack on Apt

![ubuntu_logo](ubuntu_logo.png)

Here are the exact commands to get, build, test and hack on the master branch of apt as of 2/27/2016 on Ubuntu 16.04.1 AMD64.

## Get

sudo apt-get install git

git clone https://github.com/Debian/apt

## Build

sudo apt-get install \\

cmake \\

libevent-pthreads-2.0-5 \\

libdb5.3 \\

libdb5.3-dev \\

libcurl4-gnutls-dev \\

zlib1g-dev \\

libbz2-dev \\ liblzma-dev \\

liblz4-dev \\

docbook-xsl \\

doxygen \\

libgtest-dev

cd apt

cmake .

sudo apt-get install \\

po4a \\

xsltproc \\

w3m

make all

## Test

./test/integration/run-tests

## Hack

sudo apt-get install vim

vim

In vim do: setlocal shiftwidth=3 noexpandtab tabstop=8

Discussion and patch submission on the mailing list: deity@lists.debian.org ([archive](http://lists.debian.org/deity/))

## Tip

To find the packages installed on your system \[1\]:

cat /var/lib/dpkg/status

## Note

Official git: git://anonscm.debian.org/apt/apt.git

Branch: master

## Reference

1\. https://github.com/Debian/apt