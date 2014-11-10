---
id: 2014-001
cve: CVE-2014-0159
title: Denial of service attack against OpenAFS fileserver processes
issued: 9-Apr-2014
updated: 9-Apr-2013
severity: High
affected: OpenAFS server versions 1.4.8 through 1.6.6. Also 1.6.8pre1.
patches:
  - patch: openafs-sa-2014-001.patch
---

An attacker with the ability to connect to an OpenAFS fileserver can
trigger a buffer overflow, crashing the server.
