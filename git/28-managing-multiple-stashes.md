# Managing multiple stashes

```
 master  git status
On branch master
nothing to commit, working tree clean
 master  ls
file  file2  file3  l1  l3-file
 master  echo "Change" >> file
 master ●  git stash save "simple change"
Saved working directory and index state On master: simple change
 master  echo "Other change" >> file2
 master ●  git stash save "other change" 
Saved working directory and index state On master: other change
 master  echo "Yet another change" >> file3 
 master ●  git stash save "yet another change"  
Saved working directory and index state On master: yet another change
```

```
git stash list

stash@{0}: On master: yet another change
stash@{1}: On master: other change
stash@{2}: On master: simple change
stash@{3}: WIP on master: c8d946a Done with the WIP
```

Note that the list is reversed, index 0 is the last stash.

```
git stash show stash@{0}

 file3 | 1 +
 1 file changed, 1 insertion(+)
```

```
git stash show stash@{1}

 file2 | 1 +
 1 file changed, 1 insertion(+)
```

Reapply stashes

```
 master  git status
On branch master
nothing to commit, working tree clean
 master  git stash apply stash@{1}
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file2

no changes added to commit (use "git add" and/or "git commit -a")
 master ●  git stash list     

stash@{0}: On master: yet another change
stash@{1}: On master: other change
stash@{2}: On master: simple change
stash@{3}: WIP on master: c8d946a Done with the WIP

git stash drop stash@{1}
git stash clear

```