---
title: OpenAFS Newsletter, Volume 2, Issue 12, December 2010
---

# OpenAFS Newsletter, Volume 2, Issue 12, December 2010

Welcome to the December issue of the OpenAFS newsletter. This newsletter
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

Work on the 1.6.x stable branch continues. The first release candidate for
the 1.6.x series is expected this month.

One of the AFS3 group chairs issued a call for consensus on the
draft-brashear-afs3-pts-extended-names draft, which will last until
December 16.

Some updates for OpenBSD 4.7 were merged into 1.4.x stable branch.

## Events

### BoF at LISA 2010

I forgot to send an email to report on how the BoF went.  I was pleased by
the turnout - we had probably 20-25 people there, most of whom do not use
AFS currently but were looking at possible distributed file systems.  The
bulk of the session was taken up by me and a few other AFS admins who were
there talking about AFS, how it works, and answering questions people had
about it and what it could do.  Hopefully we got some new converts! :)

\--Brian Sebby

## AFS Protocol Standardization

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://lists.openafs.org/mailman/listinfo/afs3-standardization](http://lists.openafs.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names)

Status: Eighth Draft (07) - Call for Consensus

Last update: November 29, 2010

Just pushed -07. I hope to ask the chairs to call for consensus soon.

\-07, contains some typographical fixes and minor rewording based on
suggestions from Steve Simmons.

\--Derrick

Douglas Engert issued a call for consensus. The call for consensus will
last until December 16.

\--Ed.

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

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

The man pages were updated to discourage the use of the uss command. The
HTML generation scripts were updated to ignore ".pod.in" files and other
stuff that should be ignored. Some minor POD syntax errors were fixed in
the fileserver man page.

Jeffrey Altman added some code so that the Admin and User Guides show the
AFS version in the revision history.

\--Jason

### Google Summer of Code 2010

OpenAFS received five slots for the 2010 Google Summer of Code.

Go to [http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs](http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs)
for more information about the GSoC projects.

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

No Progress.

\[ Stuff left to do: \] To get back to a state where it's compilable: Debug
the merged Heimdal code & figure out why/how that broke it After: Creation
of contents of /afs and testing/debugging of functionality for files

\--Matt Smith

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Extended Callback Information - January 2010
- Mac OS X OpenAFS Preference Pane - April 2010
- S3 Front-end for AFS - July 2010
- User-space cache manager - July 2010 (1.6 still not released yet)
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
    2010-12   64 (Partial month)
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
    2009-11   85

    Patches merged into the stable 1.4.x branch:
    Month   Number of Commits
    2010-12   7 (Partial month)
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
    2009-11  21

