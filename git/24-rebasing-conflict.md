# Rebasing conflict

```
 davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master
nothing to commit, working tree clean
 davis@davis-arch  ~/projects/learning-git/project   master  echo "change" >> file
 davis@davis-arch  ~/projects/learning-git/project   master ●  git commit -am "mb before rebase conflicts"
[master 0c5efff] mb before rebase conflicts
 1 file changed, 1 insertion(+)
 davis@davis-arch  ~/projects/learning-git/project   master  git checkout -b bigtrouble
Switched to a new branch 'bigtrouble'
 davis@davis-arch  ~/projects/learning-git/project   bigtrouble  echo "other change" >> file
 ✘ davis@davis-arch  ~/projects/learning-git/project   bigtrouble ●  git commit -am "fb adding trouble to file"
[bigtrouble 8b32aa4] fb adding trouble to file
 1 file changed, 1 insertion(+)
 davis@davis-arch  ~/projects/learning-git/project   bigtrouble  git checkout master
Switched to branch 'master'
 davis@davis-arch  ~/projects/learning-git/project   master  echo "something else" >> file
 davis@davis-arch  ~/projects/learning-git/project   master ●  git commit -am "mb conflicting changes brewing"
[master 0861e5d] mb conflicting changes brewing
 1 file changed, 1 insertion(+)

```

```
git log --oneline --decorate --all --graph

* 0861e5d (HEAD -> master) mb conflicting changes brewing
| * 8b32aa4 (bigtrouble) fb adding trouble to file
|/  
* 0c5efff mb before rebase conflicts
* 42f5865 Another change
* c671488 feature
* 02064fc edit
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
davis@davis-arch  ~/projects/learning-git/project   bigtrouble  git rebase master
First, rewinding head to replay your work on top of it...
Applying: fb adding trouble to file
Using index info to reconstruct a base tree...
M	file
Falling back to patching base and 3-way merge...
Auto-merging file
CONFLICT (content): Merge conflict in file
error: Failed to merge in the changes.
Patch failed at 0001 fb adding trouble to file
hint: Use 'git am --show-current-patch' to see the failed patch

Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit: run "git rebase --skip".
To abort and get back to the state before "git rebase", run "git rebase --abort".
```

We can abort the rebase and no changes will be made.

```
davis@davis-arch  ~/projects/learning-git/project  ➦ 0861e5d ●✚ >R>  git rebase --abort
```

Or we can resolve the conflict by using the mergetool:

```
git mergetool
```

Select the changes and save.

```
 davis@davis-arch  ~/projects/learning-git/project  ➦ 0861e5d ✚ >R>  git status
rebase in progress; onto 0861e5d
You are currently rebasing branch 'bigtrouble' on '0861e5d'.
  (all conflicts fixed: run "git rebase --continue")

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   file

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file.orig
```

```
davis@davis-arch  ~/projects/learning-git/project  ➦ 0861e5d ✚ >R>  git rebase --continue
Applying: fb adding trouble to file
```

```
git log --oneline --decorate --all --graph

* 9066d92 (HEAD -> bigtrouble) fb adding trouble to file
* 0861e5d (master) mb conflicting changes brewing
* 0c5efff mb before rebase conflicts
* 42f5865 Another change
* c671488 feature
* 02064fc edit
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

Do some additional changes:

```
davis@davis-arch  ~/projects/learning-git/project   bigtrouble  echo "Yet another change" >> file
 davis@davis-arch  ~/projects/learning-git/project   bigtrouble ●  git commit -am "change after rebase"
[bigtrouble ddef7ba] change after rebase
 1 file changed, 1 insertion(+)
 davis@davis-arch  ~/projects/learning-git/project   bigtrouble  git checkout master
Switched to branch 'master'
 davis@davis-arch  ~/projects/learning-git/project   master  git merge bigtrouble 
Updating 0861e5d..ddef7ba
Fast-forward
 file | 2 ++
 1 file changed, 2 insertions(+)
 davis@davis-arch  ~/projects/learning-git/project   master  git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file.orig

nothing added to commit but untracked files present (use "git add" to track)
```

And again, the merge resulted in fast forward merge, no conflict found.
