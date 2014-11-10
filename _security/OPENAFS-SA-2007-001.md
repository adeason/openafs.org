---
id: 2007-001
title: setuid (privilege escalation) in OpenAFS Unix based clients
issued: 20-Mar-2007
updated: 20-Mar-2007
severity: Medium
affected: OpenAFS 1.0-1.4.3, OpenAFS 1.5.0-1.5.16
---

Because AFS cache managers do not use authenticated connections for
non-user-authenticated sessions, checks for cache coherency are done
over an unprotected connection if they are not being done for an
authenticated user. Because of this it is possible to spoof a false
status for files in the cache.

The AFS cache manager on platforms which offer privilege based on file
modes are vulnerable to such attacks.

There are no known publicly-available exploits for this vulnerability at
this time.


