## Deleting files

If we haven't tracked a file, we will need to use operating systems `rm` command:

```
davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master
nothing to commit, working tree clean
 davis@davis-arch  ~/projects/learning-git/project   master  touch another-file
 davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	another-file

nothing added to commit but untracked files present (use "git add" to track)
 davis@davis-arch  ~/projects/learning-git/project   master  rm another-file 
 davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master
nothing to commit, working tree clean
```

If the file is tracked, we can use the `git rm` command:

```
 davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master
nothing to commit, working tree clean
 davis@davis-arch  ~/projects/learning-git/project   master  git ls-files
l1/file1
l1/file1-2
l1/l2/file-2-2
l1/l2/file2
l1/l2/l3/file3
l1/l2/l3/l4/file-4-2
l1/l2/l3/l4/file4
l3-file
 davis@davis-arch  ~/projects/learning-git/project   master  git rm l3-file
rm 'l3-file'
 davis@davis-arch  ~/projects/learning-git/project   master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	deleted:    l3-file

 davis@davis-arch  ~/projects/learning-git/project   master ✚  ls 
l1
```

We can revert the deleted file:

```
davis@davis-arch  ~/projects/learning-git/project   master ●  git checkout l3-file
davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master
nothing to commit, working tree clean
davis@davis-arch  ~/projects/learning-git/project   master  ls
l1  l3-file
```

To stage the deleted files:

```
davis@davis-arch  ~/projects/learning-git/project   master  rm -r l1/l2
 davis@davis-arch  ~/projects/learning-git/project   master ●  git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	deleted:    l1/l2/file-2-2
	deleted:    l1/l2/file2
	deleted:    l1/l2/l3/file3
	deleted:    l1/l2/l3/l4/file-4-2
	deleted:    l1/l2/l3/l4/file4

no changes added to commit (use "git add" and/or "git commit -a")
davis@davis-arch  ~/projects/learning-git/project   master ●  git add -A
davis@davis-arch  ~/projects/learning-git/project   master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	deleted:    l1/l2/file-2-2
	deleted:    l1/l2/file2
	deleted:    l1/l2/l3/file3
	deleted:    l1/l2/l3/l4/file-4-2
	deleted:    l1/l2/l3/l4/file4
```

Revert it:

```
davis@davis-arch  ~/projects/learning-git/project   master ✚  git reset HEAD .
Unstaged changes after reset:
D	l1/l2/file-2-2
D	l1/l2/file2
D	l1/l2/l3/file3
D	l1/l2/l3/l4/file-4-2
D	l1/l2/l3/l4/file4
 davis@davis-arch  ~/projects/learning-git/project   master ●  git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	deleted:    l1/l2/file-2-2
	deleted:    l1/l2/file2
	deleted:    l1/l2/l3/file3
	deleted:    l1/l2/l3/l4/file-4-2
	deleted:    l1/l2/l3/l4/file4

no changes added to commit (use "git add" and/or "git commit -a")
 davis@davis-arch  ~/projects/learning-git/project   master ●  git checkout .
 davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master
nothing to commit, working tree clean
```