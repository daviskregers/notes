# Starting by joining an existing project

You can locate a repository you want to work on, for example, on GitHub, and click on the `fork` option, this will create an own personal copy of the repository in our account. Then you can get the `clone url` to download it to your local machine.

```
davis@davis-arch  ~/projects/learning-git  git clone https://github.com/daviskregers/notes.git
Cloning into 'notes'...
remote: Enumerating objects: 303, done.
remote: Counting objects: 100% (303/303), done.
remote: Compressing objects: 100% (276/276), done.
remote: Total 303 (delta 84), reused 218 (delta 10), pack-reused 0
Receiving objects: 100% (303/303), 4.81 MiB | 1.99 MiB/s, done.
Resolving deltas: 100% (84/84), done.
davis@davis-arch  ~/projects/learning-git  ls -al
total 12
drwxr-xr-x  3 davis www-data 4096 Jan 21 20:17 .
drwxr-xr-x 20 davis www-data 4096 Jan 21 20:17 ..
drwxr-xr-x 14 davis www-data 4096 Jan 21 20:17 notes
davis@davis-arch  ~/projects/learning-git  cd notes 
davis@davis-arch  ~/projects/learning-git/notes   master  ls -al
total 60
drwxr-xr-x 14 davis www-data 4096 Jan 21 20:17 .
drwxr-xr-x  3 davis www-data 4096 Jan 21 20:17 ..
drwxr-xr-x  2 davis www-data 4096 Jan 21 20:17 aws
drwxr-xr-x  3 davis www-data 4096 Jan 21 20:17 databases
drwxr-xr-x  2 davis www-data 4096 Jan 21 20:17 docker
drwxr-xr-x  2 davis www-data 4096 Jan 21 20:17 elixir
drwxr-xr-x  3 davis www-data 4096 Jan 21 20:17 frontend
drwxr-xr-x  8 davis www-data 4096 Jan 21 20:17 .git
drwxr-xr-x  2 davis www-data 4096 Jan 21 20:17 images
drwxr-xr-x  2 davis www-data 4096 Jan 21 20:17 javascript
drwxr-xr-x  6 davis www-data 4096 Jan 21 20:17 linux
drwxr-xr-x  2 davis www-data 4096 Jan 21 20:17 osx
drwxr-xr-x  3 davis www-data 4096 Jan 21 20:17 php
-rw-r--r--  1 davis www-data   34 Jan 21 20:17 README.md
drwxr-xr-x  2 davis www-data 4096 Jan 21 20:17 rust
davis@davis-arch  ~/projects/learning-git/notes   master  git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```