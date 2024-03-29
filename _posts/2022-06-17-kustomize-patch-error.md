---
title: "Kustomize patch error - 'unable to parse SM or JSON patch from'"
date: 2022-06-17 16:00:00
categories:
  - technical
tags:
  - kubernetes
  - kustomize
---
I was struggling with this rather cryptic Kustomize error recently:
```
Error: trouble configuring builtin PatchTransformer with config: `
path: resource_limits_patch.yaml
target:
  kind: Deployment
  name: nginx
`: unable to parse SM or JSON patch from [apiVersion: apps/v1
<...>
```
The patch in question:
```
apiVersion: apps/v1
kind: Deployment
metadata:
  namespace: mynamespace
spec:
  template:
    spec:
      containers:
        - name: nginx
          resources:
            requests:
              cpu: 400m
              memory: 1250Mi
            limits:
              cpu: 400m
              memory: 1250Mi
```
Turns out, you MUST have a `name` key in the patch's `metadata` section. Doesn't matter what the value is.

Fixed patch:
```
apiVersion: apps/v1
kind: Deployment
metadata:
  namespace: mynamespace
  name: required-for-kustomize-but-not-used
spec:
  template:
    spec:
      containers:
        - name: nginx
          resources:
            requests:
              cpu: 400m
              memory: 1250Mi
            limits:
              cpu: 400m
              memory: 1250Mi
```
Reference - [https://stackoverflow.com/questions/72492756/kubernetes-patch-multiple-resources-not-working](https://stackoverflow.com/questions/72492756/kubernetes-patch-multiple-resources-not-working)
