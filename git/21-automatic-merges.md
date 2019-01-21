# Automatic merges

```
 master  git status
On branch master
nothing to commit, working tree clean
  master  git checkout -b simple-change
Switched to a new branch 'simple-change'
  simple-change  echo "simple change" >> file
 ✘  simple-change ●  git commit -am "simple change"
[simple-change 83f3159] simple change
 1 file changed, 1 insertion(+)
  simple-change  git status
On branch simple-change
nothing to commit, working tree clean
  simple-change  git checkout branch
error: pathspec 'branch' did not match any file(s) known to git
 ✘  simple-change  git checkout master
Switched to branch 'master'
  master  echo "file2" >> file2
 ✘  master  git add file2         
  master ✚  git commit -m "file2"
[master 19ab207] file2
 1 file changed, 1 insertion(+)
 create mode 100644 file2
```

```
git log --oneline --decorate --graph --all

* 19ab207 (HEAD -> master) file2
| * 83f3159 (simple-change) simple change
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
 master  git merge simple-change -m "Mergin changes from simple-change Branch"
Merge made by the 'recursive' strategy.
 file | 1 +
 1 file changed, 1 insertion(+)
```

```
*   620ff72 (HEAD -> master) Mergin changes from simple-change Branch
|\  
| * 83f3159 (simple-change) simple change
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
  master  git branch -d simple-change 
Deleted branch simple-change (was 83f3159).
```

```
  master  cat file
initial
change
other change
simple change
```