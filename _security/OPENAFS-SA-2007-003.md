---
id: 2007-003
title: denial of service in OpenAFS fileserver
issued: 20-Dec-2007
updated: 21-Dec-2007
severity: Medium
affected: OpenAFS 1.3.50-1.4.5, OpenAFS 1.5.0-1.5.27
---

The AFS fileserver tracks client callbacks on files via a series of
linked lists internally. When a client acquires a new callback or gives
up an old one, these lists must be updated. Beginning in 1.3.50, a bulk
disposal mechanism was added. Due to a failure to hold a lock, unsafe
access to data could result in a crash. No data compromise is known.

There are no known publicly-available exploits for this vulnerability at
this time.
