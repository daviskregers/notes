# Environment Variables in AWS Lambda

Environment variables are good because they provide external configuration to your functions.

This way, we can change a function's behavior without even changing the code of the function.

```console
➜  python-example-iam git:(master) sls create --template aws-python --path python-example-environment-variables
Serverless: Generating boilerplate...
Serverless: Generating boilerplate in "/home/davis/projects/learning-serverless/python-example-iam/python-example-environment-variables"
Serverless: Successfully generated boilerplate for template: "aws-python"
```

We are going to set up a following funciton:

```python
import os

def hello(event, context):
    return os.environ['FIRST_NAME']
```

And the configuration:

```yaml
service: python-example-environment-variables
frameworkVersion: '2'
provider:
  name: aws
  runtime: python2.7
  lambdaHashingVersion: 20201221
  profile: serverless-admin
  region: eu-west-1
  environment:
    variable1: value1
    variable2: value2
    FIRST_NAME: John
functions:
  hello-env-john:
    handler: handler.hello
  hello-env-marc:
    handler: handler.hello
    environment:
      FIRST_NAME: Marc
```

And then we can invoke it:

```console
➜  python-example-environment-variables git:(master) ✗ sls invoke -f hello-env-john
"John"
➜  python-example-environment-variables git:(master) ✗ sls invoke -f hello-env-marc
"Marc"
```