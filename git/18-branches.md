# Branching

So far all the changes has been made on the master branch, which is not the best practice. We should make our changes into feature branches, then merge them into the master branch, once the features has been stabilized.

To get a list of all local and remote branches:

```
git branch -a
```

To create a new branch:

```
git branch newbranch
```

```
git branch -a

* master
  newbranch

```

Switch branches

```
git checkout newbranch
```

```
git branch -a

  master
* newbranch

```

```
git log --oneline --decorate

84f00a8 (HEAD -> newbranch, master) add file
4e4ddba remove file
e980c5c Add file
aa6daef moved file
a6a2066 Yello
a635aaf initial

```

rename branch

```
git branch -m newbranch oldbranch
```

delete branch

```
git branch -d oldbranch
```