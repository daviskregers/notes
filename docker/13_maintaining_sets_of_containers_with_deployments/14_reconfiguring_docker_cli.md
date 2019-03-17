# Reconfiguring docker cli

We can use this command to tell our docker to communicate to the one that is in the node:

```
eval $(minikube docker-env)
```

Note that this configures only your current terminal window. 

```
$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
$ eval $(minikube docker-env)

$ docker ps
CONTAINER ID        IMAGE                                     COMMAND                  CREATED             STATUS              PORTS               NAMES
08e1f3633220        deiveris/multi-client                     "nginx -g 'daemon of…"   7 minutes ago       Up 7 minutes                            k8s_client_client-deployment-7fbcbb74f6-6b9zp_default_07dfcefa-48ce-11e9-9347-080027ac9b62_0
2cad7cd16d67        k8s.gcr.io/pause:3.1                      "/pause"                 7 minutes ago       Up 7 minutes                            k8s_POD_client-deployment-7fbcbb74f6-6b9zp_default_07dfcefa-48ce-11e9-9347-080027ac9b62_0
70abe7496757        gcr.io/k8s-minikube/storage-provisioner   "/storage-provisioner"   3 hours ago         Up 3 hours                              k8s_storage-provisioner_storage-provisioner_kube-system_cad7848a-48b3-11e9-9347-080027ac9b62_0
c77fc24db6ed        k8s.gcr.io/pause:3.1                      "/pause"                 3 hours ago         Up 3 hours                              k8s_POD_storage-provisioner_kube-system_cad7848a-48b3-11e9-9347-080027ac9b62_0
db2a72d8a368        f59dcacceff4                              "/coredns -conf /etc…"   3 hours ago         Up 3 hours                              k8s_coredns_coredns-86c58d9df4-6vwjn_kube-system_ca149085-48b3-11e9-9347-080027ac9b62_0
6ec0a646cc54        f59dcacceff4                              "/coredns -conf /etc…"   3 hours ago         Up 3 hours                              k8s_coredns_coredns-86c58d9df4-tf5qs_kube-system_ca1377bd-48b3-11e9-9347-080027ac9b62_0
678de1a66ed9        k8s.gcr.io/pause:3.1                      "/pause"                 3 hours ago         Up 3 hours                              k8s_POD_coredns-86c58d9df4-6vwjn_kube-system_ca149085-48b3-11e9-9347-080027ac9b62_0
cc9a879cf62e        k8s.gcr.io/pause:3.1                      "/pause"                 3 hours ago         Up 3 hours                              k8s_POD_coredns-86c58d9df4-tf5qs_kube-system_ca1377bd-48b3-11e9-9347-080027ac9b62_0
69a36af4889d        fadcc5d2b066                              "/usr/local/bin/kube…"   3 hours ago         Up 3 hours                              k8s_kube-proxy_kube-proxy-8fl92_kube-system_c9cf3515-48b3-11e9-9347-080027ac9b62_0
ce6025e1d4fe        k8s.gcr.io/pause:3.1                      "/pause"                 3 hours ago         Up 3 hours                              k8s_POD_kube-proxy-8fl92_kube-system_c9cf3515-48b3-11e9-9347-080027ac9b62_0
d2346064cd2c        k8s.gcr.io/kube-addon-manager             "/opt/kube-addons.sh"    3 hours ago         Up 3 hours                              k8s_kube-addon-manager_kube-addon-manager-minikube_kube-system_5c72fb06dcdda608211b70d63c0ca488_0
44477cd9854b        3cab8e1b9802                              "etcd --advertise-cl…"   3 hours ago         Up 3 hours                              k8s_etcd_etcd-minikube_kube-system_5d1dfac2685c9f6c638fb24ff7b526ae_0
30608e848d4b        dd862b749309                              "kube-scheduler --ad…"   3 hours ago         Up 3 hours                              k8s_kube-scheduler_kube-scheduler-minikube_kube-system_4b52d75cab61380f07c0c5a69fb371d4_0
f0e707d067b0        40a817357014                              "kube-controller-man…"   3 hours ago         Up 3 hours                              k8s_kube-controller-manager_kube-controller-manager-minikube_kube-system_17eea6fd9342634d7d40a04d577641fd_0
5af97a55a8ee        fc3801f0fc54                              "kube-apiserver --au…"   3 hours ago         Up 3 hours                              k8s_kube-apiserver_kube-apiserver-minikube_kube-system_c43b7638a36a24e7ce3a86415f505a74_0
881e39c9c8d6        k8s.gcr.io/pause:3.1                      "/pause"                 3 hours ago         Up 3 hours                              k8s_POD_kube-controller-manager-minikube_kube-system_17eea6fd9342634d7d40a04d577641fd_0
183b32b7c30f        k8s.gcr.io/pause:3.1                      "/pause"                 3 hours ago         Up 3 hours                              k8s_POD_kube-scheduler-minikube_kube-system_4b52d75cab61380f07c0c5a69fb371d4_0
bb07dcd126f7        k8s.gcr.io/pause:3.1                      "/pause"                 3 hours ago         Up 3 hours                              k8s_POD_etcd-minikube_kube-system_5d1dfac2685c9f6c638fb24ff7b526ae_0
b7cad0807aa2        k8s.gcr.io/pause:3.1                      "/pause"                 3 hours ago         Up 3 hours                              k8s_POD_kube-apiserver-minikube_kube-system_c43b7638a36a24e7ce3a86415f505a74_0
091482821db9        k8s.gcr.io/pause:3.1                      "/pause"                 3 hours ago         Up 3 hours                              k8s_POD_kube-addon-manager-minikube_kube-system_5c72fb06dcdda608211b70d63c0ca488_0

```

If we view the command executed by eval, we can see that it exports some environment variables:

```
$ minikube docker-env
export DOCKER_TLS_VERIFY="1"
export DOCKER_HOST="tcp://192.168.99.101:2376"
export DOCKER_CERT_PATH="/home/davis/.minikube/certs"
export DOCKER_API_VERSION="1.35"
# Run this command to configure your shell:
# eval $(minikube docker-env)
```