---
title: OpenAFS Newsletter, Volume 2, Issue 6, June 2010
layout: page
category: newsletter
permalink: /newsletter/newsletter-2010-06-volume002-issue06.html
---

# OpenAFS Newsletter, Volume 2, Issue 6, June 2010

Welcome to the June issue of the OpenAFS newsletter. This newsletter
summarizes what is happening in the OpenAFS community.

As always, volunteers, patches, bug reports, or any other type of help is
greatly appreciated.

A new section is starting for case studies. Each issue of the newsletter
will feature one organization using OpenAFS. This new section is aimed to
give a high-level overview of how many different sites use OpenAFS. Thanks
go out to everyone who gave feedback on which questions to ask when
profiling an AFS site.

Feedback on this newsletter is welcome. The goal is to summarize the
various development efforts and news of OpenAFS for the community. Please
let Jason Edgecombe <jason@rampaginggeek.com> know what you would like to
see out of this newsletter. Any news about AFS-related projects is welcome
and may be submitted to Jason for inclusion in the next newsletter.

The current and past issues of this newsletter are available at
[http://www.openafs.org/newsletter/](http://www.openafs.org/newsletter/)

## General OpenAFS Progress

1.4.12.1 was released on May 25. This was a minor bug fix release to
support Linux 2.6.34, fix a Mac OS issue, and fix a panic. You may stick
with 1.4.12 if you aren't having any issues.

The beginning of a TAP test harness has been added to git.

The driving feature for the 1.6 release is the Demand-Attached File
Server. The 1.6 branch will be created when the DAFS bugs have been fixed
and tested.

## Case Study - Creedon Engineering

In this issue, I would like thank Ted Creedon of Creedon Engineering for
being the first organization to be profiled in the newsletter. --Jason

Jason: What is the name of your organization?

Ted: Creedon Engineering, Lake Oswego, Oregon

Jason: What does it do?

Ted: Electrical/Mechanical Consulting Engineers and software/hardware
engineering. Cyber security..

I frequently travel to remote Alaska, hence the need for AFS

Jason: So Creedon Engineering is located in Lake Oswego, Oregon, USA,
correct?

Ted: Yes

Jason: You are a one-man shop. Correct?

Ted: Yes

Jason: Do you use sub-contractors?

Ted: Yes

Jason: If you use contractors, do they use your AFS space?

Ted: No but in a large project they would

Jason: How many users does your site have?

Ted: 1

Jason: How many cells do you have?

Ted: 1

Jason: How many full-time and part-time people are responsible for AFS support
and in what capacity?

Ted: .0001

Jason: How much data do you store in AFS?

Ted: 500 GB

Jason: How do you use OpenAFS?

Ted: triple server redundant archival backup of irreplaceable photos and
engineering data with world wide secure access from low bandwidth lines.

Jason: You said "low-bandwidth", are you using dial-up, cellular phone
data network, or something more exotic, like satellite?

Ted: I was stuck with 128K out in the Aleutians but its been some time (5
years) since my last experiment.

Jason: How many servers do you have?

Ted: 4 in my office, sometimes more, never less than 3.

Jason: Are they in different locations?

Ted: No, but 2 should relocated.

Jason: How far apart are they?

Ted: Same room - which is bad but I need to get my spare UPS installed in
my home basement.

Jason: Your customer base is spread out. Which states?

Ted: I practice mainly in Alaska

Jason: Do you have customers in Canada or
outside the US?

Ted: No

Jason: Do you work on crude oil or mining equipment?

Ted: Yes, both the BP oil rig at NorthStar and the Red Dog Mine both in
Alaska. Both done in 1996-1998.  Note, any future work would include a task
to set up AFS in my proposal.

Jason: Do you use any other network storage to supplement AFS, like dropbox, or
windows shares?

Ted: Absolutely not, except for ftp - and I used ftp because of the
difficulty and time constraints of setting up AFS clients in Fairbanks.

2 years ago I was stuck with a packaged sftp program used in a very large
consulting firm (24,000 employees, 1,000 world wide offices) and my
project was sabotaged by the internal/external ftp site. AFS would have
been ideal but with an idiot based IT department, made it impossible to
implement.

If you can believe it, transmitting AutoCAD data in that corporate
environment was very primitive - to the point where productivity and
drawing/specification writing is measurably affected - my guess is by 25%
\- not to mention folks working in different offices working on the wrong
set of drawing revisions.

One issue is that tokens would be set up for 1 month lifetime. The users
are in the Construction business, not sophisticated.

Jason: Is AFS the only networked filesystem that you use?

Ted: Yes, but occasionally a shared drive

Jason: If not, what are the others, and how do they compare/contrast?

Ted: windows shares and/or samba are a pain and are insecure, also lack
backup capability.

Jason: Why do you use the other filesystems?

Ted: convenience - but rarely

Jason: Is your investment in AFS increasing or decreasing?

Ted: stable, unless you consider making new drivers/kernels an investment..

AFS is perfect for the traveling  "Road Warrior"..  And I don't have to
worry about military photos  and financial data  security.



## Events

### Annual Best Practices Workshop

The Seventh Annual International AFS & Kerberos Best Practices Workshop
was held May 24-28 at the University of Illinois. Participants enjoyed
socialising in the evenings after spending their days learning and sharing
experiences. In addition to the usual tutorials, 2 and a half days of
presentations followed, including Phillip Moore's keynote, "Global
Filesystems in the Real World: Comparing experiences with AFS and
NFS". Phil contrasted his previous work with AFS to his current work with
the OpenEFS system that runs on top of NFS now but could be used above
OpenAFS.

Other talks included topics such as tools, development, deployment,
debugging, and the future of OpenAFS.

Slides for the talks are available linked from
http://workshop.openafs.org/afsbpw10/schedule.html

### European AFS Conference

The date for the 3rd European AFS & Kerberos Conference has been set. The
conference will take place in Pilsen, Czech Republic, from September 13 to
September 15, 2010. More details are forthcoming and will be posted at
[http://afs2010.civ.zcu.cz](http://afs2010.civ.zcu.cz). The conference is being hosted by Centre for
Information Technology, University of West Bohemia.

The first Call for Participation has been announced. Please see
[http://afs2010.civ.zcu.cz/cfp.php](http://afs2010.civ.zcu.cz/cfp.php) for more information.

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
review. The only outstanding comment involves a typo ("which which").

\--Derrick Brashear

### AFS Callback Extensions

[http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo](http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo)

Status: Active - Waiting on RPC refresh

Extended callback implmementations for Unix and Windows have been
submitted to gerrit and have received initial review.  Ideally this code
will soon be able to merge, after branch for 1.6.  It's expected that its
rpc refresh dependencies will be resolvable at that point.

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

See the Per-File ACLs section for more info.

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

Status: Second Draft

Last Update: April 6, 2010

As new forms of metadata are added to AFS volumes, we are running into
limitations with the wire volume metadata structures used by the volume
server.  This internet draft aims to standardize a tag-length-value (TLV)
encoding for arbitrary AFS volume metadata.  A new version of this draft
was released on April 6th, 2010.  Everyone is invited to review and
comment on this document.  Comments should be sent to the
afs3-standardization@grand.central.org mailing list.

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

An important fix from Simon in gerrit 1832 has been merged. Gerrit 1562
(ihandle positional I/O) is still being reviewed, but has made much
progress. The salvager threadsafe changes (gerrit 1865 and its
dependencies) are also still undergoing review, but have seen much recent
change. There is one remaining known DAFS bug involving saving and
restoring fileserver state that was mentioned at the workshop, but an
underlying cause is still being looked into.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Many of the known deficiencies in the OpenAFS man pages have been fixed in
the current master branch, although some vos flags and backup commands are
not yet documented.  Two demand-attach binaries still need man pages.

The first chapter and part of the second chapter of the OpenAFS
Administration Guide have been revised.

### Userspace cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

Immediately following the libuafs presentation I gave at BPW 2010, the
perl libuafs bindings were submitted in gerrit 2048 (and 2049). There are
still at least a couple of issues to work out: specifically PIC and
packaging issues. After resolving those, I expect the next big things to
be seen out of this are krb5 authentication support and python bindings,
if the BPW discussions are any indication. Thanks to all who listened to
my talk, and provided feedback.

\--Andrew

### Kerberos v5 and multiple encryption types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

I'll be making a snapshot of openafs "m85" tonight (Ed: June 9), based exactly
on 1.5.61.  Next few goals will probably be:

- update to 1.5.74/75
- improve patch splitout process
- move to git(devel/temp)
- test on windows
- implement anonymous callback protection

\--Marcus Watts



### Google Summer of Code 2010

OpenAFS received five slots for the 2010 Google Summer of Code.

Go to [http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs](http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs)
for more information about the GSoC projects.

#### Unix Support for AppleDouble files (Posix Attributes)

Student Developer: Kelli Ireland <kelli.ireland@gmail.com>

Mentor: Derrick Brashear <shadow@gmail.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html)

Kelli Ireland (Derrick's student) kicked off the official start of the
GSoC program by attending the AFS/Kerberos workshop.  She is working
on extended attribute support, specifically for AppleDouble files (.\_
files, aka dot-underscore files).  She is currently working on a
dot-underscore file parser.

#### Encrypted Storage

Student Developer: Sanket Agarwal <sanket@sanketagarwal.com>

Mentor: Simon Wilkinson <sxw@inf.ed.ac.uk>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017424.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017424.html)

Abstract:

The AFS protocol offers encryption for data transport from client to
server. However, that data is stored on the server in cleartext, where it
can potentially be read by the administrators of that server. This poses a
real world problem for organisations who wish to outsource the provision
of their file storage, whilst keeping their data confidential. This
project would augment the existing AFS client to support encrypting data
blocks before sending them to the file server.

#### Apply the kafs project of OpenAFS

Student Developer: Lei Wang <wang840925@gmail.com>

Mentor: David Howells <dhowells@redhat.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-April/017493.html](https://lists.openafs.org/pipermail/openafs-devel/2010-April/017493.html)

The progress of kafs project is good.  We have implemented part of the DNS
support for kafs sub-project.  We created a common module in the linux kernel
for handling the DNS queries, derived from code in the CIFS module.  It should
be finished in several days.

\--Lei

#### Port OpenAFS to NetBSD

Student Developer: Matt Smith <matt.j.sm@gmail.com>

Mentor: Matt Benjamin <matt@linuxbox.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html)

Current status is that I've rebased the NetBSD port at OpenBSD, with
various adaptations targeting NetBSD 4.x.  Matt S. is getting up to speed,
starting with work on the NetBSD LKM on NetBSD 5.0.2.

\--Matt Benjamin

#### An open source version of the Microsoft Safe String Library

Student Developer: Jonas Sundberg <jonas.sundberg@gmail.com>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html)

