# Amazon S3 - Versioning

- You can version your files in Amazon S3
- It's enabled at the bucket level
- Same key overwrite will increment version by 1
- It is best practice to version your buckets
    - Protect against unintended deletes (ability to restore a version)
    - Easy roll back to previous version
- Notes:
    - Any file that is not versioned prior to enabling versioning will have version null
    - Suspending versioning does not delete the previous versions