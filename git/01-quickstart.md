# Git Quickstart

You can confirm that git is installed by using:

```
git version
```

Git requires two bits of information before we can do things - name and email address.

If it's not provided, git will try to automatically figure it out, but this process is unreliable.

```
git config --global user.name "Your name"
git config --global user.email "your@email.com"
```

The changes can be verified by using command:

```
git config --global --list
```

A project can be downloaded from a repository to local machine by using clone command:

```
git clone https://github.com/daviskregers/git.git
```

```
davis@davis-arch  ~/projects  git clone https://github.com/daviskregers/git.git
Cloning into 'git'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
 davis@davis-arch  ~/projects  cd git 
 davis@davis-arch  ~/projects/git   master  ls
README.md
 davis@davis-arch  ~/projects/git   master  
```

You can check the status of the repository by using `status` command.

```
davis@davis-arch  ~/projects/git   master  git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

```

You can see that you're on the master branch and it is up-to-date with the remote's master branch. There are no working directory changes.

If we create a new file, we'll see it in the `status`

```
davis@davis-arch  ~/projects/git   master  echo "Test Git Quick Start demo" >> start.txt
 davis@davis-arch  ~/projects/git   master  ls
README.md  start.txt
 davis@davis-arch  ~/projects/git   master  cat start.txt 
Test Git Quick Start demo
 davis@davis-arch  ~/projects/git   master  git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	start.txt

nothing added to commit but untracked files present (use "git add" to track)
 davis@davis-arch  ~/projects/git   master  
```

If we want to add the file to the staging area, we use 

```
davis@davis-arch  ~/projects/git   master  git add start.txt
 davis@davis-arch  ~/projects/git   master ✚  git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   start.txt
```

Now we can make a commit from the staging area by using:

```
davis@davis-arch  ~/projects/git   master ✚  git commit -m "Adding start text file"
[master 9d8a074] Adding start text file
 1 file changed, 1 insertion(+)
 create mode 100644 start.txt
```

Now, when using `status`

```
davis@davis-arch  ~/projects/git   master  git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

We can see that there is nothing to commit, our master branch is ahead of `origin/master` by 1 commit.

Now we can `push` to upload it to the repository.

```
davis@davis-arch  ~/projects/git   master  git push origin master
Username for 'https://github.com': ...
Password for '...@github.com': 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 326 bytes | 326.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/daviskregers/git.git
   2c533a8..9d8a074  master -> master
```
The origin is a remote name, which was created automatically when we cloned, the master is a branch on the remote.

If everything is correct, we can see the file in the remote repository.