Work is progressing a bit ahead of the proposed timeline. Both standard
and wide character versions of Cat, CatN, Copy, CopyN and Length are all
implemented and have some unit testing for the basic functionality. Wide
character versions of the functions were more similar to the standard
character versions than I had expected, so much of that work has already
been done ahead of time. Initial untested drafts of Gets, Printf and
VPrintf have also been implemented.

The things to do next will be to extend the tests to cover the new
functions and working on implementing the extended versions of all
functions, as well as unit tests for these.

\--Jonas

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Active Directory Backend for Ptserver - November 2009
- Extended Callback Information - January 2010
- Disconnected AFS support - February 2010
- Virtual Machine Images - April 2010
- Mac OS X OpenAFS Preference Pane - April 2010
- S3 Front-end for AFS - May 2010
- Rx OSD integration & Raw Vicep Access in Clients - May 2010
- Per-File ACLs - May 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 62 (last month: 35)

    Patches merged into the master branch:
    Month   Number of Commits
    2010-06   42 (Partial month)
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
    2009-07  181

    Patches merged into the stable branch:
    Month   Number of Commits
    2010-05  16
    2010-04   4
    2010-03  28
    2010-02  35
    2010-01  11
    2009-12  92
    2009-11  21
    2009-10   7
    2009-09   8
    2009-08  17
    2009-07   5

