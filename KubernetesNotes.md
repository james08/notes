# Kubernetes Objects Presentation Notes

## Agenda
1. What is an API object in Kubernetes?
  * API self discovery
2. How does a user use these objects to interact with a Kubernetes cluster?
3. API object conventions
4. Custom objects
5.


What is an object in Kubernetes?
>A Kubernetes object is a “record of intent”–once you create the object, the Kubernetes system will constantly work to ensure that object exists. By creating an object, you’re effectively telling the Kubernetes system what you want your cluster’s workload to look like; this is your cluster’s __desired state__.

How do you use an object?


## Speech
_slide 1..3_  

I'm going to start by using minikube to start a basic local k8s cluster to play with.

The primary method of interacting with the Kubernetes cluster is via the API.


A resource is an endpoint in the Kubernetes API that stores a collection of API objects of a certain kind. For example, the built-in pods resource contains a collection of Pod objects. Here is an example which also illustrates the api self discovery feature.


_give example_

http://localhost:8001/apis/apps/v1/deployments

go to selfLink

Objects are stored as resources located via the API endpoint. For example you may hit an endpoint and get a response that says 'No resource found'


Demo of object creation and status change:

```bash
watch -n 0.5 curl -i 'http://localhost:8001/apis/apps/v1/namespaces/default/deployments/deployment-example | grep -E "(spec|status)" -A 10'
```

```bash
echo 'apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: deployment-example
spec:
  replicas: 3
  revisionHistoryLimit: 10
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.10
        ports:
        - containerPort: 80
' | kubectl create -f -
```


```bash
$ minikube status
minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
```

```bash
$ kubectl proxy
Starting to serve on 127.0.0.1:8001
```

http://localhost:8001/api/v1/pods

http://localhost:8001/api/v1/namespaces/default/pods/liveness-exec

This is what an API object looks like. Typically a yaml file

Two main parts. Spec and Status.

The spec is where you tell K8s what you want. Some fields are mantatory, some are optional, some are added by K8s.

The status is where Kubernetes tells you where its at.

OBJECT FIELDS:
  apiVersion
  kind
  metadata
  spec

OBJECT MANAGEMENT

Declarative object configuration - updates only what's changed, thereby retaining other users' changes.


## Commands
```bash

watch -n 1 'kubectl get pods'
kubectl edit -f webserver.yaml
```

## URLS
Get all api endpoints: http://localhost:8001/#!/namespace?namespace=default  
Get deployments: http://localhost:8001/apis/apps/v1/deployments

## References
https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.10/#-strong-write-operations-strong-

https://github.com/kubernetes/community/blob/master/contributors/devel/api-conventions.md#objects

https://kubernetes.io/docs/tasks/access-kubernetes-api/extend-api-custom-resource-definitions/

https://kubernetes.io/docs/tasks/access-kubernetes-api/setup-extension-api-server/

https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/

https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/

https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.10/#-strong-write-operations-strong--20

https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/
