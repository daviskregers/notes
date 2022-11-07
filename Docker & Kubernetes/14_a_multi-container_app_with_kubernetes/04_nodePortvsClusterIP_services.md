# NodePort vs ClusterIP Services

Now, when we have a `client-deployment`, we are going to create the `ClusterIP` Service that is before it in the schema.

Previously we used a `NodePort` service.

The difference between these object types is that `ClusterIP` exposes a set of pods to other objects in the cluster while `NodePort` exposes a set of pods to the outside world (only good for dev purposes).

So, we are goin to create a new file `k8s/client-cluster-ip-service.yaml`:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: client-cluster-ip-service
spec:
  type: ClusterIP
  selector:
      component: web
  ports:
    - port: 3000
      targetPort: 3000
```