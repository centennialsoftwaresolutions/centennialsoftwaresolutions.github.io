# Find ".dts," ".dtsi," and ".dtb" files in a PetaLinux build, exclude ./build directory

![xilinx_logo](xilinx_logo.png)

This post shows you how to find the ".dts," ".dtsi," and ".dtb" files in a PetaLinux build, excluding the ones in the ./build directory. It also lists the files I found in a 2019.1 ZCU102 build. Files listed in orange are the files users are meant to modify.

**find . -name "\*.dts" -type f -not -path "./build\*"**

./components/plnx\_workspace/device-tree/device-tree/system-top.dts

./project-spec/meta-user/recipes-bsp/device-tree/files/zynqmp-qemu-arm.dts

./project-spec/meta-user/recipes-bsp/device-tree/files/multi-arch/zynqmp-qemu-multiarch-arm.dts

./project-spec/meta-user/recipes-bsp/device-tree/files/multi-arch/zynqmp-qemu-multiarch-pmu.dts

**find . -name "\*.dtsi" -type f -not -path "./build\*"**

./components/plnx\_workspace/device-tree/device-tree/pcw.dtsi

./components/plnx\_workspace/device-tree/device-tree/system-conf.dtsi

./components/plnx\_workspace/device-tree/device-tree/zynqmp-clk-ccf.dtsi

./components/plnx\_workspace/device-tree/device-tree/zcu102-rev1.0.dtsi

./components/plnx\_workspace/device-tree/device-tree/pl.dtsi

./components/plnx\_workspace/device-tree/device-tree/zynqmp.dtsi

./project-spec/meta-user/recipes-bsp/device-tree/files/xen.dtsi

./project-spec/meta-user/recipes-bsp/device-tree/files/system-user.dtsi

./project-spec/meta-user/recipes-bsp/device-tree/files/openamp.dtsi

./project-spec/meta-user/recipes-bsp/device-tree/files/xen-qemu.dtsi

**find . -name "\*.dtb" -type f -not -path "./build\*"**

./pre-built/linux/images/xen-qemu.dtb

./pre-built/linux/images/xen-openamp.dtb

./pre-built/linux/images/zynqmp-qemu-arm.dtb

./pre-built/linux/images/xen.dtb

./pre-built/linux/images/zynqmp-qemu-multiarch-arm.dtb

./pre-built/linux/images/openamp.dtb

./pre-built/linux/images/system.dtb

./pre-built/linux/images/zynqmp-qemu-multiarch-pmu.dtb

./images/linux/zynqmp-qemu-multiarch-arm.dtb

./images/linux/system.dtb

./images/linux/zynqmp-qemu-multiarch-pmu.dtb

**find . -name "\*.dts" -type f -not -path "./build\*" -print0 | xargs --null grep 'include'**

./components/plnx\_workspace/device-tree/device-tree/system-top.dts:#include "zynqmp.dtsi"

./components/plnx\_workspace/device-tree/device-tree/system-top.dts:#include "zynqmp-clk-ccf.dtsi"

./components/plnx\_workspace/device-tree/device-tree/system-top.dts:#include "zcu102-rev1.0.dtsi"

./components/plnx\_workspace/device-tree/device-tree/system-top.dts:#include "pl.dtsi"

./components/plnx\_workspace/device-tree/device-tree/system-top.dts:#include "pcw.dtsi"

./components/plnx\_workspace/device-tree/device-tree/system-top.dts:#include "system-user.dtsi"

**find . -name "\*.dtsi" -type f -not -path "./build\*" -print0 | xargs --null grep 'include'**

./components/plnx\_workspace/device-tree/device-tree/zcu102-rev1.0.dtsi:#include "include/dt-bindings/input/input.h"

./components/plnx\_workspace/device-tree/device-tree/zcu102-rev1.0.dtsi:#include "include/dt-bindings/gpio/gpio.h"

./components/plnx\_workspace/device-tree/device-tree/zcu102-rev1.0.dtsi:#include "include/dt-bindings/pinctrl/pinctrl-zynqmp.h"

./components/plnx\_workspace/device-tree/device-tree/zcu102-rev1.0.dtsi:#include "include/dt-bindings/phy/phy.h"

./project-spec/meta-user/recipes-bsp/device-tree/files/system-user.dtsi:/include/ "system-conf.dtsi"

**<u><span>References</span></u>**

-   UG1144 (v2019.1) May 22, 2019 PetaLinux Tools Documentation Reference Guide \[[<u><span>link</span></u>](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2019_1/ug1144-petalinux-tools-reference-guide.pdf)\] (p.109 to 111 discuss device tree files)
    
-   The Xilinx graphic is from \[[<u><span>link</span></u>](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png)\]