---
title: OpenAFS Newsletter, Volume 2, Issue 9, September 2010
layout: page
category: newsletter
permalink: /newsletter/newsletter-2010-09-volume002-issue09.html
---

# OpenAFS Newsletter, Volume 2, Issue 9, September 2010

Welcome to the September issue of the OpenAFS newsletter. This newsletter
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

The voting for the chairs of the afs3-standardization group is closed.
Preliminary results show Hartmut Reuter and Doug Engbert as the two chairs
of the AFS Protocol Standardization group. As the candidate with the most
votes, Hartmut will serve a full two-year term and Doug will serve a
one-year half-term. Official results will be confirmed later.

1.5.77 was released on September 8.  It may be downloaded from
[http://www.openafs.org/release/openafs-1.5.77.html](http://www.openafs.org/release/openafs-1.5.77.html) 1.5.77 includes some
changes to the RPM packaging where the demand-attach and traditional
fileserver binaries are both included in the same RPM.

The 1.6 branch was created in git on August 17. The 1.6 branch name is
openafs-stable-1\_6\_x.

Marc Dionne verified that OpenAFS no longer produces lots of log noise in
RedHat Enterprise Linux 6 Beta. [https://bugzilla.redhat.com/show\_bug.cgi?id=584901](https://bugzilla.redhat.com/show\_bug.cgi?id=584901)

## Case Study - PDC

In this issue, I would like thank Harald Barth from the Center for Parallel
Computing at the Royal Institute of Technology in Stockholm, Sweden for
being profiled in the newsletter. --Jason

Jason: What is the name of your organization?

Harald: Our organization is the Center for Parallel Computing at the Royal
Institute of Technology, Stockholm, Sweden. The swedish abbreviation is
"PDC". The numbers given are for our center only because I do not have
accurate numbers for other AFS cells at kth.se. There are at least 3 other
AFS cells than pdc.kth.se at the Royal Institute of Technology.

Jason: What does it do?

Harald: PDC does provide High Performance Computing for academic users in
Sweden and within joint projects within the EU.

Jason: How many users does your site have?

Harald: 1600, approx 250 active.

Jason: How many cells do you have?

Harald: pdc.kth.se. Some of the users have home directories in nada.kth.se.

Jason How many full-time and part-time people are responsible for AFS
support and in what capacity?

Harald: First line helpdesk 1.5 persons, can give basic support. More
complicated problems take part of my time.

Jason: How much data do you store in AFS?

Harald: 27TB

Jason: Do you use contractors or vendors to augment your workforce?

Harald: Rarely

Jason: How do you use OpenAFS?

Harald: All users have $HOME in AFS. AFS is used for all storage with the
exeption of some HPC data which is in Lustre and some Cern Tier 1 storage
which is in their storage solution.

Jason: What type of network bandwidth is there between your client and
servers?

Harald: 1Gbit, starting to experiment with 10Gbit. But of course there may
be clients somewhere else in the world with less bandwidth.

Jason: How many servers do you have?

Harald: Too few (as HPC researchers normally do not realize how much I/O
their programs actually utilize). The current number is 12, hopefully more
servers in the future, not to increase space but to increase throughput
and availability.

Jason: Are they in different locations? How far apart are they?

Harald: Within the same building.

Jason: How spread out are your users? Same city, region, country?

Harald: Country. The size of Sweden/Europe RTT to the furthest users is
around 15ms. Typical users are closer than 5ms.

Jason: Are your users spread all over Sweden? Europe? how many kilometers
away are your users?

Harald: Most users are of course locally, but we have never restricted
access from any other place on the Internet. As my users live and work
over all of Sweden, they access their data from their desktop computers as
well. Sweden is about the area and form of CA (slightly larger, but the
extreme north of Sweden is not populated anyway ;-). It's approximate
900km from Stockholm to my most northern university users in Luleå. Other
users in Europe are more rare, not because they can not access the data
through AFS but because they normally use scp anyway.

Jason: Do you use any other network storage to supplement AFS, like
dropbox, or windows shares?

Harald: Lustre, if a file system only visible within one cluster
classifies as "network storage".

Jason: Is AFS the only networked filesystem that you use?

Harald: See above.

Jason: If not, what are the others, and how do they compare/contrast? Why
do you use the other filesystems?

Harald: Lustre is in some aspects faster, but has by far not as good
uptime as AFS.

Jason: Is your investment in AFS increasing or decreasing?

Harald: Increasing, but not as much as investments in Lustre.

Jason: Is there anything else that you would like to say?

Harald: Recently, PDC aquired a Cray cluster which runs some SuSE modified
by Cray. It is our intention to bring AFS to that system, but so far we
have not aquired enough information about the internal to make it happen.

## Events

### European AFS Conference

The European AFS & Kerberos Conference 2010 took place in Pilsen, Czech
Republic, from September 13 to September 15. The conference was hosted by
Centre for Information Technology, University of West Bohemia.  The
conference was friendly and well-organized.

A summary of the conference will be included in next month's newsletter.
The slides are available at [http://afs2010.civ.zcu.cz/agenda.php](http://afs2010.civ.zcu.cz/agenda.php) and
the pictures are here:
[http://afs2010.civ.zcu.cz/download/afs-data/Gallery/Album/index.html](http://afs2010.civ.zcu.cz/download/afs-data/Gallery/Album/index.html)

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

Status: Seventh Draft

Last update: August 31, 2010

I hope it's done.

The Kerberos 5 name type has been removed; The GSSAPI name type with
the Kerberos OID will be used for all Kerberos 5 users. Consensus
seems near.

\--Derrick

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
which will be frequently re-based, is at
http://github.com/your-file-system/openafs-rxgk

Last Update: Jan 9, 2010

### AFS3 ACL Rights

[http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions](http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions)

Status: Second draft

Last update: January 13, 2010

We're waiting for the afs3-standardization structure to solidify before
proceeding with this. So, no progress right now.

\--Andrew Deason

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

Status: Fourth Draft

Last Update: August 4, 2010

The other week I submitted a new draft to the IETF which implements
the aforementioned changes (as well as a few others).  The new draft
is available at the following URLs:

- [http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv-03](http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv-03)
- [http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-03.html](http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-03.html)
- [http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-03.xml](http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-03.xml)
- [http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-02-03.xml.diff](http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-02-03.xml.diff)
- [file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.txt](file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.txt)
- [file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.html](file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.html)
- [file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.xml](file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.xml)
- [file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-02-03.xml.diff](file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-02-03.xml.diff)

The complete revision history is as follows:

- split unsigned 64-bit type down into several more descriptive types
that allow the TLV data stream to be more self-describing.
- add a signed 64-bit integer type to allow for relative timestamps
- now that we have more descriptive types, use them in a number of places
- change AFSVOL\_TLV\_TAG\_VOL\_TRANS\_CALL\_VALID into a boolean type payload
- make sure rxgen can parse the XDR in the appendix
- make sure generated C code compiles and links
- add in-text cites for AFS3-VVL, AFS3-FSCM, DAFS, and OSD.
- provide motivations for GetCapabilities RPC
- provide protocol semantic definitions for each newly allocated capability bit
- allocate AFSVOL\_TLV\_FLAG\_MORE bit to notify caller when we can't
send all tags due to AFSVOL\_TLV\_TAG\_MAX length limit

Any comments or feedback are appreciated.

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

A fix for improving startup times with a large number of volumes was
submitted to gerrit (2648), as have a couple of small fixes related to
setting -vhashsize (2649, 2650). The fix for salvaging attached volumes
(2329) and the fix to conditionally run fssync-debug (2480) have still not
been merged, but getting them in will be worked on shortly. Some
prerequisites for salvageserver improvements have been merged (2250,
1869).

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

The 2TB partition limit was removed from the man pages for the 1.4.x
series.

### Per-File ACLs

Project Contacts:

- Marc Dionne <marc.c.dionne@gmail.com>

I've re-activated this work over the past few weeks:

- The code on github (http://github.com/mdionne/openafs) has been rebased to
the current master branch.  The per\_file branch is the branch of interest.
- I've been experimenting with cross-directory hard links, and have a
functional implementation.  This is part of the published code on github
in the same branch, on top of the rest of the per file changes.
- Continuing work on an RFC style document to present the proposed protocol
changes, for eventual submission to the AFS standardization process

\--Marc

### Disconnected AFS support

Project Contacts:

- Simon Wilkinson <sxw@inf.ed.ac.uk>
- Dragos Tatulea <dragos.tatulea@gmail.com>

Because Disconnected AFS will be built in by default in the forthcoming
1.6 release, this section will be dropped from future newsletters.

### Google Summer of Code 2010

OpenAFS received five slots for the 2010 Google Summer of Code.

Go to [http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs](http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs)
for more information about the GSoC projects.

#### Unix Support for AppleDouble files (Posix Attributes)

Student Developer: Kelli Ireland <kelli.ireland@gmail.com>

Mentor: Derrick Brashear <shadow@gmail.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html)

No update. --Ed.

#### Encrypted Storage

Student Developer: Sanket Agarwal <sanket@sanketagarwal.com>

Mentor: Simon Wilkinson <sxw@inf.ed.ac.uk>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017424.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017424.html)

By the last newsletter, basics of chunking and extents had been
implemented along with basic file functions of
Reading/Writing/Moving/Removing and metadata file creation/deletion.

Present focus is to integrate the code with hcrypto library port in
OpenAFS.  As the port still dinkering in terms of usablity I am presently
working on some working patches in gerrit to adapt my code to use the
hcrypto library.

After this integration is complete, the task will be to manage user keys.

\--Sanket

#### Apply the kafs project of OpenAFS

Student Developer: Wang Lei <wang840925@gmail.com>

Mentor: David Howells <dhowells@redhat.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-April/017493.html](https://lists.openafs.org/pipermail/openafs-devel/2010-April/017493.html)

Wang's patches have made it upstream:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=search;s=wang840925@gmail.com;st=author](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=search;s=wang840925@gmail.com;st=author)

where they've been made use of by CIFS and NFS in addition to kAFS.

\--David

#### Port OpenAFS to NetBSD

Student Developer: Matt Smith <matt.j.sm@gmail.com>

Mentor: Matt Benjamin <matt@linuxbox.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html)

There still exists some issue where afsd fails to properly return the
contents of the /afs dir when trying to view it. At the moment, progress
has halted with that and I'm working on merging my changes with
origin/master to push up what has been completed so far.

\--Matt Smith

#### An open source version of the Microsoft Safe String Library

Student Developer: Jonas Sundberg <jonas.sundberg@gmail.com>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html)

The project has been completed successfully and is posted at
https://www.ohloh.net/p/libstrsafe/.

\--Jeffrey Altman

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Active Directory Back-end for Ptserver - November 2009
- Extended Callback Information - January 2010
- Mac OS X OpenAFS Preference Pane - April 2010
- Rx OSD integration & Raw Vicep Access in Clients - May 2010
- S3 Front-end for AFS - July 2010
- Virtual Machine Images - July 2010
- User-space cache manager - July 2010 (1.6 still not released yet)
- Kerberos v5 and multiple encryption types - July 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Patches merged into the master branch:
    Month   Number of Commits
    2010-09   52 (Partial month)
    2010-08  120
    2010-07  160
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
    2010-09   2 (Partial month)
    2010-08  10
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

Most patches are approved before the newsletter is published.  Given that,
please check out [http://gerrit.openafs.org/](http://gerrit.openafs.org/) for all of the patches
waiting for review.

### Patches merged into the master branch

    Date       Author          Change# Description
    2010-09-14 Steve Simmons    (2720) Automatically find all pod.in files and generate .pods files
    2010-09-14 Andrew Deason    (2725) DAFS: raise vhashsize limit
    2010-09-14 Andrew Deason    (2649) DAFS: Do not ignore out-of-range -vhashsize
    2010-09-14 Marc Dionne      (2733) Always check return code from iod_Write
    2010-09-14 Marc Dionne      (2732) rx: Set but not used variables
    2010-09-13 Simon Wilkinson  (2751) auth: Make token_FreeSet work on an empty set
    2010-09-13 Simon Wilkinson  (2746) Linux: Move keyring includes where they're needed
    2010-09-13 Simon Wilkinson  (2745) shlibafsrpc: Export additional symbols
    2010-09-13 Simon Wilkinson  (2744) Ignore *.dSYM files in working directory
    2010-09-13 Simon Wilkinson  (2743) Add config.log to gitignore globally
    2010-09-13 Simon Wilkinson  (2742) auth: Add a gitignore file for the test directory
    2010-09-13 Simon Wilkinson  (2741) pam: Remove unused library definitions
    2010-09-13 Simon Wilkinson  (2740) aklog: Fix some format warnings
    2010-09-13 Simon Wilkinson  (2739) aklog: Fix weak_crypto tests
    2010-09-13 Simon Wilkinson  (2737) RX: Make the sample client and server build
    2010-09-13 Simon Wilkinson  (2735) vlserver: Use com_err for Ubik error messages
    2010-09-10 Marc Dionne      (2729) Warning fix for gcc 4.5 "operation may be undefined" warnings
    2010-09-10 Andrew Deason    (2730) udebug: Always show tidCounter
    2010-09-09 Andrew Deason    (2727) namei: Do not remove n_voldir1
    2010-09-09 Michael Meffie   (2728) manpage correction for restorevol -file option
    2010-09-09 Andrew Deason    (2648) vol: Add VInit cond var and remove busywaits
    2010-09-08 Derrick Brashear (2724) update 1.5.77 release page
    2010-09-08 Andrew Deason    (2651) namei: Limit traversal when removing data dirs
    2010-09-08 Derrick Brashear (2723) 1.5.77 for web site
    2010-09-08 Steve Simmons    (2719) Add new file src/venus/cacheout to things that should be ignored.
    2010-09-08 Jeffrey Altman   (2718) Windows 1.5.77 web page update
    2010-09-08 Derrick Brashear (2715) ubik recovery and remote use correct file number
    2010-09-07 Jeffrey Altman   (2710) Windows: 1.5.77 Change Log summary
    2010-09-07 Jeffrey Altman   (2709) Windows: Improve SMB detection of Local System account
    2010-09-07 Jeffrey Altman   (2663) Windows: revise NTSTATUS response for ALLBUSY, ALLOFFLINE, and ALLDOWN
    2010-09-06 Jeffrey Altman   (2662) Windows: Modify signature of buf_CleanAsync and buf_CleanAsyncLocked
    2010-09-06 Jeffrey Altman   (2661) Windows: Permit cm_scache rwlock to be dropped when "Stablized"
    2010-09-06 Jeffrey Altman   (2660) Windows: fail cm_CheckNTOpen if READ|DELETE for readonly file
    2010-09-06 Jeffrey Altman   (2658) Windows: Add validation for directory buffer contents
    2010-09-06 Jeffrey Altman   (2657) Windows: cm_TryBulkStatRPC must process VIO errors
    2010-09-06 Jeffrey Altman   (2656) Windows: better handle RX_MSGSIZE errors
    2010-09-06 Jeffrey Altman   (2655) Windows: print the value of cm_OfflineROIsValid to afsd_init.log
    2010-09-06 Jeffrey Altman   (2654) Windows: Handle RX_RESTARTING consistently for all RPCs
    2010-09-06 Jeffrey Altman   (2653) Windows: Log cell along with volume id for server errors
    2010-09-06 Jeffrey Altman   (2652) Windows: unix modes represented in octal
    2010-09-06 Derrick Brashear (2664) rx msgsize retry logic change
    2010-09-05 Marc Dionne      (2668) afs_DoBulkStat: don't call afs_Analyze without holding the GLOCK
    2010-09-05 Andrew Deason    (2667) vos: Show effects in single-volume dryrun mode
    2010-09-05 Andrew Deason    (2665) cacheout: Improve error handling
    2010-09-05 Andrew Deason    (2666) vos: Show after effects in dryrun mode
    2010-09-02 Andrew Deason    (2643) RedHat: Package libafshcrypto libraries
    2010-09-02 Andrew Deason    (2642) RedHat: Do not force krb5-config path
    2010-09-02 Andrew Deason    (2641) RedHat: Update openafs.spec for configure changes
    2010-09-02 Andrew Deason    (2640) RedHat: Use git-version in makesrpm.pl
    2010-09-01 Andrew Deason    (2639) RedHat: Use configure.ac in makesrpm.pl
    2010-09-01 Russ Allbery     (2644) Update Autoconf Kerberos probes to latest rra-c-util version
    2010-09-01 Jonathan Billings (2630) Linux: Updated RedHat spec file with new demand attach servers and docs
    2010-08-31 Michael Meffie   (1562) ihandle positional read and write
    2010-08-31 Hartmut Reuter   (2629) Let SRXAFS_GetStatistics64 return correct values for the workstations
    2010-08-30 Derrick Brashear (2628) ubik recovery kill duplicate code
    2010-08-30 Michael Meffie   (2536) clean up stale defines in volser header
    2010-08-30 Simon Wilkinson  (2583) aklog: Add support for the new SetToken pioctl
    2010-08-30 Derrick Brashear (2622) macos afsdb reinit resolver on address change
    2010-08-30 Matt Benjamin    (2625) FBSD  try-relax child vnode locking (recurse only)
    2010-08-30 Matt Benjamin    (2623) FBSD, DFBSD (future)   call afs_FakeOpen in the write path
    2010-08-30 Andrew Deason    (2108) ubik: Protect ubik_servers in urecovery_Interact
    2010-08-30 Andrew Deason    (2107) ubik: Drop dbase versionLock during I/O and sleeps
    2010-08-30 Simon Wilkinson  (2584) New GetToken pioctl
    2010-08-30 Matt Benjamin    (2626) cache bypass  Also increment page refcount in readpage
    2010-08-30 Matt Benjamin    (2619) DFBSD  update dfbsd userland
    2010-08-30 Matt Benjamin    (2621) FBSD, DFBSD (future)  vnode_pager_setsize updates
    2010-08-28 Marc Dionne      (2620) Make hcrypto depend on config
    2010-08-26 Matt Benjamin    (2618) FBSD  restore old syscall register logic for older kernels
    2010-08-26 Matt Benjamin    (2617) sed s/porc/proc/
    2010-08-26 Simon Wilkinson  (2582) Add new SetTokenEx pioctl
    2010-08-26 Simon Wilkinson  (2581) Make unixuser's vid advisory
    2010-08-26 Simon Wilkinson  (2580) Unix CM: Generalise token storage
    2010-08-26 Benjamin Kaduk   (2616) FBSD: properly register our syscall
    2010-08-25 Matt Benjamin    (2613) FBSD:  give osi_NetReceive time to shutdown, reprise
    2010-08-25 Matt Benjamin    (2612) FBSD CM: don't call afs_close when recycling
    2010-08-25 Matt Benjamin    (2611) BSD CMs:  Don't call nonexistent afs_FlushVS in afs_vop_reclaim
    2010-08-25 Russ Allbery     (2609) Remove my misspelled twin from credits.html
    2010-08-24 Simon Wilkinson  (2607) Import of code from heimdal
    2010-08-24 Andrew Deason    (2606) venus: build cacheout
    2010-08-24 Andrew Deason    (2605) venus: make cacheout build again
    2010-08-23 Andrew Deason    (2592) ubik: add interface for reading during write locks
    2010-08-23 Andrew Deason    (2231) ubik: Fix buffers for reading-during-writes
    2010-08-23 Andrew Deason    (2106) vlserver: Allow reading during ubik writes
    2010-08-23 Andrew Deason    (2105) vlserver: Access cache via vl_ctx
    2010-08-23 Andrew Deason    (2104) vlserver: Add a struct for trans-specific data
    2010-08-23 Andrew Deason    (2230) ubik: Abstract buffer matching and pass trans ptrs
    2010-08-22 Simon Wilkinson  (2604) Don't include afsconfig.h in rxgen headers
    2010-08-21 Marc Dionne      (2600) s390x: only declare afs_sys_setgroups32_page where needed
    2010-08-21 Marc Dionne      (2602) Fixes for signed char architectures
    2010-08-21 Marc Dionne      (2603) Ignore old style definition warnings in generated code
    2010-08-20 Marc Dionne      (2601) Prototype warning cleanup - big endian
    2010-08-20 Simon Wilkinson  (2599) Add a few missing entries to our .gitignores
    2010-08-20 Simon Wilkinson  (2598) Configure: Tidy up AC_CHECK_FUNCS
    2010-08-20 Simon Wilkinson  (2597) hcrypto: Check for arc4random
    2010-08-20 Simon Wilkinson  (2596) hcrypto: Fix for IRIX
    2010-08-19 Andrew Deason    (2593) Avoid thread-unsafe PrintInode in threaded code
    2010-08-19 Andrew Deason    (2595) Windows: vol-salvage SalvInfo fixes
    2010-08-19 Simon Wilkinson  (2575) Add OpenAFS build machinery for libhcrypto
    2010-08-19 Andrew Deason    (2250) vol-salvage: Move global vars into SalvInfo struct
    2010-08-19 Andrew Deason    (1869) Remove the global tempHeader/stuff structures
    2010-08-18 Jeffrey Altman   (2590) windows.html update for 1.5.76
    2010-08-17 Jeffrey Altman   (2588) Windows: fix Freelance trailing dot enforcement
    2010-08-17 Simon Wilkinson  (2579) libafsrpc: Add new XDR symbols to exports
    2010-08-17 Simon Wilkinson  (2574) Import of code from heimdal
    2010-08-17 Simon Wilkinson  (2573) Heimdal import: Add hcrypto files
    2010-08-17 Simon Wilkinson  (2572) Handle whitespace better in import script
    2010-08-17 Jeffrey Altman   (2571) Windows: Fix remove 'register' patch
    2010-08-17 Derrick Brashear (2570) update web site for 1.5.76
    2010-08-17 Derrick Brashear (2463) death to trailing whitespace
    2010-08-17 Derrick Brashear (2436) death to register
    2010-08-17 Jason Edgecombe  (2554) Add the August 2010 newsletter
    2010-08-16 Jeffrey Altman   (2568) Windows: Return error for SetToken PIOCTL_LOGON if not LocalSystem
    2010-08-16 Derrick Brashear (2537) openafs 1.5.76
    2010-08-16 Jeffrey Altman   (2540) Windows Change Log for 1.5.76
    2010-08-16 Jeffrey Altman   (2558) Windows: prevent buffer overrun in cklog
    2010-08-16 Jeffrey Altman   (2541) Windows: Only Local System Account may set tokens for alternate ids
    2010-08-16 Jeffrey Altman   (2555) Windows: Parse Freelance entries and enforce trailing dot but no trailing ws
    2010-08-12 Chaz Chandler    (2516) autoconf detection of label support
    2010-08-12 Marc Dionne      (2546) Linux: avoid oops in memcpy_toiovec
    2010-08-12 Marc Dionne      (2545) Linux: Rework statfs super block operations configure test
    2010-08-12 Marc Dionne      (2544) Linux: switch to evict_inode
    2010-08-12 Marc Dionne      (2543) Linux: adapt to truncate sequence changes
    2010-08-12 Marc Dionne      (2542) Linux: use %pI4 if NIPQUAD is not available
    2010-08-12 Andrew Deason    (2533) viced: VNOVOL on deleted volumes
    2010-08-12 Derrick Brashear (2538) disable pmtu error gathering
    2010-08-12 Jeffrey Altman   (2539) Windows: comparisons of nul strings should match
    2010-08-12 Andrew Deason    (2531) volser: Ignore duplicate file tags when restoring
    2010-08-11 Simon Wilkinson  (2535) LINUX: More flock fixes
    2010-08-11 Simon Wilkinson  (2534) LINUX: Use correct type of error in flock code
    2010-08-11 Derrick Brashear (2515) fs discon support alternate uid
    2010-08-11 Derrick Brashear (2501) macos disconnected vnode holding fix
    2010-08-11 Jeffrey Altman   (2532) Windows: cm_Analyze should treat VOFFLINE like VMOVED or VNOVOL
    2010-08-11 Andrew Deason    (2530) salvage: update inodes array after CopyAndSalvage
    2010-08-11 Andrew Deason    (2529) salvage: Remove redundant 'code' declaration
    2010-08-11 Andrew Deason    (2528) salvage: Do not look at not-found root dir
    2010-08-11 Andrew Deason    (2527) salvage: Zero corrupted header
    2010-08-06 Andrew Deason    (2524) tviced: Fix serialize_state.o objdir
    2010-08-06 Andrew Deason    (2523) Eliminate $< outside of pattern rules
    2010-08-06 Andrew Deason    (2522) Fix objdir install/dest targets
    2010-08-06 Andrew Deason    (2521) tubik: Fix objdir builds
    2010-08-06 Andrew Deason    (2520) Fix afsd.fuse for objdir builds
    2010-08-06 Andrew Deason    (2519) rxgen: Error out if cpp exits with error
    2010-08-05 Derrick Brashear (2470) namei decodevolume allow low volume ids
    2010-08-05 Jeffrey Altman   (2525) Windows: add flags field to smb_ioctlProc_t function signature
    2010-08-05 Simon Wilkinson  (2471) Unix CM: Remove erroneous comment
    2010-08-05 Jeffrey Altman   (2518) Windows: optimize buf_FlushCleanPages
    2010-08-05 Andrew Deason    (2517) Unix: docbook revision tag requires a date
    2010-08-04 Andrew Deason    (2508) Add DAFS docs to the Unix Quick Start guide
    2010-08-04 Andrew Deason    (2506) HPUX: Add limits.h to sysincludes
    2010-08-04 Derrick Brashear (2514) fix unlabelled xdr field order on sun457 kernel for now
    2010-08-04 Derrick Brashear (2513) discon remove dirty vcaches from queue when discarding
    2010-08-04 Derrick Brashear (2512) reorder vcache references in discondiscardallshadows
    2010-08-04 Derrick Brashear (2511) discon getparentvcache leak fix
    2010-08-04 Andrew Deason    (2483) util: add afs_exec_alt
    2010-08-04 Derrick Brashear (2510) discon needs static_inline macro
    2010-08-04 Derrick Brashear (2509) darwin unused prototype
    2010-08-04 Andrew Deason    (2507) tbudb: Use INSTALL_PROGRAM, not INSTALL -f
    2010-08-03 Jeffrey Altman   (2505) Windows: Reduce complexity of Freelance Callback Logic
    2010-08-03 Jeffrey Altman   (2504) Windows: When processing pioctl paths ensure callbacks are obtained
    2010-08-02 Derrick Brashear (2502) fs disconnected remove ifdefs
    2010-08-02 Jeffrey Altman   (2500) Windows: docbook revision tag requires a date
    2010-08-02 Asanka Herath    (2492) Windows: Don't configure client when not installing client
    2010-08-02 Andrew Deason    (2497) SOLARIS: let xlator load if amd64/nfssrv is loaded
    2010-08-02 Andrew Deason    (2488) ptserver: Do not use cell for entry name len check
    2010-08-02 Asanka Herath    (2495) Windows: Fix MC options
    2010-08-02 Jeffrey Altman   (2491) Windows: Do not reference cm_data.rootSCachep directly
    2010-08-02 Jeffrey Altman   (2490) Windows: Update root.afs scache dv when Freelance dir bufs are regenerated
    2010-08-02 Jason Edgecombe  (2496) Factor out the common text in vos_addsite, vos_copy, and vos_zap
    2010-08-02 Asanka Herath    (2493) Windows: Build preprocessed POD documentation
    2010-08-02 Jeffrey Altman   (2499) Windows aklog: remove lstat preprocessor definition
    2010-08-02 Jeffrey Altman   (2498) Windows aklog: include afs/pterror.h
    2010-08-01 Asanka Herath    (2494) Skip over 'fragments' directory when scanning for PODs

### Patches merged into the stable 1.4.x branch

    Date       Author          Change# Description
    2010-09-02 Andrew Deason    (2646) RedHat: Find krb5-config in /usr/bin
    2010-09-01 Andrew Deason    (2638) Linux: RedHat packaging updates for RHEL6
    2010-08-30 Jason Edgecombe  (2615) Remove the 2TB partition limit from the 1.4.x man pages
    2010-08-25 Michael Meffie   (2610) backport of time-t-casting-fixes-20060404
    2010-08-13 Marc Dionne      (2553) Linux: Rework statfs super block operations configure test
    2010-08-13 Marc Dionne      (2552) Linux: switch to evict_inode
    2010-08-13 Marc Dionne      (2551) Linux: use %pI4 if NIPQUAD is not available
    2010-08-12 Marc Dionne      (2550) Linux: adapt to truncate sequence changes
    2010-08-12 Marc Dionne      (2549) Linux: 2.6.35 - fsync no longer takes a dentry
    2010-08-11 Andrew Deason    (2422) viced: print uuid string, not uuid itself
    2010-08-11 Andrew Deason    (2526) Include com_err.h in dumpstuff.c
    2010-08-11 Derrick Brashear (2465) vol AttachByName should mimic other volpkg errors
