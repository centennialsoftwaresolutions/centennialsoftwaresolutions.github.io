# Print the name of a file and the file's contents

![gnu_logo](gnu_logo.png)

This post lists a Linux command that will print the name of a file and then print the contents of that file.

The following command will print the name of the file and the files contents:

find . -type f -print -exec cat '{}' \\;

**References**

-   Find man page @ [link](http://linux.die.net/man/1/find)
    
-   GNU image from [link](http://en.wikipedia.org/wiki/GNU_Project)