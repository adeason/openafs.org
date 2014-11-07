---
title: OpenAFS Newsletter, Volume 2, Issue 4, April 2010
---

# OpenAFS Newsletter, Volume 2, Issue 4, April 2010

Welcome to the twelveth issue of the OpenAFS newsletter. This newsletter
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

OpenAFS version 1.5.73 was released on March 24. It was followed by three
point releases to fix some issues. The latest version is 1.5.73.3. The
gatekeepers are asking for people to really start testing the 1.5.x
releases on Unix machines to help iron out bugs before 1.6. To help people
with the testing efforts, Russ Allbery has uploaded new Debian packages:

I've uploaded Debian packages of 1.5.73.3 plus some additional recent
patches to Debian experimental.  I should be able to keep the packages up
to date with subsequent 1.5.x releases going forward.

Due to the new libkopenafs1 package, the upload will have to go through
NEW, so it will be a little bit before they show up in Debian.

\--Russ Allbery

The instructions for contributing to OpenAFS have been revised for using
Git. These instructions are in the README.git file in each release.

The growl agent for Mac OS X is included in 1.5.73, but it's not well
integrated yet. Initial feedback is positive and testers are
welcome. Please send any feedback ot the port-darwin@openafs.org mailing
list.

A new version of the AFS PERL API was released. For more information and
downloads, go to [http://www.mpa-garching.mpg.de/kwiki/nog/afsperl/](http://www.mpa-garching.mpg.de/kwiki/nog/afsperl/)

## Events

### Annual Best Practices Workshop

Plans are already underway for the seventh Workshop, to be held May 24-28,
2010, at the University of Illinois at Urbana-Champaign.  We hope to see
you there.

Web site: [http://workshop.openafs.org/afsbpw10/index.html](http://workshop.openafs.org/afsbpw10/index.html)

Register by April 14, 2010 to get the best prices.  AFS and Kerberos
tutorials are $100 each, the Workshop itself is $150, or register for
all three for only $300.

After April 14, prices will go up, so register now and save.

A tentative schedule is available. Further details, including
social events, is still forthcoming.

Hotel and travel information is also available.

We'll be looking forward to meeting you at Illinois next month!

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

This draft is in the very early stages. Mike Meffie and Tom Keiser are the
current owners of this proposal. Nickolai Zeldovich wrote the original
draft. Mike and Tom have started updating the draft with Nickolai's
permission. A formal specification of Rx is needed for a basis for other
IETF proposals.

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization](http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names)

Status: Active - Third call for review

Last Update: November 18, 2009

Expires: May 22, 2010

### AFS Callback Extensions

[http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo](http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo)

Status: Active - Waiting on RPC refresh

This proposal will be rewritten with references to the RPC time refresh.

Last update: September 23, 2009

Expires: March 23, 2010

### DNS SRV Resource Records for AFS

[http://tools.ietf.org/html/draft-allbery-afs-srv-records](http://tools.ietf.org/html/draft-allbery-afs-srv-records)

Status: Submitted to IETF

Still in the RFC Editor queue, waiting for them to have a chance to work
on it.

\--Russ

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

Last update: Jan 13, 2010

See the Per-File ACLs section for more info.

### Rx Security Object Providing Cleartext Peer Identity Assertions

[http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear](http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear)

Status: Second draft

Last Update: February 1, 2010

The Rx clear security class will improve on the rxnull security object by
eliminating certain race conditions related to IPv4 address changes.  A
\-02 revision of this internet draft will be forthcoming in the next few
days, which will update the introduction and security considerations
sections of the memo.  Everyone is invited to review this document, and
comments should be sent to the afs3-standardization@grand.central.org
mailing list.

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

## Projects

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

Gerrit 1406 (per-volume locks) has been merged along with the related
changes, and thus we can now salvage at the same time as volume
operations as well as other salvages. Gerrit 1092 is unfortunately still
not merged; we encourage additional review from anyone who can. Current
DAFS development involves adding background I/O threads to the salvager
code, and later making demand-salvages spawn as threads instead of
processes. Code for that should be available shortly.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Davor Ocelic is working on writing man pages for the new demand-attach
binaries that aren't yet documented.  The man page for state\_analyzer has
been committed.



### Pthreaded Ubik

Project Contact:

- Steven Jenkins <steven.jenkins@gmail.com>
- Andrew Deason <adeason@sinenomine.net>
- Alistair Ferguson <Alistair.Ferguson@morganstanley.com>

Gerrit 1546 (add locks for addresses and cheader) has been submitted for
review, and with that, we now believe the vlserver to be thread-safe.
Since the vlserver thread-safety issues were the only known pthreaded ubik
issues, after 1546 we are aware of no further issues with pthreaded ubik.

\--Steven

We're still discussing what solution to use in gerrit 1546 (add locks
for the vldb ubik cache). Additional problems affecting pthreaded ubik
were found and fixed in gerrit 1680 (kill afs\_inet\_ntoa) and 1681
(correct use of flags\_cond and version\_cond).

\--Andrew

This project will likely be dropped as a separate project in a couple of
issues of the newsletter when this project is fully merged into the
mainline OpenAFS code.

### Kerberos v5 and multiple encryption types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

I was hoping to have some time this week - got distracted by other
matters.  I do have one change of interest: the "tokens expired" message
which formerly looked like this:

    Feb 22 10:23:08 lancashire kernel: afs: Tokens for user of AFS id 555 for cell cats.umich.edu expired now

(where 555 was a fixed constant because the cache manager doesn't know
what viceid the user has), now looks like this:

    Apr 3 04:55:37 lancashire kernel: afs: Tokens for mdw@CATS.UMICH.EDU for cell cats.umich.edu expired now

I think that's an improvement.

Heimdal has some annoying weirdness with key types and checksums.
In 1.3.1 (at least,) the verify checksum logic insists only one
checksum algorithm is acceptable per key type.  The standards documents
do not forbid this interpetation, but don't exactly require it.
Sorting out acceptable checksum algorithms between various kerberos
distributions continues to be a problem.

I'm hoping to do a code drop soon.  It will probably be a complete
copy of source not just diffs.  I was overly aggressive about fixing
tabs and now have to "undo" some fixes to patches.  Blech.

\--Marcus

### Per-File ACLs

Project Contacts:

- Marc Dionne <marc.c.dionne@gmail.com>

Current status:

- I plan to give a talk on the topic at the upcoming workshop

\--Marc

### Mac OS X OpenAFS Preference Pane

Project Contact:

- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

The preference pane has been updated to allow the renewal of Kerberos
tickets. The GUI and afs backgrounder were updated to accomodate this
change.

\--Claudio

### \*BSD Support

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

Commit 028240329c09b6a311cb85736f41d75f7ee7a01f deals with some updated VFS calls in FreeBSD.

### Userspace cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

I've finally managed to find time to work on this again, resulting in
gerrit changes 1714-1726 which give a FUSE OpenAFS/libuafs client.
Functionality improvements over previous libuafs code include fixed
support for AFSDB and fakestat. Support will be forthcoming for some
pioctl operations (lsmount, rmmount, getacl, setacl, checkservers) and
perl SWIG bindings.

I will be presenting at AFSBPW 2010 about libuafs, on its potential uses
and how to use it.

\--Andrew

### S3 Front-end for AFS

Project Contacts:

- Fabrizio Manfredi <fabrizio.manfredi@gmail.com>
- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

We have a generic implementation in alpha test, without authentication
and specific AFS ACL support. We hope to release a first public beta at
the end of the April ( without authentication).

\--Fabrizio

### Virtual Machine Images

Project Contact:

- Fabrizio Manfredi <fabrizio.manfredi@gmail.com>

The Virtual Machine Images are updated, now the operating system is Centos
5.4 with openafs 1.4.12, in the new distribution is also present the AFS
perl API with example scripts. If you want, you can downgrade to openafs
1.4.11 with a simple snapshot rollback.  The images are in vmware format
only, you can download from:
http://sourceforge.net/projects/s3afs/files/openafs-1.4.12-vm

\--Fabrizio

### Google Summer of Code 2010

Google will be doing their Summer of Code again in 2010.  We're proud to
announce that for the third year, OpenAFS will be participating as a
mentoring organization.

\--Simon

Accepted student proposals will be announced on April 26.

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Rx OSD integration & Raw Vicep Access in Clients - August 2009
- Active Directory Backend for Ptserver - November 2009
- SetAG - December 2009
- Extended Callback Information - January 2010
- Disconnected AFS support - February 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 35 (last month: 50)

    Patches merged into the master branch:
    Month   Number of Commits
    2010-04   53 (Partial month)
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
    2010-04   2 (Partial month)
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
    2010-04-11 Jonathan A. Kollasch (1738) NetBSD 5.0 support.
    2010-04-11 Tharidu Fernando (1736) Windows: Secure C String usage in src\WINNT\afsd\fs.c
    2010-04-10 Andrew Deason    (1614) Add the Jabber MUC to the support page
    2010-04-10 Andrew Deason    (1723) Split afsd into afsd.c and afsd_kernel.c
    2010-04-09 Marc Dionne      (1640) Fileserver capabilities support for the UNIX client
    2010-04-09 Andrew Deason    (1725) Add a FUSE implementation for afsd
    2010-04-09 Andrew Deason    (1724) Make libuafs usable with afsd.o
    2010-04-09 Andrew Deason    (1726) Allow afsd.fuse to build on darwin / amd64 linux
    2010-04-05 Benjamin Kaduk   (1691) Add entries for FBSD 8.1 and 9.0
    2010-03-31 Andrew Deason    (1546) Add locks around updating the VLDB ubik cache
    2010-03-28 Derrick Brashear (1333) byte-range lock warning should include pid
    2010-03-26 Rainer Toebbicke (1311) Lockless path through afs_linux_dentry_revalidate
    2010-03-23 Derrick Brashear (1625) preliminary support for pinned vcaches
    2010-03-19 Michael Meffie    (215) rxdebug: show delayed abort packet count for rx peers
    2010-03-17 Michael Meffie   (1562) ihandle positional read and write
    2010-03-17 Simon Wilkinson  (1581) Linux Keyrings: don't ignore error code from session keyring creation
    2010-03-17 Derrick Brashear (1553) dynamic volume allocation
    2010-02-25 Michael Meffie   (1092) DAFS: avoid volume lock contention during initialization
    2010-02-24 Simon Wilkinson  (1392) More warnings cleanup
    2010-02-24 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2010-02-23 Anders Kaseorg   (1373) Adjust afs_lockctl to compensate for byte-range lock fixes
    2010-02-15 Michael Meffie   (1001) return an error from afs_readdir when out of buffers
    2010-02-06 Dan Hyde         (1212) VTRANS_LOCK not needed in TryUnlock
    2010-02-03 Dan Hyde         (1191) runningCalls: VOL_COUNT_LOCK vs VTRANS_LOCK
    2010-02-03 Derrick Brashear (1172) linux mmap anti-deadlock shouldn't break StoreAllSegments
    2010-02-03 Derrick Brashear (1201) basic kernel event system for afs cm
    2010-02-02 Simon Wilkinson  (1072) Unix CM: Conflate rxfs_[store,fetch]Variables
    2010-01-20 Simon Wilkinson  (1074) Unix CM: Include memcache's tiov in rxfs_context
    2009-11-29 Andrew Deason     (875) Make ubik use unsigned addresses
    2009-11-18 Andrew Deason     (709) Break origin's callback for RXAFS_Rename target
    2009-11-04 Andrew Deason     (436) Avoid unnecessarily updating .. in SAFSS_Rename
    2009-09-09 Matt Benjamin     (435) clear stat flag on renamed directories
    2009-08-29 Matt Benjamin     (376) K5SSL by Marcus Watts
    2009-07-29 Michael Meffie    (147) Fix bosserver directory creation
    2009-07-24 Hartmut Reuter     (70) preparing rxosd integration: change in AFSFetchStatus



### Patches merged into the master branch

    Date       Author          Change# Description
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
    2010-03-31 Benjamin Kaduk   (1676) Fix build for FBSD80
    2010-03-31 Benjamin Kaduk   (1675) Update to the new thread world order for FBSD
    2010-03-31 Benjamin Kaduk   (1674) Include limits.h for FBSD
    2010-03-31 Derrick Brashear (1670) openafs 1.5.73.1
    2010-03-31 Benjamin Kaduk   (1672) Make GCPAGs_perproc_func cleaner for FBSD case
    2010-03-31 Jonathan Billings (1671) Updated RedHat RPM spec file to include unreferenced files
    2010-03-30 Jonathan Billings (1669) Move restorevol to bin from sbin in make dest
    2010-03-30 Derrick Brashear (1668) darwin notify avoid reentrant vfs context panic
    2010-03-30 Russ Allbery     (1667) Update VCS instructions for Git
    2010-03-30 Benjamin Kaduk   (1665) Catch up to dynamically-sized cr_groups in FBSD80
    2010-03-29 Davor Ocelic     (1666) Minor state_analyzer manpage corrections
    2010-03-29 Rod Widdowson    (1649) Render the IP address for the "Ubik: Lost contact with sync-site" log message in the same way that all other IP addresses are (via afs_inet_ntoa, rather than stripping the buytes out in a manner which assumes a specific endianism).
    2010-03-29 Davor Ocelic     (1655) Initial; add state_analyzer manpage
    2010-03-28 Simon Wilkinson  (1042) Linux: Replace invalidate_inode_pages
    2010-03-28 Jeffrey Altman   (1664) Windows: buffers whose offsets are beyond EOF should be zero filled and locally allocated
    2010-03-27 Claudio Bisegni  (1656) GUI Update for Kerberos Ticket Renew
    2010-03-27 Derrick Brashear (1663) aklog pt error table warning fix
    2010-03-27 Derrick Brashear (1661) aklog more error tables
    2010-03-27 Chas Williams - CONTRACTOR (1080) LINUX: you dont need to memset() after allocating credentials
    2010-03-25 Jeffrey Altman   (1660) Windows: afslogon.dll vs windows 7
    2010-03-25 Jeffrey Altman   (1659) Windows: aklog must reset viceId to 0 before pr_CreateUser call
    2010-03-25 Jeffrey Altman   (1658) Windows: output pt error messages as strings
    2010-03-24 Derrick Brashear (1651) growl agent should handle port busy
    2010-03-24 Derrick Brashear (1654) avoid double-free cell name canonicalization
    2010-03-24 Derrick Brashear (1648) afsdump warning killing
    2010-03-24 Simon Wilkinson  (1647) Linux : Apply more dget_parent() pixie dust
    2010-03-24 Derrick Brashear (1642) make 1.5.73 relnotes
    2010-03-24 Derrick Brashear (1620) openafs 1.5.73 version strings
    2010-03-24 Jeffrey Altman   (1521) Updating UserGuide with Kerberos v5 authentication
    2010-03-24 Asanka Herath    (1633) Windows: Use a timestamp for the minidump filename
    2010-03-24 Asanka Herath    (1632) Windows: Monitor requests and gather diagnostics before a timeout
    2010-03-24 Derrick Brashear (1641) add missed release notes
    2010-03-24 Jeffrey Altman   (1636) Windows: changelog for 1.5.73
    2010-03-23 Jeffrey Altman   (1639) Windows: cm_attrs_t requires inclusion of cm_vnodeops.h
    2010-03-23 Jeffrey Altman   (1638) Windows LWP and UNIX LWP do not have the same lwp_cpptr structure
    2010-03-23 Marc Dionne      (1637) Warning fix: print burstWait fields
    2010-03-23 Marc Dionne      (1635) Fix #ifdef typo
    2010-03-23 Marc Dionne      (1634) Define __USE_XOPEN conditionally
    2010-03-23 Asanka Herath    (1602) Windows: Make default mode bits configurable
    2010-03-23 Derrick Brashear (1629) remove vnop needs discon lock
    2010-03-23 Claudio Bisegni  (1606) Develop Kerberos renew system for ticket
    2010-03-23 Derrick Brashear (1631) kill MultiBreakVolumeCallBack too
    2010-03-23 Andrew Deason    (1628) Remove BreakVolumeCallBacks prototype
    2010-03-23 Russ Allbery     (1589) vldb_check man page should say -vheader, not -pheader
    2010-03-23 Andrew Deason    (1550) vos: correct syncvldb -verbose server byte order
    2010-03-23 Derrick Brashear (1547) make tryevalfakestat really not block
    2010-03-23 Derrick Brashear (1315) viced remove dead BreakVolumeCallBacks function
    2010-03-23 Andrew Deason    (1559) vos: Avoid LWP stack overflow error on SIGINT
    2010-03-23 Andrew Deason    (1558) vos: Use IOMGR_SoftSig for signals
    2010-03-23 Andrew Deason    (1557) vos: Mark longjmp-used variables as 'volatile'
    2010-03-23 Russ Allbery     (1617) Fix strict aliasing problems or add -fno-strict-aliasing
    2010-03-22 Andrew Deason    (1582) Use AC_USE_SYSTEM_EXTENSIONS
    2010-03-22 Derrick Brashear (1590) aix mount failure unlock and seterror
    2010-03-22 Derrick Brashear (1386) update link order
    2010-03-22 Simon Wilkinson  (1340) XDR: Stop the madness
    2010-03-22 Russ Allbery     (1616) Use sigset_t and sigfillset instead of memset
    2010-03-22 Russ Allbery     (1615) Move non-executable stack assembly code to end of file
    2010-03-22 Derrick Brashear (1599) multibreak callbacks add host marking
    2010-03-21 Derrick Brashear (1611) aix vfs table entry in rc script
    2010-03-21 Derrick Brashear (1610) salvage variable initialization
    2010-03-21 Derrick Brashear (1598) comment assumptions in lih0_r
    2010-03-21 Andrew Deason    (1235) Create missing root directory when ORPH_ATTACH
    2010-03-21 Derrick Brashear (1609) aix krb5 error message handling
    2010-03-21 Derrick Brashear (1608) panic prototype for aix 6
    2010-03-21 Simon Wilkinson  (1577) Don't count root session keyrings against quota
    2010-03-20 Derrick Brashear  (451) macos fsevents hinting
    2010-03-19 Jeffrey Altman   (1531) afsadminutil: translate krb5 error messages on Windows
    2010-03-19 Andrew Deason    (1596) volume_inline.h does not need sys/file.h
    2010-03-19 Andrew Deason    (1406) DAFS: Replace partition locks with volume locks
    2010-03-19 Derrick Brashear (1594) macos uninstall redux
    2010-03-19 Derrick Brashear (1593) update macos uninstaller
    2010-03-19 Dan Hyde         (1213) VOL_LOCK needed when traversing DiskPartitionList
    2010-03-18 Benjamin Kaduk   (1587) Catch up with FBSD80's removal of thread argument to VFS calls
    2010-03-18 Derrick Brashear (1572) aix vnode hold simplification
    2010-03-18 Derrick Brashear (1584) regain glock on storedata error exit
    2010-03-18 Derrick Brashear (1583) kill apsl afssettings and fstab
    2010-03-18 Evan Broder       (778) Increase the maximum number of sysnames
    2010-03-17 Andrew Deason    (1405) Add code for locking individual volumes on disk
    2010-03-17 Benjamin Kaduk   (1576) Avoid panic on shutdown with memcache and INVARIANTS
    2010-03-17 Benjamin Kaduk   (1560) Allocate and free backing store for event mutices
    2010-03-16 Derrick Brashear (1573) rx nat event connection reference
    2010-03-16 Marc Dionne      (1575) growlagent: remove generated Makefile with make distclean
    2010-03-15 Antoine Verheijen (1574) Remove return of value for afs_MarinerLogFetch()
    2010-03-15 Derrick Brashear (1554) freebsd per-event mutexes
    2010-03-15 Andrew Deason    (1545) vlserver: make rxinfo threadsafe
    2010-03-15 Derrick Brashear (1538) afsdb lookup shouldn't leak memory on realname lookup
    2010-03-15 Michael Meffie   (1570) squash warning in db_verify
    2010-03-13 Jeffrey Altman   (1567) Windows: warnings removal for afskfw.c
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

### Patches merged into the stable branch

    Date       Author          Change# Description
    2010-04-09 Hans-Werner Paulsen (1711) Build and install PIC versions of libafsrpc and libafsauthent
    2010-04-01 Dan Hyde         (1595) VOL_LOCK needed when traversing DiskPartitionList
    2010-03-30 Simon Wilkinson  (1580) Linux: don't count pag keys against root's keyring quotas
    2010-03-25 Marc Dionne      (1657) Print rxdebug statistics as unsigned values
    2010-03-24 Evan Broder      (1650) Increase the maximum number of sysnames
    2010-03-23 Dan Hyde         (1588) volmonitor keep vtrans lock
    2010-03-23 Andrew Deason    (1627) Add support for amd64_obsd46
    2010-03-23 Andrew Deason    (1626) Add amd64 subtarget for OpenBSD
    2010-03-23 Andrew Deason    (1624) libafs: WRITEPAGE_ACTIVATE is 2.6-only
    2010-03-23 Andrew Deason    (1613) Create missing root directory when ORPH_ATTACH
    2010-03-23 Andrew Deason    (1623) libafs: afs_backing_dev_info is 2.6-only
    2010-03-23 Andrew Deason    (1622) libafs: Remove some unused functions
    2010-03-22 Russ Allbery     (1618) Move non-executable stack assembly code to end of file
    2010-03-18 Dan Hyde         (1586) volmonitor copy link before calling free
    2010-03-17 Andrew Deason    (1368) h_TossStuff_r: make sure host does not go away
    2010-03-17 Andrew Deason    (1367) h_TossStuff_r: check held-ness after lock
    2010-03-15 Michael Meffie   (1571) Avoid 'static __inline' on HPUX
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

## Resolved Tickets

Here is a list of tickets that have been resolved since March 1, 2010:

    ticket # state     created       title
      21423: resolved  Sep 07, 2005  Enhanced auto CACHESIZE code for afs.rc.linux
      22608: resolved  Oct 24, 2005  redhat-4 afs.rc smp startup broke
      23229: resolved  Nov 16, 2005  Openafs 1.4.0 cache on ext3 volume causes massive filesystem corruption
      36725: resolved  Aug 01, 2006  Relicense afssettings.m under saner license
      37658: resolved  Aug 14, 2006  openafs-1.4.1 libafsrpc missing symbols x86_64
      41823: resolved  Oct 05, 2006  reliability bug in caching seeked files ...
      49718: resolved  Dec 19, 2006  vos dump fails on amd64_linux26 client
      53759: resolved  Feb 11, 2007  1.4.2 Debian sarge afsd crash in afs_checkrootvolume
      54062: resolved  Feb 14, 2007  openafs 1.4.3rc2 still coredumps on openbsd40
      54299: resolved  Feb 17, 2007  problem after volume moves with 1.5.15
      92653: resolved  Apr 01, 2008  1.4.7pre2 - Dependency on /boot/config-{kernel-version}
     106150: resolved  Jul 06, 2008  Kernel memory leak with 1.4.7 on Linux 2.6.25
     107089: resolved  Jul 12, 2008  Kernel panic -- 1.5.39
     110696: resolved  Aug 06, 2008  OpenAFS 1.4.7 on Mac OS X 10.5.x:  intermittent access failures
     112681: resolved  Aug 19, 2008  RHEL4 Kernel Panic (firefox 3 related?)
     117415: resolved  Sep 24, 2008  Is there any script to uninstall OpenAFS on Mac OS X 10.5
     123798: resolved  Dec 01, 2008  freebsd client panics if no root.afs
     123806: resolved  Dec 03, 2008  nbsd-44 pass 1
     123820: resolved  Dec 05, 2008  Request for multiple realm support in 1.4.x
     124083: resolved  Jan 03, 2009  afssettings does not use build system correctly
     124591: resolved  Apr 04, 2009  freebsd 8 wip
     124761: resolved  May 11, 2009  Issues blocked for inclusion in future stable releases
     124877: resolved  May 27, 2009  obsd 1_5_x fixups
     125634: resolved  Nov 12, 2009  OpenAFS bug: Uninstall.command for Mac OS X does not work (fix attached)
     126067: resolved  Jan 04, 2010  rewrite afs_MemWriteBlk() using afs_MemWritevBlk()
     126107: resolved  Jan 08, 2010  emacs out of AFS server space locks compute node in D wait state
     126514: resolved  Feb 16, 2010  Linux: Ooops in __wake_up_common (from bdi_start_fn)
     126678: resolved  Mar 05, 2010  Linux: 1.5.x doesn't build on RHEL4
     126716: resolved  Mar 10, 2010  1.5.72's vos examine doesn't use cell provided by -cell argument
     126794: resolved  Mar 22, 2010  Wince when foreign bull-dogs sent out their threate
     126812: resolved  Mar 24, 2010  OpenAFS 1.5.73 MacOSX 10.6.2 growlagent-openafs crashes
     126813: resolved  Mar 24, 2010  OpenAFS 1.5.73 aklog crash
