---
id: 2009-002
cve: CVE-2009-1250
title: Denial of service attack against Linux cache manager
issued: 6-Apr-2009
updated: 6-Apr-2009
severity: Medium
affected: OpenAFS 1.0-1.4.8, OpenAFS 1.5.0-1.5.58
---

AFS may pass an error code obtained from the fileserver directly to the
Linux kernel, using a Linux mechanism that merges error codes and
pointers into a single value. However, this mechanism is unable to
distinguish certain error codes from pointers. When AFS returns a code
of this type to the kernel, the kernel treats it as a pointer and
attempts to dereference it. This causes a kernel panic, and results in a
denial of service attack.

There are no known publicly-available exploits for this vulnerability at
this time.
