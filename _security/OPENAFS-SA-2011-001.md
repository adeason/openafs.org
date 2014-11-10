---
id: 2011-001
cve: CVE-2011-0430
title:  Denial of service attack against Rx server processes
issued: 23-Feb-2011
updated: 23-Feb-2011
severity: High
affected: OpenAFS servers versions 1.2.8 - 1.4.12.1, 1.5.0-1.5.74 for all platforms
---

An attacker with control of a client, or the ability to forge RX
packets, can crash a server of affected hosts. This vulnerability is
being tracked as CVE-2011-0430.

Currently the advisory erroneously states 1.4.14 is vulnerable.

CVE-2011-0431, while correctly describing 1.4.14 as containing the fix
for this issue, describes in its summary the release as broken. It is
not. We recommend sites upgrade to 1.4.14; However, the impact of the
issue is limited to a denial of service attack by a user with the
ability to affect a lock of AFS though the client on a host.
