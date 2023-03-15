---
title: "yq Quoting with variables in Powershell"
date: 2023-03-15T13:25:38-04:00
categories:
  - technical
tags:
  - yaml
  - yq
  - powershell
---
This took me far to long to figure out, so I thought I'd post it here in case someone else needs to keep their hair.
Using the `yq` tool under PowerShell, the quoting gets complex when adding variables to the query. This formula seems to work:
```
$somevariable="foo"
yq -M ".root[] | select(.name == \""$somevariable\"").bah[]" .\document.yaml
```
