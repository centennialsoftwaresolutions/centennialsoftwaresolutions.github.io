# Fix E216: No such group or event: filetypedetect BufReadPost msg in <SNR>14_XxdBack

![Vim_logo](Vim_logo.png)

This post shows two ways to stop an error that pops up in gVim > Tools > Convert Back:

Error detected while processing functions <SNR>14\_XxdBack:

line 9:

E216: No such group or event: filetypedetect BufReadPost

This message goes away when you press **Enter**.

## **<u><span>Method 1</span></u>**

Run:

```
:filetype on
```

Note, this action causes:

```
Detail: The ":filetype on" command will load one of these files:
		Amiga	    $VIMRUNTIME/filetype.vim
		Mac	    $VIMRUNTIME:filetype.vim
		MS-DOS	    $VIMRUNTIME\filetype.vim
		RiscOS	    Vim:Filetype
		Unix	    $VIMRUNTIME/filetype.vim
		VMS	    $VIMRUNTIME/filetype.vim
	This file is a Vim script that defines autocommands for the
	BufNewFile and BufRead events.  If the file type is not found by the
	name, the file $VIMRUNTIME/scripts.vim is used to detect it from the
	contents of the file.
	When the GUI is running or will start soon, the menu.vim script is
	also sourced.  See |'go-M'| about avoiding that.
```

From https://vimdoc.sourceforge.net/htmldoc/filetype.html 

## **<u><span>Method 2</span></u>**

Change menu.vim so that filetypedetect is only called if did\_load\_filetypes exists (thank you to Bram for suggesting a better conditional).

```
--- menu.vim.orig       2022-06-28 07:08:36.000000000 -0600
+++ menu.vim    2023-05-02 20:20:00.052527000 -0600
@@ -599,8 +599,10 @@
     s:XxdFind()
     exe ':%!' .. g:xxdprogram .. ' -r'
   endif
-  set ft=
-  doautocmd filetypedetect BufReadPost
+  if exists('#filetypedetect') && exists('#BufReadPost')
+    set ft=
+    doautocmd filetypedetect BufReadPost
+  endif
   &mod = mod
 enddef
```

Method 2 demonstrates why Method 1 works, namely that since **filetypedetect** is defined in **filetype.vim** and since typing **:filetype on** loads **filetype.vim, filetypedetect** is loaded when the **Convert Back** menu item runs which allows the menu item to run without raising the message.

## **<u><span>References</span></u>**

**Vim logo** https://upload.wikimedia.org/wikipedia/commons/9/9f/Vimlogo.svg

Vim (text editor). (2023, April 20). In _Wikipedia_. https://en.wikipedia.org/wiki/Vim\_(text\_editor)