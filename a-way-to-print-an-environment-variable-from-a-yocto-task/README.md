# A Way to Print an Environment Variable from a Yocto Task

![yocto_project_logo](yocto_project_logo.png)

This post shows \_a\_ way to print an environment variable from a Yocto task. I list it as \_a\_ way since I'm just learning Yocto and haven't come across a better way to do this.

Given this Yocto snippet in a recipe (a \*.bb file):

```
export DL_DIR
export P
export WORKDIR

python do_unpack() {
        bb.note("Unpacking source tarball ...")

        os.system("tar x -C ${WORKDIR} -f ${DL_DIR}/${P}.tar.gz")

        bb.note("Unpacked source tarball.")
}
```

```
DL_DIR = "${TOPDIR}/downloads"
P = "${PN}-${PV}"
WORKDIR = "${TMPDIR}/work/${PF}"
```

You can use the following to see what DL\_DIR, P and WORKDIR are:

```
python do_unpack() {
        bb.note("Unpacking source tarball WORKDIR = ", d.getVar('WORKDIR', True), "DL_DIR = ", d.getVar('DL_DIR', True), "P = ", d.getVar('P', True), " ...")

        os.system("tar x -C ${WORKDIR} -f ${DL_DIR}/${P}.tar.gz")

        bb.note("Unpacked source tarball.")
}
```

**References**

-   Yocto logo from [link](http://www.yoctoproject.org/wp-content/uploads/2017/08/YoctoProject_StyleGuide.pdf).