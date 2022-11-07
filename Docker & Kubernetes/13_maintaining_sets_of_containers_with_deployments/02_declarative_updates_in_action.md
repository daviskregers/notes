# Declarative updates in action

We are going to find the `client-pod.yaml` file:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: client-pod
  labels:
    component: web
spec:
  containers:
    - name: client
      image: deiveris/multi-client
      ports:
        - containerPort: 3000
```

And modify it:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: client-pod
  labels:
    component: web
spec:
  containers:
    - name: client
      image: deiveris/multi-worker
      ports:
        - containerPort: 3000
```

Then run the command:

```
$ kubectl apply -f client-pod.yaml 
pod/client-pod configured
```

We can run the command to verify the change

```
kubectl get pods
```

We can use the command to get detailed info:

```
kubectl describe <object type> <object name>
```

