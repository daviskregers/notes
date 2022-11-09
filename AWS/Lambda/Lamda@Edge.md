---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/lambda, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---


## Lamda@Edge

- You have deployed a [[CDN]] using [[Programming/AWS/CloudFront/AWS CloudFront]]
- What if you wanted to run a global [[AWS Lambda]] alongside?
- Or how to implement request filtering before reaching your application?
- For this, you can use Lambda@Edge
    - Deploy Lambda functions alongside your [[Programming/AWS/CloudFront/AWS CloudFront]] CDN
        - Build more responsive applications
        - You don't manage servers, Lambda is deployed globally
        - Customise the [[CDN]] content
        - Pay only for what you use
- You can use [[AWS Lambda]] to change [[Programming/AWS/CloudFront/AWS CloudFront | CloudFront]] requests and responses
    - After CloudFront receives a request from a viewer (viewer request)
    - Before CloudFront forwards the request to the origin (origin request)
    - After CloudFront receives the response from the origin (origin response)
    - Before CloudFront forwards the response to the viewer (viewer response)
    - You can also generate responses to viewers without ever sending the request to the origin.

![](2019-12-31-12-05-18.png)
    
