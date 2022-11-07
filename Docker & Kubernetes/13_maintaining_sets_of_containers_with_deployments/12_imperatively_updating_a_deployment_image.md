# Imperatively updating a deployment image

We'll rebuild the image once more with a tag `v5`:

```
$ docker build -t deiveris/multi-client:v5 .
Sending build context to Docker daemon  233.9MB
Step 1/10 : FROM node:11.10.1-alpine as builder
 ---> 842caa90d45b
Step 2/10 : WORKDIR '/app'
 ---> Using cache
 ---> 38570625fbce
Step 3/10 : COPY package*.json ./
 ---> Using cache
 ---> 37c5b6da3bf9
Step 4/10 : RUN npm install
 ---> Using cache
 ---> 0f5c82488b91
Step 5/10 : COPY . .
 ---> Using cache
 ---> 5f86605194af
Step 6/10 : RUN npm run build
 ---> Using cache
 ---> eece77ba22ec
Step 7/10 : FROM nginx
 ---> 881bd08c0b08
Step 8/10 : EXPOSE 3000
 ---> Using cache
 ---> f71625d87e8d
Step 9/10 : COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
 ---> Using cache
 ---> 2212a0b54395
Step 10/10 : COPY --from=builder /app/build /usr/share/nginx/html
 ---> Using cache
 ---> 1019422ed773
Successfully built 1019422ed773
Successfully tagged deiveris/multi-client:v5

$ docker push deiveris/multi-client:v5
The push refers to repository [docker.io/deiveris/multi-client]
d244568552e6: Layer already exists 
c6e5f4e5b580: Layer already exists 
3e9eb35b1c23: Layer already exists 
c59b3ca455e3: Layer already exists 
6744ca1b1190: Layer already exists 
v5: digest: sha256:5dff734172a3ea0d1fd8f6fa91bb140f537f823afb7ac86cabc0bade2e9d1066 size: 1365

```

Now we are going to use an imperative command to update the image:

```
kubectl set image <object type>/<object name> <container name> = <new image to use>
```

```
$ kubectl apply -f client-deployment.yaml
deployment.apps/client-deployment unchanged
$ kubectl set image deployment/client-deployment client=deiveris/multi-client:v5
deployment.extensions/client-deployment image updated
$ kubectl get pods
NAME                                 READY   STATUS        RESTARTS   AGE
client-deployment-7bf8c9b5c5-ptj4h   0/1     Terminating   0          21m
client-deployment-7fbcbb74f6-x66wp   1/1     Running       0          8s
```
