---
title: "git error - RPC failed"
date: 2023-11-01T16:16:38-04:00
categories:
  - technical
tags:
  - git
  - linux
---
I had this recently during an HTTP git clone :
```
error: RPC failed; curl 56 GnuTLS recv error (-110): The TLS connection was non-properly terminated.
```
It turns out that this was a premature connection closure by something along the HTTP chain between git command line and the remote repo. In my case it was a limit on the amount I could pull for a git clone.
Changing the protocol from http:// to ssh solved it, the limit was no longer applied.

If you have control over the HTTP chain you may want to check where the limit is imposed and open it up a bit as a better solution.
