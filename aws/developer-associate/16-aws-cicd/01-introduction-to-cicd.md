# CICD - Introduction

- We have learned how to:
    - Create AWS resources, manually (fundamentals)
    - Interact with AWS programmatically (AWS CLI)
    - Deploy code to AWS using Elastic Beanstalk
- All these manual steps make it very likely for us to do mistakes.
- We would like our code "in a repository" and have it deployed onto AWS
    - Automatically
    - The right way
    - Making sure it's tested before deployed
    - With possibility to go into different stages (dev, test, staging, prod)
    - With manual approval where needed
- To be a proper AWS developer - we need to learn AWS CICD

---

- This section is all about automating the deployment we've done so far while adding increased safety
- We'll learn about:
    - AWS CodeCommit - storing our code
    - AWS CodePipeline - automating our pipeline from code to Elastic Beanstalk
    - AWS CodeBuild - building and testing our code
    - AWS CodeDeploy - deploying the code to EC2 instances (not ElasticBeanstalk)
    - AWS CodeStar - manage software development activities in one place
    - AWS CodeArtifact - store, publish and share software packages
    - AWS CodeGuru - automated code reviews using Machine Learning

---

## Continuous Integration (CI)

- Developers push the code to a code repository often (e.g. GitHub, CodeCommit, BitBucket...)
- A testing / build server checks the code as soon as it's published (CodeBuild, Jenkins CI, ...)
- The developer gets feedback about the tests and checks that have passed / failed

- Find bugs early, then fix bugs
- Deliver faster as the code is tested
- Deploy often
- Happier developers, as they're unblocked

![](2022-04-21-07-49-15.png)


## Continous Deliver (CD)

- Ensures that the software can be released reliably whenever needed
- Ensures deployments happen often and are quick
- Shift away from "one release every 3 months" to "5 releases a day"
- That usually means automated deployment (e.g. CodeDeploy, Jenkins CD, Spinnaker, ...)

![](2022-04-21-07-51-02.png)

## Technology Stack for CICD

![](2022-04-21-07-51-53.png)