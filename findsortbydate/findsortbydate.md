# find sort by date

![gnu_logo](gnu_logo.png)

Linux commands to sort found files by date.

This post shows the most useful answer I saw on [https://unix.stackexchange.com](http://unix.stackexchange.com/) to sort found files. I also add how to sort the files modified in the last 10 minutes.

**Commands**

Sort all files found by time modified

```
find . your-options -printf "%T+\t%p\n" | sort
```

Sort all files modified less than 12 minutes ago

```
find . -cmin -12 -printf "%T+\t%p\n" | sort
```

**References**

-   See original [link](http://unix.stackexchange.com/questions/29899/how-can-i-use-find-and-sort-the-results-by-mtime?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa) and answer from [angus](http://unix.stackexchange.com/users/4873/angus)
    
-   Free Online HTML Escape / Unescape Tool - FreeFormatter.com
    
-   Find man page @ [link](http://linux.die.net/man/1/find)
    
-   GNU image from [link](http://en.wikipedia.org/wiki/GNU_Project)