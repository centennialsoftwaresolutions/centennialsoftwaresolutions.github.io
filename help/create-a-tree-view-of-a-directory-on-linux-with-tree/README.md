# Create a Tree-View of a Directory on Linux with 'tree'

![gnu_logo_1](gnu_logo_1.png)

This post shows you how to create a tree-view of a directory on Linux (Ubuntu).

Install and Use Tree

To create a tree view of a directory install **tree** by running **sudo apt install tree**

Type **tree** in the directory you'd like to list:

![tree_2](tree_2.png)

Type **tree -d** to just get directories:

![tree_d_3](tree_d_3.png)

Create this Directory

The demo tree structure was created using these commands:

**mkdir ~/treedemo**

**cd ~/treedemo/**

**mkdir dir1**

**mkdir dir2**

**mkdir dir3**

**cd dir1**

**touch file1.txt**

**touch file2.txt**

**touch file3.txt**

**cd ../dir2**

**touch file4.txt**

Type **rm -rf ~/treedemo** to remove the treedemo directory.

Reference

GNU image from \[[link](http://en.wikipedia.org/wiki/GNU_Project)\]