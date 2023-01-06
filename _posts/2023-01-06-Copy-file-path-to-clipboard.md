---
title: "Linux - Copy full path of a file to the clipboard"
date: 2023-01-06T10:38:38-04:00
categories:
  - technical
tags:
  - linux
  - zsh
---
I often find that I need to paste the full filesystem path to a given file somewhere, into a config file, onto the command line, etc. This small shell function does that:
```
function filecc() {
    if [ -z $1 ] || [ ! -f $1 ]
    then
        echo Give me a file you dummy
        return 1
    fi
    readlink -f $1 | tr -d "\n" | xclip
}
```
## Notes
- Only tested in zsh
- Depends on `xclip` which should be available from your distro's package archive. Otherwise - [https://github.com/astrand/xclip](https://github.com/astrand/xclip).
- Ideally added to you `.zshrc` file

## Example usage:
```
filecc somefile.txt
# Paste whereever needed
```
