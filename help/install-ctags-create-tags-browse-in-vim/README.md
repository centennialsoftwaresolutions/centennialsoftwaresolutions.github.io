# Install ctags, Create tags, Browse in Vim

![vim_logo_1](vim_logo_1.png)

This post presents how to install ctags on Ubuntu 16.04.3, create tags and browse the code in vim.

**Install**

Type **sudo apt-get install ctags**

Note: this command will actually install exuberant-ctags on Ubuntu 16.04.3. Here's the output

```
zpfeffer@z:~/code$ sudo apt-get install ctags
[sudo] password for zpfeffer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'exuberant-ctags' instead of 'ctags'
The following NEW packages will be installed:
  exuberant-ctags
0 upgraded, 1 newly installed, 0 to remove and 46 not upgraded.
Need to get 126 kB of archives.
After this operation, 341 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 exuberant-ctags amd64 1:5.9~svn20110310-11 [126 kB]
Fetched 126 kB in 0s (294 kB/s)     
Selecting previously unselected package exuberant-ctags.
(Reading database ... 194228 files and directories currently installed.)
Preparing to unpack .../exuberant-ctags_1%3a5.9~svn20110310-11_amd64.deb ...
Unpacking exuberant-ctags (1:5.9~svn20110310-11) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up exuberant-ctags (1:5.9~svn20110310-11) ...
update-alternatives: using /usr/bin/ctags-exuberant to provide /usr/bin/ctags (ctags) in auto mode
update-alternatives: using /usr/bin/ctags-exuberant to provide /usr/bin/etags (etags) in auto mode
```

**Create tags File**

1\. cd into the directory of code

2\. Type **ctags -R .**

**Browse Code**

1\. Open a .c, .h or .cpp file with vim

2\. Put your cursor on a symbol

3\. Type **<C-\]>** to jump to a symbol. Keep typing to build a stack of symbols.

4\. Type **<C-t>** to jump back. Pop back to where you last were. Works until the stack of symbols is exhausted.

**<u><span>References</span></u>**

-   Vim and Ctags by Andrew Stewart at \[[<u><span>link</span></u>](https://andrew.stwrt.ca/posts/vim-ctags/)\]
    
-   The Vim logo is from \[[<u><span>link</span></u>](https://commons.wikimedia.org/wiki/File:Vimlogo.svg)\]
    

**<u><span>Additional Info</span></u>**

**What is are ctags?** (asked on Reddit at \[[<u><span>link</span></u>](https://www.reddit.com/r/programming/comments/9cs1sv/install_ctags_create_tags_browse_in_vim/e5e574b/?context=3&st=jlo3wxo4&sh=95e55e04)\])

From: [<u><span>http://ctags.sourceforge.net/whatis.html</span></u>](http://ctags.sourceforge.net/whatis.html) ctags is the program that generates an index also called tags. These tags are "language objects found in source files that allows these items to be quickly and easily located by a text editor or other utility. A tag signifies a language object for which an index entry is available (or, alternatively, the index entry created for that object)."