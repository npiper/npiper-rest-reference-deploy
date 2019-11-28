# npiper-rest-reference Microservice deploy project 

This example demonstrates how to pull a docker image into different deployment architectures in a similar fashion that utilises 12 factor app style configuration injection (environment variables) per environment. 


## Level 1 - Which Version am I Deploying?

As a service develops it will have different properties and capabilities, we will be managing this at the MAJOR version level.

The Top level directory is named accordingly e.g. (v0, v1,..)

## Level 2 - Which Container / Cloud Product?

Next - where? There isn't much commonality - we may have a general 'config' properties set that migrates across environment but here choose where this is going.

 * helm-k8s
 * openshift
 * AWS-ECS
 * docker-swarm
 * ...


## Level 3 - Which Environment?

Once we know our cloud and product, decide where we are going... LOCAL, DEV, TEST or PROD are our choices.

The settings should ideally just be different property settings per environment.

## What did we use/

The sample used fabric8 maven archetype to set up.

```
Archetype: spring-boot-webmvc-archetype:2.2.197
```

### Building

The example can be built with

  

### Running the example in Kubernetes

It is assumed a running Kubernetes platform is already running. If not you can find details how to [get started](http://fabric8.io/guide/getStarted/index.html).

Assuming your current shell is connected to Kubernetes or OpenShift so that you can type a command like

```
kubectl get pods
```

or for OpenShift

```
oc get pods
```

Then the following command will package your app and run it on Kubernetes:

```
mvn fabric8:run
```

To list all the running pods:

    oc get pods

Then find the name of the pod that runs this quickstart, and output the logs from the running pods with:

    oc logs <name of pod>

You can also use the [fabric8 developer console](http://fabric8.io/guide/console.html) to manage the running pods, and view logs and much more.


#### Integration Testing

The example includes a [fabric8 arquillian](https://github.com/fabric8io/fabric8/tree/master/components/fabric8-arquillian) Kubernetes Integration Test. 
Once the container image has been built and deployed in Kubernetes, the integration test can be run with:

	mvn test -Dtest=*KT

The test is disabled by default and has to be enabled using `-Dtest`. [Integration Testing](https://fabric8.io/guide/testing.html) and [Fabric8 Arquillian Extension](https://fabric8.io/guide/arquillian.html) provide more information on writing full fledged black box integration tests for Kubernetes. 

### More details

You can find more details about running this [quickstart](http://fabric8.io/guide/quickstarts/running.html) on the website. This also includes instructions how to change the Docker image user and registry.


### Access services using a web browser

When the application is running, you can use a web browser to access the REST service. Assuming that you
have a [Vagrant setup](http://fabric8.io/guide/getStarted/vagrant.html) you can access the REST service with
`http://spring-boot-webmvc-default.vagrant.f8`.

Notice: As it depends on your OpenShift setup, the hostname (route) might vary. Verify with `oc get routes` which
hostname is valid for you.  Add the '-Dfabric8.deploy.createExternalUrls=true' option to your maven commands if you want it to deploy a Route configuration for the service.

The URL `http://spring-boot-webmvc-default.vagrant.f8/ip` can be used to obtain the IP address to show service load-balancing
when running with multiple pods.


#### Integration Testing

The example includes a [fabric8 arquillian](https://github.com/fabric8io/fabric8/tree/master/components/fabric8-arquillian) Kubernetes Integration Test. 
Once the container image has been built and deployed in Kubernetes, the integration test can be run with:

	mvn test -Dtest=*KT

The test is disabled by default and has to be enabled using `-Dtest`. [Integration Testing](https://fabric8.io/guide/testing.html) and [Fabric8 Arquillian Extension](https://fabric8.io/guide/arquillian.html) provide more information on writing full fledged black box integration tests for Kubernetes. 

### More details

You can find more details about running this [quickstart](http://fabric8.io/guide/quickstarts/running.html) on the website. This also includes instructions how to change the Docker image user and registry.

