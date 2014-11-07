---
title: OpenAFS 1.6.8 - Maintenance release for UNIX/Linux
layout: page
category: news
---

#### 2014-05-21 - OpenAFS 1.6.8 - Maintenance release for UNIX/Linux

OpenAFS 1.6.8 is the next in the current series of OpenAFS stable
releases for UNIX/Linux systems. Significant changes on top of the
security fixes in 1.6.7 include:

-   **The default fileserver sync behavior changes from "delayed" to
    "onclose".** This means that explicit syncing only happens when a
    volume is detached. This was the recommended option in recent stable
    releases, and it's believed to improve data integrity.
-   **When a client is shut down, it will give up its callbacks.** The
    Windows client has been doing this since 2007. Note that older
    fileservers (1.3.50 to 1.4.5 and 1.5.0 to 1.5.27) had a bug in the
    implementation of the relevant RPC that could cause crashes or other
    undefined behavior when this happens.
-   Improved documentation, diagnostics and error messages
-   Dozens of bug fixes and other improvements

For more information:

-   [Read the 1.6.8 release notes](/dl/openafs/1.6.8/RELNOTES-1.6.8)
-   [Go to the distribution page](/release/openafs-1.6.8.html)
-   [Read the release announcement](/pipermail/openafs-announce/2014/000467.html)

