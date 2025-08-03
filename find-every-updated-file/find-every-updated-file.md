# find every file updated by a command

![gnu_logo_1](gnu_logo_1.png)

The post lists a way to find every file that gets updated by a command.

To find every file use a "start" file and find's -cnewer flag:

```
touch start
<DO STUFF>
find . -cnewer start -printf "%T+\t%p\n" | sort
```

**How this Works**

**touch start** creates or updates a a file called start before each command. You can name your start file something other than start.

The rest of the command is documented @ [find sort by date](http://www.zachpfeffer.com/single-post/findsortbydate).

**References**

-   Find man page @ [link](http://linux.die.net/man/1/find)
    
-   GNU image from [link](http://en.wikipedia.org/wiki/GNU_Project)
    
-   [Free Online HTML Escape / Unescape Tool - FreeFormatter.com](http://www.freeformatter.com/html-escape.html)