# Encrypting a service account file

We are continuing working inside the Travis CLI docker container from previous section:

```
# travis login --pro
```

Make sure that you have copied the service account credential json file to the project directory.

```
# ls
README.md  client  k8s	multi-k8s-236808-e22ce5e7f920.json  server  worker
# mv multi-k8s-236808-e22ce5e7f920.json service-account.json
# ls
README.md  client  k8s	server	service-account.json  worker
```

Now we encrypt the file and specify that we want it to tie it up to our repository (note that it is case sensitive) :

```
# travis encrypt-file --pro service-account.json
encrypting service-account.json for daviskregers/multi-k8s
storing result as service-account.json.enc
storing secure env variables for decryption

Please add the following to your build script (before_install stage in your .travis.yml, for instance):

    openssl aes-256-cbc -K $encrypted_0c35eebf403c_key -iv $encrypted_0c35eebf403c_iv -in service-account.json.enc -out service-account.json -d

Pro Tip: You can add it automatically by running with --add.

Make sure to add service-account.json.enc to the git repository.
Make sure not to add service-account.json to the git repository.
Commit all changes to your .travis.yml.

```

We are going to copy the command:

```
openssl aes-256-cbc -K $encrypted_0c35eebf403c_key -iv $encrypted_0c35eebf403c_iv -in service-account.json.enc -out service-account.json -d
```

and copy it into the .travis.yaml

```yaml
sudo: required
services:
  - docker
before_install:
  - openssl aes-256-cbc -K $encrypted_0c35eebf403c_key -iv $encrypted_0c35eebf403c_iv -in service-account.json.enc -out service-account.json -d
  - curl https://sdk.cloud.google.com | bash > /dev/null;
  - source $HOME/google-cloud-sdk/path.bash.inc
  - gcloud components update kubectl
  - gcloud auth activate-service-account --key-file service-account.json
```

```
# ls
README.md  client  k8s	server	service-account.json  service-account.json.enc	worker
```

Now we need to delete the orginal json file and commit the `travis.yml` and the encrypted account.

```
$ rm service-account.json
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.travis.yaml
	service-account.json.enc

nothing added to commit but untracked files present (use "git add" to track)
$ git add .
$ git commit -m "travis"
[master 7114a57] travis
 2 files changed, 9 insertions(+)
 create mode 100644 .travis.yaml
 create mode 100644 service-account.json.enc
```