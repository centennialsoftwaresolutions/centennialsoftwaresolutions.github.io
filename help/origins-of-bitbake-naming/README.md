## Origins of BitBake Naming


**BitBake** evolved out of **OpenEmbedded** in the early 2000s. The naming conventions reflect that history, and sometimes the variable names don’t line up exactly with what we call them today.

For example `PN` historically meant *package name*, but in today’s Yocto world it’s really the **recipe name**. The variable names are legacy but kept for compatibility across 20+ years of BitBake.

---


* **BitBake** was originally modeled on `make`, but with a declarative, metadata-driven system.
* In **OpenEmbedded Classic**, “package” was often used loosely to mean both the *recipe* (`.bb`) and the *binary packages* (`.ipk`, `.deb`, `.rpm`).
* Over time, Yocto (2009–2011) standardized the terminology:

  * **Recipe** = the `.bb` file (instructions to build software).
  * **Package** = the binary outputs produced from recipes.

But many variable names (`PN`, `PR`, `PV`, etc.) were already established, so they stuck.

---

## Key Variable Names and Their History

* **`PN` = Package Name**

  * Original meaning: “the name of the package/recipe being built.”
  * Today, it’s effectively the **recipe name** (basename of the `.bb` file without version).
  * Example: `zlib_1.2.11.bb` → `PN = "zlib"`.

* **`PV` = Package Version**

  * Original meaning: “package version.”
  * Stuck around even though today it’s better thought of as the **recipe version**.
  * Comes directly from the filename: `_1.2.11` → `PV = "1.2.11"`.

* **`PR` = Package Revision**

  * Originally for “incrementing package revisions” (like distro maintainers do in Debian/Fedora).
  * Default `r0`, incremented when you change the recipe but not the upstream version.
  * Still called “package revision” even though it applies to recipes.

* **`P` = Package (name+version)**

  * Historical shorthand: `${PN}-${PV}`.
  * Used for source tarball names like `foo-1.2.tar.gz`.

* **`PF` = Package Full**

  * `${PN}-${PV}-${PR}`.
  * Historical “full identifier of a package” in the old OE packaging days.
  * Today: the unique triplet of name/version/revision.

---

## Recipe vs Package Today

* **Recipe** = a `.bb` file (metadata). Identified by `PN`, `PV`, `PR`.
* **Package** = one or more binary outputs (`.deb`, `.rpm`, `.ipk`) produced from a recipe.

  * Defined by `PACKAGES`, `FILES`, `RDEPENDS`.
  * Default package = `${PN}` (runtime).
  * Subpackages often `${PN}-dev`, `${PN}-dbg`, `${PN}-doc`.

So when you see variables like `PN`, `PV`, `PR`:

* They *originated* when everything was called a “package.”
* In modern Yocto docs they’re described in terms of **recipes**.

---

## Timeline of Terminology

* **Early OE (2003–2005):** “packages” meant recipes.
* **BitBake 1.0 era (2004):** variables standardized (`PN`, `PV`, `PR`, `SRC_URI`).
* **Yocto Project launch (2010–2011):** clearer separation of “recipes” vs “packages.”
* **Today:**

  * *Recipe* = build instructions (`.bb`, `.bbappend`, `.inc`).
  * *Package* = runtime output for the package manager.
  * But variable names still use the historical “package” prefix.
