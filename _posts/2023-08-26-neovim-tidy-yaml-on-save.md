---
title: "NeoVim - Tidy YAML on save"
date: 2023-08-26T14:52:38-04:00
categories:
  - technical
tags:
  - neovim
  - linux
---
I like my YAML files to be tidied and sorted (see [Tidying YAML](https://www.alexdyas.com/technical/YAML-tidy/)). What would be great is if your editor, currently NeoVim for me, would do this automatically on save:
```
-- Sort YAML files on buffer write
vim.cmd("autocmd BufWritePre *.yaml :%! yq --prettyPrint --indent 2 'sort_keys(..)' -")
```
