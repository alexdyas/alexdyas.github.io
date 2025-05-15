---
title: "vim - Remove carriage returns on save"
date: 2025-05-15T09:23:38-04:00
categories:
  - technical
tags:
  - vim
---
I've been copying and pasting a lot from Windows sessions into vim recently, and often I get carriage returns copied with the text. I save all my files in vim in 'Linux' mode, ie just the line feed.

This small function will strip all carriage return characters out of the file on save:
```
" Remove any carriage return (^M) characters that may have crept in
" Inspiration - https://stackoverflow.com/q/7495932/4046442
function TrimCarriageReturns()
  let l:save = winsaveview()
  keeppatterns %s/\r\+$//e
  call winrestview(l:save)
endfun
autocmd BufWritePre * call TrimCarriageReturns()
```
Just add it to your `.vimrc`.
