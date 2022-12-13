---
title: "Linux - Pause and restart process"
date: 2022-12-13T14:11:38-04:00
categories:
  - technical
tags:
  - linux
---
Very useful trick, pause and restart a Linux process:

Pause the process :
```
kill -STOP <pid>
```
Restart it:
```
kill -CONT <pid>
```

I've found this useful testing web services for problematic behaviour, pause nginx, test the result, restart nginx.