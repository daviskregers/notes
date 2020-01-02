# S3 Default encryption

- The old way to enable default encryption was to use a bucket policy and refuse any HTTP command without the proper headers.
- The new way is to use the "default encryption" option in S3
- Note: Bucket policies are evaluated before "default ecnryption"
