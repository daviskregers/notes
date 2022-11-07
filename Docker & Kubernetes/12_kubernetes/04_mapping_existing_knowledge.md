# Mapping existing knowledge

## Goal

Get the `multi-client` image running on our local Kubernetes Cluster running as a container.

## Compose

The `multi-client docker-compose.yml` file:

- Each service can optionally get docker-compose to build the image
- Each service represents a container we want to create
- Each entry defines the networking requirements, ports

In `Kubernetes`:

- Expects all images to be already built
- One config per object we want to create
- We have to manually set up all the networking

## Config

Get a simple container running on our local Kubernetes running:

- Make sure our image is hosted on docker hub
- Make one config file to create the container
- Make one config file to set up networking

