# Comment-out printks with Vim

![tux_vim_logo_1](tux_vim_logo_1.png)

This post shows how to comment out all the printks in Vim.

The following command will put /\* and \*/ around all printks (in all lines), after getting confirmation on each replacement

```
:%s/\(printk(.*);\)/\/* \1 *\//gc
```

**References**

-   [http://vim.wikia.com/wiki/Search\_and\_replace](http://vim.wikia.com/wiki/Search_and_replace)
    
-   [Free Online HTML Escape / Unescape Tool - FreeFormatter.com](http://www.freeformatter.com/html-escape.html)
    
-   Amalgamation of Tux from [link](http://www.iconfinder.com/icons/367633/linux_tux_icon#size=128) and the Vim logo from [link](http://commons.wikimedia.org/wiki/File:Vimlogo.svg)