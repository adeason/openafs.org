---
title: OpenAFS Newsletter, Issue 5, September 2009
layout: page
---

# OpenAFS Newsletter, Issue 5, September 2009

Welcome to the fifth issue of the OpenAFS newsletter. This newsletter
summarizes what is happening in the OpenAFS community.

As always, volunteers, patches, bug reports, or any other type of help is
greatly appreciated.

Feedback on this newsletter is welcome. The goal is to summarize the
various development efforts and news of OpenAFS for the community. Please
let Jason Edgecombe <jason@rampaginggeek.com> know what you would like to
see out of this newsletter. Any news about AFS-related projects is welcome
and may be submitted to Jason for inclusion in the next newsletter.

The current and past issues of this newsletter are available at
[http://www.openafs.org/newsletter/](http://www.openafs.org/newsletter/)

## General OpenAFS Progress

OpenAFS 1.5.62 was released on August 28, 2009. Highlights of this release
include several critical bugfixes and support for Mac OS X Snow
Leopard. 1.4.11 is still the recommended release for all Unix platforms,
including Snow Leopard. Testing of the 1.5.62 version on Unix platforms is
encouraged.

Russ Allbery gave an update on the progress of a non-profit organization
for OpenAFS. The Elders have decided that there are multiple issues,
including on-going funding, that make the formation of a non-profit
problematic at this time. In the interim, the Elders have voted
unanimously to approach the Software Freedom Conservancy and request
membership. The Elders will move forward with forming a foundation once
the economy picks up. For more information and some important details,
read Russ' announcement at:
[http://lists.openafs.org/pipermail/openafs-announce/2009/000303.html](http://lists.openafs.org/pipermail/openafs-announce/2009/000303.html)

## Events

### AFS Hackathon

The School of Informatics at the University of Edinburgh will be hosting
an AFS Hackathon 22-24 September (immediately before the European AFS
Conference). All OpenAFS developers are welcome to attend - please see the
email to openafs-announce for details, and RSVP to sxw@inf.ed.ac.uk

### European AFS Meeting

The University Roma Tre will host the 2009 European AFS Meeting from
September 28-30. The European workshop is mainly a platform for system
administrators to exchange their knowledge and report use cases. Topics of
interest include related technologies like Kerberos or LDAP and all
supported operating systems.

For more details, go to [http://www.dia.uniroma3.it/~afscon09/](http://www.dia.uniroma3.it/~afscon09/)

### Annual Best Practices Workshop

Plans are already underway for the seventh Workshop, to be held May 24-28,
2010, at the University of Illinois at Urbana-Champaign.  We hope to see
you there.

## Projects

### \*BSD Support

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

I've been working on NetBSD client targeting master.  I've sent a number
of changes, most committed, preparing for this.  My plan is to have
something committed by the EU AFS Conference in Rome.

### Extended Callback Information

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

The dependencies have begun to merge on the master branch (MCAS and all
changes are merged, miniosi is in review, XCB changesets will follow).

### Kerberos v5 and Multiple Encryption Types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

Marcus is preparing a draft paper describing the protocol and
implementation details.  (I've read a draft.)  It is planned to be
published in the next week or so.  We began submitting split-out Rxk5
changesets, the gatekeepers want to put these on a work-in-process git
branch, more TBD.

\--Matt (Ed: Received Sept 4, 2009)

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Jason updated sections 3.2 through 3.4 of chapter 2 in the Admin
Guide. Information about cross-realm trusts and foreign PTS users was
included. The instructions for submitting entries to the public CellServDB
were updated. Some text about using Freelance and Dynamic Root modes to
find foreign cells was added.

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

Only one or two DAFS issues remain that we believe are critical: 124484
(volumes not salvaged on first access from volserver), and possibly 124487
(fileserver/salvageserver lock up). 124487 may already be fixed by a
recently-merged patch for 124486 (fileserver hangs on shutdown), so 124484
may be the only remaining critical issue.

All other issues beyond those are either performance issues or are
relatively minor. Once they are fixed, we consider DAFS to be
production-ready, lacking any other issues. We can't fix issues we don't
know about, though, so testing DAFS is greatly appreciated.  Even if it
may not appropriate for production in arbitrary critical environments
quite yet, DAFS is definitely usable in its current state if you want to
try it out.

If you are interested in trying out DAFS, Steven Jenkins has written up
how to get started with it here:
[http://blog.endpoint.com/2009/06/getting-started-with-demand-attach.html](http://blog.endpoint.com/2009/06/getting-started-with-demand-attach.html)

\--Andrew



### Userspace cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

I have a working userspace unix OpenAFS client implemented via FUSE, and
perl bindings to libuafs (via SWIG). Neither are as fully-featured as the
kernel cache manager yet, but they are sufficient for simple filesystem
access, and can be used to simulate multiple clients from a single
machine.

The code is not in the main repository yet, as I need to clean up some of
the libuafs modifications, and make it play nice with the other users of
libuafs. If you want to mess around with them, though, feel free to
contact me.



### Mac OS X OpenAFS Preference Pane

Project Contact:

- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

The work done on the preference pane was directed to clean the code for
deprecated API's and adjustment for Snow Leopard. NSMenuExtra is a private
API that was never supported and has been changed to a Background Only
Application (AFSBackgrounder) that uses NSStatusItem to show the OpenAFS
lock icon on the OS X menu bar. The AFSBackgrounder is also used to get a
token at login time.



### Google Summer of Code 2009

OpenAFS received four slots for the 2009 Google Summer of Code.

Go to [http://socghop.appspot.com/org/home/google/gsoc2009/openafs](http://socghop.appspot.com/org/home/google/gsoc2009/openafs) for more
information about the GSoC projects.

#### OpenAFS Management Console on Windows

Student Developer: Brant Gurganus <brant@gurganus.name>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2009-April/016591.html](https://lists.openafs.org/pipermail/openafs-devel/2009-April/016591.html)

Progress is rolling with the management console. It can be built with
nmake now for both 32-bit and 64-bit machines. It installs and runs.
Current tasks are polishing any install issues and bringing the console up
to full functionality. After talking with Jeff, there will also be some
redesigning of the user interface from the prototyped user interface to
have a less cluttered user interface and to better follow the MMC 3.0
Guidelines.

#### Google Projects without an update

The following Google Summer of Code projects did not give a status update:

- Implementing OpenAFS Features into RedHat's kafs Kernel Module
- OpenAFS Server Preference Based on Network Conditions



### Projects with no progress or no update

- Disconnected AFS support
- Pthreaded Ubik
- Rx OSD integration & Raw Vicep Access in Clients

## Resolved Tickets

Here is a list of tickets that have been resolved since August 1, 2009:

    ticket # state     created       title
     108199: resolved  Jul 21, 2008  Incomplete file transfer : Bug Report
     125211: resolved  Aug 12, 2009  OpenAFS 1.5.61 says invalid cell during install
     125217: resolved  Aug 13, 2009  OpenAFS configure script of the source RPM doen't handle INIT_WORK_HAS_DATA macro correctly on SLES-11
     125220: resolved  Aug 13, 2009  Bug Report
     125298: resolved  Aug 28, 2009  find_task_by_vpid removed in kernel 2.6.31
     125301: resolved  Aug 28, 2009  OpenAFS 1.5.62 version discrepancy
