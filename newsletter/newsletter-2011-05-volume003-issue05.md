---
title: OpenAFS Newsletter, Volume 3, Issue 5, May 2011
---

# OpenAFS Newsletter, Volume 3, Issue 5, May 2011

Welcome to the May issue of the OpenAFS newsletter. This newsletter
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

The release of 1.6.0 is waiting on some more bug fixes. Some tests were
added for the command library. Representatives of the AFS3-standardization
group are working with the IETF on how to publish standards documents
going forward.

## Events

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

Status: Second draft - Waiting on RPC refresh

Last Update: April 26, 2011

The primary differences from previous drafts are an updated vector result
argument from proc ExtendedCallBack, and in semantic discussions, which
are simplified and reflect discussion at the 2011 OpenAFS hackathon.

Extended callback extensions were discussed at the 2011 Hackathon.  A
revised draft of the specification was published, with interface cleanups,
extensions for byte-range locking support, and referencing data types from
the RPC refresh effort.  Extension and integration work to support
byte-range locking support is made possible by Your File System, Inc, and
is available at https://github.com/your-file-system/openafs-rxgk (branch
advlock\_6\_2).

\--Matt

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

Status: Seventh Draft

Last Update: April 27, 2011

Differences from previous drafts include:

- minor updates to rx grammar, esp. AssertExtendLock
- discussion of callback channel security considerations, and
- specification of supported polling mechanism and expiration hints
- cleanups

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

A new man page was created for aklog\_dynamic\_auth, which is a loadable
authentication module for AIX.

### \*BSD Support

Project Contacts:

- Ben Kaduk <kaduk@mit.edu>

NetBSD support has caught up to where FreeBSD is. The memcache is usable,
but a disk cache still has vnode-locking issues. In addition, the FreeBSD
cache manager is usable only under moderate load. Weird issues persist
when doing weird things. Oftentimes, it doesn't shutdown cleanly, but
panics have been rare.

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
- S3 Front-end for AFS

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Patches merged into the master branch:
    Month   Number of Commits
    2011-05   32 (Partial month)
    2011-04  171
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
    2011-05   26 (Partial month)
    2011-04   21
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
    2011-05    3 (Partial month)
    2011-04    0
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

