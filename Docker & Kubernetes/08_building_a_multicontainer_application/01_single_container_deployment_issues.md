# Single Container Deployment Issues

In the previous section, there were a couple issues that were not addressed:
1. The app was simple - no outside dependencies
2. Our image was build multiple times
3. We did not use any databases

In this section we'll make a multi-container application that will use multiple databases, that is tied together with docker-compose and deployed to AWS ELB.

