# IAM Keys for deployment

Now, when everything is ready, we'll go to `Services -> IAM -> Users` and create a new user for deploying the application.

Make sure to check the `Programmatic access` box.

![](../../images/2019-03-10-14-29-57.png)

We'll attach existing policies that are related to beanstalk:

![](../../images/2019-03-10-14-31-55.png)

And create the user:

![](../../images/2019-03-10-14-32-39.png)

Now, we'll go to `Travis CI`, open up the repository settings and set them up as environment variables:

![](../../images/2019-03-10-14-35-13.png)