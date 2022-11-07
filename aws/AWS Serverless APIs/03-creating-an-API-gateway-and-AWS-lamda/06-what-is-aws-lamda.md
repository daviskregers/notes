# What is AWS lamda?

AWS lamda is an AWS service that runs code on demand based on some event like:

- S3 (file gets uploaded)
- CloudWatch (scheduled event)
- API Gateway (HTTP request)
- etc

When event is triggered, we run the code and return a result, interact with other services.

## Accessing logs

We can see logs like `console.log` output in node.js by going to `CloudWatch -> Logs` and selecting our lamda function.

![](../../../images/2019-10-05-11-01-49.png)

