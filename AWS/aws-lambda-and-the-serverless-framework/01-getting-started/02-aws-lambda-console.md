# AWS Lambda Console

In this lecture we are going to deploy our first AWS Lambda Function. We are going to do this through the AWS Console, later we'll move on to the serverless framework.

## Deploying Hello World Function Using AWS Lambda

1. Sign Up for an AWS Account
2. Create our first lambda function
3. Test and run it

## Creating our Lambda

We can access lambda by searching it in the AWS Console.

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-12-16-24.png)

There we can click on `Create Function`.

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-12-17-07.png)

There we can choose from different types of lambda functions:
- Author from scratch
    - Start with a simple hello world example and change it
- Use a blueprint
    - Build a lambda application from sample code and configuration presets for common use cases
- Container Image
    - Select  a container image to deploy for your function
- Browse serverless app repository
    - Deploy a sample lambda application from the AWS Serverless Application Repository

We are going to use the `hello-world-python` blueprint.

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-12-20-23.png)

In the next step we are going to just enter the function name as `hello-world-python` and leave everything else as-is.

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-12-22-54.png)

Once that's done, our function is successfully created.

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-12-28-19.png)

In this window we can configure the triggers, destinations for the lambda as well as change the code itself.

Currently, we are going to test it manually.

In the configuration tab we can set things like Permissions, Environment Variables and all kinds of settings.

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-13-08-59.png)

At the bottom we can change the runtime settings, where we can choose the runtime environment, the handler (which method is called) and the architecture.

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-13-11-18.png)

## Testing the Lambda

We can go to the `Test` tab and we'll see a screen to configure a new event.

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-13-14-29.png)

We can click the save changes and test.

It should succeed:

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-13-15-18.png)

## Deleting Lambda

We can delete the function by clicking `Action` and then choosing the delete.

![](Programming/AWS/aws-lambda-and-the-serverless-framework/01-getting-started/img/2021-10-12-13-17-18.png)