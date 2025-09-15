# BitBake Overrides Guide

A quick reference for **overrides** in Yocto/BitBake: how they work, when they’re applied, and best practices.

---

## What Are Overrides?

Overrides let you define **different values for the same variable** depending on context (machine, distro, recipe, class, etc.).

BitBake maintains a special variable called `OVERRIDES` (colon-separated list of active tags).
If a variable is defined with a suffix that matches an entry in `OVERRIDES`, that definition applies.

Example:

```bitbake
EXTRA_OECONF = ""
EXTRA_OECONF:qemuarm = "--enable-arm"
EXTRA_OECONF:x86     = "--enable-x86"
```

If you build for `qemuarm`, BitBake expands:

```
EXTRA_OECONF = "--enable-arm"
```

---

## How Overrides Work

* Overrides are applied at **parse time**.
* `OVERRIDES` is a list like:

  ```
  qemuarm:class-target:linux:forcevariable
  ```
* Each `:suffix` in a variable assignment is checked against this list.
* Matching suffixes are applied, others are ignored.

---

## Common Overrides

| Override           | Meaning / Usage Example                                       |
| ------------------ | ------------------------------------------------------------- |
| `:pn`              | Per-recipe (`SRC_URI:pn-mypkg`)                               |
| `:class-target`    | Applied to target recipes (`DEPENDS:class-target`)            |
| `:class-native`    | Applied to native builds on the host (`DEPENDS:class-native`) |
| `:class-nativesdk` | Applied to SDK builds (`DEPENDS:class-nativesdk`)             |
| `:machine`         | Per-machine config (`EXTRA_OECONF:qemuarm`)                   |
| `:distro`          | Per-distro config (`PACKAGECONFIG:mydistro`)                  |
| `:virtclass`       | Legacy virtual classes override                               |
| Custom             | Extend `OVERRIDES` in config to add your own.                 |

---

## Examples

### Per-machine

```bitbake
EXTRA_OECONF = ""
EXTRA_OECONF:qemuarm = "--enable-arm-mode"
EXTRA_OECONF:qemux86 = "--enable-x86-mode"
```

### Per-recipe (`pn`)

```bitbake
SRC_URI = "git://example.com/common.git"
SRC_URI:pn-myrecipe = "git://example.com/special.git"
```

### Per-class

```bitbake
DEPENDS:class-target += "zlib"
DEPENDS:class-native += "python3"
```

### Per-distro

```bitbake
PACKAGECONFIG ??= ""
PACKAGECONFIG:mydistro = "featurex featurey"
```

---

## Debugging Overrides

See active overrides:

```bash
bitbake -e myrecipe | grep ^OVERRIDES=
```

Check how a variable expanded:

```bash
bitbake -e myrecipe | grep ^EXTRA_OECONF=
```

---

## Best Practices

1. Use overrides instead of conditionals in tasks (keeps logic at parse time).
2. Group per-machine, per-distro, per-class changes with overrides.
3. Always check `OVERRIDES` in your build environment if something didn’t apply.
4. Avoid hardcoding machine names directly in recipes if possible — prefer machine `.conf` files.
5. Use `.bbappend` with overrides to extend upstream recipes cleanly.
