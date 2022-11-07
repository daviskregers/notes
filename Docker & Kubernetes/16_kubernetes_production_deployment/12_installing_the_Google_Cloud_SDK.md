# Installing the Google Cloud SDK

We are going to create a new `.travis.yaml` file ine the project directory.


```
touch .travis.yaml
```

Then we are going to tell it to install Google Cloud SDK and log into it.

```yaml
sudo: required
services:
  - docker
before_install:
  - curl https://sdk.cloud.google.com | bash > /dev/null;
  - source $HOME/google-cloud-sdk/path.bash.inc
  - gcloud components update kubectl
  - gcloud auth activate-service-account --key-file service-account.json
```