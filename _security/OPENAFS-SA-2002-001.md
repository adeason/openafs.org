---
id: 2002-001
title: xdr_array integer overflow
issued: 03-Aug-2002
updated: 03-Aug-2002
severity: High
affected: OpenAFS 1.0-1.2.5, OpenAFS 1.3.0-1.3.2
patch: xdr-updates-20020731.delta
sig: xdr-updates-20020731.delta.asc
---

There is an integer overflow bug in the SUNRPC-derived RPC library used
by OpenAFS that could be exploited to crash certain OpenAFS servers
(volserver, vlserver, ptserver, buserver) or to obtain unauthorized root
access to a host running one of these processes.

In addition, it is possible for a rogue server to attack certain
administrative clients (vos, pts, backup, butc, rxstat), but only if
certain RPC requests are made to the rogue server.

The OpenAFS fileserver and cache manager (client) are not vulnerable to
these attacks. No exploits are presently known to be available for this
vulnerability.
