# Beanstalk lifecycle policy

- Elastic Beanstalk can store at most 1000 application versions
- If you don't remove old versions you won't be able to deploy anymore
- To phase out old application versions, use a lifecycle policy
    - Based on time (old versions are removed)
    - Based on space (when you have too many versions)
- Versions that are currently used won't be deleted
- Option not to delete the source bundle in S3 to prevent data loss