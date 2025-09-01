# info info

This post lists all of the command keys for info, e.g. how to move around an info 'node'

To get this info on a Linux system type:

```
info info
```

The type 'h'

```
Basic Info command keys

x           Close this help window.
q           Quit Info altogether.
H           Invoke the Info tutorial.

Up          Move up one line.
Down        Move down one line.
DEL         Scroll backward one screenful.
SPC         Scroll forward one screenful.
Home        Go to the beginning of this node.
End         Go to the end of this node.

TAB         Skip to the next hypertext link.
RET         Follow the hypertext link under the cursor.
l           Go back to the last node seen in this window.

[           Go to the previous node in the document.
]           Go to the next node in the document.
p           Go to the previous node on this level.
n           Go to the next node on this level.
u           Go up one level.
t           Go to the top node of this document.
d           Go to the main `directory' node.

1...9       Pick the first...ninth item in this node's menu.
0           Pick the last item in this node's menu.
m           Pick a menu item specified by name.
r           Follow a cross reference specified by name.
g           Go to a node specified by name.

s           Search forward for a specified string.
{           Search for previous occurrence.
}           Search for next occurrence.
i           Search for a specified string in the index, and
              select the node referenced by the first entry found.
I           Synthesize menu of matching index entries.

C-g         Cancel the current operation.

---------------------
```

```
Commands available in Info windows:

C-a     (beginning-of-line)Move to the start of the line
C-b     (backward-char)Move backward a character
C-e     (end-of-line)Move to the end of the line
C-f     (forward-char)Move forward a character
C-g     (abort-key)Cancel current operation
C-h     (get-help-window)Display help message
TAB     (move-to-next-xref)Move to the next cross reference
LFD     (select-reference-this-line)
     Select reference or menu item appearing on this line
C-l     (redraw-display)Redraw the display
RET     (select-reference-this-line)
     Select reference or menu item appearing on this line
C-n     (next-line)Move down to the next line
C-p     (prev-line)Move up to the previous line
C-r     (isearch-backward)
     Search interactively for a string as you type it
C-s     (isearch-forward)
     Search interactively for a string as you type it
C-u     (universal-argument)
     Start (or multiply by 4) the current numeric argument
C-v     (scroll-forward-page-only)
     Scroll forward in this window staying within node
C-x C-b (list-visited-nodes)
     Make a window containing a menu of all of the currently visited nodes
C-x C-c (quit)Quit using Info
C-x C-f (view-file)Read the name of a file and select it
C-x C-g (abort-key)Cancel current operation
C-x C-v (view-file)Read the name of a file and select it
C-x 0   (delete-window)Delete the current window
C-x 1   (keep-one-window)Delete all other windows
C-x 2   (split-window)Split the current window
C-x A .. C-x M  (do-lowercase-version)
     Run command bound to this key's lowercase variant
C-x N   (search-previous)
     Repeat last search in the reverse direction
C-x O .. C-x Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
```

```
C-x ^   (grow-window)Grow (or shrink) this window
C-x b   (select-visited-node)
     Select a node which has been previously visited in a visible window
C-x f   (all-files)Show all matching files
C-x k   (kill-node)Kill this node
C-x n   (search-next)
     Repeat last search in the same direction
C-x o   (next-window)Select the next window
C-x t   (tile-windows)
     Divide the available screen space among the visible windows
C-x w   (toggle-wrap)
     Toggle the state of line wrapping in the current window
C-x M-A .. C-x M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC C-f (show-footnotes)
     Show the footnotes associated with this node in another window
