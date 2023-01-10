---
title: "kubectl - Escaping periods in field names with jsonpath."
date: 2023-01-10T13:25:38-04:00
categories:
  - technical
tags:
  - kubernetes
  - jsonpath
---
Given the following `.dockerconfigjson` type secret in Kubernetes:
```
{
    "apiVersion": "v1",
    "data": {
        ".dockerconfigjson": "kjhsadflkjhasdlfkhjasdlkfjhlasdkjhflaskdjhflkasjdhf….”
    },
    "kind": "Secret",
…
```

Getting the secret data with `kubectl` and `jsonpath`, you need to escape the period that is part of the filename:

```
kubectl get secret mysecret -n mynamespace -o jsonpath='{.data.\.dockerconfigjson}'
```