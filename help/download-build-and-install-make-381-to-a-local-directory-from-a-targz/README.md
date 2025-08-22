# Download, Build and Install Make 3.81 to a Local Directory From a **tar.gz**

![gnu_logo](gnu_logo.png)

This post lists the instructions to download, build and install Make 3.81 to a local directory.

Before running these instructions CD into a directory you want to install in.

**Commands**

**# Save directory**

INSTALLDIR=$(pwd)

**# Put a custom bin folder in place and update the path to check it first**

LOCALTOOLS=$(pwd)/tools



echo $LOCALTOOLS



mkdir -p $LOCALTOOLS 



echo export PATH=$LOCALTOOLS/bin:\$PATH > set_env.sh



source ./set_env.sh



**# Test it**



mkdir -p $LOCALTOOLS/bin



echo echo Hello > $LOCALTOOLS/bin/test-set_env.sh



chmod +x $LOCALTOOLS/bin/test-set_env.sh



test-set_env.sh **# You should see "Hello"**

[**#Get**](https://www.centennialsoftwaresolutions.com/blog/hashtags/Get) **and install make-3.81 locally**



CURDIRBEFOREMAKE=$(pwd)



LOCALPACKAGE=$(pwd)/package



echo $LOCALPACKAGE



mkdir -p $LOCALPACKAGE



cd $LOCALPACKAGE



wget https://ftp.gnu.org/gnu/make/make-3.81.tar.gz



tar -xvzf $LOCALPACKAGE/make-3.81.tar.gz



cd make-3.81



./configure --prefix=$LOCALTOOLS



make



sudo make install



cd $CURDIRBEFOREMAKE

[**#Test**](https://www.centennialsoftwaresolutions.com/blog/hashtags/Test) **make**



cd $INSTALLDIR

source ./set_env.sh

which make # you should see $LOCALTOOLS/bin/make



make --version # should show GNU Make 3.81

**Reference**

GNU image from[ link](http://en.wikipedia.org/wiki/GNU_Project).