---
title: "kubernetes.config.config_exception.ConfigException: Invalid kube-config file"
date: 2023-08-26T15:42:38-04:00
categories:
  - technical
tags:
  - kubernetes
  - linux
---
```
kubernetes.config.config_exception.ConfigException: Invalid kube-config file. Expected object with name cluster-kjhsdfkjh in /home/charlieb/.kube/config/contexts list
```
Problem is that there are multiple contexts defined in the kube config file, but the `current-context` key is not set.

One solution is to set the key to an arbitrary context.
