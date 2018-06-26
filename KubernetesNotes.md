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
Seeing as K8s uses API objects to do pretty much... everything.

This is what an API object looks like. Typically a yaml file

Two main parts. Spec and Status.

The spec is where you tell K8s what you want. Some fields are mantatory, some are optional, some are added by K8s.

The status is where Kubernetes tells you where its at.


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
