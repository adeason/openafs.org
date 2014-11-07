---
title: OpenAFS Newsletter, Volume 2, Issue 3, March 2010
layout: page
category: newsletter
permalink: /newsletter/newsletter-2010-03-volume002-issue03.html
---

# OpenAFS Newsletter, Volume 2, Issue 3, March 2010

Welcome to the eleventh issue of the OpenAFS newsletter. This newsletter
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

OpenAFS versions 1.4.12 and 1.5.72 were released. 1.5.72
includes many bug fixes and support for OpenBSD 4.6.  Derrick Brashear
added a growl agent for Mac OS X so that AFS messages are displayed to the
user. The growl agent code is in the master branch.

1.4.12 includes many bug fixes and improvements, including support for Linux
2.6.33, a preference pane for Mac OS X, and support for MIT Kerberos 1.8.

Simon Wilkinson brought up a possible copyright issue where the source
code is under the IBM Public License, and the IETF submitters cannot
provide the provisions required in RFC 5738 when IPL-licensed source code,
even header files, needs to be included as part of an IETF submission.
Jeffrey Altman is working with IBM and some IP lawyers to see how this may
be resolved.

## Events

### Annual Best Practices Workshop

Plans are already underway for the seventh Workshop, to be held May 24-28,
2010, at the University of Illinois at Urbana-Champaign.  We hope to see
you there.

