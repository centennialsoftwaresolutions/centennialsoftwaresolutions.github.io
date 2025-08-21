# "Can you grab or delete between parentheses in vi/vim?"

![vim_logo_1](vim_logo_1.png)

This post extends a good stackoverflow \[[answer](https://stackoverflow.com/questions/405415/can-you-grab-or-delete-between-parentheses-in-vi-vim)\] answer to "**Can you grab or delete between parentheses in vi/vim?**" from by \[[hop](https://stackoverflow.com/users/3850/hop)\] (asked by \[[romandas](https://stackoverflow.com/users/50111/romandas)\]).

You'd like to transform :

```
        if ((argc < 3) || (argc > 4)) {
               
        }
```

...into:

```
        if (argc != 2) {

        }
```

...and your cursor is here:

```
        if ((argc < 3) || (argc > 4)) {
                  ^
        }
```

Type **v2i)c** to select everything between the outer parenthesis, but not the parenthesis, **c** to change it then type **argc != 2**, a.k.a. **v** enters visual mode, specify you want to go **2** levels of parenthesis up then **i)** to select everything between the block and **c** deletes everything selected and puts you into INSERT mode.

Use **a)** instead of **i)** to select everything in the block and the parenthesis.

Type **:help object-select** for help with this and related commands. Type **:q** to exit help.

**<u><span>References</span></u>**

-   Original stackoverflow post \[[link](https://stackoverflow.com/questions/405415/can-you-grab-or-delete-between-parentheses-in-vi-vim)\]
    
-   Vim image from \[[link](https://en.wikipedia.org/wiki/Vim_(text_editor))\]