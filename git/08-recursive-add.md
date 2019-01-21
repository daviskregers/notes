## Recursive add

```
davis@davis-arch  ~/projects/learning-git/project   master ●  mkdir -p l1/l2/l3/l4
davis@davis-arch  ~/projects/learning-git/project   master ●  touch l1/file1
davis@davis-arch  ~/projects/learning-git/project   master ●  touch l1/l2/file2
davis@davis-arch  ~/projects/learning-git/project   master ●  touch l1/l2/l3/file3
davis@davis-arch  ~/projects/learning-git/project   master ●  touch l1/l2/l3/l4/file4
```

Git will not show the files changed recursively:

```
davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	l1/

nothing added to commit but untracked files present (use "git add" to track)
```

But we can add the changes recursively to the staging area:

```
davis@davis-arch  ~/projects/learning-git/project   master  git add .
davis@davis-arch  ~/projects/learning-git/project   master ✚  git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   l1/file1
	new file:   l1/l2/file2
	new file:   l1/l2/l3/file3
	new file:   l1/l2/l3/l4/file4

```