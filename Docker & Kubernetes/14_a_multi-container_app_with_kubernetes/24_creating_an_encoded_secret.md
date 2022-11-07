# Creating an encoded secret

We dont want to store the last environment variable the `PGPASSWORD` as a plain text. We can store it as a secret object which securely stores a piece of information in the cluster such as passwords.

In order to create it:

```
kubectl create secret <generic|docker-registry|tls> <secret name> --from-literalkey=value
```

```
$ kubectl create secret generic pgpassword --from-litraal PGPASSWORD=12345asd 
secret/pgpassword created
```

```
$ kubectl get secrets
NAME                  TYPE                                  DATA   AGE
default-token-vq8qh   kubernetes.io/service-account-token   3      5h37m
pgpassword            Opaque                                1      26s
```