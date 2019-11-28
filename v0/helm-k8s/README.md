# Helm / K8S Configuration

Instructions on configuration for a typical Spring Boot K8s / Helm package structure.

## Setting up Helm

Easiest is probably to use the built in K8s on your docker install.

```
brew install kubernetes-helm
helm
helm init
```

## Generating

```
helm create npiper-rest-reference
```


Let's understand the relevance of these files and folders created for us:

`Chart.yaml`: This is the main file that contains the description of our chart
`values.yaml`: this is the file that contains the default values for our chart
`templates`: This is the directory where Kubernetes resources are defined as templates
`charts`: This is an optional directory that may contain sub-charts
.helmignore: This is where we can define patterns to ignore when packaging (similar in concept to .gitignore)

# What we should create - Chart setup

## Deployment

`./templates/deployment.yaml`

In the file there are significant use of this syntax:

 `{{ include "hello-world.fullname" . }}`

These are the template / instructions for Helm to do its stuff.

## Service

`./templates/service.yaml`

## Providing values

We typically pass values through Built-in Objects in Helm. This is possibly the best location to provide environment specific settings / url's.

There are many such objects available in Helm, like `Release`, `Values`, `Chart`, and `Files`.

We can use the file `values.yaml` in our chart to pass values to the template rendering engine through the Built-in Object Values.

```
replicaCount: 1
image:
  repository: "hello-world"
  tag: "1.0"
  pullPolicy: IfNotPresent
service:
  type: NodePort
  port: 80
```

# Running / Testing the Chart

## Static test - 'Lint'

Test your code by substitution that there are no gaps, failures or syntax issues.

```
helm lint ./hello-world
```

## Render template locally

Use this to get quick feedback, generation.

```
helm template ./hello-world
```


## Install It!

Now you are ready, tell helm to install

```
helm install --name hello-world ./hello-world
```

TO update it:
```
helm upgrade hello-world ./hello-world
```

To rollback ( a version):
```
helm rollback hello-world 1
```

## Package it

## What's installed?

```
helm ls --all
```



# References

http://collabnix.com/kubernetes-application-deployment-made-easy-using-helm-on-docker-for-mac-18-05/

https://www.baeldung.com/kubernetes-helm
