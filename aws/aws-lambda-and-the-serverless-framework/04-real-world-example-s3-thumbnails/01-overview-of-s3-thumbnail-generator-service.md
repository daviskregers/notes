# Overview of S3 Thumbnail Generator Service

So, we'll have an S3 bucket where will upload a new image.

This event will trigger an AWS Lambda function that  will creatre a thumbnail of the image.

The new thumbnail will be uploaded into S3 bucket.

## What we'll use

- S3 events
- Function timeouts and memory
- IAM Permissions
- Plugins to deploy python dependencies (need to have docker installed)
- Custom variables
- Environment variables