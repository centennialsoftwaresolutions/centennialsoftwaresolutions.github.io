# Single Line Bash Script Split Hack

![green_script_1](green_script_1.png)

This post lists a simple sed script that will split a bash script written in a single line.

**Note:** this script **is a hack**; it can produce some wrong output. I've posted it because I've found it helpful in splitting apart bash scripts that have been squashed into a single line. Its also written simply so you can change and extend it easily.

**The Script**

```
# re-indent bash
# call with sed -f sedscript <old >new
# http://www.grymoire.com/Unix/Sed.html#uh-16
s/ function /\n\nfunction /g
s/ fi /\nfi\n\n/g
s/ if \[ /\n\nif [ /g
s/; then /; then\n/g
s/ else / \nelse /g
s/ \([[:alnum:]_]\+\)=/\n\n\1=/g
s/export/\nexport/g
s/# /\n# /g
s/ for/\nfor/g
s/ while /\nwhile /g
s/ read /\nread /g
s/ trap /\ntrap /g
s/ sed /\nsed /g
s/ rm /\nrm /g
s/ chmod /\nchmod /g
```

Copy this and save it as sedscript. Call with **sed -f sedscript <**[**<u><span>oneline.sh</span></u>**](http://oneline.sh/) **>**[**<u><span>multiline.sh</span></u>**](http://multiline.sh/)

**<u><span>References</span></u>**

-   HTML Escape / Unescape at \[[<u><span>link</span></u>](https://www.freeformatter.com/html-escape.html)\]