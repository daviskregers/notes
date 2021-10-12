# AWS Functions Timeout and Memory

We are going to change the `serverless.yaml` configuration like so:

```yaml
service: hello-world-python
frameworkVersion: '2'

provider:
  name: aws
  runtime: python2.7
  lambdaHashingVersion: 20201221
  profile: serverless-admin
  region: eu-west-1

functions:
  hello-short-timeout:
    handler: handler.hello
    memorySize: 128
    timeout: 3
  hello-long-timeout:
    handler: handler.hello
    memorySize: 256
    timeout: 6
```

And update the function:

```python
import time

def hello(event, context):
    print("second update!")
    time.sleep(4)
    return "hello-world"
```

And deploy it:

```console
➜  hello-world-python git:(master) ✗ sls deploy -v                                          [15/491]
Serverless: Packaging service...                                                                    
Serverless: Excluding development dependencies...                                                   
Serverless: Creating Stack...                                                                       
Serverless: Checking Stack create progress...                                                       
CloudFormation - CREATE_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-python-dev           
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket                  
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket                  
CloudFormation - CREATE_COMPLETE - AWS::S3::Bucket - ServerlessDeploymentBucket                     
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::BucketPolicy - ServerlessDeploymentBucketPolicy      
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::BucketPolicy - ServerlessDeploymentBucketPolicy      
CloudFormation - CREATE_COMPLETE - AWS::S3::BucketPolicy - ServerlessDeploymentBucketPolicy         
CloudFormation - CREATE_COMPLETE - AWS::CloudFormation::Stack - hello-world-python-dev              
Serverless: Stack create finished...                                                                
Serverless: Uploading CloudFormation file to S3...                                                  
Serverless: Uploading artifacts...                                                                  
Serverless: Uploading service hello-world-python.zip file to S3 (481 B)...
Serverless: Validating template...
Serverless: Updating Stack...
Serverless: Checking Stack update progress...
CloudFormation - UPDATE_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-python-dev
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloDashlongDashtimeoutLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloDashshortDashtimeoutLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloDashlongDashtimeoutLogGroup
CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - HelloDashlongDashtimeoutLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloDashshortDashtimeoutLogGroup
CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - HelloDashshortDashtimeoutLogGroup
CloudFormation - CREATE_COMPLETE - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - HelloDashlongDashtimeoutLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - HelloDashshortDashtimeoutLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - HelloDashlongDashtimeoutLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - HelloDashshortDashtimeoutLambdaFunction
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Function - HelloDashlongDashtimeoutLambdaFunction
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Function - HelloDashshortDashtimeoutLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloDashlongDashtimeoutLambdaVersion3kQV2oC0POBMifyDGFV4BsSfc7frlb3RPwdnjzQPFgM
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloDashlongDashtimeoutLambdaVersion3kQV2oC0POBMifyDGFV4BsSfc7frlb3RPwdnjzQPFgM
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloDashshortDashtimeoutLambdaVersionznsbIl9hJRSWGiJqJdhDyz4W89MX5Gwoo9dGTsCttw
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - HelloDashlongDashtimeoutLambdaVersion3kQV2oC0POBMifyDGFV4BsSfc7frlb3RPwdnjzQPFgM
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloDashshortDashtimeoutLambdaVersionznsbIl9hJRSWGiJqJdhDyz4W89MX5Gwoo9dGTsCttw
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - HelloDashshortDashtimeoutLambdaVersionznsb
Il9hJRSWGiJqJdhDyz4W89MX5Gwoo9dGTsCttw
CloudFormation - UPDATE_COMPLETE_CLEANUP_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-pyth
on-dev
CloudFormation - UPDATE_COMPLETE - AWS::CloudFormation::Stack - hello-world-python-dev
Serverless: Stack update finished...
Service Information
service: hello-world-python
stage: dev
region: eu-west-1
stack: hello-world-python-dev
resources: 9
api keys:
  None
endpoints:
functions:
  hello-short-timeout: hello-world-python-dev-hello-short-timeout
  hello-long-timeout: hello-world-python-dev-hello-long-timeout
layers:
  None
Stack Outputs
HelloDashshortDashtimeoutLambdaFunctionQualifiedArn: arn:aws:lambda:eu-west-1:539690530154:function:hello-world-python-dev-hello-short-timeout:1
ServerlessDeploymentBucketName: hello-world-python-dev-serverlessdeploymentbucket-13qatxs10r6fv
HelloDashlongDashtimeoutLambdaFunctionQualifiedArn: arn:aws:lambda:eu-west-1:539690530154:function:hello-world-python-dev-hello-long-timeout:1

Serverless: Deprecation warning: Starting with v3.0.0, "-v" will no longer be supported as alias for "--verbose" option. Please use "--verbose" flag instead.
            More Info: https://www.serverless.com/framework/docs/deprecations/#CLI_VERBOSE_OPTION_ALIAS

Toggle on monitoring with the Serverless Dashboard: run "serverless"
```

Now we can test them:

```console
➜  hello-world-python git:(master) ✗ sls invoke -f hello-short-timeout -l
{
    "errorMessage": "2021-10-12T11:24:59.786Z 4fd2df20-4cd4-4883-b84c-6b8f8b38f0bc Task timed out after 3.00 seconds"
}
--------------------------------------------------------------------
START RequestId: 4fd2df20-4cd4-4883-b84c-6b8f8b38f0bc Version: $LATEST
second update!
END RequestId: 4fd2df20-4cd4-4883-b84c-6b8f8b38f0bc
REPORT RequestId: 4fd2df20-4cd4-4883-b84c-6b8f8b38f0bc  Duration: 3003.17 ms    Billed Duration: 3000 ms    Memory Size: 128 MB     Max Memory Used: 23 MB  Init Duration: 2.01 ms

2021-10-12T11:24:59.786Z 4fd2df20-4cd4-4883-b84c-6b8f8b38f0bc Task timed out after 3.00 seconds


 
 Serverless Error ----------------------------------------
 
  Invoked function failed
 
  Get Support --------------------------------------------
     Docs:          docs.serverless.com
     Bugs:          github.com/serverless/serverless/issues
     Issues:        forum.serverless.com
 
  Your Environment Information ---------------------------
     Operating System:          linux
     Node Version:              16.10.0
     Framework Version:         2.62.0
     Plugin Version:            5.4.6
     SDK Version:               4.3.0
     Components Version:        3.17.1
 
➜  hello-world-python git:(master) ✗ sls invoke -f hello-long-timeout -l
"hello-world"
--------------------------------------------------------------------
START RequestId: 21066957-d8a2-44b9-8c69-110c31030b1b Version: $LATEST
second update!
END RequestId: 21066957-d8a2-44b9-8c69-110c31030b1b
REPORT RequestId: 21066957-d8a2-44b9-8c69-110c31030b1b  Duration: 4004.47 ms    Billed Duration: 4005 ms    Memory Size: 256 MB     Max Memory Used: 23 MB  Init Duration: 0.86 ms


➜  hello-world-python git:(master) ✗ 
```

So, the short timeout function failed while the long one succeeded.

The morale of the story - you can limit your timeouts to limit your spending, but make sure to track your run times as it can kill your functions as well.

We can also configure this under provider:

```yaml
service: hello-world-python
frameworkVersion: '2'

provider:
  name: aws
  runtime: python2.7
  lambdaHashingVersion: 20201221
  profile: serverless-admin
  region: eu-west-1
  memorySize: 512
  timeout: 2

functions:
  hello-short-timeout:
    handler: handler.hello
  hello-long-timeout:
    handler: handler.hello
    memorySize: 256
    timeout: 6
```

