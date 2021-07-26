# AWS Cloud Overview - Regions & AZ

## AWS Cloud history
- 2002 - AWS was launched internally.
- 2003 - Amazon infrastructure is one of their core strength. Idea to market.
- 2004 - Launched publicly with SQS
- 2006 - Re-launched publicly with SQS, S3 & EC2
- 2007 - Launched in Europe

- In 2019, AWS had $35.02 billion in annual revenue
- AWS accounts for 47% of market in 2019 (microsoft is 2nd with 22%)
- Pioneer and Leader of the AWS Cloud Market for the 9th consecutive year
- Over 1 million active users

## AWS Cloud Use Cases

- AWS Enables you to build sophisticaed, scalable applications
- Applicable to a diverse set of industries
    - MCDonalds
    - 21st century fox
    - Activision
    - Netflix
- Use cases include
    - Enterprise IT
    - Backup & Storage,
    - Big Data Analytics
    - Website hosting, Mobile & Social Apps
    - Gaming

## AWS Global infrastructure

- AWS Regions
    - It has regions all around the world
    - Names can be us-east-1, eu-west-3
    - A region is a cluster of data centers
    - Most AWS Services are region scoped
    - You might want to choose an AWS region based on following criteria:
        - Compliance - with data governance and legal requirements: data never leaves a region without your explicit permission.
        - Proximity to customers: reduced latency
        - Available services within a region: new services and new features aren' t available in every region.
        - Pricing: pricing varies region to region and is transparent in the service pricing page.
- AWS Availability Zones
    - Each region has many availability zones (usually 3, min is 2, max is 6).
        - ap-southeast-2a
        - ap-southeast-2b
        - ap-southeast-2c
    - Each availability zone (AZ) is one or more discrete data centers with redundant power, networking and connectivity.
    - They're separate from each other, so that they' re isolated from disasters
    - They're connected with high bandwidth, ultra-low latency networking
- AWS Edge Locations / Points of Presence
    - Amazon has 216 Points of Presence (205 Edge Locations & || regional caches) in 84 cities across 42 countries.
    - Content is delivered to end users with lower latency.

https://infrastructure.aws/

## Tour of the AWS Console

- AWS has Global Services:
    - Identity and Access Management (IAM)
    - Route 53 (DNS Service)
    - CloudFront (Content Delivery Network)
    - WAF (Web Application Firewall)
- Most AWS Services are region-scoped:
    - Amazon EC2 (Infrastructure as a Service)
    - Elastic Beanstalk (Platform as a Service)
    - Lambda (Function as a Service)
    - Rekognition (Software as a Service)
Region table: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services
