---
title: Delete local git branches
creation date: 2023-12-14 11:37
draft: false
tags:
  - git
  - documentation
---
# Problem
After working for some time on a project, you end up having dozens of local branches that are not relevant because already merged.

# What we want ?
Delete local branches that have been merged to master / main.

# How ?
1. Get a list of branches that have been merged.
- checkout to the master / main branch of your project
- run this command to see the list of already merged branches:

if your are using main as you master branch:
```bash
git branch --merged main
```

else, if you are using master as your master branch:
```bash
git branch --merged master
```

2. Delete all the branches (adapt the command if your master branch is called master):
```bash
git branch --merged main | egrep -v '^\s*\*?\s*master$' | xargs git branch -d
```

# Delete remaining un-merged branches
1. If you try to delete a branch that has not been merged with the `-d` option you will have an error: `error: The branch '<branch-name>' is not fully merged.
`
2. You must use the `-D` option:
```bash
git branch -D <branch-name>
```
