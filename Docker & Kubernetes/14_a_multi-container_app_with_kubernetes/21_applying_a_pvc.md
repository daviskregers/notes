# Applying a PVC

Now the last thing is to apply the PVC to our local cluster.

```
$ kubectl apply -f k8s 
service/client-cluster-ip-service unchanged
deployment.apps/client-deployment unchanged
persistentvolumeclaim/database-persistent-volume-claim created
service/postgres-cluster-ip-service unchanged
deployment.apps/postgres-deployment configured
service/redis-cluster-ip-service unchanged
deployment.apps/redis-deployment unchanged
service/server-cluster-ip-service unchanged
deployment.apps/server-deployment unchanged
deployment.apps/worker-deployment unchanged
```

```
$ kubectl get pv
NAME                                       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                                      STORAGECLASS   REASON   AGE
pvc-6fb13666-48e0-11e9-9347-080027ac9b62   2Gi        RWO            Delete           Bound    default/database-persistent-volume-claim   standard                61s
```

```
$ kubectl get pvc
NAME                               STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
database-persistent-volume-claim   Bound    pvc-6fb13666-48e0-11e9-9347-080027ac9b62   2Gi        RWO            standard       86s
```
