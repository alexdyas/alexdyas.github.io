---
title: "Copy to system clipboard from Vim"
date: 2023-06-21T09:13:38-04:00
categories:
  - technical
tags:
  - vim
  - linux
---
As is often the case, I find something today that I wonder why I haven't looked for before. Copy from Vim to the system clipboard, ie not just inside Vim.

Basically just add the `*` register to your yanks, eg:
```
:23,67*y
```
From [https://stackoverflow.com/a/3961954/4046442](https://stackoverflow.com/a/3961954/4046442)
