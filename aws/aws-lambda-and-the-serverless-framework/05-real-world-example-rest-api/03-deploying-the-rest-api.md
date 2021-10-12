# Deploying the REST API

Once the service is set up, we can deploy it.

```console
sls deploy -v
```

Once deployed, we'll see our 5 lambda functions:

![](img/2021-10-12-16-59-53.png)

There will be a dynamoDB table setup:

![](img/2021-10-12-17-00-21.png)

And API Gateway routes:

![](img/2021-10-12-17-00-53.png)

--- 

