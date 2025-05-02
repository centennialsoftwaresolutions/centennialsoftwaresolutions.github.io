![windows_10_logo](windows_10_logo.png)

This post lists Windows 10 search examples to help you find what you're looking for.

## Examples

Find:

...PowerPoint files:

```
System.FileExtension:=".pptx"
```

...a filename containing "status"

```
System.FileName:~="status"
```

...files modified today

```
System.ItemDate:System.StructuredQueryType.DateTime#Today
```

...files modified yesterday

```
System.ItemDate:System.StructuredQueryType.DateTime#Yesterday
```

...files modified this month

```
System.ItemDate:System.StructuredQueryType.DateTime#ThisMonth
```

...files modified between Feb 1st, 2021 and the 4th that are between 5 KB ad 10 MB

```
System.ItemDate:2/1/21..2/4/21 System.Size:5kb..10mb
```

## References

Using Advanced Query Syntax Programmatically from docs.microsoft.com [[link](https://docs.microsoft.com/en-us/windows/win32/search/-search-3x-advancedquerysyntax?redirectedfrom=MSDN)]

Windows 10 logo from commons.wikimedia.org @ [[link](https://commons.wikimedia.org/wiki/File:Windows_10_Logo.svg)]

How to Search for Text Inside of Any File Using Windows Search from www.howtogeek.com @ [[link](https://www.howtogeek.com/99406/how-to-search-for-text-inside-of-any-file-using-windows-search/)]