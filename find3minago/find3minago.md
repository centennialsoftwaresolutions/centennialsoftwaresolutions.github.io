# Find files updated less then 3 minutes ago, less then 10 minutes ago

![gnu_logo](gnu_logo.png)

This post lists the commands to find files updated less than 3 minutes ago or less than 10 minutes ago anywhere under the current directory.

To find a file that was updated less than 3 minutes ago on Linux type:

```
find . -cmin -3
```

To find a file that was updated less than 10 minutes ago type:

```
find . -cmin -10
```

One place this is useful is when working with Yocto. Yocto writes out log files as it works. Running this command allows you to see which files got updated or generated after your last build command.

**References**

-   Find man page @ [link](http://linux.die.net/man/1/find)
    
-   GNU image from [link](http://en.wikipedia.org/wiki/GNU_Project)