# Comparing working directory and repository (last commit)

```
 davis@davis-arch  ~/projects/learning-git/project   master  git status       
On branch master
nothing to commit, working tree clean
 davis@davis-arch  ~/projects/learning-git/project   master  echo "initial" >> file
 davis@davis-arch  ~/projects/learning-git/project   master  git add file
 davis@davis-arch  ~/projects/learning-git/project   master ✚  git commit -m "add file"
[master 84f00a8] add file
 1 file changed, 1 insertion(+)
 create mode 100644 file
 davis@davis-arch  ~/projects/learning-git/project   master  echo "something" >> file
```

```
git diff HEAD