# Pull with rebase

When there are changes on the remote and we have made changes, we can merge them using fetch:

```
git fetch origin master
```

But, if we want to make so our changes come after the changes in remote, we can use pull with rebase:

```
git pull --rebase origin master
```

