# IAM Permissions for Lambda Functions

Our lambda functions access other services like S3 to store images or dynamoDB to store and retrieve data.

By default our lambda functions are not authorized to do that.

For this, we provide an IAM policy which allows you to entirely secure your AWS setup.

For this we are going to create a new project.

```console
➜  learning-serverless git:(master) sls create --template aws-python --path python-example-iam
Serverless: Generating boilerplate...
Serverless: Generating boilerplate in "/home/davis/projects/learning-serverless/python-example-iam"
Serverless: Successfully generated boilerplate for template: "aws-python"
```

And create a following function:

```python
import boto3

def hello(event, context):
    client = boto3.client('lambda')
    response = client.list_functions()
    return response

```

This will get the list of all the lambda functions we have and return them.

First off, we are going to try to run it without any IAM permissions.


```console
➜  learning-serverless git:(master) ✗ cd python-example-iam                                                                                                           
➜  python-example-iam git:(master) ✗ sls deploy                                                                                                                       
Serverless: Packaging service...                                                                                                                                      
Serverless: Excluding development dependencies...                                                                                                                     
Serverless: Creating Stack...                                                                                                                                         
Serverless: Checking Stack create progress...                                                                                                                         
........                                                                                                                                                              
Serverless: Stack create finished...                                                                                                                                  
Serverless: Uploading CloudFormation file to S3...                                                                                                                    
Serverless: Uploading artifacts...                                                                                                                                    
Serverless: Uploading service python-example-iam.zip file to S3 (490 B)...                                                                                            
Serverless: Validating template...                                                                                                                                    
Serverless: Updating Stack...                                                                                                                                         
Serverless: Checking Stack update progress...                                                                                                                         
...............                                                                                                                                                       
Serverless: Stack update finished...                                                                                                                                  
Service Information                                                                                                                                                   
service: python-example-iam                                                                                                                                           
stage: dev                                                                                                                                                            
region: us-east-1                                                                                                                                                     
stack: python-example-iam-dev                                                                                                                                         
resources: 6                                                                                                                                                          
api keys:                                                                                                                                                             
  None                                                                                                                                                                
endpoints:                                                                                                                                                            
functions:                                                                                                                                                            
  hello: python-example-iam-dev-hello                                                                                                                                 
layers:                                                                                                                                                               
  None                                                                                                                                                                
                                                                                                                                                                      
Toggle on monitoring with the Serverless Dashboard: run "serverless"  
➜  python-example-iam git:(master) sls invoke -f hello -l 
{
    "stackTrace": [
        [
            "/var/task/handler.py",
            5,
            "hello",
            "response = client.list_functions()"
        ],
        [
            "/var/runtime/botocore/client.py",
            386,
            "_api_call",
            "return self._make_api_call(operation_name, kwargs)"
        ],
        [
            "/var/runtime/botocore/client.py",
            705,
            "_make_api_call",
            "raise error_class(parsed_response, operation_name)"
        ]
    ],
    "errorType": "ClientError",
    "errorMessage": "An error occurred (AccessDeniedException) when calling the ListFunctions operation: User: arn:aws:sts::357261687744:assumed-role/python-example-iam-dev-us-east-1-lambdaRole/python-example-iam-dev-hello is not authorized to perform: lambda:ListFunctions on resource: *"
}
--------------------------------------------------------------------
START RequestId: 4e318fca-ab2b-4ed4-8303-75957bb26a64 Version: $LATEST
/var/runtime/boto3/compat.py:86: PythonDeprecationWarning: Boto3 will no longer support Python 2.7 starting July 15, 2021. To continue receiving service updates, bug fixes, and security updates please upgrade to Python 3.6 or later. More information can be found here: https://aws.amazon.com/blogs/developer/announcing-end-of-support-for-python-2-7-in-aws-sdk-for-python-and-aws-cli-v1/
warnings.warn(warning, PythonDeprecationWarning)
An error occurred (AccessDeniedException) when calling the ListFunctions operation: User: arn:aws:sts::357261687744:assumed-role/python-example-iam-dev-us-east-1-lambdaRole/python-example-iam-dev-hello is not authorized to perform: lambda:ListFunctions on resource: *: ClientError
Traceback (most recent call last):
  File "/var/task/handler.py", line 5, in hello
    response = client.list_functions()
  File "/var/runtime/botocore/client.py", line 386, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/var/runtime/botocore/client.py", line 705, in _make_api_call
    raise error_class(parsed_response, operation_name)
ClientError: An error occurred (AccessDeniedException) when calling the ListFunctions operation: User: arn:aws:sts::357261687744:assumed-role/python-example-iam-dev-us-east-1-lambdaRole/python-example-iam-dev-hello is not authorized to perform: lambda:ListFunctions on resource: *

END RequestId: 4e318fca-ab2b-4ed4-8303-75957bb26a64
REPORT RequestId: 4e318fca-ab2b-4ed4-8303-75957bb26a64  Duration: 306.51 ms     Billed Duration: 307 ms Memory Size: 1024 MB Max Memory Used: 63 MB  Init Duration: 186.54 ms


 
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
```

So the request fails. We are going to configure the iam in the serverless.yaml.

```yaml
service: python-example-iam
frameworkVersion: '2'

provider:
  name: aws
  runtime: python2.7
  lambdaHashingVersion: 20201221
  profile: serverless-admin
  region: eu-west-1
  iamRoleStatements:
    - Effect: Allow
      Action:
        - lambda:*
      Resource:
        - "*"
functions:
  hello:
    handler: handler.hello
```

