# Install and Remove the WSL Ubuntu-22.04 Distribution

This post shows how to **Install and Remove the WSL Ubuntu-22.04 Distribution**. It also lists the output of wsl --help.

## Prerequisites

Run [Get WSL](https://www.css-techhelp.com/post/get-wsl-enabling-and-disabling-microsoft-windows-subsystem-linux-in-powershell-a-comprehensive-guide) 

## Computer Configuration

```
wsl --status
# Default Distribution: docker-desktop-data
# Default Version: 2

wsl -v
# WSL version: 1.2.5.0
# Kernel version: 5.15.90.1
# WSLg version: 1.0.51
# MSRDC version: 1.2.3770
# Direct3D version: 1.608.2-61064218
# DXCore version: 10.0.25131.1002-220531-1700.rs-onecore-base2-hyp
# Windows version: 10.0.19045.2846
```

## Install and Remove the WSL Ubuntu-22.04 Distribution

\# Run PowerShell

```
$env:WSL_UTF8=1
wsl --help | more
```

\# Save help open it in Windows

```
wsl --help > wsl.help
explorer.exe .
notepade wsl.help
```

\# Get the available distributions:

```
wsl --list --online
```

\# Output

```
# The following is a list of valid distributions that can be installed.
# Install using 'wsl.exe --install <Distro>'.
# 
# NAME                                   FRIENDLY NAME
# Ubuntu                                 Ubuntu
# Debian                                 Debian GNU/Linux
# kali-linux                             Kali Linux Rolling
# Ubuntu-18.04                           Ubuntu 18.04 LTS
# Ubuntu-20.04                           Ubuntu 20.04 LTS
# Ubuntu-22.04                           Ubuntu 22.04 LTS
# OracleLinux_7_9                        Oracle Linux 7.9
# OracleLinux_8_7                        Oracle Linux 8.7
# OracleLinux_9_1                        Oracle Linux 9.1
# SUSE-Linux-Enterprise-Server-15-SP4    SUSE Linux Enterprise Server 15 SP4
# openSUSE-Leap-15.4                     openSUSE Leap 15.4
# openSUSE-Tumbleweed                    openSUSE Tumbleweed
```

\# For the next command, when prompted

\# Use: username for the username

\# Use: password for the password

```
wsl.exe --install --d Ubuntu-22.04
```

\# Output:

```
# Installing: Ubuntu 22.04 LTS
# Ubuntu 22.04 LTS has been installed.
# Launching Ubuntu 22.04 LTS...
# Installing, this may take a few minutes...
# Please create a default UNIX user account. The username does not need to match your Windows username.
# For more information visit: https://aka.ms/wslusers
# Enter new UNIX username: username
# New password:
# Retype new password:
# passwd: password updated successfully
# The operation completed successfully.
# Installation successful!
# To run a command as administrator (user "root"), use "sudo <command>".
# See "man sudo_root" for details.
# 
# Welcome to Ubuntu 22.04.2 LTS (GNU/Linux 5.15.90.1-microsoft-standard-WSL2 x86_64)
# 
#  * Documentation:  https://help.ubuntu.com
#  * Management:     https://landscape.canonical.com
#  * Support:        https://ubuntu.com/advantage
# 
# 
# This message is shown once a day. To disable it please create the
# /home/username/.hushlogin file.
```

\# Get the Window's path to HOME, run this at the distributions prompt:

```
explorer.exe .
```

\# You should see something like:

```
# \\wsl.localhost\Ubuntu-22.04\home\username
```

\# Set the default explicitly to work around this [<u><span>bug</span></u>](https://www.css-techhelp.com/post/wsl-error-3-wsl-8-error-createprocessentrycommon-370-getpwuid-0-failed-2)

\# Get out of the distribution

```
exit
```

\# See the default

```
wsl -l
```

\# Output

```
# Windows Subsystem for Linux Distributions:
# docker-desktop-data (Default) <------ NOTICE
# Ubuntu-22.04
# docker-desktop
```

\# Set the default

```
wsl --set-default Ubuntu-22.04
```

\# Output

```
# The operation completed successfully.
```

\# See the default

```
wsl -l
```

\# Output

```
# Windows Subsystem for Linux Distributions:
# Ubuntu-22.04 (Default) <------ NOTICE
# docker-desktop-data
# docker-desktop
```

\# Test entering and exiting wsl

```
wsl
```

\# Output

```
# To run a command as administrator (user "root"), use "sudo <command>".
# See "man sudo_root" for details.
#
# username@LAPTOP-3MCNKKJO:/mnt/c/Users/Zach Pfeffer$
```

\# Run to test

```
exit
wsl
exit
```

\# Unregister the distribution and delete the root filesystem.

```
wsl.exe --unregister Ubuntu-22.04
```

\# Output

```
# Unregistering.
# The operation completed successfully.
```

\# \\\\wsl.localhost\\Ubuntu-22.04\\home\\username is now gone

## wsl --help

```
Copyright (c) Microsoft Corporation. All rights reserved.
For privacy information about this product please visit https://aka.ms/privacy.

Usage: wsl.exe [Argument] [Options...] [CommandLine]

Arguments for running Linux binaries:

    If no command line is provided, wsl.exe launches the default shell.

    --exec, -e <CommandLine>
        Execute the specified command without using the default Linux shell.

    --shell-type <Type>
        Execute the specified command with the provided shell type.

        Types:
            standard
                Execute the specified command using the default Linux shell.

            login
                Execute the specified command using the default Linux shell as a login shell.

            none
                Execute the specified command without using the default Linux shell.

    --
        Pass the remaining command line as-is.

Options:
    --cd <Directory>
        Sets the specified directory as the current working directory.
        If ~ is used the Linux user's home path will be used. If the path begins
        with a / character, it will be interpreted as an absolute Linux path.
        Otherwise, the value must be an absolute Windows path.

    --distribution, -d <Distro>
        Run the specified distribution.

    --user, -u <UserName>
        Run as the specified user.

    --system
        Launches a shell for the system distribution.

Arguments for managing Windows Subsystem for Linux:

    --help
        Display usage information.

    --debug-shell
        Open a WSL2 debug shell for diagnostics purposes.

    --event-viewer
        Opens the application view of the Windows Event Viewer.

    --install [Distro] [Options...]
        Install a Windows Subsystem for Linux distribution.
        For a list of valid distributions, use 'wsl.exe --list --online'.

        Options:
            --no-launch, -n
                Do not launch the distribution after install.

            --web-download
                Download the distribution from the internet instead of the Microsoft Store.

    --mount <Disk>
        Attaches and mounts a physical or virtual disk in all WSL 2 distributions.

        Options:
            --vhd
                Specifies that <Disk> refers to a virtual hard disk.

            --bare
                Attach the disk to WSL2, but don't mount it.

            --name <Name>
                Mount the disk using a custom name for the mountpoint.

            --type <Type>
                Filesystem to use when mounting a disk, if not specified defaults to ext4.

            --options <Options>
                Additional mount options.

            --partition <Index>
                Index of the partition to mount, if not specified defaults to the whole disk.

    --release-notes
        Opens a web browser to view the WSL release notes page.

    --set-default-version <Version>
        Changes the default install version for new distributions.

    --shutdown
        Immediately terminates all running distributions and the WSL 2
        lightweight utility virtual machine.

    --status
        Show the status of Windows Subsystem for Linux.

    --unmount [Disk]
        Unmounts and detaches a disk from all WSL2 distributions.
        Unmounts and detaches all disks if called without argument.

    --update
        Update the Windows Subsystem for Linux package.

        Options:
            --web-download
                Download the update from the internet instead of the Microsoft Store.

            --pre-release
                Download a pre-release version if available. Implies --web-download.

    --version, -v
        Display version information.

Arguments for managing distributions in Windows Subsystem for Linux:

    --export <Distro> <FileName> [Options]
        Exports the distribution to a tar file.
        The filename can be - for standard output.

        Options:
            --vhd
                Specifies that the distribution should be exported as a .vhdx file.

    --import <Distro> <InstallLocation> <FileName> [Options]
        Imports the specified tar file as a new distribution.
        The filename can be - for standard input.

        Options:
            --version <Version>
                Specifies the version to use for the new distribution.

            --vhd
                Specifies that the provided file is a .vhdx file, not a tar file.
                This operation makes a copy of the .vhdx file at the specified install location.

    --import-in-place <Distro> <FileName>
        Imports the specified .vhdx file as a new distribution.
        This virtual hard disk must be formatted with the ext4 filesystem type.

    --list, -l [Options]
        Lists distributions.

        Options:
            --all
                List all distributions, including distributions that are
                currently being installed or uninstalled.

            --running
                List only distributions that are currently running.

            --quiet, -q
                Only show distribution names.

            --verbose, -v
                Show detailed information about all distributions.

            --online, -o
                Displays a list of available distributions for install with 'wsl.exe --install'.

    --set-default, -s <Distro>
        Sets the distribution as the default.

    --set-version <Distro> <Version>
        Changes the version of the specified distribution.

    --terminate, -t <Distro>
        Terminates the specified distribution.

    --unregister <Distro>
        Unregisters the distribution and deletes the root filesystem.
```

## References

Windows 10 Logo

Tux Logo

![Tux_on_windows_logo_1](Tux_on_windows_logo_1.png)