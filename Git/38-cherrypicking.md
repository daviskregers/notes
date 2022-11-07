# Cherrypicking

If you have 2 branches and you have a a change that needs to be applied from one to another, but only the one specific change, you can use cherrypicking.

```
 master  git status
On branch master
nothing to commit, working tree clean
 master  git checkout -b develop
Switched to a new branch 'develop'
 develop  echo "fix 1" >> file 
 develop ●  git commit -am "Fix 1"
[develop 7a837cc] Fix 1
 1 file changed, 1 insertion(+)
 develop  echo "fix 2" >> file
 develop ●  git commit -am "Fix 2"
[develop c5bd510] Fix 2
 1 file changed, 1 insertion(+)
 develop  git log --oneline --decorate --graph

* c5bd510 (HEAD -> develop) Fix 2
* 7a837cc Fix 1
* af6b837 (tag: v-1.2, master) Updating for v-1.2
* 6a09e40 (tag: v-1.1) Tweaking a file
* b4ff9f3 (tag: v-1.0) Done with the WIP2
* 0ce9769 Done with the WIP2
* b419d7e Emergency fix
* c8d946a Done with the WIP
* b8e1096 Quick fix
* ddef7ba (bigtrouble) change after rebase
* 9066d92 fb adding trouble to file
* 0861e5d mb conflicting changes brewing
* 0c5efff mb before rebase conflicts
* 42f5865 Another change
* c671488 feature
* 02064fc (tag: v-0.9-beta) edit
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

 develop  git checkout master
Switched to branch 'master'
 master  echo "hello" >> file2
 master ●  git commit -am "Updates away from develop"
[master 0c27eb4] Updates away from develop
 1 file changed, 1 insertion(+)

git cherry-pick 7a837cc
[master 4dde5df] Fix 1
 Date: Tue Jan 22 20:21:37 2019 +0200
 1 file changed, 1 insertion(+)

git status
On branch master
nothing to commit, working tree clean

git log --oneline --decorate --graph --all

* 4dde5df (HEAD -> master) Fix 1
* 0c27eb4 Updates away from develop
| * c5bd510 (develop) Fix 2
| * 7a837cc Fix 1
|/  
* af6b837 (tag: v-1.2) Updating for v-1.2
* 6a09e40 (tag: v-1.1) Tweaking a file
* b4ff9f3 (tag: v-1.0) Done with the WIP2
* 0ce9769 Done with the WIP2
...

```


