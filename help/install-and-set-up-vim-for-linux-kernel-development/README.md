# Install and Set up Vim for Linux Kernel Development

![tux_vim_logo](tux_vim_logo.png)

This post lists the steps to install and setup Vim for Linux kernel development.

**<u><span>Steps</span></u>**

1\. Type **sudo apt-get install vim**

2\. Type **vi ~/.vimrc**

3\. Copy **:set tabstop=8 softtabstop=8 shiftwidth=8 noexpandtab cindent cc=80 | %retab | autocmd BufWritePre \* %s/\\s\\+$//e**

4\. In vim type **i**

5\. Paste the line you copied into the doc

6\. Press **ESC**

7\. Type **:w ENTER**

8\. Press **ESC**

9\. Press :**q ENTER**

**<u><span>Reference</span></u>**

Image is an amalgamation of images from \[[<u><span>link</span></u>](https://en.wikipedia.org/wiki/Vim_(text_editor))\] (Vim) and \[[<u><span>link</span></u>](https://www.iconfinder.com/icons/367633/linux_tux_icon#size=128)\] (Tux)

**<u><span>Note</span></u>**

A post that covers fixing tabs is at \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/set-up-fix-a-buffer-for-linux-kernel-coding-style-in-vim)\].