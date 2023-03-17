---
title: "yq quoting with variables in Powershell"
date: 2023-03-15T13:25:38-04:00
categories:
  - technical
tags:
  - yaml
  - yq
  - powershell
---
This took me far to long to figure out, so I thought I'd post it here in case someone else wishes to keep all their hair.
Using the `yq` tool under PowerShell, the quoting gets complex when adding variables to the query. Either of these arcane formulas seem to work:
```
# Backslash + double quotes + double quotes
$somevariable="foo"
yq -M ".root[] | select(.name == \""$somevariable\"").bah[]" .\document.yaml
```
```
# Backslash + tick + double quotes
$somevariable="foo"
yq -M ".root[] | select(.name == \`"$somevariable\`").bah[]" .\document.yaml
```
Thanks to P for the second solution.
