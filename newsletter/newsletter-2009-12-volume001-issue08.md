---
title: OpenAFS Newsletter, Issue 8, December 2009
---

# OpenAFS Newsletter, Issue 8, December 2009

Welcome to the eighth issue of the OpenAFS newsletter. This newsletter
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

I hope everyone enjoys the holidays.

## General OpenAFS Progress

OpenAFS 1.5.68 was released on December 8. Key highlights include dynamic
server ranking based on network conditions and support for more than 128
fileserver threads.

Disk cache performance on Fedora 12 may be poor because of IMA support in
the kernel. Using a memory cache or recompiling the kernel to disable IMA
support are workarounds. Fixing this in the long-term may require
reworking how the disk cache accesses files.

Mike Meffie pointed out that a fileserver lockup was fixed recently. Bug
124097 was fixed commit 416e2f11c35f5d55f91090b30b4db1a9bf6d6e0 which was
pulled into the 1.4.x branch and should make it into the next 1.4.x
release.

## Events

### Annual Best Practices Workshop

Plans are already underway for the seventh Workshop, to be held May 24-28,
2010, at the University of Illinois at Urbana-Champaign.  We hope to see
you there.

### European AFS Conference

The date for the 3rd European AFS & Kerberos Conference has been set. The
conference will take place in Pilsen, Czech Republic, from September 13 to
September 15, 2010. More details are forthcoming and will be posted at
[http://afs2010.civ.zcu.cz](http://afs2010.civ.zcu.cz).

## AFS Protocol Standardization

Informal drafts that haven't been uploaded to the IETF web site:

Rx Spec:

[http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html](http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html)

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization](http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names-00](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names-00)

Status: Active - Second call for review

As before, I've written up a draft based on the 2004 Stockholm AFSig
hackathon discussion of the PTS alternate authentication names proposal,
as modified based on further feedback and the 2009 Edinburgh Hackathon.
Comments welcome and encouraged.

\--Derrick Brashear

### AFS Callback Extensions

