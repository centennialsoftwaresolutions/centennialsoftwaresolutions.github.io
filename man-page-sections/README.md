# man page sections

![gnu_logo](gnu_logo.png)

This post lists how to **list** the available sections of a manual and **view** one, **what each section number means** and in what order man searches for a section. All of this info is available by typing: man man.

**List Available Sections**

Type:

```
man -f man
```

Example Output:

```
pfefferz@plc2:~$ man -f man
man (7)              - macros to format man pages
man (1)              - an interface to the on-line reference manuals
```

Note:

Replace the second man with the manual you're interested in.

**View a Section**

Type:

```
man 7 man
```

Example Output:

```
MAN(7)                     Linux Programmer's Manual                    MAN(7)

NAME
       man - macros to format man pages

SYNOPSIS
       groff -Tascii -man file ...

       groff -Tps -man file ...

       man [section] title

DESCRIPTION
       This manual page explains the groff an.tmac macro package (often called
       the man macro package).  This macro package should be used by  develop‐
```

**What Each Section Number Means**

```
       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous  (including  macro  packages  and  conventions), e.g.
           man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]
```

Note

You can find this by typing:

```
man man
```

**Search Order**

```
The default action is to search in all  of  the  available
sections following a pre-defined order ("1 n l 8 3 2 3posix 3pm 3perl 5
4 9 6 7" by default, unless overridden  by  the  SECTION  directive  in 
/etc/manpath.config),
```

Note

You can find this by typing:

```
man man
```

**References**

-   GNU image from [link](http://en.wikipedia.org/wiki/GNU_Project)
    
-   Free Online HTML Escape at [link](http://www.freeformatter.com/html-escape.html)