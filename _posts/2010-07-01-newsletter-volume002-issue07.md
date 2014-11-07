---
title: OpenAFS Newsletter, Volume 2, Issue 7, July 2010
layout: page
category: newsletter
permalink: /newsletter/newsletter-2010-07-volume002-issue07.html
---

# OpenAFS Newsletter, Volume 2, Issue 7, July 2010

Welcome to the June issue of the OpenAFS newsletter. This newsletter
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

OpenAFS 1.5.75 was released on July 7. It includes various fixes and
improvements.

There is the start of a test harness in 1.5.75 and the master git
branch. The tests give output in the Test Anything Protocol (TAP), which
makes it easy to integrate tests written different languages. All tests
will eventually reside in the "tests" folder in git. Please refer to the
"tests/README" and "tests/HOWTO" files in the openafs git repository for
more information on how to write tests.

As was discussed in the chat rooms and mailing lists, the
\--enable-fast-restart configure option has been removed on the master
branch to deter novice users from using it without understanding the
ramifications.  This option allows the file server to restart after a
crash without salvaging volumes first.  This option is dangerous because
data corruption may go unnoticed because the volumes might not be salvaged
while a good backup is still around. The demand-attach file server offers
a better option, which allows for quicker start up than the
non-demand-attach server with less chance of data corruption.  Only the
fast-restart configure option was removed.  The fast-restart code will
remain in the tree until at least version 2.0.  If you still need to
enable the fast-restart functionality and understand the consequences,
then run configure, add the line "\#define FAST\_RESTART 1" to
src/config/afsconfig.h and compile.

Around the time of the 1.5.75 release, a new development plan was
announced. The new plan calls for multiple simultaneously developed
branches, which will be released as different versions. The new versions
will be as follows:

- 1.6.x (stable) - branching is imminent. The 1.6 branch will be cut form the
current master branch. Some release candidates will be released to iron
out the bugs before the 1.6.0 release. 1.6 will be the new stable branch,
which will replace 1.4.
- 1.7.x (development) - This branch will be based on the 1.6 branch sometime
after 1.6.0 is released. It will include all patches from 1.6.x and will
serve the integration of the Native Windows (IFS) client.
- 1.8.x (stable) - Once 1.7 is considered stable, the 1.8 branch will be cut
from 1.7 and, the 1.6 branch will be retired.
- 1.9.x (development) - After the 1.6 branch is cut, the master branch will
be opened for various changes targeted for 1.9. This will include IFS and
non-IFS changes. The plan is to focus resources on having a 1.6.0 release
before a 1.9.0 release, but these releases may happen out of order.
- 2.0.x (stable) - based on 1.9. The IFS client is planned to be
included. The 2.0.0 release will not happen before the 1.8.0 release.