[http://www.ietf.org/id/draft-benjamin-extendedcallbackinfo-00.txt](http://www.ietf.org/id/draft-benjamin-extendedcallbackinfo-00.txt)

Status: Active - Needs more discussion

We need to decide whether we're going to wait for the RPC refresh changes
before publishing extended callbacks. My belief is that that's the only
factor currently delaying this document. The question here, essentially,
is whether anyone would deploy extended callbacks before deploying updated
RPCs. To date, nobody has said they would do so.

\--Simon Wilkinson

### DNS SRV Resource Records for AFS

[http://tools.ietf.org/html/draft-allbery-afs-srv-records-01](http://tools.ietf.org/html/draft-allbery-afs-srv-records-01)

Status: Last Call before IETF submission

This is a last call for any further feedback, corrections, or comments on
draft-allbery-afs-srv-records-01 before I ask about advancing it as an RFC
independent submission.  The current text is available at:

[http://tools.ietf.org/id/draft-allbery-afs-srv-records](http://tools.ietf.org/id/draft-allbery-afs-srv-records)

Please send any further comments before December 14th.  If I have not
heard anything by that point that seems to question consensus on this
document, I will approach the Application Area ADs and ask their opinion
about whether to proceed as an independent submission as an informational
RFC or whether they feel this should be standards track for any reason.
(I suspect that informational is correct since AFS is not an IETF
protocol, but I want to ask just in case.)

\--Russ Allbery

## Projects

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

The fix for 124484 (volserver salvages) in gerrit 786/787 has been a
little delayed from trying to agree on new volume package APIs, but
progress is being made. Another notable DAFS change undergoing review is
in gerrit 880, which can dramatically speed up salvages. DAFS developer
documentation is being actively worked on, and should be available
sometime soon.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Simon Wilkinson made a small correction in the pt\_util man page.

### Userspace cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

Pioctl emulation is working for ACL and mountpoint manipulation. I'm
working on cleaning up my patchsets to be suitable for gerrit submission.

\--Andrew

### SetAG

Project Contact:

- Alberto Mancini <ab.mancini@gmail.com>

Project Description:

During the developement of a web-interface for AFS (still in progress, see
"AFS access through the web", "European AFS meeting 2009"), we found that
the use of PAGs (shared between threads) to keep credentials forces
inefficient choices in the development of some applications
(e.g. authenticated web services), so we switched to a more fine grained
"credential pointer", named AG, that can be associated to just a thread.

Current Status:
We have a sample implementation for Linux based on openafs 1.4, stable
enough for our in house development; we are planning the porting to
openafs 1.5.

There is a tiny Java wrapper (jni) that provides access to the 'AG'
functionality so that tokens are associated to single threads,
of course we also wrapped ktc\_SetToken to authenticate in java.

\--Alberto

### OpenAFS Server Preference Based on Network Conditions

Project Contact:

- Jake Thebault-Spieker <summatusmentis@gmail.com>

These changes have been merged into the master and 1.5.x branches. They
are included in v1.5.58. This section will be part of the general OpenAFS
news in future newsletters.

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Disconnected AFS support - June 2009
- Rx OSD integration & Raw Vicep Access in Clients - August 2009
- Extended Callback Information - October 2009
- \*BSD Support - October 2009
- Mac OS X OpenAFS Preference Pane - November 2009
- Kerberos v5 and multiple encryption types - November 2009
- S3 Front-end for AFS - November 2009
- Active Directory Backend for Ptserver - November 2009
- Virtual Machine Images - November 2009

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 27 (last month: 36)

    Patches merged into the master branch:
    Month   Number of Commits
    2009-12   24  (Partial month)
    2009-11   86
    2009-10  154
    2009-09  142
    2009-08   78
    2009-07  181

    Patches merged into the stable branch:
    Month   Number of Commits
    2009-12   2 (Partial month)
    2009-11  21
    2009-10   7
    2009-09   8
    2009-08  17
    2009-07   5

### Patches waiting for review

    Date       Author         Change# Description
    2009-12-11 Claudio Bisegni  (906) OpenAFS Preference Pane Now the preference pane is fat compiled.
    2009-12-11 Andrew Deason    (787) DAFS: Allow non-fileserver to schedule salvages
    2009-12-10 Michael Meffie   (905) Prefix global defines
    2009-12-10 Michael Meffie   (855) Consolidate duplicate definitions
    2009-12-08 Jeffrey Altman   (900) Windows: return ENOMEM from cm_BPlus functions on malloc failure
    2009-12-03 Andrew Deason    (880) DAFS: Maintain viced volume group hierarchy cache
    2009-12-02 Simon Wilkinson  (794) Add printf format checks to afs_com_err()
    2009-12-02 Simon Wilkinson  (793) Add printf format checks to util's log functions
    2009-12-01 Andrew Deason    (870) Add the 'vos endtrans' command
    2009-11-29 Andrew Deason    (875) Make ubik use unsigned addresses
    2009-11-21 Simon Wilkinson  (837) Move GLOCK initialisation to platform directories
    2009-11-20 Simon Wilkinson  (838) Kernel is always defined
    2009-11-19 Marc Dionne      (847) src/pam warning fixes
    2009-11-18 Andrew Deason    (709) Break origin's callback for RXAFS_Rename target
    2009-11-18 Simon Wilkinson  (796) Add printf format checks to the rest of tree
    2009-11-12 Simon Wilkinson  (792) Add printf format checks to the cache manager
    2009-11-12 Derrick Brashear (783) conservative dynamic vcache fix for 14x
    2009-11-12 Simon Wilkinson  (795) Add printf format checks to rx
    2009-11-04 Derrick Brashear (451) macos knote fsevents hinting
    2009-11-04 Andrew Deason    (436) Avoid unnecessarily updating .. in SAFSS_Rename
    2009-11-04 Evan Broder      (778) Increase the maximum number of sysnames
    2009-11-04 Michael Meffie   (215) Print throttled packet counts with rxdebug
    2009-10-26 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2009-09-09 Matt Benjamin    (435) clear stat flag on renamed directories
    2009-08-29 Matt Benjamin    (376) K5SSL by Marcus Watts
    2009-07-29 Michael Meffie   (147) Fix bosserver directory creation
    2009-07-24 Hartmut Reuter    (70) preparing rxosd integration: change in AFSFetchStatus



### Patches merged into the master branch

    Date       Author         Change# Description
    2009-12-10 Andrew Deason    (786) Expand ProgramType enumeration
    2009-12-10 Simon Wilkinson  (903) Linux: Use splice to speed up cache storeback
    2009-12-10 Simon Wilkinson  (902) Rework cache store back
    2009-12-10 Marc Dionne      (904) Linux: deal with ctl_name removal
    2009-12-08 Simon Wilkinson  (901) pt_util runs on database servers
    2009-12-08 Jeffrey Altman   (892) Windows: cm_BPlusEnumAlloc should not fail for zero entries
    2009-12-08 Jeffrey Altman   (893) Windows: cm_BPlusDirBuildTree can fail
    2009-12-08 Derrick Brashear (896) macos avoid dotunderbar lookups in fakestat mode
    2009-12-07 Derrick Brashear (898) add newline to lockprocs_prototypes.h
    2009-12-07 Andrew Deason    (869) Dump all hostFlags in hosts.dump
    2009-12-07 Andrew Deason    (895) Make HandleClientContext take an afs_ucred_t
    2009-12-07 Simon Wilkinson  (894) Remove AFS_USEBUFFERS
    2009-12-05 Derrick Brashear (891) Windows: Version update for 1.5.68
    2009-12-05 Derrick Brashear (889) rx packet dumper not in kernel
    2009-12-05 Derrick Brashear (888) unix 1.5.68
    2009-12-04 Jeffrey Altman   (887) Fix midnight volume calculation to build on Windows
    2009-12-04 Rainer Toebbicke (849) Calculate midnight (for volume stats) based on standard functions
    2009-12-04 Jeffrey Altman   (886) Windows: Version update for 1.5.67
    2009-12-04 Derrick Brashear (885) unix 1.5.67
    2009-12-04 Derrick Brashear (883) add rx packet trace debug dumping for unix
    2009-12-03 Jeffrey Altman   (884) Windows: change notes for 1.5.67 release
    2009-12-03 Derrick Brashear (881) add unlock support to afscp
    2009-12-03 Jeffrey Altman   (319) Use xdr_alloc and xdr_free within ptuser
    2009-12-01 Michael Meffie   (879) shutdown_icl return type void
    2009-11-30 Andrew Deason    (736) Correct duplicate special inodes while salvaging
    2009-11-29 Marc Dionne      (860) Warning fixes - key handling
    2009-11-29 Andrew Deason    (876) Add server prefix to utst_int.xg
    2009-11-28 Andrew Deason    (863) Add safety checks on all hostList traversals
    2009-11-28 Andrew Deason    (873) Add a watchdog timer for ShutDownAndCore(PANIC)
    2009-11-28 Andrew Deason    (871) Correct include paths in fs_conv_sol26.c
    2009-11-28 Andrew Deason    (872) 'Flexible client buffer growth' fallout
    2009-11-26 Jeffrey Altman   (868) Windows: Fix test for setting FILE_ATTR_READONLY
    2009-11-25 Rainer Toebbicke (799) Flexible client buffer growth
    2009-11-24 Jeffrey Altman   (859) Windows: disable readonly volume versioning due to file server bug
    2009-11-24 Jeffrey Altman   (858) Windows: cm_TryBulkStatus processing changes
    2009-11-24 Jeffrey Altman   (852) Windows: provide enhanced error output to aklog
    2009-11-24 Jeffrey Altman   (857) Windows: when assigning a new clientModTime, hold a lock
    2009-11-24 Jeffrey Altman   (854) Windows: modify src/rxkad/NTMakefile to avoid file copies
    2009-11-24 Jeffrey Altman   (856) viced: set volume sync data in bulk status rpcs
    2009-11-23 Marc Dionne      (730) Linux: Keyrings PAG handling changes
    2009-11-23 Marc Dionne      (867) Remove "unused" warnings from lex generated files
    2009-11-23 Marc Dionne      (864) Linux: hinting removal fallout
    2009-11-21 Marc Dionne      (865) Revert "osi_UFSOpen returns struct osi_file *"
    2009-11-20 Simon Wilkinson  (851) osi_UFSOpen returns struct osi_file *
    2009-11-20 Simon Wilkinson  (850) Remove inode hinting for dcaches
    2009-11-20 Andrew Deason    (845) Define afs_maxvcount everywhere
    2009-11-20 Simon Wilkinson  (820) Fix prepare and commit_write to do the right thing
    2009-11-20 Simon Wilkinson  (726) Linux: Use atomics for credential reference counts
    2009-11-19 Andrew Deason    (846) Define WCOREDUMP in salvsync-server.c
    2009-11-19 Simon Wilkinson  (834) Rationalise our include paths
    2009-11-19 Mickey Lane      (840) Fix 2 errors in Windows release Notes
    2009-11-19 Jeffrey Altman   (824) Windows: cm_BkgDaemon requeuing only applies to BkgStore
    2009-11-19 Jeffrey Altman   (827) Windows: Improvements to background fetch processing
    2009-11-19 Jeffrey Altman   (828) Windows: buf_DirtyBuffersExist uses fileHashp not allp list pointer
    2009-11-19 Jeffrey Altman   (829) Windows: Permit custom version numbers and default cellname
    2009-11-18 Andrew Deason    (842) Define T_SRV when not defined for us
    2009-11-18 Andrew Deason    (843) src/afs/afs_user.c typo
    2009-11-18 Andrew Deason    (844) AIX: Missing brace in afs_vnop_flock.c
    2009-11-18 Matt Benjamin    (584) viced ihandle boost
    2009-11-18 Simon Wilkinson  (839) Name chunkOps structure elements
    2009-11-18 Michael Meffie   (841) fix for volser transaction object race conditions
    2009-11-18 Simon Wilkinson  (835) Linux: Fix lock ordering
    2009-11-18 Marc Dionne      (836) aklog build fix: com_err.h header
    2009-11-17 Derrick Brashear (832) ktc remove unused variable
    2009-11-17 Simon Wilkinson  (822) Translate messages from ktc_SetToken
    2009-11-17 Simon Wilkinson  (821) Better errors from aklog
    2009-11-17 Derrick Brashear (818) asm unexecutable stack
    2009-11-16 Jeffrey Altman   (825) Windows: Code signing with cross-signed certificates
    2009-11-16 Jeffrey Altman   (831) Windows: Use STATUS_IO_TIMEOUT where STATUS_TIMEOUT was returned
    2009-11-16 Jeffrey Altman   (826) Windows: Error mapping for VBUSY and VRESTARTING
    2009-11-15 Jeffrey Altman   (830) Windows: Fix port assignment to use network byte order
    2009-11-15 Jeffrey Altman   (791) Windows: ports in the cache manager are stored in network byte order
    2009-11-13 Andrew Deason    (815) Make ktc_curpag also detect ONEGROUP PAG gids
    2009-11-13 Simon Wilkinson  (819) Use set_page_writeback and end_page_writeback
    2009-11-11 Marc Dionne      (797) Linux: Use the kernel's credentials structure
    2009-11-11 Andrew Deason    (814) Do not check *aoutSize in PGetPAG
    2009-11-11 Simon Wilkinson  (813) Update warning inhibition
    2009-11-11 Simon Wilkinson  (812) Prototype kalog_Init
    2009-11-11 Simon Wilkinson  (811) const char paths for ubik_ServerInit
    2009-11-11 Simon Wilkinson  (810) Fix des key type issue in bosoprocs
    2009-11-11 Simon Wilkinson  (809) Prototype UV_Bind
    2009-11-11 Simon Wilkinson  (807) Remove 'M' variants of lock macros
    2009-11-11 Simon Wilkinson  (808) Fix warnings from afsconf_SetExtendedCellInfo
    2009-11-11 Simon Wilkinson  (806) Include signal.h for sigfillset
    2009-11-11 Marc Dionne      (804) krb_udp.c warning fix
    2009-11-11 Michael Meffie   (800) cm: address race condition in afs_QueueVCB
    2009-11-11 Simon Wilkinson  (805) cr_gid is already used by Darwin
    2009-11-11 Marc Dionne      (803) src/pam/afs_auth.c warning fix
    2009-11-10 Derrick Brashear (801) unix srv record network byte order fix
    2009-11-10 Russ Allbery     (798) Update afsd cache and firewall details
    2009-11-10 Simon Wilkinson  (802) Fix locking in FlushVCBs when called from discon
    2009-11-09 Marc Dionne      (768) Unix client: wrappers for credentials structure access
    2009-11-09 Michael Meffie   (764) viced: avoid useless core if shutdown during initialization
    2009-11-08 Simon Wilkinson  (789) Add printf-style format checking
    2009-11-08 Simon Wilkinson  (785) Complete removal of DUX client code
    2009-11-08 Marc Dionne      (790) Linux: always use afs_maybe_unlock_kernel
    2009-11-08 Simon Wilkinson  (784) Move vnode macros to their own directories
    2009-11-07 Simon Wilkinson  (788) Add error_table.c to gitignore in comerr
    2009-11-05 Andrew Deason    (782) Cleanup VOffline log message
    2009-11-05 Simon Wilkinson  (781) Prevent VLRUQ race in ShakeLooseVCaches
    2009-11-04 Rainer Toebbicke (756) Correct diskused and files when cloning a volume
    2009-11-04 Derrick Brashear (772) macos fstrace msgcat search path
    2009-11-04 Derrick Brashear (771) macos 10.6 64bit trace fixes
    2009-11-04 Marc Dionne      (752) Linux - Fix disk cache access for selinux/AppArmor constrained processes
    2009-11-03 Andrew Deason    (716) Check for (hostFlags & HOSTDELETED) after h_Lock_r
    2009-11-03 Andrew Deason    (765) DAFS: Avoid SALVSYNC communication during shutdown
    2009-11-03 Andrew Deason    (769) DAFS: Wait for exclusive ops in FSYNC_VOL_OFF
    2009-11-02 Dan Hyde         (757) Add array bounds checking in h_Enumerate
    2009-11-02 Marc Dionne      (759) Linux: Fix write_begin configure test for recent RHEL kernels
    2009-11-02 Marc Dionne      (758) Fix memory allocation warnings at shutdown



### Patches merged into the stable branch

    Date       Author         Change# Description
    2009-12-01 Andrew Deason    (882) Correct duplicate special inodes while salvaging
    2009-12-01 Michael Meffie   (877) shutdown_icl returns void
    2009-11-30 Andrew Deason    (878) Modify Solaris Rx NetIfPoller to avoid Panic
    2009-11-28 Rainer Toebbicke (874) Avoid IHandle leak when failing to attach volume
    2009-11-23 Andrew Deason    (776) Check for (hostFlags & HOSTDELETED) after h_Lock_r
    2009-11-20 Andrew Deason    (862) Add array bounds checking in h_Enumerate
    2009-11-19 Michael Meffie   (619) volser transaction object race conditions
    2009-11-19 Andrew Deason    (853) Make ktc_curpag also detect ONEGROUP PAG gids
    2009-11-16 Anders Kaseorg   (823) Clean up console message
    2009-11-11 Michael Meffie   (817) cm: address race condition in afs_QueueVCB
    2009-11-11 Andrew Deason    (816) Do not check *aoutSize in PGetPAG
    2009-11-05 Marc Dionne      (767) Fix memory allocation warnings at shutdown
    2009-11-05 Marc Dionne      (766) Linux: Fix write_begin configure test for recent RHEL kernels
    2009-11-04 Derrick Brashear (780) macos 10.6 64bit trace fixes
    2009-11-04 Russ Allbery     (779) .gitignore for src/pinstall
    2009-11-04 Russ Allbery     (777) Always use kbuild for all Linux kernel configure probes
    2009-11-04 Marc Dionne      (774) Linux - Fix disk cache access for selinux/AppArmor constrained processes
    2009-11-04 Russ Allbery     (775) Build shadow header files when necessary on Linux
    2009-11-04 Russ Allbery     (773) Make afsd.pod reflect reality
    2009-11-02 Andrew Deason    (762) Avoid using released hosts
    2009-11-02 Andrew Deason    (763) Protect rx_call iovq from simultaneous attempts to empty it
    2009-11-02 Andrew Deason    (761) Dec old special inodes in inode convertROtoRW
    2009-11-02 Marc Dionne      (760) Linux: Avoid deadlock in readdir - release GLOCK for filldir
    2009-10-30 Marc Dionne      (755) Linux: 2.6.32 - Adapt to writeback changes
    2009-10-28 Andrew Deason    (749) Avoid prematurely destroying callback_rxcon
    2009-10-21 Andrew Deason    (702) HPUX: Do not sigwait on critical signals



## Resolved Tickets

Here is a list of tickets that have been resolved since November 1, 2009:

    ticket # state     created       title
      92944: resolved  Apr 03, 2008  [OpenAFS-devel] SELinux biting OpenAFS [Cache manager using the wrong SELinux context]
     125475: resolved  Oct 08, 2009  OpenAFS on kernel 2.6.32 triggers WARNING at fs/fs-writeback.c:1112
     125486: resolved  Oct 10, 2009  Uninstall.command Open AFS v1.565
     125544: resolved  Oct 27, 2009  BUG at osi_file.c:87 with AppArmor
     125555: resolved  Oct 30, 2009  OpenAFS 1.4.11 crash on RHEL 5 update 4 systems
