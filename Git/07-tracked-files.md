## Tracked files

If we have a file that is already commited and we change it, git will track it and let us know that it has been changed:

```
davis@davis-arch  ~/projects/learning-git  git init project
Initialized empty Git repository in /home/davis/projects/learning-git/project/.git/
davis@davis-arch  ~/projects/learning-git  cd project 
 master  touch file
 master  git add file
 master ✚  git commit -m "initial commit"
[master (root-commit) ac6cbef] initial commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file
 master  git status
On branch master
nothing to commit, working tree clean
 master  echo "changed" >> file
 master ●  git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file

no changes added to commit (use "git add" and/or "git commit -a")
```

We can shortcut to both add file to staging area and commit by using a following command:

```
 master ●  git commit -am "commit message"
[master e93c1a1] commit message
 1 file changed, 1 insertion(+)
 master  git status
On branch master
nothing to commit, working tree clean
```

The `-a` stands for add to staging area, `-m` for message.

A way to find out if our file is being tracked by git we can use a command:

```
 master  git ls-files
file
```

We can see that git tracks the `file`. If we add a new file, it wont be tracked unless added to staging area or commited:

```
 master  touch file2
 master  git ls-files
file
```