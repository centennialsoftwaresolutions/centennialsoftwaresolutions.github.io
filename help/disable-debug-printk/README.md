# Disable debug printk

![tux_logo](tux_logo.png)

This post lists the command that disables debug messages from getting printed to the console.

Execute this on the console to stop the messages:

```
echo 6 > /proc/sys/kernel/printk
```

Execute this on the console to start the messages:

```
echo 7 > /proc/sys/kernel/printk
```

Execute this to read the current level:

```
cat /proc/sys/kernel/printk
```

You'll see four numbers. The first number is the current log level. You set this. The second is the default log level. The third is the lowest value you can set the log level, typically 1 and the last is what the log level is at boot.

Reference

1\. What "6" (and the other numbers mean) is described here: [link](http://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/include/linux/kern_levels.h?id=HEAD). For reference (table listed at [link](http://elinux.org/Debugging_by_printing)):

| Name         | String | Meaning                                                      | alias function                         |
| :----------- | :----- | :----------------------------------------------------------- | :------------------------------------- |
| KERN_EMERG   | "0"    | Emergency messages, system is about to crash or is unstable  | pr_emerg                               |
| KERN_ALERT   | "1"    | Something bad happened and action must be taken immediately  | pr_alert                               |
| KERN_CRIT    | "2"    | A critical condition occurred like a serious hardware/software failure | pr_crit                                |
| KERN_ERR     | "3"    | An error condition, often used by drivers to indicate difficulties with the hardware | pr_err                                 |
| KERN_WARNING | "4"    | A warning, meaning nothing serious by itself but might indicate problems | pr_warning                             |
| KERN_NOTICE  | "5"    | Nothing serious, but notably nevertheless. Often used to report security events. | pr_notice                              |
| KERN_INFO    | "6"    | Informational message e.g. startup information at driver initialization | pr_info                                |
| KERN_DEBUG   | "7"    | Debug messages                                               | pr_debug, pr_devel if DEBUG is defined |
| KERN_DEFAULT | "d"    | The default kernel loglevel                                  |                                        |
| KERN_CONT    | ""     | "continued" line of log printout (only done after a line that had no enclosing \n) [[1\]](http://lwn.net/Articles/252651/) | pr_cont                                |

2\. Styling tables @ [link](http://www.w3schools.com/cSS/css_table.asp).

3\. Escape HTML @ [link](http://www.freeformatter.com/html-escape.html#ad-output).

4\. Tux from [link](http://en.wikipedia.org/wiki/Tux) (found via Google image search).