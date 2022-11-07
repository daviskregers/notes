# Travis deployment overview

We are going to do following steps to deploy the application to Google Cloud using Travis CI.

1. Install Gogle Cloud SDK CLI
2. Configure the SDK with out Google Cloud auth info
3. Login to Docker CLI
4. Build the `test` version of multi-client
5. Run tests
6. If tests pass, run a script to deploy newest images
7. Build all our images, tag each one, push each to docker hub
8. Apply all configs in `k8s` folder
9. Imperatively set latest images on each deployment

