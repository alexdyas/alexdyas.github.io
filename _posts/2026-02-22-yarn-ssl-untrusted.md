---
title: "Force Yarn to ignore SSL ceritifcate issues"
date: 2026-02-07T14:06:38-04:00
categories:
  - technical
tags:
  - linux
  - ssl
  - yarn
  - traefik
  - kubernetes
---
I'm just putting this here as it wasn't an immediately clear fix. I was building the Traefik container image from source.

Error:
```
YN0001: │ RequestError: self-signed certificate in certificate chain
```

Fix:

In `~/.yarnrc.yaml` or equivaqlent:

```
enableStrictSsl: false
```

Caveat - Be aware that this will prevent errors/warnings about unsafe TLS certificates, blah blah. If you're already at this point you take full responsibility for what you're doing.
