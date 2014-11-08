---
title: pam-afs-session 1.0 released
layout: page
category: news
---

#### 2006-12-06 - pam-afs-session 1.0 released

pam-afs-session is a PAM module intended for use with a Kerberos v5 PAM
module to obtain an AFS PAG and AFS tokens on login. It puts every new
session in a PAG regardless of whether it was authenticated with
Kerberos and runs a configurable external program to obtain tokens. It
supports using Heimdal's libkafs for the AFS interface and falls back to
an internal Linux-only implementation if libkafs isn't available.

-   [Go to the announcement](/pipermail/openafs-announce/2006/000175.html)

