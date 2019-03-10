# Creating the EB environment

Now that the `Dockerrun.aws.json` is set up, we'll need to create the Elastic Beanstalk environment.
To do that we'll log into the `AWS Management Console` and go to the `Services -> Elastic Beanstalk` and click on the `Create New Application`.

![](../../images/2019-03-10-13-03-25.png)

Now we'll create a new environment

![](../../images/2019-03-10-13-04-01.png)

Select the `Web server` environemnt:

![](../../images/2019-03-10-13-04-22.png)

In the next form, everything can stay as it is except for the `Platform` section. Select thge `Multi-container Docker` option.

![](../../images/2019-03-10-13-05-07.png)

And click on the `Create Environment`.

Now it will take some time to create the environment:

![](../../images/2019-03-10-13-06-45.png)

When it's finished, you'll be redirected to a page like this:

![](../../images/2019-03-10-13-13-11.png)

And when visiting the environment URL, you'll see the sample app.

![](../../images/2019-03-10-13-13-28.png)