---
title: "Python - object has no attribute LDAP"
date: 2024-08-26T21:25:38-04:00
categories:
  - technical
tags:
  - python
  - coding
---
Pulled my hair out over the following Python error while working with the LDAP package:
```
Traceback (most recent call last):
  File "/home/alex/source/ldap-auth.py", line 122, in <module>
    user_authenticated = user_ldap_authenticated(ldap_url, ldap_bind_dn, password)
  File "/home/alex/source/ldap-auth.py", line 86, in user_ldap_authenticated
    ldapobject = ldap.initialize(ldap_url)
AttributeError: 'list' object has no attribute 'initialize'
```
The error wasn't at all straight forward.
It turns out that I had a list object called `ldap`:
```
...
for ldap in ldap_urls:
  foo,bah = ldap
...
```
Apparently this clashed with the main LDAP object called `ldap` in the same namespace, therefore the error.

Moral - be careful with how you're declaring your object names and the namesapaces.
