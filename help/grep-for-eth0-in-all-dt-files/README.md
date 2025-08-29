# Find "eth0" in all "*.dt*" files

![tux_logo](tux_logo.png)

**Post Description**

This posts gives a fast and a slow way to find eth0 in all "\*.dt\*" files under the current directory. You may use this to find the string "eth0" in device tree files.

```
 time find . -name '*.dt*' -print0 | xargs --null grep -Hi 'eth0'
```

Fastreal 0m0.139s 

user 0m0.067s 

sys 0m0.075s

Slow

```
time find . -type f -name "*.dt*" -exec grep -Hi 'eth0' {} \;
```

real 0m2.432s 

user 0m1.816s 

sys 0m0.639s

**Command Line Options Explained**

[grep](http://www.gnu.org/software/grep/manual/grep.html#Matching-Control)

**\-H**

Print the file name for each match. This is the default when there is more than one file to search.

**\--ignore-case**

Ignore case distinctions, so that characters that differ only in case match each other. Although this is straightforward when letters differ in case only via lowercase-uppercase pairs, the behavior is unspecified in other situations. For example, uppercase “S” has an unusual lowercase counterpart “ſ” (Unicode character U+017F, LATIN SMALL LETTER LONG S) in many locales, and it is unspecified whether this unusual character matches “S” or “s” even though uppercasing it yields “S”. Another example: the lowercase German letter “ß” (U+00DF, LATIN SMALL LETTER SHARP S) is normally capitalized as the two-character string “SS” but it does not match “SS”, and it might not match the uppercase letter “ẞ” (U+1E9E, LATIN CAPITAL LETTER SHARP S) even though lowercasing the latter yields the former.

\-y is an obsolete synonym that is provided for compatibility. (-i is specified by POSIX.)

find

[xargs](http://www.gnu.org/software/findutils/manual/html_node/find_html/xargs-options.html)

**\--null**

Input file names are terminated by a null character instead of by whitespace, and any quotes and backslash characters are not considered special (every character is taken literally). Disables the end of file string, which is treated like any other argument.

[find](http://www.gnu.org/software/findutils/manual/html_mono/find.html)

**\-print0**

Print the entire file name on the standard output, followed by a null character.

Good Google search to find command line options:

"site:gnu.org grep"

**Machine MHz**

```
build $ cat /proc/cpuinfo | grep "MHz"
cpu MHz		: 2700.000
cpu MHz		: 2700.000
cpu MHz		: 2700.000
cpu MHz		: 2700.000
cpu MHz		: 2700.000
cpu MHz		: 2700.000
cpu MHz		: 2700.000
cpu MHz		: 2700.000
```

**Reference**

Tux from [link](http://en.wikipedia.org/wiki/Tux) (found via Google image search).