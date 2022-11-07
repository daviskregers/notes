# Fast Forward merges

```
  master  git status
On branch master
nothing to commit, working tree clean
  master  git checkout -b some-change 
Switched to a new branch 'some-change'
  some-change  git status
On branch some-change
nothing to commit, working tree clean
  some-change  echo "change" >> file
  some-change ●  git status
On branch some-change
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file

no changes added to commit (use "git add" and/or "git commit -a")
  some-change ●  git commit -am "Change file"
[some-change 5040750] Change file
 1 file changed, 1 insertion(+)
```

```
 some-change  git log --oneline

5040750 (HEAD -> some-change) Change file
84f00a8 (master) add file
4e4ddba remove file
e980c5c Add file
aa6daef moved file
a6a2066 Yello
a635aaf initial
```

```

  some-change  git checkout master
Switched to branch 'master'
  master  git diff master some-change

diff --git a/file b/file
index e79c5e8..8ea0713 100644
--- a/file
+++ b/file
@@ -1 +1,2 @@
 initial
+change

```

```
 master  git merge some-change master
Updating 84f00a8..5040750
Fast-forward
 file | 1 +
 1 file changed, 1 insertion(+)
  master  git status
On branch master
nothing to commit, working tree clean
```

```
git log --oneline --graph --decorate

* 5040750 (HEAD -> master, some-change) Change file
* 84f00a8 add file
* 4e4ddba remove file
* e980c5c Add file
* aa6daef moved file
* a6a2066 Yello
* a635aaf initial

```

```
 master  git branch -d some-change
Deleted branch some-change (was 5040750).
```