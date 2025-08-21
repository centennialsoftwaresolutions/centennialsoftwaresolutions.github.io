# Integrate SWUpdate into a PetaLinux Project

![yocto_project](yocto_project.png)

This post lists steps to integrate SWUpdate into a PetaLinux Project.

The results have not been thoroughly tested.

**Steps**

1\. Clone the SWUpdate meta layer into ext\_source:

```
cd components
mkdir -p ext_source
cd ext_source
git clone https://github.com/sbabic/meta-swupdate.git 
cd meta-swupdate
git checkout morty
```

2\. Download these patches to the meta-swupdate directory

-   [patch1.txt](http://drive.google.com/open?id=1APFJW-n3iOKamCY87DrhtSKDZP_W_dRc)
    
-   [patch2.txt](http://drive.google.com/open?id=1VLY_fwwx3kWv7Uu5jQoX27C5MPhCQR3j)
    

3\. Apply the patches:

```
patch -p1 < patch1.txt
patch -p1 < patch2.txt
```

4\. Follow the instructions for adding a layer listed in [link](http://www.zachpfeffer.com/single-post/Add-a-Yocto-Layer-to-a-PetaLinux-Project-and-Build-a-Recipe-in-the-Layer-with-PetaLinux-Tools) (but use meta-swupdate instead of the example) and add the following to project-spec/meta-user/conf/petalinucbsp.conf:

```
project-spec/meta-user/conf/petalinuxbsp.conf
@@ -1,3 +1,5 @@
 #User Configuration
 
 #OE_TERMINAL = "tmux"
+
+SIGGEN_UNLOCKED_RECIPES += "mtd-utils"
```

You should have approximately these diffs once you're done:

```
iff --git a/project-spec/configs/config b/project-spec/configs/config
index 0914524..980a885 100644
--- a/project-spec/configs/config
+++ b/project-spec/configs/config
@@ -255,5 +255,6 @@ CONFIG_YOCTO_NETWORK_SSTATE_FEEDS_URL="http://petalinux.xilinx.com/sswreleases/r
 #
 # User Layers
 #
-CONFIG_USER_LAYER_0=""
+CONFIG_USER_LAYER_0="/home/pfefferz/plprjs4/mtd_board/components/ext_source/meta-swupdate"
+CONFIG_USER_LAYER_1=""
 CONFIG_SUBSYSTEM_BOOTARGS_GENERATED="earlycon clk_ignore_unused"
diff --git a/project-spec/configs/rootfs_config b/project-spec/configs/rootfs_config
index f3561dd..df48a0c 100644
--- a/project-spec/configs/rootfs_config
+++ b/project-spec/configs/rootfs_config
@@ -4379,6 +4379,7 @@ CONFIG_bridge-utils=y
 #
 # user packages 
 #
+CONFIG_swupdate=y
 
 #
 # PetaLinux RootFS Settings
diff --git a/project-spec/meta-user/conf/petalinuxbsp.conf b/project-spec/meta-user/conf/petalinuxbsp.conf
index a2e9efa..936ee17 100644
--- a/project-spec/meta-user/conf/petalinuxbsp.conf
+++ b/project-spec/meta-user/conf/petalinuxbsp.conf
@@ -1,3 +1,5 @@
 #User Configuration
 
 #OE_TERMINAL = "tmux"
+
+SIGGEN_UNLOCKED_RECIPES += "mtd-utils"
diff --git a/project-spec/meta-user/recipes-core/images/petalinux-image.bbappend b/project-spec/meta-user/recipes-core/images/petalinux-image.bbappend
index 72e0dad..f767bdc 100644
--- a/project-spec/meta-user/recipes-core/images/petalinux-image.bbappend
+++ b/project-spec/meta-user/recipes-core/images/petalinux-image.bbappend
@@ -2,3 +2,4 @@
 #      cascaded representation with line breaks are not valid in this file.
 IMAGE_INSTALL_append = " peekpoke"
 IMAGE_INSTALL_append = " gpio-demo"
+IMAGE_INSTALL_append = " swupdate"
```

5\. Type petalinux-build and test.

**Reference**

-   swupdate documentation is at [https://sbabic.github.io/swupdate/](http://sbabic.github.io/swupdate/)
    
-   The Xilinx + Yocto graphic is an amalgamation of [Xilinx](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png) and [Yocto](http://www.yoctoproject.org/docs/2.0/yocto-project-qs/yocto-project-qs.html) icons.
    

**Notes**

You'll get SWUpdate 2017.1 with this method. Take a look at this [link](http://www.zachpfeffer.com/single-post/Add-a-Yocto-Layer-to-a-PetaLinux-Project-and-Build-a-Recipe-in-the-Layer-with-PetaLinux-Tools) to see how to figure this out.