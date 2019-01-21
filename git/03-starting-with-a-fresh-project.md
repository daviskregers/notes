## Starting  with a fresh project (git init)

In order to start a fresh git repository, you can use the `init` command

```
git init project-name
```

It will create a folder `project-name`.

```
davis@davis-arch  ~/projects/learning-git  git init project
Initialized empty Git repository in /home/davis/projects/learning-git/project/.git/
davis@davis-arch  ~/projects/learning-git  ls         
project
davis@davis-arch  ~/projects/learning-git  cd project 
 master  ls
 master  git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
 master  ls -al
total 12
drwxr-xr-x 3 davis www-data 4096 Jan 21 20:04 .
drwxr-xr-x 3 davis www-data 4096 Jan 21 20:04 ..
drwxr-xr-x 7 davis www-data 4096 Jan 21 20:04 .git
 master  
```

You can see that a diretory called `project` is created, it contains the `.git` hidden directory.
