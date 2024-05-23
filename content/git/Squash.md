---
title: Squash
draft: false
tags:
  - git
  - documentation
cssclasses:
  - md-full-width
---
## What do we mean by squashing commit?
Here we speak about the action of taking multiple commits and transforming them into 1 commit.

## When would I want to do that?
It is useful to to it before rebase an other branch (main, master ...) into your branch if you have a lot of commits in your branch. This prevents your from having to replay all commits 1 by 1, which may not have a lot of sense, especially if you commit different versions of the same file in different commits.

---

```bash
git rebase -i <after-this-commit>
```

Where `<after-this-commit>` is either:
- the hash of the parent of the oldest commit you want to squash
- the relative location from the head

---

## Example

```bash
git log --oneline
```
outputs:
```console
cac9ca8d (HEAD -> feat/pass-on-hidden-visible-merger, origin/feat/pass-on-hidden-visible-merger) make constants for default values
df30abde move price fieldin its own folder
b39d3ab1 improve test name
153cea41 feature(api+front): new accounting system
91240206 (main) fix(api): fix bug with free orders not receiving emails
```

If you want to squash from `(HEAD -> feat/pass-on-hidden-visible-merger, origin/feat/pass-on-hidden-visible-merger) make constants for default values`  **included** to `feature(api+front): new accounting system` **included**:

1. Copy the hash of the commit **after** the last one you want to include. Here, it is the hash of the mr `(main) fix(api): fix bug with free orders not receiving emails` -> `91240206`

2. Run the command:
```bash
 git rebase -i <after-this-commit>
```
 It will open a text editor with something like this:
```console                                                                                                   
pick 153cea41 feature(api+front): new accounting system
pick b39d3ab1 improve test name
pick df30abde move price fieldin its own folder
pick cac9ca8d make constants for default values
```

To squash all your commits into one, you must replace the word `pick` with `squash` in front of each line **EXCEPT** the first one (you let the word `pick` on this one).
You can use the shortcut `s` instead of `squash`.

3. So the file must look like this:
```console
pick 153cea41 feature(api+front): new accounting system
s b39d3ab1 improve test name
s df30abde move price fieldin its own folder
s cac9ca8d make constants for default values
```

Then you save, and it opens:
```console
# This is a combination of 4 commits.
# This is the 1st commit message:

feature(api+front): new accounting system

# This is the commit message #2:

improve test name

# This is the commit message #3:

move price fieldin its own folder

# This is the commit message #4:

make constants for default values
```

This is here that you choose what will be the new commit message.

4. You can either:
- `delete`  or `comment` everything, and add a new message.
	or
- `comment` every message except the one you want to keep.

For exemple, if you choose the second option:
```console
# This is a combination of 4 commits.
# This is the 1st commit message:

feature(api+front): new accounting system

# This is the commit message #2:

#improve test name

# This is the commit message #3:

#move price fieldin its own folder

# This is the commit message #4:

#make constants for default values
```

The commit message will be: `feature(api+front): new accounting system` because it is the only message no commented.
You can save.

5. You can now push with:
```bash
git push -f
```

You can comment every message but one (this will be the final commit message), or you can comment all message, and

Then you can push -f to the remote branch