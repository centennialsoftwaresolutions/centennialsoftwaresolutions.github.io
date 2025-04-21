# Files Updated by 2021.2 petalinux-create -t apps

![Xilinx_logo](Xilinx_logo.png)

This post lists the **files** updated in a 2021.2 PetaLinux project after \[petalinux-create --project board\_linux -t apps --template install --name mypetalinuxapp --enable --force\] is run.

<u><span>Generate the List</span></u>

cd /scratch/zpfeffer/2022-08-25/board/board\_linux

source /tools/xilinx/petalinux-v2021.2-final/settings.sh

touch start

petalinux-create --project board\_linux \\

​	\-t apps --template install --name mypetalinuxapp --enable --force

find . -cnewer start -type f -printf "%p\\n" | sort

<u><span>The List</span></u>

./board\_linux/build/conf/bblayers.conf

./board\_linux/build/misc/rootfs\_config/Kconfig

./board\_linux/build/misc/rootfs\_config/Kconfig.user

./board\_linux/.petalinux/usage\_statistics

./board\_linux/.petalinux/usage\_statistics\_token

./board\_linux/project-spec/configs/rootfs\_config

./board\_linux/project-spec/configs/rootfs\_config.old

./board\_linux/project-spec/meta-user/conf/user-rootfsconfig

./board\_linux/project-spec/meta-user/recipes-apps/mypetalinuxapp/files/mypetalinuxapp

./board\_linux/project-spec/meta-user/recipes-apps/mypetalinuxapp/.gdbinit

./board\_linux/project-spec/meta-user/recipes-apps/mypetalinuxapp/mypetalinuxapp.bb

./board\_linux/project-spec/meta-user/recipes-apps/mypetalinuxapp/README

<u><span>Reference</span></u>

-   Xilinx logo clipped from [<u><span>xilinx.com</span></u>](http://xilinx.com/)