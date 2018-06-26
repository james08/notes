# Kubernetes Objects Presentation Notes

What is an object in Kubernetes?
>A Kubernetes object is a “record of intent”–once you create the object, the Kubernetes system will constantly work to ensure that object exists. By creating an object, you’re effectively telling the Kubernetes system what you want your cluster’s workload to look like; this is your cluster’s __desired state__.

How do you use an object?


## Speech

This is what an API object looks like. Typically a yaml file

Two main parts. Spec and Status.

The spec is where you tell Kub what you want

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
