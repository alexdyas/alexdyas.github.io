---
title: "Chrome Warning NET::ERR_SSL_OBSOLETE_VERSION"
date: 2020-07-23T14:03:00-04:00
categories:
  - technical
tags:
  - chrome
  - linux
  - osx
  - windows
---
Recent versions of Chrome now show warnings when visiting sites that still use legacy TLS versions. Although not recommended, this warning can be silenced:

* chrome://flags/#legacy-tls-enforced
* Change the setting for "Enforce deprecation of legacy TLS versions" from 'Default' to 'Disabled'
* Restart Chrome

A better, long term fix obs is to fix your web site.