### Patches merged into the master branch

    Date       Committer        Change# Description
    2011-05-17 Ken Dreyer        (4670) doc: -afsdb uses SRV records
    2011-05-16 Andrew Deason     (4669) viced: Don't VTakeOffline_r without glock
    2011-05-16 Andrew Deason     (4668) viced: Check vnode length on Rename and Link
    2011-05-15 Andrew Deason     (4485) doc: Add aklog_dynamic_auth manpage
    2011-05-15 Andrew Deason     (4646) viced: Enable NAT ping on hosts
    2011-05-15 Andrew Deason     (4645) viced: h_SetupCallbackConn_r in removeAddress_r
    2011-05-15 Andrew Deason     (4638) dasalvager: unlink fsstate.dat when standalone
    2011-05-15 Simon Wilkinson   (4653) cmd tests: Initialise string retval
    2011-05-15 Andrew Deason     (4641) libafs: Flush vcaches in afs_shutdown
    2011-05-15 Andrew Deason     (4640) libafs: GiveUpAllCallBacks at shutdown again
    2011-05-15 Andrew Deason     (4639) libafs: Do not write-lock afs_xserver on ICBS
    2011-05-15 Russ Allbery      (4657) Fix misspelling of writable as writeable
    2011-05-15 Marc Dionne       (4656) Linux: fix reading files larger than the chunk size
    2011-05-14 Andy Cobaugh      (4643) rpm: Really undefine %dist
    2011-05-14 Marc Dionne       (4654) Linux: fix permission op test for certain compilers
    2011-05-12 Derrick Brashear  (4644) afscp: tellmeaboutyourself stub wants host byte order
    2011-05-09 Jeffrey Altman    (4633) Windows: always try afs/cell@USER-REALM first
    2011-05-09 Jeffrey Altman    (4632) Windows: support dotted names in aklog
    2011-05-09 Andrew Deason     (4626) libafs: Put back GetCapabilities user reference
    2011-05-09 Andrew Deason     (4625) libafs: Get rx conn ref with afs conn ref
    2011-05-06 Jeffrey Altman    (4629) Windows: replace CYGWIN envvar with CYGWINDIR
    2011-05-06 Jeffrey Altman    (4627) Windows: change log for 1.5.9905
    2011-05-05 Andrew Deason     (4624) libafs: Correct afs_LoopServers flags
    2011-05-05 Jeffrey Altman    (4623) vol: switch to rk_closesocket
    2011-05-05 Jeffrey Altman    (4620) afscp: use closesocket when closing sockets
    2011-05-03 Russ Allbery      (4607) Further fix gssapi.m4 for Heimdal without libroken
    2011-05-03 Jonathan A. Kollasch (4605) NetBSD: DEBUG can not typically be defined
    2011-05-03 Jonathan A. Kollasch (4604) NetBSD: translate timeval structure format in clock_GetTime()
    2011-05-02 Andrew Deason     (4583) viced: Improve deleted client log messages
    2011-05-02 Andrew Deason     (4582) viced: Do not try to reuse deleted client
    2011-05-02 Jonathan A. Kollasch (4599) Remove unused variable
    2011-05-02 Jeffrey Altman    (4597) Windows: Fix caching of non-existing vols
    2011-04-30 Andrew Deason     (4590) Add missing LIB_roken references
    2011-04-29 Derrick Brashear  (4595) avoid downward vcache pressure when entries are free
    2011-04-29 Andrew Deason     (3958) libafs: Drop xvcache for AllocCBR
    2011-04-29 Andrew Deason     (4584) libafs: Use vcount, not maxvcount to trim vcaches
    2011-04-29 Russ Allbery      (4594) Fix various build problems with the test suite
    2011-04-29 Russ Allbery      (4589) Resync test harness with C TAP Harness 1.7
    2011-04-28 Russ Allbery      (4588) Resync Autoconf macros from rra-c-util 3.3
    2011-04-28 Russ Allbery      (4587) Resync src/cf/gssapi.m4 with rra-c-util 3.3 (fixes OpenBSD)
    2011-04-28 Andrew Deason     (4586) doc: Fix 'vos endtrans' copyright
    2011-04-28 Andrew Deason     (4581) viced: Avoid ref leak on origin callback break
    2011-04-28 Andrew Deason     (4580) viced: Transfer host ref in h_FindClient_r
    2011-04-27 Derrick Brashear  (4561) IRIX: set vfs pointer when creating new vcaches
    2011-04-27 Simon Wilkinson   (4547) cmd: Support splitting switches and values with '='
    2011-04-27 Simon Wilkinson   (4546) cmd: Tidy up -help output
    2011-04-27 Simon Wilkinson   (4545) cmd: Add support for params with optional values
    2011-04-27 Simon Wilkinson   (4544) cmd: Add parameter aliasing
    2011-04-27 Simon Wilkinson   (4543) cmd: Add accessor functions for options
    2011-04-27 Simon Wilkinson   (4542) cmd: Add option to add a param at a specific pos
    2011-04-27 Thomas L. Kula    (3899) Add -usetokens option to libadmin test 'afscp'
    2011-04-27 Simon Wilkinson   (4562) Linux: Don't read pages beyond the cache eof
    2011-04-27 Andrew Deason     (4577) Build libafscp when we lack kerberos
    2011-04-27 Simon Wilkinson   (4575) Irix: Add a simple osi_ReadRandom implementation
    2011-04-27 Marc Dionne       (4491) src/afs: Set but unused variables warning fixes
    2011-04-27 Andrew Deason     (4576) Fix --without-krb5
    2011-04-27 Simon Wilkinson   (4574) Rewrite asetkey to support extended key types
    2011-04-27 Chaz Chandler     (4578) afsio: remove unnecessary reference to malloc.h
    2011-04-27 Marc Dionne       (4526) ubik: add uvote_HaveSyncAndVersion
    2011-04-27 Derrick Brashear  (4569) macos: further next version support
    2011-04-27 Marc Dionne       (4525) ubik: Defer updateUbikNetworkAddress until after RX startup
    2011-04-27 Marc Dionne       (4524) ubik: locking in recovery.c
    2011-04-27 Marc Dionne       (4490) ubik: always hold DB lock for urecovery_ResetState()
    2011-04-27 Marc Dionne       (4489) ubik: set UBIK_RECLABELDB before propagating version
    2011-04-27 Marc Dionne       (4488) ubik: remote: fix DB lock usage
    2011-04-26 Benjamin Kaduk    (3547) Rename libcom_err to libafscom_err
    2011-04-26 Andrew Deason     (4553) pam: Password is const in setcred
    2011-04-26 Marc Dionne       (4563) Linux: cleanup aio support
    2011-04-26 Simon Wilkinson   (4541) cmd: Split up dispatch function
    2011-04-26 Simon Wilkinson   (4540) cmd: Add an option to disable abbreviations
    2011-04-26 Simon Wilkinson   (4539) cmd: Add function to disable positional commands
    2011-04-26 Simon Wilkinson   (4538) cmd: Add some tests to the test suite
    2011-04-26 Andrew Deason     (4554) pam: Fix password torching const-ness
    2011-04-26 Simon Wilkinson   (4537) cmd: Make the original test suite build
    2011-04-26 Jeffrey Altman    (4560) Windows: afskfw return error if krb5 not loaded
    2011-04-26 Jeffrey Altman    (4559) Windows: build afskfw.c without leashw32.dll
    2011-04-26 Jeffrey Altman    (4558) Windows: avoid preprocessor symbols redefinitions
    2011-04-26 Jeffrey Altman    (4557) Windows: NPLogonNotify provide password in all cases
    2011-04-26 Jeffrey Altman    (4556) windows: improved logging from NPLogonNotify
    2011-04-26 Simon Wilkinson   (4536) cmd: Cleanup
    2011-04-26 Marc Dionne       (4487) pam: Clear up PAM_CONST related warnings on Linux
    2011-04-25 Andrew Deason     (4530) viced: Release all hosts in h_Enumerate*
    2011-04-25 Simon Wilkinson   (4510) Linux: Restrict # of cbrs we allocate at once
    2011-04-25 Andrew Deason     (4529) viced: Print a warning when using a deleted client
    2011-04-25 Andrew Deason     (4528) viced: Force valid host enumeration flags
    2011-04-25 Andrew Deason     (4527) viced: Fix host enumeration flags
    2011-04-25 Jeffrey Altman    (4548) Windows: remove trailing whitespace
    2011-04-25 Simon Wilkinson   (4535) autoconf: Add required headers to net/if.h test
    2011-04-25 Simon Wilkinson   (4550) Windows: Remove duplicate file
    2011-04-24 Jonathan A. Kollasch (4509) Fix build of user-space on nbsd50 and greater
    2011-04-22 Jonathan A. Kollasch (4512) Add nbsd60 param files and autoconf logic
    2011-04-22 Andrew Deason     (4521) libafs: Initialize _settok_tokenCell primary flag
    2011-04-22 Andrew Deason     (4519) Revert "aklog: Return token when performing 524 conversion"
    2011-04-22 Jeffrey Altman    (4501) Windows: change thyper to offset and fix error
    2011-04-21 Andrew Deason     (4513) aklog: Return token when performing 524 conversion
    2011-04-21 Derrick Brashear  (4511) Darwin CM: afs_IsDynrootFid takes a fid ...
    2011-04-21 Derrick Brashear  (4508) afsio: fix objdir build
    2011-04-21 Marc Dionne       (4504) Unused variable warning fixes
    2011-04-21 Jonathan A. Kollasch (4506) Allocate system type ID numbers for i386_nbsd60 and amd64_nbsd60
    2011-04-21 Jonathan A. Kollasch (4505) Make whitespace consistent in NetBSD system type ID number section
    2011-04-20 Jeffrey Altman    (4498) Windows: avoid race when writing mountPointString
    2011-04-20 Marc Dionne       (4497) adminutil: parallel build fixes
    2011-04-20 Derrick Brashear  (4476) libafscp: add lock support
    2011-04-20 Simon Wilkinson   (4494) make afsdump_scan get ACLs right
    2011-04-20 Simon Wilkinson   (4495) FreeBSD: Don't ignore Makefile
    2011-04-18 Derrick Brashear  (4492) roken header dependencies mean we need roken
    2011-04-18 Andrew Deason     (4480) auth: Set correct flags in token_extractRxkad
    2011-04-17 Derrick Brashear  (4475) libafscp: fix kerberos bits
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

