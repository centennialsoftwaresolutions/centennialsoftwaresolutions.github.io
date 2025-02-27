# How do I find the MD5 SUM of a file on Windows?

![windows_logo](windows_logo.png)

This post shows you how to **find the MD5 SUM of a file on Windows** 10 Pro.

## Steps to **Find the MD5 SUM of a File on Windows**

**Step 1**: Open PowerShell

Press: **Windows Key + r**, Type: **powershell**

**Step 2**: Type:

```
Get-FileHash
"D:\installers\amd\2023.2\FPGAs_AdaptiveSoCs_Unified_2023.2_1013_2256.tar.gz" -Algorithm MD5
```

Example Output:

```
Algorithm       Hash
Path
---------       ----
----
MD5			   64D64E9B937B6FD5E98B41811C74AAB2
D:\installe...
```

## Reference

**Windows Version**:

From PowerShell or CMD, run:

```
PS C:\Users\Zach Pfeffer systeminfo | findstr /B /C:"OS Name" /B /C:"OS Version"
```

Output:

```
OS Name:                   Microsoft Windows 10 Pro
OS Version:                10.0.19045 N/A Build 19045
```

**Windows 10 Logo**:

[https://commons.wikimedia.org/wiki/File:Windows_logo_-_2012_%28dark_blue%29.svg](https://commons.wikimedia.org/wiki/File:Windows_logo_-_2012_(dark_blue).svg) 