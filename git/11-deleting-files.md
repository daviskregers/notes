## Deleting files

If we haven't tracked a file, we will need to use operating systems `rm` command:

```
 master  git status
On branch master
nothing to commit, working tree clean
  master  touch another-file
  master  git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	another-file

nothing added to commit but untracked files present (use "git add" to track)
  master  rm another-file 
  master  git status
On branch master
nothing to commit, working tree clean
```

If the file is tracked, we can use the `git rm` command:

```
  master  git status
On branch master
nothing to commit, working tree clean
  master  git ls-files
l1/file1
l1/file1-2
l1/l2/file-2-2
l1/l2/file2
l1/l2/l3/file3
l1/l2/l3/l4/file-4-2
l1/l2/l3/l4/file4
l3-file
  master  git rm l3-file
rm 'l3-file'
  master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	deleted:    l3-file

  master ✚  ls 
l1
```

We can revert the deleted file:

```
 master ●  git checkout l3-file
 master  git status
On branch master
nothing to commit, working tree clean
 master  ls
l1  l3-file
```

To stage the deleted files:

```
 master  rm -r l1/l2
  master ●  git status
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
 master ●  git add -A
 master ✚  git status
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
 master ✚  git reset HEAD .
Unstaged changes after reset:
D	l1/l2/file-2-2
D	l1/l2/file2
D	l1/l2/l3/file3
D	l1/l2/l3/l4/file-4-2
D	l1/l2/l3/l4/file4
  master ●  git status
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
  master ●  git checkout .
  master  git status
On branch master
nothing to commit, working tree clean
```