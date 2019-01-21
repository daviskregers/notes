# Visual Diff / Merge Tool 

In order to make things easier when working with diffs and branch merges, we can use `P4Merge` tool that helps with comparing and conflict  merging.

You can install it on arch:

```
yaourt -S p4v
```

Now we can configure git to use it for comparing and conflict resolution:

```
git config --global merge.tool p4merge
git config --global mergetool.p4merge.path "/usr/bin/p4merge"
git config --global mergetool.prompt false
git config --global diff.tool p4merge
git config --global difftool.p4merge.path "/usr/bin/p4merge"
git config --global diftool.prompt false
```

Verify changes:

```
git config --list --global
```
