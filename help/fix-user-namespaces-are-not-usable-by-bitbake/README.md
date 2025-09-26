# ERROR: User namespaces are not usable by BitBake (AppArmor issue)

## Cause

Ubuntu 24.04 introduces stricter defaults for **unprivileged user namespaces**. BitBake relies on user namespaces for sandboxing. When AppArmor blocks them, BitBake fails with:

```
ERROR: User namespaces are not usable by BitBake, possibly due to AppArmor.
```

------

## One-Time Fix

As noted in the [Ubuntu 24.04 LTS release notes](https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890#unprivileged-user-namespace-restrictions):

```
sudo su
echo 0 > /proc/sys/kernel/apparmor_restrict_unprivileged_userns
exit
```

or:

```
echo 0 | sudo tee /proc/sys/kernel/apparmor_restrict_unprivileged_userns
```

------

## Persistent Fix

1. Create `/etc/sysctl.d/60-apparmor-namespace.conf` with the following content:

   ```
   kernel.apparmor_restrict_unprivileged_userns=0
   ```

2. Reboot.

------

## Verification

To confirm the setting has been applied:

```bash
cat /proc/sys/kernel/apparmor_restrict_unprivileged_userns
```

If the value is `0`, unprivileged user namespaces are allowed and BitBake should work again.

------

## Environment / Error Trigger

- Run `petalinux-build` from **PetaLinux Tools 2025.1**
- Host: Ubuntu **24.04.3** running in a VMWare VM

------

## Full Error Output

```bash
demo@demo:~/zcu102_petalinux/xilinx-zcu102-xsct-2025.1$ petalinux-build 
[INFO] Building project
[INFO] Bitbake is not available, some functionality may be reduced.
[INFO] Using HW file: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/project-spec/hw-description/system.xsa
[INFO] Getting Platform info from HW file
[INFO] Silentconfig project
[INFO] Silentconfig rootfs
[INFO] Generating configuration files
[INFO] Generating workspace directory
NOTE: Starting bitbake server...
NOTE: Started PRServer with DBfile: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/build/cache/prserv.sqlite3, Address: 127.0.0.1:46271, PID: 17613
INFO: Specified workspace already set up, leaving as-is
[INFO] bitbake petalinux-image-minimal
NOTE: Started PRServer with DBfile: /home/demo/zcu102_petalinux/xilinx-zcu102-xsct-2025.1/build/cache/prserv.sqlite3, Address: 127.0.0.1:34731, PID: 17673
WARNING: XSCT has been deprecated. It will still be available for several releases. In the future, it's recommended to start new projects with SDT workflow.
ERROR: User namespaces are not usable by BitBake, possibly due to AppArmor.
See https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890#unprivileged-user-namespace-restrictions for more information.

Summary: There was 1 WARNING message.
Summary: There was 1 ERROR message, returning a non-zero exit code.
[ERROR] Command bitbake petalinux-image-minimal failed

```