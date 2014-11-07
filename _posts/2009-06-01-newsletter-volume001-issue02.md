---
title: OpenAFS Newsletter, Issue 2, June 2009
layout: page
category: newsletter
permalink: /newsletter/newsletter-2009-06-volume001-issue02.html
---

# OpenAFS Newsletter, Issue 2, June 2009

Yay! This is the second issue of the OpenAFS newsletter. The newsletter
summarizes what is happening in the OpenAFS community. This issue has
coverage of the workshop.

As always, volunteers, patches, bug reports, or any other type of help is
greatly appreciated.

Feedback on this newsletter is welcome. The goal is to summarize the
various development efforts and news of OpenAFS for the community. Please
let Jason Edgecombe <jason@rampaginggeek.com> know what you would like to
see out of this newsletter.

The current and past issues of this newsletter are available at
[http://www.openafs.org/newsletter/](http://www.openafs.org/newsletter/)

## General OpenAFS Progress

OpenAFS 1.4.11rc1 was released on June, 11, 2009. It's expected to be the
last release from CVS. A transition to git will be made and 1.5.x releases
will come from that, with the current CVS HEAD becoming the starting point
for the next 1.5.x release. Tools will be needed and are being developed
to work with git. We obviously seek people to help us with git (and
gerrit) tools, the latter of which requires Java expertise.  Many build
system changes are in place in the new 1.5.x tree, most for the better.

Testers are wanted. Reports of success or failure of the release candidate
should be sent to openafs.info@openafs.org.

OpenAFS 1.5.60 was released on May 31, 2009. Source and binaries are
available from [http://www.openafs.org/release/openafs-1.5.60.html](http://www.openafs.org/release/openafs-1.5.60.html)

The 1.5 branch is now dead. In preparation for the conversion to git, the
CVS HEAD was purged of anything that is not on 1.5, and the 1.5 and HEAD
branches were then synchronized. 1.5.61 will be cut from git once the head
is officially converted.

## Issues to look out for

Known issues in 1.4.10:

- A infrequent panic in the Linux VFS layer, which is difficult to reproduce.
- Data can be lost when a mapped file is much larger than the cache and
the file is written to after a close call.
- fileserver host list can be corrupted.
- Volumes can go offline during release
- Memory corruption when CellServDB contains more than 8 DB servers:

In Windows OpenAFS clients, iTunes can cause issues on 32bit Windows with
cache sizes larger then 500MB

Ref: Bug\# 124917
[http://rt.central.org/rt/Ticket/Display.html?id=124917&user=guest&pass-guest](http://rt.central.org/rt/Ticket/Display.html?id=124917&user=guest&pass-guest)

## Events

The Sixth Annual International AFS & Kerberos Best Practices Workshop was
held at Stanford University on June 1-5, 2009.

Ref: [http://workshop.openafs.org/afsbpw09/index.html](http://workshop.openafs.org/afsbpw09/index.html)

Despite a slightly smaller than usual attendance, OpenAFS administrators
and developers from a half dozen countries gathered at Stanford University
the first week in June for the sixth annual AFS & Kerberos Best Practices
Workshop.  As always, there were full-day classes in the use and best
practices of OpenAFS and Kerberos. Social activities included a fantastic
evening at the Computer History Museum and a BBQ dinner.  (Organizer
Derrick Brashear commented, "No blows were exchanged."  However, there was
much beer consumed.)

Great talks over two and a half days ranged from status reports and
updates on existing software to new toys, plus a repeat of last-year's
favorite, the troubleshooting panel.  Keynotes were given by Roland
Dowdeswell, talking about how a hypothetical multi-national financial firm
could use Kerberos in their world-wide infrastructure, and Jim Morris,
talking about the origins of what's now called AFS.  Slides from most
talks are available from the website ([http://workshop.openafs.org/](http://workshop.openafs.org/)).

Plans are already underway for the seventh Workshop, to be held May 24-28,
2010, at the University of Illinois at Urbana-Champaign.  We hope to see
you there.

## Projects

### Disconnected AFS support

Project Contacts:

- Simon Wilkinson <sxw@inf.ed.ac.uk>
- Dragos Tatulea <dragos.tatulea@gmail.com>

There have been no code changes since the last newsletter, although a
number of people continue to test the code. Please consider trying it out,
and share any experiences, good or bad. --Simon

There was no progress on my side. -- Dragos

### Security Releases

Security Officer:

- Simon Wilkinson <sxw@inf.ed.ac.uk>

No security issues since 1.4.9, 1.4.10, and 1.5.59 were released in April
2009.

### Fedora 11 and Linux 2.6.29 support

Project Contact:

- Simon Wilkinson <sxw@inf.ed.ac.uk>

Fedora 11 contains updates to the kernel and glibc which means that
OpenAFS 1.4.10 will neither build, nor run correctly. Prebuilt binary and
source RPMs containing the necessary patches are available from the
OpenAFS website, or simply install
[http://www.openafs.org/dl/openafs/1.4.10/openafs-repository-1.4.10-1.noarch.rpm](http://www.openafs.org/dl/openafs/1.4.10/openafs-repository-1.4.10-1.noarch.rpm)
and run 'yum install kmod-openafs openafs-client openafs-krb5' to install
an OpenAFS client.

If you wish to use an existing source tarball on Fedora 11, then you will
need to grab the deltas STABLE14-dprintf-rename-20090427 and
STABLE14-linux26-defer-cred-changing-20090511 from
[http://www.openafs.org/cgi-bin/wdelta](http://www.openafs.org/cgi-bin/wdelta) . The forthcoming 1.4.11 release
will contain both of these fixes.



### Git

Project Contact:

- Simon Wilkinson <sxw@inf.ed.ac.uk>

As has been heavily trailed, our change over from CVS to git for revision
control is almost upon us. Along with the new revision control system, we
also intend to make use of Google's gerrit code review tool. Gerrit will
provide a mechanism by which anyone in the community may submit, review
and comment upon forthcoming code changes. More details, and a sneak
preview of what is to come, are available in
[http://workshop.openafs.org/afsbpw09/talks/fri\_2/FromTinyAcorns.pdf](http://workshop.openafs.org/afsbpw09/talks/fri\_2/FromTinyAcorns.pdf)



### Binary Packaging

Project Contact:

- Simon Wilkinson <sxw@inf.ed.ac.uk>

With the arrival of Fedora 11, we say goodbye to Fedora 7. No new binary
builds for OpenAFS on Fedora 7 will be produced. This is a significantly
longer life than Fedora themselves provide for releases, but please do let
us know if this will cause problems. We currently automatically build RPMs
for all kernels on both ix86 and x86\_64 architectures for Fedora 8, Fedora
9, Fedora 10, Fedora 11, RHEL4 and RHEL5. All these packages are available
from the OpenAFS site.



### Newsletter

Project Contact:

- Jason Edgecombe <jason@rampaginggeek.com>

Progress is good. We have a second issue of the newsletter. I received
positive feedback from multiple people. Even one of our very active
contributors was surprised by how much was going on. This means that the
newsletter is serving a valuable purpose.

FYI, the newsletters are writen in POD format and stored alongside the
html files on the OpenAFS web site.

### Google Summer of Code 2009

OpenAFS received four slots for the 2009 Google Summer of Code.

Go to [http://socghop.appspot.com/org/home/google/gsoc2009/openafs](http://socghop.appspot.com/org/home/google/gsoc2009/openafs) for more
information about the GSoC projects.

Three of the projects are still active. Unfortunately, one student had to
back out.

The active student projects are:

#### OpenAFS Server Preference Based on Network Conditions

Student Developer: Jake Thebault-Spieker <summatusmentis@gmail.com>

Mentor: Derrick Brashear <shadow@gmail.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2009-April/016590.html](https://lists.openafs.org/pipermail/openafs-devel/2009-April/016590.html)

Current work in re-ordering the server preferences list takes into account
four things. Timeout time from the server, the round-trip time smoothed to
allow for short-term network hiccups, and the ratio between packets send and
the packets that needed to be resent. Work is still being done to decide how
the rank should be scaled for each of these variables, but this may get
pushed back until later, as the goal at this point is to get something
working. Things in the pipeline: How this affects initial rank after
boot-time, having the ranking be adjusted at some time interval, data
available to be inferred from the application layers, and the windows
client.

#### OpenAFS Management Console on Windows

Student Developer: Brant Gurganus <brant@gurganus.name>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2009-April/016591.html](https://lists.openafs.org/pipermail/openafs-devel/2009-April/016591.html)

I'm intending to make something available this week to make sure it's
installing fine and so forth. Last week I didn't really do much since I was
at the workshop, though it was nice to get a few questions about the
project.

I've probably done more work prior to Google Summer of Code's official
coding start time. In that time, I've researched how to tie the MMC
framework to Windows Forms, how to install and register an MMC snap-in
assembly, and simply looked into how the MMC framework is architected. I've
also looked at authoring an MSC console.

(Ed: This was received on June 7, 2009)

#### Implementing OpenAFS Features into RedHat's kafs Kernel Module

Student Developer: Wang Lei <wang840925@gmail.com>

Mentor: David Howells <dhowells@redhat.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2009-April/016595.html](https://lists.openafs.org/pipermail/openafs-devel/2009-April/016595.html)

In brief, we have finished three kAFS pioctl operations and have several
pioctls partially implemented.  I have read some of the OpenAFS documents
and I am becoming more familiar with kAFS and OpenAFS as the project
progresses.

With the help of my mentor, I have built an environment with one OpenAFS
server, one OpenAFS client and one kAFS client for development and
testing, and I have become familiar with the tools and development
environments, e.g. git and the formatting of kernel patches.  I have
learnt a lot about OpenAFS and dealing with open source projects, since
the Linux kAFS GSoC project started.  Next, I will work to accelerate the
completion of the rest of the pioctl operations.

Workshop presentation on kAFS:
[http://workshop.openafs.org/afsbpw09/thu\_2\_2.html](http://workshop.openafs.org/afsbpw09/thu\_2\_2.html)

### Kerberos v5 and Multiple Encryption Types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

Rxk5 patches against 1.5.60 and 1.4.10 are available for folks who would
like to try rxk5 in a test cell.  (A number of sites have offered to do
this.)  We will provide assistance as needed.  Marcus is working on a
draft protocol description to be published in afs3-standardization.  David
Howells is beginning an implementation of rxk5 in kAFS.

### \*BSD Support

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

Support for OpenBSD 4.5 was -really- added.  Build support for Freebsd 7.2
should appear shortly.  Fixes for at least one outstanding locking issue
on FreeBSD post 7.0 are being worked on.  A NetBSD cache manager port is
in progress.



### Extended Callback Information

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

I've created preliminary patches against openafs-devel-1.5.x for extended
callbacks and dependencies.  There's still some testing work for the
latest xcb changes, which added features over the previous milestone of
Aug. 2008.  I'll be publishing paths to patches and requests for review
over the next few weeks.

### Rx OSD integration & Raw Vicep Access in Clients

Project Contacts:

- Hartmut Reuter <reuter@rzg.mpg.de>
- Felix Frank <Felix.Frank@Desy.de>
- Christof Hanke <hanke@rzg.mpg.de>

RXOSD is an extension for OpenAFS to allow file data to be put into
dedicated "object storage", which is arbitrarly spread across servers.
Among other things, this allows read/write replication of data.  An
enhancement to the basic object storage paradigm is the ability to
transparently archive and restore data to and from HSM systems, similar to
the way MR-AFS used to facilitate.  Hartmut Reuter and Christof Hanke
(both RZG) and Felix Frank (DESY) work on the integration of this
extension of OpenAFS.  Patches submitted to the OpenAFS-Gatekeepers are
aimed to be small and amount to no more than one change each.  Everyone
interested in RXOSD and/or its integration into OpenAFS is cordially
invited to send an email to the integrators or the openafs-info mailing
list.

Ref: [https://lists.openafs.org/pipermail/openafs-devel/2009-May/016625.html](https://lists.openafs.org/pipermail/openafs-devel/2009-May/016625.html)

Concerning vicep-access I can tell you that this will come into OpenAFS
along with RXOSD because it's just another protocol supported by the
restructured client. However, it's ifdefed and configured separately so
that it could be used independently from RXOSD. But, of course, it makes
more sense to use it along with RXOSD because filesystems such as Lustre
and GPFS are good for large files, but slow for file creation and
deletion. So you would prefer to keep the small files in the fileserver's
local partition.

Workshop Presentation on vicep direct access:
[http://workshop.openafs.org/afsbpw09/thu\_2\_3.html](http://workshop.openafs.org/afsbpw09/thu\_2\_3.html)

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Thanks to contributions from Steven Jenkins and Mike Robinson of End
Point, our man page coverage is now essentially complete.  Every OpenAFS
command has a corresponding man page.

Thanks to Jeff Altman of Your File System, Inc., the old IBM architecture
and protocol documentation has been converted to header files with Doxygen
comments, allowing us to generate that documentation from editable source
and eventually better integrate it with the OpenAFS source.  This work was
funded under a SBIR grant.

The build system for the OpenAFS manuals has been overhauled to use more
current tools.  We now generate Windows Help files from the same source as
well as much better HTML and PDF output and get the version number for the
manual from the OpenAFS build system.

Thanks to edits by Jason Edgecombe and reviews by Jeffrey Altman and Russ
Allbery, chapter 1 of the Admin Guide has been updated to give warnings
about kaserver and include Kerberos 5.

## Resolved Tickets

Here is a list of tickets that have been resolved since May 1, 2009:

    ticket # state     created       title
      20947: resolved  Aug 18, 2005  Better cache partition checks in afsd
      23750: resolved  Nov 29, 2005  1.4.0 client crash
      60275: resolved  Apr 25, 2007  'make dest' fails to create man dir + manpages
     124130: resolved  Jan 14, 2009  Convert MR-AFS Residency Command to Rx OSD
     124359: resolved  Feb 13, 2009  Read-write volume corruption on openafs 1.5.x
     124514: resolved  Mar 19, 2009  OpenAFS 1.4.9 milestone
     124522: resolved  Mar 20, 2009  krb5 platform build defaults
     124551: resolved  Mar 28, 2009  [PATCH] encryption for PTS queries
     124552: resolved  Mar 28, 2009  [PATCH] Use $AFS_POST_INIT in Red Hat initscript if defined
     124563: resolved  Mar 31, 2009  Print unsigned values as such in rxdebug
     124569: resolved  Mar 31, 2009  fbsd 1.5.x sig_t old typo
     124581: resolved  Apr 02, 2009  stack overflow afs_GetDownD
     124627: resolved  Apr 15, 2009  Re: [OpenAFS-devel] Cache inconsistency in client 1.4.8 and above
     124671: resolved  Apr 22, 2009  Handling last store of dirty pages with memcache
     124681: resolved  Apr 23, 2009  patch for building on freebsd5.5
     124709: resolved  Apr 28, 2009  linux26 issue with pagsh.krb and Pag location in group list
     124715: resolved  Apr 30, 2009  minor path remods for src/tests; refactor of src/tests/afs-rmcell.sh to use new style
     124716: resolved  Apr 30, 2009  src/tests/OpenAFS/Dirpath.pm.in should be cvs remove'd
     124719: resolved  May 01, 2009  obsd 44 and 45
     124725: resolved  May 04, 2009  Please pull up XML documentation
     124737: resolved  May 05, 2009  periodic kernel panic - linux 2.6.29.1 / OpenAFS 1.4.10
     124742: resolved  May 06, 2009  AFS Explorer Shell IsPathInAFS broken for dead-end symlinks
     124770: resolved  May 12, 2009  1.5 build fix: mmap patch fallout
     124776: resolved  May 15, 2009  "vos partinfo" gives wrong output on windows.
     124787: resolved  May 18, 2009  AFS client 1.5.59 crashing with "Unhandled exception" on Windows 2003
     124788: resolved  May 18, 2009  compile_et man page
     124789: resolved  May 18, 2009  add copyauth man page
     124790: resolved  May 18, 2009  fs monitor man page
     124791: resolved  May 18, 2009  man page for restorevol
     124792: resolved  May 18, 2009  man page for rmtsysd
     124793: resolved  May 18, 2009  man page for vsys
     124794: resolved  May 18, 2009  fix CellServDB man page coveraged of -dynroot
     124799: resolved  May 18, 2009  fix .krb commands
     124800: resolved  May 18, 2009  New man pages for Windows installer
     124810: resolved  May 26, 2009  errno compile error in JAVA source
     124878: resolved  May 27, 2009  crash dump from Windows XP (32-bit) and 1.5.59 client
     124880: resolved  May 27, 2009  Add -rxmaxmtu parameter to afsd to help avoid VPN fragmentation of UDP packets
     124891: resolved  Jun 01, 2009  CellServDB parsing subject to buffer overflows
     124893: resolved  Jun 02, 2009  ptserver debug flag correction
     124894: resolved  Jun 02, 2009  ptprocs vicelog newlines and loglevels
     124898: resolved  Jun 03, 2009  src/aklog/klog.c uninitialized variable tofree
     124910: resolved  Jun 08, 2009  Windows: cm_cell_t lists not properly protected by cm_cellLock



## CVS statistics

The CVS statistics have been removed for now. The HEAD branch has been
synchronized with the 1.5 branch in preparation fo the git transition. The
1.5 branch is now dead.