### Patches merged into the master branch

    Date       Committer       Change# Description
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
    2010-11-30 Jeffrey Altman   (3393) Windows: permit code signing without timestamps
    2010-11-29 Christof Hanke   (3392) Unix afsd: Check for mountpoint /afs first
    2010-11-29 Marc Dionne      (3375) Cache bypass: switch to rx_Readv
    2010-11-28 Steve Simmons    (2633) More deprecations noted.
    2010-11-28 Derrick Brashear (3315) external import script should rebase away whitespace
    2010-11-27 Simon Wilkinson  (3212) .gitignore update
    2010-11-27 Andrew Deason    (2726) vos: Improve release recovery on timed-out trans
    2010-11-27 Derrick Brashear (3150) ubik sync client error recovery
    2010-11-27 Jeffrey Altman   (3388) Windows: NSIS installer requires the architecture for CL=1400
    2010-11-27 Jeffrey Altman   (3387) Windows: make use of AFSDEV_BIN and set the PATH
    2010-11-27 Christof Hanke   (3345) check curses-libs by configure
    2010-11-27 Christof Hanke   (1970) Add output-table to libafsutil
    2010-11-27 Benjamin Kaduk   (3390) Fix FBSD build after warning cleanups
    2010-11-27 Benjamin Kaduk   (3389) Catch up on FBSD releases
    2010-11-25 Benjamin Kaduk   (3200) FBSD: warning cleanups
    2010-11-25 Andrew Deason    (3367) Utilize --enable-warnings for SUNWspro
    2010-11-25 Andrew Deason    (3366) Only specify CFLAGS_NO* with --enable-checking
    2010-11-25 Andrew Deason    (3365) Solaris: Support -i in shlib-build
    2010-11-25 Andrew Deason    (3364) afsd: Remove unused definitions
    2010-11-25 Andrew Deason    (3363) vol: Move VOL_CV_TIMEDWAIT to volume_inline.h
    2010-11-25 Benjamin Kaduk   (3376) Fix build for archs with -lcrypt
    2010-11-25 Andrew Deason    (3362) FUSE: Link to afshcrypto and crypt
    2010-11-25 Chaz Chandler    (3386) Add explicit libafsauthent dependency for aklog
    2010-11-25 Simon Wilkinson  (3356) aklog: Build a pthreaded, rather than lwp, version
    2010-11-25 Derrick Brashear (3209) aklog weak warning
    2010-11-25 Andrew Deason    (3385) ubik: Log a message when we replay the trans log
    2010-11-25 Andrew Deason    (3384) ubik: Replay the transaction log label correctly
    2010-11-25 Simon Wilkinson  (3355) auth: Allow identities in the UserList
    2010-11-25 Marc Dionne      (3374) Cache bypass: Only compile bypass code for the Linux kernel
    2010-11-25 Marc Dionne      (3373) Cache bypass: remove ifdefs under src/afs/LINUX
    2010-11-25 Marc Dionne      (3372) Cache bypass: Remove AFS_KMAP_ATOMIC
    2010-11-24 Jeffrey Altman   (3383) rx: add rx_opaque and rx_identity exports
    2010-11-24 Simon Wilkinson  (3382) Import of code from heimdal
    2010-11-24 Simon Wilkinson  (3381) Import of code from heimdal
    2010-11-24 Jeffrey Altman   (3324) Windows: build src/rx/tests
    2010-11-24 Steve Simmons    (2637) Update the man pages pod source adding text to discourage use of uss.  Usually the text added was a copy of a CAUTION section that had already been added in a few places. This change applies it consistently across all uss-related man pages. In pod1/afs.po
    2010-11-24 Jeffrey Altman   (3380) Windows: indicate that roken is a dynamic library for roken.h
    2010-11-24 Jeffrey Altman   (3377) Windows: roken getopt renamed to rk_getopt, vars exported
    2010-11-24 Simon Wilkinson  (3379) Import of code from heimdal
    2010-11-24 Simon Wilkinson  (3378) Import of code from heimdal
    2010-11-24 Jeffrey Altman   (3330) roken: modify build configuration to permit Windows to work
    2010-11-24 Jeffrey Altman   (3361) rxkad: rename bswap32 to octetswap32
    2010-11-24 Jeffrey Altman   (3350) rxkad: fix bg-fcrypt to work with roken
    2010-11-24 Simon Wilkinson  (3371) roken: Add the strsep function
    2010-11-24 Simon Wilkinson  (3370) Import of code from heimdal
    2010-11-24 Simon Wilkinson  (3369) Imports: Import heimdal:lib/roken/strsep.c
    2010-11-24 Simon Wilkinson  (3354) roken: Add base64 functions to libroken
    2010-11-24 Simon Wilkinson  (3353) rx: Store identity type in rx_identity_new
    2010-11-24 Simon Wilkinson  (3352) rx: Rework identity copying
    2010-11-23 Benjamin Kaduk   (3275) FBSD: close race in afs_root
    2010-11-23 Simon Wilkinson  (3360) Import of code from heimdal
    2010-11-22 Derrick Brashear (3357) redhat init script fix missing space
    2010-11-22 Simon Wilkinson  (3351) userok: Allow NULL components in kerberosSuperUser
    2010-11-22 Jeffrey Altman   (3349) Windows: update nsis installer for hcrypto and roken
    2010-11-22 Jeffrey Altman   (3348) Windows: update wix installer for afsroken.dll
    2010-11-22 Christof Hanke   (3343) use intptr_t instead of ifdef
    2010-11-21 Christof Hanke   (3344) use computed values in src/gtx/curseswindows.c
    2010-11-21 Simon Wilkinson  (3334) Imports: Add reporting of new and removed files
    2010-11-21 Simon Wilkinson  (3218) hcrypto: Cleanup all build products
    2010-11-21 Christof Hanke   (3341) use proper 64bit casting for pointer-math
    2010-11-21 Christof Hanke   (3342) remove unnecessary dependency
    2010-11-20 Jeffrey Altman   (3338) add src/roken/roken.h to src/roken/.gitignore
    2010-11-20 Jeffrey Altman   (3337) Windows: permit aklog to build with krb4 support and roken
    2010-11-20 Jeffrey Altman   (3336) Windows: Have get/free addrinfo and nameinfo functions
    2010-11-20 Jeffrey Altman   (3333) Windows: Add hcrypto to the msi installer
    2010-11-20 Jeffrey Altman   (3335) Windows: more libroken fixes
    2010-11-20 Jeffrey Altman   (3331) Windows: conditionally set tray icon state
    2010-11-20 Jeffrey Altman   (3323) more rx/tests cleanups
    2010-11-19 Felix Frank      (3305) rxgen: add *TranslateOpcode functions to XDR code
    2010-11-19 Andrew Deason    (3302) doc: Do not process .in files for html
    2010-11-19 Simon Wilkinson  (2578) Use hcrypto for kernel md5
    2010-11-19 Simon Wilkinson  (2577) Remove local crypto
    2010-11-19 Marc Dionne      (3292) Linux: define llseek operations
    2010-11-19 Simon Wilkinson  (3211) Replace bits of libutil with libroken
    2010-11-19 Simon Wilkinson  (3206) hcrypto: Use system wide libroken
    2010-11-19 Simon Wilkinson  (3210) Build: Fix broken bracketing in shared Makefile
    2010-11-19 Jeffrey Altman   (3328) Windows: build tsalvaged on Windows
    2010-11-19 Jeffrey Altman   (3327) Windows: build tptserver on Windows
    2010-11-19 Jeffrey Altman   (3326) Windows: build tubik
    2010-11-18 Jeffrey Altman   (3325) Windows: add roken.h to src/roken cleanup list
    2010-11-18 Jeffrey Altman   (3322) Windows: Add CODESIGN_OTHER option to make signtool rules
    2010-11-18 Jeffrey Altman   (3309) volser: remove unused yesprompt function
    2010-11-18 Jeffrey Altman   (2089) Convert from using nvldbentry to uvldbentry
    2010-11-17 Simon Wilkinson  (3205) libroken: Build on windows
    2010-11-17 Simon Wilkinson  (3320) Add snprintf to roken for Unix builds
    2010-11-17 Derrick Brashear (3316) roken build vsyslog
    2010-11-16 Derrick Brashear (3311) Import of code from heimdal
    2010-11-16 Andrew Deason    (3289) Use afs_foff_t for file offsets
    2010-11-16 Derrick Brashear (3310) import vsyslog from roken for AIX
    2010-11-15 Anders Kaseorg   (3278) Linux: Fix prototypes for afs_xsetgroups and sys_setgroupsp and friends
    2010-11-15 Hartmut Reuter   (3013) RXOSD and VICEP-ACCESS fields and bits in afs.h
    2010-11-15 Anders Kaseorg   (3277) Linux: Fix prototypes for sys_setgroups_stub and sys32_setgroups_stub
    2010-11-15 Andrew Deason    (2647) ubik: Record the last write tid in writeTidCounter
    2010-11-15 Derrick Brashear (3297) avoid requeueing callbacks during shutdown
    2010-11-15 Andrew Deason    (3291) afscp: Add -s option
    2010-11-15 Andrew Deason    (2984) viced: Add options for interrupting clients
    2010-11-15 Andrew Deason    (3216) vol: Interrupt RX calls accessing offlining vols
    2010-11-15 Andrew Deason    (3215) vol: Add interfaces for registering RX calls
    2010-11-15 Andrew Deason    (3214) vol: Add VGetVolumeTimed
    2010-11-14 Jeffrey Altman   (3304) Windows: ktc_ListTokensEx stub assignment error
    2010-11-14 Jeffrey Altman   (3303) Windows: clean token.h/token.xdr.c from src/auth
    2010-11-12 Andrew Deason    (2873) viced: Allow checkout of VOL_STATE_DELETED volumes
    2010-11-12 Andrew Deason    (3301) doc: Fix fileserver synopsis
    2010-11-12 Hartmut Reuter   (3293) Use port in ugen_ClientInit
    2010-11-12 Andrew Deason    (3290) afscp: Always show fetch/store errors
    2010-11-12 Andrew Deason    (3296) vos release: Avoid full dump on all sites
    2010-11-11 Andrew Deason    (2484) Fix util test dependencies
    2010-11-11 Michael Meffie   (3294) viced: fix missing host lock in h_Enumerate
    2010-11-11 Andrew Deason    (2865) salvager: Do not break cbks when salvaging parts
    2010-11-09 Tom Keiser       (2979) vol: make namei_ListAFSSubDirs deal with multiple/bad linktables
    2010-11-09 Alejandro R. Sedeno (3273) Linux: use DEFINE_MUTEX for afs_linux_alloc_sem on newer kernels
    2010-11-08 Marc Dionne      (3281) Cache bypass: make readpage deal with reads at end of file
    2010-11-08 Andrew Deason    (2872) volser: Do not FSYNC_VOL_DONE temporary volumes
    2010-11-08 Jeffrey Altman   (3285) rxperf: use parallel connections
    2010-11-08 Marc Dionne      (3282) Cache bypass: adjust read size for non-contiguous readpages
    2010-11-08 Jeffrey Altman   (3279) RX: rxi_PrepareSendPacket drops call lock; WaitforTQ required
    2010-11-08 Andrew Deason    (3274) vol: Do not give back not-checked-out vols
    2010-11-08 Marc Dionne      (3283) Cache bypass: release and unlock pages when we get 0-length reply
    2010-11-06 Simon Wilkinson  (3160) rx: Reorganise includes
    2010-11-06 Michael Meffie   (3268) Windows: fix keystroke delay in waitkey
    2010-11-06 Michael Meffie   (3257) avoid private stdio fields in waitkey
    2010-11-05 Andrew Deason    (3272) DAFS: Do not let VScheduleSalvage_r free vp
    2010-11-05 Derrick Brashear (3180) merge ntops and namei
    2010-11-05 Derrick Brashear (3270) RedHat:  Remove potpourri.h from RedHat SPEC file manifest
    2010-11-05 Marc Dionne      (3266) Cache bypass: Fix oops in bypass transition functions
    2010-11-04 Andrew Deason    (3263) RX: Fix old rx_stats incrementors
    2010-11-04 Andrew Deason    (3262) krb5_free_string takes a krb5_context
    2010-11-04 Andrew Deason    (3261) tsm: Make explicit rules for stem-changing targets
    2010-11-04 Andrew Deason    (3260) UKERNEL: f_fsid is a struct on AIX
    2010-11-04 Andrew Deason    (3259) afsd: Pass cacheMountDir to aix_vmount
    2010-11-04 Andrew Deason    (3258) Use termios.h for winsize test where available
    2010-11-04 Marc Dionne      (3244) volser: add missing Makefile dependencies
    2010-11-03 Marc Dionne      (3245) Linux: 2.6.37 - replace get_sb with mount
    2010-11-03 Hartmut Reuter   (2952) Make osi_fetchstore.c protocol independent
    2010-11-03 Rod Widdowson    (3187) Docs: Specify where the Windows mini dump file is written
    2010-11-03 Derrick Brashear (3219) rx mutex inversion fix
    2010-11-03 Jeffrey Altman   (3220) Windows: Do not leak cm_volume_t objects from the LRU queue
    2010-11-02 Jeffrey Altman   (3177) vol: attach2 must always return with VOL_LOCK held
    2010-11-02 Chas Williams - CONTRACTOR (3207) afs: minor cleanup for LINUX struct vcache
    2010-11-02 Andrew Deason    (2329) DAFS: Fix demand-salvages of attached volumes
    2010-11-02 Andrew Deason    (3213) Cleanup VOffline log message for non-DAFS
    2010-11-02 Andrew Deason    (3217) QSG: DAFS uses dasalvager
    2010-11-01 Derrick Brashear (3208) check for error_message
    2010-11-01 Derrick Brashear (3194) kill off afs/debug.h
    2010-11-01 Simon Wilkinson  (3191) Add libroken as its own library

