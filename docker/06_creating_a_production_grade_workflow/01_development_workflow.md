# Development workflow

In this section we'll start looking at the production-grade workflow which consists of following steps:
1. Development
2. Testing
3. Deployment

In order to setup this development workflow, will revolve around creating a github repository from where it will be deployed to a hosting service.
Github workflow will use feature branch workflow.

Changes that is to be merged in master will be issued by a pull request, which automatically will also invoke:
1. TravisCI tests

After the merge we'll invoke:
1. TravisCI tests
2. Deploy to AWS Elastic Beanstalk