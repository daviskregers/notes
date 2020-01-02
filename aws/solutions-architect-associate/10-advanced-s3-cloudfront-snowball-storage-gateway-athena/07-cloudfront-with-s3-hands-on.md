# AWS CloudFront Hands On

## We'll create an S3 Bucket

![](images/2019-12-31-07-53-56.png)

Everything currently will be with default settings. 

Found a free HTML template to upload for testing.

![](images/2019-12-31-07-58-30.png)

## We'll create a CloudFront distribution and an Origin Access identity, limit the S3 bucket to be accessed only using this identity.

Now we are going to `CloudFront` service in AWS Console and create a distribution.

In the `Origin Domain Name` we select our S3 bucket.
Check `Restrict bucket Access`, create a new identity `access-identity-demo`, check `Grant Read Permissions on Bucket`.

`Viewer Protocol Policy` - `Redirect HTTP to HTTPS`.

![](images/2019-12-31-08-04-03.png)

Now the distribution is being created, it can take several minutes to complete.

![](images/2019-12-31-08-05-01.png)

We should also see an `Origin Access Identity` created.

![](images/2019-12-31-08-05-59.png)

Also, we can see that the public access has been enabled for the S3 bucket. 

![](images/2019-12-31-08-07-31.png)

Now, when visiting the generated CloudFront URL, we might see a redirect to the bucket itself and throwing an error.

![](images/2019-12-31-08-18-16.png)

This is due to the fact that everything is set up but the AWS internal DNS has not been updated yet, it might take a couple of hours to update and then it should work.