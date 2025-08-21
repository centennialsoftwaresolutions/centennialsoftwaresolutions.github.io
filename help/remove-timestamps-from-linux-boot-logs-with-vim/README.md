# Remove Timestamps From Linux boot logs with Vim

This line replaces the values between \[ and \] with white space.

:%s/\\(\\\[\\).\*\\(\\\]\\)/\\1 \\2/g

**%** - find a replace on every line

**s** - search and replace

**\\(\\\[\\)** - select the first bracket, can then refer to it with \\1

**.\*** - all characters

**\\(\\\]\\)** - select the second bracket, can then refer to it with \\2

**g** - replace all instances on a line