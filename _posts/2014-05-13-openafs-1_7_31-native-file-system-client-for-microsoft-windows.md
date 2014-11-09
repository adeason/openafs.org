---
title: OpenAFS 1.7.31 - Native File System client for Microsoft Windows
layout: page
category: news
---


OpenAFS 1.7.31 is the next a series of OpenAFS clients for the Microsoft
Windows platform that is implemented as a native file system. 
Significant changes since 1.7.30:

-   Fixes a variety of rare errors that can lead to data corruption.
    -   one specific to synchronous file writes on Server 2012 R2.

-   File copies from readonly volumes could fail with a Media Protected
    error due to failure of the afs redirector to permit setting file
    position on a readonly file handle.
-   Prevent applications from unintentionally clearing the Reparse Point
    or Directory attribute when setting other attributes on files and
    directories.
-   If a file has the DOS readonly attribute set, deny all writes,
    truncations, and overwrites in the redirector and not the
    afsd\_service. Waiting for the afsd\_service to see the store
    operation is too late. The Windows cache manager has already
    accepted the data.
-   Fix a potential BSOD when afs redirector trace is enabled.
-   Improved support for applications that set the Last Modified
    Timestamp to -1 to indicate that the timestamp should not be
    modified.

**All users of previous 1.7 releases should upgrade.**

The 1.7 series is for Microsoft Windows only.

-   [Read the release announcement](/pipermail/openafs-announce/2014/000464.html)
-   [Go to the Microsoft Windows page](/windows.html)
-   [Go to the distribution page](/release/openafs-1.7.31.html)

