# CloudFront Signed URL / Cookies

- You want to distribute paid shared content to premium users over the world
- We can use CloudFront Signed URL / Cookie. We attach a policy with:
    - Includes URL expiration
    - Includes IP ranges to access the data from
    - Trusted signers (which AWS accounts can create signed URLs)
- How long should the URL be valid for?
    - shared content (movie, music): make it short (a few minutes)
    - private content (private to the user): you can make it last for years
- Signed URL = access to individual files (one signed URL per file)
- Signed Cookies = access to multiple files (one signed cookie for many files)

## CloudFront Signed URL vs S3 Pre-Signed URL

- CloudFront Signed URL
    - Allow access to a path, no matter the origin
    - Account wide key-pair, only the root can manage it
    - Can filter by IP, path,date, expiration
    - Can leverage caching features
- S3 Pre-Signed URL:
    - Issue a request as the person who pre-signed the URL
    - Uses IAM  key of the signing IAM principal
    - Limited Lifetime