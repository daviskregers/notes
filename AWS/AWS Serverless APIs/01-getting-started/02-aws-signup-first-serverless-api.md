# AWS Signup and First serverless API

You can go to [https://console.aws.amazon.com/console/home](https://console.aws.amazon.com/console/home) to sign up for AWS, this will require a valid credit card.

When the signup is done and we're in the console, we can open up services menu and searchn for `API Gateway`. 

![](../../../images/2019-10-05-08-49-42.png)

Click on `Get started` button. We want a `new REST API`.

![](../../../images/2019-10-05-08-51-17.png)

Not click on `Create API` and you will have this API.

![](../../../images/2019-10-05-08-51-52.png)

We can click on `Actions -> Create Resource` to create a new resource

![](../../../images/2019-10-05-08-53-01.png)

We can't call this yet, because we haven't provided request methods. We can do this by clicking on `Actions -> Create Method`.

![](../../../images/2019-10-05-08-54-19.png)

Now, we can provide an integration for the method like a:
- Lamda function
- HTTP endpoint
- Mock
- AWS service
- VPC link

![](../../../images/2019-10-05-08-56-18.png)

After choosing `Mock`, we can click on the `Integration Response`
![](../../../images/2019-10-05-08-57-04.png)

And set a `Mapping template`.

![](../../../images/2019-10-05-08-59-14.png)

Now we are ready to deploy it by going to `Actions -> Deploy API`.
Select a new deployment stage.

![](../../../images/2019-10-05-09-00-33.png)

Then, we will receive an URL like `https://j12yugstuf.execute-api.eu-central-1.amazonaws.com/development`.

When visiting it, we will receive an error message:

![](../../../images/2019-10-05-09-02-16.png)

But, if we go to the actual endpoint at `https://j12yugstuf.execute-api.eu-central-1.amazonaws.com/development/first-api-test`, we are going to see the mock data.

![](../../../images/2019-10-05-09-03-12.png)