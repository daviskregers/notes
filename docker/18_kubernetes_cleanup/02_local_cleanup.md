# Local Environment Cleanup

## Stopping minikube

To stop Minikube, and the VM that it runs, run `minikube stop` .  You can bring your local cluster back online at any time by running `minikube start`

## Stopping running containers

You might still have some containers running on your machine.  Try a `docker ps`.  You can then run `docker stop <container_id>` to clean up any running containers.

## Clearing the Build cache

All the images that we built and ran during the course are cached on your local machine - they might be taking up to around 1GB of space.  You can clean these up by running `docker system prune`.