# CodePipeline Overview

- Visual Workflow to orchestrate your CICD
- Source - CodeCommit, ECR, S3, Bitbucket, Github
- Build - CodeBuild, Jenkins, CloudBees, TeamCity
- Test - CodeBuild, AWS Device Farm, 3rd party tools
- Deploy - CodeDeploy, ElasticBeanstalk, CloudFormation, ECS, S3, ...
- Consists of stages:
    - Each stage can have sequential actions and/or parallel actions
    - Example: Build->Test->Deploy->Load Testing->...
    - Manual approval can be defined at any stage

![](2022-04-21-08-20-30.png)

## Artifacts

- Each pipeline stage can create artifacts
- Artifacts stored in an S3 bucket and passed on to the next stage

## Troubleshooting

- For CodePipeline Pipeline/Action/Stage Execution State Changes
- Use CloudWatch Events (Amazon EventBridge). Example:
    - You can create events for failed pipelines
    - You can create events for cancelled stages
- If CodePipeline fails a stage, your pipeline stops, and you can get information in the console
- If pipeline can't perform an action, make sure the "IAM Service Role" attached does have enough IAM permissions (IAM Policy)
- AWS CloudTrail can be used to audit AWS API calls