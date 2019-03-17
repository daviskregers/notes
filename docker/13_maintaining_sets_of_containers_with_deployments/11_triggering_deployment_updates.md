# Triggering deployment updates

Now, when we have made a new image and deployed to docker hub, we need to apply it to the kubernetes cluster.

Currently the issue with our configuration is that if we try to make changes by applying deployment:

```
$ kubectl apply -f client-deployment.yaml
deployment.apps/client-deployment unchanged
```

This is because the configuration file has not changed.

There are 3 solutions on how to get around this (none of which are great):
- Manually delete pods to get the deployment to recreate them with the latest version
- Tag build timages with a real version number and specify that version in the config file
- Use an imperative command to update the image version the deployment should use