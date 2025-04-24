# Which Petalinux version does this existing Petalinux project use?

Scenario:

You are looking at a Petalinux project and want to know which Petalinux version it uses.

Solution:

Inside every Petalinux project, in addition to the "build," "components," and "project-spec" directories, there's also a hidden ".petalinux" directory.

Inside .petalinux, a file named "metadata" contains the Petalinux version on the first line.

```
$ ls
build components config.project image project-spec

$ cat .petalinux/metadata
PETALINUX_VER=2021.2
...
```

This file has existed since at least Petalinux v2018.1, if not since before then.