# Unique deployment images

We are create the `deploy.sh` file that Travis CI is going to execute:

```bash
# Build images
docker build -t deiveris/multi-client -f ./client/Dockerfile ./client
docker build -t deiveris/multi-server -f ./server/Dockerfile ./server
docker build -t deiveris/multi-worker -f ./worker/Dockerfile ./worker

# Push to Docker Hub
docker push deiveris/multi-client 
docker push deiveris/multi-server
docker push deiveris/multi-woker

# Apply configrations
kubectl apply -f k8s

# Imperatively set latest images on each deployment
kubectl set image deployments/server-deployment server=deiveris/multi-server
```

This deployment will not work perfectly, because it will set the `latest` tag to the deployments. Since the `latest` was already previously set, there will be no changes.

This can be fixed by using a git commit SHA checksum. 
Before we apply this, we will create new environment variables for travis:

```yaml
sudo: required
services:
  - docker
env:
  global:
    - SHA = $(git rev-parse HEAD)
    - CLOUDSDK_CORE_DISABLE_PROMPTS=1
before_install:
  - openssl aes-256-cbc -K $encrypted_0c35eebf403c_key -iv $encrypted_0c35eebf403c_iv -in service-account.json.enc -out service-account.json -d
  - curl https://sdk.cloud.google.com | bash > /dev/null;
  - source $HOME/google-cloud-sdk/path.bash.inc
  - gcloud components update kubectl
  - gcloud auth activate-service-account --key-file service-account.json
  - gcloud config set project multi-k8s-236808
  - gcloud config set compute/zone europe-west1-c
  - gcloud container clusters get-credentials multi-cluster
  - echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_ID" --password-stdin
  - docker build -t deiveris/react-test -f ./client/Dockerfile.dev ./client

script:
  - docker run deiveris/react-test npm test -- --coverage

deploy:
  provider: script
  script: bash ./deploy.sh
  on: 
    branch: master
```

Now the deployment script will look like this:

```bash
# Build images
docker build -t deiveris/multi-client:latest -t deiveris/multi-client:$SHA -f ./client/Dockerfile ./client
docker build -t deiveris/multi-server:latest -t deiveris/multi-server:$SHA -f ./server/Dockerfile ./server
docker build -t deiveris/multi-worker:latest -t deiveris/multi-worker:$SHA -f ./worker/Dockerfile ./worker

# Push to Docker Hub

docker push deiveris/multi-client:latest
docker push deiveris/multi-server:latest
docker push deiveris/multi-woker:latest

docker push deiveris/multi-client:$SHA
docker push deiveris/multi-server:$SHA
docker push deiveris/multi-woker:$SHA

# Apply configrations
kubectl apply -f k8s

# Imperatively set latest images on each deployment
kubectl set image deployments/server-deployment server=deiveris/multi-server:$SHA
kubectl set image deployments/client-deployment client=deiveris/multi-client:$SHA
kubectl set image deployments/worker-deployment worker=deiveris/multi-worker:$SHA
```
