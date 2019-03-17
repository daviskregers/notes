# Applying deployment

Since we still have the pod running from previous attempts, we are going to remove it:

```
kubectl delete -f <config file>
```

```
$ kubectl delete -f client-pod.yaml 
pod "client-pod" deleted
$ kubectl get pods
No resources found.
```

Now we'll apply the deployment:

```
$ kubectl apply -f client-deployment.yaml 
deployment.apps/client-deployment created
$ kubectl get pods
NAME                                 READY   STATUS    RESTARTS   AGE
client-deployment-7bf8c9b5c5-48b4v   1/1     Running   0          5s
$ kubectl get deployments
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
client-deployment   1/1     1            1           40s
```

And we can verify that we can still access the nginx site:

```
$ minikube ip
192.168.99.101
```

Open up `http://192.168.99.101:31515/`

![](../../images/2019-03-17-17-01-53.png)