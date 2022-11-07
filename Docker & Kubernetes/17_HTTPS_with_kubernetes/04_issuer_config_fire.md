# Wire up Cert Manager

We are going to create `k8s/issuer.yaml` file:

```yaml
apiVersion: certmanager.k8s.io/v1alpha1
kind: ClusterIssuer
metadata:
  name: letsencrypt-prod
spec:
  acme:
    server: https://acme-v02.api.letsencrypt.org/directory
    email: 'kregers.davis@gmail.com'
    privateKeySecretRef:
      name: letsencrypt-prod
    http01: {}
```