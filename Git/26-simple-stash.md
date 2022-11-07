# Simple stash

A stash is used whenever you have modified something and you need to change something else now. The changes made previously are WIP and aren't done. You can use stash to save them and work on something else.

```  master  git status
On branch master
nothing to commit, working tree clean
  master  ls
file  file2  l1  l3-file
  master  echo "Stash this" >> file
  master ●  git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file

no changes added to commit (use "git add" and/or "git commit -a")
  master ●  git stash     
Saved working directory and index state WIP on master: ddef7ba change after rebase
  master  git status
On branch master
nothing to commit, working tree clean
  master  cat file
initial
change
other change
simple change
conflicting
yet another change
edit
another edit
change
other change
something else
Yet another change
  master  echo "Important change" >> file
  master ●  git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file

no changes added to commit (use "git add" and/or "git commit -a")
  master ●  git commit -am "Quick fix"
[master b8e1096] Quick fix
 1 file changed, 1 insertion(+)
  master  git status
On branch master
nothing to commit, working tree clean
  master  git stash apply 
Auto-merging file
CONFLICT (content): Merge conflict in file
  master ●✚  git mergetool
Merging:
file

Normal merge conflict for 'file':
  {local}: modified file
  {remote}: modified file
QString::arg: 1 argument(s) missing in %1 - %2
  master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   file

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file.orig

  master ✚  rm file.orig
  master ✚  git commit -am "Done with the WIP"
[master c8d946a] Done with the WIP
 1 file changed, 1 insertion(+)
  master  git status
On branch master
nothing to commit, working tree clean
  master  git stash list

 stash@{0}: WIP on master: ddef7ba change after rebase

  master  git stash drop
Dropped refs/stash@{0} (1b28e504f2725e160d03c9174e9b6a26dae4771e)


```



