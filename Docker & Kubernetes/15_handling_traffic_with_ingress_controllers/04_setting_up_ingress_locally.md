# Setting up ingress locally

First we are going to [https://kubernetes.github.io/ingress-nginx/deploy/#generic-deployment](https://kubernetes.github.io/ingress-nginx/deploy/#generic-deployment).

And copy the `Mandatory command` and run it:

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/mandatory.yaml
```

This will create a health check pod called `default-backend`, configs and the deployment of `ingress controller`.

```
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/mandatory.yaml
namespace/ingress-nginx created
configmap/nginx-configuration created
configmap/tcp-services created
configmap/udp-services created
serviceaccount/nginx-ingress-serviceaccount created
clusterrole.rbac.authorization.k8s.io/nginx-ingress-clusterrole created
role.rbac.authorization.k8s.io/nginx-ingress-role created
rolebinding.rbac.authorization.k8s.io/nginx-ingress-role-nisa-binding created
clusterrolebinding.rbac.authorization.k8s.io/nginx-ingress-clusterrole-nisa-binding created
deployment.apps/nginx-ingress-controller created
```

```
$ minikube addons enable ingress
-   ingress was successfully enabled
```

