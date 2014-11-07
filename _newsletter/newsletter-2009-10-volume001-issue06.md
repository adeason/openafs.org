---
title: OpenAFS Newsletter, Issue 6, October 2009
layout: page
---

# OpenAFS Newsletter, Issue 6, October 2009

Welcome to the sixth issue of the OpenAFS newsletter. This newsletter
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

There were three OpenAFS 1.5.x releases since the last newsletter. OpenAFS
1.5.65 was released on October 6, 2009. Highlights of this release include
several important bug fixes. All of the existing compile-time warnings have
been silenced, but they may be re-enabled with a ./configure option. This
was done to help prevent new warnings from creeping into the code. The
configure option can be used for those developers trying to clean up the
older warnings.

There was some discussion of allowing one or two hyphens to specify
command-line options. Michael Meffie supplied a patch to allow this and it
was approved. This feature will be included in a future release.

The OpenAFS web site is now using git for source control, and the older
CVS repository for the web site has been disabled.

Jeff Altman and Derrick Brashear gave a status update on OpenAFS progress
at the European AFS Meeting. Your File System Inc. has committed to
working on several improvements to OpenAFS and contributing them back to
OpenAFS. There is more information in the Jeff & Derrick's slides at
[http://www.dia.uniroma3.it/~afscon09/docs/part1.pdf](http://www.dia.uniroma3.it/~afscon09/docs/part1.pdf) and
[http://www.dia.uniroma3.it/~afscon09/docs/part3.pdf](http://www.dia.uniroma3.it/~afscon09/docs/part3.pdf). There is an
updated road map at [http://www.openafs.org/roadmap.html](http://www.openafs.org/roadmap.html).

There is some discussion about getting rid of the AFS lock icon in the
Windows system tray for future versions of AFS. A few people value the
clear indication that the lock icon gives for being logged in. Please join
in the discussion on the openafs-info mailing list.

## Events

### AFS Hackathon

On September 22-24, an AFS Hackathon was held at The School of Informatics
at the University of Edinburgh. Simon Wilkinson posted a summary on the
openafs-devel and afs3-standardization mailing lists. The summary is
available at
[https://lists.openafs.org/pipermail/openafs-devel/2009-October/017096.html](https://lists.openafs.org/pipermail/openafs-devel/2009-October/017096.html)

The jabber chat logs of the Hackathon are available at
[http://conference.openafs.org/hackathon@conference.openafs.org/](http://conference.openafs.org/hackathon@conference.openafs.org/)

### European AFS Meeting

The Second Annual European AFS Workshop was held at Roma Tre University,
Italy, on September 28-30, 2009.

Ref: [http://www.dia.uniroma3.it/~afscon09/](http://www.dia.uniroma3.it/~afscon09/)

The attendance of the event remained stable at about 50 people from 6
countries, including two colleagues from Pilsen, Czech Republic. There was
an introductory day, a day dealing with advanced topics, and a final
half-day dedicated mainly to site reports. Social activities consisted of
a sponsored bus tour through Rome (Sun Microsystems), a sponsored visit to
St Paul's Basilica (DIA Roma Tre), the second largest cathedral after
St. Peter's, and two dinners in typical Roman restaurants, where the
attendants proudly consumed more wine than water.

Thanks to INFN, this year Jeffrey Altman and Derrick Brashear were again
the invited guests, and Hartmut Reuter provided a detailed tutorial on the
combination of AFS with object storage. The slides of all talks are
available on the website, and the event was transmitted in real-time
streaming, provided by ENEA. Recordings can be freely accessed over the
web.

This workshop was a joint effort of the Department of Informatics and
Automation from Roma Tre University, and three research institutions:
CASPUR, ENEA, INFN. Two industrial sponsors contributed: E4 company and
Sun Microsystems.

The next year's conference will be hosted either in Pilsen, Czech
Republic, or Hamburg, Germany.

\--Wolfgang Alexander Gehrke

### Annual Best Practices Workshop

Plans are already underway for the seventh Workshop, to be held May 24-28,
2010, at the University of Illinois at Urbana-Champaign.  We hope to see
you there.

## Projects

### AFS Protocol Standardization

There is some progress in afs3-standardization.  There are new protocol
descriptions for rxgk, rxk5, and Rx/OSD that were published in advance of
the hackathon, I just submitted a proposal for SRV records for AFS, and I
think there was an extended callback draft published as well.

\--Russ Allbery

Current active protocol drafts:

- AFS Callback Extensions

[http://www.ietf.org/id/draft-benjamin-extendedcallbackinfo-00.txt](http://www.ietf.org/id/draft-benjamin-extendedcallbackinfo-00.txt)

- DNS SRV Resource Records for AFS

[http://www.ietf.org/id/draft-allbery-afs-srv-records-01.txt](http://www.ietf.org/id/draft-allbery-afs-srv-records-01.txt)

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

A fix for 124484 (volumes not salvaged on first access from volserver) is
nearing completion, and should see public review soon. 124484 may be the
last critical DAFS bug; we are currently trying to reproduce earlier-seen
problems with the newest patches to see if they still exist.

We are also working on improved developer documentation for DAFS, as it
has been noted that a lack of a broad overview for the changes DAFS brings
(specifically in the volume package) has made contributions and review
prohibitively difficult for newcomers to DAFS code.

\--Andrew

### Mac OS X OpenAFS Preference Pane

Project Contact:

- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

The MacOSX Preference Pane has been updated to use the launchd start
mode. StartupItems has been replaced by the launchd technology. The
behavior of the OpenAFS service at start-up can be managed from the
Preference Pane. Both the launchd daemon and the preference pane use the
/Library/OpenAFS/Tools/root.client/usr/vice/etc/afs.rc file to start or
stop OpenAFS.

### Extended Callback Information

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

XCB was discussed at Edinburgh, and at the request of the group, a new I-D
draft was published, removing mention of asynchronous delivery.  That
feature will be revisited in future.  The XCB draft is under last call,
and interested parties are requested to review the draft and send comments
or indication of "support" or "not support" to the afs3-standardization
list.

A draft document of the protocol changes is available at
[http://www.ietf.org/id/draft-benjamin-extendedcallbackinfo-00.txt](http://www.ietf.org/id/draft-benjamin-extendedcallbackinfo-00.txt).

### \*BSD Support

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

I am gradually sending changes indirectly related to NetBSD cache manager
port.  The most recent are related to AFS\_PROC and AFS\_UCRED.

### Kerberos v5 and multiple encryption types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

Marcus have a presentation at the European AFS Meeting
[http://www.dia.uniroma3.it/~afscon09/docs/watts.pdf](http://www.dia.uniroma3.it/~afscon09/docs/watts.pdf)

### Google Summer of Code 2009

OpenAFS received four slots for the 2009 Google Summer of Code.

Go to [http://socghop.appspot.com/org/home/google/gsoc2009/openafs](http://socghop.appspot.com/org/home/google/gsoc2009/openafs) for more
information about the GSoC projects.

The Google Summer of code is over for this year. The code from the three
active GSoC projects is available at
[http://code.google.com/p/google-summer-of-code-2009-openafs/downloads/list](http://code.google.com/p/google-summer-of-code-2009-openafs/downloads/list)

#### OpenAFS Server Preference Based on Network Conditions

Student Developer: Jake Thebault-Spieker <summatusmentis@gmail.com>

Mentor: Derrick Brashear <shadow@gmail.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2009-April/016590.html](https://lists.openafs.org/pipermail/openafs-devel/2009-April/016590.html)

The server preferences project has implemented code for the Windows platform
to rank servers based on packet round-trip time which is currently available
in gerrit. Using throughput as well will have updated code in gerrit soon
(although this is still a work in progress).

Upon getting code that seems reasonable for the Windows platform, the Unix
port should be a matter of re-implementing the code, but not changing too
much. I hope to have the unix port completed within a month, time-allowing.

\--Jake

Even though the Google Summer of code has ended, Jake will continue
working on the project until completion. He is still working within the
original specifications of the project.

A presentation about Jake's work was given at the European AFS Workshop
[http://www.dia.uniroma3.it/~afscon09/docs/part2.pdf](http://www.dia.uniroma3.it/~afscon09/docs/part2.pdf).

\--Ed.

### Projects with no progress or no update

- Disconnected AFS support
- Pthreaded Ubik
- Rx OSD integration & Raw Vicep Access in Clients
- Userspace cache manager
- Better Documentation

## Resolved Tickets

Here is a list of tickets that have been resolved since September 1, 2009:

    ticket # state     created       title
       1187: resolved  Oct 31, 2002  rxgen features
     124990: resolved  Jun 25, 2009  addition of doc/arch/dafs-vnode-fsa.dot
     125099: resolved  Jul 14, 2009  1.4.11 ../configure; make fails
     125101: resolved  Jul 15, 2009  ubik_VL_GetEntryByIDN not attempted
     125151: resolved  Jul 23, 2009  make clean issue on OSX
     125158: resolved  Jul 24, 2009  Re: getcwd() returns invalid working directory in chroot environment
     125226: resolved  Aug 14, 2009  ktc_curpag deactivated for non Kerberos environment -> breaks pam_afs.so
     125285: resolved  Aug 26, 2009  afs global lock not held
     125342: resolved  Sep 01, 2009  Mac OS 1.4 and 1.5 clients fail with huge root [=cache] partition sizes
     125351: resolved  Sep 02, 2009  Bug Report: windows client flooding fileserver
     125355: resolved  Sep 03, 2009  missing init causes erratic results using the client's "hard mount" functionality
     125388: resolved  Sep 09, 2009  OpenAFS 1.5.50 on Windows clients can DoS an openafs cell
     125389: resolved  Sep 10, 2009  Integrated login failed: Unknown code KTC2 on windows 1.5.6204
     125391: resolved  Sep 11, 2009  windows 64-bit 1.5.63 msi installer is corrupt