### Patches waiting for review

    Date       Author          Change# Description
    2010-06-10 Derrick Brashear (2117) unix cm log path mtu warning when retrying
    2010-06-10 Derrick Brashear (2116) unix cm activate mtu pings
    2010-06-10 Derrick Brashear (2115) rx mtu ping handling
    2010-06-10 Derrick Brashear (2114) path mtu don't track nonsequenced packets
    2010-06-10 Derrick Brashear (2113) rx checkcall kill extra indirection on call for conn
    2010-06-10 Derrick Brashear (2112) idle dead time track less
    2010-06-10 Andrew Deason    (2107) ubik: Drop dbase versionLock during I/O and sleeps
    2010-06-09 Andrew Deason    (2106) vlserver: Allow reading during ubik writes
    2010-06-09 Andrew Deason    (2105) vlserver: Access cache via vl_ctx
    2010-06-09 Andrew Deason    (2104) vlserver: Add a struct for trans-specific data
    2010-06-09 Andrew Deason    (2103) ubik: add interface for reading during write locks
    2010-06-09 Andrew Deason    (2108) ubik: Protect ubik_servers in urecovery_Interact
    2010-06-07 Matt Benjamin    (2053) windows  cm_BeginDirOp add flags (nobuildtree)
    2010-06-07 Jeffrey Altman   (2089) Convert from using nvldbentry to uvldbentry
    2010-06-07 Michael Meffie   (1562) ihandle positional read and write
    2010-06-06 Jeffrey Altman   (1742) Make -printuuid an option for all vos commands
    2010-06-06 Jeffrey Altman   (2090) Remove 'register' from src/volser
    2010-06-04 Russ Allbery     (2026) Rework the Kerberos Autoconf probes
    2010-06-04 Matt Benjamin    (2071) VICE error table
    2010-06-04 Simon Wilkinson  (1824) Use git describe to determine build version
    2010-06-04 Michael Meffie   (215) rxdebug: show delayed abort packet count for rx peers
    2010-06-04 Russ Allbery     (2082) Fix aklog warnings when building with Heimdal
    2010-06-04 Russ Allbery     (2083) Document vos listaddrs -host and -uuid
    2010-06-02 Andrew Deason    (1869) Remove the global tempHeader/stuff structures
    2010-06-02 Andrew Deason    (1863) Provide an abstract thread pool object
    2010-06-02 Andrew Deason    (1865) Allow salsrv salvage I/O to occur in parallel
    2010-06-02 Andrew Deason    (1864) Parallel I/O extensions to namei backend
    2010-06-02 Andrew Deason    (1862) Provide an abstract work queue object
    2010-06-01 Andrew Deason    (2048) Add AFS::ukernel libuafs perl bindings
    2010-05-27 Andrew Deason    (2049) Add documentation for AFS::ukernel
    2010-05-27 Matt Benjamin    (2011) Extended callback implementation
    2010-05-26 Rod Widdowson    (2027) Make file offsets in vldb layout unsigned ints.
    2010-05-26 Andrew Deason    (1979) Mention that -fakestat fakes local cellular mounts
    2010-05-26 Derrick Brashear (1959) bosserver force corefiles
    2010-05-17 Christof Hanke   (1975) Example usage of the tabular output in libcmd
    2010-05-17 Simon Wilkinson  (1823) Linux: Remove the BKL
    2010-05-17 Christof Hanke   (1970) Add output-table to libcmd
    2010-05-17 Rainer Toebbicke (1311) Lockless path through afs_linux_dentry_revalidate
    2010-05-17 Andrew Deason    (1940) Reuse existing non-linktable special inodes
    2010-05-16 Jeffrey Altman   (1965) Windows: add BSD getopt to afsutil.lib
    2010-05-12 Michael Meffie   (1949) xstat: fix large integer output
    2010-05-08 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2010-05-07 sanket           (1777) Add xml functionality to the vos examine command
    2010-05-06 Rainer Toebbicke (1903) Do not corrupt volume linktable when special file already exists
    2010-05-05 Derrick Brashear (1906) fix dumptool on macos
    2010-05-04 Rainer Toebbicke (1902) patch cbd_printCBcrash - harden callback debugging
    2010-05-03 Derrick Brashear (1872) no fs sa /afs in dynroot mode
    2010-04-28 Derrick Brashear (1852) mariner log messages for creating and removing files
    2010-04-19 Michael Meffie   (1786) viced: host hash address collisions
    2010-03-23 Derrick Brashear (1625) preliminary support for pinned vcaches
    2010-03-17 Derrick Brashear (1553) dynamic volume allocation
    2010-02-15 Michael Meffie   (1001) return an error from afs_readdir when out of buffers
    2010-02-03 Dan Hyde         (1191) runningCalls: VOL_COUNT_LOCK vs VTRANS_LOCK
    2010-02-03 Derrick Brashear (1172) linux mmap anti-deadlock shouldn't break StoreAllSegments
    2010-02-03 Derrick Brashear (1201) basic kernel event system for afs cm
    2010-01-20 Simon Wilkinson  (1074) Unix CM: Include memcache's tiov in rxfs_context
    2009-11-29 Andrew Deason    (875) Make ubik use unsigned addresses
    2009-09-09 Matt Benjamin    (435) clear stat flag on renamed directories
    2009-08-29 Matt Benjamin    (376) K5SSL by Marcus Watts
    2009-07-29 Michael Meffie   (147) Fix bosserver directory creation
    2009-07-24 Hartmut Reuter   (70) preparing rxosd integration: change in AFSFetchStatus



