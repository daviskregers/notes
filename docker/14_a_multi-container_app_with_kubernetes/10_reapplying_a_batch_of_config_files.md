# Reapplying a batch of config files

```
$ kubectl apply -f k8s   
service/client-cluster-ip-service unchanged
deployment.apps/client-deployment unchanged
service/server-cluster-ip-service created
deployment.apps/server-deployment created
deployment.apps/worker-deployment created
```

```
$ kubectl get pods
NAME                                 READY   STATUS             RESTARTS   AGE
client-deployment-7bf8c9b5c5-7gcc7   1/1     Running            0          21m
client-deployment-7bf8c9b5c5-96g47   1/1     Running            0          21m
client-deployment-7bf8c9b5c5-qr64m   1/1     Running            0          21m
server-deployment-d9cb6bcf4-2v75c    1/1     Running            0          26s
server-deployment-d9cb6bcf4-4z7n4    1/1     Running            0          26s
server-deployment-d9cb6bcf4-kp84s    1/1     Running            0          26s
worker-deployment-85896bdb7-cs52k    0/1     CrashLoopBackOff   1          26s
```

```
$ kubectl get deployments
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
client-deployment   3/3     3            3           22m
server-deployment   3/3     3            3           67s
worker-deployment   0/1     1            0           67s
```

```
$ kubectl get services
NAME                        TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
client-cluster-ip-service   ClusterIP   10.101.240.238   <none>        3000/TCP   22m
kubernetes                  ClusterIP   10.96.0.1        <none>        443/TCP    4h25m
server-cluster-ip-service   ClusterIP   10.99.73.109     <none>        5000/TCP   86s
```

We can check logs of pods by using:

```
$kubectl logs server-deployment-d9cb6bcf4-4z7n4

> @ start /app
> node index.js

Listening
{ Error: connect ECONNREFUSED 127.0.0.1:5432
    at TCPConnectWrap.afterConnect [as oncomplete] (net.js:1083:14)
  errno: 'ECONNREFUSED',
  code: 'ECONNREFUSED',
  syscall: 'connect',
  address: '127.0.0.1',
  port: 5432 }
```