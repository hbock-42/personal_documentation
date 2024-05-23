---
title: Git log pretty
draft: false
tags:
  - git
  - documentation
cssclasses:
  - md-full-width
---
https://ma.ttias.be/pretty-git-log-in-one-line/

Like git log, but with a graph showing you when fork and merge occurred:
```bash
git log --graph --pretty=oneline --abbrev-commit
```

This one is the same with more colours:
```bash
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```
