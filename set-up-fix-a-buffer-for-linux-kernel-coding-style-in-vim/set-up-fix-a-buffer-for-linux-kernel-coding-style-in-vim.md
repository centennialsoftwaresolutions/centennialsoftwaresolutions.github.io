# Set Up & Fix a Buffer for Linux kernel Coding Style in Vim

![linux_vim_logo_1](linux_vim_logo_1.png)

This post lists the Vim commands to set up and fix a buffer so that it adheres to Linux kernel coding style guidelines.

**<u><span>Commands</span></u>**

**Set up options**

:set tabstop=8 softtabstop=8 shiftwidth=8 noexpandtab cindent

**Fix the Existing Buffer (now that the options are in effect)**

:%retab

**Remove white space on save**

:autocmd BufWritePre \* %s/\\s\\+$//e

**Set a 80 char column visual guide**

:set cc=80

**<u><span>Execute All Commands At Once</span></u>**

:set tabstop=8 softtabstop=8 shiftwidth=8 noexpandtab cindent cc=80 | %retab | autocmd BufWritePre \* %s/\\s\\+$//e

**Note**

You can put this line directly into your personal Vim initialization file: ~/.vimrc

**<u><span>References</span></u>**

-   Options at \[[link](http://www.ittc.ku.edu/~kulkarni/teaching/EECS678/projects/scheduling/materials/dot_vimrc)\]
    
-   Retab at \[[link](http://vim.wikia.com/wiki/Converting_tabs_to_spaces)\]
    
-   Remove white space at \[[link](http://vim.wikia.com/wiki/Remove_unwanted_spaces)\]
    
-   Over 80 char at \[[link](https://stackoverflow.com/questions/235439/vim-80-column-layout-concerns?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)\]
    
-   Image is an amalgamation of images from \[[link](https://en.wikipedia.org/wiki/Vim_(text_editor))\] (Vim) and \[[link](https://www.iconfinder.com/icons/367633/linux_tux_icon#size=128)\] (Tux)
    
-   Multiple commands at once \[[link](http://vim.wikia.com/wiki/Multiple_commands_at_once)\]