### Patches merged into the stable 1.4.x branch

    Date       Committer       Change# Description
    2010-12-14 Derrick Brashear (3523) update ticket5 from heimdal
    2010-12-14 Marc Dionne      (3512) Linux: define llseek operations
    2010-12-13 Jeffrey Altman   (3505) CellServDB update 13 Dec 2010
    2010-12-07 Antoine Verheijen (3426) OpenBSD: Add ifaddr_* macros to osi_machdep.h
    2010-12-07 Antoine Verheijen (3478) OpenBSD: Use Darwin version of afsi_SetServerIPRank() for OpenBSD 4.7 and above.
    2010-12-07 Antoine Verheijen (3474) Darwin: Assign correct value to myDstaddr in afsi_SetServerIPRank()
    2010-12-07 Antoine Verheijen (3473) DARWIN: Fix processing using ifaddr_* macros in afsi_SetServerIPRank()
    2010-11-22 Derrick Brashear (3358) redhat init script fix missing space
    2010-11-21 Derrick Brashear (3340) RX: Force sane timeout values
    2010-11-21 Derrick Brashear (3339) RX: Adjust all timeouts for RTT
    2010-11-17 Derrick Brashear (3318) RPM scripts should allow newbinary restart to restart
    2010-11-16 Marc Dionne      (3313) Linux: fix statfs configure test
    2010-11-15 Anders Kaseorg   (3308) Linux: Fix prototypes for afs_xsetgroups and sys_setgroupsp and friends
    2010-11-15 Anders Kaseorg   (3307) Linux: Fix prototypes for sys_setgroups_stub and sys32_setgroups_stub
    2010-11-15 Alejandro R. Sedeno (3288) Linux: use DEFINE_MUTEX for afs_linux_alloc_sem on newer kernels
    2010-11-15 Derrick Brashear (3286) Do not call afs_FlushVCBs with afs_xvcache held
