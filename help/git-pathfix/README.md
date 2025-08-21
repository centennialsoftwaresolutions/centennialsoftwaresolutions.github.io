# Using git clean/smudge filters to abstract absolute paths across a shared PetaLinux project

A PetaLinux project can contain absolute paths in certain files. These cause breakage when multiple developers are working on a project, or if you have multiple copies of a project on your disk.

One easy solution is to use git clean and smudge filters to abstract the absolute path. In short:

- The clean filter "cleans up" the absolute paths. When you commit files/changes into git, it'll find absolute paths and replace them with a placeholder.
- The smudge filter does the opposite. When you clone or check out a branch, it'll smudge the placeholder back into an absolute path.

After the simple initial setup, this all happens transparently behind the scenes.

---

There are three steps:

1) Create the clean and smudge scripts
2) Specify a filter that applies the two scripts
3) Tell git to run the filter on all files


This document describes:
- The 3 steps in detail
- A full example of using this on a brand new git project
- A note on using this with an existing git project, e.g. an existing PetaLinux project
- A note on a more complex configuration option (not recommended)

---

## Step 1: Create clean/smudge scripts

We want the scripts to find absolute paths and replace them with a placeholder. This can be done with sed. Git will run these scripts on every file that's changed (when staged).

You can place these scripts inside the git project, but then you'll need to set them up individually for each project. It's better to install them in a fixed location on your system, e.g. `~/bin/git_pathfix_clean.sh` and `~/bin/git_pathfix_smudge.sh`.

Installing the scripts user-wide has no negative side effects and makes it simpler to set up new projects. When installed user-wide, it'll also allow for the filters to work when cloning new projects with zero extra steps. We highly recommend this over the per-project approach - the per-project approach also adds additional complication when cloning the repository.

**Place in your user dir**
```
mkdir -p ~/bin/
echo 'sed "s|$(pwd)|__GIT_PATHFIX_PLACEHOLDER__|g"' >~/bin/git_pathfix_clean.sh
echo 'sed "s|__GIT_PATHFIX_PLACEHOLDER__|$(pwd)|g"' >~/bin/git_pathfix_smudge.sh
```

**(Alternative: Place in git project)**
```
# (while in your git project's basedir)
echo 'sed "s|$(pwd)|__GIT_PATHFIX_PLACEHOLDER__|g"' >clean.sh
echo 'sed "s|__GIT_PATHFIX_PLACEHOLDER__|$(pwd)|g"' >smudge.sh
```

When git runs the clean/smudge scripts, `pwd` will be the git project basedir.

## Step 2: Specify a filter

Now that we have the scripts created, the next step is to specify a filter that applies these scripts. You can do this user-wide, which will make the filter available in every project on your system. (The filter won't be activated by default on every project; it'll just be available for use). Alternatively, you can specify it in the project-specific config.

**Specify for user**
```
git config --global filter.pathfix.clean  ~/bin/git_pathfix_clean.sh
git config --global filter.pathfix.smudge ~/bin/git_pathfix_smudge.sh
```

This is equivalent to adding the following lines to your ~/.gitconfig:

```
[filter "pathfix"]
  clean  = /home/css/bin/git_pathfix_clean.sh
  smudge = /home/css/bin/git_pathfix_smudge.sh
```

**(Alternative: Specify for git project)**

Option 1: Specify relative paths to the scripts

This will cause errors if you run `git add` from subdirectories in your git project, because git looks for them in the cwd. So you'll always have to cd back to the project basedir when doing `git add`.

```
git config filter.pathfix.clean  clean.sh
git config filter.pathfix.smudge smudge.sh
```

Option 2: Specify absolute paths to the scripts

This will need to be updated if you move the git project to a different location on disk.

```
git config filter.pathfix.clean  $(pwd)/clean.sh
git config filter.pathfix.smudge $(pwd)/smudge.sh
```

These are equivalent to adding these lines to `.git/config` in the project:
```
[filter "pathfix"]
  clean  = clean.sh
  smudge = smudge.sh
  # OR
  clean  = /path/to/clean.sh
  smudge = /path/to/smudge.sh
```

## Step 3: Enable the filter

In `.gitattributes`, tell git to apply the pathfix filter to all files. (Instead of `*`, you could use something like `*.c` to limit it to specific files)

```
echo "* filter=pathfix" >>.gitattributes
git add .gitattributes
```

The .gitattributes file is synced across the remote, so anybody who clones the project will have this config already set up for them. That means this only needs to be done once per project.

