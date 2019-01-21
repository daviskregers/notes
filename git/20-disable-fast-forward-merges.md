# Disable fast forward merges

```
 master  git status
On branch master
nothing to commit, working tree clean
  master  git checkout -b other-change
Switched to a new branch 'other-change'
  other-change  echo "other change" >> file
  other-change ●  git status
On branch other-change
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file

no changes added to commit (use "git add" and/or "git commit -a")
  other-change ●  git commit -am "Other change"
[other-change a4d0bc9] Other change
 1 file changed, 1 insertion(+)
  other-change  git status
On branch other-change
nothing to commit, working tree clean
  other-change  git checkout master
Switched to branch 'master'
  master  git merge other-change --no-ff
Merge made by the 'recursive' strategy.
 file | 1 +
 1 file changed, 1 insertion(+)
  master  git status
On branch master

```

```
 master  git log --oneline --decorate --graph

*   9521a8d (HEAD -> master) Merge branch 'other-change'
|\  
| * a4d0bc9 (other-change) Other change
|/  
* 5040750 Change file
* 84f00a8 add file
* 4e4ddba remove file
* e980c5c Add file
* aa6daef moved file
* a6a2066 Yello
* a635aaf initial
```

```
  master  git branch -d other-change 
Deleted branch other-change (was a4d0bc9).
```