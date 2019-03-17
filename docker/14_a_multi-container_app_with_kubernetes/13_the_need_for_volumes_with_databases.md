# The need for volumes with databases

We are going to set up the `Postgre PVC` in the previous schema, which stands for `Persistent Volume Claim`.

If we would have a pod that crashes for the postgres, kubernetes would remove it and create a new clean one. If we would not have a volume, all data that was written to it would be lost.

So, we use volumes to host the data on the host machine.