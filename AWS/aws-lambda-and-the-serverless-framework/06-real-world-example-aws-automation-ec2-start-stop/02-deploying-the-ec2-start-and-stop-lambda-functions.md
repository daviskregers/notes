# Deploying the EC2 start and stop lambda functions

We are going to create a new project:

```console
➜  learning-serverless git:(master) sls create --template aws-python --path 07-ec2-start-stop
Serverless: Generating boilerplate...
Serverless: Generating boilerplate in "/home/davis/projects/learning-serverless/07-ec2-start-stop"
Serverless: Successfully generated boilerplate for template: "aws-python"

```

We are going to set up the serverless.yaml like this:

```yaml
service: service-07-ec2-start-stop
frameworkVersion: '2'
provider:
  name: aws
  runtime: python2.7
  lambdaHashingVersion: 20201221
  region: eu-west-1
  profile: serverless-admin
  memorySize: 128
  iamRoleStatements:
    - Effect: Allow
      Action:
        - ec2:*
      Resource: "*"
functions:
  start-ec2:
    handler: handler.start_ec2
    timeout: 60
    events:
      - schedule: cron(0 13 * * ? *)
  stop-ec2:
    handler: handler.stop_ec2
    timeout: 60
    events:
      - schedule: cron(0 21 * * ? *)
```

And the handler file, like so:

```python
import boto3

ec2 = boto3.client('ec2')

def start_ec2(event, context):
    ec2_instances = get_all_ec2_ids()
    = get_all_ec2_ids()
    response = ec2.start_instances(
            InstanceIds=ec2_instances,
            DryRun=False)
    return response

def stop_ec2(event, context):
    ec2_instances = get_all_ec2_ids()
    response = ec2.stop_instances(
            InstanceIds = ec2_instances,
            DryRun = False
        )
    return response

def get_all_ec2_ids():
    response = ec2.describe_instances(DryRun=False)
    instances = []
    for reservation in response["Reservations"]:
        for instance in reservation["Instances"]:
            instances.append(instance["InstanceId"])

    return instances
```