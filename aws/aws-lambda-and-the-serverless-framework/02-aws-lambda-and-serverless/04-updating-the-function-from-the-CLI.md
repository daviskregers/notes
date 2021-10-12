# Updating the function from the CLI

## Updating the funciton and deploying the stack

We are going to change the function:

```python
def hello(event, context):
    print("first update!")
    return "hello-world"
```

```console
➜  hello-world-python git:(master) ✗ nvim
➜  hello-world-python git:(master) ✗ sls invoke -f hello -l 
"hello-world"
--------------------------------------------------------------------
START RequestId: ba4a4095-104a-4b9a-bacb-6a03593d41ba Version: $LATEST
Hi!
END RequestId: ba4a4095-104a-4b9a-bacb-6a03593d41ba
REPORT RequestId: ba4a4095-104a-4b9a-bacb-6a03593d41ba  Duration: 0.35 ms       Billed Duration: 1 ms   Memory Size: 1024 MB    Max Memory Used: 23 MB


➜  hello-world-python git:(master) ✗ sls deploy -v
Serverless: Packaging service...
Serverless: Excluding development dependencies...
Serverless: Uploading CloudFormation file to S3...
Serverless: Uploading artifacts...
Serverless: Uploading service hello-world-python.zip file to S3 (464 B)...
Serverless: Validating template...
Serverless: Updating Stack...
Serverless: Checking Stack update progress...
CloudFormation - UPDATE_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-python-dev
CloudFormation - UPDATE_IN_PROGRESS - AWS::Lambda::Function - HelloLambdaFunction
CloudFormation - UPDATE_COMPLETE - AWS::Lambda::Function - HelloLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloLambdaVersionnYuVKWVqZo3ayPZ2VhECVLLDq2S1214n8jqgJs4e0g
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloLambdaVersionnYuVKWVqZo3ayPZ2VhECVLLDq2S1214n8jqgJs4e0g
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - HelloLambdaVersionnYuVKWVqZo3ayPZ2VhECVLLDq2S1214n8jqgJs4e0g
CloudFormation - UPDATE_COMPLETE_CLEANUP_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-python-dev
CloudFormation - DELETE_SKIPPED - AWS::Lambda::Version - HelloLambdaVersionpC2AzkyzeFlxav73Mzt7weVZ7YH18lex6bRJ5zN0SE
CloudFormation - UPDATE_COMPLETE - AWS::CloudFormation::Stack - hello-world-python-dev
Serverless: Stack update finished...
Service Information
service: hello-world-python
stage: dev
region: eu-west-1
stack: hello-world-python-dev
resources: 6
api keys:
  None
endpoints:
functions:
  hello: hello-world-python-dev-hello
layers:
  None

Stack Outputs
HelloLambdaFunctionQualifiedArn: arn:aws:lambda:eu-west-1:539690530154:function:hello-world-python-dev-hello:2
ServerlessDeploymentBucketName: hello-world-python-dev-serverlessdeploymentbucket-1gnp3uaf77yre

Serverless: Deprecation warning: Starting with v3.0.0, "-v" will no longer be supported as alias for "--verbose" option. Please use "--verbose" flag instead.
            More Info: https://www.serverless.com/framework/docs/deprecations/#CLI_VERBOSE_OPTION_ALIAS

Toggle on monitoring with the Serverless Dashboard: run "serverless"
➜  hello-world-python git:(master) ✗ sls invoke -f hello -l
"hello-world"
--------------------------------------------------------------------
START RequestId: 6592a35a-19cf-4ea4-974c-fee4d4a775f5 Version: $LATEST
first update!
END RequestId: 6592a35a-19cf-4ea4-974c-fee4d4a775f5
REPORT RequestId: 6592a35a-19cf-4ea4-974c-fee4d4a775f5  Duration: 0.22 ms       Billed Duration: 1 ms   Memory Size: 1024 MB    Max Memory Used: 23 MB  Init Duration: 0.80 ms


➜  hello-world-python git:(master) ✗ 
```

## Deploying the function without updating the whole stack

Now we are going to update the function once more:

```python
def hello(event, context):
    print("second update!")
    return "hello-world"
```

```console
➜  hello-world-python git:(master) ✗ sls invoke -f hello -l
"hello-world"
--------------------------------------------------------------------
START RequestId: a2bfe322-a4d7-450b-a2b8-e2f99fd41710 Version: $LATEST
first update!
END RequestId: a2bfe322-a4d7-450b-a2b8-e2f99fd41710
REPORT RequestId: a2bfe322-a4d7-450b-a2b8-e2f99fd41710  Duration: 0.27 ms       Billed Duration: 1 ms   Memory Size: 1024 MB    Max Memory Used: 23 MB


➜  hello-world-python git:(master) ✗ sls deploy function -f hello
Serverless: Packaging function: hello...
Serverless: Excluding development dependencies...
Serverless: Uploading function: hello (464 B)...
Serverless: Successfully deployed function: hello
Serverless: Configuration did not change. Skipping function configuration update.
➜  hello-world-python git:(master) ✗ sls invoke -f hello -l      
"hello-world"
--------------------------------------------------------------------
START RequestId: 9c7252a0-58b9-4504-8be8-b52709a9af1c Version: $LATEST
second update!
END RequestId: 9c7252a0-58b9-4504-8be8-b52709a9af1c
REPORT RequestId: 9c7252a0-58b9-4504-8be8-b52709a9af1c  Duration: 0.25 ms       Billed Duration: 1 ms   Memory Size: 1024 MB    Max Memory Used: 23 MB  Init Duration: 0.81 ms


➜  hello-world-python git:(master) ✗
```