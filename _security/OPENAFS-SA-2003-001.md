---
id: 2003-001
title: Cryptographic weakness in Kerberos v4
issued: 25-Mar-2003
updated: 25-Mar-2003
severity: High
affected: OpenAFS 1.0-1.2.8, OpenAFS 1.3.0-1.3.2
patches:
  - patch: kaserver-disable-krb4-crossrealm-20030317.delta
    sig: kaserver-disable-krb4-crossrealm-20030317.delta.asc
---

A cryptographic weakness in version 4 of the Kerberos protocol allows an
attacker to use a chosen-plaintext attack to impersonate any principal
in a realm. OpenAFS kaserver implements version 4 of the Kerberos
protocol, and therefore is vulnerable. An attacker that knows a shared
cross-realm key between any remote realm and the local realm can
impersonate any principal in the local realm to AFS database servers and
file servers in the local cell, and other services in the local realm.
An attacker that can create arbitrary principal names in a realm can
also impersonate any principal in that realm.

If your realm has no shared keys, and does not allow users to create
arbitrary principal names, you are not exposed to this vulnerability.

There are no known publicly-available exploits for this vulnerability at
this time.
