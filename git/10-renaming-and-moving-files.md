## Renaming and moving files

We can move and rename files by using the following command:

```
davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master
nothing to commit, working tree clean
davis@davis-arch  ~/projects/learning-git/project   master  git mv l1/l2/l3/file-3-2 l3-file
davis@davis-arch  ~/projects/learning-git/project   master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	renamed:    l1/l2/l3/file-3-2 -> l3-file
davis@davis-arch  ~/projects/learning-git/project   master ✚  git commit -m "moved file"
[master aa6daef] moved file
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename l1/l2/l3/file-3-2 => l3-file (100%)
davis@davis-arch  ~/projects/learning-git/project   master  ls
l1  l3-file
```

When using operating system, it will not track the renamed files:

```
davis@davis-arch  ~/projects/learning-git/project   master  mv l1/l2/l3/l4/file-4-2 l1/l2/l3/l4/file-4.2
davis@davis-arch  ~/projects/learning-git/project   master ●  git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	deleted:    l1/l2/l3/l4/file-4-2

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	l1/l2/l3/l4/file-4.2

no changes added to commit (use "git add" and/or "git commit -a")
```

We can use a command to see the rename:

```
davis@davis-arch  ~/projects/learning-git/project   master ●✚  git add -u
davis@davis-arch  ~/projects/learning-git/project   master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	renamed:    l1/l2/l3/l4/file-4-2 -> l1/l2/l3/l4/file-4.2
```