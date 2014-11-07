---
title: OpenAFS Newsletter, Volume 2, Issue 5, May 2010
layout: page
category: newsletter
permalink: /newsletter/newsletter-2010-05-volume002-issue05.html
---

# OpenAFS Newsletter, Volume 2, Issue 5, May 2010

Welcome to the anniversary issue of the OpenAFS newsletter, yay! This
newsletter summarizes what is happening in the OpenAFS community.

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

1.5.74 was released on April 22. It includes many fixes and improvements,
including updates for FreeBSD 8.0, and an experimental FUSE client among
other improvements.

Testing continues for the 1.5.X series on Unix platforms. There is a patch
(commit 14195f0f) in git against 1.5.74 that fixes a kernel panic on RHEL
6 Beta. The kernel panic affects OpenAFS versions 1.5.66 through 1.5.74.

On RedHat Enterprise Linux (RHEL) 6 Beta and Fedora 12, there is an issue
where the kernel generates large volumes of system log traffic when the
AFS disk cache is accessed.  RedHat Bugzilla entry \#584901
[https://bugzilla.redhat.com/show\_bug.cgi?id=584901](https://bugzilla.redhat.com/show\_bug.cgi?id=584901) is tracking this
issue and includes a fix for the issue. The RedHat kernel team is
reviewing the patch for possible inclusion in the production release of
RHEL 6.

The 1.4.x versions of OpenAFS don't work with Linux kernel 2.6.34. Version
1.4.12.1 will be released to deal with that

Some groundwork has been started for read/write replication based on
Vishal Powar's code from the 2008 Google summer of code. The code requires
a new RPC protocol between fileserver. A standards proposal is planned for
documenting the new protocol.

Adam Megacz reported success while using an unauthenticated 1.4.11 client
on an Apple TV.

## Events

### Annual Best Practices Workshop

The seventh Workshop will be held May 24-28, 2010, at the University of
Illinois at Urbana-Champaign.  We hope to see you there.

Web site: [http://workshop.openafs.org/afsbpw10/index.html](http://workshop.openafs.org/afsbpw10/index.html)

We'll be looking forward to meeting you at Illinois this month!

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

### AFS Callback Extensions

[http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo](http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo)

Status: Active - Waiting on RPC refresh

This proposal will be rewritten with references to the RPC time refresh.

Last update: September 23, 2009

### DNS SRV Resource Records for AFS

[http://tools.ietf.org/html/rfc5864](http://tools.ietf.org/html/rfc5864)

Status: Published

The draft was accepted and published as RFC 5864.

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

Gerrit 1092 (initialization volume lock contention) has been merged, which
should speed up DAFS startup on fileservers with large numbers of
volumes. An important fix has been discovered by Simon Wilkinson in gerrit
1832, which is undergoing review. Several thread-safety fixes to the
salvaging code has culminated with gerrit 1865 (undergoing review), which
allows for multiple I/O threads in salvages, potentially providing salvage
speed improvements. Gerrit 1562 (positional I/O; required for new
improvements) is still undergoing review, but has made much recent
progress.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

IIRC, we merged some XML document updates, but most of the work was on the
man pages.  People have been doing very well about submitting
documentation changes with changes that need documentation.  Some
improvements to the demand-attach file server documentation were merged,
although there are still some undocumented binaries in a demand-attach
build (I believe man pages for them are currently being worked on).

### Pthreaded Ubik

Project Contact:

- Steven Jenkins <steven.jenkins@gmail.com>
- Andrew Deason <adeason@sinenomine.net>
- Alistair Ferguson <Alistair.Ferguson@morganstanley.com>

This code has been merged into the master branch. It will not appear as a
separate project in future newsletters.

### Per-File ACLs

Project Contacts:

- Marc Dionne <marc.c.dionne@gmail.com>

Current status:

The published code on github for per-file ACLs has the following new
features:

- Capabilities (server and client) are used to determine if file ACL support
should be active, both on the server and client
- Volume moves, dumps and restores are functional
- New Fetch/StoreACL RPCs are defined and used, in anticipation of the RPC
refresh.  Only the new RPCs will support file ACL semantics.

The github fork is at http://github.com/mdionne/openafs, and the most
current work is in the per-file branch, which should be the default branch.

\--Marc

### \*BSD Support

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

Added Support for NetBSD 5.0, and added conditionals for FreeBSD 8.1 and 9.0.

### Userspace cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

All recent related changes have been merged, and Debian packages
containing the FUSE OpenAFS client should be in Debian soon, thanks to
Russ Allbery. Modern libuafs perl bindings are still forthcoming, but
should be available before the workshop this month.

\--Andrew

### Rx OSD integration & Raw Vicep Access in Clients

Project Contacts:

- Hartmut Reuter <reuter@rzg.mpg.de>
- Felix Frank <Felix.Frank@Desy.de>
- Christof Hanke <hanke@rzg.mpg.de>

The cell ipp-garching.mpg.de is currently switching production servers to
openafs-osd based on 1.4.12.  Hartmut Reuter started to port the
extensions to 1.5.x.  Debian and possibly ubuntu packages of openafs-osd
are available soon. --Christof

### SetAG

Project Contact:

- Alberto Mancini <ab.mancini@gmail.com>

Due to lack of resources and development time SetAG has to be considered a
discontinued project, sorry.  We had no possibility in the last months of
working on updating our code to follow changes in openafs so definitely I
think that the project has to be rethinked from scratch.

\--Alberto

### Google Summer of Code 2010

OpenAFS received five slots for the 2010 Google Summer of Code.

Go to [http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs](http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs)
for more information about the GSoC projects.

#### Unix Support for AppleDouble files (Posix Attributes)

Student Developer: Kelli Ireland <kelli.ireland@gmail.com>

Mentor: Derrick Brashear <shadow@gmail.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html)

Abstract:

AppleDouble files, commonly used to store metadata and extended attributes
in filesystems without native support for them, would be supported by all
POSIX-compliant OpenAFS platforms. This would provide a means to allow
client-side extended attribute support to be added in a
backward-compatible manner without requiring changes to the AFS file
servers. It also opens the door for future protocol changes to be made, if
better accommodation of metadata and extended attributes is desired.

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

Abstract:

Last year, I have took the project, and as a student of GSoC2009. I have
finished partly a task, as Linus and some of the Linux community against
implement pioctl() directly in the kernel. We used other ways to talk to
the kernel after we gave up some implementation that have done. There is
my project idea and time line at last. My major is distributed file
system. As I have some experience of my research and this project, I think
I could do it well.



#### Port OpenAFS to NetBSD

Student Developer: Matt Smith <matt.j.sm@gmail.com>

Mentor: Matt Benjamin <matt@linuxbox.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html)

Abstract:

Around the same time the original Linux port of AFS was done, a port to
NetBSD was also available. While NetBSD has evolved, the original AFS port
did not keep pace. Since then, a port to NetBSD has been highly
desired. This project will port the OpenAFS client to run on NetBSD.

#### An open source version of the Microsoft Safe String Library

Student Developer: Jonas Sundberg <jonas.sundberg@gmail.com>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html)

