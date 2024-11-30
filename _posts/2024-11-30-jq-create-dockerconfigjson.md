---
title: "JQ - Create .dockerconfigjson file"
date: 2024-11-30T11:42:38-04:00
categories:
  - technical
tags:
  - jq
  - coding
  - docker
  - kubernetes
  - linux
---
Use the `jq` tool to create a `.dockerconfigjson` file from existing details, including inline `base64` encoding.
```
export REGISTRY="theregistry"
export EMAILADDRESS=eddie@example.com
export USER="eddie"
export PASSWORD="mysup3rp4ssw0rd"
jq --null-input --arg registry "$REGISTRY"                                                         \
                --arg emailaddress "$EMAILADDRESS"                                                 \
                --arg encodedcredentials $(echo "$USER:$PASSWORD" |  base64)                       \
                '{"auths": { ($registry): {"email": $emailaddress, "auth": $encodedcredentials}}}'
```
This is formatted for a Linux type command line, but it wouldn't take much to convert it to PowerShell if you're so inclined.
