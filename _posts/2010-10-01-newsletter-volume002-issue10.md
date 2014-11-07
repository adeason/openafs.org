---
title: OpenAFS Newsletter, Volume 2, Issue 10, October 2010
layout: page
category: newsletter
permalink: /newsletter/newsletter-2010-10-volume002-issue10.html
---

# OpenAFS Newsletter, Volume 2, Issue 10, October 2010

Welcome to the October issue of the OpenAFS newsletter. This newsletter
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

There is no case study this month.  Please email Jason if you would like
to volunteer.

## General OpenAFS Progress

The official results for the chairs of the afs3-standardization group is still
pending, waiting on the results from one of the three vote-takers.

Jeffrey Altman announced that the OpenAFS code base needs to migrate away
from MIT Kerberos and towards Heimdal as the primary Kerberos library
<[http://lists.openafs.org/pipermail/openafs-devel/2010-September/017932.html](http://lists.openafs.org/pipermail/openafs-devel/2010-September/017932.html)\>.
This change is required to maintain a high-level of Windows support and to
enable the use of stronger encryption. To make this change easier, a shim
library is being developed at
[http://github.com/secure-endpoints/heimdal-krbcompat](http://github.com/secure-endpoints/heimdal-krbcompat), which allows for
either Kerberos distribution to be used. The transition was discussed on
the openafs-devel mailing list with most people preferring that minimal
Heimdal code be imported into the OpenAFS git repository.

## Events

### European AFS Conference

Thanks to Michal Svamberg for providing a summary of the European AFS
Conference. --Ed.

The European OpenAFS & Kerberos Conference 2010
<[http://afs2010.civ.zcu.cz](http://afs2010.civ.zcu.cz)\> was held between 13 and 15 September 2010
in Pilsen <["http://en.wikipedia.org/wiki/Plzeň"](#http://en.wikipedia.org/wiki/Plzeň)\>, Czech Republic
<["http://en.wikipedia.org/wiki/Czech\_Republic"](#http://en.wikipedia.org/wiki/Czech\_Republic)\>. It was hosted by the
Centre for Information Technology, University of West Bohemia
<[http://www.zcu.cz/en/](http://www.zcu.cz/en/)\>.  Earlier international conferences took place
in Graz (2008) <[http://www.openafs.at/](http://www.openafs.at/)\> and Rome (2009)
<["http://www.dia.uniroma3.it/~afscon09/"](#http://www.dia.uniroma3.it/~afscon09/)\>.

The number of participants grows steadily and the event promises to become
a regular European forum for OpenAFS users and developers. This year,
there were 75 participants from nine different countries. In addition,
on-line audience counting more than 50 viewers around the world was
watching live streams.

The organizing institute has been an AFS user for many years, having
started the early experiments with Transarc AFS in 1994 and relying on AFS
as the only distributed file system across the campus (23000+ accounts,
200+ servers, 7800+ end user PCs) since 1996. Find more information on the
distributed environment deployed by the hosting institute as well as other
organizations relying on AFS and Kerberos in posters
<["http://afs2010.civ.zcu.cz/desc.php?name=sr"](#http://afs2010.civ.zcu.cz/desc.php?name=sr)\>.

To name but a few lectures from the program:

- Christof Hanke: Cell management and monitoring
<["http://afs2010.civ.zcu.cz/desc.php?name=hanke\_tools"](#http://afs2010.civ.zcu.cz/desc.php?name=hanke\_tools)\> - The talk
presented monitoring infrastructure based on nagios, used at the RZG in
developing a new management structure for its large cell.
- Love Hörnquist Astrand: Heimdal - new features in 1.5
<["http://afs2010.civ.zcu.cz/desc.php?name=heimdal"](#http://afs2010.civ.zcu.cz/desc.php?name=heimdal)\> - The talk
discussed features added with the upcoming 1.5 release and additional
changes to related Heimdal projects.
- Thomas Keiser: Deploying the Demand Attach File Server
<["http://afs2010.civ.zcu.cz/desc.php?name=dafs"](#http://afs2010.civ.zcu.cz/desc.php?name=dafs)\> - This talk gave a
brief overview of administrator-visible changes in the DAFS file server,
and then cover issues involved in migrating a production deployment to the
forthcoming OpenAFS 1.6 DAFS file server.

Visit the conference web site at [http://afs2010.civ.zcu.cz/agenda.php](http://afs2010.civ.zcu.cz/agenda.php)
to watch recordings of other interesting talks.

The conference program also included two tutorials. The first one,
Advanced Tuning & Troubleshooting
<["http://afs2010.civ.zcu.cz/desc.php?name=tutorial-II"](#http://afs2010.civ.zcu.cz/desc.php?name=tutorial-II)\>, was given by
Derrick Brashear and Jeffrey Altman. Participants were invited to present
problems they are facing and received tips for tuning their environment to
achieve better performance.

The second tutorial, Setting-up your AFS Cell
<["http://afs2010.civ.zcu.cz/desc.php?name=tutorial-I"](#http://afs2010.civ.zcu.cz/desc.php?name=tutorial-I)\>, was given by
Wolfgang Alexander Gehrke and Christof Hanke. It focused on beginners, who
learned about the internals of the system and had a chance to try and set
up their own file servers within a testing infrastructure.

The official program was complemented by social events. Participants have
learned about the World's best beer, seen the brewery and tasted the final
product. The organizers were delighted by their enthusiasm and also by the
persistence of those who endured until late night or even early morning.
See the image gallery <[http://afs2010.civ.zcu.cz/gallery.php](http://afs2010.civ.zcu.cz/gallery.php)\> for
photographs taken at the conference sessions as well as the social events.

We would like to thank all attendants and we are looking forward to next
year's event, which is going to be hosted by DESY <[http://www.desy.de/](http://www.desy.de/)\>
in Hamburg.

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

A request for last call will happen soon.

\--Derrick

### AFS Callback Extensions

[http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo](http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo)

Status: Active - Waiting on RPC refresh

Last Update: September 23, 2009

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

Last Draft Update: Jan 9, 2010

A working implementation of rxgk was demonstrated at the European AFS &
Kerberos Workshop in Pilsen. Whilst there is still work to be done, both
on completing the implementation, and on getting the code into the OpenAFS
tree, this is an important milestone. Slides from the Pilsen talk are
available on their web site, the current rxgk code is, as always,
available on github.

\--Simon Wilkinson

### AFS3 ACL Rights

[http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions](http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions)

Status: Second draft

Last update: January 13, 2010

We're waiting for the afs3-standardization structure to solidify before
proceeding with this. So, no progress right now.

\--Andrew Deason

### Rx Security Object Providing Clear-text Peer Identity Assertions

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

A fix for improving startup preattachment speed was merged (gerrit
2648), as well as the minor fixes for -vhashsize (2649, 2650). The fix
for salvaging attached volumes (2329) was almost merged, but had a
conflict that was recently resolved and hasn't been merged yet. More
prerequisites for salvageserver threading improvements have been merged
(1862, 1863), and the improvements themselves should be in soon, as
well. A fix for log-related performance problems with large numbers of
volumes was submitted and merged in gerrit 2759.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

There were a few minor fixes, but I don't think any significant changes in
the past month.

\--Russ

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

I am following up on the branch completed by Simon at
http://github.com/your-file-system/openafs-rxgk/tree/rxgk. This contains
code for rxgk AND hcrypto. I am presently hacking code off for my hcrypto
usage.

\--Sanket

#### Port OpenAFS to NetBSD

Student Developer: Matt Smith <matt.j.sm@gmail.com>

Mentor: Matt Benjamin <matt@linuxbox.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html)

Due to classwork, the only progress I've been able to make so far is to
merge the changes from the summer with master.

The version that I pushed up still only had a mountable LKM, was able to
retrieve the names of the files from the server but could not actually
create the vnodes. So what remains is to finish debugging vnode creation,
then move on to reading/writing, permissions, etc.

Unfortunately, I cloned master today and was unable to compile it again
due to some Heimdal changes that had been merged. Those aren't from me,
however.  :)

\--Matt Smith

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
- Per-File ACLs - August 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Patches merged into the master branch:
    Month   Number of Commits
    2010-10   75 (Partial month)
    2010-09  135
    2010-08  115
    2010-07  154
    2010-06  171
    2010-05  139
    2010-04  161
    2010-03  140
    2010-02  155
    2010-01  103
    2009-12   72
    2009-11   85
    2009-10  154
    2009-09  142

    Patches merged into the stable 1.4.x branch:
    Month   Number of Commits
    2010-10   2 (Partial month)
    2010-09   2
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

### Patches merged into the master branch

    Date       Author          Change# Description
    2010-10-14 Marc Dionne      (2989) LINUX/osi_vnodeops.c: minor coding style fixes
    2010-10-14 Jeffrey Altman   (2978) Rx: function return type on separate line
    2010-10-14 Andrew Deason    (1864) Parallel I/O extensions to namei backend
    2010-10-14 Marc Dionne      (2975) Linux: fix statfs configure test
    2010-10-14 Tom Keiser       (2980) rx: fix typo in rx_atomic Solaris backend
    2010-10-14 Simon Wilkinson  (2959) rx: Don't count unknown packets as missing
    2010-10-14 Jeffrey Altman   (2966) Rx: Consolidate wait for tq busy and make its use uniform
    2010-10-14 Simon Wilkinson  (2957) rx: Don't malloc the xmit list
    2010-10-14 Andrew Deason    (2973) LINUX: old kernel warning fixes
    2010-10-14 Tom Keiser       (2968) don't release Volume lightweight ref too early
    2010-10-14 Hans-Werner Paulsen (2972) wrong rule to make afsd_fuse
    2010-10-14 Marc Dionne      (2976) Linux: fix aklog -setpag to work with ktc_SetTokenEx
    2010-10-14 Andrew Deason    (2947) RX: Force sane timeout values
    2010-10-14 Andrew Deason    (2967) RX: Adjust all timeouts for RTT
    2010-10-13 Tom Keiser       (2970) trailing commas make xlc a sad panda
    2010-10-13 Tom Keiser       (2971) update fssync-debug to handle the VOL_LOCKED flag
    2010-10-13 Chas Williams - CONTRACTOR (2943) Use bigger I/O sizes for the memcache
    2010-10-13 Simon Wilkinson  (2963) hcrypto: Tidy up some merge conflicts
    2010-10-13 Andrew Deason    (2946) LINUX: Build fixes for older kernels
    2010-10-12 Simon Wilkinson  (2956) rx: Don't call gettimeofday for every packet ack
    2010-10-12 Jeffrey Altman   (2964) Windows: Build hcrypto shared library
    2010-10-12 Jeffrey Altman   (2961) Windows: Cleanup build scripts; no include\afs or include\rx
    2010-10-12 Simon Wilkinson  (2962) Fix rxperf includes
    2010-10-11 Simon Wilkinson  (2955) rx: Indent dpf definition
    2010-10-11 Simon Wilkinson  (2954) Import of code from heimdal
    2010-10-11 Simon Wilkinson  (2953) Heimdal: Import rand-w32.c for hcrypto on Windows
    2010-10-11 Jeffrey Altman   (2950) Windows: Do not issue RXAFS change RPCs on known RO volumes
    2010-10-11 Simon Wilkinson  (2896) Unix: Rework build system
    2010-10-11 Andrew Deason    (2480) fssync-debug: exec DAFS version if DAFS detected
    2010-10-11 Phillip Moore    (2948) Extract the .version file when building the srpm file
    2010-10-11 Benjamin Kaduk   (2951) Revert "FBSD: in lookup, when ISDOTDOT, unlock dvp"
    2010-10-06 Benjamin Kaduk   (2942) FBSD: in lookup, when ISDOTDOT, unlock dvp
    2010-10-06 Phillip Moore    (2940) Added missing CLI argument dropped during last commit.
    2010-10-05 Jeffrey Altman   (2913) Windows: do not leak cm_volume_t objects from LRU queue
    2010-10-05 Phillip Moore    (2914) Quick Start Guide updated for RHEL rpms, and CLI syntax
    2010-10-05 Christof Hanke   (2912) volserver: Do not return ENOMEM on AIX from XVolListPartitions
    2010-10-05 Jeffrey Altman   (2910) Windows: Kill AFS_LARGEFILES preprocessor symbol
    2010-10-05 Jeffrey Altman   (2880) rx: Reduce dependence on call->lock
    2010-10-05 Simon Wilkinson  (2908) Irix: Make compiler less chatty
    2010-10-05 Simon Wilkinson  (2904) hcrypto: Fix builds on Irix
    2010-10-05 Simon Wilkinson  (2907) Import of code from heimdal
    2010-10-05 Simon Wilkinson  (2906) Yet more imports from libroken
    2010-10-05 Simon Wilkinson  (2870) Kill AFS_64BIT_ENV
    2010-10-05 Simon Wilkinson  (2909) Revert "util: Add base64 from Heimdal's roken"
    2010-10-05 Simon Wilkinson  (2902) Import yet more files from Heimdal
    2010-10-05 Simon Wilkinson  (2903) Import of code from heimdal
    2010-10-04 Simon Wilkinson  (2901) Heimdal: Fix 32bit build problems
    2010-10-04 Andrew Deason    (2893) vol: Log ignored dirs that look like partitions
    2010-10-04 Simon Wilkinson  (2900) util: Add base64 from Heimdal's roken
    2010-10-04 Simon Wilkinson  (2899) hcrypto: Build fixes
    2010-10-04 Simon Wilkinson  (2898) Import of code from heimdal
    2010-10-04 Simon Wilkinson  (2897) Add more files from Heimdal
    2010-10-04 Simon Wilkinson  (2895) configure: Don't let autoconf pick our CFLAGS
    2010-10-04 Simon Wilkinson  (2894) configure: Restore saved CFLAGS
    2010-10-03 Marc Dionne      (2892) Remove duplicate rx_stats targets in libuafs Makefile
    2010-10-03 Andrew Deason    (2731) vos release: Force full dump on RO_DONTUSE sites
    2010-10-03 Chas Williams - CONTRACTOR (2891) sin_family is not network order
    2010-10-03 Derrick Brashear (2890) rx stats atomic inclusion needs kmutexes for emulation
    2010-10-03 Jeffrey Altman   (2887) Windows: Ensure that cm_NameI errors are acted upon promptly
    2010-10-03 Jeffrey Altman   (2886) Windows: Fix Parent(path) computation to permit mp and symlink creation
    2010-10-03 Derrick Brashear (2885) add rxstats to kernel
    2010-10-03 Marc Dionne      (2888) Conditionalize include of string.h in rx_stats.c
    2010-10-03 Marc Dionne      (2889) Linux: correct use of atomic_add and atomic_sub functions
    2010-10-02 Jeffrey Altman   (2882) Rx: Fix RXDEBUG_PACKET builds
    2010-10-02 Jeffrey Altman   (2881) Rx: raise rx_minPeerTimeout to 20ms
    2010-10-02 Jeffrey Altman   (2871) Rx: When call receive is done, send ack all packet
    2010-10-02 Jeffrey Altman   (2837) Rx: protect rx_conn and rx_call refCount field with rx_refcnt_mutex
    2010-10-02 Derrick Brashear (2884) darwin kernel atomics
    2010-10-02 Chas Williams - CONTRACTOR (2877) add option to rxperf to use rx_Readv() instead of rx_Read()
    2010-10-02 Jeffrey Altman   (2883) Windows: Pass Volume Root Fid to cm_Analyze after RXAFS_GetVolumeStatus
    2010-10-02 Andrew Deason    (1863) Provide an abstract thread pool object
    2010-10-02 Andrew Deason    (1862) Provide an abstract work queue object
    2010-10-02 Derrick Brashear (2875) exempt instant timeouts from mtu discovery
    2010-10-02 Andrew Deason    (2759) DAFS: Raise LogLevel for per-chain vol stats
    2010-10-01 Chas Williams - CONTRACTOR (2876) rename some variables in rxperf
    2010-09-30 Chas Williams - CONTRACTOR (2869) configure: --with-linux-kernel-packaging should default to disabled
    2010-09-30 Chas Williams - CONTRACTOR (2874) afsd's -mem_alloc_sleep is obselete -- update documentation to reflect this.
    2010-09-30 Simon Wilkinson  (2859) rx: Add rx_NewThreadId function
    2010-09-30 Simon Wilkinson  (2863) rx: Don't have different args for rxi_FreeCall
    2010-09-30 Andrew Deason    (2533) viced: VNOVOL on deleted volumes
    2010-09-30 Simon Wilkinson  (2862) rx: Make statistics interface use Atomics
    2010-09-30 Simon Wilkinson  (2861) rx: Use atomics for rxi_AllocSize and rxi_AllocCnt
    2010-09-30 Simon Wilkinson  (2860) rx: Make nWaiting and nWaited atomic
    2010-09-30 Andrew Deason    (2650) DAFS: document the limits of -vhashsize
    2010-09-30 Derrick Brashear (2868) linux define ucontext properly
    2010-09-30 Simon Wilkinson  (2858) rx: Add atomic operations code
    2010-09-30 Asanka Herath    (2866) Windows: Set NTDDI_VERSION when setting _WIN32_WINNT
    2010-09-29 Benjamin Kaduk   (2864) More FBSD syscall tweaking
    2010-09-29 Simon Wilkinson  (2856) RX: Tidy reader data locking
    2010-09-28 Simon Wilkinson  (2857) rx: Limit window size to max acks
    2010-09-27 Simon Wilkinson  (2855) rxperf: Really set UDP buffer size
    2010-09-27 Simon Wilkinson  (2854) Fix rxperf so that it works with pthreads
    2010-09-27 Marc Dionne      (2853) viced, tviced: Set but not used variables
    2010-09-27 Marc Dionne      (2852) volser: Set but not used variables
    2010-09-27 Marc Dionne      (2851) tubik: minor Makefile cleanups
    2010-09-27 Derrick Brashear (2850) pam test should return an int in main
    2010-09-26 Russ Allbery     (2849) Update Debian packaging to 1.5.77-2 release
    2010-09-24 Michael Meffie   (2843) scout: display fetch and store counts as unsigned
    2010-09-24 Simon Wilkinson  (2844) rx: Big windows make us sad
    2010-09-24 Simon Wilkinson  (2842) libafsrpc depends on rxstat and fsint
    2010-09-23 Matt Smith       (2767) Updates to the Cache Manager to include NetBSD5 support
    2010-09-23 Simon Wilkinson  (2840) rxperf: Fix the Unix build again
    2010-09-23 Simon Wilkinson  (2841) rxperf: Add build rules to build a pthreaded version
    2010-09-23 Simon Wilkinson  (2833) Add an LWP version of the hcrypto library
    2010-09-23 Simon Wilkinson  (2576) Move des/stats.h to rxkad directory
    2010-09-23 Simon Wilkinson  (2828) tests: Fix objdir builds
    2010-09-23 Simon Wilkinson  (2827) rx: Add struct rx_identity
    2010-09-23 Simon Wilkinson  (2826) rx: Add an opaque type
    2010-09-23 Russ Allbery     (2836) Link dafssync-debug(8) to fssync-debug(8)
    2010-09-23 Russ Allbery     (2831) Fix POD errors in fileserver and dasalvager
    2010-09-23 Russ Allbery     (2830) Update bos create man page for new naming of demand-attach binaries
    2010-09-23 Simon Wilkinson  (2825) auth: Add documentation for ktc_ListTokensEx
    2010-09-23 Simon Wilkinson  (2608) hcrypto: Add dirfd definition for solaris
    2010-09-23 Jeffrey Altman   (2835) Additional functionality for rxperf
    2010-09-23 Simon Wilkinson  (2838) libuafs: Don't #define user
    2010-09-23 Simon Wilkinson  (2832) rxkad: Make the test suite build again
    2010-09-22 Simon Wilkinson  (2834) rxperf: Fix so it builds on Unix
    2010-09-21 Simon Wilkinson  (2736) rxgen: Handle complex structures
    2010-09-21 Jeffrey Altman   (2815) Rx: Change minimum peer timeout to 2ms
    2010-09-21 Jeffrey Altman   (2818) Rx: Permit MakeDebugCall() be be compiled when RXDEBUG is undefined
    2010-09-21 Jeffrey Altman   (2817) Rx: Do not hold call lock across memcpy in rx_ReadProc/rx_WriteProc
    2010-09-21 Russ Allbery     (2819) Add NEWS entries for OpenAFS 1.5.77 and 1.5.76
    2010-09-21 Jeffrey Altman   (2816) Rx: Permit udp buffer size to be set in rxperf
    2010-09-21 Jeffrey Altman   (2771) Windows: Negative Caching for Volume Lookups
    2010-09-20 Russ Allbery     (2761) Mention KRB5CCNAME in the aklog man page
    2010-09-20 Jeffrey Altman   (2783) Rx: Permit ADAPT_WINDOW code to build
    2010-09-20 Jeffrey Altman   (2779) Windows: Export additional RX debugging variables from afsrpc.dll
    2010-09-20 Jeffrey Altman   (2778) Rx: PrintTheseStats should not be dependent on RXDEBUG
    2010-09-20 Jeffrey Altman   (2777) Rx: move TSFPQ prototypes from rx_globals.h to rx_protoypes.h
    2010-09-20 Jeffrey Altman   (2776) Rx: properly compute dataPacketsReSent statistic
    2010-09-20 Jeffrey Altman   (2775) Rx: always use tservice variable in rxi_ServerProc
    2010-09-20 Jeffrey Altman   (2787) Rx: Only backoff the peer timeout once
    2010-09-20 Jeffrey Altman   (2782) Rx: only compute peer bytes sent and received if rx_stats_active
    2010-09-20 Jeffrey Altman   (2781) Rx: avoid lock churn in rxi_ReceiveAckPacket
    2010-09-20 Jeffrey Altman   (2774) Windows: Release builds of Rx should be lean and mean
    2010-09-20 Jeffrey Altman   (2773) Rx: Build rxperf test application on Windows
    2010-09-20 Simon Wilkinson  (2750) rx: Call rxgen_consts.h by its proper name
    2010-09-20 Simon Wilkinson  (2738) RX: Make rxi_Alloc return (void *)
    2010-09-20 Simon Wilkinson  (2758) viced: Don't fall back to tokens
    2010-09-20 Simon Wilkinson  (2757) ubik: Remove unused error codes
    2010-09-20 Marc Dionne      (2734) rxgen, kauth: Set but not used variables
    2010-09-20 Simon Wilkinson  (2756) ptserver: Merge WhoIsThis and WhoIsThisWithName
    2010-09-20 Simon Wilkinson  (2755) Add additional dependencies for shlibafsrpc
    2010-09-20 Simon Wilkinson  (2753) userok: Don't double check for expiry
    2010-09-20 Simon Wilkinson  (2752) auth: Restructure userok
    2010-09-20 Simon Wilkinson  (2749) tokens: Use the new tokens interface
    2010-09-20 Jeffrey Altman   (2772) Rx: Move rxperf test application to src/rx/tests
    2010-09-20 Simon Wilkinson  (2748) auth: Add the ktc_ListTokensEx function
    2010-09-20 Jeffrey Altman   (2780) Rx: cleanup testclient and testserver test applications
    2010-09-20 Simon Wilkinson  (2747) authcon: Use ktc_GetTokenEx in ClientAuthToken
    2010-09-20 Simon Wilkinson  (2766) Rename kauth/token.c as kauth/katoken.c
    2010-09-20 Jeffrey Altman   (2765) Windows: Add new token interface with stub for ktc_GetTokenEx
    2010-09-20 Simon Wilkinson  (2754) Linux: print after BUG() is pretty useless
    2010-09-20 Marc Dionne      (2784) vlserver: Set but not used variables
    2010-09-20 Andrew Deason    (2763) libafs: Fix pioctl get/putInt alignment issues
    2010-09-20 Andrew Deason    (2760) volser: Delete timed-out temporary volumes
    2010-09-20 Marc Dionne      (2785) butc: Set but unused variables
    2010-09-20 Andrew Deason    (2764) libafs: Fix compile errors in afs_nfsclnt.c
    2010-09-20 Marc Dionne      (2786) vol: Set but not used variables
    2010-09-19 Marc Dionne      (2770) Linux: normalize error return for emulated syscalls
    2010-09-17 Derrick Brashear (2762) disable Rx packet tracking
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
    2010-09-08 Andrew Deason    (2651) namei: Limit traversal when removing data dirs
    2010-09-08 Steve Simmons    (2719) Add new file src/venus/cacheout to things that should be ignored.
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

### Patches merged into the stable 1.4.x branch

    Date       Author          Change# Description
    2010-10-11 Andrew Deason    (2879) Use afs_foff_t for offsets
    2010-10-11 Andrew Deason    (2423) Use afs_sfsize_t for *_SIZE results
    2010-09-02 Andrew Deason    (2646) RedHat: Find krb5-config in /usr/bin
    2010-09-01 Andrew Deason    (2638) Linux: RedHat packaging updates for RHEL6
    2010-08-30 Jason Edgecombe  (2615) Remove the 2TB partition limit from the 1.4.x man pages
    2010-08-25 Michael Meffie   (2610) backport of time-t-casting-fixes-20060404