ESC C-g (abort-key)Cancel current operation
ESC TAB (move-to-prev-xref)Move to the previous cross reference
ESC C-v (scroll-other-window)Scroll the other window
ESC ESC A .. ESC ESC N  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC Up  (prev-line)Move up to the previous line
ESC Down        (next-line)Move down to the next line
ESC Right       (forward-word)Move forward a word
ESC Left        (backward-word)Move backward a word
ESC ESC O E .. ESC ESC O Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC O M-A .. ESC ESC O M-Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC P .. ESC ESC Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC [ 5 A .. ESC ESC [ 5 Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC PgUp        (scroll-other-window-backward)Scroll the other window backward
ESC ESC [ 5 M-A .. ESC ESC [ 5 M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC [ 6 A .. ESC ESC [ 6 Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC PgDn        (scroll-other-window)Scroll the other window
ESC ESC [ 6 M-A .. ESC ESC [ 6 M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
```

```
ESC ESC [ A     (prev-line)Move up to the previous line
ESC ESC [ B     (next-line)Move down to the next line
ESC ESC [ C     (forward-word)Move forward a word
ESC ESC [ D     (backward-word)Move backward a word
ESC ESC [ E .. ESC ESC [ Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC [ M-A .. ESC ESC [ M-Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC M-A .. ESC ESC M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC -   (add-digit-to-numeric-arg)
     Add this digit to the current numeric argument
ESC 0 .. ESC 9  (add-digit-to-numeric-arg)
     Add this digit to the current numeric argument
ESC <   (beginning-of-node)Move to the start of this node
ESC >   (end-of-node)Move to the end of this node
ESC A .. ESC N  (do-lowercase-version)
     Run command bound to this key's lowercase variant
Up      (prev-line)Move up to the previous line
Down    (next-line)Move down to the next line
Right   (forward-char)Move forward a character
Left    (backward-char)Move backward a character
ESC O E (do-lowercase-version)
     Run command bound to this key's lowercase variant
End     (end-of-node)Move to the end of this node
ESC O G (do-lowercase-version)
     Run command bound to this key's lowercase variant
Home    (beginning-of-node)Move to the start of this node
ESC O I .. ESC O Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC O M-A .. ESC O M-Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC P .. ESC Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC [ 3 A .. ESC [ 3 Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
DEL     (scroll-backward)Scroll backward in this window
ESC [ 3 M-A .. ESC [ 3 M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC [ 5 A .. ESC [ 5 Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
```

```
ESC [ 6 A .. ESC [ 6 Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
PgDn    (scroll-forward)Scroll forward in this window
ESC [ 6 M-A .. ESC [ 6 M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC [ A (prev-line)Move up to the previous line
ESC [ B (next-line)Move down to the next line
ESC [ C (forward-char)Move forward a character
ESC [ D (backward-char)Move backward a character
ESC [ E .. ESC [ Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC [ M-A .. ESC [ M-Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC b   (backward-word)Move backward a word
ESC f   (forward-word)Move forward a word
ESC r   (move-to-window-line)
     Move the cursor to a specific line of the window
ESC v   (scroll-backward-page-only)
     Scroll backward in this window staying within node
ESC x   (execute-command)
     Read a command name in the echo area and execute it
ESC M-A .. ESC M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
SPC     (scroll-forward)Scroll forward in this window
,       (next-index-match)
     Go to the next matching index item from the last `i' command
/       (search)Read a string and search for it
0       (last-menu-item)
     Select the last item in this node's menu
1 .. 9  (menu-digit)Select this menu item
<       (first-node)Select the first node in this file
=       (display-file-info)
     Show full file name of node being displayed
>       (last-node)Select the last node in this file
?       (get-help-window)Display help message
A .. F  (do-lowercase-version)
     Run command bound to this key's lowercase variant
G       (menu-sequence)
     Read a list of menus starting from dir and follow them
```

```
H       (get-info-help-node)Visit Info node `(info)Help'
I       (virtual-index)
     List all matches of a string in the index
J .. N  (do-lowercase-version)
     Run command bound to this key's lowercase variant
O       (goto-invocation-node)
     Find the node describing program invocation
P .. Q  (do-lowercase-version)
     Run command bound to this key's lowercase variant
R       (toggle-regexp)
     Toggle the usage of regular expressions in searches
S       (search-case-sensitively)
     Read a string and search for it case-sensitively
T .. Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
[       (global-prev-node)
     Move backwards or up through node structure
]       (global-next-node)
     Move forwards or down through node structure
b       (beginning-of-node)Move to the start of this node
d       (dir-node)Select the node `(dir)'
e       (end-of-node)Move to the end of this node
f       (xref-item)
     Read a footnote or cross reference and select its node
g       (goto-node)Read a node name and select it
h       (get-help-window)Display help message
i       (index-search)
     Look up a string in the index for this file
l       (history-node)Select the most recently selected node
m       (menu-item)Read a menu item and select its node
n       (next-node)Select the Next node
p       (prev-node)Select the Prev node
q       (quit)Quit using Info
r       (xref-item)
     Read a footnote or cross reference and select its node
s       (search)Read a string and search for it
t       (top-node)Select the node `Top' in this file
u       (up-node)Select the Up node
x       (delete-window)Delete the current window
{       (search-previous)
     Repeat last search in the reverse direction
}       (search-next)
     Repeat last search in the same direction
```

```
DEL     (scroll-backward)Scroll backward in this window
M-C-f   (show-footnotes)
     Show the footnotes associated with this node in another window
M-C-g   (abort-key)Cancel current operation
M-TAB   (move-to-prev-xref)Move to the previous cross reference
M-C-v   (scroll-other-window)Scroll the other window
M--     (add-digit-to-numeric-arg)
     Add this digit to the current numeric argument
M-0 .. M-9      (add-digit-to-numeric-arg)
     Add this digit to the current numeric argument
M-<     (beginning-of-node)Move to the start of this node
M->     (end-of-node)Move to the end of this node
M-A .. M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
M-b     (backward-word)Move backward a word
M-f     (forward-word)Move forward a word
M-r     (move-to-window-line)
     Move the cursor to a specific line of the window
M-v     (scroll-backward-page-only)
     Scroll backward in this window staying within node
M-x     (execute-command)
     Read a command name in the echo area and execute it
---------------------

Commands available in the echo area:

C-a     (echo-area-beg-of-line)Move to the start of this line
C-b     (echo-area-backward)Move backward a character
C-d     (echo-area-delete)Delete the character under the cursor
C-e     (echo-area-end-of-line)Move to the end of this line
C-f     (echo-area-forward)Move forward a character
C-g     (echo-area-abort)Cancel or quit operation
C-h     (echo-area-rubout)Delete the character behind the cursor
TAB     (echo-area-complete)Insert completion
LFD     (echo-area-newline)
     Accept (or force completion of) this line
C-k     (echo-area-kill-line)Kill to the end of the line
C-l     (redraw-display)Redraw the display
RET     (echo-area-newline)
     Accept (or force completion of) this line
C-q     (echo-area-quoted-insert)Insert next character verbatim
```

```
C-t     (echo-area-transpose-chars)Transpose characters at point
C-u     (universal-argument)
     Start (or multiply by 4) the current numeric argument
C-x ESC A .. C-x ESC Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
C-x ESC [ 3 A .. C-x ESC [ 3 Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
C-x DEL (echo-area-backward-kill-line)Kill to the beginning of the line
C-x ESC [ 3 M-A .. C-x ESC [ 3 M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
C-x ESC [ A .. C-x ESC [ Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
C-x ESC [ M-A .. C-x ESC [ M-Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
C-x ESC M-A .. C-x ESC M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
C-x A .. C-x Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
C-x o   (next-window)Select the next window
C-x DEL (echo-area-backward-kill-line)Kill to the beginning of the line
C-x M-A .. C-x M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
C-y     (echo-area-yank)Yank back the contents of the last kill
ESC C-g (echo-area-abort)Cancel or quit operation
ESC TAB (echo-area-tab-insert)Insert a TAB character
ESC C-v (echo-area-scroll-completions-window)Scroll the completions window
ESC ESC A .. ESC ESC N  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC Up .. ESC Down      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC Right       (echo-area-forward-word)Move forward a word
ESC Left        (echo-area-backward-word)Move backward a word
ESC ESC O E .. ESC ESC O Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC O M-A .. ESC ESC O M-Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC P .. ESC ESC Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC [ 3 A .. ESC ESC [ 3 Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC DEL (echo-area-backward-kill-word)Kill the word preceding the cursor
ESC ESC [ 3 M-A .. ESC ESC [ 3 M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
```

```
ESC ESC [ A .. ESC ESC [ B      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC [ C     (echo-area-forward-word)Move forward a word
ESC ESC [ D     (echo-area-backward-word)Move backward a word
ESC ESC [ E .. ESC ESC [ Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC [ M-A .. ESC ESC [ M-Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC ESC M-A .. ESC ESC M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC -   (add-digit-to-numeric-arg)
     Add this digit to the current numeric argument
ESC 0 .. ESC 9  (add-digit-to-numeric-arg)
     Add this digit to the current numeric argument
ESC ?   (echo-area-possible-completions)List possible completions
ESC A .. ESC N  (do-lowercase-version)
     Run command bound to this key's lowercase variant
Up .. Down      (do-lowercase-version)
     Run command bound to this key's lowercase variant
Right   (echo-area-forward)Move forward a character
Left    (echo-area-backward)Move backward a character
ESC O E (do-lowercase-version)
     Run command bound to this key's lowercase variant
End     (echo-area-end-of-line)Move to the end of this line
ESC O G (do-lowercase-version)
     Run command bound to this key's lowercase variant
Home    (echo-area-beg-of-line)Move to the start of this line
ESC O I .. ESC O Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC O M-A .. ESC O M-Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC P .. ESC Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC [ 3 A .. ESC [ 3 Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
DEL     (echo-area-rubout)Delete the character behind the cursor
ESC [ 3 M-A .. ESC [ 3 M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC [ A .. ESC [ B      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC [ C (echo-area-forward)Move forward a character
```

```
ESC [ D (echo-area-backward)Move backward a character
ESC [ E .. ESC [ Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC [ M-A .. ESC [ M-Z  (do-lowercase-version)
     Run command bound to this key's lowercase variant
ESC b   (echo-area-backward-word)Move backward a word
ESC d   (echo-area-kill-word)Kill the word following the cursor
ESC f   (echo-area-forward-word)Move forward a word
ESC y   (echo-area-yank-pop)Yank back a previous kill
ESC DEL (echo-area-backward-kill-word)Kill the word preceding the cursor
ESC M-A .. ESC M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
SPC     (echo-area-complete)Insert completion
! .. >  (echo-area-insert)Insert this character
?       (echo-area-possible-completions)List possible completions
@ .. ~  (echo-area-insert)Insert this character
DEL     (echo-area-rubout)Delete the character behind the cursor
M-C-g   (echo-area-abort)Cancel or quit operation
M-TAB   (echo-area-tab-insert)Insert a TAB character
M-C-v   (echo-area-scroll-completions-window)Scroll the completions window
M--     (add-digit-to-numeric-arg)
     Add this digit to the current numeric argument
M-0 .. M-9      (add-digit-to-numeric-arg)
     Add this digit to the current numeric argument
M-?     (echo-area-possible-completions)List possible completions
M-A .. M-Z      (do-lowercase-version)
     Run command bound to this key's lowercase variant
M-b     (echo-area-backward-word)Move backward a word
M-d     (echo-area-kill-word)Kill the word following the cursor
M-f     (echo-area-forward-word)Move forward a word
M-y     (echo-area-yank-pop)Yank back a previous kill
M-DEL   (echo-area-backward-kill-word)Kill the word preceding the cursor
---------------------
```

```
The following commands can only be invoked via M-x:

M-x scroll-forward-set-window
     Scroll forward in this window and set default window size
M-x scroll-forward-page-only-set-window
     Scroll forward in this window staying within node and set default window size
M-x scroll-backward-set-window
     Scroll backward in this window and set default window size
M-x scroll-backward-page-only-set-window
     Scroll backward in this window staying within node and set default window size
M-x down-line
     Scroll down by lines
M-x up-line
     Scroll up by lines
M-x scroll-half-screen-down
     Scroll down by half screen size
M-x scroll-half-screen-up
     Scroll up by half screen size
M-x prev-window
     Select the previous window
M-x find-menu
     Move to the start of this node's menu
M-x visit-menu
     Visit as many menu items at once as possible
M-x man
     Read a manpage reference and select it
M-x print-node
     Pipe the contents of this node through INFO_PRINT_COMMAND
M-x search-backward
     Read a string and search backward for it
M-x numeric-arg-digit-loop
     Internally used by C-u
M-x echo-area-insert
     Insert this character
M-x describe-key
     Print documentation for KEY
M-x where-is
     Show what to type to execute a given command
M-x describe-command
     Read the name of an Info command and describe it
M-x set-screen-height
     Set the height of the displayed window
M-x index-apropos
     Grovel all known info file's indices for a string and build a menu
M-x describe-variable
     Explain the use of a variable
M-x set-variable
     Set the value of an Info variable
```