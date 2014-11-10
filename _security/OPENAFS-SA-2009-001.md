---
id: 2009-001
cve: CVE-2009-1251
title: Network based buffer overflow attack against Unix cache manager
issued: 6-Apr-2009
updated: 6-Apr-2009
severity: Medium
affected: OpenAFS 1.0-1.4.8, OpenAFS 1.5.0-1.5.58
---

AFS's XDR data marshalling language permits the construction of arrays
with a size constrained by the interface definition. The XDR decoding
language will accept data from the server up to this maximum size, which
in some cases is stored into a buffer allocated by the client. In
several locations, the AFS client assumes that the server will never
return more data than requested, and so allocates a buffer smaller than
this maximum size. Whilst this causes no problems when communicating
with valid servers, an attacker can return more data than expected, and
overflow the client's buffer.

There are no known publicly-available exploits for this vulnerability at
this time.


