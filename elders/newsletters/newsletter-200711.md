---
title: OpenAFS Newsletter – November 2007
---


*An Update to the OpenAFS Community compiled by the Advisory Council*

Introduction
============

The OpenAFS Newsletter is intended to be a regular communiqué from the
OpenAFS Elders to the community of OpenAFS administrators and end
users.  In these newsletters the Elders will summarize the activities of
the OpenAFS community, the progress that has been achieved in OpenAFS
development, and outline the road map of future development that could
be accomplished with the availability of sufficient resources. It is
hoped that these newsletters will strengthen the community and foster
additional dialogues and participation.

Council of Elders Monthly Meeting
=================================

The OpenAFS Advisory Council met on November 13.  The following topics
were discussed in the meeting:  Development, AFS & Kerberos Best
Practices Workshop, Documentation, and OpenAFS communications.  Minutes
of the meeting can be found at: 
[http://www.openafs.org/pages/elders/minutes-20071113.html](http://www.openafs.org/pages/elders/minutes-20071113.html).\

**Council of Elders - Member Resignation** 

Warren Yenson has resigned from the OpenAFS Council of Elders because he
is no longer actively involved in OpenAFS development or with OpenAFS
customers.   Warren had been closely involved with OpenAFS in his
position at Morgan Stanley, but he has not been involved with AFS in his
position at Google.  The Council of Elders would like to thank Warren
for his contributions to OpenAFS and wish him well in the future.

OpenAFS Development Update
==========================

Below is a summary of recent OpenAFS development activity.

UNIX/Linux Servers
-   1.4.5 packages have been uploaded to Debian. 
-   The 1.4 backport of the Kerberos multiple-realm patch will be pulled
    into the Debian packages so that it can be more broadly tested.
-   There will be additional work to improve Documentation, including
    Russ committing pending contributions from Jason Edgecomb. 
-   Stanford and Sine Nomine are persuing a file server problem that's
    causing periodic segfaults due to an apparent free list corruption. 
    Once this bug is identified and fixed, it should be included in a
    1.4.6 release.
-   Russ is going to try to get some resources at Stanford to start
    testing the demand-attach fileservers.

UNIX/Linux Clients
-   OpenAFS 1.4.5 was released and includes support for Leopard, Solaris
    10-update 4, and new Linux support.
-   Bug fixes proposed for 1.4.6 include verifying
    viced-accurately-track-file-callbacks-20071112 fixes the bug seen
    with CBFree/FEFree corruption, viced-missing-lock-20071109,
    libafsrpc-makefile-fix-20071110 for RPMS,
    linux-nsec-timestamp-zero-20071106, linux-splice-support-2007-1106
    and solaris-nevada-update-2007-1101,
    linux-afs-unlinked-file-dentry-flagging-20071031, and various Mac
    and RPM packaging files.
-   Pending work includes module unload cleanup, afs\_HashOutDCache
    panic, and an Rx error. 
-   Longer term, there is work planned to stabilize 1.5 so that we are
    able to put out 1.6 series releases.  There has also been discussion
    with the HePiX community regarding a timeout issue which limits AFS
    throughput.  Derrick is working with Rainer Toebbicke regarding his
    Rx test tool to resolve this matter.  He is also working with
    Hartmut Reuter to integrate his AFS OSD code.  However, the timing
    of this work depends on the availability of resources.

Windows Clients

There have been three OpenAFS for Windows releases since the last Elders
meeting: OpenAFS [1.5.25
(9/20/07)](https://lists.openafs.org/pipermail/openafs-announce/2007/000206.html),
[1.5.26
(10/23/07)](https://lists.openafs.org/pipermail/openafs-announce/2007/000212.html),
[1.5.27
(11/7/07)](https://lists.openafs.org/pipermail/openafs-announce/2007/000215.html).

The following work is changes have been made post 1.5.27::
-   Optimization of the performance of the Windows cache manager.
-   A new option which permits .readonly callbacks to be automatically
    renewed prior to expiration.  This option can reduce load on
    .readonly volumes over long periods of time. However, it is an
    optional feature since it will resulte in a single FetchStgatus
    request being sent per .readonly volume whether or not the client is
    actively using that volume.

Future work plans for OpenAFS Windows Development include:
-   OpenAFS Redirector work (in progress)
-   OpenAFS File System Filter Driver that will permit \\\\AFS to be
    used without requiring the presence of the Microsoft Loopback
    Adapter.
-   Implementation of Extended Attributes by storing data in the Apple
    Double Files as described in RFC 1740.

In-depth Focus on Ongoing Development:  Documentation
-----------------------------------------------------

Work is slowly proceeding on improving the OpenAFS documentation and
manuals, but there's a lot of work to do, and we can always use more
volunteers.

The OpenAFS Admin Reference Manual has been converted to manual pages
(written in POD), and significant work has been done to update them and
write additional entries for new commands.  The current manual pages can
be found in OpenAFS CVS in the doc/man-pages directory and have been
shipped with all recent OpenAFS releases.  doc/man-pages/README contains
a list of work that still needs to be done, and all of the manual pages
would benefit from further review and editing.  Additionally, we need a
volunteer to work on automating the process of converting these manual
pages to HTML and hooking that into the process for generating the
OpenAFS web site. 

The other OpenAFS manuals have been converted to DocBook, but now need
cleanup, updates for all the changes since OpenAFS 1.0, removal of
obsolete information, and removal of additional IBM-specific sections,
language, and assumptions.  The Quick Start Guide is our first priority,
but work on any of the manuals is welcome.

The protocol documentation which we received from IBM in PDF format has
been converted to Microsoft Word .DOC files.  These documents need to be
further converted to DocBook, be reformatted, and have the Table of
Contents and Index sections rebuilt using the appropriate tags. After
this work is complete, the OpenAFS developers can work to update the
documentation to match the current implementation.

Work on OpenAFS's documentation is coordinated on the
[openafs-doc@openafs.org](mailto:openafs-doc@openafs.org) mailing list. 
Before starting work on a large project, please mention the work on that
mailing list so that we can avoid duplicating effort.

AFS & Kerberos Best Practices Workshop
--------------------------------------

The 2008 Workshop will be held at NJIT in Newark, NJ, the week of May
19-23, 2008.   There is a block of rooms available at Newark Penn
Station Hilton.  For more information on the workshop, please visit:
[http://workshop.openafs.org/afsbpw08/](http://workshop.openafs.org/afsbpw08/).
  
OpenAFS Council of Elders – Next Meeting

December 11, 2007


