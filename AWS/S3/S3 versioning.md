---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, review]
sr-due: 2023-01-15
sr-interval: 54
sr-ease: 270
---

# S3 Versioning

- You can version your files in [[AWS S3]]
- It is enabled at the [[AWS S3 Bucket]] level
- Same key overwrite will increment it's version
- It is best practice your [[AWS S3 Bucket]]
    - Protect against unintended deletes (ability to restore a version)
    - Easy [[roll back]] to previous version
- Any file that is not versioned prior to enabling versioning will have version "null"

![](2019-12-30-11-49-00.png)

![](2019-12-30-11-49-40.png)

If we upload the same file once more:

![](2019-12-30-11-51-14.png)

Even if we hide the versions and delete the file, it will still be visible under the versions tab.