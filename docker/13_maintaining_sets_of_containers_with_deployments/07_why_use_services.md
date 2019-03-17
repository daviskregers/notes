# Why use services?

Now when we have an idea on how deployments work, we can try to understand the need of services.

```
$ kubectl get pods -o wide
NAME                                 READY   STATUS    RESTARTS   AGE     IP           NODE       NOMINATED NODE   READINESS GATES
client-deployment-7bf8c9b5c5-48b4v   1/1     Running   0          4m37s   172.17.0.4   minikube   <none>           <none>
```

As we can see from the table, every single pod gets a seperate IP address. When it is updated, it can get an entirely differnt IP address.

The service will look at every pod that matches it's `selector` and then automatically route traffic to it.
