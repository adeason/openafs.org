---
title: OpenAFS Newsletter, Volume 3, Issue 2, February 2011
---

# OpenAFS Newsletter, Volume 3, Issue 2, February 2011

Welcome to the February issue of the OpenAFS newsletter. This newsletter
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

OpenAFS 1.6.0pre2 will be released over the next few days. The 1.6
prereleases need more testing by the community. Testing is key in getting
a stable 1.6.0 release. Please report any bugs to the bug tracker and
report your success to the openafs-devel@openafs.org mailing list.

OpenAFS is looking for mentors and project ideas for the 2011 Google
Summer of Code. Anyone wishing to be a mentor or submit a project idea
should send an email to openafs-gatekeepers@openafs.org. The deadline for
application is March 11, 2011.

A discussion about how to upgrade the afs protocols to support IPv6
addresses has started on the afs3-standardization mailing list
[http://lists.openafs.org/mailman/listinfo/afs3-standardization](http://lists.openafs.org/mailman/listinfo/afs3-standardization)

## Events

### Annual Best Practices Workshop

The organizers of the AFS & Kerberos Best Practices Workshop 2011
announces the Call For Participation.  The CFP closes on March 1, 2011.
Acceptances will be made on a continuing schedule based on fit with
other talks.

This year's Workshop will be held at the University of North Carolina at
Charlotte, June 6-10, 2011.

[http://workshop.openafs.org/afsbpw11/cfp.html](http://workshop.openafs.org/afsbpw11/cfp.html)

## AFS Protocol Standardization

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://lists.openafs.org/mailman/listinfo/afs3-standardization](http://lists.openafs.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names)

Status: Eighth Draft (07) - Consensus reached

A working clarification has been approved, the draft will be submitted as
experimental.

\--Derrick

### AFS Callback Extensions

[http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo](http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo)

Status: Active - Waiting on RPC refresh

Last Update: September 23, 2009

There is a need to publish a revised draft.  I should be able do so in the
next couple of weeks.

\--Matt Benjamin

### RXGK

[http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk](http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk)

Status: Initial Draft

Last Draft Update: Jan 9, 2010

A working implementation of rxgk was demonstrated at the European AFS &
Kerberos Workshop in Pilsen. Whilst there is still work to be done, both
on completing the implementation, and on getting the code into the OpenAFS
tree, this is an important milestone. Slides from the Pilsen talk are
available on their web site. The current rxgk code is, as always,
available on github at [https://github.com/your-file-system/openafs-rxgk](https://github.com/your-file-system/openafs-rxgk)

This work is being funded by Your File System, Inc.

\--Simon Wilkinson

### Rx Security Object Providing Clear-text Peer Identity Assertions

[http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear](http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear)

Status: Third draft

Last Update: April 17, 2010

### AFSVol Tag-Length-Value Remote Procedure Call Extensions

[http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv](http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv)

Status: Fourth Draft

Last Update: August 4, 2010

Draft -03 is currently awaiting feedback to
afs3-standardization@openafs.org. Any feedback would be appreciated.

\--Tom

Tom has issued a second call for review.

\--Ed.

### AFS Byte-Range File Locking

[http://tools.ietf.org/html/draft-mbenjamin-afs-file-locking](http://tools.ietf.org/html/draft-mbenjamin-afs-file-locking)

Status: Fifth Draft

This draft proposes protocol extensions to support byte-range and
mandatory locking.

The first draft was submitted on May 5, 2010.

### Adding Extended Authentication Names to the Bos Super User list

[http://tools.ietf.org/html/draft-wilkinson-afs3-bos-identities](http://tools.ietf.org/html/draft-wilkinson-afs3-bos-identities)

Status: Initial Draft

Last Update: December 7, 2010

This document describes an additional set of RX remote procedure calls
which may be used to managed extended authenticated names within the AFS-3
basic overseer service's SuperUser list

## Projects

### Extended Callback Information

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

An updated XCB implementation (features added to better support byte-range
locking, e.g., unicast XCB message types and corrected callback
per-message results) is available in provisional form from the
openafs-rxgk repository at
[https://github.com/your-file-system/openafs-rxgk](https://github.com/your-file-system/openafs-rxgk).  A version with
important bugfixes should be available in the next 1-2 weeks.

This work is being performed under a contract from Your File System Inc.

Sine Nomine Associates provided funding for Extended Callback Information
(2008).  Also bugfixes, and assistance with verification.

\--Matt

### User-space cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

A few libuafs fixes and improvements (including Perl bindings) have been
submitted in gerrit 3896 and its dependent changes. There are still
various maintainability issues being worked out, but the code is
available there and is functional.

The Userspace CM project is funded by Sine Nomine Associates.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Some minor spelling and grammatical errors were fixed in the vos\_clone man
page.  The merge-pod script was modified to work with older versions of
Perl.

### Mac OS X OpenAFS Preference Pane

Project Contact:

- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

1.6.0pre2 will include a fix to disallow "get tokens at login" when login
via AD is configured, as this is not supported and can make a machine
impossible to log into.

\--Derrick Brashear

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- S3 Front-end for AFS - July 2010
- Kerberos v5 and multiple encryption types - July 2010
- Per-File ACLs - August 2010
- Virtual Machine Images - November 2010
- Rx OSD integration & Raw Vicep Access in Clients - November 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Patches merged into the master branch:
    Month   Number of Commits
    2011-02   22 (Partial month)
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
    2010-02  155
    2010-01  103

    Patches merged into the stable 1.6.x branch:
    Month   Number of Commits
    2011-02  117 (Partial month)
    2011-01   47
    2010-12   43
    2010-11   33
    2010-10   98
    2010-09   81
    2010-08    2

    Patches merged into the stable 1.4.x branch:
    Month   Number of Commits
    2011-01   1
    2010-12  16
    2010-11   9
    2010-10   7
    2010-09   2
    2010-08  10
    2010-06   2
    2010-05  15
    2010-04   4
    2010-03  28
    2010-02  35
    2010-01  11

### Patches merged into the master branch

    Date       Committer        Change# Description
    2011-02-13 Jeffrey Altman    (3936) Windows: Release Notes updates for 1.6pre2
    2011-02-12 Marc Dionne       (3883) Linux: 2.6.38: dentry->d_count is not an atomic
    2011-02-12 Jeffrey Altman    (3926) Windows: ChangeLog updates for 1.6.pre1
    2011-02-12 Jeffrey Altman    (3925) Windows: Fix GetIoctlHandle path construction
    2011-02-12 Jeffrey Altman    (3924) Windows: Fix symlink and mount point make \\afs\xxx handling
    2011-02-11 Simon Wilkinson   (3921) util: Actually install thread_pool_types.h
    2011-02-10 Marc Dionne       (3910) scout: restore parallel make
    2011-02-09 Marc Dionne       (3764) ubik: always prefer a dirty cache page for write transactions
    2011-02-09 Rainer Toebbicke  (3765) Early dispose of replies in rx_Multi
    2011-02-09 Derrick Brashear  (3777) evalmountdata null pointer before use
    2011-02-09 Marc Dionne       (3771) Linux: 2.6.38: deal with dcache_lock removal
    2011-02-09 Marc Dionne       (3770) Linux: 2.6.38: Adjust for permission inode operation changes
    2011-02-09 Marc Dionne       (3769) Linux: allow compile flags to be passed to AC_CHECK_LINUX_BUILD
    2011-02-09 Andrew Deason     (3891) ConvertROtoRW: Use old copyDate for creationDate
    2011-02-08 Jeffrey Altman    (3904) Windows: correct pthread_xxx_init semantics
    2011-02-08 Andrew Deason     (3762) afscp: Fix -s option for writes
    2011-02-03 Jeffrey Altman    (3882) Windows: remove duplicate advapi32.lib references
    2011-02-03 Ken Dreyer        (3890) spelling/grammar fixes for manpages
    2011-02-02 Ken Dreyer        (3879) spelling/grammar fixes for vos_clone manpage
    2011-02-02 Andrew Deason     (3876) Rx: Do not stop keepalives on ACKALL receipt
    2011-02-01 Andrew Deason     (3822) afsd: Do not check for /afs if -nomount
    2011-02-01 Jeffrey Altman    (3821) Windows: No NCBRESET when probing Loopback after start
    2011-01-31 Derrick Brashear  (3874) evalmountdata: put back colon in .:mount syntax only if we removed it
    2011-01-31 Simon Wilkinson   (3776) tests: Fix auth/superuser-t.c to work on Linux
    2011-01-31 Simon Wilkinson   (3775) bozo: Fix linker problem on Linux
    2011-01-31 Simon Wilkinson   (3774) Windows: Install rx_atomic.h
    2011-01-31 Simon Wilkinson   (3767) Unix CM: Move kernel crypto include files
    2011-01-31 Jeffrey Altman    (3773) Windows: out of order locks cm_CheckCBExpiration
    2011-01-29 Simon Wilkinson   (3766) aklog: Use correct CFLAGS
    2011-01-28 Rod Widdowson     (3768) Do not compare an FD_t < 0
    2011-01-27 Marc Dionne       (3759) linux: 2.6.38: Make d_revalidate RCU-walk aware
    2011-01-27 Marc Dionne       (3758) linux: 2.6.38: New d_op handling
    2011-01-27 Andrew Deason     (3431) RX: Avoid retrying calls on busy channels
    2011-01-27 Simon Wilkinson   (3761) Import of code from heimdal
    2011-01-27 Jeffrey Altman    (3760) Windows: Correct cm_volume locking
    2011-01-25 Andrew Deason     (3756) vol-salvage: Only delete bad vnodes during !check
    2011-01-25 Derrick Brashear  (3755) MacOS: fix SetFile call in growlagent makefile
    2011-01-25 Jeffrey Altman    (3648) Windows: cm_GiveUpAllCallBacksAllServersMulti()
    2011-01-25 Rod Widdowson     (3746) Windows: fix parameters and return value from nt_seek
    2011-01-25 Rod Widdowson     (3744) Windows: read and write take void* buffers, open takes a const char*
    2011-01-24 Antoine Verheijen (3751) OpenBSD: Eliminate complaint about built-in malloc.
    2011-01-24 Antoine Verheijen (3750) OpenBSD: Remove user.h from dir.c for OpenBSD 4.8
    2011-01-24 Antoine Verheijen (3749) OpenBSD: curproc has moved in OpenBSD 4.8
    2011-01-24 Antoine Verheijen (3748) OpenBSD: Add support for OpenBSD 4.8
    2011-01-24 Rod Widdowson     (3747) Windows: remove unused label in ntops.c
    2011-01-24 Rod Widdowson     (3745) Windows: remove faulty assumptions about device names in vol-salvage
    2011-01-23 Jeffrey Altman    (3739) Windows: more exports afsauthent.dll
    2011-01-23 Jeffrey Altman    (3742) Windows: log and invalidate invalid dir pages
    2011-01-22 Antoine Verheijen (3725) OpenBSD: Make OpenBSD 4.7 param headers consistent
    2011-01-22 Jeffrey Altman    (3712) vol: namei_ops improve readability; fix namei_create on Windows
    2011-01-22 Jeffrey Altman    (3711) vol: fix CreateFile params nt_unlink and nt_open
    2011-01-22 Jeffrey Altman    (3707) vol: add comment nt_unlink cannot with fopen handles
    2011-01-22 Jeffrey Altman    (3706) vol: remove potential data loss warnings in vol-salvage.c
    2011-01-22 Jeffrey Altman    (3705) vol: use correct file name base for temporary file
    2011-01-22 Jeffrey Altman    (3704) vol: use OS_UNLINK instead of unlink
    2011-01-22 Jeffrey Altman    (3703) vol: fix namei_ListAFSSubDirs on Windows
    2011-01-22 Jeffrey Altman    (3702) vol: use OS_DIRSEP in many more places
    2011-01-22 Jeffrey Altman    (3701) vol: fix _namei_examine_reg DELETE_ZLC usage
    2011-01-22 Jeffrey Altman    (3700) vol: make it clearer that SetOGM is not impl on Windows
    2011-01-22 Jeffrey Altman    (3699) vol: avoid double dir separators from addtoname
    2011-01-22 Jeffrey Altman    (3696) vol: clear ih_synced before dropping lock
    2011-01-20 Derrick Brashear  (3690) MacOS: don't allow krb5 at login when AD plugin authenticates
    2011-01-20 Jeffrey Altman    (3710) vol: nt_DriveToDev must return a value
    2011-01-20 Jeffrey Altman    (3709) vol: nt_open should not create missing directories
    2011-01-20 Jeffrey Altman    (3708) vol: Make ntops functions 64-bit capable
    2011-01-20 Jeffrey Altman    (3698) vol: avoid defining unused struct on windows
    2011-01-20 Jeffrey Altman    (3697) vol: indent cpp definitions; add NAMEI_SPECDIRC
    2011-01-20 Jeffrey Altman    (3695) vol: remove [UN]LOCKFILE data loss warnings on Windows
    2011-01-20 Jeffrey Altman    (3693) Windows: build mtafsdir.lib and use it
    2011-01-20 Toby Burress      (3692) FreeBSD: properly identify the rxk_Listener so that msleep() returns
    2011-01-20 Antoine Verheijen (3689) OpenBSD: Change code optimization setting
    2011-01-20 Antoine Verheijen (3688) Move check for unspecified CFLAGS in configure.ac
    2011-01-20 Antoine Verheijen (3687) OpenBSD: No ruid/rgid in cred structure.
    2011-01-20 Antoine Verheijen (3686) OpenBSD: Don't call non-existent routines in osi_vfsops.c
    2011-01-19 Antoine Verheijen (3685) OpenBSD: Fix parameters in call to afs_close()
    2011-01-19 Antoine Verheijen (3684) OpenBSD: Install no-NFS version of libafs
    2011-01-19 Derrick Brashear  (3683) MacOS: panic decoder should check for unloaded kexts
    2011-01-19 Antoine Verheijen (3682) OpenBSD: Fix use of macros for AFS_KALLOC/AFS_KFREE
    2011-01-19 Antoine Verheijen (3681) OpenBSD: Remove macros definitions for afs_osi_Alloc et al.
    2011-01-18 Jeffrey Altman    (3675) volser: select() cannot be used to sleep on windows
    2011-01-18 Jeffrey Altman    (3674) Windows: refactor cm_CheckCBExpiration multihomed
    2011-01-18 Jeffrey Altman    (3659) Windows: use cm_ServerEqual() in cm_Analyze()
    2011-01-18 Rainer Toebbicke  (3677) Re-enable rx connection hard timeout
    2011-01-17 Andrew Deason     (3676) vol: Windows requires binary fmode for salvaged
    2011-01-16 Jeffrey Altman    (3670) vol: use OS_UNLINK() instead of unlink()
    2011-01-15 Jeffrey Altman    (3672) vol: construct proper VolDir path on Windows
    2011-01-15 Jeffrey Altman    (3671) vol: fdHandleAllocateChunk should init all fields
    2011-01-15 Jeffrey Altman    (3669) vol: use OS_DIRSEP when constructing paths
    2011-01-15 Jeffrey Altman    (3668) volser: use OS_CLOSE() instead of close()
    2011-01-15 Jeffrey Altman    (3667) vol: initialize FdHandle_t stack objects
    2011-01-15 Jeffrey Altman    (3666) vol: Fix ntops to provide expected semantics
    2011-01-15 Jeffrey Altman    (3665) vol: Windows requires binary fmode for salvager
    2011-01-15 Jeffrey Altman    (3664) vol: fix OS_LOCKFILE/OS_UNLOCKFILE for Windows
    2011-01-15 Andrew Deason     (3663) RX: Pre-10 Solaris lacks atomic inc/dec
    2011-01-15 Andrew Deason     (3662) RX: Include netinet/ip6.h before inet/ip.h
    2011-01-15 Andrew Deason     (3661) merge-pod: Be more compatible with older perl
    2011-01-15 Benjamin Kaduk    (3656) FBSD: remove vestiges of Giant
    2011-01-14 Jeffrey Altman    (3658) Windows: fixup gettmpdir()
    2011-01-14 Jeffrey Altman    (3657) Windows: osilog param size is size_t
    2011-01-13 Andrew Deason     (3652) RX: No userspace atomic_ops in Solaris pre-10
    2011-01-13 Derrick Brashear  (3651) afsd: CellItems doesn't apply to memcache mode
    2011-01-12 Andrew Deason     (3653) SOLARIS: Include sys/varargs.h for kernel stdarg
    2011-01-11 Marc Dionne       (3637) Cache bypass: fix use of incorrect "states"
    2011-01-10 Andrew Deason     (3636) LINUX: afs_linux_put_link is void
    2011-01-10 Stephan Wiesand   (3628) rpm: don't package files twice
    2011-01-10 Andrew Deason     (3627) git-version: Do not specify --ignore-submodules
    2011-01-10 Jeffrey Altman    (3630) Windows: refactor buf_Get() to improve readability
    2011-01-10 Jeffrey Altman    (3629) Windows: remove all refs to unused buf_GetNew()
    2011-01-05 Tom Keiser        (2969) provide more verbose logging when VGetVolumeByVp_r fails
    2011-01-04 Jeffrey Altman    (3617) Windows: remove unused vars from cm_server.c
    2011-01-04 Jeffrey Altman    (3616) Windows: netidmgr_plugin move roken.h to afscred.h
    2011-01-04 Jeffrey Altman    (3615) Windows: permit clean when switching platforms
    2011-01-03 Simon Wilkinson   (3614) Unix CM: Don't blow up if we have non-rxkad tokens
    2011-01-03 Simon Wilkinson   (3613) roken: Check for bswap16 and bswap32 defines
    2011-01-03 Simon Wilkinson   (3612) autoconf: Tidy up header includes
    2011-01-02 Simon Wilkinson   (3611) auth: Move key related code to its own file
    2011-01-02 Simon Wilkinson   (3608) libadmin: Don't use internal struct for key data
    2011-01-02 Simon Wilkinson   (3610) tests: Add more tests for auth KeyFile handling
    2011-01-02 Simon Wilkinson   (3609) roken: Export more snprintf symbols
    2011-01-02 Simon Wilkinson   (2585) Add "brief" option to rxgen
    2011-01-02 Simon Wilkinson   (3581) rx: Implement rx_atomic_dec_and_read
    2011-01-02 Simon Wilkinson   (3580) rx: Protect rx_atomic.h against multiple inclusion
    2011-01-02 Simon Wilkinson   (3607) auth: Don't crash if UserList contains bogus line
    2011-01-02 Simon Wilkinson   (3606) rx: Don't crash when emptying an empty identity

### Patches merged into the stable 1.6.x branch

    Date       Committer        Change# Description
    2011-02-13 Jeffrey Altman    (3937) Windows: Release Notes updates for 1.6pre2
    2011-02-13 Jeffrey Altman    (3934) Windows: ChangeLog updates for 1.6.pre2
    2011-02-13 Marc Dionne       (3935) Linux: 2.6.38: dentry->d_count is not an atomic
    2011-02-13 Jeffrey Altman    (3933) Windows: 1.5.78 Change Log summary
    2011-02-13 Jeffrey Altman    (3931) Windows: Version 1.6pre2
    2011-02-13 Jeffrey Altman    (3930) doc: Do not process .in files for html
    2011-02-13 Jeffrey Altman    (3929) Windows: Fix GetIoctlHandle path construction
    2011-02-13 Jeffrey Altman    (3928) Windows: Fix symlink and mount point make \\afs\xxx handling
    2011-02-11 Antoine Verheijen (3923) OpenBSD: curproc has moved in OpenBSD 4.8
    2011-02-11 Antoine Verheijen (3922) OpenBSD: Add support for OpenBSD 4.8
    2011-02-11 Antoine Verheijen (3920) OpenBSD: Make OpenBSD 4.7 param headers consistent
    2011-02-11 Derrick Brashear  (3919) evalmountdata null pointer before use
    2011-02-11 Derrick Brashear  (3918) Linux: 2.6.38: deal with dcache_lock removal
    2011-02-11 Derrick Brashear  (3917) Linux: 2.6.38: Adjust for permission inode operation changes
    2011-02-11 Derrick Brashear  (3916) Linux: allow compile flags to be passed to AC_CHECK_LINUX_BUILD
    2011-02-11 Derrick Brashear  (3915) Windows: correct pthread_xxx_init semantics
    2011-02-10 Derrick Brashear  (3806) Windows: cleanup preprocessor definition namespace
    2011-02-10 Derrick Brashear  (3914) Windows: remove duplicate advapi32.lib references
    2011-02-10 Derrick Brashear  (3913) spelling/grammar fixes for manpages
    2011-02-10 Derrick Brashear  (3912) spelling/grammar fixes for vos_clone manpage
    2011-02-10 Derrick Brashear  (3911) Windows: No NCBRESET when probing Loopback after start
    2011-02-08 Derrick Brashear  (3908) namei: Limit traversal when removing data dirs
    2011-02-08 Derrick Brashear  (3907) namei: Do not remove n_voldir1
    2011-02-08 Derrick Brashear  (3906) Remove unreached lines
    2011-02-08 Derrick Brashear  (3905) vol: Always use INVALID_FD to indicate an invalid fd
    2011-02-08 Derrick Brashear  (3858) Windows: more exports afsauthent.dll
    2011-02-08 Derrick Brashear  (3859) Windows: remove faulty assumptions about device names in vol-salvage
    2011-02-08 Derrick Brashear  (3860) Windows: remove unused label in ntops.c
    2011-02-08 Derrick Brashear  (3861) OpenBSD: Remove user.h from dir.c for OpenBSD 4.8
    2011-02-08 Derrick Brashear  (3862) OpenBSD: Eliminate complaint about built-in malloc.
    2011-02-08 Derrick Brashear  (3863) Windows: read and write take void* buffers, open takes a const char*
    2011-02-08 Derrick Brashear  (3864) Windows: fix parameters and return value from nt_seek
    2011-02-08 Derrick Brashear  (3865) Windows: cm_GiveUpAllCallBacksAllServersMulti()
    2011-02-08 Derrick Brashear  (3866) vol-salvage: Only delete bad vnodes during !check
    2011-02-08 Derrick Brashear  (3867) Windows: Correct cm_volume locking
    2011-02-08 Derrick Brashear  (3887) vol: Add VInit cond var and remove busywaits
    2011-02-08 Derrick Brashear  (3886) Avoid thread-unsafe PrintInode in threaded code
    2011-02-08 Derrick Brashear  (3885) vol: Use OSI_NULLSOCKET and not -1 to indicate invalid fssync fd
    2011-02-08 Derrick Brashear  (3878) Rx: Do not stop keepalives on ACKALL receipt
    2011-02-08 Derrick Brashear  (3872) Windows: out of order locks cm_CheckCBExpiration
    2011-02-08 Derrick Brashear  (3871) Do not compare an FD_t < 0
    2011-02-08 Derrick Brashear  (3870) linux: 2.6.38: Make d_revalidate RCU-walk aware
    2011-02-08 Derrick Brashear  (3869) linux: 2.6.38: New d_op handling
    2011-02-08 Andrew Deason     (3763) RX: Avoid retrying calls on busy channels
    2011-02-08 Derrick Brashear  (3857) Windows: log and invalidate invalid dir pages
    2011-02-08 Derrick Brashear  (3856) vol: fix CreateFile params nt_unlink and nt_open
    2011-02-08 Derrick Brashear  (3855) vol: namei_ops improve readability; fix namei_create on Windows
    2011-02-08 Derrick Brashear  (3854) vol: add comment nt_unlink cannot with fopen handles
    2011-02-08 Derrick Brashear  (3853) vol: remove potential data loss warnings in vol-salvage.c
    2011-02-07 Derrick Brashear  (3894) Use afs_foff_t for file offsets
    2011-02-07 Derrick Brashear  (3851) vol: use OS_UNLINK instead of unlink
    2011-02-07 Derrick Brashear  (3850) vol: fix namei_ListAFSSubDirs on Windows
    2011-02-07 Derrick Brashear  (3852) vol: use correct file name base for temporary file
    2011-02-07 Derrick Brashear  (3900) vol: use OS_DIRSEP in many more places
    2011-02-04 Derrick Brashear  (3841) vol: indent cpp definitions; add NAMEI_SPECDIRC
    2011-02-04 Derrick Brashear  (3840) vol: remove [UN]LOCKFILE data loss warnings on Windows
    2011-02-04 Derrick Brashear  (3843) vol: Make ntops functions 64-bit capable
    2011-02-04 Derrick Brashear  (3842) vol: avoid defining unused struct on windows
    2011-02-04 Derrick Brashear  (3844) vol: nt_open should not create missing directories
    2011-02-04 Derrick Brashear  (3845) vol: clear ih_synced before dropping lock
    2011-02-04 Derrick Brashear  (3847) vol: make it clearer that SetOGM is not impl on Windows
    2011-02-04 Derrick Brashear  (3846) vol: avoid double dir separators from addtoname
    2011-02-04 Derrick Brashear  (3848) vol: fix _namei_examine_reg DELETE_ZLC usage
    2011-02-04 Derrick Brashear  (3839) MacOS: panic decoder should check for unloaded kexts
    2011-02-04 Derrick Brashear  (3838) volser: select() cannot be used to sleep on windows
    2011-02-04 Derrick Brashear  (3837) Windows: refactor cm_CheckCBExpiration multihomed
    2011-02-04 Derrick Brashear  (3836) Windows: use cm_ServerEqual() in cm_Analyze()
    2011-02-04 Derrick Brashear  (3833) vol: construct proper VolDir path on Windows
    2011-02-04 Derrick Brashear  (3835) vol: Windows requires binary fmode for salvaged
    2011-02-04 Derrick Brashear  (3832) vol: fdHandleAllocateChunk should init all fields
    2011-02-04 Derrick Brashear  (3834) vol: use OS_UNLINK() instead of unlink()
    2011-02-04 Derrick Brashear  (3889) vol: make namei_ListAFSSubDirs deal with multiple/bad linktables
    2011-02-04 Derrick Brashear  (3831) vol: use OS_DIRSEP when constructing paths
    2011-02-03 Derrick Brashear  (3830) volser: use OS_CLOSE() instead of close()
    2011-02-03 Derrick Brashear  (3829) vol: initialize FdHandle_t stack objects
    2011-02-03 Derrick Brashear  (3828) vol: Fix ntops to provide expected semantics
    2011-02-03 Derrick Brashear  (3827) merge ntops and namei
    2011-02-03 Derrick Brashear  (3884) ihandle positional read and write
    2011-02-03 Derrick Brashear  (3826) Parallel I/O extensions to namei backend
    2011-02-03 Derrick Brashear  (3825) windows: native versions of ih_pread and ih_pwrite
    2011-02-03 Derrick Brashear  (3824) vol: Windows requires binary fmode for salvager
    2011-02-03 Derrick Brashear  (3823) vol: fix OS_LOCKFILE/OS_UNLOCKFILE for Windows
    2011-02-03 Derrick Brashear  (3820) Windows: fixup gettmpdir()
    2011-02-03 Derrick Brashear  (3819) Windows: osilog param size is size_t
    2011-02-03 Derrick Brashear  (3818) rpm: don't package files twice
    2011-02-03 Derrick Brashear  (3817) git-version: Do not specify --ignore-submodules
    2011-02-03 Derrick Brashear  (3816) Windows: refactor buf_Get() to improve readability
    2011-02-03 Derrick Brashear  (3815) Windows: remove all refs to unused buf_GetNew()
    2011-02-03 Derrick Brashear  (3814) Windows: remove unused vars from cm_server.c
    2011-02-03 Derrick Brashear  (3813) Windows: permit clean when switching platforms
    2011-02-03 Derrick Brashear  (3812) Add "brief" option to rxgen
    2011-02-03 Derrick Brashear  (3807) vos: do not mix memory allocation methods
    2011-02-03 Derrick Brashear  (3808) Windows: fs checkservers should list vldb as well
    2011-02-03 Derrick Brashear  (3809) Windows: fs checkserver skip multi-homed up server
    2011-02-03 Derrick Brashear  (3810) Windows: buf_CleanAsync scp->fid == bp->fid
    2011-02-03 Derrick Brashear  (3811) Windows: MIT license applies to parsemode()
    2011-02-02 Derrick Brashear  (3805) Windows: separate parsemode from fs into own file
    2011-02-02 Derrick Brashear  (3804) Windows: fs chmod and display mode in fs examine
    2011-02-02 Derrick Brashear  (3877) afsd: Do not check for /afs if -nomount
    2011-02-01 Derrick Brashear  (3803) Windows: clear mountPointStringp on status change
    2011-02-01 Derrick Brashear  (3802) Windows: Add VIOC_GETUNIXMODE and VIOC_SETUNIXMODE
    2011-02-01 Derrick Brashear  (3801) Windows: log error code for smb lan thread fail
    2011-02-01 Derrick Brashear  (3800) Windows: PerformanceTuningInterval Merge error
    2011-02-01 Derrick Brashear  (3799) DAFS: Avoid logging harmless LEAVE_OFF failures
    2011-02-01 Derrick Brashear  (3798) DAFS: Fix VOL_QUERY_VOP error codes
    2011-02-01 Derrick Brashear  (3797) Fix AUD_HOST callers
    2011-02-01 Derrick Brashear  (3796) tvolser: Link libafsrpc after libusd
    2011-02-01 Derrick Brashear  (3795) DAFS: make FSYNC_VOL_QUERY_VOP DAFS-only
    2011-02-01 Derrick Brashear  (3794) DAFS: fix ifdef
    2011-02-01 Derrick Brashear  (3793) Windows: test for path in afs before symlink test
    2011-02-01 Derrick Brashear  (3792) vol_split: Recover from stream open failure
    2011-02-01 Derrick Brashear  (3791) Windows: fix checked UNICODE build of talocale
    2011-02-01 Derrick Brashear  (3790) Windows: Build afs_shl_ext.dll with talocaleU.lib
    2011-02-01 Derrick Brashear  (3789) Windows: install afs_shl_ext icon files
    2011-02-01 Derrick Brashear  (3788) Windows: build a UNICODE version of talocale.lib
    2011-02-01 Derrick Brashear  (3787) Windows: fix UNICODE build for talocale
    2011-02-01 Derrick Brashear  (3786) Windows: afs_shl_ext improve overlay handlers
    2011-01-31 Derrick Brashear  (3875) evalmountdata: put back colon in .:mount syntax only if we removed it
    2011-01-31 Derrick Brashear  (3785) Windows: afs_shl_ext Show icon mount point overlay
    2011-01-31 Derrick Brashear  (3784) Windows: afs_shl_ext folder bkgrnd context menu
    2011-01-31 Derrick Brashear  (3783) Windows: Remove fallback from GetCaps to GetTime
    2011-01-31 Derrick Brashear  (3782) Unix afsd: Check for mountpoint /afs first
    2011-01-31 Derrick Brashear  (3781) vos: Improve release recovery on timed-out trans
    2011-01-31 Derrick Brashear  (3780) Windows: NSIS installer requires the architecture for CL=1400
    2011-01-31 Derrick Brashear  (3779) Windows: make use of AFSDEV_BIN and set the PATH
    2011-01-31 Derrick Brashear  (3778) merge-pod: Be more compatible with older perl
    2011-01-26 Derrick Brashear  (3757) MacOS: fix SetFile call in growlagent makefile
    2011-01-25 Benjamin Kaduk    (3754) FreeBSD: properly identify the rxk_Listener so that msleep() returns
    2011-01-22 Antoine Verheijen (3724) OpenBSD: Change code optimization setting
    2011-01-22 Antoine Verheijen (3723) OpenBSD: Install no-NFS version of libafs
    2011-01-22 Antoine Verheijen (3722) OpenBSD: Remove duplicate assignment of COMMON_INCLUDE in libafs
    2011-01-22 Antoine Verheijen (3721) OpenBSD: Don't call non-existent routines in osi_vfsops.c
    2011-01-22 Antoine Verheijen (3720) Move include of sys/types.h in kopenafs.c
    2011-01-22 Antoine Verheijen (3719) OpenBSD: Fix parameters in call to afs_close()
    2011-01-22 Antoine Verheijen (3718) OpenBSD: Fix use of macros for AFS_KALLOC/AFS_KFREE
    2011-01-22 Antoine Verheijen (3717) OpenBSD: Remove macros definitions for afs_osi_Alloc et al.
    2011-01-22 Antoine Verheijen (3716) OpenBSD: No ruid/rgid in cred structure.
    2011-01-18 Derrick Brashear  (3680) Re-enable rx connection hard timeout
    2011-01-18 Derrick Brashear  (3679) FBSD: remove vestiges of Giant
    2011-01-18 Derrick Brashear  (3678) afsd: CellItems doesn't apply to memcache mode
    2011-01-13 Derrick Brashear  (3655) SOLARIS: Include sys/varargs.h for kernel stdarg
    2011-01-12 Derrick Brashear  (3654) FBSD: we're 64 bit capable
    2011-01-12 Derrick Brashear  (3650) FBSD7: Don't sleep with the glock
    2011-01-12 Derrick Brashear  (3649) Bring FBSD 7.X client back to life
    2011-01-12 Derrick Brashear  (3647) Cache bypass: switch to rx_Readv
    2011-01-12 Derrick Brashear  (3646) Cache bypass: Only compile bypass code for the Linux kernel
    2011-01-12 Derrick Brashear  (3645) Cache bypass: remove ifdefs under src/afs/LINUX
    2011-01-12 Derrick Brashear  (3644) Cache bypass: release and unlock pages when we get 0-length reply
    2011-01-12 Derrick Brashear  (3643) Cache bypass: adjust read size for non-contiguous readpages
    2011-01-11 Derrick Brashear  (3642) Cache bypass: make readpage deal with reads at end of file
    2011-01-11 Derrick Brashear  (3641) Cache bypass: Remove AFS_KMAP_ATOMIC
    2011-01-11 Derrick Brashear  (3640) Cache bypass: fix use of incorrect "states"
    2011-01-11 Derrick Brashear  (3639) Cache bypass: Fix oops in bypass transition functions
    2011-01-11 Derrick Brashear  (3638) Zero rx_multi_lock before initializing it
    2011-01-10 Andrew Deason     (3620) provide more verbose logging when VGetVolumeByVp_r fails
    2011-01-10 Benjamin Kaduk    (3633) FBSD: StopListener glocking fixup
    2011-01-10 Andrew Deason     (3626) vos: free ubulkentries with xdr_free
    2011-01-10 Andrew Deason     (3624) vos release: Avoid full dump on all sites
    2011-01-10 Andrew Deason     (3635) volser: Fix broken bulk conversion
    2011-01-10 Andrew Deason     (3634) vos: Abstract out bulk list conversion
    2011-01-10 Benjamin Kaduk    (3631) FBSD: close race in afs_root
    2011-01-10 Benjamin Kaduk    (3632) FBSD: band-aid vnode locking in lookup
    2011-01-05 Andrew Deason     (3618) Use afs_foff_t for file offsets
    2011-01-02 Andrew Deason     (3571) HPUX: Allow des.c to compile

### Patches merged into the stable 1.4.x branch

    Date       Committer        Change# Description
    2011-01-25 Simon Wilkinson   (3753) Removed kpasswd from openafs-file-list
    2010-12-23 Andrew Deason     (3587) SOLARIS: Free vcache mappings on shutdown
    2010-12-23 Andrew Deason     (3586) UINT_MAX requires limits.h
    2010-12-23 Andrew Deason     (3585) rxkad heimdal cleanup
    2010-12-22 Andrew Deason     (3574) vos status: actually show created time
    2010-12-22 Andrew Deason     (3572) vol: Log ignored dirs that look like partitions
    2010-12-22 Christof Hanke    (3541) Honour --enable-debug for userspace parts
    2010-12-22 Andrew Deason     (3573) vos: Mark longjmp-used variables as 'volatile'
    2010-12-16 Derrick Brashear  (3534) LINUX: Use correct type of error in flock code
    2010-12-15 Marc Dionne       (3529) Linux 2.4: Restore missing unlock_kernel()
    2010-12-14 Derrick Brashear  (3523) update ticket5 from heimdal
    2010-12-14 Marc Dionne       (3512) Linux: define llseek operations
    2010-12-13 Jeffrey Altman    (3505) CellServDB update 13 Dec 2010
    2010-12-07 Antoine Verheijen (3426) OpenBSD: Add ifaddr_* macros to osi_machdep.h
    2010-12-07 Antoine Verheijen (3478) OpenBSD: Use Darwin version of afsi_SetServerIPRank() for OpenBSD 4.7 and above.
    2010-12-07 Antoine Verheijen (3474) Darwin: Assign correct value to myDstaddr in afsi_SetServerIPRank()
    2010-12-07 Antoine Verheijen (3473) DARWIN: Fix processing using ifaddr_* macros in afsi_SetServerIPRank()
