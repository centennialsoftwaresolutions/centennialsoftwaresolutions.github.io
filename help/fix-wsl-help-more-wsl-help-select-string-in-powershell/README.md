# Fix [wsl --help | more] & [wsl --help | Select-String] in PowerShell

![Tux_on_winfows_logo](Tux_on_winfows_logo.png)

By default wsl outputs UTF-16LE. This causes issues when piping output to **more or Select-String**. This post describes a fix. **TL;DR** Set $env:WSL\_UTF8=1

## <u><span>Issue</span></u>

Typing:

```
wsl --help | more
```

...you see:

```
C
o
r
p
o
r
a
t
i
o
n
.

A
l
l

-- More  --
```

## <u><span>Fix</span></u>

Run this to fix:

```
$env:WSL_UTF8=1
```

These work now:

```
wsl --help | more
```

```
wsl --help | Select-String "Display"
```

Revert back with the following:

```
$env:WSL_UTF8=0 
```

## <u><span>Environment</span></u>

```
systeminfo /fo csv | ConvertFrom-Csv | select OS*, System*, Hotfix* | Format-List -Property 'OS Version'
# OS Version : 10.0.19045 N/A Build 19045
```

```
$PSVersionTable
# Name                           Value
# ----                           -----
# PSVersion                      5.1.19041.2673
# PSEdition                      Desktop
# PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
# BuildVersion                   10.0.19041.2673
# CLRVersion                     4.0.30319.42000
# WSManStackVersion              3.0
# PSRemotingProtocolVersion      2.3
# SerializationVersion           1.1.0.1
```

```
wsl --version | Select-String "WSL version"
# WSL version: 1.2.5.0
```

## <u><span>References</span></u>

wsl.exe outputting unicode to stdout [#4607](https://www.centennialsoftwaresolutions.com/blog/hashtags/4607)

https://github.com/microsoft/WSL/issues/4607 

wsl release with WSL_UTF8=1

https://github.com/microsoft/WSL/releases/tag/0.64.0 

about_Character_Encoding

https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-7.3 

UTF-16

https://en.wikipedia.org/wiki/UTF-16 

Windows 10 Logo

[https://commons.wikimedia.org/wiki/File:Windows_logo_-_2012_%28dark_blue%29.svg](https://commons.wikimedia.org/wiki/File:Windows_logo_-_2012_(dark_blue).svg) 

Tux Logo

Tux (mascot). (2023, April 10). In *Wikipedia*. https://en.wikipedia.org/wiki/Tux_(mascot) 

[https://en.wikipedia.org/wiki/Tux_%28mascot%29#/media/File:Tux.png](https://en.wikipedia.org/wiki/Tux_(mascot)#/media/File:Tux.png) 