The AFSLore Wiki has a new location and different software. The new
location is [http://wiki.openafs.org/AFSLore/WebHome/](http://wiki.openafs.org/AFSLore/WebHome/), and the wiki was
converted from twiki to ikiwiki. ikiwiki allows the wiki content to be
stored in git. This allows for content edits to be done through the web or
through git.

## Case Study - University of Maryland, College Park

In this issue, I would like thank Thomas Payerle from The University of
Maryland (College Park) for being profiled in the newsletter. --Jason

Thomas Payerle is an IT Sys Analyst at UMD.

Jason: How many full-time and part-time people are responsible for AFS
support and in what capacity?

Thomas: A manager and five full-time staff, however, administering AFS is
a fairly small part of their job.  Other responsibilities include support
of the campus Kerberos infrastructure, three medium-sized high performance
computing clusters, and general system support for 300 or so University
Solaris and Linux systems.

Jason: How much data do you store in AFS?

Thomas: We have 40TB or so dedicated to AFS storage.  About 5TB resides on
our SAN and 35TB on direct attached RAID storage.  Actual usage is much
less.

Jason: Do you use contractors or vendors to augment your workforce? If so,
do they use your AFS space?

Thomas: Rarely, but if the need arises and AFS access is required, we
provide it.

Jason: How do you use OpenAFS?

Thomas: OpenAFS is integral to the Unix environment that comprises our
academic, research, and computing infrastructure.  We use it to replicate
core OS components and applications running on Linux and Solaris.  We also
use it to deploy some Microsoft Windows applications.  User home
directories and web pages reside in AFS, as does the University's central
web hosting and WebSphere environments.  Access to AFS has traditionally
been provided via a native client, which is installed by default on all
supported Linux and Solaris machines and by hand on Windows and Macintosh
desktops on an as needed basis.  More recently, we also have begun
providing AFS access via a native web interface (a locally-modified MFILE
clone) and via WebDAV.

Jason: How many servers do you have?

Thomas: 10 file servers, 3 DB servers

Jason: Are they in different locations? How far apart are they?

Thomas: Servers reside in three campus locations that are approximately
0.25 miles (0.5 km) apart.

Jason: Do you use any other network storage to supplement AFS, like Dropbox, or
Windows shares?

Is AFS the only networked file-system that you use?

If not, what are the others, and how do they compare/contrast?

If applicable, why do you use the other file-systems?

Thomas: Microsoft DFS is the networked file-system of choice for Windows
desktops attached to the campus Active Directory infrastructure.  CIFS is
also used, though predominantly to integrate Windows desktops in
departments with Linux infrastructures.  Such departments also often use
NFS, especially those units who have the need/desire for departmental
control.  NFS is also often used to provide access to large data sets for
researchers with high-speed network connections who don't need the
management features of AFS and don't benefit much from its caching
performance.

Finally, Lustre is replacing NFS in the HPCC arena due to its high
performance

Jason: Is your investment in AFS increasing or decreasing?

Thomas: No change.

## Events

### European AFS Conference

European AFS & Kerberos Conference 2010 is glad to invite you to register
for this year's event, which will take place in Pilsen, Czech Republic,
from September 13 to September 15. The conference is being hosted by
Centre for Information Technology, University of West Bohemia.

See the conference WWW pages at [http://afs2010.civ.zcu.cz](http://afs2010.civ.zcu.cz) for further
details and breaking news.

Take advantage of the early registration rates, available until July
31\. Registration can be done on-line at
[http://afs2010.civ.zcu.cz/register/](http://afs2010.civ.zcu.cz/register/).

There are still some available agenda slots. Everyone is welcome to share
their experiences and ideas!

Submit your talk to afs2010@civ.zcu.cz. The "Call for Participation" will
end Monday August 2, 2010. Acceptances will be made based upon quality,
applicability, and fit with other submissions.

We are looking forward to seeing you in Pilsen!

The Workshop Organizers,

[http://afs2010.civ.zcu.cz/](http://afs2010.civ.zcu.cz/)

afs2010@civ.zcu.cz

## AFS Protocol Standardization

Informal drafts that haven't been uploaded to the IETF web site:

Rx Spec:

[http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html](http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html)

This draft is in the very early stages. Mike Meffie and Tom Keiser are the
current owners of this proposal. A formal specification of Rx is needed as
a basis for other IETF proposals.

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization](http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names)

Status: Third Draft

draft-brashear-afs3-pts-extended-names continues to be available for
review. There is still discussion about the technical content and
background references.

### AFS Callback Extensions

[http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo](http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo)

Status: Active - Waiting on RPC refresh

The callback draft is stable.  There is a published implementation. My
understanding is that it is accepted with the requirement that it be
adjusted to use RPC refresh data types, which means AFSFetchStatus64 and
the new 100ns time data type.  This is regarded as "trivial" but at the
same time, the spec can't be standardized as is.  It is planned for merge
in, IIRC, 1.9/1.10.

\--Matt Benjamin

### RXGK

[http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk](http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk)

Status: Active

Rxgk is a security layer for AFS which will support strong encryption and
authentication through Kerberos v5, GSI and any other GSSAPI security
mechanism.

Changes which are considered suitable for the 1.5.x series are in git -
look for changes with author sxw@your-file-system.com. A development tree,
which will be frequently rebased, is at
http://github.com/your-file-system/openafs-rxgk

Last Update: Jan 9, 2010

### AFS3 ACL Rights

[http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions](http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions)

Status: Second draft

Last update: January 13, 2010

This draft calls for volume-level restrictions on what users with 'a'
administrator rights to a folder may do. For example, you may want to
prevent users from granting 'w' write access to 'system:anyuser', which
would give anyone in the world with an AFS client write access.

### Rx Security Object Providing Cleartext Peer Identity Assertions

[http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear](http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear)

Status: Third draft

Last Update: April 17, 2010

I released a new version of the Rx Clear security class I-D the other
day.  I am hereby soliciting comments on this new version of the
draft.

[http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear](http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear)

The major changes in this version of the document are:

- new introductory section that better explains the relationship
between Rx and AFS-3 so that the document is more approachable for
novices
- additional prose in the security considerations section which better
explains how this security object changes the attack vectors, as well
as a brief mention of securing rxnull/rxclear with IPsec
- flesh out the AFS assigned numbers registrar section with formal
specifications for each newly requested registry
- change the endpoint identifier type enumeration from 32-bits to
8-bits, as the larger size seemed quite wasteful
- mark several security header fields as reserved for future use
- I added a number of informative references to Transarc and CMU ITC
tech reports

\--Tom

### AFSVol Tag-Length-Value Remote Procedure Call Extensions

[http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv](http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv)

Status: Third Draft

Last Update: June 15, 2010

Here is the change log for this revision:

- ERRATA: AFSCAPABILITIESMAX is actually defined to be 196, not 192
- add section re: cache coherence to the tag enumeration RPC
- add section re: day-of-week usage following discussion with mmeffie
- s/AFSVOL\_TLV\_TAG\_VOL\_DAY\_USE/AFSVOL\_TLV\_TAG\_VOL\_STAT\_USE\_TODAY/ following
discussion with mmeffie
- add AFSVOL\_TLV\_TAG\_VOL\_STAT\_USE\_TODAY\_DATE following discussion with
mmeffie
- add section re: definition of each tlv payload type
- add section re: definition of each tlv flag
- add note soliciting comments to afs3-stds list
- s/GCO Registrar/AFS Assigned Numbers Registrar/
- s/afsint/AFSVol/ so that we keep our options open with respect to wider
standardization of TLV semantics
- add AFSVOL\_TLV\_TYPE\_UINT64\_VEC payload type
- convert various tags from AFSVOL\_TLV\_TYPE\_OPAQUE to
AFSVOL\_TLV\_TYPE\_UINT64\_VEC
- add AFSVOL\_TLV\_FLAG\_QUALIFIER\_NO\_MATCH flag
- write AFSVol TLV Payloads registry definition
- write AFSVol TLV Tags registry definition
- add registry for AFSVol\_TLV.tlv\_flags
- add registry for AFSVol\_stat\_use\_per\_dow.stat\_flags
- write AFSVol Vol State Expls registry definition
- write AFSVol Program Types registry definition
- add numeric value assignments for newly created registries
- add RFC section references to new allocations
- add reference to Simon's AFS-STDS charter
- add an appendix with sample XDR for AFSVol Capabilities
- add an appendix with sample XDR for AFSVol TLV
- various cosmetic improvements (e.g. adding vspace tags)

Moving forward, I propose making one change in -03.  Namely, I want to
split type AFSVOL\_TLV\_TYPE\_UINT64 up into a few types that embed some
limited semantic knowledge into the TLV layer.  Specifically, I'm thinking
of splitting AFSVOL\_TLV\_TYPE\_UINT64 into the following six types:

- AFSVOL\_TLV\_TYPE\_UINT64    \[generic unit-less type, as before\]
- AFSVOL\_TLV\_TYPE\_TIME\_ABS  \[Simon's rpc refresh 100ns unit; absolute\]
- AFSVOL\_TLV\_TYPE\_TIME\_REL  \[Simon's rpc refresh 100ns unit; relative\]
- AFSVOL\_TLV\_TYPE\_BLOCKS    \[storage in 1KiB units\]
- AFSVOL\_TLV\_TYPE\_VOLUME\_ID
- AFSVOL\_TLV\_TYPE\_PARTITION\_ID

All six would be backed by afs\_uint64 in the AFSVol\_TLV\_value union. While
this change isn't strictly necessary, it's relatively straightforward to
implement, and makes the resulting volume TLV data considerably more
self-describing.

As always, comments and feedback are invited.

\--Tom

### AFS Byte-Range File Locking

[http://tools.ietf.org/html/draft-mbenjamin-afs-file-locking](http://tools.ietf.org/html/draft-mbenjamin-afs-file-locking)

Status: Fifth Draft

This draft proposes protocol extensions to support byte-range and
mandatory locking.

The first draft was submitted on May 5, 2010.

## Projects

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

The DAFS bug mentioned at the workshop involving restoring fileserver
state has been fixed (gerrit 2205). One more DAFS bug involving
demand-salvages of on-line volumes has been identified and is being
worked on (gerrit 2329). A proposed run-time option is in gerrit 2277 to
enable fast-restart-like functionality with DAFS. We're also working on
Admin Guide and Quick Start documentation for DAFS, as well as always
building DAFS and non-DAFS binaries (instead of having DAFS be a
configure-time option). The positional I/O work and threaded salvaging
work is postponed until after 1.6 has been branched.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

One of the remaining demand-attach binaries has now been documented,
leaving only one left to document.  There have been some other, more minor
improvements to the man page documentation.

The OpenAFS wiki has been relocated from dementia.org to a new permanent
home and temporary URL at openafs-wiki.stanford.edu, probably soon to get
a \*.openafs.org DNS name.  It is now using ikiwiki, and the eventual plan
is to allow people to check out and commit to the underlying Git
repository via Gerrit, which is more efficient than using the web editor
for significant work.



### User-space cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

No update (on hold until 1.6 has branched).

\--Andrew

### Kerberos v5 and multiple encryption types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

The next rxk5 "m" base will be 1.5.74.  Before dealing with the new
"afsconf\_PickClientSecObj", I updated rxk5 "xo" (1.4 base).  \[ The
gatekeepers need not care, but rxk5 for 1.4 is more interesting to
potential testers, then there's rxosd which has unique crypto. \] Nearly
all of my recent work has been on refining patch splitting.  I'm up to
over 100 distinct patches.  The split process can work on m, xo, or in the
future rxk5 for rxosd or 1.6 or 1.9 The next snapshot I do will be of
"xo".  Feedback for those patches will improve what I do next for 1.5.74.

\--Marcus

- update to 1.5.74/75
- improve patch splitout process
- move to git(devel/temp)
- test on windows
- implement anonymous callback protection

\--Marcus Watts

### S3 Front-end for AFS

Project Contacts:

- Fabrizio Manfredi <fabrizio.manfredi@gmail.com>
- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

We have a new internal snapshot (alpha2) with 90% of the S3 functions.  We
have also a non-AFS-based simple authentication and some revision
primitives, but it lacks some parts like logging or load balancing.  We
hope to release a preview soon.

\--Manfred

### Virtual Machine Images

Project Contact:

- Fabrizio Manfredi <fabrizio.manfredi@gmail.com>

Update operating system to CentOS 5.5 with two VMware snapshot inside, one
is based on openafs 1.4.12.1 second it is based on openafs 1.5.74.  I also
updated the AFS Perl module to 2.6.2.  Link for download:
[https://sourceforge.net/projects/s3afs/files/](https://sourceforge.net/projects/s3afs/files/)

We also develop a generic "binding" interface with swig for scripting
languages, you will find in the next update

### Google Summer of Code 2010

OpenAFS received five slots for the 2010 Google Summer of Code.

Go to [http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs](http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs)
for more information about the GSoC projects.

#### Unix Support for AppleDouble files (Posix Attributes)

Student Developer: Kelli Ireland <kelli.ireland@gmail.com>

Mentor: Derrick Brashear <shadow@gmail.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html)

Initial implementation of dot-underscore file parser is being used for
testing.  Rewrite will be needed before integration.

\--Kelli Ireland

#### Encrypted Storage

Student Developer: Sanket Agarwal <sanket@sanketagarwal.com>

Mentor: Simon Wilkinson <sxw@inf.ed.ac.uk>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017424.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017424.html)

Abstract:

The AFS protocol offers encryption for data transport from client to
server. However, that data is stored on the server in cleartext, where it
can potentially be read by the administrators of that server. This poses a
real world problem for organizations who wish to outsource the provision
of their file storage, whilst keeping their data confidential. This
project would augment the existing AFS client to support encrypting data
blocks before sending them to the file server.

#### Apply the kafs project of OpenAFS

Student Developer: Wang Lei <wang840925@gmail.com>

Mentor: David Howells <dhowells@redhat.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-April/017493.html](https://lists.openafs.org/pipermail/openafs-devel/2010-April/017493.html)

We have almost finished the DNS support sub-project.  I've been
working on adding some features to make it more complete.  I have also
been working on picking up the pioctl sub-project to be worked on
next.

\--Wang Lei

#### Port OpenAFS to NetBSD

Student Developer: Matt Smith <matt.j.sm@gmail.com>

Mentor: Matt Benjamin <matt@linuxbox.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html)

I have finished modifications to the LKM so that it now builds. I'm
currently working on learning how to use ddb to debug it as it still
crashes when loaded. The next step will be to move on to debugging
functionality.

\--Matt Smith

#### An open source version of the Microsoft Safe String Library

Student Developer: Jonas Sundberg <jonas.sundberg@gmail.com>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html)

The basic versions of the functions have been tested on both Linux and
Windows and the the tests have been verified against the Microsoft
implementation. A draft of the extended functions has also been
written. The current focus is implementing tests for the extended
functionalities of the extended functions to test the draft
implementation and verify the functionality against the Microsoft
implementation.

\--Jonas

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Active Directory Back-end for Ptserver - November 2009
- Extended Callback Information - January 2010
- Disconnected AFS support - February 2010
- Mac OS X OpenAFS Preference Pane - April 2010
- Rx OSD integration & Raw Vicep Access in Clients - May 2010
- Per-File ACLs - May 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 74 (last month: 62)

    Patches merged into the master branch:
    Month   Number of Commits
    2010-07   62 (Partial month)
    2010-06  171
    2010-05  139
    2010-04  160
    2010-03  140
    2010-02  156
    2010-01  103
    2009-12   72
    2009-11   85
    2009-10  154
    2009-09  142
    2009-08   78

    Patches merged into the stable 1.4.x branch:
    Month   Number of Commits
    2010-06   2
    2010-05  15
    2010-04   4
    2010-03  28
    2010-02  35
    2010-01  11
    2009-12  92
    2009-11  21
    2009-10   7
    2009-09   8
    2009-08  17

### Patches waiting for review

    Date       Author          Change# Description
    2010-07-10 Simon Wilkinson  (2384) Linux: Actually use freezer compatibility func
    2010-07-10 Simon Wilkinson  (2383) Linux: Use freezer compatibility macros in RX
    2010-07-09 Andrew Deason    (2338) vos status: report human-readable last*Time
    2010-07-09 Andrew Deason    (2337) vos status: add lastActiveTime field
    2010-07-09 Andrew Deason    (2336) vos status: actually show created time
    2010-07-09 Andrew Deason    (2376) RX: ignore all local 127/8 IFF_LOOPBACK interfaces
    2010-07-09 Andrew Deason    (2367) Treat all 127.0/16 addresses as loopback
    2010-07-09 Andrew Deason    (2375) Consolidate loopback address tests
    2010-07-09 Andrew Deason    (2368) viced: Ignore client loopback alternate addresses
    2010-07-09 Michael Meffie   (1786) viced: host hash address collisions
    2010-07-09 Andrew Deason    (2370) GetInodeSummary: free inode info
    2010-07-08 Chaz Chandler    (2372) libafscp: code cleanup
    2010-07-08 Chaz Chandler    (2371) libafscp: a library for "clientless" operations
    2010-07-08 Derrick Brashear (2366) rx mtu discovery tuning beyond ifmtu
    2010-07-08 Michael Meffie   (2312) print assertion expression
    2010-07-07 Andrew Deason    (2329) DAFS: Fix demand-salvages of attached volumes
    2010-07-07 Derrick Brashear (2344) viced install signal handler earlier
    2010-07-07 Michael Meffie   (2349) man: document bos addhost -clone
    2010-07-06 Derrick Brashear (2307) solaris build userland with CC
    2010-07-02 Benjamin Kaduk   (2321) FBSD: bandaid around vcache opens tracking
    2010-07-01 Michael Meffie   (1562) ihandle positional read and write
    2010-07-01 Andrew Deason    (2277) Add -unsafe-attach fileserver option
    2010-06-30 Jeffrey Hutzelman (2288) Fast restart for Ubik database servers
    2010-06-30 Simon Wilkinson  (2290) Linux: Make keyring destructor remove all tokens
    2010-06-30 Jeffrey Hutzelman (2275) Don't overflow a buffer on the vlserver's stack at startup
    2010-06-30 Jeffrey Hutzelman (2287) Add -ubiknocoord option to prevent becoming coordinator
    2010-06-29 Jeffrey Hutzelman (2279) Include user and build host in version string
    2010-06-28 Matt Benjamin    (2229) An RPC test dispatch library for vice
    2010-06-24 Andrew Deason    (2250) vol-salvage: Move global vars into SalvInfo struct
    2010-06-24 Christof Hanke   (1970) Add output-table to libcmd
    2010-06-24 Andrew Deason    (2246) Move FUSE autoconf code to acinclude.m4
    2010-06-23 Andrew Deason    (2239) Provide man pages for more fssync-debug commands
    2010-06-23 Michael Meffie   (1949) xstat: fix large integer output
    2010-06-22 Andrew Deason    (2231) ubik: Fix buffers for reading-during-writes
    2010-06-22 Andrew Deason    (2106) vlserver: Allow reading during ubik writes
    2010-06-22 Andrew Deason    (2230) ubik: Abstract buffer matching and pass trans ptrs
    2010-06-22 Andrew Deason    (2108) ubik: Protect ubik_servers in urecovery_Interact
    2010-06-22 Andrew Deason    (2107) ubik: Drop dbase versionLock during I/O and sleeps
    2010-06-22 Andrew Deason    (2105) vlserver: Access cache via vl_ctx
    2010-06-21 Hartmut Reuter   (70) preparing rxosd integration: change in AFSFetchStatus
    2010-06-20 Christof Hanke   (1975) Example usage of the tabular output in libcmd
    2010-06-19 Matt Benjamin    (2216) unix cm  rx-oblivious connection pooling
    2010-06-18 Russ Allbery     (2146) Add replacement mkstemp and use it
    2010-06-16 Andrew Deason    (2209) VGetVolume_r: do not wait for offlining volumes
    2010-06-15 Andrew Deason    (2161) libafs: consistently hold vnode refs
    2010-06-09 Andrew Deason    (2104) vlserver: Add a struct for trans-specific data
    2010-06-07 Jeffrey Altman   (2089) Convert from using nvldbentry to uvldbentry
    2010-06-06 Jeffrey Altman   (1742) Make -printuuid an option for all vos commands
    2010-06-06 Jeffrey Altman   (2090) Remove 'register' from src/volser
    2010-06-04 Matt Benjamin    (2071) VICE error table
    2010-06-04 Michael Meffie   (215) rxdebug: show delayed abort packet count for rx peers
    2010-06-02 Andrew Deason    (1869) Remove the global tempHeader/stuff structures
    2010-06-02 Andrew Deason    (1863) Provide an abstract thread pool object
    2010-06-02 Andrew Deason    (1865) Allow salsrv salvage I/O to occur in parallel
    2010-06-02 Andrew Deason    (1864) Parallel I/O extensions to namei backend
    2010-06-02 Andrew Deason    (1862) Provide an abstract work queue object
    2010-06-01 Andrew Deason    (2048) Add AFS::ukernel libuafs perl bindings
    2010-05-27 Andrew Deason    (2049) Add documentation for AFS::ukernel
    2010-05-27 Matt Benjamin    (2011) Extended callback implementation
    2010-05-17 Rainer Toebbicke (1311) Lockless path through afs_linux_dentry_revalidate
    2010-05-16 Jeffrey Altman   (1965) Windows: add BSD getopt to afsutil.lib
    2010-05-08 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2010-05-07 sanket           (1777) Add xml functionality to the vos examine command
    2010-05-05 Derrick Brashear (1906) fix dumptool on macos
    2010-03-23 Derrick Brashear (1625) preliminary support for pinned vcaches
    2010-03-17 Derrick Brashear (1553) dynamic volume allocation
    2010-02-15 Michael Meffie   (1001) return an error from afs_readdir when out of buffers
    2010-02-03 Dan Hyde         (1191) runningCalls: VOL_COUNT_LOCK vs VTRANS_LOCK
    2010-02-03 Derrick Brashear (1172) linux mmap anti-deadlock shouldn't break StoreAllSegments
    2010-02-03 Derrick Brashear (1201) basic kernel event system for afs cm
    2010-01-20 Simon Wilkinson  (1074) Unix CM: Include memcache's tiov in rxfs_context
    2009-09-09 Matt Benjamin    (435) clear stat flag on renamed directories
    2009-08-29 Matt Benjamin    (376) K5SSL by Marcus Watts
    2009-07-29 Michael Meffie   (147) Fix bosserver directory creation



### Patches merged into the master branch

    Date       Author          Change# Description
    2010-07-10 Russ Allbery     (2378) Update config.guess and config.sub to 2009-12-30 and 2010-01-22
    2010-07-10 Russ Allbery     (2377) Make config.sub executable
    2010-07-10 Russ Allbery     (2381) Terminate the DARWIN80 #if in afs_osidnlc.c
    2010-07-10 Russ Allbery     (2379) Fix ktime test for errors
    2010-07-10 Russ Allbery     (2380) Include linux/freezer.h in rx_kmutex.c
    2010-07-09 Andrew Deason    (2357) Use afs_sfsize_t for *_SIZE results
    2010-07-09 Benjamin Kaduk   (2373) Remove incorrect critical section use in dnlc_lookup
    2010-07-09 Michael Meffie   (2374) wiki url changed
    2010-07-09 Michael Meffie   (2369) build fix on older linux
    2010-07-08 Alexander Ivan Redinger (2348) SOURCE-MAP updates
    2010-07-08 Jonathan Billings (2364) Update the Red Hat spec file to include fssync-debug man pages
    2010-07-08 Simon Wilkinson  (2320) vos: Don't call SubEnumerate twice
    2010-07-08 Andrew Deason    (2359) Fix VPrintDiskStats_r logging
    2010-07-08 Andrew Deason    (2358) viced: Remove stray \r
    2010-07-08 Russ Allbery     (2356) Remove a few erroneous NEWS entries for 1.5.75
    2010-07-08 Benjamin Kaduk   (2362) Fix build
    2010-07-08 Benjamin Kaduk   (2360) FBSD: sync with NFS for *pages vnops
    2010-07-07 Russ Allbery     (2355) Add NEWS entries for 1.5.75
    2010-07-07 Andrew Deason    (2353) klog: refactor klog_prompter
    2010-07-07 Andrew Deason    (2352) Fix shlibafsrpc des.c hp-ux special case
    2010-07-07 Andrew Deason    (2351) HPUX: correct PostPopulateVCache vfsp set
    2010-07-07 Andrew Deason    (2350) HPUX: include proc_iface.h for proc_t
    2010-07-07 Andrew Deason    (2339) UINT_MAX requires limits.h
    2010-07-07 Derrick Brashear (2343) kernel InitPeerParams has bogus branching and dup code
    2010-07-06 Andrew Deason    (2341) HPUX: make osi_procname a stub
    2010-07-06 Andrew Deason    (2340) Fix stray static inline
    2010-07-06 Derrick Brashear (2335) fix newline conventions
    2010-07-06 Derrick Brashear (2334) rxkad heimdal cleanup
    2010-07-06 Jeffrey Altman   (2333) Windows: update release notes for 1.5.75
    2010-07-06 Jeffrey Altman   (2332) Windows: ChangeLog for 1.5.75
    2010-07-06 Derrick Brashear (2328) make openafs 1.5.75
    2010-07-04 Benjamin Kaduk   (2331) FBSD: always close the rx socket when shutting down
    2010-07-04 Benjamin Kaduk   (2330) Do not recurse on the glock in rxk_NewSocketHost
    2010-07-03 Jonathan Billings (2305) Removed kpasswd from openafs-file-list
    2010-07-02 Derrick Brashear (2327) update VAllocVnode logging
    2010-07-02 Andrew Deason    (2286) DAFS: Salvage VG on volume creation error
    2010-07-02 Andrew Deason    (2285) DAFS: Allow FSSYNC salvages on unknown volumes
    2010-07-02 Marc Dionne      (2324) Linux: cache bypass: fix FCSBypass tests
    2010-07-02 Marc Dionne      (2323) Linux: cache bypass: warning fix in afs_bypasscache.c
    2010-07-02 Andrew Deason    (2284) DAFS: Log attempted salvage requests
    2010-07-02 Matt Benjamin    (2215) cache-bypass  explicitly reference pages involved in background i/o
    2010-07-02 Simon Wilkinson  (2316) Build: Let configure pick our lex and yacc
    2010-07-02 Simon Wilkinson  (2283) Build: Rework git version detection
    2010-07-02 Andrew Deason    (2276) vol: Move destroyMe check outside of inUse check
    2010-07-02 Derrick Brashear (2291) VAllocVnode error handling
    2010-07-02 Rainer Toebbicke (2243) Do not call afs_FlushVCBs with afs_xvcache held
    2010-07-02 Derrick Brashear (1959) bosserver force corefiles
    2010-07-02 Marc Dionne      (2325) Linux: cache bypass: remove warning print before panic
    2010-07-02 Marc Dionne      (2322) Linux: cache bypass: warning fixes in afs_pioctl.c
    2010-07-02 Marc Dionne      (2319) Linux: cache bypass: deal with the afs_serverHasNo64Bit case
    2010-07-02 Rainer Toebbicke (2244) Protect truncate_inode_pages when called from osi_VM_FlushPages
    2010-07-02 Marc Dionne      (2317) Linux: cache bypass: avoid unused variable warnings
    2010-07-02 Marc Dionne      (2318) Linux: cache bypass: warning cleanup in afs_daemons.c
    2010-07-02 Simon Wilkinson  (2298) Linux: Fix pagevec use in cache-bypass
    2010-07-01 Benjamin Kaduk   (2315) FBSD: do not recurse on the afs_xvcache write lock
    2010-07-01 Andrew Deason    (2314) Document fs -human
    2010-07-01 Andrew Deason    (2313) fs diskfree displays 'total' not 'kbytes'
    2010-07-01 Andrew Deason    (2311) fs: Correct human-readable output alignment
    2010-07-01 Tom Keiser       (2309) nuke configure options from AIX param files
    2010-07-01 Derrick Brashear (2306) update ticket5 from heimdal
    2010-07-01 Andrew Deason    (2278) Remove --enable-fast-restart configure option
    2010-07-01 Tom Keiser       (2308) DAFS: fix VOL_HDR_IN_LRU state bit tracking
    2010-06-30 Andrew Deason    (2304) fs: HumanPrintSpace is void
    2010-06-30 Andrew Deason    (2303) vlclient: Remove incorrect whitespace fix
    2010-06-30 Benjamin Kaduk   (2297) Disable red zones for amd64 FBSD kernel code
    2010-06-30 Simon Wilkinson  (2301) Add human-readable printout to fs df
    2010-06-30 Simon Wilkinson  (2300) fix & enhance vlclient command-line handling
    2010-06-30 Simon Wilkinson  (2299) Fix VLog so that actual levels are used
    2010-06-30 Benjamin Kaduk   (2296) FBSD: in reclaim, print the failed vnode
    2010-06-30 Benjamin Kaduk   (2295) Actually invalidate the buffer in FBSD's FlushPages
    2010-06-30 Benjamin Kaduk   (2294) FBSD TryToSmush locking fixup
    2010-06-30 Benjamin Kaduk   (2293) Correct whitespace in FBSD/osi_vm.c
    2010-06-30 Benjamin Kaduk   (2292) Correct FBSD-version conditionals for VFS locking
    2010-06-30 Derrick Brashear (2282) stop abusing OPTMZ in aklog
    2010-06-29 Derrick Brashear (2281) klog warning fix
    2010-06-29 Rod Widdowson    (2280) Fix checked build of vldb_check
    2010-06-28 Simon Wilkinson  (1824) Use git describe to determine build version
    2010-06-28 Andrew Deason    (2272) LINUX24: crfree typo
    2010-06-28 Andrew Deason    (2271) LINUX24: remove pagecopy and other 2.6-only code
    2010-06-28 Andrew Deason    (2274) LINUX: Remove LINUX26 conditional in proc2cred
    2010-06-28 Andrew Deason    (2273) LINUX24: Remove BDI references
    2010-06-28 Andrew Deason    (2270) LINUX24: NEED_IOCTL32 fixup
    2010-06-28 Andrew Deason    (2269) LINUX24: cr_ref is a regular int
    2010-06-28 Andrew Deason    (2268) LINUX24: Remove group_info macros/functions
    2010-06-28 Rod Widdowson    (2027) Make file offsets in vldb layout unsigned ints
    2010-06-28 Simon Wilkinson  (2266) Make make_libafs_tree.pl use strict and warnings
    2010-06-28 Marc Dionne      (2260) Linux: Use filehandles for all 2.6 kernels
    2010-06-28 Matt Benjamin    (2267) linux trivially track host signedness in afs_prototypes.h
    2010-06-27 Andrew Deason    (2257) libafs: correct export_reqhandler prototype
    2010-06-27 Andrew Deason    (2256) Use unsigned addresses in the NFS exporter
    2010-06-27 Andrew Deason    (2255) Use unsigned IP addresses in bu*
    2010-06-27 Andrew Deason    (2254) vlserver: Use unsigned addresses
    2010-06-27 Marc Dionne      (2259) Linux: remove some 2.6 specific code from 2.4
    2010-06-27 Simon Wilkinson  (2265) Autoconf: Update AC_INIT macro use
    2010-06-27 Simon Wilkinson  (2264) RPM Packaging: Make file types clear
    2010-06-27 Simon Wilkinson  (2263) RPM Packaging: All debug kernels are bad
    2010-06-27 Simon Wilkinson  (2262) RPM Packaging: Add support for Fedora 12 and Fedora 13
    2010-06-27 Simon Wilkinson  (2261) RPM Packaging: Skip comments in configure.in
    2010-06-26 Andrew Deason    (2258) Remove semicolon from AFS_NORETURN
    2010-06-25 Andrew Deason    (2253) ptserver: Remove IP_WILDCARDS symbol
    2010-06-25 Andrew Deason    (2252) ptserver: Use unsigned addresses
    2010-06-25 Andrew Deason    (2251) rx: Use unsigned addresses
    2010-06-25 Andrew Deason    (2249) volser: Use unsigned addresses and volume IDs
    2010-06-25 Matt Benjamin    (2245) windows  add rx_Get/SetServiceSpecific to libafsrpc module exports
    2010-06-25 Simon Wilkinson  (2247) Linux: Check return code from VerifyVCache in mmap
    2010-06-24 Andrew Deason    (2242) Remove stale warning suppressions
    2010-06-24 Jeffrey Altman   (2238) Windows: Cleanup of src/config/NTMakefile
    2010-06-24 Matt Benjamin    (2234) windows  don't include assert.h (and afs support headers) in util_cr.c
    2010-06-23 Andrew Deason    (2241) Indicate that fssync unix sockets are the default
    2010-06-23 Rainer Toebbicke (1902) patch cbd_printCBcrash - harden callback debugging
    2010-06-23 Andrew Deason    (2240) ubik: Remove api for reading during write locks
    2010-06-23 Benjamin Kaduk   (2214) Try to flush vnodes in FBSD's unmount, bailing if necessary
    2010-06-23 Derrick Brashear (1852) mariner log messages for creating and removing files
    2010-06-23 Rainer Toebbicke (2233) Don't hold on to the afs_xvcache lock while creating a symlink
    2010-06-23 Andrew Deason    (2236) vldb_check: Interpret VLOP_* vlentry flags
    2010-06-23 Andrew Deason    (2235) vos: Interpret VLOP_* lock flags
    2010-06-23 Rainer Toebbicke (1903) Do not corrupt volume linktable when special file already exists
    2010-06-23 Andrew Deason    (875) Make ubik use unsigned addresses
    2010-06-23 Andrew Deason    (1979) Mention that -fakestat fakes local cellular mounts
    2010-06-23 Davor Ocelic     (2220) Provide manpage for fssync-debug and most subcmds
    2010-06-23 Derrick Brashear (1872) no fs sa /afs in dynroot mode
    2010-06-23 Andrew Deason    (2211) vol: break callbacks when needsCallback is set
    2010-06-22 Derrick Brashear (2228) rx mtu ping timing tweaks
    2010-06-22 Marc Dionne      (2232) Fix CHush test
    2010-06-22 Derrick Brashear (2223) test suite warning safety
    2010-06-22 Derrick Brashear (2217) afsd -dynroot-sparse mode for hushed cells
    2010-06-22 Andrew Deason    (2210) salvaged: Break volume callbacks on vol change
    2010-06-22 Benjamin Kaduk   (2222) Simplify preprocessor logic in afs_pioctl
    2010-06-22 Andrew Deason    (2226) vldb_check: ntohs ubik header size
    2010-06-22 Andrew Deason    (2212) Set VolumeChanged when we create a new root dir
    2010-06-22 Andrew Deason    (2225) ubik: Do not hide ReplayLog errors
    2010-06-22 Andrew Deason    (2224) ubik: ntohl on reading the replay log
    2010-06-21 Davor Ocelic     (2219) Update manpage links, fix doc typo in fssync-debug
    2010-06-19 Derrick Brashear (2218) update macos readmes
    2010-06-18 Benjamin Kaduk   (2213) Fix aklog segfault
    2010-06-17 Simon Wilkinson  (1823) Linux: Remove the BKL
    2010-06-16 Russ Allbery     (2207) Remove configure remnants of Digital UNIX / Tru64 client
    2010-06-16 Chaz Chandler    (2155) IRIX: Implement makesname()
    2010-06-16 Chaz Chandler    (2154) IRIX code cleanup
    2010-06-16 Andrew Deason    (2205) Do not assume non-valid addrs in addr hash table
    2010-06-16 Andrew Deason    (2204) Make h_stateVerifyAddrHash log port on errors
    2010-06-16 Russ Allbery     (2082) Fix aklog warnings when building with Heimdal
    2010-06-15 Russ Allbery     (2026) Rework the Kerberos Autoconf probes
    2010-06-15 Andrew Deason    (2124) GetVolume: do not wait for offlining volumes
    2010-06-15 Andrew Deason    (2206) afscp: Correctly advertise local addresses
    2010-06-15 Jeffrey Altman   (2203) mkvers.c - remove afsconfig.h, afs/param.h and assert.h
    2010-06-15 Andrew Deason    (2160) Fix tptserver and tvlserver install rules
    2010-06-15 Andrew Deason    (2123) Cleanup and doxygen-ify the comments for GetVolume
    2010-06-15 Russ Allbery     (2162) Build util tests properly with make check
    2010-06-14 Jeffrey Altman   (2159) Windows: ensure that afsconfig.h and afs/param.h are included
    2010-06-14 Jeffrey Altman   (2158) Windows: fix definition of lstat() macro
    2010-06-14 Jeffrey Altman   (2157) Windows: define errno_t on compilers older than 1400
    2010-06-14 Andrew Deason    (2103) ubik: add interface for reading during write locks
    2010-06-14 Derrick Brashear (2153) arm darwin port
    2010-06-14 Derrick Brashear (2150) ktc newpag stub when environ is not supported
    2010-06-14 Derrick Brashear (2149) darwin afsd include cleanup
    2010-06-14 Derrick Brashear (2148) afsd mill dup sys/mount.h include
    2010-06-14 Marc Dionne      (2130) Linux: Fix RCU_READ_LOCK test
    2010-06-14 Derrick Brashear (2147) generated file target
    2010-06-14 Derrick Brashear (2145) buildtools target
    2010-06-14 Derrick Brashear (2116) unix cm activate mtu pings
    2010-06-14 Derrick Brashear (2115) rx mtu ping handling
    2010-06-14 Derrick Brashear (2114) path mtu don't track nonsequenced packets
    2010-06-14 Derrick Brashear (2113) rx checkcall kill extra indirection on call for conn
    2010-06-14 Derrick Brashear (2112) idle dead time track less
    2010-06-14 Derrick Brashear (2117) unix cm log path mtu warning when retrying
    2010-06-14 Matt Benjamin    (2151) mcas fix gc_get_tag return type
    2010-06-14 Matt Benjamin    (2152) mcas cleanup inc/dec macros
    2010-06-13 Simon Wilkinson  (2143) libadmin: Don't dereference NULL pointer in cmd
    2010-06-13 Simon Wilkinson  (2142) fs: Can't use store behind data if pioctl errored
    2010-06-13 Simon Wilkinson  (2141) viced: CopyOnWrite2 shouldn't return undefined val
    2010-06-13 Simon Wilkinson  (2140) Formatting fixes
    2010-06-13 Simon Wilkinson  (2139) vol: open() needs mode if called with O_CREAT
    2010-06-13 Simon Wilkinson  (2138) audit: result is only used on AIX
    2010-06-13 Russ Allbery     (2129) Avoid off-by-one error when saving the password in klog
    2010-06-13 Simon Wilkinson  (2144) bucoord: Use mkstemp properly
    2010-06-13 Marc Dionne      (2131) Linux s390x: replace AFS_64BIT_KERNEL with AFS_LINUX_64BIT_KERNEL
    2010-06-13 Simon Wilkinson  (2137) comerr: Don't leak CFStringRef
    2010-06-13 Simon Wilkinson  (2136) libadmin: Don't use undefined value
    2010-06-13 Simon Wilkinson  (2135) Add support for clang compiler attributes
    2010-06-13 Simon Wilkinson  (2134) Add AFS_NORETURN macro and use it
    2010-06-13 Simon Wilkinson  (2133) rxgen: Remove inlist from autogenerated code
    2010-06-13 Simon Wilkinson  (2132) Changes to build with clang on Mac OS 10.5
    2010-06-13 Russ Allbery     (2083) Document vos listaddrs -host and -uuid
    2010-06-13 Simon Wilkinson  (2127) Linux: Fix set_cr_group_info and cr_group_info
    2010-06-12 Andrew Deason    (2122) Do not set inUse for non-fileserver non-DAFS
    2010-06-12 Andrew Deason    (2126) vlclient: work with non-space whitespace
    2010-06-11 Derrick Brashear (2125) dafs state analyzer shouldn't require trailing spaces in commands
    2010-06-11 Andrew Deason    (2121) Remove afsio warnings and errors
    2010-06-11 Matt Benjamin    (2053) windows  cm_BeginDirOp add flags (nobuildtree)
    2010-06-11 Simon Wilkinson  (2120) RX: Can't assert a void result
    2010-06-11 Matt Benjamin    (2097) rx service specific data
    2010-06-10 Andrew Deason    (709) Break origin's callback for RXAFS_Rename target
    2010-06-10 Andrew Deason    (436) Avoid unnecessarily updating .. in SAFSS_Rename
    2010-06-10 Jeffrey Altman   (2110) Windows: Revise SMB QuerySecurityInfo for MS10-020
    2010-06-10 Derrick Brashear (2091) further constrict nat pings
    2010-06-10 Russ Allbery     (2109) Add additional documentation for the new test suite
    2010-06-09 Andrew Deason    (2102) Install pthreaded ptserver and vlserver
    2010-06-09 Andrew Deason    (2101) Move FreeBlock prototype to vlserver_internal.h
    2010-06-09 Andrew Deason    (2100) Define updateUbikNetworkAddress static
    2010-06-09 Russ Allbery     (2099) Fix the trailing #endif comment in tests/tap/basic.h
    2010-06-09 Russ Allbery     (2098) Add okv function to the TAP test library
    2010-06-09 Jeffrey Altman   (2095) Windows: Detect if AFSCache is memory mapped to a new address
    2010-06-08 Andrew Deason    (2096) Solaris: lookup "" like "."
    2010-06-07 Andrew Deason    (2094) AIX: make osi_procname a stub
    2010-06-07 Andrew Deason    (1987) libafs: consistently hold vnode refs
    2010-06-07 Andrew Deason    (2093) Make lib/afs.exp in sys_depinstall
    2010-06-07 Andrew Deason    (2092) AIX: declare code in osi_TryEvictVCache
    2010-06-05 Jeffrey Altman   (2088) Windows: remove src/NTMakefile
    2010-06-05 Jeffrey Altman   (2087) Windows: Cleanup .exp .res .manifest and others
    2010-06-05 Jeffrey Altman   (2080) Windows: Update fs newcell and add VIOCNEWCELL2
    2010-06-05 Jeffrey Altman   (2079) Windows: Freelance Import CellServDB
    2010-06-05 Jeffrey Altman   (2085) Windows: engage path mtu discovery for rx
    2010-06-05 Jeffrey Altman   (2084) Windows: enable circular buffer management for rx socket input
    2010-06-04 Russ Allbery     (2065) Comprehensive edit of Admin Guide chapter two (first 20%)
    2010-06-04 Derrick Brashear (2069) rx mtu discovery constrainment code
    2010-06-04 Simona Poilinca  (1778) Windows: convert cm_config.c to use strsafe library
    2010-06-04 Asanka Herath    (2034) Windows: Support building a lite-client installer
    2010-06-04 Rainer Toebbicke (2072) "fs checkservers" during cache creation can crash client
    2010-06-04 Russ Allbery     (2035) Document in SalvageLog(5) the per-partition salvager logs
    2010-06-03 Jeffrey Altman   (2078) Windows: Fix usage of cm_FreeServerList
    2010-06-03 Jeffrey Altman   (2077) Windows: Reduce number of Nat Ping Connections
    2010-06-03 Jeffrey Altman   (2076) Windows: Fix cm_IoctlSkipQueryOptions buffer management
    2010-06-03 Jeffrey Altman   (2075) Windows: do not request KEY_WRITE privilege if not required
    2010-06-03 Jeffrey Altman   (2074) Windows: warning removal
    2010-06-03 Derrick Brashear (2081) darwin notify don't recurse on vcache lock
    2010-06-03 Andrew Deason    (2073) up: refuse multicharacter arguments
    2010-06-03 Asanka Herath    (2033) Windows: Fix midl options for generating stub code
    2010-06-02 Derrick Brashear (2068) rx allow setpeermtu to take a peer
    2010-06-02 Derrick Brashear (2067) rx setpeermtu should handle a host correctly
    2010-06-02 Derrick Brashear (2066) aklog no krb524 kill warnings
    2010-06-01 Russ Allbery     (2052) Add warnings for Authentication Server commands
    2010-06-01 Derrick Brashear (2058) prune further list of connections we natping on

### Patches merged into the stable 1.4.x branch

    Date       Author          Change# Description
    2010-06-23 Andrew Deason    (2237) ubik: ntohl on reading the replay log
    2010-06-14 Russ Allbery     (2128) Do not use AFS_PTR_FMT or %p in 1.4