---

# Overview - new git project setup

You create (`git init`) a new git project at `/home/alice/project`.

You've already created clean/smudge scripts that translate between absolute paths and placeholders, placed in `~/bin/...`.

You've already specified the `pathfix` filter in `~/.gitconfig`.

All you need to do in this project is create the `.gitattributes` file:

```
echo "* filter=pathfix" >>.gitattributes
git add .gitattributes
git commit -m 'Add pathfix filter'
```

In the project you create a file named `x`, with contents (or create a PetaLinux project, ...):

```
foo
ASDF/home/alice/project/barGHJK
baz
```

You run `git add x`. The clean filter gets activated and replaces the staged file contents with:

```
foo
ASDF__GIT_PATHFIX_PLACEHOLDER__/barGHJK
baz
```

This is completely transparent behind-the-scenes. The file on your disk is unmodified, it still contains the actual `/home/alice/project` path. But the placeholder is what's committed into git.

You push to remote, and your coworker Bob clones the project into `/home/bob/proj` (or pulls an update after the clone). Git runs the smudge filter on the file, which translates `__GIT_PATHFIX_PLACEHOLDER__` back to the actual `$(pwd)` on their system. So the file on Bob's disk contains:

```
foo
ASDF/home/bob/proj/barGHJK
baz
```

---

# Note 1: Adding to an existing project

You already have an existing project with files (e.g. have already run `petalinux-create` and now want to add pathfix).

Have all coworkers (including yourself) set up the clean/smudge scripts and filter spec (.sh files and `~/.gitconfig`).

Set up the `.gitattributes` file as normal:

```
echo "* filter=pathfix" >>.gitattributes
git add .gitattributes
git commit -m 'Add pathfix filter'
```

This will apply the clean filter to any new files you add to the project. If a file contains an absolute path and you change the file and `git add` after changing it, that'll also trigger git to run the clean filter on the file.

However, git won't proactively apply the filter to existing unchanged files. So any absolute paths that are already present in your project will remain. To convert those existing absolute paths, run:

```
git add --renormalize .
git commit -m 'Convert existing abspaths to placeholders'
git push
```

The `add --renormalize` will trigger git to run the clean filter on the entire project, converting all existing absolute paths to the placeholders.

---

# Full PetaLinux flow

```
petalinux-create -t project -n proj -s ..path/to/bsp.xsa
cd proj

git init

git add .gitignore
git commit -m 'Init git'

echo "* filter=pathfix" >>.gitattributes
git add .gitattributes
git commit -m 'Add pathfix filter'

git add --renormalize .
git commit -m 'Convert existing abspaths to placeholders'
git push
```

After this, continue with `petalinux-config`, `petalinux-build`, and other git operations as normal.

No extra steps are needed when cloning the project. As long as you have the .sh files and the `~/.gitconfig` set up in your user, everything will "just work."

---

# Note 2: User-wide vs per-project config

There are three components:

- the clean and smudge scripts (the .sh scripts)
- the filter specification (which names the filter 'pathfix' and points it to the scripts)
- the file attributes (which tell git to run the filter on all files)

The `.gitattributes` file is synced across remote, so once it's added to the project it's present for everyone.

If you place the clean and smudge scripts in the project, those will also be synced with the project. Alternatively, each collaborator can put them on their system (user-wide or system-wide).

The filter specification can be installed user-wide, in `~/.gitconfig`. If each collaborator has done this, it'll be available for use in all their projects. However, you can also install it into the project's `.git/config`. The project-specific `.git/config` file is *not* synced across the remote, so each user will need to set that up manually after cloning. And then re-run the smudge filter (see below).

For this reason, we recommend that:
- All collaborators install the clean/smudge .sh scripts into their user dir
- All collaborators install the filter spec into `~/.gitconfig` (user-wide)

Then it "just works", with no additional per-project configuration needed (aside from the one-time setup of the `.gitattributes` file when you create the project).

With the per-project config, after you clone the repository you'll need to manually set up `.git/config` to specify the filter. Also, the filter did not exist while you were cloning, so your cloned files on disk will contain the absolute paths. After you set up the filter again, you'll need to apply it to the existing files:

```
# (from git repo basedir)
rm .git/index
git checkout HEAD -- .
```

---

# References

https://git-scm.com/book/ms/v2/Customizing-Git-Git-Attributes#_keyword_expansion

On re-applying the smudge filters after cloning a repository: https://stackoverflow.com/a/21653524