### Patches merged into the stable 1.6.x branch

    Date       Committer        Change# Description
    2011-05-17 Derrick Brashear  (4665) rpm: Really undefine %dist
    2011-05-17 Derrick Brashear  (4664) Linux: fix reading files larger than the chunk size
    2011-05-17 Derrick Brashear  (4663) libafs: Do not write-lock afs_xserver on ICBS
    2011-05-17 Derrick Brashear  (4662) dasalvager: unlink fsstate.dat when standalone
    2011-05-15 Andrew Deason     (4637) libafs: Put back GetCapabilities user reference
    2011-05-15 Marc Dionne       (4655) Linux: fix permission op test for certain compilers
    2011-05-10 Jeffrey Altman    (4635) Windows: always try afs/cell@USER-REALM first
    2011-05-10 Jeffrey Altman    (4634) Windows: support dotted names in aklog
    2011-05-06 Jeffrey Altman    (4630) Windows: replace CYGWIN envvar with CYGWINDIR
    2011-05-06 Jeffrey Altman    (4628) Windows: change log for 1.5.9905
    2011-05-03 Derrick Brashear  (4618) make 1.6.0pre5
    2011-05-03 Derrick Brashear  (4617) NetBSD: DEBUG can not typically be defined
    2011-05-03 Derrick Brashear  (4616) NetBSD: translate timeval structure format in clock_GetTime()
    2011-05-03 Derrick Brashear  (4615) avoid downward vcache pressure when entries are free
    2011-05-03 Simon Wilkinson   (4614) Fix com_err renaming
    2011-05-03 Andrew Deason     (4592) viced: Avoid ref leak on origin callback break
    2011-05-03 Andrew Deason     (4593) viced: Improve deleted client log messages
    2011-05-03 Andrew Deason     (4591) viced: Transfer host ref in h_FindClient_r
    2011-05-03 Derrick Brashear  (4603) libafs: Drop xvcache for AllocCBR
    2011-05-03 Derrick Brashear  (4602) libafs: Use vcount, not maxvcount to trim vcaches
    2011-05-03 Derrick Brashear  (4600) Linux: Don't read pages beyond the cache eof
    2011-05-03 Andrew Deason     (4534) viced: Release all hosts in h_Enumerate*
    2011-05-03 Andrew Deason     (4533) viced: Print a warning when using a deleted client
    2011-05-03 Andrew Deason     (4532) viced: Force valid host enumeration flags
    2011-05-02 Derrick Brashear  (4601) doc: Fix 'vos endtrans' copyright
    2011-05-02 Jeffrey Altman    (4598) Windows: Fix caching of non-existing vols
    2011-04-29 Derrick Brashear  (4572) Rename libcom_err to libafscom_err
    2011-04-28 Derrick Brashear  (4571) macos: further next version support
    2011-04-27 Derrick Brashear  (4579) IRIX: set vfs pointer when creating new vcaches
    2011-04-27 Marc Dionne       (4570) Linux: Fix fallout from path_lookup commit
    2011-04-26 Andrew Deason     (4531) viced: Fix host enumeration flags
    2011-04-26 Jeffrey Altman    (4568) Windows: afskfw return error if krb5 not loaded
    2011-04-26 Jeffrey Altman    (4567) Windows: build afskfw.c without leashw32.dll
    2011-04-26 Jeffrey Altman    (4566) Windows: avoid preprocessor symbols redefinitions
    2011-04-26 Jeffrey Altman    (4565) Windows: NPLogonNotify provide password in all cases
    2011-04-26 Jeffrey Altman    (4564) windows: improved logging from NPLogonNotify
    2011-04-26 Andrew Deason     (4503) AIX51: Fix PAGs
    2011-04-26 Derrick Brashear  (4555) Linux: Restrict # of cbrs we allocate at once
    2011-04-25 Jeffrey Altman    (4549) Windows: remove trailing whitespace
    2011-04-25 Derrick Brashear  (4552) Darwin CM: afs_IsDynrootFid takes a fid ...
    2011-04-25 Simon Wilkinson   (4551) Windows: Remove duplicate file
    2011-04-22 Jeffrey Altman    (4523) Windows: change thyper to offset and fix error
    2011-04-22 Jeffrey Altman    (4522) Windows: avoid race when writing mountPointString
    2011-04-22 Andrew Deason     (4518) aklog: Return token when performing 524 conversion
    2011-04-17 Jeffrey Altman    (4459) asetkey: permit des-cbc-md5 and des-cbc-md4 keys
    2011-04-13 Andrew Deason     (4460) libafs: Do not specify an Rx busy channel error
    2011-04-01 Antoine Verheijen (4388) OpenBSD: Complete implementation of afs_osi_TimedSleep

### Patches merged into the stable 1.4.x branch

    Date       Committer        Change# Description
    2011-05-17 Andrew Deason     (4667) unix blacklistonce should default to fail if no fid
    2011-05-05 Andrew Deason     (4622) avoid downward vcache pressure when entries are free
    2011-05-05 Andrew Deason     (4621) libafs: Use vcount, not maxvcount to trim vcaches
