## Adding git to an existing project

If we have a directory that already has files in it and we want to version it using git, we can:

```
davis@davis-arch  ~/projects  mkdir existing-project
davis@davis-arch  ~/projects  cd existing-project 
davis@davis-arch  ~/projects/existing-project  touch file1
davis@davis-arch  ~/projects/existing-project  touch file2
davis@davis-arch  ~/projects/existing-project  ls -al
total 8
drwxr-xr-x  2 davis www-data 4096 Jan 21 20:12 .
drwxr-xr-x 20 davis www-data 4096 Jan 21 20:12 ..
-rw-r--r--  1 davis www-data    0 Jan 21 20:12 file1
-rw-r--r--  1 davis www-data    0 Jan 21 20:12 file2
davis@davis-arch  ~/projects/existing-project  git init
Initialized empty Git repository in /home/davis/projects/existing-project/.git/
davis@davis-arch  ~/projects/existing-project   master  ls -al
total 12
drwxr-xr-x  3 davis www-data 4096 Jan 21 20:12 .
drwxr-xr-x 20 davis www-data 4096 Jan 21 20:12 ..
-rw-r--r--  1 davis www-data    0 Jan 21 20:12 file1
-rw-r--r--  1 davis www-data    0 Jan 21 20:12 file2
drwxr-xr-x  7 davis www-data 4096 Jan 21 20:12 .git
davis@davis-arch  ~/projects/existing-project   master  git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file1
	file2

nothing added to commit but untracked files present (use "git add" to track)

```

Now we can commit the files recursively:

```
davis@davis-arch  ~/projects/existing-project   master  git add .
davis@davis-arch  ~/projects/existing-project   master ✚  git commit -m "Initial commit"
[master (root-commit) 4bd5a61] Initial commit
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file1
 create mode 100644 file2
davis@davis-arch  ~/projects/existing-project   master  git status
On branch master
nothing to commit, working tree clean
```

To remove the git versioning:

```
davis@davis-arch  ~/projects/existing-project   master  rm -rf .git
davis@davis-arch  ~/projects/existing-project  ls -al  
total 8
drwxr-xr-x  2 davis www-data 4096 Jan 21 20:15 .
drwxr-xr-x 20 davis www-data 4096 Jan 21 20:12 ..
-rw-r--r--  1 davis www-data    0 Jan 21 20:12 file1
-rw-r--r--  1 davis www-data    0 Jan 21 20:12 file2
```