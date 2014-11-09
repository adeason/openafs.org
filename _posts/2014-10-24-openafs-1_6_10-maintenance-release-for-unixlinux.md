---
title: OpenAFS 1.6.10 - Maintenance release for UNIX/Linux
layout: page
category: news
---


OpenAFS 1.6.10 is the next in the current series of OpenAFS stable
releases for UNIX/Linux systems. Significant changes on top of the
security fixes in 1.6.9 include:

-   The addition of volscan(8), a swiss army knife utility for gathering
    information about volume content efficiently on the fileserver
    hosting it.
-   The client now reports just under 2 TiB free space in /afs.
    Previously, it reported 9 GiB on most platforms, which could cause
    problems with software checking for sufficient free space before
    attempting to write files larger than that.
-   Client support for Linux kernels up to 3.16
-   Support for FreeBSD 9.3 and 10.1
-   Improved documentation, diagnostics and error messages
-   Dozens of bug fixes and other improvements

Note: There is a known issue affecting Linux clients, causing spurious
ENOENT errors on fakestat mounts, often showing up as getcwd() failures.
This problem had been fixed in the 1.6.8 release, but seems to be back
in 1.6.10 due to a change fixing another issue. Please find the details
in the later comments in the [bug
report](http://grand.central.org/rt/Ticket/Display.html?id=131780&user=guest&pass=guest).

For more information:

-   [Read the 1.6.10 release notes](/dl/openafs/1.6.10/RELNOTES-1.6.10)
-   [Go to the distribution page](/release/openafs-1.6.10.html)
-   [Read the release announcement](/pipermail/openafs-announce/2014/000472.html)

