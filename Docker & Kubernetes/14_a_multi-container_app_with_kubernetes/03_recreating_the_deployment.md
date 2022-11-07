# Recreating the deployment

We are going to clean up the previously copied project removing files:

```
$ rm .travis.yml 
$ rm docker-compose.yml 
$ rm -r .elasticbeanstalk
$ rm Dockerrun.aws.json 
$ rm -r nginx 
$ mkdir k8s
```

Now we'll create a new deployment `k8s/client-deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: client-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      component: web
  template:
    metadata:
      labels:
        component: web
    spec:
      containers:
        - name: client
          image: deiveris/multi-client
          ports:
            - containerPort: 3000
```
