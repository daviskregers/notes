# Ignoring unwanted files

Usually there are files in the repository like `.DS_Store` on mac, ar source cache like `.pyc` in python, that we don't want in our repository. We can tell git to ignore them.

```
 master  touch .DS_Store
  master  touch l1/.DS_Store
  master  git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.DS_Store
	l1/.DS_Store

nothing added to commit but untracked files present (use "git add" to track)
  master  echo ".DS_Store" >> .gitignore
  master  git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore

nothing added to commit but untracked files present (use "git add" to track)
```

We can also use pattern matching it:

```
  master  touch l1/l2/1.ignored
  master  touch l1/l2/2.ignored
  master  touch l1/l2/3.ignored
  master  git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
	l1/l2/1.ignored
	l1/l2/2.ignored
	l1/l2/3.ignored

nothing added to commit but untracked files present (use "git add" to track)
  master  echo "*.ignored" >> .gitignore
  master  git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore

nothing added to commit but untracked files present (use "git add" to track)
```

And negate it

```
 master  echo '!2.ignored' >> .gitignore
  master  cat .gitignore
.DS_Store
*.ignored
!2.ignored
  master  git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
	l1/l2/2.ignored

nothing added to commit but untracked files present (use "git add" to track)
```