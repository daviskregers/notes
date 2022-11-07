# Running containers in pods

When  we installed `kubectl` and `minikube`, we ran a command `minikube start`. It created a new VM on our computer that is running as a `Node`.

It will be used by kubernetes to run different objects.

One of the most basic objects are known as a `Pod` for which we previously made a configuration file. It will group containers for the nginx image.

Pod must run 1 or more containers within it. Usually when there are multiple containers defined in the `Pod`, it is because they are tighlt coupled. Like a `database backup` service would most certaily need a database in order for it to run.

The metadata section is mostly used for logging purposes and object coupling.