### Patches merged into the master branch

    Date       Author          Change# Description
    2010-06-10 Matt Benjamin    (2097) rx service specific data
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
    2010-05-30 Rod Widdowson    (1991) Rewrite vldb_check -fix
    2010-05-30 Rod Widdowson    (1990) Add bounds checking prior to IOs in vldb_check
    2010-05-30 Russ Allbery     (2059) Reformat chapter two of the OpenAFS Administration Guide
    2010-05-30 Russ Allbery     (2063) Add a sample test program to the new test suite
    2010-05-30 Russ Allbery     (2062) Import C TAP Harness 1.2 as a testing harness
    2010-05-30 Russ Allbery     (2061) Add src/tests/OpenAFS/Dirpath.sh to .gitignore
    2010-05-30 Russ Allbery     (2060) Clean up warnings in the tests directory
    2010-05-30 Marc Dionne      (2064) Linux: 2.6.35 - fsync no longer takes a dentry
    2010-05-29 Rainer Toebbicke (2057) Typo made sysctl table invisible
    2010-05-28 Derrick Brashear (1986) viced: kill console use
    2010-05-28 Russ Allbery     (2045) Comprehensive edit of chapter one of the Administration Guide
    2010-05-28 Russ Allbery     (2044) Reformat chapter one of the OpenAFS Administration Guide
    2010-05-28 Russ Allbery     (2041) Add k_haspag to libkopenafs
    2010-05-28 Andrew Deason    (2047) libuafs: Add uafs_Init compat function
    2010-05-28 Russ Allbery     (2051) Make all the default target in libadmin samples and test
    2010-05-28 Russ Allbery     (2050) Clean up warnings in libadmin/bos/afs_bosAdmin.c
    2010-05-27 Russ Allbery     (2043) Clean up the introduction to the Administration Guide
    2010-05-27 Andrew Deason    (2046) libuafs: Remove afsd symlink in setup
    2010-05-27 Derrick Brashear (2042) background daemon don't wipe code before it gets used
    2010-05-27 Russ Allbery     (2036) Flesh out NEWS for recent work
    2010-05-27 Russ Allbery     (2037) Update Debian packaging to 1.5.74.1-1
    2010-05-27 Russ Allbery     (2040) Fix compilation of the imported config_file.c parser
    2010-05-27 Marc Dionne      (2039) scout.c: only declare width once
    2010-05-26 Andrew Deason    (1546) Protect ubik cache accesses
    2010-05-26 Russ Allbery     (2038) Fix syntax error when supergroups are not enabled
    2010-05-26 Asanka Herath    (2032) Add /dest and /obj to .gitignore
    2010-05-26 Russ Allbery     (2031) Remove references to IBM AFS
    2010-05-26 Derrick Brashear (2010) avoid nat ping for authenticated connections
    2010-05-26 Russ Allbery     (2030) Remove references to AFS Product Support in -oktozap
    2010-05-26 Russ Allbery     (2029) Remove -rebuildDB flag to ptserver
    2010-05-26 Russ Allbery     (2028) Remove documentation of kaserver -fastKeys
    2010-05-26 Simon Wilkinson  (1935) Add an OpenAFS config file parser
    2010-05-26 Michael Meffie   (1951) scout: adjustable column widths
    2010-05-26 Derrick Brashear (2024) dumpstuff nbytes can't exceed 32 bits
    2010-05-26 Russ Allbery     (2025) Synchronize LICENSE files
    2010-05-25 Matt Benjamin    (2017) windows  handle NONODE case uniformly in cm_BPlusDirDeleteEntry
    2010-05-25 Simon Wilkinson  (1934) Import of code from heimdal
    2010-05-25 Simon Wilkinson  (1971) Autoconf : Kill dead code
    2010-05-25 Derrick Brashear (2021) fs getserverprefs needs a larger buffer
    2010-05-25 Simon Wilkinson  (2002) Linux: Disable syscall probes if we have keyrings
    2010-05-25 Andrew Deason    (1920) vol, volser, and viced type fixes
    2010-05-25 Russ Allbery     (2020) Add libafs_tree to .gitignore
    2010-05-25 Russ Allbery     (2019) Fix libafs_tree's cross-architecture support
    2010-05-25 Russ Allbery     (2018) Postmoderize use of AC_CHECK_TYPE
    2010-05-25 Russ Allbery     (2015) Update fs {get,set}serverprefs documentation for DNS
    2010-05-25 Derrick Brashear (1851) report server address when known for afs warnings
    2010-05-24 Derrick Brashear (2016) getcapabilities avoid panic when cell is not filled
    2010-05-23 Rod Widdowson    (1983) Read volume at correct address when looking for broken forward links.
    2010-05-23 Simon Wilkinson  (2014) Autoconf: Tidy up resolver retrans retry test
    2010-05-23 Matt Benjamin    (2013) windows  map lstat to _stat (mrafsStyleLogs)
    2010-05-23 Russ Allbery     (1938) Update bos addkey/listkeys and KeyFile man pages for asetkey
    2010-05-22 Benjamin Kaduk   (2012) Do not lie about needing Giant
    2010-05-19 Marc Dionne      (2000) Linux: remove unused label
    2010-05-19 Simon Wilkinson  (1392) More warnings cleanup
    2010-05-19 Simon Wilkinson  (1993) Linux: Use positional r/w, not llseek
    2010-05-19 Derrick Brashear (1992) dafs: don't restart for new binaries using mrafs scanner time
    2010-05-19 Simon Wilkinson  (1878) Unix CM: Use macros for process name and id access
    2010-05-19 Derrick Brashear (1984) mrafs logs don't clobber existing logs
    2010-05-19 Benjamin Kaduk   (1989) Do not sleep in FBSD's getevent()
    2010-05-18 Simon Wilkinson  (1913) Always include afsconfig.h in autogenerated files
    2010-05-18 Matt Benjamin    (1982) linux PageCheck may be PageFsMisc
    2010-05-18 Derrick Brashear (1985) darwin afs.conf: growlagent example
    2010-05-18 Matt Benjamin    (1981) linux include osi_compat.h in rx/LINUX/rx_knet.c
    2010-05-18 Simon Wilkinson  (1977) Fileserver: Don't sync every 10 seconds
    2010-05-18 Derrick Brashear (1978) rx: work harder to notice and handle MorePackets request
    2010-05-17 Simon Wilkinson  (1974) Autoconf: Use AC_CACHE_CHECK
    2010-05-17 Derrick Brashear (1961) afsprefs: clarify restart requirement
    2010-05-17 Rod Widdowson    (1955) Clean up logging from vldb_check.
    2010-05-17 Rod Widdowson    (1964) Stop overanxious htonl in vldb_check -fix
    2010-05-17 Simon Wilkinson  (1834) Demand Attach: Volumes and vnodes are different
    2010-05-17 Simon Wilkinson  (1833) Demand Attach: Simplify __VVGC_entry_cl_add
    2010-05-17 Simon Wilkinson  (1832) Demand-Attach: Remove dangerous trailing else
    2010-05-17 Benjamin Kaduk   (1969) Enable PutVCache for FBSD80 and higher
    2010-05-17 Benjamin Kaduk   (1968) Kill FBSD4X with fire
    2010-05-17 Simon Wilkinson  (1973) Autoconf: Use AC_CHECK_MEMBERS
    2010-05-17 Simon Wilkinson  (1972) Autoconf: Use a standard test for socklen_t
    2010-05-16 Benjamin Kaduk   (1967) Do not try to increase the refcount of a NULL vnode
    2010-05-16 Andrew Deason    (1966) Solaris: do not call VFS_RELE with GLOCK
    2010-05-14 Hartmut Reuter   (1958) Don't use afs_linux_storeProc with memory cache, it only works with disk cache.
    2010-05-12 Andrew Deason    (1957) Solaris: stop NetIfPoller on shutdown
    2010-05-12 Jeffrey Altman   (1956) Windows: move afsconfig.h / param.h to afscred.h
    2010-05-12 Jeffrey Altman   (1954) Windows: netidmgr_plugin must include afsconfig.h
    2010-05-12 Jeffrey Altman   (1953) Fix missing semicolon in non-AFS_NAMEI_ENV builds vol/nuke.c
    2010-05-12 Jeffrey Altman   (1952) Windows: fix consistency of afsconfig-windows.h
    2010-05-12 Derrick Brashear (1926) inlinebulk analyze errors
    2010-05-12 Andrew Deason    (1238) Consolidate code for reading/writing vol headers
    2010-05-12 Jeffrey Altman   (1928) Rx: prevent rx_rpc_stats mutex from being a global bottleneck
    2010-05-12 Jeffrey Altman   (1950) Windows: Add support for NetWkstaGetInfo levels 101 and 102
    2010-05-12 Jeffrey Altman   (1939) Windows: Prevent overflow during percent used calc in Explorer Shell Ext
    2010-05-12 Jeffrey Altman   (1937) Windows: use system CreateUuid instead of afs variant
    2010-05-12 Jeffrey Altman   (1931) Windows: Freelance vs ACLs
    2010-05-12 Jeffrey Altman   (1930) Make afsio be useful on Windows and fix bugs
    2010-05-12 Jeffrey Altman   (1918) Windows: RXAFS_InlineBulkStat errors must be processed via cm_Analyze
    2010-05-11 Michael Meffie   (1948) Linux: missing configure test
    2010-05-11 Simon Wilkinson  (1919) Remove intptr.m4
    2010-05-11 Derrick Brashear (1941) vnode alloc bitnumber returns bitnumber
    2010-05-11 Andrew Deason    (1927) vlserver: prevent duplicate IPs via ChangeAddr
    2010-05-10 Jeffrey Altman   (1936) Windows: define HAVE_SSIZE_T
    2010-05-09 Simon Wilkinson  (1933) Add a list of files to import from Heimdal
    2010-05-09 Simon Wilkinson  (1932) Add a tool to import external repositories
    2010-05-09 Jeffrey Altman   (1929) Windows: fs.c requires size_t len not int len
    2010-05-07 Russ Allbery     (1915) Include common param file for Linux alpha builds
    2010-05-07 Benjamin Kaduk   (1925) Define osi_procname for FBSD
    2010-05-07 Benjamin Kaduk   (1923) Actually fix build for FBSD80 after vcache refactoring
    2010-05-07 Benjamin Kaduk   (1691) Add entries for FBSD 8.1 and 9.0
    2010-05-06 Simon Wilkinson  (1914) Modernise use of AC_CHECK_TYPE
    2010-05-06 Antoine Verheijen (1910) OpenBSD: Use osi_obsd_Free() for all releases of OBSD
    2010-05-06 Antoine Verheijen (1909) OpenBSD: Use FREE instead of KFREE
    2010-05-06 Simon Wilkinson  (1912) Always include afsconfig.h
    2010-05-06 Marc Dionne      (1908) Fix typo: LockType -> lockType
    2010-05-05 Derrick Brashear (1895) fcntl write lock on readonly file error fix
    2010-05-05 Derrick Brashear (1907) afsdump scan kill warnings
    2010-05-04 Derrick Brashear (1904) freebsd vcache splitting fallout
    2010-05-04 Tharidu Fernando (1736) Windows: Secure C String usage in src\WINNT\afsd\fs.c
    2010-05-04 Jonathan A. Kollasch (1738) NetBSD 5.0 support.
    2010-05-04 Andrew Deason    (1899) Solaris: shutdown in freevfs, not unmount
    2010-05-04 Simon Wilkinson  (1881) Refactor afs_NewVCache
    2010-05-04 Andrew Deason    (1880) Solaris: prevent AFS umount while busy
    2010-05-04 Andrew Deason    (1879) Solaris: return ENOTSUP for force-unmounts
    2010-05-04 Michael Meffie   (1896) pts mem -expandgroups and -supergroups examples
    2010-05-04 Antoine Verheijen (1898) OpenBSD: Fix bug in setpag() when group list is empty
    2010-05-04 Antoine Verheijen (1897) Fix pattern to detect i386-based OpenBSD system type
    2010-05-03 Asanka Herath    (1797) Windows: Show configuration pages for all types of MSI installations
    2010-05-03 Andrew Deason    (1860) Provide a queue_NodeInit() interface
    2010-05-02 Jeffrey Altman   (1894) Windows: Restructure cm_LookupInternal addition of Freelance entries
    2010-05-02 Jeffrey Altman   (1893) Windows: Permit BPlus tree lookups within cm_ApplyDir
    2010-05-02 Jeffrey Altman   (1892) Windows: Prevent cm_FreelanceAddSymlink from creating a symlink ending in a dot
    2010-05-02 Jeffrey Altman   (1891) Windows: normalize error codes from cm_FreelanceAddSymlink
    2010-05-02 Jeffrey Altman   (1890) Windows: Force rebuilding Freelance directory in AddMount and AddSymlink
    2010-05-02 Jeffrey Altman   (1889) Windows: normalize return codes from cm_FreelanceAddMount
    2010-05-02 Jeffrey Altman   (1888) Windows: use cm_noteLocalMountPointChange whenever fakeDirVersion is changed
    2010-05-02 Jeffrey Altman   (1887) Windows: add locked parameter to cm_noteLocalMountPointChange
    2010-05-02 Jeffrey Altman   (1886) Windows: remove unused code from cm_FollowMountPoint
    2010-05-02 Jeffrey Altman   (1885) Windows: initialize to zero Freelance fake root directory
    2010-05-02 Jeffrey Altman   (1884) Windows: make cm_BPlusDirFoo public
    2010-05-02 Jeffrey Altman   (1883) Windows: correct "fs quota" pioctl validation check
    2010-05-02 Jeffrey Altman   (1882) Windows: getAFSServer wrong variable used in uncompiled code
    2010-05-02 Jeffrey Altman   (1876) Windows: add 'locked' flag to cm_FSync and call when dropping write locks
    2010-05-02 Jeffrey Altman   (1875) Windows: FlushFile ioctl should call cm_FSync, not buf_CleanVnode

