# S3 versioning

- You can version your files in AWS S3
- It is enabled at the bucket level
- Same key overwrite will increment it's version
- It is best practice your buckets
    - Protect against unintended deletes (ability to restore a version)
    - Easy roll back to previous version
- Any file that is not versioned prior to enabling versioning will have version "null"

![](2019-12-30-11-49-00.png)

![](2019-12-30-11-49-40.png)

If we upload the same file once more:

![](2019-12-30-11-51-14.png)

Even if we hide the versions and delete the file, it will still be visible under the versions tab.