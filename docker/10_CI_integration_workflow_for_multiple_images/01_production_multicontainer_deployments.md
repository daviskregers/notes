# Production multi-container deployments

Previously on our single container setup we were:
1. Pushing code to github
2. TravisCI automatically pulled repo
3. TravisCI built an image, tested the code
4. TravisCI pushed the code to AWS ELB
5. ELB built image, deployed it

In our multi-container setup:
1. We push to github
2. TravisCI automatically pulls repo
3. Travis CI builds a test image, tests the code
4. TravisCI builds prod images
5. TravisCI pushes built prod images to docker hub
6. Travis pushes project to AWS ELB
7. ELB pulls images from Docker Hub, deploys

