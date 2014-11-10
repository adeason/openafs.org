---
id: 2013-002
cve: CVE-2013-1795
title: Buffer overflow in OpenAFS ptserver
issued: 27-Feb-2013
updated: 27-Feb-2013
severity: High
affected: OpenAFS servers before version 1.6.2
patches:
  - patch: openafs-sa-2013-002.patch
  - patch: openafs-sa-2013-002-1_4_14_1.patch
    vers: 1.4.14.1
---

An attacker can crash an OpenAFS ptserver by sending an IdToName RPC
with a large payload. This vulnerability is being tracked as
CVE-2013-1795.
