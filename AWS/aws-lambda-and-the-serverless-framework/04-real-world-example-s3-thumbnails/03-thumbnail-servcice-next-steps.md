# Ideas to make our service better

- Make sure we handle errors
    - Corrupted images
    - Non image files
- Make sure we correctly measure timeouts
- Do not create a thumbnail if the image is too big (over >5MB)
- Build alerting using AWS SNS if an image is not successfully processed
- Put image metadata in DynamoDB (the metadata you want)