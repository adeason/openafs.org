---
title: OpenAFS Newsletter, Volume 3, Issue 1, January 2011
layout: page
category: newsletter
permalink: /newsletter/newsletter-2011-01-volume003-issue01.html
---

# OpenAFS Newsletter, Volume 3, Issue 1, January 2011

Welcome to the January issue of the OpenAFS newsletter. This newsletter
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

The 1.6.0 release candidate 1 is available for download from
[http://www.openafs.org/release/openafs-1.6.0pre1.html](http://www.openafs.org/release/openafs-1.6.0pre1.html). The 1.6.x series
will be the new stable release series for OpenAFS. 1.6.0 includes all of
the changes from the 1.5.x series. The differences between the 1.4.x and
1.6.x series are too numerous to mention.

Release 1.4.14 is available from
[http://www.openafs.org/dl/openafs/1.4.14/](http://www.openafs.org/dl/openafs/1.4.14/). Changes include numberous
fixes and support the Linux kernel versions up to 2.6.37.

## AFS Protocol Standardization

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://lists.openafs.org/mailman/listinfo/afs3-standardization](http://lists.openafs.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names)

Status: Eighth Draft (07) - Consensus reached

A minor wording clarification will be provided, at which point this
will be ready to be ratified as a standard.
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
available on their web site, the current rxgk code is, as always,
available on github.

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
openafs-rxgk repository.  A version with important bugfixes should be
available in the next 1-2 weeks.

\--Matt

### User-space cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

The PIC-related problems with the libuafs perl bindings on some
platforms have been fixed, and will be submitted to gerrit sometime
soon. There will certainly be other issues and such to discuss when that
happens, but this is seeing progress again.

\--Andrew

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Mac OS X OpenAFS Preference Pane - April 2010
- S3 Front-end for AFS - July 2010
- Kerberos v5 and multiple encryption types - July 2010
- Per-File ACLs - August 2010
- Virtual Machine Images - November 2010
- Rx OSD integration & Raw Vicep Access in Clients - November 2010
- Better Documentation - December 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Patches merged into the master branch:
    Month   Number of Commits
    2011-01   30 (Partial month)
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
    2009-12   72

    Patches merged into the stable 1.4.x branch:
    Month   Number of Commits
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
    2009-12  92

### Patches merged into the master branch

    Date       Committer       Change# Description
    2011-01-15 Andrew Deason    (3662) RX: Include netinet/ip6.h before inet/ip.h
    2011-01-15 Andrew Deason    (3661) merge-pod: Be more compatible with older perl
    2011-01-15 Benjamin Kaduk   (3656) FBSD: remove vestiges of Giant
    2011-01-14 Jeffrey Altman   (3658) Windows: fixup gettmpdir()
    2011-01-14 Jeffrey Altman   (3657) Windows: osilog param size is size_t
    2011-01-13 Andrew Deason    (3652) RX: No userspace atomic_ops in Solaris pre-10
    2011-01-13 Derrick Brashear (3651) afsd: CellItems doesn't apply to memcache mode
    2011-01-12 Andrew Deason    (3653) SOLARIS: Include sys/varargs.h for kernel stdarg
    2011-01-11 Marc Dionne      (3637) Cache bypass: fix use of incorrect "states"
    2011-01-10 Andrew Deason    (3636) LINUX: afs_linux_put_link is void
    2011-01-10 Stephan Wiesand  (3628) rpm: don't package files twice
    2011-01-10 Andrew Deason    (3627) git-version: Do not specify --ignore-submodules
    2011-01-10 Jeffrey Altman   (3630) Windows: refactor buf_Get() to improve readability
    2011-01-10 Jeffrey Altman   (3629) Windows: remove all refs to unused buf_GetNew()
    2011-01-05 Tom Keiser       (2969) provide more verbose logging when VGetVolumeByVp_r fails
    2011-01-04 Jeffrey Altman   (3617) Windows: remove unused vars from cm_server.c
    2011-01-04 Jeffrey Altman   (3616) Windows: netidmgr_plugin move roken.h to afscred.h
    2011-01-04 Jeffrey Altman   (3615) Windows: permit clean when switching platforms
    2011-01-03 Simon Wilkinson  (3614) Unix CM: Don't blow up if we have non-rxkad tokens
    2011-01-03 Simon Wilkinson  (3613) roken: Check for bswap16 and bswap32 defines
    2011-01-03 Simon Wilkinson  (3612) autoconf: Tidy up header includes
    2011-01-02 Simon Wilkinson  (3611) auth: Move key related code to its own file
    2011-01-02 Simon Wilkinson  (3608) libadmin: Don't use internal struct for key data
    2011-01-02 Simon Wilkinson  (3610) tests: Add more tests for auth KeyFile handling
    2011-01-02 Simon Wilkinson  (3609) roken: Export more snprintf symbols
    2011-01-02 Simon Wilkinson  (2585) Add "brief" option to rxgen
    2011-01-02 Simon Wilkinson  (3581) rx: Implement rx_atomic_dec_and_read
    2011-01-02 Simon Wilkinson  (3580) rx: Protect rx_atomic.h against multiple inclusion
    2011-01-02 Simon Wilkinson  (3607) auth: Don't crash if UserList contains bogus line
    2011-01-02 Simon Wilkinson  (3606) rx: Don't crash when emptying an empty identity
    2010-12-30 Jeffrey Altman   (3605) Windows: MIT license applies to parsemode()
    2010-12-29 Jeffrey Altman   (3604) Windows: buf_CleanAsync scp->fid == bp->fid
    2010-12-28 Jeffrey Altman   (3603) Windows: fs checkserver skip multi-homed up server
    2010-12-28 Jeffrey Altman   (3602) Windows: fs checkservers should list vldb as well
    2010-12-28 Jeffrey Altman   (3600) vos: do not mix memory allocation methods
    2010-12-28 Jeffrey Altman   (3599) Windows: cleanup preprocessor definition namespace
    2010-12-28 Jeffrey Altman   (3591) Windows: separate parsemode from fs into own file
    2010-12-28 Jeffrey Altman   (3590) vos: free ubulkentries with xdr_free
    2010-12-27 Simon Wilkinson  (3598) tests: Add tests for afsconf_'s key functions
    2010-12-27 Simon Wilkinson  (3597) Don't trust # of entries from ListAttributes
    2010-12-27 Andrew Deason    (3575) Remove extra trailing \s in Makefiles
    2010-12-27 Simon Wilkinson  (3596) volser: Fix broken bulk conversion
    2010-12-27 Simon Wilkinson  (3595) vos: Abstract out bulk list conversion
    2010-12-27 Andrew Deason    (3584) Link hcrypto before roken
    2010-12-26 Russ Allbery     (3592) Update NEWS for 1.5.78 and 1.6.0pre1
    2010-12-26 Simon Wilkinson  (3593) auth: Add more tests and resulting fixes to userok
    2010-12-23 Derrick Brashear (3588) DAFS: listvol + unsalvagable volumes = intolerable delay
    2010-12-23 Andrew Deason    (3583) Prefer libHcurses over libcurses
    2010-12-23 Andrew Deason    (3582) HPUX: Put __HP_CURSES back in
    2010-12-22 Simon Wilkinson  (3579) rx: Make rx_atomic.h a shared header
    2010-12-22 Derrick Brashear (3564) LWP: kill dead code
    2010-12-22 Derrick Brashear (3556) LWP: don't copy pid to a null pointer
    2010-12-22 Andrew Deason    (3569) LINUX: Avoid unnecessary afs_ShakeLooseVCaches
    2010-12-22 Andrew Deason    (3433) LINUX: Reduce stack depth on recursive symlink res
    2010-12-21 Andrew Deason    (3568) Cache bypass: remove ifdefs under src/afs/LINUX24
    2010-12-21 Derrick Brashear (3565) DARWIN: replace resource merge script ref with binary
    2010-12-21 Derrick Brashear (3563) DARWIN: make growlagent build not run afoul of ._ fun
    2010-12-21 Derrick Brashear (3562) DARWIN: make ARCHFLAGS propagate to shlibs
    2010-12-21 Jeffrey Altman   (3546) Windows: fs chmod and display mode in fs examine
    2010-12-21 Derrick Brashear (3555) backup: pass in valid dummy pid for LWP
    2010-12-21 Andrew Deason    (3553) LINUX24: Include linux/pagemap.h
    2010-12-20 Andrew Deason    (3554) LINUX24: Define afs_linux_can_bypass
    2010-12-20 Benjamin Kaduk   (3551) FBSD7: Don't sleep with the glock
    2010-12-20 Benjamin Kaduk   (3549) FBSD: StopListener glocking fixup
    2010-12-20 Benjamin Kaduk   (3548) Bring FBSD 7.X client back to life
    2010-12-20 Benjamin Kaduk   (3550) Zero rx_multi_lock before initializing it
    2010-12-20 Jeffrey Altman   (3552) Windows: clear mountPointStringp on status change
    2010-12-20 Jeffrey Altman   (3545) Windows: Add VIOC_GETUNIXMODE and VIOC_SETUNIXMODE
    2010-12-19 Jeffrey Altman   (3544) Fix fallback processing for ktc_GetTokenEx()
    2010-12-18 Derrick Brashear (3542) darwin: fix fixed setpag error handling
    2010-12-16 Derrick Brashear (3532) macos nfs translator vnode ref fix
    2010-12-13 Anders Kaseorg   (3276) Linux: Fix AFS_NORETURN violation with osi_AssertFailK
    2010-12-13 Simon Wilkinson  (3139) opr: Add new queue implementation
    2010-12-13 Derrick Brashear (3403) refactor afs_CheckServers
    2010-12-13 Andrew Deason    (3498) Add ioctl-based AFS calls for Solaris 11
    2010-12-13 Jeffrey Altman   (3503) CellServDB update 13 Dec 2010
    2010-12-13 Jeffrey Altman   (3502) Windows: log error code for smb lan thread fail
    2010-12-12 Jeffrey Altman   (3500) Windows: PerformanceTuningInterval Merge error
    2010-12-10 Andrew Deason    (3499) Add afs init script for Solaris 11
    2010-12-10 Andrew Deason    (3494) DAFS: Avoid logging harmless LEAVE_OFF failures
    2010-12-10 Andrew Deason    (3493) DAFS: Fix VOL_QUERY_VOP error codes
    2010-12-10 Andrew Deason    (3497) DARWIN: Fix setpag syscall error detection
    2010-12-10 Christof Hanke   (3434) Fix mech of building export on AIX
    2010-12-10 Andrew Deason    (3492) Fix AUD_HOST callers
    2010-12-09 Andrew Deason    (3482) auth: Move <NoAuth> to a named constant
    2010-12-09 Andrew Deason    (3477) tvolser: Link libafsrpc after libusd
    2010-12-09 Andrew Deason    (3475) auth: Return SuperUser identity for localauth
    2010-12-08 Anders Kaseorg   (3491) rxi_NatKeepAliveEvent: Shrink excessive stack buffer
    2010-12-08 Derrick Brashear (3485) DAFS: make FSYNC_VOL_QUERY_VOP DAFS-only
    2010-12-08 Derrick Brashear (3484) DAFS: fix ifdef
    2010-12-07 Andrew Deason    (3472) SOLARIS: Free vcache mappings on shutdown
    2010-12-07 Jeffrey Altman   (3468) modify FindIndex to compare uuids
    2010-12-07 Derrick Brashear (3471) afsconf_SuperUser verify identity before use
    2010-12-07 Jeffrey Altman   (3469) Windows: partial impl of TokenEx functions
    2010-12-07 Jeffrey Altman   (3467) Windows: test for path in afs before symlink test
    2010-12-07 Marc Dionne      (3298) Lockless path through afs_linux_dentry_revalidate
    2010-12-07 Andrew Deason    (3465) RX: Always define kernel XDR symbols to be AFS XDR
    2010-12-07 Andrew Deason    (3368) Remove unreached lines
    2010-12-07 Andrew Deason    (3466) vol_split: Recover from stream open failure
    2010-12-07 Andrew Deason    (3464) tubik: Link with libafsauthent
    2010-12-07 Andrew Deason    (3463) roken: Export rk_daemon, not daemon
    2010-12-06 Andrew Deason    (3462) SOLARIS: Fix some rx_atomic.h warnings
    2010-12-06 Andrew Deason    (2548) libafs: Set tvcp->callback before BulkStatus
    2010-12-06 Derrick Brashear (3448) linux: avoid leaking parent when revalidating and it is /afs
    2010-12-05 Jeffrey Altman   (3440) Windows: build a UNICODE version of talocale.lib
    2010-12-05 Jeffrey Altman   (3446) Windows: fix checked UNICODE build of talocale
    2010-12-05 Jeffrey Altman   (3442) Windows: Build afs_shl_ext.dll with talocaleU.lib
    2010-12-05 Jeffrey Altman   (3441) Windows: install afs_shl_ext icon files
    2010-12-05 Jeffrey Altman   (3445) Windows: afs_shl_ext improve overlay handlers
    2010-12-05 Jeffrey Altman   (3444) Windows: afs_shl_ext Show icon mount point overlay
    2010-12-05 Jeffrey Altman   (3443) Windows: afs_shl_ext folder bkgrnd context menu
    2010-12-05 Jeffrey Altman   (3439) Windows: fix UNICODE build for talocale
    2010-12-04 Jeffrey Altman   (3419) Windows: Remove fallback from GetCaps to GetTime
    2010-12-04 Christof Hanke   (3435) Add .gitignore for tsm41
    2010-12-04 Andrew Deason    (3432) LINUX: Define zero_user_segment
    2010-12-03 Antoine Verheijen (3430) OpenBSD: Remove duplicate assignment of COMMON_INCLUDE in libafs
    2010-12-03 Antoine Verheijen (3429) Move include of sys/types.h in kopenafs.c
    2010-12-02 Derrick Brashear (3407) properly mark servers down for rx errors except OPCODE
    2010-12-02 Matt Benjamin    (2216) unix cm  rx-oblivious connection pooling
    2010-12-02 Derrick Brashear (3423) balance afs_vcount in non-linux CM
    2010-12-02 Derrick Brashear (3424) freebsd: properly track vcache references
    2010-12-02 Michael Meffie   (3421) Import of code from heimdal
    2010-12-02 Derrick Brashear (3420) osconf quoting for macros
    2010-12-02 Derrick Brashear (3408) configure: add lresolv to MT_LIBS
    2010-12-02 Antoine Verheijen (3418) OpenBSD: Fix variable name typo in osi_vcache.c
    2010-12-02 Antoine Verheijen (3417) OpenBSD: Fix use of mstat Length field in osi_vm.c
    2010-12-02 Antoine Verheijen (3405) OpenBSD: Use Darwin version of afsi_SetServerIPRank() for OpenBSD 4.7 and above.
    2010-12-01 Antoine Verheijen (3402) Darwin: Assign correct value to myDstaddr in afsi_SetServerIPRank()
    2010-12-01 Antoine Verheijen (3401) DARWIN: Fix processing using rx_ifaddr_* macros in afsi_SetServerIPRank()
    2010-12-01 Simon Wilkinson  (3397) Import of code from heimdal
    2010-12-01 Benjamin Kaduk   (3391) FBSD: clean up rx_socket teardown
    2010-12-01 Simon Wilkinson  (3400) Import of code from heimdal
    2010-12-01 Simon Wilkinson  (3399) util: Add definition of KRB5_BUFSIZ
    2010-12-01 Simon Wilkinson  (3398) Build and use roken's mkstemp
    2010-12-01 Simon Wilkinson  (3396) Import mkstemp.c from libroken

### Patches merged into the stable 1.4.x branch

    Date       Committer       Change# Description
    2010-12-23 Andrew Deason    (3587) SOLARIS: Free vcache mappings on shutdown
    2010-12-23 Andrew Deason    (3586) UINT_MAX requires limits.h
    2010-12-23 Andrew Deason    (3585) rxkad heimdal cleanup
    2010-12-22 Andrew Deason    (3574) vos status: actually show created time
    2010-12-22 Andrew Deason    (3572) vol: Log ignored dirs that look like partitions
    2010-12-22 Christof Hanke   (3541) Honour --enable-debug for userspace parts
    2010-12-22 Andrew Deason    (3573) vos: Mark longjmp-used variables as 'volatile'
    2010-12-16 Derrick Brashear (3534) LINUX: Use correct type of error in flock code
    2010-12-15 Marc Dionne      (3529) Linux 2.4: Restore missing unlock_kernel()
    2010-12-14 Derrick Brashear (3523) update ticket5 from heimdal
    2010-12-14 Marc Dionne      (3512) Linux: define llseek operations
    2010-12-13 Jeffrey Altman   (3505) CellServDB update 13 Dec 2010
    2010-12-07 Antoine Verheijen (3426) OpenBSD: Add ifaddr_* macros to osi_machdep.h
    2010-12-07 Antoine Verheijen (3478) OpenBSD: Use Darwin version of afsi_SetServerIPRank() for OpenBSD 4.7 and above.
    2010-12-07 Antoine Verheijen (3474) Darwin: Assign correct value to myDstaddr in afsi_SetServerIPRank()
    2010-12-07 Antoine Verheijen (3473) DARWIN: Fix processing using ifaddr_* macros in afsi_SetServerIPRank()
