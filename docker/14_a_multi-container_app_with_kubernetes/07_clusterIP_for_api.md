# Cluster IP for the Express API

Now we are going to make a configuration file `k8s/server-cluseter-ip-service.yaml`.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: server-cluster-ip-service
spec:
  type: ClusterIP
  selector:
      component: server
  ports:
    - port: 5000
      targetPort: 5000
```