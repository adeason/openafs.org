---
id: 2013-001
title: Buffer overflows in OpenAFS fileserver
issued: 27-Feb-2013
updated: 27-Feb-2013
severity: High
affected: OpenAFS servers before version 1.6.2
patch: openafs-sa-2013-001.patch
---

* openafs-sa-2013-001-1_4_14_1.patch (for 1.4.14.1)


By carefully crafting an ACL entry an attacker may overflow fixed length
buffers within the OpenAFS fileserver, crashing the fileserver, and
potentially permitting the execution of arbitrary code. To perform the
exploit, the attacker must already have permissions to create ACLs on
the fileserver in question. This vulnerability is being tracked as
CVE-2013-1794.

