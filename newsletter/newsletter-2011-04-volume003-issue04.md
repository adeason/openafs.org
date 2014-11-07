---
title: OpenAFS Newsletter, Volume 3, Issue 4, April 2011
---

# OpenAFS Newsletter, Volume 3, Issue 4, April 2011

Welcome to the April issue of the OpenAFS newsletter. This newsletter
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

1.6.0rc4 was released.  It's available from
[http://www.openafs.org/release/openafs-1.6.0pre4.html](http://www.openafs.org/release/openafs-1.6.0pre4.html). it includes many
bugfixes. The release of version 1.6.0 is imminent.

Linux kernels beyond 2.6.38 are not expected to be supported in future
releases of the 1.4.x series because of significant kernel changes that
would disrupt the stability of the 1.4.x series.  The 1.6.x releases will
continue to support newer Linux kernel releases.

Thanks to Garrett Wollman, we have a new buildslave running FreeBSD 8.2

The 2011 Workshop has been turned into an online event. Details below.

## Events

### Pittsburgh Hackathon

We'll be having a development hackathon in Pittsburgh, actual site to be
announced, April 25-27.  Goal is to follow the Edinburgh 2009 hackathon
with additional planning for revising RPCs for new data types, as well as
attempting to work through planning merging of work to the git master such
as the previous libosi work, extended callbacks, etc.

Please let me know if you plan to come so I can have an approximate
headcount for planning purposes.

\--Derrick Brashear

### Annual Best Practices Workshop

Due to the on-going economic issues affecting a broad range of
organizations that have typically sent attendees to previous workshops, it
has been determined that the 2011 AFS and Kerberos Best Practices Workshop
will be held as an online event. The 2012 AFS and Kerberos Best Practices
Workshop will be held at The University of North Carolina at Charlotte.

[http://workshop.openafs.org/afsbpw11/](http://workshop.openafs.org/afsbpw11/)

## AFS Protocol Standardization

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://lists.openafs.org/mailman/listinfo/afs3-standardization](http://lists.openafs.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://datatracker.ietf.org/doc/draft-brashear-afs3-pts-extended-names/](http://datatracker.ietf.org/doc/draft-brashear-afs3-pts-extended-names/)

Status: Tenth Draft - Consensus reached

Last Update: March 7, 2011

A working clarification has been approved, the draft will be submitted as
experimental.

\--Derrick

### AFS Callback Extensions

[http://datatracker.ietf.org/doc/draft-benjamin-extendedcallbackinfo/](http://datatracker.ietf.org/doc/draft-benjamin-extendedcallbackinfo/)

Status: Expired (First draft) - Waiting on RPC refresh

Last Update: September 23, 2009

### RXGK

[http://datatracker.ietf.org/doc/draft-wilkinson-afs3-rxgk/](http://datatracker.ietf.org/doc/draft-wilkinson-afs3-rxgk/)

Status: Expired (First draft)

Last Update: Jan 9, 2010

### Rx Security Object Providing Clear-text Peer Identity Assertions

[http://datatracker.ietf.org/doc/draft-tkeiser-rxrpc-sec-clear/](http://datatracker.ietf.org/doc/draft-tkeiser-rxrpc-sec-clear/)

Status: Expired (Third draft)

Last Update: April 17, 2010

### AFSVol Tag-Length-Value Remote Procedure Call Extensions

[http://datatracker.ietf.org/doc/draft-tkeiser-afs3-volser-tlv/](http://datatracker.ietf.org/doc/draft-tkeiser-afs3-volser-tlv/)

Status: Expired (Fourth Draft)

Last Update: August 4, 2010

Tom has issued a second call for review.

\--Ed.

### AFS Byte-Range File Locking

[http://datatracker.ietf.org/doc/draft-mbenjamin-afs-file-locking/](http://datatracker.ietf.org/doc/draft-mbenjamin-afs-file-locking/)

Status: Expired (Sixth Draft)

Last Update: May 13, 2010

This draft proposes protocol extensions to support byte-range and
mandatory locking.

The first draft was submitted on May 5, 2010.

### Adding Extended Authentication Names to the Bos Super User list

[http://datatracker.ietf.org/doc/draft-wilkinson-afs3-bos-identities/](http://datatracker.ietf.org/doc/draft-wilkinson-afs3-bos-identities/)

Status: Initial Draft

Last Update: December 7, 2010

This document describes an additional set of RX remote procedure calls
which may be used to managed extended authenticated names within the AFS-3
basic overseer service's SuperUser list

### Adding a Flexible GetSize RPC Variant to the AFS-3 Volume Service

Status: Fourth Draft

Last Update: March 30, 2011

[http://datatracker.ietf.org/doc/draft-deason-afs3-getsizev2/](http://datatracker.ietf.org/doc/draft-deason-afs3-getsizev2/)

The only real substantive change in this is section 8 (AFS-3 Registry
Considerations), where the draft now specifies allocation ranges for the
flags for AFSVolDumpV2 and AFSVolGetSizeV2. It specifies the range
0x00000001-0x00800000 to be allocated by the AFS-3 registry, and the rest
to be used for private use.

\-- Andrew Deason

This is a second call for review on draft-deason-afs3-getsizev2-03. Any
feedback would be appreciated.

\--Andrew Deason

### Base Types for Time in AFS-3

Status: Second Draft

Last Update: April 12, 2011

[http://datatracker.ietf.org/doc/draft-deason-afs3-type-time/](http://datatracker.ietf.org/doc/draft-deason-afs3-type-time/)

This document describes a 64-bit time type with 100 nanosecond resolution
for future AFS3 protocol use.

The largest change is that there are now three types defined:
AFSRelTimestamp (no resolution), AFSTime, and the new AFSTimestamp (no
resolution). There is now extensive text explaining the details and
reasoning for the "resolution" field in AFSTime. While we can still
discuss/argue about it here, I just want to bring up the possibility
that we \_could\_ to some extent defer such things for the I-Ds that
actually make use of these time types (since this document leaves the
decision of AFSTime vs AFSTimestamp completely up to the using
RPC/structure). It could even be split into a separate I-D, if that is
desired.

Other changes include the addition of sample conversion code per Jeff,
and text recommending keeping the special value of timestamp 0 per
Simon. I think that the actual meaning of timestamp 0 is up to each
RPC/structure, so in this document, the special case of 0 is just a
recommendation for future RPC/structure definitions.

There are also some language changes regarding the definition of the
"resolution" field, though the actual meaning is basically the same.

The document also now specifies that a resolution of 0 represents an
"unknown resolution" per Tom, though implementations SHOULD treat it as
a 1-second res. The document now also requires that the resolution is
always 1 second or less, to ensure that we are sane w.r.t. existing
implementations.

Any and all feedback and review is welcomed.

\--Andrew Deason

### AFS-3 Extensible XDR Discriminated Union Primitive Type

Status: Initial Draft

Last Update: March 7, 2011

[http://datatracker.ietf.org/doc/draft-keiser-afs3-xdr-union/](http://datatracker.ietf.org/doc/draft-keiser-afs3-xdr-union/)

This document adds special discriminated unions to the XDR encoding format
for use in AFS3. This came out of discussions on how to encode IPv6
addresses for AFS3 and transitioned to a more general data type.

## Projects

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

The pt\_util man page was updated to the remove the warning about the
versino and epoch being byte-swapped on little endian systems.

### S3 Front-end for AFS

Project Contacts:

- Fabrizio Manfredi <fabrizio.manfredi@gmail.com>
- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

We have the mys3 version 0.2, the new features of this version are:

- Multi user support, the users are stored in a flat file at the moment
- More attributes are supported in the s3 call
- In the packages is now available a s3cmd, a simple and powerful client
for interaction with S3 server and with a nice function of synchronization
from local disk to s3server and vice versa

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Kerberos v5 and multiple encryption types - July 2010
- Per-File ACLs - August 2010
- Rx OSD integration & Raw Vicep Access in Clients - November 2010
- Mac OS X OpenAFS Preference Pane - February 2011
- Extended Callback Information - February 2011
- Virtual Machine Images - March 2011
- User-space cache manager

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Patches merged into the master branch:
    Month   Number of Commits
    2011-04   95 (Partial month)
    2011-03  185
    2011-02   89
    2011-01  102
    2010-12  105
    2010-11  145
    2010-10  168
    2010-09  135
    2010-08  115
    2010-07  154
    2010-06  171
    2010-05  139
    2010-04  161
    2010-03  140

    Patches merged into the stable 1.6.x branch:
    Month   Number of Commits
    2011-04   30 (Partial month)
    2011-03   73
    2011-02  171
    2011-01   47
    2010-12   43
    2010-11   33
    2010-10   98
    2010-09   81
    2010-08    2

    Patches merged into the stable 1.4.x branch:
    Month   Number of Commits
    2011-03   17
    2011-02   12
    2011-01    1
    2010-12   16
    2010-11    9
    2010-10    7
    2010-09    2
    2010-08   10
    2010-06    2
    2010-05   15
    2010-04    4
    2010-03   28
    2010-02   35

### Patches merged into the master branch

    Date       Committer        Change# Description
    2011-04-16 Simon Wilkinson   (4465) libafs: Remove afs_write duplication
    2011-04-16 Derrick Brashear  (4474) libafscp fixes
    2011-04-16 Derrick Brashear  (4381) afsio: rewrite using libafscp
    2011-04-15 Andrew Deason     (4478) RX: Remove allocation counters
    2011-04-15 Andrew Deason     (4471) Suppress cmp component version error messages
    2011-04-15 Andrew Deason     (4479) AIX51: Fix PAGs
    2011-04-15 Andrew Deason     (4477) tsm41: Reformat function definitions
    2011-04-15 Andrew Deason     (4470) pam: Use PAM_CONST more often
    2011-04-15 Andrew Deason     (4469) pam: Check for null upwd from getpwnam_r
    2011-04-15 Andrew Deason     (4468) pam: Use POSIX getpwnam_r on Solaris
    2011-04-15 Andrew Deason     (4472) vfsck: Fix roken fallout
    2011-04-15 Derrick Brashear  (4473) kernel upcall rx env should shut down event daemon
    2011-04-13 Andrew Deason     (4467) Fix some configure header prereqs
    2011-04-13 Andrew Deason     (4466) RX: Include sys/file.h for rx_lwp.c
    2011-04-13 Jeffrey Altman    (4458) asetkey: permit des-cbc-md5 and des-cbc-md4 keys
    2011-04-13 Simon Wilkinson   (4464) libafs: Remove unecessary parameters to afs_read
    2011-04-13 Simon Wilkinson   (4463) libafs: Remove afs_read duplication
    2011-04-13 Simon Wilkinson   (4462) fs: Abstract out code to get the last component
    2011-04-13 Simon Wilkinson   (4455) viced: Remove logging duplication
    2011-04-12 Simon Wilkinson   (4461) libuafs: Add afsd symlink to the clean rules
    2011-04-12 Ken Dreyer        (4457) fix manpage for udebug -servers
    2011-04-11 Jeffrey Altman    (4456) roken: export tsearch, tdelete, tfind on windows
    2011-04-11 Derrick Brashear  (4424) afscp: build for windows
    2011-04-11 Andrew Deason     (4452) DAFS: Request salvage on detach for volser
    2011-04-11 Andrew Deason     (4445) DAFS: Do not give back vol to viced after salvage
    2011-04-11 Andrew Deason     (4444) volser: Avoid assert on ViceCreateRoot failure
    2011-04-11 Derrick Brashear  (4451) add tsearch to Windows
    2011-04-11 Derrick Brashear  (4454) Import of code from heimdal
    2011-04-10 Andrew Deason     (2503) XDR: decouple from system XDR implementation
    2011-04-10 Derrick Brashear  (4453) Import of code from heimdal
    2011-04-10 Simon Wilkinson   (4447) ptserver: Add cmdline options for config and log
    2011-04-10 Derrick Brashear  (4449) Import tsearch.c from roken
    2011-04-09 Simon Wilkinson   (4446) tests: Remove spurious rxgk reference
    2011-04-08 Andrew Deason     (4442) afsd: Trim trailing slashes on Linux mntent
    2011-04-08 Simon Wilkinson   (4433) Windows: Use roken gettimeofday implementation
    2011-04-08 Simon Wilkinson   (4443) Import of code from heimdal
    2011-04-08 Simon Wilkinson   (4440) vlserver: Add options for config, log and db
    2011-04-06 Andrew Deason     (4439) salvager: Error volumes on GetInodeSummary errors
    2011-04-06 Andrew Deason     (4438) salvager: Do not AskDelete on GetInodeSummary fail
    2011-04-06 Marc Dionne       (4441) ubik: don't rely on timeout value after select()
    2011-04-06 Rainer Toebbicke  (3909) Atomically collect callbacks to be broken
    2011-04-05 Andrew Deason     (4437) Correct strftime callers
    2011-04-05 Marc Dionne       (4264) ubik: take DB lock in ubik_GetVersion
    2011-04-05 Marc Dionne       (4263) ubik: DB lock usage in ubik_Flush and ubik_Write
    2011-04-05 Marc Dionne       (4262) ubik: SVOTE_Beacon should hold the DB lock for CheckTid
    2011-04-05 Marc Dionne       (4174) ubik: Document lock ordering
    2011-04-05 Marc Dionne       (4158) ubik: Introduce version lock
    2011-04-05 Marc Dionne       (4157) ubik: Introduce new address lock
    2011-04-05 Marc Dionne       (4156) ubik: Introduce new vote lock
    2011-04-05 Simon Wilkinson   (4432) Import of code from heimdal
    2011-04-05 Marc Dionne       (4155) ubik: Introduce new beacon lock
    2011-04-05 Simon Wilkinson   (4431) Roken: Import gettimeofday
    2011-04-05 Simon Wilkinson   (4430) Tidy up gettimeofday usage
    2011-04-05 Andrew Deason     (4393) afs: Retry unlock after afs_StoreAllSegments
    2011-04-05 Simon Wilkinson   (4427) Remove NINTERFACE define
    2011-04-05 Simon Wilkinson   (4426) Replace afs_ctime with strftime and friends
    2011-04-04 Simon Wilkinson   (4425) configure: Check for localtime_r properly
    2011-04-04 Simon Wilkinson   (4423) util: Remove the unused magic.h header
    2011-04-04 Simon Wilkinson   (4422) xstat: Tidy up header includes
    2011-04-04 Simon Wilkinson   (4421) vol: Tidy up header includes
    2011-04-04 Simon Wilkinson   (4420) vol: Don't use MAX_INT when UINT_MAX will do
    2011-04-04 Simon Wilkinson   (4418) viced: Tidy header includes
    2011-04-04 Simon Wilkinson   (4419) Irix: Supress some more warnings in kernel builds
    2011-04-04 Simon Wilkinson   (4417) vfsck: Tidy header includes
    2011-04-04 Simon Wilkinson   (4416) tsalvaged: Tidy up build rules
    2011-04-04 Simon Wilkinson   (4415) venus: Tidy up header includes
    2011-04-03 Simon Wilkinson   (4414) uss: Tidy up header includes
    2011-04-03 Simon Wilkinson   (4413) usd: Tidy header includes
    2011-04-03 Simon Wilkinson   (4412) update: Tidy up header includes
    2011-04-03 Simon Wilkinson   (4411) ubik: Tidy up header includes
    2011-04-03 Simon Wilkinson   (4410) pthreaded servers: Tidy up header includes
    2011-04-03 Simon Wilkinson   (4409) sys: Tidy up header includes
    2011-04-03 Simon Wilkinson   (4408) scout: Tidy header includes
    2011-04-03 Simon Wilkinson   (4407) rxkad: Tidy header includes
    2011-04-03 Simon Wilkinson   (4405) rxgen: Tidy up header includes
    2011-04-03 Simon Wilkinson   (4404) rxdebug: Tidy header includes
    2011-04-03 Simon Wilkinson   (4403) rx: Tidy header includes
    2011-04-03 Simon Wilkinson   (4402) procmgmt: Tidy header includes
    2011-04-03 Simon Wilkinson   (4401) pam: Tidy header includes
    2011-04-03 Simon Wilkinson   (4406) roken: Add env functions to configure checks
    2011-04-02 Marc Dionne       (4400) Update README.WARNINGS, adjust warning inhibition flags
    2011-04-02 Marc Dionne       (4399) Convert ubik_Call(x) calls to ubik_x()
    2011-04-02 Marc Dionne       (4398) fsprobe: Fix usage message
    2011-04-02 Marc Dionne       (4397) fsprobe: call RXAFS_GetTime directly
    2011-04-02 Simon Wilkinson   (4389) Linux: Fix USE_UCONTEXT detection
    2011-04-02 Simon Wilkinson   (4386) libwp: Tidy header includes
    2011-04-02 Andrew Deason     (4395) afs: Avoid memory leak on recursive write flock
    2011-04-02 Marc Dionne       (4396) crypto: return a value from krb5_abortx
    2011-04-01 Derrick Brashear  (4387) macos: no more startupitems
    2011-04-01 Derrick Brashear  (4380) libafscp: code cleanup
    2011-04-01 Simon Wilkinson   (4385) log: Tidy header includes
    2011-04-01 Marc Dionne       (4382) Linux: Fix fallout from path_lookup commit
    2011-04-01 Simon Wilkinson   (4384) libadmin: Tidy header includes
    2011-04-01 Simon Wilkinson   (4332) libacl: Tidy header includes
    2011-04-01 Simon Wilkinson   (4331) kopenafs: Tidy up headers
    2011-03-30 Marc Dionne       (4360) Linux: 2.6.39: replace path_lookup with kern_path
    2011-03-30 Derrick Brashear  (4379) xdr symbol fallout
    2011-03-30 Benjamin Kaduk    (4378) Unbreak make dest for FBSD
    2011-03-30 Antoine Verheijen (4373) OpenBSD: Complete implementation of afs_osi_TimedSleep
    2011-03-30 Andrew Deason     (4377) vol: Add timeouts to SYNC server select() calls
    2011-03-30 Andrew Deason     (4376) Always set LIB_roken when we find libroken
    2011-03-29 Russ Allbery      (4374) NEWS updates for 1.6.0pre4
    2011-03-29 Chas Williams - CONTRACTOR (4252) rx: always use/protect the xdr routines in the kernel
    2011-03-29 Simon Wilkinson   (4330) kauth: Tidy header includes
    2011-03-29 Simon Wilkinson   (4329) gtx: Tidy header includes
    2011-03-29 Simon Wilkinson   (4328) fsprobe: Tidy header includes
    2011-03-29 Simon Wilkinson   (4327) finale: Tidy header includes
    2011-03-29 Simon Wilkinson   (4326) dir: Tidy header includes
    2011-03-29 Jeffrey Altman    (4365) vol: remove flock emulation now provided by roken
    2011-03-29 Simon Wilkinson   (4325) com_err: Tidy header includes
    2011-03-29 Simon Wilkinson   (4368) AIX: Add flock to roken
    2011-03-28 Simon Wilkinson   (4324) cmd: Tidy header includes
    2011-03-28 Simon Wilkinson   (4323) bu*: Tidy header includes
    2011-03-28 Simon Wilkinson   (4367) Import of code from heimdal
    2011-03-28 Simon Wilkinson   (4366) Import flock.c from roken
    2011-03-28 Simon Wilkinson   (4322) bozo: Tidy header includes
    2011-03-28 Derrick Brashear  (4271) ihandle release locking simplification
    2011-03-28 Simon Wilkinson   (4321) auth: Tidy header includes
    2011-03-28 Simon Wilkinson   (4364) autoconf: Add tests for resolver headers
    2011-03-28 Simon Wilkinson   (4363) fssync: Rename state
    2011-03-28 Simon Wilkinson   (4320) audit: Tidy header includes
    2011-03-28 Simon Wilkinson   (4319) vol: Tidy header includes
    2011-03-28 Simon Wilkinson   (4318) volser: Tidy header includes
    2011-03-28 Simon Wilkinson   (4317) volser: More renaming of putshort and putint32
    2011-03-27 Simon Wilkinson   (4316) afs_snprintf is dead, long live rk_snprintf
    2011-03-27 Simon Wilkinson   (4362) Windows: Don't use %I for IP addresses
    2011-03-27 Benjamin Kaduk    (4350) Remove outdated rc file for afsd on FBSD
    2011-03-27 Marc Dionne       (4361) Linux: 2.6.39: deal with BKL removal
    2011-03-27 Benjamin Kaduk    (4351) new files for FreeBSD packaging at 1.6.0pre3
    2011-03-27 Simon Wilkinson   (4305) vlserver: Rationalise usage message
    2011-03-27 Simon Wilkinson   (4304) ptserver: Rationalise usage message
    2011-03-27 Simon Wilkinson   (4341) HP/UX: Make more use of roken
    2011-03-27 Simon Wilkinson   (4340) crypto: Fixes for recent Heimdal changes
    2011-03-27 Simon Wilkinson   (4339) Import of code from heimdal
    2011-03-27 Simon Wilkinson   (4338) Add getdtablesize to the roken import
    2011-03-27 Simon Wilkinson   (4303) aklog: Tidy header includes
    2011-03-27 Simon Wilkinson   (4302) NO_DES_H_INCLUDE is no longer necessary
    2011-03-27 Simon Wilkinson   (4299) ptserver: Tidy header includes
    2011-03-27 Benjamin Kaduk    (4349) Remove stale FreeBSD packaging
    2011-03-27 Jeffrey Altman    (4348) Windows: export roken symbols
    2011-03-26 Jeffrey Altman    (4347) Windows: change log for 1.5.9904 (1.6.0pre4)
    2011-03-26 Andrew Deason     (4344) viced: REALLYCLOSE origfdP after CoW
    2011-03-26 Andrew Deason     (4343) Revert "ihandle: Ensure FDH_REALLYCLOSE really closes"
    2011-03-25 Jeffrey Altman    (4179) vol: avoid MAXINT redefinition warning in vnode.c
    2011-03-25 Andrew Deason     (4189) SOLARIS: Perform daemon syscalls as kernel threads
    2011-03-25 Andrew Deason     (4188) libafs: Consolidate afs_DaemonOp code
    2011-03-25 Andrew Deason     (4345) SOLARIS: Correct ioctl syscall error handling
    2011-03-25 Andrew Deason     (4187) libafs: Indent afs_call.c ifdef maze
    2011-03-25 Andrew Deason     (4342) ihandle: One more indentation fix
    2011-03-25 Andrew Deason     (4274) ihandle: Ensure FDH_REALLYCLOSE really closes
    2011-03-25 Jeffrey Altman    (4333) Windows: trailing dot not part of volume name
    2011-03-25 Andrew Deason     (4315) salvager: Stop asking for DAFSness on SYNC_FAILED
    2011-03-25 Andrew Deason     (4298) DAFS: Allow the volumeSalvager to checkout volumes
    2011-03-25 Derrick Brashear  (4312) add AFS_DEMAND_ATTACH_UTIL
    2011-03-25 Russ Allbery      (4311) Correctly document the AFS client setuid defaults
    2011-03-25 Simon Wilkinson   (4301) util: Tidy header includes
    2011-03-25 Simon Wilkinson   (4300) vlserver: Tidy header includes
    2011-03-25 Andrew Deason     (4308) DAFS: Correct FSYNC_VOL_QUERY_VOP checks
    2011-03-24 Jeffrey Altman    (4240) Windows: avoid recursive cm_CheckOfflineVolume
    2011-03-24 Andrew Deason     (4297) salvager: Give back volumes when exiting early
    2011-03-24 Andrew Deason     (4296) DAFS: Do not record vol ops for DELETED vols
    2011-03-24 Andrew Deason     (4295) salvager: Do not AskOnline nonexistent volumes
    2011-03-24 Andrew Deason     (4294) namei: Log ListViceInodes write failures
    2011-03-24 Andrew Deason     (4293) salvager: Fix conversion from stdio calls
    2011-03-24 Derrick Brashear  (4290) macos next support
    2011-03-24 Derrick Brashear  (4288) osconf: reduplicate systype stuff
    2011-03-24 Andrew Deason     (4287) DAFS: Do not VDeregisterVolOp_r while exclusive
    2011-03-23 Simon Wilkinson   (4285) rpm: Build srpms without %dist in their name
    2011-03-22 Andrew Deason     (4273) Fix ihandle.c indents
    2011-03-22 Andrew Deason     (4272) vclosevnodefiles-ihandle-leak-20090216
    2011-03-22 Derrick Brashear  (3487) DAFS: fix forceDAFS support in salvager
    2011-03-22 Russ Allbery      (4270) Update NEWS for 1.6.0pre3 release
    2011-03-22 Derrick Brashear  (3486) DAFS: allow salvager to detect whether FSYNC server is DAFS
    2011-03-21 Andrew Deason     (4233) viced: Check vnode length on dir ops
    2011-03-21 Andrew Deason     (4199) vol: Correct VolumeNumber for large volume IDs
    2011-03-21 Andrew Deason     (4198) vol: Handle large volume IDs in VLockFile
    2011-03-21 Andrew Deason     (4197) vol: Make VLockFile arguments consistent
    2011-03-21 Andrew Deason     (4259) libafs: Do not osi_FlushPages for dirs
    2011-03-21 Andrew Deason     (4242) DAFS: DFlushVolume outside of vol glock
    2011-03-21 Simon Wilkinson   (4267) util: Fix exec_alt
    2011-03-21 Derrick Brashear  (4266) lwp: override dbg and optmz settings
    2011-03-21 Derrick Brashear  (4265) osx: restore atomic stats to knet
    2011-03-20 Andrew Deason     (4244) salvager: Fix volume parsing on 64-bit
    2011-03-18 Derrick Brashear  (3691) MacOS: allow cdead vcaches to be found in FindVCache if requested
    2011-03-18 Simon Wilkinson   (4253) util: Remove unnecessary uuid_mem* macros
    2011-03-18 Simon Wilkinson   (4251) dir: Make test utility build again
    2011-03-18 Simon Wilkinson   (4249) util: Remove remote.h
    2011-03-17 Simon Wilkinson   (4258) rpms: Make makesrpm.pl cater for new rpm names
    2011-03-17 Derrick Brashear  (4239) macos: kernel socket upcall
    2011-03-17 Simon Wilkinson   (4257) rpms: Use new CellServDB
    2011-03-17 Simon Wilkinson   (4248) util: Remove packages.h
    2011-03-17 Simon Wilkinson   (4247) util: Remove itc.h
    2011-03-17 Andrew Deason     (4256) viced: Actually print client CPS
    2011-03-17 Simon Wilkinson   (4246) util: Remove isathing
    2011-03-17 Derrick Brashear  (4255) osx: decode-panic should work in add-kext only land
    2011-03-17 Simon Wilkinson   (4245) kauth: Use strtol for integer argument handling
    2011-03-17 Derrick Brashear  (4254) osx: prefs pane should properly detect version
    2011-03-15 Simon Wilkinson   (4234) Throw the compiler a bone ...
    2011-03-15 Derrick Brashear  (4229) macos: dont want bind 8 compat on leopard
    2011-03-15 Jeffrey Altman    (4227) Windows: 1.6pre3 changes
    2011-03-15 Simon Wilkinson   (4223) Linux: Fix return codes from setpag
    2011-03-15 Simon Wilkinson   (4222) Revert "Linux: normalize error return for emulated syscalls"
    2011-03-14 Simon Wilkinson   (4215) auth: Use the UserListFileName function more
    2011-03-14 Simon Wilkinson   (4216) roken: Export rk_asprintf on Windows
    2011-03-14 Simon Wilkinson   (4214) auth: Refactor CellServDB path creation
    2011-03-14 Michael Meffie    (4218) readme typos
    2011-03-13 Simon Wilkinson   (4213) tests: Fix KeyFile test so it works from harness
    2011-03-13 Simon Wilkinson   (4203) auth: Rework afsconf_UpToDate to use CellServDB
    2011-03-13 Simon Wilkinson   (4212) tests: Fix the authcon test to avoid pthread errors
    2011-03-13 Simon Wilkinson   (4211) pt_util: Initialise empty database correctly
    2011-03-13 Simon Wilkinson   (4210) DOC: pt_util now outputs ntohl'd epoch and version
    2011-03-13 Simon Wilkinson   (4204) crypto: Add krb5_crypto_fx_cf2 to our prototypes
    2011-03-13 Simon Wilkinson   (4202) ubik: Allow servers to have more than 3 seclayers
    2011-03-13 Simon Wilkinson   (4201) afsconf: Rework security flags
    2011-03-13 Simon Wilkinson   (4200) ubik: Remove dependency on auth
    2011-03-11 Chas Williams - CONTRACTOR (4206) solaris: fix typo in the solaris 11 startup script
    2011-03-11 Andrew Deason     (4196) salvager: Do not abort on large volume IDs
    2011-03-10 Simon Wilkinson   (4173) Don't use KERN_OPTMZ or KERN_DBG on Linux 2.6
    2011-03-10 Simon Wilkinson   (4192) hcrypto: don't redefine key_type
    2011-03-10 Simon Wilkinson   (4190) Remove redundant entries from MT_CFLAGS
    2011-03-10 Simon Wilkinson   (4172) Remove -D_LARGEFILE64_SOURCE on Linux
    2011-03-10 Simon Wilkinson   (4191) Revert "hcrypto: avoid key_type redefinition"
    2011-03-10 Derrick Brashear  (4178) hcrypto: avoid key_type redefinition
    2011-03-09 Derrick Brashear  (3971) linux: defer vcache evictions when sleep would be needed
    2011-03-09 Jeffrey Altman    (4183) Windows: handle rx busy call channel
    2011-03-08 Andrew Deason     (4159) RX: Avoid timing out non-kernel busy channels
    2011-03-08 Simon Wilkinson   (4171) Clarify the role of XCFLAGS and simplify MT_CFLAGS
    2011-03-08 Jeffrey Altman    (4149) vol: FILE* to FD_t except logging and special ops
    2011-03-08 Andrew Deason     (3960) aklog: Do not include XCFLAGS twice
    2011-03-08 Jeffrey Altman    (4147) vol: consolide afs_xxxx macros in ihandle.h
    2011-03-08 Marc Dionne       (4177) libadmin: minor warning fix
    2011-03-07 Jeffrey Altman    (4148) vol: remove warning on use of DFlushVolume
    2011-03-07 Simon Wilkinson   (4153) Disable vectored positional IO if no 64bit support
    2011-03-07 Simon Wilkinson   (4154) crypto: Avoid variadic macros
    2011-03-06 Marc Dionne       (4151) ubik: cleanup DB lock usage in SDISK_SendFile
    2011-03-06 Marc Dionne       (4146) ubik: refactor pthread creation code
    2011-03-06 Marc Dionne       (4145) ubik: remove unused code
    2011-03-06 Simon Wilkinson   (4152) Fix positional I/O support for largefiles
    2011-03-06 Marc Dionne       (4144) ubik: Rearrange some initialization code
    2011-03-06 Marc Dionne       (4143) ubik: make uphys_close static
    2011-03-06 Marc Dionne       (4142) ubik: remove successive Quorum_EndIO, Quorum_StartIO calls
    2011-03-06 Jeffrey Altman    (4137) volser: warning removal
    2011-03-06 Marc Dionne       (4141) ubik: add lock initialization function
    2011-03-06 Marc Dionne       (4140) ubik: rename DInit, call from initialization sequence
    2011-03-06 Jeffrey Altman    (4150) ubik: build all files for pthread version
    2011-03-05 Jeffrey Altman    (4138) volser: restore diskPartition[64] lock_fd comment
    2011-03-05 Jeffrey Altman    (4136) volser: cleanup volser_internal.h
    2011-03-05 Marc Dionne       (4139) ubik: remove unused UBIK_PAUSE code
    2011-03-05 Jeffrey Altman    (4135) volser: make private lockproc routines private
    2011-03-05 Simon Wilkinson   (4129) Unix CM: Remove redefinition of "inline"
    2011-03-05 Jeffrey Altman    (4131) Revert "Convert from using nvldbentry to uvldbentry"
    2011-03-05 Jeffrey Altman    (4130) Revert "modify FindIndex to compare uuids"
    2011-03-04 Andrew Deason     (4126) viced: Set HWHO_INPROGRESS in CheckHost_r
    2011-03-04 Jeffrey Altman    (4124) Windows: mp target trailing dot not part vol name
    2011-03-04 Jeffrey Altman    (4111) Windows: avoid use of cm_buf for MPs and Symlinks
    2011-03-04 Andrew Deason     (4060) vol: Check for blank vnode in VAllocVnode_r
    2011-03-04 Andrew Deason     (4059) DAFS: VnLock after VnWaitQuiescent in VAllocVnode
    2011-03-04 Andrew Deason     (4058) DAFS: Wait for exclusive ops in VFreeBitMapEntry_r
    2011-03-04 Andrew Deason     (4120) DAFS: Clear salvage stats on VOL_DONE
    2011-03-04 Andrew Deason     (4119) DAFS: Allow LEAVE_OFF for DELETED volumes
    2011-03-04 Andrew Deason     (4118) vol-salvage: VOL_DONE deleted volumes
    2011-03-04 Michael Meffie    (4122) rpm: fix ChangeLog filename in doc rpm
    2011-03-04 Andrew Deason     (4121) viced: Check vnode length on read and write
    2011-03-04 Andrew Deason     (4117) vol-salvage: calloc volume summary structs
    2011-03-03 Andrew Deason     (4116) vol-salvage: Fix AskOnline error message
    2011-03-03 Andrew Deason     (4115) Give a default reason in *sync-debug
    2011-03-03 Simon Wilkinson   (4104) tests: Remove errant rxgk build rule
    2011-03-03 Simon Wilkinson   (4103) auth: Add GetAllKeys function
    2011-03-03 Simon Wilkinson   (4114) Tidy up assorted clean targets
    2011-03-03 Simon Wilkinson   (4101) kernel crypto: Tidy up includes
    2011-03-03 Derrick Brashear  (4107) tweak uvldb-making function
    2011-03-03 Derrick Brashear  (4108) rx: cancel growmtu event on resetcall
    2011-03-02 Simon Wilkinson   (4100) ptuser/hpr: Don't check for a KeyFile
    2011-03-02 Simon Wilkinson   (4099) ptserver: Always set up Ubik security
    2011-03-02 Simon Wilkinson   (4098) auth: Add Ktoken.xdr.c to the clean rule
    2011-03-02 Chaz Chandler     (2371) libafscp: a library for "clientless" operations
    2011-03-02 Simon Wilkinson   (4097) volser: Rename putshort and putint32
    2011-03-02 Simon Wilkinson   (4096) roken: Fix out-of-tree libroken builds
    2011-03-01 Simon Wilkinson   (4094) Fix grammar in configure check description
    2011-03-01 Andrew Deason     (4095) Revert "LWP: remove ucontext header from preempt module"

### Patches merged into the stable 1.6.x branch

    Date       Committer        Change# Description
    2011-04-13 Andrew Deason     (4460) libafs: Do not specify an Rx busy channel error
    2011-04-01 Antoine Verheijen (4388) OpenBSD: Complete implementation of afs_osi_TimedSleep
    2011-03-29 Derrick Brashear  (4371) Linux: 2.6.39: replace path_lookup with kern_path
    2011-03-29 Derrick Brashear  (4370) Linux: 2.6.39: deal with BKL removal
    2011-03-28 Derrick Brashear  (4372) Windows: change log for 1.5.9904 (1.6.0pre4)
    2011-03-28 Andrew Deason     (4369) SOLARIS: Correct ioctl syscall error handling
    2011-03-28 Derrick Brashear  (4352) viced: REALLYCLOSE origfdP after CoW
    2011-03-27 Derrick Brashear  (4355) new files for FreeBSD packaging at 1.6.0pre3
    2011-03-27 Derrick Brashear  (4354) Remove outdated rc file for afsd on FBSD
    2011-03-27 Derrick Brashear  (4353) Remove stale FreeBSD packaging
    2011-03-25 Derrick Brashear  (4337) salvager: Stop asking for DAFSness on SYNC_FAILED
    2011-03-25 Derrick Brashear  (4336) DAFS: Allow the volumeSalvager to checkout volumes
    2011-03-25 Derrick Brashear  (4335) add AFS_DEMAND_ATTACH_UTIL
    2011-03-25 Jeffrey Altman    (4334) Windows: trailing dot not part of volume name
    2011-03-25 Derrick Brashear  (4314) Windows: avoid recursive cm_CheckOfflineVolume
    2011-03-25 Derrick Brashear  (4313) Correctly document the AFS client setuid defaults
    2011-03-25 Russ Allbery      (4310) Update NEWS for 1.6.0pre3 release
    2011-03-25 Russ Allbery      (4309) Update 1.6 NEWS entry based on 1.6.0pre2 release notes
    2011-03-24 Derrick Brashear  (4307) rpm: Build srpms without %dist in their name
    2011-03-24 Derrick Brashear  (4306) DAFS: Do not VDeregisterVolOp_r while exclusive
    2011-03-24 Derrick Brashear  (4291) macos next support
    2011-03-24 Derrick Brashear  (4292) osconf: reduplicate systype stuff
    2011-03-24 Derrick Brashear  (4284) vol: Correct VolumeNumber for large volume IDs
    2011-03-24 Derrick Brashear  (4283) salvager: Fix volume parsing on 64-bit
    2011-03-24 Derrick Brashear  (4282) viced: Actually print client CPS
    2011-03-24 Derrick Brashear  (4278) DAFS: fix forceDAFS support in salvager
    2011-03-24 Derrick Brashear  (4277) DAFS: allow salvager to detect whether FSYNC server is DAFS
    2011-03-24 Derrick Brashear  (4276) openafs 1.6.0pre4
    2011-03-23 Derrick Brashear  (4281) rpms: Use new CellServDB
    2011-03-23 Derrick Brashear  (4280) rpms: Make makesrpm.pl cater for new rpm names
    2011-03-23 Derrick Brashear  (4279) util: Fix exec_alt
    2011-03-23 Derrick Brashear  (4275) vclosevnodefiles-ihandle-leak-20090216
    2011-03-21 Derrick Brashear  (4243) MacOS: allow cdead vcaches to be found in FindVCache if requested
    2011-03-21 Derrick Brashear  (4238) macos: kernel socket upcall
    2011-03-21 Derrick Brashear  (4269) osx: prefs pane should properly detect version
    2011-03-21 Derrick Brashear  (4268) osx: decode-panic should work in add-kext only land
    2011-03-19 Andrew Deason     (4261) viced: Allow checkout of VOL_STATE_DELETED volumes
    2011-03-16 Anders Kaseorg    (4235) Throw the compiler a bone ...
    2011-03-15 Jeffrey Altman    (4231) Windows: permit code signing without timestamps
    2011-03-15 Jeffrey Altman    (4230) Windows: Add CODESIGN_OTHER option to make signtool rules
    2011-03-15 Jeffrey Altman    (4228) Windows: 1.6pre3 changes
    2011-03-15 Derrick Brashear  (4226) Linux: Fix return codes from setpag
    2011-03-15 Derrick Brashear  (4225) Revert "Linux: normalize error return for emulated syscalls"
    2011-03-15 Derrick Brashear  (4221) Windows: mp target trailing dot not part vol name
    2011-03-15 Derrick Brashear  (4220) Windows: avoid use of cm_buf for MPs and Symlinks
    2011-03-14 Michael Meffie    (4219) readme typos
    2011-03-14 Derrick Brashear  (4217) pt_util: Initialise empty database correctly
    2011-03-12 Jeffrey Altman    (4207) Windows: conditionally set tray icon state
    2011-03-11 Derrick Brashear  (4208) solaris: fix typo in the solaris 11 startup script
    2011-03-11 Derrick Brashear  (4205) make openafs 1.6.0pre3
    2011-03-10 Andrew Deason     (4194) SOLARIS: Free vcache mappings on shutdown
    2011-03-10 Derrick Brashear  (4186) linux: defer vcache evictions when sleep would be needed
    2011-03-10 Derrick Brashear  (4185) Windows: handle rx busy call channel
    2011-03-09 Michael Meffie    (4184) rpm: fix ChangeLog filename in doc rpm
    2011-03-09 Andrew Deason     (4182) RX: Avoid timing out non-kernel busy channels
    2011-03-08 Andrew Deason     (4170) vol: Check for blank vnode in VAllocVnode_r
    2011-03-08 Andrew Deason     (4169) DAFS: VnLock after VnWaitQuiescent in VAllocVnode
    2011-03-08 Andrew Deason     (4168) DAFS: Wait for exclusive ops in VFreeBitMapEntry_r
    2011-03-08 Andrew Deason     (4175) salvager: Do not break cbks when salvaging parts
    2011-03-08 Andrew Deason     (4167) vol-salvage: VOL_DONE deleted volumes
    2011-03-08 Andrew Deason     (4166) DAFS: Clear salvage stats on VOL_DONE
    2011-03-08 Andrew Deason     (4165) DAFS: Allow LEAVE_OFF for DELETED volumes
    2011-03-08 Andrew Deason     (4164) vol-salvage: calloc volume summary structs
    2011-03-08 Andrew Deason     (4176) Windows: vol-salvage SalvInfo fixes
    2011-03-08 Andrew Deason     (4163) vol-salvage: Move global vars into SalvInfo struct
    2011-03-08 Andrew Deason     (4162) Revert "LWP: remove ucontext header from preempt module"
    2011-03-08 Derrick Brashear  (4161) Fix positional I/O support for largefiles
    2011-03-08 Derrick Brashear  (4160) Disable vectored positional IO if no 64bit support
    2011-03-05 Derrick Brashear  (4134) Don't trust # of entries from ListAttributes
    2011-03-05 Derrick Brashear  (4133) Revert "Convert from using nvldbentry to uvldbentry"
    2011-03-05 Derrick Brashear  (4132) Revert "modify FindIndex to compare uuids"
    2011-03-05 Andrew Deason     (4127) viced: Set HWHO_INPROGRESS in CheckHost_r
    2011-03-03 Derrick Brashear  (4113) tweak uvldb-making function
    2011-03-03 Derrick Brashear  (4112) rx: cancel growmtu event on resetcall
    2011-03-02 Andrew Deason     (4110) fssync-debug: exec DAFS version if DAFS detected

### Patches merged into the stable 1.4.x branch

    Date       Committer        Change# Description
    2011-03-28 Antoine Verheijen (4359) OpenBSD: Eliminate complaint about built-in malloc.
    2011-03-28 Antoine Verheijen (4358) OpenBSD: Remove user.h from dir.c for OpenBSD 4.8
    2011-03-28 Antoine Verheijen (4357) OpenBSD: curproc has moved in OpenBSD 4.8
    2011-03-28 Antoine Verheijen (4356) OpenBSD: Add support for OpenBSD 4.8
    2011-03-26 Antoine Verheijen (4346) OpenBSD: Add amd64 config header for OpenBSD 4.7
    2011-03-16 Andrew Deason     (4209) salvager: Do not abort on large volume IDs
    2011-03-16 Andrew Deason     (4181) viced: Enforce lwps limit for -L
    2011-03-16 Andrew Deason     (4180) rx: Reset fd_set in LWP rxi_Sendmsg
    2011-03-16 Andrew Deason     (4128) viced: Set HWHO_INPROGRESS in CheckHost_r
    2011-03-16 Andrew Deason     (4105) Solaris: do not call VFS_RELE with GLOCK
    2011-03-16 Anders Kaseorg    (4066) Linux: Reduce key_alloc flags confusion
    2011-03-16 Anders Kaseorg    (4055) Linux: install_session_keyring: key_alloc flags are unsigned long
    2011-03-16 Anders Kaseorg    (4054) Don't count root session keyrings against quota
    2011-03-16 Andrew Deason     (3619) Use afs_foff_t for file offsets
    2011-03-16 Andrew Deason     (2161) libafs: consistently hold vnode refs
    2011-03-16 Simon Wilkinson   (4241) Remove original rxgk implementation
    2011-03-16 Anders Kaseorg    (4236) Throw the compiler a bone ...
