# BitBake Variables Guide

A quick reference for **assignment operators, parse vs eval time, datastore behavior, bad vs good examples, and best practices** in Yocto/BitBake.

------

## 1. Assignment Operators Cheat Sheet

| Operator   | Name                 | Parse Time Behavior                               | Eval Time Behavior               |
| ---------- | -------------------- | ------------------------------------------------- | -------------------------------- |
| `=`        | Deferred assignment  | Stores expression (not expanded yet)              | Expanded when used               |
| `:=`       | Immediate assignment | Expands immediately, frozen value                 | Stays fixed, ignores later edits |
| `?=`       | Weak assignment      | Sets only if unset (first time)                   | -                                |
| `??=`      | Very weak assignment | Sets only if *untouched anywhere* (true fallback) | -                                |
| `+=`       | Append (with space)  | Appends immediately w/ space                      | Already stringified              |
| `=+`       | Prepend (with space) | Prepends immediately w/ space                     | Already stringified              |
| `:append`  | Deferred append      | Queued for later (recorded in variable history)   | Applied at expansion             |
| `:prepend` | Deferred prepend     | Queued for later (recorded in variable history)   | Applied at expansion             |
| `:remove`  | Deferred removal     | Queued for later (recorded in variable history)   | Applied at expansion             |

------

### `??=` Example

```bitbake
# base config
FOO ??= "fallback"

# higher layer
FOO ?= "weak-default"

# recipe
FOO = "strong"
```

Final result:

```
FOO = "strong"
```

Explanation:

- `??=` applies only if *nobody ever touches* the variable.
- Since both `?=` and `=` touched it, the `??=` is ignored.
- If nothing else touched `FOO`, it would stay `"fallback"`.

------

## 2. Datastore Pipeline

BitBake stores variable **operation history** in a datastore (`d`) during parse time, then applies those operations at eval time.

Example:

```bitbake
FOO = "a"
FOO += " b"
FOO:append = " c"
FOO:remove = "b"
```

### Parse Time (`bitbake -e` shows history)

```
# $FOO [4 operations]
#   set     -> "a"
#   +=      -> " b"
#   _append -> " c"
#   _remove -> "b"
```

### Eval Time (when expanded in a task)

```
Start: "a"
Apply += " b"      -> "a b"
Apply :append " c" -> "a b c"
Apply :remove "b"  -> "a c"
```

**Final value:**

```
FOO = "a c"
```

------

## 3. All Operators Pipeline Example

```bitbake
FOO = "a"
FOO += " b"
FOO:append = " c"
FOO:prepend = "z "
FOO:remove = "b"
BAR ??= "fallback"
BAZ ?= "default"
EARLY := "${FOO}"
```

### Parse Time

- `FOO` set = `"a"`
- `+= " b"` applied immediately
- `:append " c"` queued
- `:prepend "z "` queued
- `:remove "b"` queued
- `BAR ??= "fallback"` (only if untouched)
- `BAZ ?= "default"` (only if unset)
- `EARLY := "a b"` (immediate, frozen)

### Eval Time

```
Start: "a b"
Apply :prepend -> "z a b"
Apply :append  -> "z a b c"
Apply :remove  -> "z a c"
```

### Final Values

```
FOO   = "z a c"
BAR   = "fallback"
BAZ   = "default"
EARLY = "a b"   (frozen at parse time)
```

------

## 4. Bad vs Good Examples

### Bad: `DEPENDS` inside a task

```bitbake
do_compile() {
    DEPENDS += "zlib"   # too late!
    oe_runmake
}
```

- `DEPENDS` is a **parse-time** variable.
- At this point, the task graph is already built, so this line is meaningless.

**Good: put it at parse time**

```bitbake
DEPENDS = "zlib"

do_compile() {
    oe_runmake   # zlib is guaranteed available
}
```

------

### Bad: Locking values too early with `:=`

```bitbake
EXTRA_FLAGS = "-O2"
CFLAGS := "${HOST_CFLAGS} ${EXTRA_FLAGS}"

EXTRA_FLAGS += "-Wall"
```

- `:=` froze `CFLAGS` at parse time.
- The latter `+= "-Wall"` never shows up.

**Good: use deferred expansion `=`**

```bitbake
EXTRA_FLAGS = "-O2"
CFLAGS = "${HOST_CFLAGS} ${EXTRA_FLAGS}"

EXTRA_FLAGS += "-Wall"
```

- At eval time, `CFLAGS` sees `"-O2 -Wall"` as expected.

------

### Bad: Using `+=` in layered metadata

```bitbake
# base recipe
SRC_URI = "git://example.com/foo.git"

# layer 1
SRC_URI += " file://patch1.patch"

# layer 2
SRC_URI:append = " file://patch2.patch"
```

- `+=` appended immediately, stringifying the variable.
- Later `:append` works, but `:remove` may fail since the structure is flattened.

**Good: use only `:append` / `:prepend` in layers**

```bitbake
SRC_URI = "git://example.com/foo.git"

# layer 1
SRC_URI:append = " file://patch1.patch"

# layer 2
SRC_URI:append = " file://patch2.patch"
```

- Both patches stack cleanly.
- `:remove` works reliably.

------

### Bad: Mixing parse/eval logic

```bitbake
do_compile() {
    if [ "${MACHINE}" = "qemuarm" ]; then
        EXTRA_OECONF += "--enable-arm-mode"
    fi
    ./configure ${EXTRA_OECONF}
}
```

- `EXTRA_OECONF` is a parse-time variable; modifying it inside a task is meaningless.

**Good: use conditional assignment with overrides**

```bitbake
EXTRA_OECONF = ""
EXTRA_OECONF:qemuarm = "--enable-arm-mode"

do_configure() {
    ./configure ${EXTRA_OECONF}
}
```

- The override applies at parse time, before tasks expand.

------

## 5. Best Practices

1. Use `=` (deferred) for most assignments keeps values flexible and layering-friendly.

2. Avoid `:=` unless absolutely necessary (e.g., inherit decisions, path freezing).

3. Use `?=` or `??=` for defaults so users/distro configs can override easily.

   - `?=` weak, can be overridden by later `=` or `:append`.
   - `??=` fallback, ignored if *anyone* else touches the variable.

4. Use `:append` / `:prepend` / `:remove` in `.bbappend` and layered configs.

5. Avoid `+=` / `=+` in layered setups — they act immediately and can break later `:append` / `:remove`. OK in local one-off recipes.

6. Keep **parse-time variables** (`DEPENDS`, `RDEPENDS`, `SRC_URI`, `PACKAGECONFIG`, `inherit`) at the **top** of your recipe.

7. Use **eval-time variables** (`CFLAGS`, `LDFLAGS`, `${WORKDIR}`, `${D}`, `${S}`) inside tasks.

8. Check expansions with:

   ```bash
   bitbake -e <recipe> | less
   ```

9. Structure recipes clearly:

   - **Parse-time section**: WHAT to build (deps, source, configs).
   - **Eval-time section**: HOW to build (flags, tasks).
   - **Packaging section**: FILES, RDEPENDS, etc.

10. Remember:

    - **Parse-time** = build graph.
    - **Eval-time** = build execution.
