# Creating Git repo

We are going to create a repository on GitHub:

https://github.com/daviskregers/multi-k8s

Then `cd` into it and push the code:

```
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
	README.md
	client/
	k8s/
	server/
	worker/

nothing added to commit but untracked files present (use "git add" to track)
 $ git add .
 $ git commit -m "add files"
[master (root-commit) acadafe] add files
 43 files changed, 17403 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 README.md
 create mode 100755 client/.gitignore
 create mode 100644 client/Dockerfile
 create mode 100644 client/Dockerfile.dev
 create mode 100755 client/README.md
 create mode 100644 client/nginx/default.conf
 create mode 100644 client/package-lock.json
 create mode 100644 client/package.json
 create mode 100755 client/public/favicon.ico
 create mode 100755 client/public/index.html
 create mode 100755 client/public/manifest.json
 create mode 100644 client/src/App.css
 create mode 100644 client/src/App.js
 create mode 100644 client/src/App.test.js
 create mode 100644 client/src/Fib.js
 create mode 100644 client/src/OtherPage.js
 create mode 100644 client/src/index.css
 create mode 100644 client/src/index.js
 create mode 100644 client/src/logo.svg
 create mode 100644 client/src/registerServiceWorker.js
 create mode 100755 client/src/serviceWorker.js
 create mode 100644 k8s/client-cluster-ip-service.yaml
 create mode 100644 k8s/client-deployment.yaml
 create mode 100644 k8s/database-persistent-volume-claim.yaml
 create mode 100644 k8s/ingress-service.yaml
 create mode 100644 k8s/postgres-cluster-ip-service.yaml
 create mode 100644 k8s/postgres-deployment.yaml
 create mode 100644 k8s/redis-cluster-ip-service.yaml
 create mode 100644 k8s/redis-deployment.yaml
 create mode 100644 k8s/server-cluseter-ip-service.yaml
 create mode 100644 k8s/server-deployment.yaml
 create mode 100644 k8s/worker-deployment.yaml
 create mode 100644 server/Dockerfile
 create mode 100644 server/Dockerfile.dev
 create mode 100644 server/index.js
 create mode 100644 server/keys.js
 create mode 100644 server/package.json
 create mode 100644 worker/Dockerfile
 create mode 100644 worker/Dockerfile.dev
 create mode 100644 worker/index.js
 create mode 100644 worker/keys.js
 create mode 100644 worker/package.json
 $ git remote add origin git@github.com:daviskregers/multi-k8s.git
 $ git push -u origin master
Enumerating objects: 50, done.
Counting objects: 100% (50/50), done.
Delta compression using up to 8 threads
Compressing objects: 100% (49/49), done.
Writing objects: 100% (50/50), 150.76 KiB | 1.17 MiB/s, done.
Total 50 (delta 8), reused 0 (delta 0)
remote: Resolving deltas: 100% (8/8), done.
To github.com:daviskregers/multi-k8s.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

```