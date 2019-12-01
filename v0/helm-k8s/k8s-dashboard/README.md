# K8S Dashboard setup

https://github.com/kubernetes/dashboard

# User Setup

```
kubectl create -f serviceAccount.yaml
kubectl create -f clusterRoleBinding.yaml
```

# Getting a token

```
kubectl proxy

kubectl -n kube-system describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')
```
