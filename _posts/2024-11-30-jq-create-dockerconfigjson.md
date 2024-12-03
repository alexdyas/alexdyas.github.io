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
Linux, bash style :
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
Powershell for those of us who are forced to (minus the email address):
```
$REGISTRY="theregistry"
$USER="eddie"
$PASSWORD="mysup3rp4ssw0rd"
jq --null-input --arg registry "$REGISTRY" `
                --arg encodedcredentials $([Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes("${USER}:${PASSWORD}"))) `
                '{"auths": { ($registry): {"auth": $encodedcredentials}}}' > .dockerconfigjson
```
Beware that the file produced in Powershell is subject to Windows' bizarre encoding rules (UTF16, BOM etc). Here is a general use snippet that can sanitise the file for use elsewhere:
```
$MyRawString = Get-Content -Raw $pathtofile
$Utf8NoBomEncoding = New-Object System.Text.UTF8Encoding $False
[System.IO.File]::WriteAllLines($pathtofile, $MyRawString, $Utf8NoBomEncoding)
 ```
