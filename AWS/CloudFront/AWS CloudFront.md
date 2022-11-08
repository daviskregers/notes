---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/cloudfront, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# AWS CloudFront

- [[Content Delivery Network (CDN)]]
- Improves read performance, content is cached at [[edge]]
- 136 points of presence globally ([[edge locations]])
- Popular with [[S3]] but works with [[AWS EC2]], [[Programming/AWS/EC2/Elastic LoadBalancer 2/Load Balancing]]
- Can help to protect against [[network attacks]]
- Can provide [[SSL encryption]] ([[HTTPS]]) at the edge using ACM
- [[Programming/AWS/CloudFront/AWS CloudFront]] can use SSL encryption (HTTPS) to talk to your applications
- Support [[RTMP Protocol]] (videos/media)

## CloudFront Signed URL / Signed Cookies

- Say you wanted to distribute paid shared content to premium users over the world, the content lives int [[S3]].
- If S3 can only be accessed through CloudFront, we cannot use self-signed S3 URLS
- We can use CloudFront signed URLs. We attach a policy with:
    - Included URL expiration
    - Include IP ranges to access data from
    - Trusted signers (which AWS accounts can create signed URLs)
- CloudFront signed URL can only be created using the AWS SDK, so you have to code an application to verify users and generate these URLs
- How long should the url be valid for?
    - Shared content (movie, music): make it short (a few minutes)
    - Private content (private to the user): you can make it last for years

## CloudFront vs [[S3 Cross Region Replication]]

- CloudFront
    - Global [[Edge Network]]
    - Files are cached for a [[TTL]] (maybe a day)
    - Great for static content that must be available everywhere
    - Geo Restriction - you can restrict who can access your distribution
        - Whitelist - allow your users to access your content only if they're in one of the countries on a list of approved countries
        - Blacklist - prevent your users from accessing your content if they're in one of the countries on a blacklist of banned countries.
        - The country is determined by using a 3rd party Geo-IP database
        - Use case - copyright laws to control access to content
- [[S3 Cross Region replication]]
    - Must be setup for each region you want replication to happen
    - Files are updated in near real-time
    - Read only
    - Great for dynamic content that needs to be available at low latency in few regions