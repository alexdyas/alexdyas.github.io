---
title: "Vim - Skeleton files"
date: 2022-01-20T14:18:00-04:00
categories:
  - technical
tags:
  - linux
  - vim
---
I've been looking for a way to quickly create 'skeleton' files of the text files I work on regularly, for instance Kubernetes yaml files.

This is a vim solution to the problem, which works for me as vim is what I'll be using in almost all cases to start editing the new file. It uses the `au BufNewFile` configuration in your `.vimrc` file.

Example, to create a new Kubernetes deployment file:

```
au BufNewFile deployment.yaml 0r ~/.skeletons/deployment.yaml
```

This relies on the skeleton file already being present, create that the way you want.

Once this is in place, just `vim deployment.yaml` in the directory where you are working. If the file doesn't already exist vim will open with the skeleton file already in the buffer. All you have to do is start editing, and save.
