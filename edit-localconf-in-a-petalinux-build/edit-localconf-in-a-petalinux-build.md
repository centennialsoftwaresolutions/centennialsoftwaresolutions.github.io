# Edit local.conf in a PetaLinux Build

![yocto_project_logo](yocto_project_logo.png)

This post discusses how to edit "local.conf" in a build managed by PetaLinux Tools.

**How To Edit local.conf**

Put your changes in **./project-spec/meta-user/conf/petalinuxbsp.conf** to "edit" **conf/local.conf**.

**Discussion**

PetaLinux Tools stores local.conf at **build/conf/local.conf**.

Any changes you make to **local.conf** are lost because PetaLinux Tools 2017.4 generates **local.conf**.

To allow people to "edit" local.conf PetaLinux Tools generates this line at the end of local.conf:

```
include conf/petalinuxbsp.conf
```

This line ensures that conf/petalinuxbsp.conf is read when local.conf.

**References**

The Xilinx + Yocto graphic is an amalgamation of [Xilinx](http://pbs.twimg.com/profile_images/535545777020338176/pEWdIYq__400x400.png) and [Yocto](http://www.yoctoproject.org/docs/2.0/yocto-project-qs/yocto-project-qs.html) icons.