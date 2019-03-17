# Limitations in config updates

If we change the `client-pod.yaml` from:

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

to

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
        - containerPort: 9999
```

And update:

```
kubectl apply -f client-pod.yaml
```

It will throw an error saying:

```
The Pod "client-pod" is invalid: spec: Forbidden: pod updates may not change fields other than `spec.containers[*].image`, `spec.initContainers[*].image`, `spec.activeDeadlineSeconds` or `spec.tolerations` (only additions to existing tolerations)
```

So, we are only allowed to change these 4 different properties.