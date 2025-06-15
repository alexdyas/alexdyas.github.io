---
title: "One imagePullBackoff reason amongst many"
date: 2025-06-15T12:19:38-04:00
categories:
  - technical
tags:
  - kubernetes
---
I stumbled across a new to me reason for the irritating imagePullBackoff error in Kubernetes. Amongst the many well documents reasons this can happen, bad credentials, wrong path to container image etc, you should also check for wrong secret type.

A properly constructed secret for container registry authentication looks like this:
```
apiVersion: v1
kind: Secret
metadata:
  name: mygreatapp-registry-credentials
  namespace: mygreatapp
data:
  .dockerconfigjson: UmVhbGx5IHJlYWxseSByZWVlZWVlZWVlZWFhYWFhYWFhYWFhYWFhYWFhYWFhYWFhYWFhYWxsbGxsbGxsbGxsbGxsbGxsbGxsbGxsbGxsbGxsbGx5eXl5eXl5eXl5eXl5eXl5eXl5eSBsbGxsbGxsbGxsbGxsbG9vb29vb29vb29vb29vb29vb29vb29vb29vb25ubm5ubm5ubm5ubm5ubm5ubm5ubm5ubmdnZ2dnZ2dnZ2dnZ2dnZ2dnZ2cgYXV0aCBrZXlzCg==
type: kubernetes.io/dockerconfigjson
```
Note the secret type. If you forget to define the correct type Kubernetes will not use the secret as authentication for the image pull.