Web site: [http://workshop.openafs.org/afsbpw10/index.html](http://workshop.openafs.org/afsbpw10/index.html)

### European AFS Conference

The date for the 3rd European AFS & Kerberos Conference has been set. The
conference will take place in Pilsen, Czech Republic, from September 13 to
September 15, 2010. More details are forthcoming and will be posted at
[http://afs2010.civ.zcu.cz](http://afs2010.civ.zcu.cz). The conference is being hosted by Centre for
Information Technology, University of West Bohemia.

## AFS Protocol Standardization

Informal drafts that haven't been uploaded to the IETF web site:

Rx Spec:

[http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html](http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html)

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization](http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names)

Status: Active - Third call for review

Last Update: November 18, 2009

### AFS Callback Extensions

[http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo](http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo)

Status: Active - Needs more discussion

We need to decide whether we're going to wait for the RPC refresh changes
before publishing extended callbacks. My belief is that that's the only
factor currently delaying this document. The question here, essentially,
is whether anyone would deploy extended callbacks before deploying updated
RPCs. To date, nobody has said they would do so.

\--Simon Wilkinson

Last update: September 23, 2009

Expires: March 23, 2010

### DNS SRV Resource Records for AFS

[http://tools.ietf.org/html/draft-allbery-afs-srv-records](http://tools.ietf.org/html/draft-allbery-afs-srv-records)

Status: Submitted to IETF

It's been approved by the IESG as a proposed standard and is now in the
RFC Editor queue.  All the procedural hurdles have therefore been cleared,
and all that should remain is wordsmithing with the RFC Editor and final
publication.

\--Russ

### RXGK

[http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk](http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk)

Status: Active

Rxgk is a security layer for AFS which will support strong encryption and
authentication through Kerberos v5, GSI and any other GSSAPI security
mechanism.

Documents describing rxgk have been published and are being discussed on
the afs3-standardization list. To date, no major objections have been
raised in both public, and private, review.

rxgk implementation work is continuing, focusing this month on improving
token support. All of our tools currently assume that only a single token
type is in use, and all of the new RX security layers will require that
this be extended to support multiple different types. Two new pioctls
(based on work already done by Love in Arla) were proposed and discussed
on openafs-devel and an implementation produced. The kernel token store
was extended to support multiple token types, and aklog was refactored to
move the rxkad specific code out of the main loop.

A side effect of this work is that a number of changes have been made to
improve code quality in the cache manager.

Changes which are considered suitable for the 1.5.x series are in git -
look for changes with author sxw@your-file-system.com. A development tree,
which will be frequently rebased, is at
http://github.com/your-file-system/openafs-rxgk

\--Simon

### AFS3 ACL Rights

[http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions](http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions)

Status: Second draft

Last update: Jan 13, 2010

See the Per-File ACLs section for more info.

### Rx Security Object Providing Cleartext Peer Identity Assertions

[http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear](http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear)

Status: BCP

Last Update: February 1, 2010

### AFSVol Tag-Length-Value Remote Procedure Call Extensions

[http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv](http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv)

Status: BCP (second call for comments)

Last Update: November 16, 2009

## Projects

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

The salvaging performance improvements in gerrit 880 (volume group
cache) have been merged, and gerrit 1092 (parallel preattach
optimization) looks about ready to go. Several patches culminating in
gerrit 1406 (per-volume locks) have been submitted, which allow for
demand-salvages to occur at the same time as volume operations (as well
as other salvages) on the same partition. DAFS developer documentation
has been submitted in gerrit 1376.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Andrew Deason documented some of the FSSYNC commands. Jason Edgecombe
fixed some minor issues in the CellAlias man page and wrote a new
section for the Admin Guide that discusses how to tune the client cache
size.

### Pthreaded Ubik

Project Contact:

- Steven Jenkins <steven.jenkins@gmail.com>
- Andrew Deason <adeason@sinenomine.net>
- Alistair Ferguson <Alistair.Ferguson@morganstanley.com>

We've found a reproducible test case which exhibits the bug and expect a
patch to be completed by mid-March.

\--Alistair

Gerrit 1546 (add locks for addresses and cheader) has been submitted for
review, and with that, we now believe the vlserver to be thread-safe.
Since the vlserver thread-safety issues were the only known pthreaded
ubik issues, after 1546 we are aware of no further issues with pthreaded
ubik.

\--Andrew

### Kerberos v5 and multiple encryption types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

Bug fixes to work with MIT Kerberos 1.8, works.

Heimdal 1.3.1 - in progress.  Configuring Heimdal build to work with lwp
openafs has become more tricky.  Had some experimental success.

Installing from "build out of tree" - more fixes.

Started looking at design issues for split "rxkad/rxk5" cell.

\--Marcus

### Per-File ACLs

Project Contacts:

- Marc Dionne <marc.c.dionne@gmail.com>

Current status:

- An updated proposal will be posted to afs3-std - this is mostly to
iron out the expected semantics, particularly for dealing with legacy
clients.
- I plan to give a talk on the topic at the upcoming workshop

Code wise there is now some real progress:

- The existing code has been rebased to the current git master
- It's being broken down to smaller patches in git, and gradually
pushed to a fork on github.  This is not yet ready for public
consumption, but the idea is that the tree will be available for early
testers and reviewers before it goes to gerrit.  It is subject to
being rebased and respun as work progresses.
- The basics are functional, but with some assumptions that may have
to change later.  For instance it makes use of a field in the on-disk
vnode that I know conflicts with the OSD code.
- Current work is dealing with compatibility issues with older clients
and servers, volume moves and dumps, etc.

\--Marc

### Mac OS X OpenAFS Preference Pane

Project Contact:

- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

The preference pane has been stabilized a little but more. An issue has
been resolved in Mac OS X 10.6 where clicking the login icon would show
the icon again without showing the password text field when "get krb5
ticket at login time" option is on.

\--Claudio

### \*BSD Support

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

Support for OpenBSD 4.6 was included in 1.5.72.

### Google Summer of Code 2010

OpenAFS applied to be a mentoring organization in this year's Google
Summer of Code, which pays students up to $5000 to spend their summer
working on open source software. ( More details at
http://code.google.com/soc/ ) We've done this successfully for the last
two years, with major improvements such as disconnected operation
resulting from the programme. We need project ideas, mentors, and
students! If you have an idea that would make a suitable 3 month project
for a student developer or if you would be happy to remotely advise a
student over the course of the summer, please let us know. Google will
announce the list of accepted organizations on March 18th.

Please also advertise the programme to any students you come in contact
with, and if you are a student who is interested in participating, get in
touch.

\--Simon Wilkinson

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Rx OSD integration & Raw Vicep Access in Clients - August 2009
- S3 Front-end for AFS - November 2009
- Active Directory Backend for Ptserver - November 2009
- Virtual Machine Images - November 2009
- SetAG - December 2009
- Userspace cache manager - December 2009
- Extended Callback Information - January 2010
- Disconnected AFS support - February 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 50 (last month: 51)

    Patches merged into the master branch:
    Month   Number of Commits
    2010-03   52 (Partial month)
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
    2010-03  13 (Partial month)
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
    2010-03-13 Jeffrey Altman   (1531) afsadminutil: translate krb5 error messages on Windows
    2010-03-13 Michael Meffie   (1562) ihandle positional read and write
    2010-03-13 Jeffrey Altman   (1567) Windows: warnings removal for afskfw.c
    2010-03-13 Derrick Brashear (1538) afsdb lookup shouldn't leak memory on realname lookup
    2010-03-13 Michael Meffie   (1566) build on hpux again
    2010-03-12 Rainer Toebbicke (1311) Lockless path through afs_linux_dentry_revalidate
    2010-03-12 Andrew Deason    (1545) vlserver: make rxinfo threadsafe
    2010-03-12 Benjamin Kaduk   (1560) Allocate and free backing store for event mutices
    2010-03-12 Derrick Brashear (1554) freebsd per-event mutexes
    2010-03-10 Andrew Deason    (1557) vos: Mark longjmp-used variables as 'volatile'
    2010-03-10 Andrew Deason    (1559) vos: Avoid LWP stack overflow error on SIGINT
    2010-03-10 Andrew Deason    (1558) vos: Use IOMGR_SoftSig for signals
    2010-03-10 Derrick Brashear (1553) dynamic volume allocation
    2010-03-09 Derrick Brashear  (451) macos fsevents hinting
    2010-03-09 Andrew Deason    (1405) Add code for locking individual volumes on disk
    2010-03-09 Andrew Deason    (1550) vos: correct syncvldb -verbose server byte order
    2010-03-09 Andrew Deason    (1546) vlserver: Add locks for addresses and cheader
    2010-03-09 Derrick Brashear (1547) make tryevalfakestat really not block
    2010-03-05 Jeffrey Altman   (1521) Updating UserGuide with Kerberos v5 authentication
    2010-03-02 Derrick Brashear (1333) byte-range lock warning should include pid
    2010-02-27 Derrick Brashear (1386) update link order
    2010-02-26 Andrew Deason    (1406) DAFS: Replace partition locks with volume locks
    2010-02-26 Derrick Brashear (1403) restore internal xdr function names for kernelspace
    2010-02-25 Michael Meffie   (1092) DAFS: avoid volume lock contention during initialization
    2010-02-24 Simon Wilkinson  (1392) More warnings cleanup
    2010-02-24 Andrew Deason    (1235) Create missing root directory when ORPH_ATTACH
    2010-02-24 Derrick Brashear (1315) viced remove dead BreakVolumeCallBacks function
    2010-02-24 Andrew Deason    (1368) h_TossStuff_r: make sure host does not go away
    2010-02-24 Andrew Deason    (1367) h_TossStuff_r: check held-ness after lock
    2010-02-24 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2010-02-23 Evan Broder       (778) Increase the maximum number of sysnames
    2010-02-23 Anders Kaseorg   (1373) Adjust afs_lockctl to compensate for byte-range lock fixes
    2010-02-18 Simon Wilkinson  (1340) XDR: Stop the madness
    2010-02-15 Michael Meffie   (1001) return an error from afs_readdir when out of buffers
    2010-02-06 Dan Hyde         (1212) VTRANS_LOCK not needed in TryUnlock
    2010-02-05 Dan Hyde         (1213) VOL_LOCK needed when traversing DiskPartitionList
    2010-02-03 Dan Hyde         (1191) runningCalls: VOL_COUNT_LOCK vs VTRANS_LOCK
    2010-02-03 Derrick Brashear (1172) linux mmap anti-deadlock shouldn't break StoreAllSegments
    2010-02-03 Derrick Brashear (1201) basic kernel event system for afs cm
    2010-02-02 Simon Wilkinson  (1072) Unix CM: Conflate rxfs_[store,fetch]Variables
    2010-01-20 Simon Wilkinson  (1074) Unix CM: Include memcache's tiov in rxfs_context
    2010-01-14 Chas Williams - CONTRACTOR (1080) LINUX: you dont need to memset() after allocating credentials
    2009-11-29 Andrew Deason     (875) Make ubik use unsigned addresses
    2009-11-18 Andrew Deason     (709) Break origin's callback for RXAFS_Rename target
    2009-11-04 Andrew Deason     (436) Avoid unnecessarily updating .. in SAFSS_Rename
    2009-11-04 Michael Meffie    (215) Print throttled packet counts with rxdebug
    2009-09-09 Matt Benjamin     (435) clear stat flag on renamed directories
    2009-08-29 Matt Benjamin     (376) K5SSL by Marcus Watts
    2009-07-29 Michael Meffie    (147) Fix bosserver directory creation
    2009-07-24 Hartmut Reuter     (70) preparing rxosd integration: change in AFSFetchStatus



### Patches merged into the master branch

    Date       Author          Change# Description
    2010-03-13 Jeffrey Altman   (1529) Windows: afskfw - conditionalize use of krb5_get_error_message for KFW 3.1 and earlier
    2010-03-13 Jeffrey Altman   (1530) Windows: netidmgr - conditionalize use of krb5_get_error_message for KFW 3.1 and earlier
    2010-03-11 Derrick Brashear (1561) macos dropbox fix for finder
    2010-03-10 Derrick Brashear (1551) dkms configure correctly
    2010-03-10 Andrew Deason    (1556) Squash pthreaded vos warnings
    2010-03-10 Simon Wilkinson  (1555) Don't always use the local cell for db clients
    2010-03-09 Simon Wilkinson  (1552) Update RPM CellServDB
    2010-03-09 Andrew Deason    (1549) udebug: Fix byte ordering of last yes host
    2010-03-09 Andrew Deason    (1548) vldb_check: do not ntohl u_chars
    2010-03-09 Andrew Deason    (1404) Add FSYNC_VerifyCheckout
    2010-03-09 Andrew Deason    (1376) Add DAFS documentation overview for developers
    2010-03-09 Andrew Deason    (1358) Add VLockFileReinit
    2010-03-09 Andrew Deason    (1357) VLockFile: add a couple of asserts
    2010-03-09 Andrew Deason    (1356) Schedule all salvages via VScheduleSalvage_r
    2010-03-09 Andrew Deason    (1349) Add FSSYNC debug logging
    2010-03-09 Andrew Deason    (1390) Move *SYNC string translation out of fssync-debug
    2010-03-09 Andrew Deason    (1348) Do not rely on vol header for V*VolumeHandles_r
    2010-03-09 Derrick Brashear (1544) darwin report kext load address
    2010-03-09 Benjamin Kaduk   (1541) Export prototypes for osi_fbsd_{alloc,free} for use in rx
    2010-03-09 Benjamin Kaduk   (1540) Use correct types for UFS devices
    2010-03-09 Benjamin Kaduk   (1539) Use the correct API for msleep() in FBSD's afs_osi_TimedSleep()
    2010-03-09 Benjamin Kaduk   (1526) FBSD build finishes for me
    2010-03-08 Derrick Brashear (1537) afsconf srv lookup fill cellname
    2010-03-07 Derrick Brashear (1533) Begin support for OpenBSD 4.7
    2010-03-07 Derrick Brashear (1532) OpenBSD: eliminate use of VREF() macro
    2010-03-07 Benjamin Kaduk   (1528) Be type correct in osi_ThreadUnique() for FBSD
    2010-03-07 Benjamin Kaduk   (1527) FBSD module loads now
    2010-03-06 Jeffrey Altman   (1520) Windows: use krb5_get_error_message instead of error_message
    2010-03-06 Simon Wilkinson  (1524) Linux: Make keyring destructor remove all tokens
    2010-03-06 Simon Wilkinson  (1525) Linux: Fix builds on RHEL4
    2010-03-06 Marc Dionne      (1523) Linux: replace invalidate_inode_pages
    2010-03-06 Jeffrey Altman   (1519) Windows: use krb5_get_error_message to translate krb5 errors in afskfw library
    2010-03-06 Jeffrey Altman   (1518) Windows: use krb5_get_error_message in netidmgr_plugin
    2010-03-06 Jeffrey Altman   (1517) Windows: Add krb5 error message functions to loadfuncs header
    2010-03-05 Jeffrey Altman   (1514) Windows: reset local mount point count during freelance re-initialization
    2010-03-05 Simon Wilkinson  (1522) Linux : Don't leak GLOCK when writing CellServDB
    2010-03-05 Derrick Brashear (1513) add growl agent for macos
    2010-03-05 Derrick Brashear (1511) darwin afshelper fix startup check
    2010-03-04 Derrick Brashear (1512) evalmount copy out volid for sure
    2010-03-03 Derrick Brashear (1507) macos shutdown consistent behavior
    2010-03-03 Derrick Brashear (1505) add user warning facility via mariner for macos
    2010-03-03 Derrick Brashear (1504) support mariner messages sans vcache
    2010-03-03 Derrick Brashear (1503) rewrite marinerlogfetching
    2010-03-03 Derrick Brashear (1502) restore mariner storing message
    2010-03-03 Derrick Brashear (1501) de-printf the cache manager
    2010-03-03 Jason Edgecombe  (1308) Add a section on how to tune the AFS cache using xstat_cm_test
    2010-03-03 Marc Dionne      (1506) Remove duplicate make targets in tubik, cleanup dependencies
    2010-03-02 Derrick Brashear (1500) darwin vfsops ansification
    2010-03-02 Derrick Brashear (1499) afs_util don't use printf
    2010-03-02 Derrick Brashear (1371) BOP_MOVE and userspace move EXDEV helper
    2010-03-01 Claudio Bisegni  (1492) OSXPreferencePane checkAfsStatusForStartup method modification for search /afs volume for determinate if afs is on has been transfered into checkAfsStatus. checkAfsStatusForStartup method is used to check when afs start axitn system startup. Anyway these 
    2010-03-01 Marc Dionne      (1489) Don't pass NULL to strcmp
    2010-02-28 Benjamin Kaduk   (1491) More help for the FBSD build
    2010-02-28 Benjamin Kaduk   (1490) Make build progress farther
    2010-02-28 Derrick Brashear (1410) macos prefs pane more reliable running indicator
    2010-02-28 Jeffrey Altman   (1487) Windows: rx lowlevel nat ping
    2010-02-28 Derrick Brashear (1488) magic mount parser fix
    2010-02-27 Derrick Brashear (1408) macos prefs pane krb5 auth setup
    2010-02-27 Derrick Brashear (1379) irix syscall arg fix for rx
    2010-02-27 Derrick Brashear (1407) institute afsdb dns lookup timeout if we can
    2010-02-27 Derrick Brashear (1393) rx lowlevel nat ping
    2010-02-26 Andrew Deason    (1347) Convert ObtainSalvageLock to the VLockFile API
    2010-02-26 Marc Dionne      (1402) Enable parallel build for tubik
    2010-02-26 Derrick Brashear (1384) background daemon genericization
    2010-02-26 Derrick Brashear (1385) hush another afsd warning
    2010-02-25 Derrick Brashear (1382) darwin vnops code cleanup
    2010-02-25 Derrick Brashear (1381) darwin afscall syscall should set retval
    2010-02-25 Derrick Brashear (1399) macos bulkstat cleanup after racing stats
    2010-02-25 Rainer Toebbicke (1396) Do not leak information on partial success in RXAFS_InlineBulkStatus
    2010-02-25 Derrick Brashear (1383) correct magic vnode volumename parsing
    2010-02-25 Derrick Brashear (1380) irix kill efs and start pruning pre-65
    2010-02-25 Derrick Brashear (1378) irix cachemgr inode abstraction correction
    2010-02-24 Derrick Brashear (1391) freebsd initglock endif fix
    2010-02-24 Derrick Brashear (1388) remove dropbox attribute leak fix
    2010-02-24 Andrew Deason    (1346) Make VLockFile not DAFS-specific
    2010-02-24 Andrew Deason    (1345) VLockFile: init fd to INVALID_FD, not zero
    2010-02-24 Andrew Deason    (1344) VLockFile: Do not close fd on lock failure
    2010-02-24 Derrick Brashear (1314) viced avoid global pruclient during acl ops
    2010-02-23 Chaz Chandler    (1377) add limits.h to sysincludes.h on IRIX
    2010-02-23 Anders Kaseorg   (1351) Linux: autoconf.h is moving in 2.6.33
    2010-02-23 Anders Kaseorg   (1350) Linux: Use kbuild to check for UML
    2010-02-23 Anders Kaseorg   (1352) Linux: Fix conversion of whole-file locks
    2010-02-23 Anders Kaseorg   (1353) Adjust afs_lockctl to compensate for byte-range lock fixes
    2010-02-22 Andrew Deason    (1264) Abstract /vicepX header traversal
    2010-02-22 Andrew Deason    (1317) Allow GetSomeSpace_r to select an optimal host
    2010-02-22 Andrew Deason    (1330) h_TossStuff_r: make sure host does not go away
    2010-02-22 Derrick Brashear (1363) analyze warning fix
    2010-02-22 Andrew Deason    (1362) Prevent deadlock if fs_stateSave panics
    2010-02-22 Andrew Deason    (1305) Check for HOSTDELETED before h_Hold_r
    2010-02-22 Andrew Deason    (1304) Correct the h_Enumerate_r hostList safety check
    2010-02-22 Andrew Deason    (1312) h_TossStuff_r: check held-ness after lock
    2010-02-22 Derrick Brashear (1360) analyze paranoia
    2010-02-22 Derrick Brashear (1355) idledead client dont interrupt writes
    2010-02-19 Rainer Toebbicke (1343) Init ih_synced for new ihandle
    2010-02-19 Marc Dionne      (1342) Avoid dprintf conflict
    2010-02-19 Simon Wilkinson  (1341) Linux: bdi doesn't always have a name
    2010-02-18 Simon Wilkinson  (1339) Unix: Fix objdir builds
    2010-02-18 Simon Wilkinson  (1338) Add xdrmem and xdrlen to shlib builds
    2010-02-17 Andrew Deason    (1337) Add support for amd64_obsd46
    2010-02-17 Andrew Deason    (1336) Include stdint.h when using intptr_t
    2010-02-17 Derrick Brashear (1335) kill macos prior to panther
    2010-02-17 Andrew Deason    (1263) salvager: avoid needing temp files to stay around
    2010-02-17 Andrew Deason     (880) DAFS: Maintain viced volume group hierarchy cache
    2010-02-17 Andrew Deason    (1237) Add a general file-level locking API
    2010-02-17 Derrick Brashear (1332) linux bdi allocate memory
    2010-02-17 Simon Wilkinson  (1326) aklog: Refactor token management operations
    2010-02-17 Simon Wilkinson  (1325) aklog: Refactor token acquisition code
    2010-02-17 Simon Wilkinson  (1324) aklog: Use a function to print debug statements
    2010-02-17 Simon Wilkinson  (1334) aklog: Actually use new get_realm_from_cred fn
    2010-02-17 Simon Wilkinson  (1323) aklog: Tidy realm handling
    2010-02-17 Simon Wilkinson  (1322) aklog: Dispose of the pointless confname string
    2010-02-17 Simon Wilkinson  (1321) aklog: Clean up cell handling
    2010-02-17 Simon Wilkinson  (1320) aklog: Cosmetic cleanup
    2010-02-17 Simon Wilkinson  (1319) Unix CM: Tidy up the statistics interface
    2010-02-17 Jason Rogers     (1316) prdb_verify -rebuild with supergroups fix
    2010-02-17 Derrick Brashear (1303) macos bulkstat support
    2010-02-16 Derrick Brashear (1329) xdrmem for ukernel
    2010-02-16 Simon Wilkinson  (1328) Unix CM: Add xdrmem and xdrlen to kernel builds
    2010-02-16 Simon Wilkinson  (1327) Add xdrlen and xdrmem to pthread build
    2010-02-16 Simon Wilkinson  (1318) Remove the old new token interface
    2010-02-15 Adam Megacz      (1310) Have bosserver catch SIGTERM and shut down gracefully.
    2010-02-15 Jason Edgecombe  (1307) Some minor rewording and grammatical tweaks of the CellAlias man page
    2010-02-13 Derrick Brashear (1302) add bulk newvcache method
    2010-02-13 Marc Dionne      (1306) Initialize variable that can potentially be used uninitialized
    2010-02-12 Derrick Brashear (1301) darwin vn hold dead code removal
    2010-02-12 Derrick Brashear (1287) irix stdarg printing
    2010-02-12 Andrew Deason    (1236) Document FSSYNC commands
    2010-02-12 Derrick Brashear (1300) irix test kernel cleanup
    2010-02-12 Jeffrey Altman   (1298) Windows: Prevent explorer shell extension from crashing if symbolic link add fails
    2010-02-11 Derrick Brashear (1294) remove erroneous disabling of darwin rx event scheduling hook
    2010-02-11 Jeffrey Altman   (1292) Windows: 1.5.72
    2010-02-11 Derrick Brashear (1291) make unix 1.5.72
    2010-02-11 Derrick Brashear (1290) set minimum darwin kernel rx sleep
    2010-02-11 Simon Wilkinson  (1283) Linux: Use current_creds() if stashed creds fail
    2010-02-11 Jeffrey Altman   (1288) Remove warnings in src/ptserver/ptclient.c
    2010-02-10 Derrick Brashear (1286) tweak osi_Panic until all platforms can grok stdarg
    2010-02-10 Derrick Brashear (1285) remove osi_Panic prototype on irix
    2010-02-09 Derrick Brashear (1066) darwin rxevent sleep instead of polling
    2010-02-09 Derrick Brashear (1284) reclaim CCore1 vcache state
    2010-02-09 Jeffrey Altman   (1273) Windows: Permit Windows to build
    2010-02-09 Andrew Deason    (1238) Consolidate code for reading/writing vol headers
    2010-02-09 Rainer Toebbicke (1252) afs_TruncateAllSegments() make sure correct afs_size_t comparison is used when selecting dcache entries for truncation
    2010-02-09 Derrick Brashear (1281) ensure secObj is initialized in afs_ConnBySA
    2010-02-09 Derrick Brashear (1233) provide afs_osi_TimedSleep
    2010-02-09 Derrick Brashear (1225) internationalize comerr
    2010-02-09 Simon Wilkinson  (1280) Unix CM: Make cache bypass build again
    2010-02-09 Simon Wilkinson  (1279) Unix CM: Just use Bogus for VenusLogging
    2010-02-09 Simon Wilkinson  (1278) Unix CM: Wrap afs_pioctl.c at 80 columes
    2010-02-09 Simon Wilkinson  (1244) Refactor afs_ioctl code
    2010-02-09 Simon Wilkinson  (1243) UKERNEL: End the #define u insanity
    2010-02-09 Simon Wilkinson  (1242) Add rx security index enum
    2010-02-09 Andrew Deason    (1254) salvager: alias -f to -force
    2010-02-09 Simon Wilkinson  (1241) Unix CM: Simplify #ifdef ladder in lock.h
    2010-02-09 Simon Wilkinson  (1240) Unix CM: Indent #ifdef ladder in lock.h
    2010-02-09 Simon Wilkinson  (1239) Unix CM: Reorganise security object code
    2010-02-09 Simon Wilkinson  (1277) Initialise ptuser to NULL
    2010-02-09 Derrick Brashear (1276) OpenBSD: don't use AFS_GLOBAL_SUNLOCK on single processor system
    2010-02-09 Derrick Brashear (1275) OpenBSD: allow for more graceful shutdown
    2010-02-09 Derrick Brashear (1274) OpenBSD: fix lookup of network interfaces
    2010-02-09 Jeffrey Altman   (1272) Windows: add xdrlen
    2010-02-09 Derrick Brashear (1271) OpenBSD: move AFS memory type offet
    2010-02-09 Derrick Brashear (1269) Fix segmentation fault in vsu_GetVolumeID
    2010-02-09 Chaz Chandler    (1266) irix label changes rx subdir
    2010-02-09 Chaz Chandler    (1267) fix AFS_ASSERT_GLOCK on irix and aix
    2010-02-09 Derrick Brashear (1265) Add support for OpenBSD 4.6
    2010-02-08 Andrew Deason    (1253) tubik: Initialize mutexes and cvs
    2010-02-07 Derrick Brashear (1251) darwin vnodeops cleanup
    2010-02-07 Derrick Brashear (1249) macos package allow backrev
    2010-02-06 Derrick Brashear (1248) fetchstore reorg
    2010-02-06 Derrick Brashear (1247) set storeproc for non-linux
    2010-02-05 Derrick Brashear (1246) decode-panic deal with kextload
    2010-02-05 Jeffrey Altman   (1245) Windows: Remove use of AFS_AFSDB_ENV from kauth/user_nt.c
    2010-02-04 Derrick Brashear (1230) macos prefs pane spelling
    2010-02-04 Marc Dionne      (1229) Don't clear afs_stats_cmperf too early during shutdown
    2010-02-04 Derrick Brashear (1228) fakestat should preclude afsdb lookups too
    2010-02-03 Derrick Brashear (1227) macos installer scripts shouldn't echo
    2010-02-03 Derrick Brashear (1226) format fallout
    2010-02-03 Simon Wilkinson  (1224) Fix fs storebehind on files with 2 or more servers
    2010-02-03 Simon Wilkinson  (1223) Fix pioctl input and output handling
    2010-02-03 Simon Wilkinson  (1222) Make twiddle build
    2010-02-03 Simon Wilkinson  (1221) Add xdr_len, to work out required buffer size
    2010-02-03 Simon Wilkinson  (1220) Add xdr_mem to the Unix build
    2010-02-03 Simon Wilkinson   (796) Add printf format checks to the rest of tree
    2010-02-03 Simon Wilkinson   (795) Add printf format checks to rx
    2010-02-03 Simon Wilkinson  (1219) Add interface to select client security objects
    2010-02-03 Simon Wilkinson   (792) Add printf format checks to the cache manager
    2010-02-03 Simon Wilkinson   (794) Add printf format checks to afs_com_err()
    2010-02-03 Simon Wilkinson   (793) Add printf format checks to util's log functions
    2010-02-03 Simon Wilkinson  (1218) Don't pass tokens around the backup system
    2010-02-03 Simon Wilkinson  (1177) Common interface for server security objects
    2010-02-03 Simon Wilkinson  (1217) Document the extra options to fs getcacheparms
    2010-02-02 Simon Wilkinson  (1208) Add a set of strings for the InstallationCheck
    2010-02-02 Andrew Deason    (1211) Squash pthreaded ubik warnings
    2010-02-02 Andrew Deason    (1210) Use -A and -u in pthreaded ubik rxgen
    2010-02-02 Andrew Deason    (1209) Build utst_client for pthreaded ubik
    2010-02-02 Simon Wilkinson  (1206) Don't echo from the InstallationCheck script
    2010-02-02 Simon Wilkinson  (1205) Remove internal vldbClientInit prototype
    2010-02-02 Derrick Brashear (1200) icl 64 bit platform rationalization
    2010-02-02 Derrick Brashear (1199) icl trace code deduplication
    2010-02-02 Simon Wilkinson  (1204) Fix USS to use volser prototypes
    2010-02-02 Simon Wilkinson  (1202) xdr_proc_t really is different on linux26_i386
    2010-02-02 Simon Wilkinson  (1203) Darwin: Stop CM builds when errors occur
    2010-02-02 Marc Dionne      (1195) Linux: warning fix in osi_file.c
    2010-02-02 Simon Wilkinson  (1194) Linux: Fix breakage in llseek error handling
    2010-02-01 Derrick Brashear (1190) call afs_osi_suser correctly in PNewUuid
    2010-02-01 Derrick Brashear (1185) make 1.5.71 for unix
    2010-02-01 Jeffrey Altman   (1184) Windows: ChangeLog and Version Number for 1.5.71
    2010-02-01 Simon Wilkinson  (1073) Unix CM: Always use ->storeproc()

### Patches merged into the stable branch

    Date       Author          Change# Description
    2010-03-10 Andrew Deason    (1370) Allow GetSomeSpace_r to select an optimal host
    2010-03-10 Andrew Deason    (1369) Remove lih_r
    2010-03-08 Derrick Brashear (1536) remove fc_test from normal build
    2010-03-08 Derrick Brashear (1535) openafs 1.4.12
    2010-03-07 Antoine Verheijen (1510) Begin support for OpenBSD 4.7
    2010-03-07 Antoine Verheijen (1509) OpenBSD: eliminate use of VREF() macro
    2010-03-05 Derrick Brashear (1516) darwin afshelper fix startup check
    2010-03-05 Derrick Brashear (1515) correct cred mgmt typo
    2010-03-03 Derrick Brashear (1508) remove the force.. comments
    2010-03-03 Derrick Brashear (1498) Linux: bdi doesn't always have a name
    2010-03-03 Derrick Brashear (1497) linux bdi allocate memory
    2010-03-01 Derrick Brashear (1494) OSXPreferencePane checkAfsStatusForStartup method modification for search /afs volume for determinate if afs is on has been transfered into checkAfsStatus. checkAfsStatusForStartup method is used to check when afs start axitn system startup. Anyway these 
    2010-03-01 Derrick Brashear (1493) macos prefs pane more reliable running indicator
    2010-02-28 Derrick Brashear (1409) macos prefs pane krb5 auth setup
    2010-02-26 Chaz Chandler    (1400) add libsys.a to rxkad Makefile
    2010-02-25 Antoine Verheijen (1397) Fix (p)install of compile_et (addendum)
    2010-02-25 Derrick Brashear (1394) make openafs 1.4.12pre4
    2010-02-24 Derrick Brashear (1389) remove dropbox attribute leak fix
    2010-02-23 Anders Kaseorg   (1372) Linux: Fix conversion of whole-file locks
    2010-02-23 Anders Kaseorg   (1375) Linux: autoconf.h is moving in 2.6.33
    2010-02-23 Anders Kaseorg   (1374) Linux: Use kbuild to check for UML
    2010-02-22 Andrew Deason    (1366) Check for HOSTDELETED before h_Hold_r
    2010-02-22 Andrew Deason    (1365) Correct the h_Enumerate_r hostList safety check
    2010-02-22 Derrick Brashear (1364) analyze warning fix
    2010-02-22 Derrick Brashear (1361) analyze paranoia
    2010-02-22 Derrick Brashear (1359) idledead client dont interrupt writes
    2010-02-21 Anders Kaseorg   (1354) Linux: Remove unused LINUX_KERNEL_SELINUX test
    2010-02-11 Derrick Brashear (1293) make openafs 1.4.12pre3
    2010-02-11 Derrick Brashear (1289) Linux: Use current_creds() if stashed creds fail
    2010-02-09 Derrick Brashear (1282) afs_TruncateAllSegments() make sure correct afs_size_t comparison is used when selecting dcache entries for truncation
    2010-02-09 Antoine Verheijen (1257) OpenBSD: don't use AFS_GLOBAL_SUNLOCK on single processor system
    2010-02-09 Antoine Verheijen (1260) OpenBSD: allow for more graceful shutdown
    2010-02-09 Antoine Verheijen (1259) OpenBSD: fix lookup of network interfaces
    2010-02-09 Antoine Verheijen (1258) OpenBSD: move AFS memory type offet
    2010-02-09 Derrick Brashear (1270) Fix segmentation fault in vsu_GetVolumeID
    2010-02-09 Antoine Verheijen (1261) Add support for OpenBSD 4.6
    2010-02-09 Antoine Verheijen (1256) OpenBSD: allow code optimization to be turned off
    2010-02-07 Derrick Brashear (1250) macos package allow backrev
    2010-02-04 Derrick Brashear (1232) fakestat should preclude afsdb lookups too
    2010-02-04 Derrick Brashear (1231) macos prefs pane spelling
    2010-02-02 Derrick Brashear (1216) no debian packaging in 1.4.x
    2010-02-02 Derrick Brashear (1215) Add a set of strings for the InstallationCheck
    2010-02-02 Derrick Brashear (1214) create debugging kext package for MacOS
    2010-02-02 Derrick Brashear (1207) Don't echo from the InstallationCheck script
    2010-02-02 Derrick Brashear (1197) afs_vnop_attrs: syntax error in conditional expression
    2010-02-01 Derrick Brashear (1193) call afs_osi_suser correctly in PNewUuid
    2010-02-01 Derrick Brashear (1186) make 1.4.12 rc2
    2010-02-01 Derrick Brashear (1183) rx idledeadtime don't track window wait

## Resolved Tickets

Here is a list of tickets that have been resolved since February 1, 2010:

    ticket # state     created       title
       1435: resolved  May 08, 2003  Re: [OpenAFS-devel] 1.2.9: Pthreads and signals combination is
  broken.
      16876: resolved  Dec 17, 2004  'make install' on Solaris installs kdump incorrectly
      17092: resolved  Dec 29, 2004  negative block after salvage
      20884: resolved  Aug 16, 2005  [PATCH] don't bother with aklog.c
      21357: resolved  Sep 04, 2005  AFSDB lookups w/ djbdns dnscache
      22341: resolved  Oct 14, 2005  rc7 vs solaris9u8/sparc: deadlock
      22621: resolved  Oct 24, 2005  tbutc-solaris-and-vos-api-fixes-20051024 does not build
      26101: resolved  Jan 30, 2006  os x, 10.4.4, 1.4.1-rc5, server hangs cause afsd to die
      58498: resolved  Apr 04, 2007  OpenAFS 1.4.2 kernel panic
      76728: resolved  Nov 08, 2007  releasing volume in partially DAFS cell fails
      78814: resolved  Nov 29, 2007  OpenAFS 1.4.5 failing to install system call hooks on RHEL 5.1 x86_64
      80601: resolved  Dec 17, 2007  OpenAFS startup fails silently on MacOSX if network is not yet up
      89479: resolved  Mar 10, 2008  AFSCommander application code
     110502: resolved  Aug 05, 2008  Leopard: aklog unknown error for expired tickets
     123932: resolved  Dec 13, 2008  NaT Consumption on openafs-1.4.8-1.1.1
     123933: resolved  Dec 13, 2008  some UNTESTED changes to compile FBSD 8-CURRENT
     123937: resolved  Dec 14, 2008  Derrick review only: macroify VOP_*ATTR
     124916: resolved  Jun 10, 2009  DAFS bos salvage uses ambiguous salvager flag
     124975: resolved  Jun 23, 2009  fix rxgen in various Makefiles in HEAD
     124977: resolved  Jun 23, 2009  properly initialize pthreaded ubik mutexes & condvars
     124995: resolved  Jun 26, 2009  Kernel panic with OpenAFS 1.4.10 under Mac OS X 10.5.7/ppc
     125407: resolved  Sep 18, 2009  Snow Leopard, Large Cache Size
     125490: resolved  Oct 13, 2009  libraries that call exit() and have executable stacks
     125491: resolved  Oct 13, 2009  Libraries with executable stacks
     126069: resolved  Jan 04, 2010  Free kernel memory allocations at shutdown
     126107: resolved  Jan 08, 2010  emacs out of AFS server space locks compute node in D wait state
     126317: resolved  Feb 01, 2010  OpenAFS-1.4.12pre2  afs_vnop_attrs.c fails to compile on sun4x_515, sunx86_510 and sun4x_59
     126322: resolved  Feb 02, 2010  Less than useful error message when using 10.5 installer on 10.6
     126514: resolved  Feb 16, 2010  Linux: Ooops in __wake_up_common (from bdi_start_fn)
     126628: resolved  Feb 26, 2010  Mac OS PrefPane prevents all logins (munged /etc/authorization)
     126678: resolved  Mar 05, 2010  Linux: 1.5.x doesn't build on RHEL4
     126716: resolved  Mar 10, 2010  1.5.72's vos examine doesn't use cell provided by -cell argument
