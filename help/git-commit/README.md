# Key points from Chris Beams git-commit

![git_logo](git_logo.png)

Purpose

[ I wrote this to quickly refer to the the points I found relevant in ](http://chris.beams.io/posts/git-commit/)[https://chris.beams.io/posts/git-commit/. ](http://chris.beams.io/posts/git-commit/)

Point 1

While many repositories’ logs look like the former, there are exceptions. The [Linux kernel](http://github.com/torvalds/linux/commits/master) and [Git itself](http://github.com/git/git/commits/master) are great examples. Look at [Spring Boot](http://github.com/spring-projects/spring-boot/commits/master), or any repository managed by [Tim Pope](http://github.com/tpope/vim-pathogen/commits/master).

Point 2

The seven rules of a great Git commit message:

1.  Separate subject from body with a blank line
    
2.  Limit the **subject line** to **50** characters
    
3.  Capitalize the subject line
    
4.  Do not end the subject line with a period
    
5.  Use the imperative mood in the subject line
    
6.  Wrap the **body** at **72** characters
    
7.  Use the body to explain **what and why** vs. how
    

Point 3

A properly formed Git commit subject line should always be able to complete the following sentence:

If applied, this commit will _your subject line here_

Point 4

This commit from Bitcoin Core is a great example of explaining what changed and why:

```
commit eb0b56b19017ab5c16c745e6da39c53126924ed6
Author: Pieter Wuille 
Date:   Fri Aug 1 22:57:55 2014 +0200

   Simplify serialize.h's exception handling

   Remove the 'state' and 'exceptmask' from serialize.h's stream
   implementations, as well as related methods.

   As exceptmask always included 'failbit', and setstate was always
   called with bits = failbit, all it did was immediately raise an
   exception. Get rid of those variables, and replace the setstate
   with direct exception throwing (which also removes some dead
   code).

   As a result, good() is never reached after a failure (there are
   only 2 calls, one of which is in tests), and can just be replaced
   by !eof().

   fail(), clear(n) and exceptions() are just never called. Delete
   them.
```

Point 5

Read [Pro Git](http://git-scm.com/book/en/v2)

Additional Links

-   [Documentation](http://github.com/torvalds/linux/tree/master/Documentation/process) on how to contribute to Linux kernel
    
-   [Specific doc](http://github.com/torvalds/linux/blob/master/Documentation/process/5.Posting.rst) on formatting a patch
    

Content Cited

1.  Content from [https://chris.beams.io/posts/git-commit/](http://chris.beams.io/posts/git-commit/)
    
2.  git image from [https://git-scm.com/images/logos/downloads/Git-Logo-2Color.png](http://git-scm.com/images/logos/downloads/Git-Logo-2Color.png) found by Googling "git" images on 2017-10-14