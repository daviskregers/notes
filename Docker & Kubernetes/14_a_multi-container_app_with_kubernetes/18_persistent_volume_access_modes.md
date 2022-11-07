# Persistent VOlume Access Modes

Once more, a volume claim is something we attach to a pod config.
So, previously created PVC tells kubernetes that it must find a volume with the given requirements.

We have 3 different access modes:
- ReadWriteOnce - can be used by a single node at a time
- ReadOnlyMany - multiple nodes at the same time can read from this volume
- ReadWriteMany - can be read and written to by many nodes

And the storage has to be 2G  of space.

