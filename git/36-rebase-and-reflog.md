# Rebase and Reflog

Remove the last commit.

```

git status
On branch master
nothing to commit, working tree clean

git log --oneline --decorate --graph

* af6b837 (HEAD -> master, tag: v-1.2) Updating for v-1.2
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

git reset HEAD^1
Unstaged changes after reset:
M	file2

git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file2

no changes added to commit (use "git add" and/or "git commit -a")

git log --oneline --decorate --graph

* 6a09e40 (HEAD -> master, tag: v-1.1) Tweaking a file
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

```

Reflog is a log of all the changes made

```
git reflog

6a09e40 (HEAD -> master, tag: v-1.1) HEAD@{0}: reset: moving to HEAD^1
af6b837 (tag: v-1.2) HEAD@{1}: commit: Updating for v-1.2
6a09e40 (HEAD -> master, tag: v-1.1) HEAD@{2}: commit: Tweaking a file
b4ff9f3 (tag: v-1.0) HEAD@{3}: reset: moving to HEAD
b4ff9f3 (tag: v-1.0) HEAD@{4}: checkout: moving from newchanges to master
b4ff9f3 (tag: v-1.0) HEAD@{5}: reset: moving to HEAD
b4ff9f3 (tag: v-1.0) HEAD@{6}: checkout: moving from master to newchanges
b4ff9f3 (tag: v-1.0) HEAD@{7}: reset: moving to HEAD
b4ff9f3 (tag: v-1.0) HEAD@{8}: reset: moving to HEAD
b4ff9f3 (tag: v-1.0) HEAD@{9}: reset: moving to HEAD
b4ff9f3 (tag: v-1.0) HEAD@{10}: reset: moving to HEAD
b4ff9f3 (tag: v-1.0) HEAD@{11}: commit: Done with the WIP2
0ce9769 HEAD@{12}: commit: Done with the WIP2
b419d7e HEAD@{13}: commit: Emergency fix
c8d946a HEAD@{14}: reset: moving to HEAD
c8d946a HEAD@{15}: reset: moving to HEAD
c8d946a HEAD@{16}: commit: Done with the WIP
b8e1096 HEAD@{17}: commit: Quick fix
ddef7ba (bigtrouble) HEAD@{18}: reset: moving to HEAD
ddef7ba (bigtrouble) HEAD@{19}: merge bigtrouble: Fast-forward
0861e5d HEAD@{20}: checkout: moving from bigtrouble to master
ddef7ba (bigtrouble) HEAD@{21}: commit: change after rebase
9066d92 HEAD@{22}: rebase finished: returning to refs/heads/bigtrouble
9066d92 HEAD@{23}: rebase: fb adding trouble to file
0861e5d HEAD@{24}: rebase: checkout master
8b32aa4 HEAD@{25}: rebase: updating HEAD
8b32aa4 HEAD@{26}: rebase: updating HEAD
0861e5d HEAD@{27}: rebase: checkout master
8b32aa4 HEAD@{28}: checkout: moving from master to bigtrouble
0861e5d HEAD@{29}: commit: mb conflicting changes brewing
0c5efff HEAD@{30}: checkout: moving from bigtrouble to master
8b32aa4 HEAD@{31}: commit: fb adding trouble to file
0c5efff HEAD@{32}: checkout: moving from master to bigtrouble
0c5efff HEAD@{33}: commit: mb before rebase conflicts
42f5865 HEAD@{34}: merge myfeature: Fast-forward
02064fc (tag: v-0.9-beta) HEAD@{35}: checkout: moving from myfeature to master
42f5865 HEAD@{36}: commit: Another change
c671488 HEAD@{37}: rebase finished: returning to refs/heads/myfeature
c671488 HEAD@{38}: rebase: feature
02064fc (tag: v-0.9-beta) HEAD@{39}: rebase: checkout master
156f433 HEAD@{40}: checkout: moving from master to myfeature
02064fc (tag: v-0.9-beta) HEAD@{41}: commit: edit
fa79281 HEAD@{42}: checkout: moving from myfeature to master
156f433 HEAD@{43}: commit: feature
fa79281 HEAD@{44}: checkout: moving from master to myfeature
fa79281 HEAD@{45}: commit (merge): merge conflict
14ae637 HEAD@{46}: commit: yet another change
620ff72 HEAD@{47}: checkout: moving from conflicting-change to master
5d495a8 (conflicting-change) HEAD@{48}: commit: Conflicting change
620ff72 HEAD@{49}: checkout: moving from master to conflicting-change
620ff72 HEAD@{50}: merge simple-change: Merge made by the 'recursive' strategy.
19ab207 HEAD@{51}: commit: file2
9521a8d HEAD@{52}: checkout: moving from simple-change to master
83f3159 HEAD@{53}: commit: simple change
9521a8d HEAD@{54}: checkout: moving from master to simple-change
9521a8d HEAD@{55}: merge other-change: Merge made by the 'recursive' strategy.
5040750 HEAD@{56}: checkout: moving from other-change to master
a4d0bc9 HEAD@{57}: commit: Other change
5040750 HEAD@{58}: checkout: moving from master to other-change
5040750 HEAD@{59}: checkout: moving from other-change to master
5040750 HEAD@{60}: checkout: moving from master to other-change
5040750 HEAD@{61}: merge some-change: Fast-forward
84f00a8 HEAD@{62}: checkout: moving from some-change to master
5040750 HEAD@{63}: commit: Change file
84f00a8 HEAD@{64}: checkout: moving from master to some-change
84f00a8 HEAD@{65}: checkout: moving from newbranch to master
84f00a8 HEAD@{66}: checkout: moving from master to newbranch
84f00a8 HEAD@{67}: commit: add file
4e4ddba HEAD@{68}: commit: remove file
e980c5c HEAD@{69}: commit: Add file
aa6daef HEAD@{70}: commit: moved file
a6a2066 HEAD@{71}: commit: Yello
a635aaf HEAD@{72}: commit (initial): initial
```

Reset to state before removing the last commit.

```
git reset af6b837

git log --oneline --decorate --graph

* af6b837 (HEAD -> master, tag: v-1.2) Updating for v-1.2
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

```

Different resets:

- Mixed reset
  - Reset staging area and point the head to new location
- Hard reset
  - Reset local working directory, staging area and point the head to new location
- Soft reset 
  - Point the head to new location