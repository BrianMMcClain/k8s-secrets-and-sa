Kubernetes Secrets and Service Accounts
===

Secrets
---

- `secret.yaml`: Basic secret to use in the example pods. Username and password are encoded as base64

pod-secret-as-file.yaml
---

Mounts the secret as files in the pod, which can be accessed as any other file. 

`kubectl apply -f pod-secret-as-file.yaml`

```
$ kubectl exec secret-as-file -- ls /etc/mysecret       
password
username
```

```
$ kubectl exec secret-as-file -- cat /etc/mysecret/username
myusername
```

pod-secret-as-env.yaml
---

Stores the secrets as environment variables.

`kubectl apply -f pod-secret-as-env.yaml`

```
$ kubectl exec secret-as-env -- sh -c "echo \$SECRET_USERNAME"
myusername
```