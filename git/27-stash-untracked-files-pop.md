# Stashing untracked files and using pop

Normally stashing works with tracked files:

``` master  git ls-files
file
file2
l1/file1
l1/file1-2
l1/l2/file-2-2
l1/l2/file2
l1/l2/l3/file3
l1/l2/l3/l4/file-4-2
l1/l2/l3/l4/file4
l3-file
 master  echo "Some change" >> file2
 master ●  git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file2

no changes added to commit (use "git add" and/or "git commit -a")
 master ●  echo "new file" >> file3 
 master ●  git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file2

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file3

no changes added to commit (use "git add" and/or "git commit -a")
 master ●  git stash
Saved working directory and index state WIP on master: c8d946a Done with the WIP
 master  git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file3

nothing added to commit but untracked files present (use "git add" to track)
 master  git stash apply 
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   file2

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file3

no changes added to commit (use "git add" and/or "git commit -a")
 master ●  git stash drop
Dropped refs/stash@{0} (fa963e048c53b322f8715e497aea64030dea9261)

```

We can do a workaround for this:

```
 master ●  git stash -u
Saved working directory and index state WIP on master: c8d946a Done with the WIP
 master  git status
On branch master
nothing to commit, working tree clean
 master  echo "Yet another change" >> file2
 master ●  git commit -am "Emergency fix"
[master b419d7e] Emergency fix
 1 file changed, 1 insertion(+)
 master  git status
On branch master
nothing to commit, working tree clean
 master  git stash pop     
Auto-merging file2
CONFLICT (content): Merge conflict in file2
 master ●✚  git mergetool
Merging:
file2

Normal merge conflict for 'file2':
  {local}: modified file
  {remote}: modified file
QString::arg: 1 argument(s) missing in %1 - %2
 master ✚  cat file2
file2
feature
Some change
Yet another change
 master ✚  git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   file2

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file2.orig
	file3


```