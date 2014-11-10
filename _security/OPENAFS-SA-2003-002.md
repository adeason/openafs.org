---
id: 2003-002
title: Rx connection hijacking vulnerability
issued: 18-Apr-2003
updated: 18-Apr-2003
severity: Medium
affected: OpenAFS 1.0-1.2.7, OpenAFS 1.3.0-1.3.2
patch: openafs-sa-2003-002.patch
sig: openafs-sa-2003-002.patch.asc
---

There is a bug in the Rx RPC protocol, used by AFS, which can be
exploited by an attacker to hijack arbitrary Rx connections. This allows
the attacker to mount a denial of service attack by breaking arbitrary
Rx connections. Additionally, unless encryption is used, such as rxkad
mode crypt ("fs setcrypt on") and the user accessing files is
authenticated (has valid tokens), the attacker can observe and modify
the data being transferred.

The AFS cache manager and other AFS administrative clients (such as pts,
fs, vos, etc) are vulnerable to these attacks. Vulnerable AFS servers
allow connections from AFS cache managers to be hijacked, but not
connections from the other AFS administrative clients (such as pts, fs,
vos, etc).

There are no known publicly-available exploits for this vulnerability at
this time.

