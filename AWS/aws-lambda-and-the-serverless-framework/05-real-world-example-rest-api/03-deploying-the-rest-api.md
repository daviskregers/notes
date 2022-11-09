# Deploying the REST API

Once the service is set up, we can deploy it.

```console
sls deploy -v
```

Once deployed, we'll see our 5 lambda functions:

![](Programming/AWS/aws-lambda-and-the-serverless-framework/05-real-world-example-rest-api/img/2021-10-12-16-59-53.png)

There will be a dynamoDB table setup:

![](Programming/AWS/aws-lambda-and-the-serverless-framework/05-real-world-example-rest-api/img/2021-10-12-17-00-21.png)

And API Gateway routes:

![](Programming/AWS/aws-lambda-and-the-serverless-framework/05-real-world-example-rest-api/img/2021-10-12-17-00-53.png)

--- 

