# Top 20 BitBake Variables

## Recipe identity

1. **`PN`** – Package name (usually recipe filename without version).
2. **`PV`** – Package version.
3. **`PR`** – Recipe revision (default `r0`).
4. **`P`** – Combination of `PN` and `PV` (e.g., `foo-1.2`).

---

## Source and build dirs

5. **`SRC_URI`** – Where to fetch source (git, tarball, patches).
6. **`S`** – Source directory inside `${WORKDIR}`.
7. **`WORKDIR`** – Work directory for this recipe.
8. **`B`** – Build directory (default = `${S}`, but sometimes separate).
9. **`D`** – Destination dir for `do_install` (staging before packaging).

---

## Build control

10. **`DEPENDS`** – Build-time dependencies (other recipes).
11. **`RDEPENDS`** – Runtime dependencies.
12. **`EXTRA_OECONF`** – Extra flags passed to `./configure`.
13. **`EXTRA_OEMAKE`** – Extra flags passed to `make`.
14. **`FILES`** – Files included in binary packages.
15. **`PACKAGES`** – List of output packages generated from recipe.

---

## Compiler & environment

16. **`CFLAGS`** – C compiler flags.
17. **`LDFLAGS`** – Linker flags.
18. **`CPPFLAGS`** – Preprocessor flags.

---

## Staging & install

19. **`bindir`, `sbindir`, `libdir`, `includedir`** – Standard install dirs.
20. **`prefix`, `exec_prefix`** – Prefix for installation paths (default `/usr`).

---

# Why these matter

* **`PN`, `PV`, `PR`** define what you’re building.
* **`SRC_URI`, `S`, `WORKDIR`, `B`, `D`** define *where* it builds.
* **`DEPENDS`, `RDEPENDS`** define *dependencies*.
* **`EXTRA_OECONF`, `EXTRA_OEMAKE`, `CFLAGS`, `LDFLAGS`** control *how it builds*.
* **`FILES`, `PACKAGES`, `bindir`…** define *what gets packaged and where it lands*.

