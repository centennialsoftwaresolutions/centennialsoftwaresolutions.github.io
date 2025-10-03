# Call bitbake directly while inside the PetaLinux environment hack

```
petalinux-build -c "--version; bitbake -e"
```

or 

```
petalinux-build -c ''--version; bitbake -e'
```

# Why this works

In https://github.com/Xilinx/PetaLinux/blob/xlnx_rel_v2024.1/scripts/petalinux-build `"--version; bitbake -e"` gets assigned to `build_comp` unchanged. A  standard Python concatenation creates `bitbake_cmd`:

```
bitbake_cmd = 'bitbake %s' % build_comp
```

This is passed to `run_bitbakecmd`:

```
bitbake_utils.run_bitbakecmd(bitbake_cmd, proot, logfile=args.logfile, extraenv=None, shell=True)
```

Resulting in the call `bitbake --version; bitbake -e`. 