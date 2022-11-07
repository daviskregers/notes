# Simple rebase

```
  master  git checkout -b myfeature
Switched to a new branch 'myfeature'
  myfeature  echo "feature" >> file2
  myfeature ●  git commit -am "feature"
[myfeature 156f433] feature
 1 file changed, 1 insertion(+)
  myfeature  git checkout master
Switched to branch 'master'
  master  echo "edit" >> file
 ✘  master ●  git commit -am "edit"
[master 02064fc] edit
 1 file changed, 1 insertion(+)
```

```
git log --oneline --decorate --all --graph 

* 02064fc (HEAD -> master) edit
| * 156f433 (myfeature) feature
|/  
*   fa79281 merge conflict
|\  
| * 5d495a8 (conflicting-change) Conflicting change
* | 14ae637 yet another change
|/  
*   620ff72 Mergin changes from simple-change Branch
|\  
| * 83f3159 simple change
* | 19ab207 file2
|/  
*   9521a8d Merge branch 'other-change'
|\  
| * a4d0bc9 Other change
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
 ✘  master  git checkout myfeature
Switched to branch 'myfeature'
  myfeature  git rebase master
First, rewinding head to replay your work on top of it...
Applying: feature
```

The rebase added the master changes into the feature branch, now it appears as the changes in the feature branch were made after the commit on the master branch.

```
git log --oneline --decorate --all --graph 

* c671488 (HEAD -> myfeature) feature
* 02064fc (master) edit
*   fa79281 merge conflict
|\  
| * 5d495a8 (conflicting-change) Conflicting change
* | 14ae637 yet another change
|/  
*   620ff72 Mergin changes from simple-change Branch
|\  
| * 83f3159 simple change
* | 19ab207 file2
|/  
*   9521a8d Merge branch 'other-change'
|\  
| * a4d0bc9 Other change
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
 ✘  myfeature  echo "another edit" >> file
  myfeature ●  git commit -am "Another change"
[myfeature 42f5865] Another change
 1 file changed, 1 insertion(+)
  myfeature  git checkout master
Switched to branch 'master'
  master  git merge myfeature 
Updating 02064fc..42f5865
Fast-forward
 file  | 1 +
 file2 | 1 +
 2 files changed, 2 insertions(+)
```

Since we rebased, we ended up with a fast-forward merge instead of a merge conflict.