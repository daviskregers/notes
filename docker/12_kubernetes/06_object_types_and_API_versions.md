# Object types and API versions

Previously made configuration files are used to make kubernetes objects which are slightly different than docker containers.

The term `object` references a thing that exists in the kubernetes cluster that can be one of many types like:

- StatefulSet
- ReplicaController
- Pod
- Service
- etc

Objects serve different purposes - running a container, monitoring container, setting up networking etc.

When we specify `apiVersion` in the configuration file scopes types of objects we want to create in the configuration file:

- `apiVersion: v1`
  - componentStatus
  - configMap
  - Endpoints
  - Event
  - Namespace
  - Pod
  - ...
- `apiVersion: apps/v1`
  - ConvrollerRevision
  - StatefulSet
  - ...