Abstract:

A cross platform implementation of the Safe String Library (StrSafe.h)
provided by Microsoft. The library will allow multi platform software to
use a single library for safe string operations. This will reduce the risk
for buffer overflows and will increase code sharing between code for
different platforms.

A lot of focus will be put on unit testing of the library thoroughly. This
will make it easier to be confident in the correctness of the library.



### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Active Directory Backend for Ptserver - November 2009
- Extended Callback Information - January 2010
- Disconnected AFS support - February 2010
- Virtual Machine Images - April 2010
- Kerberos v5 and multiple encryption types - April 2010
- Mac OS X OpenAFS Preference Pane - April 2010
- S3 Front-end for AFS

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 35 (last month: 50)

    Patches merged into the master branch:
    Month   Number of Commits
    2010-05   80 (Partial month)
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
    2010-05   9 (Partial month)
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
    2010-05-18 Anders Kaseorg   (1988) Linux: replace invalidate_inode_pages
    2010-05-18 Andrew Deason    (1987) libafs: consistently hold vnode refs
    2010-05-18 Derrick Brashear (1986) viced: kill console use
    2010-05-18 Rod Widdowson    (1983) Read volume at correct address when looking for broken forward links.
    2010-05-18 Derrick Brashear (1984) mrafs logs don't clobber existing logs
    2010-05-18 Andrew Deason    (1920) vol, volser, and viced type fixes
    2010-05-17 Michael Meffie   (1562) ihandle positional read and write
    2010-05-17 Andrew Deason    (1979) Mention that -fakestat fakes local cellular mounts
    2010-05-17 Christof Hanke   (1975) Example usage of the tabular output in libcmd
    2010-05-17 Simon Wilkinson  (1823) Linux: Remove the BKL
    2010-05-17 Derrick Brashear (1959) bosserver force corefiles
    2010-05-17 Christof Hanke   (1970) Add output-table to libcmd
    2010-05-17 Rainer Toebbicke (1311) Lockless path through afs_linux_dentry_revalidate
    2010-05-17 Simon Wilkinson  (1971) Autoconf : Kill dead code
    2010-05-17 Andrew Deason    (1940) Reuse existing non-linktable special inodes
    2010-05-16 Simon Wilkinson  (1392) More warnings cleanup
    2010-05-16 Simon Wilkinson  (1878) Unix CM: Use macros for process name and id access
    2010-05-16 Jeffrey Altman   (1965) Windows: add BSD getopt to afsutil.lib
    2010-05-13 Michael Meffie   (1951) scout: increase field widths
    2010-05-13 Andrew Deason    (1546) Protect ubik cache accesses
    2010-05-12 Michael Meffie   (1949) xstat: fix large integer output
    2010-05-11 Simon Wilkinson  (1935) Add an OpenAFS config file parser
    2010-05-11 Russ Allbery     (1938) Update bos addkey/listkeys and KeyFile man pages for asetkey
    2010-05-11 Simon Wilkinson  (1934) Import of code from heimdal
    2010-05-10 Andrew Deason    (1865) Allow salsrv salvage I/O to occur in parallel
    2010-05-10 Andrew Deason    (1864) Parallel I/O extensions to namei backend
    2010-05-10 Andrew Deason    (1862) Provide an abstract work queue object
    2010-05-10 Andrew Deason    (1863) Provide an abstract thread pool object
    2010-05-08 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2010-05-07 Simona Poilinca  (1778) Replaced the unsafe string functions in src/WINNT/afsd/cm_config.c with the safe versions available in microsoft's strsafe lib
    2010-05-07 sanket           (1777) Add xml functionality to the vos examine command
    2010-05-06 Antoine Verheijen (1917) OpenBSD: Use FREE instead of KFREE
    2010-05-06 Antoine Verheijen (1916) OpenBSD: Add missing header files
    2010-05-06 Rainer Toebbicke (1903) Do not corrupt volume linktable when special file already exists
    2010-05-05 Derrick Brashear (1851) report server address when known for afs warnings
    2010-05-05 Derrick Brashear (1906) fix dumptool on macos
    2010-05-04 Andrew Deason    (1869) Remove the global tempHeader/stuff structures
    2010-05-04 Jeffrey Altman   (1742) Make -printuuid an option for all vos commands
    2010-05-04 Rainer Toebbicke (1902) patch cbd_printCBcrash - harden callback debugging
    2010-05-03 Derrick Brashear (1872) no fs sa /afs in dynroot mode
    2010-05-01 Simona Poilinca  (1789) Independent implementation of StringCchCopyA and StringCchCatA
    2010-04-28 Derrick Brashear (1852) mariner log messages for creating and removing files
    2010-04-23 Simon Wilkinson  (1824) Use git describe to determine build version
    2010-04-19 Michael Meffie   (1786) viced: host hash address collisions
    2010-04-19 Andrew Deason    (1614) Add the Jabber MUC to the support page
    2010-03-23 Derrick Brashear (1625) preliminary support for pinned vcaches
    2010-03-19 Michael Meffie   (215) rxdebug: show delayed abort packet count for rx peers
    2010-03-17 Derrick Brashear (1553) dynamic volume allocation
    2010-02-15 Michael Meffie   (1001) return an error from afs_readdir when out of buffers
    2010-02-06 Dan Hyde         (1212) VTRANS_LOCK not needed in TryUnlock
    2010-02-03 Dan Hyde         (1191) runningCalls: VOL_COUNT_LOCK vs VTRANS_LOCK
    2010-02-03 Derrick Brashear (1172) linux mmap anti-deadlock shouldn't break StoreAllSegments
    2010-02-03 Derrick Brashear (1201) basic kernel event system for afs cm
    2010-02-02 Simon Wilkinson  (1072) Unix CM: Conflate rxfs_[store,fetch]Variables
    2010-01-20 Simon Wilkinson  (1074) Unix CM: Include memcache's tiov in rxfs_context
    2009-11-29 Andrew Deason    (875) Make ubik use unsigned addresses
    2009-11-18 Andrew Deason    (709) Break origin's callback for RXAFS_Rename target
    2009-11-04 Andrew Deason    (436) Avoid unnecessarily updating .. in SAFSS_Rename
    2009-09-09 Matt Benjamin    (435) clear stat flag on renamed directories
    2009-08-29 Matt Benjamin    (376) K5SSL by Marcus Watts
    2009-07-29 Michael Meffie   (147) Fix bosserver directory creation
    2009-07-24 Hartmut Reuter   (70) preparing rxosd integration: change in AFSFetchStatus



