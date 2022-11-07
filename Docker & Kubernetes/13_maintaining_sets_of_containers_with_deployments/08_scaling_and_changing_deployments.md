# Scaling and changing deployments

We are going to open up the `client-deployment.yaml` file:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: client-deployment
spec:
  replicas: 1
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

And modify the port that previously failed on pod update:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: client-deployment
spec:
  replicas: 1
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
            - containerPort: 9999
```

```
$ kubectl apply -f client-deployment.yaml 
deployment.apps/client-deployment configured
$ kubectl get pods
NAME                                 READY   STATUS    RESTARTS   AGE
client-deployment-69f476d99b-s4trm   1/1     Running   0          18s
$ kubectl get deployments 
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
client-deployment   1/1     1            1           10m
```

```
$ kubectl describe pods 

Name:               client-deployment-69f476d99b-s4trm
Namespace:          default
Priority:           0
PriorityClassName:  <none>
Node:               minikube/10.0.2.15
Start Time:         Sun, 17 Mar 2019 17:08:31 +0200
Labels:             component=web
                    pod-template-hash=69f476d99b
Annotations:        <none>
Status:             Running
IP:                 172.17.0.5
Controlled By:      ReplicaSet/client-deployment-69f476d99b
Containers:
  client:
    Container ID:   docker://7c59d43a6cd56c8eabfca5230f1fe2929b52debf49b58ff7d0022c6e8031ac93
    Image:          deiveris/multi-client
    Image ID:       docker-pullable://deiveris/multi-client@sha256:51c71c0006401fcb25f15b0bf809b58e0f5a3885271b3d655fe1ed685a2f64f9
    Port:           9999/TCP
    Host Port:      0/TCP
    State:          Running
      Started:      Sun, 17 Mar 2019 17:08:34 +0200
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-vq8qh (ro)
Conditions:
  Type              Status
  Initialized       True 
  Ready             True 
  ContainersReady   True 
  PodScheduled      True 
Volumes:
  default-token-vq8qh:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-vq8qh
    Optional:    false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  85s   default-scheduler  Successfully assigned default/client-deployment-69f476d99b-s4trm to minikube
  Normal  Pulling    84s   kubelet, minikube  pulling image "deiveris/multi-client"
  Normal  Pulled     83s   kubelet, minikube  Successfully pulled image "deiveris/multi-client"
  Normal  Created    83s   kubelet, minikube  Created container
  Normal  Started    82s   kubelet, minikube  Started container
```

We can see that the pod is working on the port `9999`.

If we change the `replicas: 5`

```
$ kubectl get deployments
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
client-deployment   5/5     5            5           13m
$ kubectl get pods
NAME                                 READY   STATUS    RESTARTS   AGE
client-deployment-69f476d99b-9dzd5   1/1     Running   0          25s
client-deployment-69f476d99b-ct94h   1/1     Running   0          25s
client-deployment-69f476d99b-lwbcj   1/1     Running   0          25s
client-deployment-69f476d99b-nt5mz   1/1     Running   0          25s
client-deployment-69f476d99b-s4trm   1/1     Running   0          3m7s

```