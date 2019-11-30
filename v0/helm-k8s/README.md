# Helm chart for npiper-rest-reference Deployment

A helm chart for deploying the npiper-rest-reference spring boot application.

# LOCAL Environment - MacOS Docker Desktop + Kubernetes

Once you've installed Docker , and Docker for Desktop - enable kubernetes and start to set it up.  It appears Helm is already installed.

```
kubectl config get-contexts
kubectl config use-context docker-for-desktop

// Test
kubectl get namespaces
```

## Get a Dashboard

See: https://github.com/kubernetes/dashboard

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml

kubectl proxy

http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/login
```

## [Helm Quickstart](https://helm.sh/docs/intro/quickstart/)

## Helm - Add repositories
```
helm repo add stable https://kubernetes-charts.storage.googleapis.com/

// Install RabbitMQ
helm install stable/rabbitmq --generate-name
```
## Create a chart

```
helm create npiper-rest-reference
```

# Install it

```
helm install npiper-rest-reference ./npiper-rest-reference

// Get the port
kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services npiper-rest-reference
```

Then go to `http://localhost:{port}/depot/10001/inventory_summaries`

# References

https://www.baeldung.com/kubernetes-helm

https://medium.com/containers-101/local-kubernetes-for-mac-minikube-vs-docker-desktop-f2789b3cad3a

https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md

https://github.com/kubernetes/dashboard

https://helm.sh/docs/intro/
