# Optimizing content delivery with CloudFront

Currently our static website files are located in eu-central-1, but if a user accesses from US, it might take a while while everything is loaded. 

We can use CloudFront to cache these files on CDN and deliver to the user from nearest location.

AWS CloudFront Overview: https://aws.amazon.com/cloudfront/

AWS CloudFront Developer Guides: http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html

AWS CloudFront Pricing: https://aws.amazon.com/cloudfront/pricing/

## Creating a distribution on CloudFront

We can go to `AWS Console -> Cloudfront -> Create distribution`, most likely we'll want to select `web` as the protocol.

Then we need to set up things.

In the `Origin Domain Name` we want to set up our s3 bucket that is used for static webserver.

![](../../../images/2019-10-05-14-45-33.png)

The other settings we might to look at - maximum TTL, forward cookies, compress objects automatically.

In the Distribution settings setup correct price class, defailt root object as `index.html` and enable the `cookie logging` to the previously created log bucket.

Now, when clicking on `Create Distribution` it will create it and will take some time to sync it across all the locations.

