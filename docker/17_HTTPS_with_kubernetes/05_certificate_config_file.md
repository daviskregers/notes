# Certificate Config File

We are going to create `k8s/certificate.yaml`:

```yaml
apiVersion: certmanager.k8s.io/v1alpha1
kind: Certificate
metadata:
  name: k8s-deiveris-lv-tls
spec:
  secretName: k8s-deiveris-lv
  issuerRef:
    name: letsencrypt-prod
    kind: ClusterIssuer
  commonName: k8s.deiveris.lv
  dnsNames:
    - k8s.deiveris.lv
  acme:
    config:
      - http01:
          ingressClass: nginx
        domains:
          - k8s.deiveris.lv
```
