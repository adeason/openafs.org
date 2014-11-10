---
id: 2014-002
cve: CVE 2014-4044
title: Use of uninitialized memory in OpenAFS fileserver
issued: 12-Jun-2014
updated: 12-Jun-2014
severity: High
affected: OpenAFS fileserver version 1.6.8
patch: openafs-sa-2014-002.patch
cve: 2014-4044
---

The 1.6.8 release of the OpenAFS fileserver and dafileserver
processes introduced a security vulnerability in the host package
due to the use of uninitialized memory allocations from the process
heap.

An attacker with the ability to connect to an OpenAFS fileserver over
the network can trigger the use of uninitialized memory and, potentially,
execution of arbitrary code with the privileges of the fileserver
process.

