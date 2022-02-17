# CloudFront Caching & Caching Invalidations

## CloudFront Caching

- Cache based on
    - Headers
    - Session Cookies
    - Query String Parameters
- The cache lives at each CloudFront Edge Location
- You want to maximize the cache hit rate to minimize requests on the origin
- Control the TTL (0 seconds to 1 year), can be set by the origin using the Cache-Control header, Expires header
- You can invalidate part of the cache using the CreateInvalidation API