And then deploy and invoke again:

```console
➜  python-example-iam git:(master) ✗ sls invoke -f hello -l                                                                                                           
{                                                                                                                                                                     
    "Functions": [                                                                                                                                                    
        {                                                                                                                                                             
            "TracingConfig": {                                                                                                                                        
                "Mode": "PassThrough"                                                                                                                                 
            },                                                                                                                                                        
            "Version": "$LATEST",      
            "CodeSha256": "Nn8prCQ4VjwPWFA+Wi/pTckoZ9R7hWEZWZymn/gI3Fc=",                                                                                                                         
            "FunctionName": "python-example-iam-dev-hello",                                                         
            "MemorySize": 1024,                                                    
            "RevisionId": "eb571f80-37b9-4174-b283-7249f9df2859",                  
            "CodeSize": 490,  
            "PackageType": "Zip",                                                  
            "FunctionArn": "arn:aws:lambda:eu-west-1:539690530154:function:python-example-iam-dev-hello",                                                                                                                                
            "Handler": "handler.hello",
            "Role": "arn:aws:iam::539690530154:role/python-example-iam-dev-eu-west-1-lambdaRole",                                                                     
            "Timeout": 6,              
            "LastModified": "2021-10-12T11:41:50.296+0000",                                                                                                           
            "Runtime": "python2.7",                                                              
            "Description": ""                                                      
        },                         
        {                                                                                        
            "TracingConfig": {
                "Mode": "PassThrough"
            },                                                                                                                                                                                    
            "Version": "$LATEST",      
            "CodeSha256": "FJI+X2rjl83woBoRp+ozHqHBRNlvxDCvvE0Zj9POW6Q=",                                                                                                                         
            "FunctionName": "hello-world-python-dev-hello-long-timeout",                                            
            "MemorySize": 256,                                                     
            "RevisionId": "215e0ac3-7712-45d7-89a7-f814640d78a0",                  
            "CodeSize": 481, 
            "PackageType": "Zip",
            "FunctionArn": "arn:aws:lambda:eu-west-1:539690530154:function:hello-world-python-dev-hello-long-timeout",                                                                                                                   
            "Handler": "handler.hello",
            "Role": "arn:aws:iam::539690530154:role/hello-world-python-dev-eu-west-1-lambdaRole",                                                                                                                                        
            "Timeout": 6,     
            "LastModified": "2021-10-12T11:29:42.426+0000",                        
            "Runtime": "python2.7",                                                              
            "Description": ""                                                                    
        },                                                                                                                                                            
        {                              
            "TracingConfig": {                                                                                                                                        
                "Mode": "PassThrough" 
            },                                                                     
            "Version": "$LATEST",  
            "CodeSha256": "FJI+X2rjl83woBoRp+ozHqHBRNlvxDCvvE0Zj9POW6Q=",                        
            "FunctionName": "hello-world-python-dev-hello-short-timeout",                                           
            "VpcConfig": {       
                "SubnetIds": [],                                                                                                                                                                  
                "VpcId": "",           
                "SecurityGroupIds": []                                                                                                                                                            
            },                                                                     
            "MemorySize": 512,                                                                   
            "RevisionId": "118ef4c8-541a-4e24-8466-9c802468f477",                  
            "CodeSize": 481,                                                       
            "PackageType": "Zip",    
            "FunctionArn": "arn:aws:lambda:eu-west-1:539690530154:function:hello-world-python-dev-hello-short-timeout",                                                                                                                  
            "Handler": "handler.hello",
            "Role": "arn:aws:iam::539690530154:role/hello-world-python-dev-eu-west-1-lambdaRole",                                                                                                                                        
            "Timeout": 2,     
            "LastModified": "2021-10-12T11:29:42.304+0000",                                      
            "Runtime": "python2.7",                                                
            "Description": ""                                                      
        }                                                                                        
    ],                                          
    "ResponseMetadata": {                                                                        
        "RetryAttempts": 0,                     
        "HTTPStatusCode": 200,                  
        "RequestId": "1383966a-249a-4b49-b493-dadb219b2b45",                                                        
        "HTTPHeaders": {                        
            "date": "Tue, 12 Oct 2021 11:42:12 GMT",                                             
            "x-amzn-requestid": "1383966a-249a-4b49-b493-dadb219b2b45",                          
            "content-length": "2992",                                                                                                                                                             
            "content-type": "application/json",                                                                                                                                                   
            "connection": "keep-alive"                                                           
        }                                                                                        
    }                                                                                                                                                                                             
}                                                         
--------------------------------------------------------------------                                                
START RequestId: 13622bc9-a2ad-44b7-bdb1-faea58c913bf Version: $LATEST                                              
/var/runtime/boto3/compat.py:86: PythonDeprecationWarning: Boto3 will no longer support Python 2.7 starting July 15, 2021. To continue receiving service updates, bug fixes, and security updates please upgrade to Python 3.6 or later. 
More information can be found here: https://aws.amazon.com/blogs/developer/announcing-end-of-support-for-python-2-7-in-aws-sdk-for-python-and-aws-cli-v1/                                                                                
warnings.warn(warning, PythonDeprecationWarning)                                                                    
END RequestId: 13622bc9-a2ad-44b7-bdb1-faea58c913bf                                                                 
REPORT RequestId: 13622bc9-a2ad-44b7-bdb1-faea58c913bf  Duration: 289.32 ms     Billed Duration: 290 ms Memory Size: 1024 MB    Max Memory Used: 63 MB  Init Duration: 167.40 ms             
```