---
title: OpenAFS Security Advisory 2009-001
layout: page
category: news
---

#### 2009-04-06 - OpenAFS Security Advisory 2009-001

OpenAFS clients versions 1.0-1.4.8, 1.5.0-1.5.58 for all Unix platforms
except MacOS 10.4, 10.5.   An attacker with control of a fileserver, or
the ability to forge RX packets, can crash the cache manager, and hence
the kernel, of any Unix AFS client. It may be possible for an attacker
to cause the kernel to execute arbitrary code. This vulnerability is
being tracked as CVE-2009-1251.

-   [Go to the advisory](/security/OPENAFS-SA-2009-001.txt)

