# Verifying the certificate

We can check if everything was set up correctly by running a command:

```
kregers_davis@cloudshell:~ (multi-k8s-236808)$ kubectl get certificates
NAME
k8s-deiveris-lv-tls
```

```
kregers_davis@cloudshell:~ (multi-k8s-236808)$ kubectl describe certificates
Name:         k8s-deiveris-lv-tls
Namespace:    default
Labels:       <none>
Annotations:  kubectl.kubernetes.io/last-applied-configuration={"apiVersion":"certmanager.k8s.io/v1alpha1","kind":"Certificate","metadata":{"annotations":{},"name":"k8s-deiveris-lv-tls","namespace":"default"},"spec...
API Version:  certmanager.k8s.io/v1alpha1
Kind:         Certificate
Metadata:
  Creation Timestamp:  2019-04-06T12:16:17Z
  Generation:          1
  Resource Version:    36905
  Self Link:           /apis/certmanager.k8s.io/v1alpha1/namespaces/default/certificates/k8s-deiveris-lv-tls
  UID:                 c7cb696e-5865-11e9-ac17-42010a840032
Spec:
  Acme:
    Config:
      Domains:
        k8s.deiveris.lv
      Http 01:
        Ingress Class:  nginx
  Common Name:          k8s.deiveris.lv
  Dns Names:
    k8s.deiveris.lv
  Issuer Ref:
    Kind:       ClusterIssuer
    Name:       letsencrypt-prod
  Secret Name:  k8s-deiveris-lv
Status:
  Conditions:
    Last Transition Time:  2019-04-06T12:16:52Z
    Message:               Certificate is up to date and has not expired
    Reason:                Ready
    Status:                True
    Type:                  Ready
  Not After:               2019-07-05T11:16:51Z
Events:
  Type     Reason              Age              From          Message
  ----     ------              ----             ----          -------
  Warning  IssuerNotFound      3m (x2 over 3m)  cert-manager  clusterissuer.certmanager.k8s.io "letsencrypt-prod" not found
  Warning  IssuerNotReady      3m               cert-manager  Issuer letsencrypt-prod not ready
  Normal   Generated           3m               cert-manager  Generated new private key
  Normal   GenerateSelfSigned  3m               cert-manager  Generated temporary self signed certificate
  Normal   OrderCreated        3m               cert-manager  Created Order resource "k8s-deiveris-lv-tls-2662049116"
  Normal   OrderComplete       2m               cert-manager  Order "k8s-deiveris-lv-tls-2662049116" completed successfully
  Normal   CertIssued          2m               cert-manager  Certificate issued successfully
```

Check that secrets are created:

```
kregers_davis@cloudshell:~ (multi-k8s-236808)$ kubectl get secrets
NAME                                 TYPE                                  DATA      AGE
default-token-6vq4q                  kubernetes.io/service-account-token   3         3h
k8s-deiveris-lv                      kubernetes.io/tls                     3         5m
my-nginx-nginx-ingress-token-mrtj5   kubernetes.io/service-account-token   3         1h
pgpassword                           Opaque                                1         2h
kregers_davis@cloudshell:~ (multi-k8s-236808)$
```