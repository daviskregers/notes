# S3 Buckets and Objects

## Buckets

- Amazon S3 allows people to store objects (files) in buckets (directories)
- Buckets must have a globally unique name
- Buckets are defined at the region level
- Naming convention
    - no uppercase
    - no underscore
    - 3-63 characters long
    - not an IP
    - must start with lowercase letter or number

## Objects

- Objects (files) have a key
- The key is full path:
    - s3://my-bucket/my_file.txt
    - s3://my-bucket/my_folder1/another_folder/my_name.txt
- The key is composed of prefix + object name
    - prefix: my_folder1/another_folder
    - name: my_name.txt
- There's no concept of "directories" within buckets. Although the UI will trick you to think otherwise.
- Just keys with very long names that contain slashes.

---

- Object values are content of the body:
    - Max object size is 5 TB
    - If uploading more than 5 GB, must use multi-part upload
- Metadata (list of text key / value pairs - system or user metadata)
- Tags (unicode key / value pair - up to 10) - useful for security / lifecycle
- Version ID (if versioning is enabled)

