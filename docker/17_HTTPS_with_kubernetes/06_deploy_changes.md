# Deploy changes

```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	k8s/certificate.yaml
	k8s/issuer.yaml

nothing added to commit but untracked files present (use "git add" to track)
$ git add .
$ git commit -m "added certificateand issuer"
[master 56fb459] added certificate and issuer
 2 files changed, 29 insertions(+)
 create mode 100644 k8s/certificate.yaml
 create mode 100644 k8s/issuer.yaml
$ git push origin master
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 794 bytes | 794.00 KiB/s, done.
Total 5 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:daviskregers/multi-k8s.git
   3dee337..56fb459  master -> master
```

Now the travis will update the cluster.