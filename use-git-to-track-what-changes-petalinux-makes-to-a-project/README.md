# Use Git to track what changes Petalinux makes to a project

You can use Git to figure out what changes Petalinux makes to a project when you run Petalinux commands. This can be helpful when debugging, to figure out exactly what Petalinux is doing. This flow doesn't require any special usage/setup; it's just not the most obvious use case of Git if you haven't seen something like this before. Hopefully this tip is helpful for you!

Get your Petalinux project to the base state that you want to start tracking from, then:

```
cd petalinux-project
git init .
git add .
git commit -m 'initial commit'

# run your petalinux commands

git status
git diff
# see what changed
```

Optionally, delete the git repository when done: rm -rf .git

Note: Petalinux generates a default .gitignore when creating a project. This default .gitignore will exclude the entire build/ directory, the images/linux/ output directory, and some other paths, so git won't track changes Petalinux makes to files in those places. If you do un-ignore the build folder, git will slow down massively due to the huge number of files in it.