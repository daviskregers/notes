# Lambda@Edge Overview

- You have deployed a CDN using CloudFront
- What if you wanted to run a global AWS Lambda alongside?
- Or how to implement request filtering before reaching your application?

- For this, you can use Lambda@Edge
    - Deploy lambda functions alongside your CloudFront CDN
        - Build more responsive applications
        - You don't manage servers, Lambda is deployed globally
        - Customize CDN content
        - Pay only for what you use

## Lambda@Edge

- You can use Lambda to change CloudFront requests and responses
    - After CloudFront receives a request from a viewer (viewer request)
    - Before CloudFront forwwards the request to the origin (origin request)
    - After CloudFront receives the response from the origin (origin response)
    - Before CloudFront forwards the response to the viewer (viewer response)
    - You can also generate responses to viewers without ever sending the request to the origin.

![](2022-05-12-07-28-52.png)

![](2022-05-12-07-29-15.png)

## Use Cases

- Website Security and Privacy
- Dynamic Web Application at the Edge
- Search Enging Optimization (SEO)
- Intelligently Route Across Origins and Data Centers
- Bot Mitigation at the Edge
- Real-time Image Transformation
- A/B Testing
- User Authentication and Authorization
- User Prioritization
- User Tracking and Analytics

