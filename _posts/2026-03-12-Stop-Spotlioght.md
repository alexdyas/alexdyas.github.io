---
title: "Stop MacOS Spotlight indexing external drives"
date: 2026-03-12T13:28:38-04:00
categories:
  - technical
tags:
  - apple
  - macos
  - finder
---
Caveat emptor - Some advanced stuff here, follow at your own risk.

I've been battling with MacOS writing all sorts of crap onto external drives, and having difficulties ejecting them because some unknown process has files open on the drive.

This seems to be a difinitive way of getting MacOS to ignore external drives in it's never ending quest to create as many files as possible:
```
touch /Volumes/<volume>/.metadata_never_index
```
Once you've done this you may also want to delete the `.Spotlight-V100` directory from the volume.