### Patches merged into the stable branch

    Date       Author          Change# Description
    2010-05-26 Michael Meffie   (1951) scout: adjustable column widths
    2010-05-24 Antoine Verheijen (1917) OpenBSD: Use FREE instead of KFREE
    2010-05-24 Antoine Verheijen (1916) OpenBSD: Add missing header files
    2010-05-20 Simon Wilkinson  (2009) fix other oldtvix typo
    2010-05-20 Simon Wilkinson  (2008) Initialize oldvtix
    2010-05-20 Simon Wilkinson  (2004) Recover from afs_GetVolSlot errors
    2010-05-20 Derrick Brashear (2003) macos 32 bit platform user address transform
    2010-05-19 Anders Kaseorg   (1988) Linux: replace invalidate_inode_pages
    2010-05-18 Antoine Verheijen (1911) OpenBSD: Use osi_obsd_Free() for all releases of OBSD
    2010-05-17 Michael Meffie   (1945) prdb_verify -rebuild with supergroups fix
    2010-05-16 Andrew Deason    (1943) Solaris: prevent AFS umount while busy
    2010-05-11 Andrew Deason    (1944) Solaris: shutdown in freevfs, not unmount
    2010-05-11 Andrew Deason    (1942) Solaris: return ENOTSUP for force-unmounts
    2010-05-05 Dan Hyde         (1843) viced-host-uuid-and-addr-hashing-corrections-20090530
    2010-05-05 Antoine Verheijen (1900) Fix pattern to detect i386-based OpenBSD system type
    2010-05-05 Antoine Verheijen (1901) OpenBSD: Fix bug in setpag() when group list is empty


