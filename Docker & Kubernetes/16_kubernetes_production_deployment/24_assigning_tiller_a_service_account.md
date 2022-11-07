# Assigning Tiller a Service account

We can run the following commands in `Google Cloud Shell` to create a service account for `Tiller`. 

```
kubectl create serviceaccount --namespace kube-system tiller
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
```

![](../../images/2019-04-06-13-47-22.png)

Now, we can finally run the helm init:

```
helm init --service-account tiller --upgrade
```

![](../../images/2019-04-06-13-49-01.png)

Now, finally, we have `Helm` installed.