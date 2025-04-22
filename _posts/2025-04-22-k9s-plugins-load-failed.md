---
title: "k9s Plugins load failed! error, one solution"
date: 2025-04-22T11:07:38-04:00
categories:
  - technical
tags:
  - k9s
  - kubernetes
---
The [k9s](https://k9scli.io) cli Kubernetes front-end is indispensable.

I came across a weird issue with it recently, the following error at startup : "Plugins load failed!". It turns out this message is rather misleading, at least in my case.

The problem was actually nothing to do with plugins, but instead stale cached information in `~/.local/share/k9s/clusters` after some changes to the remote clusters. Removing everything under this directory fixed the issue.

The k9s logs helped debug this. Find your log location:

```
k9s info
```
