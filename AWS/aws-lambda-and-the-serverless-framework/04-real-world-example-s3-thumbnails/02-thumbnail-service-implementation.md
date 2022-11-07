# Thumbnail service implementation

We are going to create a new project.

```console
➜  learning-serverless git:(master) sls create --template aws-python --path 05-python-s3-thumbnail
Serverless: Generating boilerplate...
Serverless: Generating boilerplate in "/home/davis/projects/learning-serverless/05-python-s3-thumbnail"
Serverless: Successfully generated boilerplate for template: "aws-python"
```

We are going to populate the `serverless.yaml` file:

```yaml
service: service-05-python-s3-thumbnail
frameworkVersion: '2'
provider:
  name: aws
  runtime: python2.7
  lambdaHashingVersion: 20201221
  region: eu-west-1
  profile: serverless-admin
  timeout: 10
  memorySize: 128
  iamRoleStatements:
    - Effect: Allow
      Action:
        - "s3:*"
      Resource: "*"
  environment:
    THUMBNAIL_SIZE: 128

custom:
  bucket: davis-s3-thumbnail-generator
  pythonRequirements:
    dockerizePip: true

functions:
  s3-thumbnail-generator:
    handler: handler.s3_thumbnail_generator
    events:
      - s3:
          bucket: ${self:custom.bucket}
          event: s3:ObjectCreated:*
          rules:
            - suffix: .png
plugins:
  - serverless-python-requirements
```

And the `handler.py` file:

```python
import boto3
import cStringIO
from PIL import Image, ImageOps
import os

s3 = boto.client('s3')
size = int(os.environ['THUMBNAIL_SIZE'])

def s3_thumbnail_generator(event, context):
    print(event)

    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']
    image = get_s3_image(bucket, key)
    thumbnail = image_to_thumbnail(image)
    thumbnail_key = new_filename(key)

    url = upload_to_s3(bucket, thumbnail_key, thumbnail)
    return url

def get s3_image(bucket, key):
    response = s3.get_object(Bucket=bucket, Key=key)
    imagecontent = response['Body'].read()

    file = cStringIO.StringIO(imagecontent)
    img = Image.open(file)
    return img

def image_to_thumbnail(image):
    return ImageOps.fit(image, (size, size), Image.ANTIALIAS)

def new_filename(key)
    key_split = key.rsplit('.', 1)
    return key_split + "_thumbnail.png"

def upload_to_s3(bucket, key, image):
    out_thumbnail = cStringIO.StringIO()
    image.save(out_thumbnail, 'PNG')
    out_thumbnail.seek(0)

    response = s3.put_object(
        ACL='public-read',
        Body=out_thumbnail,
        Bucket=bucket,
        ContentType='image/png',
        Key=key
    )
    print(response)

    url = '{}/{}/{}'.format(s3.meta.endpoint_url, bucket, key)
    return url
```

Also, create `requirements.txt` file:

```
Pillow
```

Then, we are going to deploy it!

```console
➜  05-python-s3-thumbnail git:(master) ✗ sls plugin install -n serverless-python-requirements
Serverless: Installing plugin "serverless-python-requirements@latest" (this might take a few seconds...)
Serverless: Successfully installed "serverless-python-requirements@latest"
➜  05-python-s3-thumbnail git:(master) ✗ sls deploy
```

Now we can test it by uploading an image:

![](2021-10-12-16-00-45.png)

After we refresh the bucket, the thumbnail is available:

![](2021-10-12-16-08-23.png)