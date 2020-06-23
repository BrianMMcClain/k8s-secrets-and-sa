Kubernetes Secrets and Service Accounts
===

Secrets
---

- `secret-base64.yaml`: Basic secret to use in the example pods, where keys and values are all provided in the YAML. Username and password are encoded as base64

Containers
---
- `kubectl-alpine`: Minimal container that ships with `bash` and `kubectl`, used to demonstrate Service Accounts. Available on Docker Hub at [brianmmcclain/kubectl-alpine](https://hub.docker.com/r/brianmmcclain/kubectl-alpine).

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