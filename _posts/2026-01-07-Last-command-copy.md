---
title: "Copy last command in shell history to clipboard"
date: 2026-01-07T16:00:38-04:00
categories:
  - technical
tags:
  - linux
  - zsh
  - bash
---
More command line clipboard functionality. This shell function copies the last line in your shell history to the clipboard.
```
# Copy last command from shell history into clipboard
function cl() {
    fc -ln | tail -1 | tr --delete "\n" | xclip -selection clipboard
}
```
