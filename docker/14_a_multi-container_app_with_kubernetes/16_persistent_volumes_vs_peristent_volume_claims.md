# Persistent Volumes vs Persistent Volume Claims

A persistent volume claim is not a volume, but an options of storages instead. When a volume gets claimed, kubernetes checks statically provisioned peristent volumes, if none are found, kubernetes creates a dynamically provisioned persistent volume.

Basically, PVC looks at existing volumes, if there are none, it creates them on the fly.