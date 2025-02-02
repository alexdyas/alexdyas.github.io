---
title: "vim macro to validate Jenkinsfile against remote Jenkins server"
date: 2025-02-02T13:06:38-04:00
categories:
  - technical
tags:
  - vim
  - groovy
  - pipeline
  - jenkins
---
I've been doing a lot of Jenkins pipeline work recently. The development cycle is a bit laborious, code, git commit, re-run the pipeline in Jenkins, find out I missed off a bracket, GOTO 10.

I've been experiementing with Groovy/Jenkins pipeline linters, but they are scant and don't seem to be that useful.

I found out that Jenkins itself has a couple of development related APIs, one of which will validate a Jenkinsfile and report any issues. So I wrote a vim macro to do this with the current buffer. Saves a lot of time.

```
let @j = ":w ! curl --silent --insecure --request POST --user '<Jenkins username>:<api token>' --form 'jenkinsfile=<-' 'https://<Jenkins url>/jenkins/pipeline-model-converter/validate'"
```

Typically you put this macro in your `.vimrc`.

Replace `<Jenkins username>`, `<api token>` and `<Jenkins url>` with your own values. You _may_ need to remove `/jenkins/` from the URL depending on how you're exposing the app on HTTP.

The Jenkinsfile is read from `stdin`, see the `-` in the `--form` parameter. You can change this to a file in the filesystem if that suits you better.

My Jenkins server runs on a self generated TLS cert, hence the curl `--insecure`, remove this as necessary.

This has been written and tested for vim running on Linux, but it _should_ work with little modification under Windows/Powershell.
