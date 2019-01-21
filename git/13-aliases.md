# Git aliases

We can create our own commands that will compress long commands like

```
git log --all --graph --decorate --oneline
```

```
davis@davis-arch  ~/projects/learning-git/project   master  git hist
git: 'hist' is not a git command. See 'git --help'.
davis@davis-arch  ~/projects/learning-git/project   master  git config --global alias.hist "log --all --graph --decorate --oneline" 
 davis@davis-arch  ~/projects/learning-git/project   master  git hist
```

Not that commands inside the alias does not contain the `git` prefix.

```
* aa6daef (HEAD -> master) moved file
* a6a2066 another commit
* a635aaf initial
```
