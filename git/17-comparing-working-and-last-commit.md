# Comparing working directory and repository (last commit)

```
  master  git status       
On branch master
nothing to commit, working tree clean
  master  echo "initial" >> file
  master  git add file
  master ✚  git commit -m "add file"
[master 84f00a8] add file
 1 file changed, 1 insertion(+)
 create mode 100644 file
  master  echo "something" >> file
```

```
git diff HEAD