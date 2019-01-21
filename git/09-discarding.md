## Backing out changes

If we need to back-out the changes from the staging area (unstage), we can use a following command:

```
davis@davis-arch  ~/projects/learning-git/project   master  touch l1/file1-2
davis@davis-arch  ~/projects/learning-git/project   master  touch l1/l2/file-2-2
davis@davis-arch  ~/projects/learning-git/project   master  touch l1/l2/l3/file-3-2
davis@davis-arch  ~/projects/learning-git/project   master  touch l1/l2/l3/l4/file-4-2 
davis@davis-arch  ~/projects/learning-git/project   master  git add .
davis@davis-arch  ~/projects/learning-git/project   master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   l1/file1-2
	new file:   l1/l2/file-2-2
	new file:   l1/l2/l3/file-3-2
	new file:   l1/l2/l3/l4/file-4-2

davis@davis-arch  ~/projects/learning-git/project   master ✚  git reset HEAD l1/l2/file-2-2
davis@davis-arch  ~/projects/learning-git/project   master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   l1/file1-2
	new file:   l1/l2/l3/file-3-2
	new file:   l1/l2/l3/l4/file-4-2

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	l1/l2/file-2-2

```

Now, the file `l1/l2/file2-2` has moved back into the `working directory` state. 

If we want to revert (`discard`) the changes to the file as it was last commited:

```
davis@davis-arch  ~/projects/learning-git/project   master ✚  echo "changes" >> l1/l2/l3/file-3-2
davis@davis-arch  ~/projects/learning-git/project   master ●✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   l1/file1-2
	new file:   l1/l2/l3/file-3-2
	new file:   l1/l2/l3/l4/file-4-2

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   l1/l2/l3/file-3-2

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	l1/l2/file-2-2

davis@davis-arch  ~/projects/learning-git/project   master ●✚  git checkout l1/l2/l3/file-3-2
davis@davis-arch  ~/projects/learning-git/project   master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   l1/file1-2
	new file:   l1/l2/l3/file-3-2
	new file:   l1/l2/l3/l4/file-4-2

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	l1/l2/file-2-2
```