# Find all text files

![tux](tux.png)

This blog is a repost of the best answer I've found to-date for: **find all text files**.

It also contains some additional info on how the method works.

Read to the end for an "improved" version.

**Command**

```
find . -type f -exec grep -Iq . {} \; -and -print
```

\-From stackoverflow submitted by [crudcore](http://stackoverflow.com/users/606784/crudcore)

**How this Works**

From the original post:

_The -I option to grep tells it to immediately ignore binary files and the . option along with the -q will make it immediately match text files so it goes very fast. You can change the -print to a -print0 for piping into an xargs -0 or something if you are concerned about spaces (thanks for the tip, @lucas.werkmeister!)Also the first dot is only necessary for certain BSD versions of find such as on OS X, but it doesn't hurt anything just having it there all the time if you want to put this in an alias or something._

**Additional Commentary**

find evaluates each expression for each file. There are 3 expressions here: **\-type**, **\-exec** and **\-print**. If **type** is not a file find moves on. If the **exec** doesn't return 0 find moves on. Only if the **type** is a **file** and **exec** returns **non-zero** will the print execute. To see this put the print first:

```
find . -print -type f -exec grep -Iq . {} \;
```

In this form every file will be output since print is always true.

**"Improved"**

**\-and** isn't needed

There is an implicit -and between each expression (from man find, look at definition of -and)

**.** isn't needed

If you don't list a starting point find assumes '**.**' (from **man find**, first paragraph under Description)

The "improved" version is:

```
find -type f -exec grep -Iq . {} \; -print
```

"improved" is in quotes because this change doesn't make the command noticeably faster and may actually be less desirable since people typically see find with **.** and **\-and** and may therefore be confused.

**Additional Examples**

```
find -type f -name "*do_*" -exec grep -Iq . {} \; -exec grep -REns "initrd" {} \; -exec echo "^^^^" \; -print -exec echo " " \;
```

Find files (-type f) whose names contain do\_ (-name "\*do\_\*") that are not binary (-exec grep -Iq . {} \\;) that contain the string initrd (-exec grep -REns "initrd" {} \\;) echo a ^^^^ then print the file name (-print) then print a new line (echo " " \\;)

**References**

-   Tux from [link](http://en.wikipedia.org/wiki/Tux)
    
-   Free Online HTML Escape / Unescape Tool - FreeFormatter.com @ [link](http://www.freeformatter.com/html-escape.html)