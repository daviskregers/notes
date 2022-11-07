# Git aliases

We can create our own commands that will compress long commands like

```
git log --all --graph --decorate --oneline
```

```
 master  git hist
git: 'hist' is not a git command. See 'git --help'.
 master  git config --global alias.hist "log --all --graph --decorate --oneline" 
  master  git hist
```

Not that commands inside the alias does not contain the `git` prefix.

```
* aa6daef (HEAD -> master) moved file
* a6a2066 another commit
* a635aaf initial
```
