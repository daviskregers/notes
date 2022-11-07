# Lambda Synchronous Invocations Hands On

Previously we tested the Lambda using the test button, which was a syncronous invocation meaning that we waited for the lambda to be finished.

![](2022-05-12-07-01-45.png)

We can also invoke it via shell

```console

// Linux / Mac
$ aws lambda invoke --function-name hello-world --cli-binary-format raw-in-base64-out --payload '{"key1": "value1", "key2": "value2", "key3": "value3"}' --region eu-west-1 response.json
// Windows Powershell
$ aws lambda invoke --function-name hello-world --cli-binary-format raw-in-base64-out --payload '{\"key1\": \"value1\", \"key2\": \"value2\", \"key3\": \"value3\"}' --region eu-west-1 response.json
// Windows CMD
$ aws lambda invoke --function-name hello-world --cli-binary-format raw-in-base64-out --payload '{""key1"": ""value1"", ""key2"": ""value2"", ""key3"": ""value3""}' --region eu-west-1 response.json

$ cat response.json
```

