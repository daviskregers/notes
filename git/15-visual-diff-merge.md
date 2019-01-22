# Visual Diff / Merge Tool 

In order to make things easier when working with diffs and branch merges, we can use `P4Merge` tool that helps with comparing and conflict  merging.

You can install it on arch:

```
yaourt -S p4v
```

On ubuntu-based machine:
```
cd /tmp
wget http://www.perforce.com/downloads/perforce/r18.1/bin.linux26x86_64/p4v.tgz
tar zxvf p4v.tgz
sudo cp -r p4v-* /usr/local/p4v/
sudo ln -s /usr/local/p4v/bin/p4merge /usr/local/bin/p4merge
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