### Patches merged into the master branch

    Date       Author          Change# Description
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
    2010-04-28 Marc Dionne      (1877) Warning fix: cpp hates apostrophes
    2010-04-28 Matt Benjamin    (1874) netbsd: rebase cm at NetBSD 4.0
    2010-04-28 Derrick Brashear (1873) upstream dumpscan changes
    2010-04-28 Simon Wilkinson  (1871) Linux: Register number sysctls only when desperate
    2010-04-28 Marc Dionne      (1870) Linux: specify void argument for afs_try_to_freeze inlines
    2010-04-27 Marc Dionne      (1868) Linux autoconf: fix name for struct cred test
    2010-04-27 Marc Dionne      (1867) Linux autoconf typo
    2010-04-27 Andrew Deason    (1861) Add some directory package doxygen comments
    2010-04-27 Simon Wilkinson  (1859) Linux: autoconf fallout
    2010-04-27 Matt Benjamin    (1858) netbsd: remove old (non-original) NBSD port
    2010-04-27 Marc Dionne      (1828) Linux: Remove unnecessary crhold on incomplete kernel credentials
    2010-04-27 Derrick Brashear (1846) flush changes on LOCK_EX unlock
    2010-04-27 Derrick Brashear (1841) allow file length to be updated unless we're writing
    2010-04-27 Simon Wilkinson  (1857) Linux: Reorder the tests
    2010-04-27 Simon Wilkinson  (1856) Linux: Don't preprocess osi_vfs.h
    2010-04-27 Simon Wilkinson  (1855) Linux: Don't waste autoconf checks on cpp defines
    2010-04-27 Simon Wilkinson  (1854) Linux: Add general autoconf macro for Linux kernel
    2010-04-27 Simon Wilkinson  (1853) Linux: Add autoconf macro for structure checks
    2010-04-27 Simon Wilkinson  (1849) Linux: Macroise kernel function autoconf tests
    2010-04-27 Simon Wilkinson  (1845) Linux: Tidy up freezer code
    2010-04-27 Simon Wilkinson  (1844) Linux: Simplify header file checks
    2010-04-27 Matt Benjamin    (1850) Rename afs_nbsd_* functions in OBSD
    2010-04-27 Simon Wilkinson  (1848) Overzealous .gitignore under rxkad
    2010-04-26 Marc Dionne      (1847) Overzealous clean target under rxkad
    2010-04-26 Derrick Brashear (1840) dcache dirty pages flag is solaris only
    2010-04-26 Simon Wilkinson  (1820) Linux: Don't hide memory management
    2010-04-26 Simon Wilkinson  (1821) Linux: The kernel module always runs in the kernel
    2010-04-26 Derrick Brashear (1837) fix other oldtvix typo
    2010-04-26 Marc Dionne      (1810) Initialize oldvtix
    2010-04-26 Simon Wilkinson  (1822) Linux: Use kernel network helper functions
    2010-04-26 Simon Wilkinson  (1819) Linux: Remove old code from RX kernel implementation
    2010-04-26 Simon Wilkinson  (1818) Linux: Don't pass f_pos down to the filesystem
    2010-04-26 Simon Wilkinson  (1817) Linux: Removed unused define
    2010-04-26 Simon Wilkinson  (1816) Linux: Don't roll our own llseek
    2010-04-26 Derrick Brashear (1827) cachemgr store file too big error exit via usual path
    2010-04-26 Simon Wilkinson  (1836) Move rxkad/domestic/* into rxkad/ directory proper
    2010-04-26 Simon Wilkinson  (1831) Improve shared library building support
    2010-04-26 Simon Wilkinson  (1830) Linux: Remove prototype warning inhibition
    2010-04-26 Simon Wilkinson  (1829) Fix make clean and make distclean
    2010-04-26 Simon Wilkinson  (1835) Really kill des_stub
    2010-04-24 Simon Wilkinson  (1826) Fix objdir builds
    2010-04-23 Derrick Brashear (1825) macos growl agent warning parser fix
    2010-04-23 Derrick Brashear (1814) openafs 1.5.74.1
    2010-04-23 Derrick Brashear (1813) macos launchd be more patient
    2010-04-23 Simon Wilkinson  (1811) Unix: Modify disk cache versioning
    2010-04-23 Marc Dionne      (1812) Warning fix: cast to expected type
    2010-04-22 Andrew Deason    (1809) Update nextVnodeUnique before checking inUse
    2010-04-22 Andrew Deason    (1808) Prefer EndCall errors in StoreMini
    2010-04-22 Simon Wilkinson  (1807) Linux: Tidy up packaging
    2010-04-22 Simon Wilkinson  (1806) Linux: RedHat packaging updates for RHEL6
    2010-04-22 Andrew Deason    (1805) Resolve symlinks for 'fs rmmount'
    2010-04-22 Derrick Brashear (1333) byte-range lock warning should include pid
    2010-04-22 sanket           (1771) Adding osi_procname macro to different platforms
    2010-04-21 Derrick Brashear (1802) macos bulkstat again
    2010-04-21 Russ Allbery     (1791) Fix UCONTEXT detection on ppc_linux26 via include order
    2010-04-21 Andrew Deason    (1801) Recover from afs_GetVolSlot errors
    2010-04-21 Russ Allbery     (1799) Add RFC 5864 to the protocol documentation directory
    2010-04-21 Russ Allbery     (1792) Install afsd.fuse and man page if built
    2010-04-21 Anders Kaseorg   (1800) Add src/afsd/afsd.fuse and src/libuafs/afsd to .gitignore
    2010-04-21 Andrew Deason    (1783) Add documentation for fs callback xstats
    2010-04-21 Derrick Brashear (1793) kauth admin tools ubik prototyping
    2010-04-20 Jonathan Billings (1798) Updated dkms.conf to remove MPS=$SMP from make
    2010-04-20 Jonathan Billings (1796) Added explanatory comments for restorevol move
    2010-04-20 Jonathan Billings (1795) Fixed more locations to reflect recent changes
    2010-04-20 Jonathan Billings (1794) Fixed RedHat SPEC file to reflect updates in code
    2010-04-20 Russ Allbery     (1790) Remove special-case call sequence for KAM_SetPassword on s390
    2010-04-20 Andrew Deason    (1784) Use AC_PREREQ
    2010-04-20 Russ Allbery     (1787) Fixes and clarifications to vos setaddrs man page
    2010-04-20 Russ Allbery     (1788) Update Debian packaging for 1.5.74
    2010-04-19 Derrick Brashear (1782) macos disable bulkstat
    2010-04-19 Derrick Brashear (1776) macos bulkstat don't double reget refs
    2010-04-18 Derrick Brashear (1775) bulkstat restore bulkfetching state for reused vcaches
    2010-04-18 Jeffrey Altman   (1774) Windows: correct locking in cm_FreeServerList
    2010-04-18 Jeffrey Altman   (1769) Windows: Preserve volume location info in case of comm fail
    2010-04-18 Jeffrey Altman   (1773) Windows: prevent infinite idle error response
    2010-04-17 Jeffrey Altman   (1772) Windows: Increase the memory map version
    2010-04-17 Derrick Brashear (1768) openafs 1.5.74
    2010-04-17 Jeffrey Altman   (1770) Windows: 1.5.74 change log
    2010-04-17 Jeffrey Altman   (1766) Rx: make conn_call_lock and conn_data_lock usage consistent
    2010-04-17 Jeffrey Altman   (1767) Windows: cm_UpdateCell must hold cell lock across server random
    2010-04-17 Jeffrey Altman   (1761) Windows: CM_SCACHESYNC_STOREDATA for non-files have no buffers
    2010-04-17 Jeffrey Altman   (1762) Windows: define new event log messages for cm_Analyze VBUSY, VRESTARTING, etc.
    2010-04-17 Jeffrey Altman   (1760) Windows: wait for I/O on buffers to complete in cm_SetupStoreBIOD
    2010-04-17 Jeffrey Altman   (1759) Windows: split cm_buf_t.flags field to ensure proper locking
    2010-04-16 Marc Dionne      (1765) Remove unused variable in vos.c
    2010-04-16 Derrick Brashear (1764) work around finder setting modes on symlinks
    2010-04-16 Jeffrey Altman   (1744) Add vos setaddrs command and man page
    2010-04-16 Jeffrey Altman   (1763) Convert param.rs_aix61.h EOF from CR-LF to LF
    2010-04-15 Simon Wilkinson  (1758) Tidy up UKERNEL includes
    2010-04-15 Jeffrey Altman   (1755) Rx: restore thread safety to rx_NewCall
    2010-04-15 Derrick Brashear (1756) darwin bulk race needs an iocount
    2010-04-15 Derrick Brashear (1753) macos and bsd readdir type guessing fix
    2010-04-15 Derrick Brashear (1757) snowleopard fuse fallout
    2010-04-15 Marc Dionne      (1750) Replace unsafe use of gets()
    2010-04-15 Derrick Brashear (1754) drop afs_xserver lock during GetCapabilities
    2010-04-15 Russ Allbery     (1749) Autogenerate a Debian changelog for correct package versioning
    2010-04-14 Andrew Deason    (1725) Add a FUSE implementation for afsd
    2010-04-14 Andrew Deason    (1724) Use afsd code in libuafs
    2010-04-14 Jeffrey Altman   (1741) Rename uvldbentry spare1 to matchindex
    2010-04-13 Marc Dionne      (1748) Fix new UKERNEL warnings on 64-bit
    2010-04-13 Andrew Deason    (1747) Add support for pkg-config m4 macros
    2010-04-13 Andrew Deason    (1746) Squash afs_GenericStoreProc warning
    2010-04-13 Andrew Deason    (1745) libuafs: Add $(XCFLAGS) to CFLAGS on all platforms
    2010-04-13 Michael Meffie   (1092) DAFS: avoid volume lock contention during initialization
    2010-04-13 Marc Dionne      (1640) Fileserver capabilities support for the UNIX client
    2010-04-13 Jeffrey Altman   (1740) Rx: avoid out of order lock acquisition in rx_NewCall
    2010-04-13 Andrew Deason    (1743) Do not turn off AFS_HAVE_STATVFS for UKERNEL
    2010-04-13 Andrew Deason    (1723) Split afsd into afsd.c and afsd_kernel.c
    2010-04-10 Matt Smith       (1737) Fix problems from afs_osi_gcpags reorganization
    2010-04-10 Michael Meffie   (1735) afsmonitor: fix segv on exit
    2010-04-10 Michael Meffie   (1734) afsmonitor: show busy counts
    2010-04-10 Marc Dionne      (1733) Fix UKERNEL build error - include afs/afs_osi.h
    2010-04-09 Matt Smith       (1727) Move contents of afs_osi_gcpags to per-OS files
    2010-04-09 Andrew Deason    (1679) Correct incorrect type-punning fixes
    2010-04-09 Michael Meffie   (1731) afsmonitor: add fs callback xstats collection
    2010-04-09 Michael Meffie   (1730) afsmonitor: avoid showing full perf stats garbage
    2010-04-09 Derrick Brashear (1729) ukernel osi prototypes header
    2010-04-09 Andrew Deason    (1722) UKERNEL: allow creation of non-detached threads
    2010-04-09 Andrew Deason    (1721) Use AFS_CACHE_VNODE_PATH for UKERNEL
    2010-04-09 Andrew Deason    (1714) Make osi_GetTime work on 64-bit libuafs
    2010-04-09 Andrew Deason    (1720) afsd: squash inode format warning
    2010-04-09 Andrew Deason    (1719) UKERNEL: prototype uafs_Shutdown
    2010-04-09 Andrew Deason    (1718) UKERNEL: Use real vnode type constants
    2010-04-09 Andrew Deason    (1717) UKERNEL: check for null afs_CurrentDir on shutdown
    2010-04-09 Andrew Deason    (1716) UKERNEL: add uafs_statvfs
    2010-04-09 Andrew Deason    (1715) Prevent uafs_readdir/closedir segfault
    2010-04-09 Russ Allbery     (1713) Update Debian packaging files
    2010-04-09 Russ Allbery     (1712) Add OpenAFS-debug.*.plist to .gitignore
    2010-04-08 Michael Meffie   (1601) pts mem -expandgroups option
    2010-04-08 Michael Meffie   (1600) pts mem -supergroup option
    2010-04-07 Russ Allbery     (1710) Explain in CellServDB man page that server lines can be omitted
    2010-04-07 Simon Wilkinson  (1705) Linux: kmap() not page_address()
    2010-04-07 Andrew Deason    (1709) Fix typo in bos_create manpage
    2010-04-07 Rod Widdowson    (1708) Make tests/afcp compile cleanly
    2010-04-07 Russ Allbery     (1706) Reallocate memory in aklog for the AFS ID string
    2010-04-07 Russ Allbery     (1704) Make src/rx/rx.c not executable
    2010-04-07 Russ Allbery     (1707) Improve demand-attach fileserver bos documentation
    2010-04-06 Jeffrey Altman   (1702) Windows: Support new Cygwin docbook stylesheet location
    2010-04-06 Jeffrey Altman   (1696) Windows: WinTorture Verbose mode display all logged messages
    2010-04-06 Jeffrey Altman   (1701) Windows: permit documentation to be built without binaries
    2010-04-06 Jeffrey Altman   (1699) Windows: tag is listitem not llstitem
    2010-04-06 Derrick Brashear (1700) make openafs 1.5.73.3
    2010-04-06 Derrick Brashear (1698) macos bulkstat avoid reclaiming vnodes
    2010-04-06 Derrick Brashear (1690) avoid macos bulkstat vlru when no non-dead vnodes exist
    2010-04-06 Derrick Brashear (1693) panic generation update
    2010-04-06 Jeffrey Altman   (1695) Windows: cm_UpdateVolumeLocation !append exts to num vol names
    2010-04-06 Jeffrey Altman   (1697) Rx: Remove conn_call_lock contention between rx_NewCall and rx_EndCall
    2010-04-05 Aditya Sarawgi   (1694) 	Replace kmodstat by kldstat
    2010-04-05 Jeffrey Altman   (1685) Fix usage of RX_CALL_TQ_WAIT flag
    2010-04-05 Derrick Brashear (1682) rx_ClearTransmitQueue should signal waiters when flushing
    2010-04-05 Derrick Brashear (1692) macos panic decoder update
    2010-04-02 Derrick Brashear (1687) macos 32 bit platform user address transform
    2010-04-02 Derrick Brashear (1688) make 1.5.73.2
    2010-04-02 Derrick Brashear (1684) freebsd switch back to condvar-based sleep
    2010-04-02 Derrick Brashear (1686) macos installer pane warning fix
    2010-04-02 Andrew Deason    (1681) tubik: Correct use of flags_cond and version_cond
    2010-04-02 Andrew Deason    (1680) Kill afs_inet_ntoa
    2010-04-02 Derrick Brashear (1683) freebsd glock assertions
    2010-04-01 Andrew Deason    (1678) fssync-debug: fix strict-aliasing problems
    2010-04-01 Simon Wilkinson  (1645) Fix formatting issues in src/afs
    2010-04-01 Benjamin Kaduk   (1677) Set a storeOps storeproc for the memcache case

### Patches merged into the stable branch

    Date       Author          Change# Description
    2010-05-19 Anders Kaseorg   (1988) Linux: replace invalidate_inode_pages
    2010-05-18 Antoine Verheijen (1911) OpenBSD: Use osi_obsd_Free() for all releases of OBSD
    2010-05-17 Michael Meffie   (1945) prdb_verify -rebuild with supergroups fix
    2010-05-16 Andrew Deason    (1943) Solaris: prevent AFS umount while busy
    2010-05-11 Andrew Deason    (1944) Solaris: shutdown in freevfs, not unmount
    2010-05-11 Andrew Deason    (1942) Solaris: return ENOTSUP for force-unmounts
    2010-05-05 Dan Hyde         (1843) viced-host-uuid-and-addr-hashing-corrections-20090530
    2010-05-05 Antoine Verheijen (1900) Fix pattern to detect i386-based OpenBSD system type
    2010-05-05 Antoine Verheijen (1901) OpenBSD: Fix bug in setpag() when group list is empty
    2010-04-13 Simon Wilkinson  (1581) Linux Keyrings: don't ignore error code from session keyring creation
    2010-04-13 Anders Kaseorg   (1373) Adjust afs_lockctl to compensate for byte-range lock fixes
    2010-04-09 Hans-Werner Paulsen (1711) Build and install PIC versions of libafsrpc and libafsauthent
    2010-04-01 Dan Hyde         (1595) VOL_LOCK needed when traversing DiskPartitionList

## Resolved Tickets

Here is a list of tickets that have been resolved since March 1, 2010:

    ticket # state     created       title
      15586: resolved  Oct 10, 2004  src/libafsrpc and src/shibafsrpc should be rationalized
      94658: resolved  Apr 15, 2008  Volumes without root directories are useless
     126366: resolved  Feb 05, 2010  OpenAFS 1.5.71 for Windows  - problem with DNS lookup
     126451: resolved  Feb 12, 2010  GetSomeSpace_r always looks in vain for deletable hosts
     126454: resolved  Feb 12, 2010  h_Hold_r callers not checking HOSTDELETED
     126497: resolved  Feb 15, 2010  volume callback breaks sent to all hosts
     126561: resolved  Feb 20, 2010  fcntl locks broken by linux-byte-range-locks-sensibility-20090526
     126846: resolved  Mar 30, 2010  Wrong quota calculation in windows graphical interface.
     126852: resolved  Mar 31, 2010  Can't create new Drive Letters per User on Windows Vista / 7
     126868: resolved  Apr 02, 2010  Kernel Panic MacOSX 10.6.3 OpenAFS 1.5.73.1
     126871: resolved  Apr 02, 2010  KernelPanic MacOSX 10.6.3 OpenAFS 1.5.73.2
     126962: resolved  Apr 14, 2010  DLL problem seven 64bits
     127020: resolved  Apr 26, 2010  Software license locallzed language versions
