# Applying multiple files with Kubectl

Just to make sure everything is fine, we'll load both of previously created files.

First, we are going to delete deployments from previous section.

```
$ kubectl get deployments
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
client-deployment   1/1     1            1           114m
$ kubectl delete deployment client-deployment
deployment.extensions "client-deployment" deleted
$ kubectl get deploymens
error: the server doesn't have a resource type "deploymens"
 $ kubectl get deployments
No resources found.
$ kubectl get pods
No resources found.
```

```
$ kubectl get services
NAME               TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
client-node-port   NodePort    10.106.105.100   <none>        3050:31515/TCP   3h12m
kubernetes         ClusterIP   10.96.0.1        <none>        443/TCP          4h
$ kubectl delete service client-node-port
service "client-node-port" deleted
$ kubectl get services                   
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   4h
```

Now, when applying, instead of specifying each file separately, we can specify the `k8s` directory.

```
$ kubectl apply -f k8s 
service/client-cluster-ip-service created
deployment.apps/client-deployment created
```

```
$ kubectl get deployments
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
client-deployment   3/3     3            3           32s
$ kubectl get pods
NAME                                 READY   STATUS    RESTARTS   AGE
client-deployment-7bf8c9b5c5-7gcc7   1/1     Running   0          35s
client-deployment-7bf8c9b5c5-96g47   1/1     Running   0          35s
client-deployment-7bf8c9b5c5-qr64m   1/1     Running   0          35s
$ kubectl get services
NAME                        TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
client-cluster-ip-service   ClusterIP   10.101.240.238   <none>        3000/TCP   39s
kubernetes                  ClusterIP   10.96.0.1        <none>        443/TCP    4h2m
```