---
title: "Namespace stuck in Terminating - Kubernetes"
date: 2021-12-14T14:03:00-04:00
categories:
  - technical
tags:
  - kubernetes
  - linux
  - jq
---
Occasionally you may find that having issued a `kubectl delete namespace yournamespace` command, the namespace gets stuck in Terminating state, and is never actually deleted.

Here is a one liner, using `jq` that will alter the namespace to allow kubernetes to remove it:

```
kubectl get namespace yournamespace -o json | jq 'del(.spec.finalizers[] | select(. == "kubernetes"))' | kubectl replace --raw "/api/v1/namespaces/yournamespace/finalize" -f -
```

Replace `yournamespace` for the namespace you want to delete (appears twice in the line).

Or wrap it in a shell function, I'll leave that as an exercise for you, dear reader.
