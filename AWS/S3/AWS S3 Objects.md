---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## Objects

- [[AWS S3 Objects]] (files) have a Key. The key is the full path.
    - <my_bucket>/my_file.txt
    - <my_bucket>/my_folder1/another/my_file.txt
- There's no concept of "directories" within [[AWS S3 Bucket]] (although the UI will trick you to think otherwise).
- Just keys with very long names that contain slashes ("/")
- Object values are the content of the body:
    - Max Size is 5TB
    - If uploading more than 5GB, must use "multi-part upload"
- Metadata (list of text /key pairs - system or user metadata)
- Tags (unicode key/value pair - up to 10) - useful for security / lifecycle.
- Version ID - if versioning enabled

The creation process is fairly easy:

![](2019-12-30-11-42-53.png)

![](2019-12-30-11-43-40.png)

![](2019-12-30-11-44-07.png)

When opening the bucket, we can upload files to it: 

![](2019-12-30-11-45-13.png)

![](2019-12-30-11-46-52.png)