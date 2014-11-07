---
title: OpenAFS Newsletter, Volume 2, Issue 1, January 2010
layout: page
category: newsletter
permalink: /newsletter/newsletter-2010-01-volume002-issue01.html
---

# OpenAFS Newsletter, Volume 2, Issue 1, January 2010

Welcome to the ninth issue of the OpenAFS newsletter. This newsletter
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

Some discussion took place about which configure and command-line options
should be changed before the code is branched for 1.6. The archive is at
[http://lists.openafs.org/pipermail/openafs-info/2009-December/032494.html](http://lists.openafs.org/pipermail/openafs-info/2009-December/032494.html).
Based on this discussion, Simon Wilkinson submitted patches to enable
bos-restricted mode at compile-time, remove the --disable-large-fileserver
configuration option, always enabled AFSDB support inclients, and always
have the "vos listvol" command show full output. These patches were
accepted and merged into the master git branch.

Code cleanup: Russ Allbery fixed all compiler warnings regarding
supergroups onthe i386 platform. Some warnings remain on x86\_64 platforms.

Simon's patch to tone down the warnings about syscall probing was accepted
into the 1.4.x branch and will be in the next 1.4 release.

1.4.12 release candidate 1 was released on January 12. Testing and
feedback is encouraged. Please report any success or failures on the
openafs-into or openafs-devel email lists. Bug reports are greatly
appreciated.

## Events

### Annual Best Practices Workshop

Plans are already underway for the seventh Workshop, to be held May 24-28,
2010, at the University of Illinois at Urbana-Champaign.  We hope to see
you there.

Web site: [http://workshop.openafs.org/afsbpw10/index.html](http://workshop.openafs.org/afsbpw10/index.html)

The deadline for proposals is February 1:

[http://workshop.openafs.org/afsbpw10/cfp.html](http://workshop.openafs.org/afsbpw10/cfp.html)

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

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names-00](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names-00)

Status: Active - Third call for review

Third call for review; I'm gonna ask for a last call later in the
month as so far all review comment has been incorporated, unless
something comes up.

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

[http://tools.ietf.org/id/draft-allbery-afs-srv-records](http://tools.ietf.org/id/draft-allbery-afs-srv-records)

Status: Submitted to IETF

The IESG has received a request from an individual submitter to consider
the following document:

\- 'DNS SRV Resource Records for AFS '
  <draft-allbery-afs-srv-records-03.txt> as a Proposed Standard

The IESG plans to make a decision in the next few weeks, and solicits
final comments on this action.  Please send substantive comments to the
ietf@ietf.org mailing lists by 2010-02-05. Exceptionally, comments may be
sent to iesg@ietf.org instead. In either case, please retain the beginning
of the Subject line to allow automated sorting.

Please note that the document has a Normative Downreference to RFC 1183,
which is an Experimental RFC.

The file can be obtained via
http://www.ietf.org/internet-drafts/draft-allbery-afs-srv-records-03.txt

IESG discussion can be tracked via
https://datatracker.ietf.org/public/pidtracker.cgi?command=view\_id&dTag=190
89&rfc\_flag=0



### RXGK

I've just pushed a new version of the RXGK draft to the Internet Drafts
repository. I believe that this draft addresses all of the comments I've
received to date, and all of the issues raised at the Edinburgh Hackathon.

Implementation is likely to start shortly - review would be greatly
appreciated!

The draft is available from:
http://www.ietf.org/id/draft-wilkinson-afs3-rxgk-00.txt

\--Simon

### AFS3 ACL Rights

[http://www.ietf.org/id/draft-deason-afs3-acl-restrictions-01.txt](http://www.ietf.org/id/draft-deason-afs3-acl-restrictions-01.txt)

Status: Second draft

Andrew Deason has published an IETF draft to provide a common document for
discussion of the proposed new ACL rights to prevent users with admin
rights on a folder from giving rights to system:anyuser.

## Projects

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

Bug 124484 (volserver salvages) has finally been fixed, and with that,
we are aware of no open DAFS-specific bugs that are critical for
production use. The salvager optimization in gerrit 880 is being
partially reworked to better accommodate changes in volume/partition
locking which is currently in progress. Parts of the new developer
documentation have been completed, and should be public soon.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Just the regular maintenance work on the man pages and documentation of
new features.

\--Russ

Documentation fixes were made for vos\_dump, asetkey, and bos.

### \*BSD Support

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

I've released cm updates for FreeBSD RELENG\_8, most are committed; number
of outstanding cm issues is shrinking; a 9-CURRENT update will follow.

I have updated patches for a NetBSD cm port rebased from OpenBSD's ,
though result isn't 100% working cm, it's a...big improvement.  Will send
soon for consideration.

\--Matt

### Pthreaded Ubik

Project Contact:

- Steven Jenkins <steven.jenkins@gmail.com>
- Andrew Deason <adeason@sinenomine.net>

After several months of inactivity, several people have started work on
fixing the known problems in pthreaded ubik.  Contact Steven Jenkins or
Andrew Deason if you would like to help with bug fixing and/or testing.

### Mac OS X OpenAFS Preference Pane

Project Contact:

- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

The preference pane is now compiled as a multi-platform binary for the
ppc, i386, and x86\_64 Mac OS X platforms.

\--Claudio

### Extended Callback Information

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

I understand extended callbacks to be not blocked, but is complicated
because rpc refresh work must precede it--a solution would seemingly be
opening of a pre-1.6 branch

\--Matt

### Kerberos v5 and multiple encryption types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

rxk5 has been stalled for a bit, but potentially it could be unblocked by
opening of a pre-1.6 branch

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Disconnected AFS support - June 2009
- Rx OSD integration & Raw Vicep Access in Clients - August 2009
- S3 Front-end for AFS - November 2009
- Active Directory Backend for Ptserver - November 2009
- Virtual Machine Images - November 2009
- SetAG - December 2009
- Userspace cache manager - December 2009

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 27 (last month: 27)

    Patches merged into the master branch:
    Month   Number of Commits
    2010-01   38  (Partial month)
    2009-12   72
    2009-11   85
    2009-10  154
    2009-09  142
    2009-08   78
    2009-07  181

    Patches merged into the stable branch:
    Month   Number of Commits
    2010-01   7 (Partial month)
    2009-12  92
    2009-11  21
    2009-10   7
    2009-09   8
    2009-08  17
    2009-07   5

### Patches waiting for review

    Date       Author         Change# Description
    2010-01-15 Marc Dionne       (847) src/pam warning fixes
    2010-01-14 Derrick Brashear (1101) abstract rx if structure access
    2010-01-14 Simon Wilkinson  (1074) Unix CM: Include memcache's tiov in rxfs_context
    2010-01-14 Jeffrey Altman   (1084) Windows: Permit AFSCache file to be encrypted
    2010-01-14 Simon Wilkinson  (1073) Unix CM: Always use ->storeproc()
    2010-01-14 Chas Williams - CONTRACTOR (1080) LINUX: you dont need to memset() after allocating credentials
    2010-01-14 Simon Wilkinson  (1072) Unix CM: Conflate rxfs_[store,fetch]Variables
    2010-01-14 Derrick Brashear  (451) macos knote fsevents hinting
    2010-01-14 Michael Meffie   (1001) return an error from afs_readdir when out of buffers
    2010-01-14 Michael Meffie   (1092) DAFS: avoid volume lock contention during initialization
    2010-01-06 Derrick Brashear (1066) darwin rxevent sleep instead of polling
    2009-12-30 Andrew Deason     (880) DAFS: Maintain viced volume group hierarchy cache
    2009-12-16 Simon Wilkinson   (792) Add printf format checks to the cache manager
    2009-12-02 Simon Wilkinson   (794) Add printf format checks to afs_com_err()
    2009-12-02 Simon Wilkinson   (793) Add printf format checks to util's log functions
    2009-11-29 Andrew Deason     (875) Make ubik use unsigned addresses
    2009-11-18 Andrew Deason     (709) Break origin's callback for RXAFS_Rename target
    2009-11-18 Simon Wilkinson   (796) Add printf format checks to the rest of tree
    2009-11-12 Simon Wilkinson   (795) Add printf format checks to rx
    2009-11-04 Andrew Deason     (436) Avoid unnecessarily updating .. in SAFSS_Rename
    2009-11-04 Evan Broder       (778) Increase the maximum number of sysnames
    2009-11-04 Michael Meffie    (215) Print throttled packet counts with rxdebug
    2009-10-26 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2009-09-09 Matt Benjamin     (435) clear stat flag on renamed directories
    2009-08-29 Matt Benjamin     (376) K5SSL by Marcus Watts
    2009-07-29 Michael Meffie    (147) Fix bosserver directory creation
    2009-07-24 Hartmut Reuter     (70) preparing rxosd integration: change in AFSFetchStatus

### Patches merged into the master branch

    Date       Author         Change# Description
    2010-01-15 Asanka Herath    (1103) Fix typo in AdminGuide
    2010-01-14 Dan Hyde         (1098) volmonitor keep vtrans lock
    2010-01-14 Simon Wilkinson   (838) Kernel is always defined
    2010-01-14 Simon Wilkinson   (837) Move GLOCK initialisation to platform directories
    2010-01-14 Simon Wilkinson  (1062) rewrite afs_MemWriteBlk() using afs_MemWritevBlk()
    2010-01-14 Simon Wilkinson  (1061) Quick fix for readpages when using memcache
    2010-01-14 Chas Williams - CONTRACTOR (1079) afsd: decprecate -mem_alloc_sleep flag (and related code)
    2010-01-14 Andrew Deason    (1090) Always check VInitVolumePackage2 return code
    2010-01-14 Simon Wilkinson  (1097) Remove weekly bosserver restarts
    2010-01-13 Simon Wilkinson  (1007) Linux: Rework PAG to group conversions
    2010-01-13 Jeffrey Altman   (1089) Windows: remove signed vs unsigned error in smb_Init
    2010-01-13 Jeffrey Altman   (1087) Windows: Protect buffers in smb_WriteData from simultaneous writes
    2010-01-13 Jeffrey Altman   (1017) Windows: fs examine owner and group are signed
    2010-01-13 Jeffrey Altman   (1086) Windows: do not call cm_SearchCellByDNS if AFS_AFSDB_ENV is not defined
    2010-01-13 Jeffrey Altman   (1085) Windows: buf_Recycle should clean up flags and reset version
    2010-01-13 Jeffrey Altman   (1083) Windows: do not leak scp->dirlock if cm_BPlusDirBuildTree fails
    2010-01-13 Jeffrey Altman   (1016) Windows: alter nmtest CreateFile modes
    2010-01-13 Jeffrey Altman    (900) Windows: return ENOMEM from cm_BPlus functions on malloc failure
    2010-01-12 Simon Wilkinson  (1075) Use dget_parent to handle getting inode of parent
    2010-01-12 Matt Benjamin    (1068) freebsd:  CM changes targeting RELENG_8
    2010-01-12 Andrew Deason     (997) DAFS: avoid saving fileserver state when panicing
    2010-01-12 Andrew Deason     (787) DAFS: Allow non-fileserver to schedule salvages
    2010-01-08 Simon Wilkinson  (1082) Revert "Linux: Replace invalidate_inode_pages"
    2010-01-08 Derrick Brashear (1059) linux kernel lacks uintptr
    2010-01-08 Chas Williams - CONTRACTOR (1078) UNIX CM: remove the last remaining reference to afs_rxglobal_lock
    2010-01-07 Chas Williams - CONTRACTOR (1077) LINUX/: ifdef for GFP_NOFS conditionals
    2010-01-06 Derrick Brashear (1056) darwin module prototype and cleanup
    2010-01-06 Dan Hyde         (1069) volmonitor copy link before calling free
    2010-01-06 Simon Wilkinson  (1071) Linux: Mark our super block as not updating access time
    2010-01-06 Simon Wilkinson  (1070) Linux: Use the correct ATIME flag
    2010-01-05 Derrick Brashear (1065) cachemanager additional cleanup
    2010-01-05 Derrick Brashear (1057) macos code signature for afsd
    2010-01-05 Marc Dionne      (1063) Linux: don't oops on writeback if vcache has no stashed credentials
    2010-01-05 Andrew Deason    (999) Refuse to attach inode partitions with UFS logging
    2010-01-05 Michael Meffie   (1046) viced: allow alternate addresses on the same hash chain again
    2010-01-05 Simon Wilkinson  (1060) Fixes for supergroups on Darwin 64bit
    2010-01-04 Simon Wilkinson  (1047) Unix CM: Use xdr_free to free memory allocated by XDR
    2010-01-04 Matt Benjamin    (1055) freebsd: fix afs_root signature (RELENG_8)
    2009-12-31 Marc Dionne      (1054) Build fix: restore centry in ptutils.c
    2009-12-31 Russ Allbery     (1050) Remove warnings from supergroups code on x86
    2009-12-31 Russ Allbery     (1051) Correct spelling errors in man pages
    2009-12-31 Matt Benjamin    (1023) freebsd: track RELENG_8
    2009-12-31 Simon Wilkinson  (1035) Linux: Check for multiple silly renames
    2009-12-31 Simon Wilkinson  (1034) Abstract out Linux sillyrename function
    2009-12-31 Simon Wilkinson  (1033) Remove unused configuration tests
    2009-12-31 Simon Wilkinson  (1032) Remove HAVE_STRUCT_BUF test
    2009-12-31 Simon Wilkinson  (1031) Remove --disable-full-vos-listvol-switch option
    2009-12-31 Simon Wilkinson  (1030) Remove --disable-afsdb
    2009-12-31 Derrick Brashear (1037) clean up axscache at shutdown
    2009-12-31 Andrew Deason    (1048) Make DAFS 'bos salvage' work in restricted mode
    2009-12-31 Simon Wilkinson  (1029) Remove --disable-largefile-fileserver
    2009-12-31 Simon Wilkinson  (1028) Turn on bos restricted code
    2009-12-31 Russ Allbery     (1052) Update .gitignore for copied rxkad files
    2009-12-31 Simon Wilkinson  (1041) Linux: #if BLAH should be #if defined(BLAH)
    2009-12-30 Michael Meffie   (1049) missing brace in afs_get_sb
    2009-12-30 Simon Wilkinson  (1038) Unix: Rename aklog_main.c as aklog.c
    2009-12-30 Simon Wilkinson  (1036) Unix: Merge aklog with aklog_main
    2009-12-30 Derrick Brashear  (995) avoid leaking stat info
    2009-12-30 Simon Wilkinson  (1040) Fix ioctl32 inclusion on Sparc 64
    2009-12-30 Andrew Deason    (1039) Return a cell name from afsconf_LookupServer
    2009-12-30 Simon Wilkinson  (1045) Documentation: Fix asetkey syntax
    2009-12-30 Simon Wilkinson  (1042) Linux: Replace invalidate_inode_pages
    2009-12-30 Simon Wilkinson  (1044) Documentation: vos dump -verbose outputs to stderr
    2009-12-30 Simon Wilkinson  (1043) rxgen: Remove stray debugging statement
    2009-12-28 Andrew Deason    (1027) Move TOP_INCDIR/des dependency to prelude
    2009-12-23 Andrew Deason    (1000) Check viced FetchData length for cache bypass
    2009-12-23 Andrew Deason    (1025) Fix warnings in fs.c with --enable-cache-bypass
    2009-12-22 Simon Wilkinson  (1022) Solaris: Don't access lbolt directly
    2009-12-22 Simon Wilkinson  (1021) Solaris: Don't directly fiddle with the groups structure
    2009-12-22 Simon Wilkinson  (1020) Solaris: Be more flexible about compilers
    2009-12-22 Simon Wilkinson  (1019) Look for aclocal in more places
    2009-12-22 Andrew Deason    (1018) Fix typo in afs_linux_cred_is_current
    2009-12-21 Michael Meffie    (905) Prefix global defines
    2009-12-21 Michael Meffie    (855) Consolidate duplicate definitions
    2009-12-20 Marc Dionne      (1011) Linux: fix sysctl for 2.6.33
    2009-12-20 Marc Dionne      (1009) Linux: utsrelease.h is moving
    2009-12-20 Simon Wilkinson  (1006) Fix PAGs for all platforms without Linux keyrings
    2009-12-20 Simon Wilkinson  (1005) Linux: Simplify keyring compatibility code
    2009-12-20 Simon Wilkinson  (1004) Linux: Don't panic when keys aren't found
    2009-12-20 Marc Dionne       (768) Unix client: wrappers for credentials structure access
    2009-12-19 Simon Wilkinson  (1003) Linux: Flush vcaches when a mount fails
    2009-12-18 Andrew Deason     (996) Do not trust FetchData length from fileservers
    2009-12-18 Andrew Deason     (998) platform target depends on cmd and vol
    2009-12-17 Derrick Brashear  (988) kernel ioctl32 conversion typecasting
    2009-12-16 Andrew Deason     (870) Add the 'vos endtrans' command
    2009-12-13 Claudio Bisegni   (906) OpenAFS Preference Pane Now the preference pane is fat compiled.
    2009-12-10 Andrew Deason     (786) Expand ProgramType enumeration
    2009-12-10 Simon Wilkinson   (903) Linux: Use splice to speed up cache storeback
    2009-12-10 Simon Wilkinson   (902) Rework cache store back
    2009-12-10 Marc Dionne       (904) Linux: deal with ctl_name removal
    2009-12-08 Simon Wilkinson   (901) pt_util runs on database servers
    2009-12-08 Jeffrey Altman    (892) Windows: cm_BPlusEnumAlloc should not fail for zero entries
    2009-12-08 Jeffrey Altman    (893) Windows: cm_BPlusDirBuildTree can fail
    2009-12-08 Derrick Brashear  (896) macos avoid dotunderbar lookups in fakestat mode
    2009-12-07 Derrick Brashear  (898) add newline to lockprocs_prototypes.h
    2009-12-07 Andrew Deason     (869) Dump all hostFlags in hosts.dump
    2009-12-07 Andrew Deason     (895) Make HandleClientContext take an afs_ucred_t
    2009-12-07 Simon Wilkinson   (894) Remove AFS_USEBUFFERS
    2009-12-05 Derrick Brashear  (891) Windows: Version update for 1.5.68
    2009-12-05 Derrick Brashear  (889) rx packet dumper not in kernel
    2009-12-05 Derrick Brashear  (888) unix 1.5.68
    2009-12-04 Jeffrey Altman    (887) Fix midnight volume calculation to build on Windows
    2009-12-04 Rainer Toebbicke  (849) Calculate midnight (for volume stats) based on standard functions
    2009-12-04 Jeffrey Altman    (886) Windows: Version update for 1.5.67
    2009-12-04 Derrick Brashear  (885) unix 1.5.67
    2009-12-04 Derrick Brashear  (883) add rx packet trace debug dumping for unix
    2009-12-03 Jeffrey Altman    (884) Windows: change notes for 1.5.67 release
    2009-12-03 Derrick Brashear  (881) add unlock support to afscp
    2009-12-03 Jeffrey Altman    (319) Use xdr_alloc and xdr_free within ptuser
    2009-12-01 Michael Meffie    (879) shutdown_icl return type void

### Patches merged into the stable branch

    Date       Author         Change# Description
    2010-01-14 Simon Wilkinson  (1102) Spec file changes
    2010-01-14 Simon Wilkinson  (1099) Don't install compile_et into its own directory
    2010-01-14 Derrick Brashear  (994) Linux: kmem_cache_create fix and cleanup
    2010-01-12 Derrick Brashear (1091) make 1.4.12rc1
    2010-01-08 Derrick Brashear (1081) linux kernel lacks uintptr
    2010-01-07 Andrew Deason    (1076) avoid leaking stat info
    2010-01-07 Derrick Brashear (1053) viced host always hash on add
    2009-12-30 Michael Meffie   (1026) viced: add then remove when changing addresses
    2009-12-23 Simon Wilkinson  (1024) Shout less about system call hooks when using keyrings
    2009-12-20 Marc Dionne      (1013) Linux: deal with ctl_name removal
    2009-12-20 Christof Hanke   (1015) Backport casting from origin/master to origin/openafs-stable-1_4_x
    2009-12-20 Marc Dionne      (1012) Linux: utsrelease.h is moving
    2009-12-20 Simon Wilkinson  (1008) Linux: Flush vcaches when a mount fails
    2009-12-19 Andrew Deason    (1002) Do not trust FetchData length from fileservers
    2009-12-17 Derrick Brashear  (993) Implementation of new dump tag and length standard
    2009-12-17 Andrew Deason     (991) Add a watchdog timer for ShutDownAndCore(PANIC)
    2009-12-17 Derrick Brashear  (990) Add safety checks on all hostList traversals
    2009-12-17 Simon Wilkinson   (992) Rename installed version of compile_et
    2009-12-17 Derrick Brashear  (961) make afsd partition size check be large partition safe
    2009-12-17 Derrick Brashear  (989) kernel ioctl32 conversion typecasting
    2009-12-17 Derrick Brashear  (987) openafs 1.4 butc prototype fallout
    2009-12-17 Derrick Brashear  (986) Prevent VLRUQ race in ShakeLooseVCaches
    2009-12-17 Derrick Brashear  (985) salvager-sensible-chdirlessness-20090122
    2009-12-17 Derrick Brashear  (913) macos avoid dotunderbar lookups in fakestat mode
    2009-12-17 Derrick Brashear  (984) butc prototype 1.4 fallout
    2009-12-17 Derrick Brashear  (983) rx 1.4 mutex naming
    2009-12-17 Derrick Brashear  (982) packet allocation for 1.4 has no debug counter field
    2009-12-17 Derrick Brashear  (981) Remove hardcoded maximum time
    2009-12-17 Derrick Brashear  (980) Fix locking in afs_buffer.c
    2009-12-17 Derrick Brashear  (979) OpenAFS Preference Pane Now the preference pane is fat compiled.
    2009-12-17 Derrick Brashear  (975) Correct diskused and files when cloning a volume
    2009-12-17 Derrick Brashear  (974) prevent rx peer timeout from reaching 0.0 seconds
    2009-12-17 Derrick Brashear  (973) Fix a couple more unlink()s in vol-salvage.c
    2009-12-17 Derrick Brashear  (972) AFSPreference Pane Mounts View refresh issue
    2009-12-17 Derrick Brashear  (971) Use ranlib -c for Mac OS X Leopard
    2009-12-17 Derrick Brashear  (970) OpenAFS Preference Pane 64bit and Symbolic Link features implemented.
    2009-12-17 Derrick Brashear  (969) Improve accuracy of Rx RTT calculation by skipping retransmitted packets
    2009-12-17 Derrick Brashear  (968) OSX Launchd Startup Manage  with Preference Pane
    2009-12-17 Derrick Brashear  (967) OS Preference pane clean for final version
    2009-12-17 Derrick Brashear  (966) launchdaemon support for MacOS
    2009-12-17 Derrick Brashear  (965) AFSPreference Pane, has changed the content of launchd xml control file for AFSBackgrounder
    2009-12-17 Derrick Brashear  (964) Manage the login in the OSX Fast User Switch mode
    2009-12-17 Derrick Brashear  (963) make fileserver avoid salvage loop on init failure
    2009-12-17 Derrick Brashear  (962) Unlink correct files in salvager
    2009-12-17 Derrick Brashear  (960) Fix cache tracking for small fragsizes
    2009-12-17 Derrick Brashear  (959) darwin knet avoid rx socket during shutdown
    2009-12-17 Derrick Brashear  (958) macos package updates
    2009-12-17 Derrick Brashear  (957) des crypt cope with 64 bit longs
    2009-12-17 Derrick Brashear  (956) Fixed the tokens update and update .gitignore for MacOSX packaging file
    2009-12-17 Derrick Brashear  (955) macos afs prefspane support for 10.4
    2009-12-17 Derrick Brashear  (954) 10.6 update(Workaround for kerberos bug) and cleaning of deprecated function form code
    2009-12-17 Derrick Brashear  (953) Make MacOS installer pane permit dashes
    2009-12-17 Derrick Brashear  (952) OSX Preference Pane and AFS Backgrounder
    2009-12-17 Derrick Brashear  (951) OSX AFSBackgrounder fix minor bug
    2009-12-17 Derrick Brashear  (950) Removed user perspectivev3 file in xcode project and update the gitconfig
    2009-12-17 Derrick Brashear  (949) Cleaned most warning OSX OpenAFS preference  and completed the AFSBackgrounder implementation
    2009-12-17 Derrick Brashear  (948) AFS Backgrounder implementation & warirng clean
    2009-12-17 Derrick Brashear  (947) Start coding OSX Backgrounder Application, for OpenAFS Preference Pane, that user NSStatusItem
    2009-12-17 Derrick Brashear  (946) install AFSCommander in prefpane dir
    2009-12-17 Derrick Brashear  (945) In rxi_SendPacket[List], down hosts if ENETUNREACH or equivalent
    2009-12-17 Derrick Brashear  (944) Build fix - pre-processor typos in rx_lwp.c and rx_pthread.c
    2009-12-17 Derrick Brashear  (943) Use -errno or WSAGetLastError() as return value from rxi_Sendmsg()
    2009-12-17 Derrick Brashear  (942) Running bos -noauth should not require client CellServDB configuration
    2009-12-17 Derrick Brashear  (941) afsprefs pane shouldn't hardcode 10.4 sdk
    2009-12-17 Derrick Brashear  (940) Finish afscell implementation work
    2009-12-17 Derrick Brashear  (939) platform makefile should handle clean target
    2009-12-17 Derrick Brashear  (938) Makefile.in modification for compile AFSPreference source code
    2009-12-17 Derrick Brashear  (937) OSX Preference Pane Source Import
    2009-12-17 Derrick Brashear  (936) OSX Preference Pane
    2009-12-17 Derrick Brashear  (935) avoid call to rxi_FreePacket with NULL pointer
    2009-12-17 Derrick Brashear  (934) AFSOP_STOP_RXEVENT sometimes set without wakeup
    2009-12-17 Derrick Brashear  (933) vos print_addr() must call ubik_VL_GetAddrsU with correct level of indirection
    2009-12-17 Derrick Brashear  (932) Make 'fs listquota' output readable for large quota
    2009-12-17 Derrick Brashear  (931) Fix assert message to avoid printing garbage
    2009-12-17 Derrick Brashear  (930) Correct pointer type of 'next' field within struct volinfo
    2009-12-17 Derrick Brashear  (929) linux-locking-brace-fix-20090602
    2009-12-17 Derrick Brashear  (928) linux-byte-range-locks-sensibility-20090526
    2009-12-17 Derrick Brashear  (927) rx-pthread-mutex-protects-threadcount-20090128
    2009-12-17 Derrick Brashear  (926) fix-tsfpq-20090210
    2009-12-17 Derrick Brashear  (925) tsm41-makefile-fix-20090609
    2009-12-17 Derrick Brashear  (924) Search for the Linux version in the correct header
    2009-12-17 Derrick Brashear  (922) rx-user-socket-buffer-sizes-20090110
    2009-12-17 Derrick Brashear  (921) salvager-no-chdir-20081108
    2009-12-17 Derrick Brashear  (976) asm unexecutable stack
    2009-12-17 Derrick Brashear  (920) rx-rdwr-avoid-free-null-packet-20081026
    2009-12-17 Derrick Brashear  (919) rx-change-packet-allocation-calculation-20080925
    2009-12-17 Derrick Brashear  (918) rx-buffer-allocation-corrected-20080813
    2009-12-17 Derrick Brashear  (917) Move afscell to platform/DARWIN
    2009-12-17 Derrick Brashear  (916) macos-afscell-configurator-20080423
    2009-12-17 Derrick Brashear  (915) Move end label into correct position
    2009-12-17 Derrick Brashear  (914) viced: set volume sync data in bulk status rpcs
    2009-12-17 Derrick Brashear  (912) vos-move-avoid-spurious-unlock-20080424
    2009-12-17 Derrick Brashear  (977) Linux: Fix lock ordering
    2009-12-17 Derrick Brashear  (911) pioctl-settoken-malloc-fail-check-20080206
    2009-12-17 Derrick Brashear  (910) macos panic decoder should handle 64 bit kernel in 32 bit mode
    2009-12-17 Derrick Brashear  (909) redhat spec dkms don't strip modules
    2009-12-16 Andrew Deason     (908) Dump all hostFlags in hosts.dump
    2009-12-01 Andrew Deason     (882) Correct duplicate special inodes while salvaging
    2009-12-01 Michael Meffie    (877) shutdown_icl returns void

## Resolved Tickets

Here is a list of tickets that have been resolved since December 1, 2009:

    ticket # state     created       title
      20954: resolved  Aug 19, 2005  Canonical vs. Local paths
      22431: resolved  Oct 17, 2005  problem with chkconfig in afs init for RHEL Linux. (1.4.0rc5)
      23321: resolved  Nov 20, 2005  more cleanup for rx global lock
      23765: resolved  Nov 29, 2005  OpenAFS 1.4.0 fileserver hangs writing to qlogic fibre disk on GNU/Linux server
      23995: resolved  Dec 06, 2005  Suggested additions to RPM spec
      25412: resolved  Jan 13, 2006  patch to reset volume usage data at midnight in current timezone
      25966: resolved  Jan 27, 2006  Using the Solaris 10 Kerberos support with Openafs-1.4.1-rc5 aklog
      30632: resolved  Apr 21, 2006  speed up namei volume operations by grouping fsyncs
      34561: resolved  Jun 28, 2006  rewrite linux kernel configuration tests
      34939: resolved  Jul 05, 2006  proposed patch to resolve compiler warnings against des and other functions
      48353: resolved  Dec 04, 2006  Problem with afs_NewVCache
      55026: resolved  Feb 26, 2007  Re: [OpenAFS] little install problem...
      58003: resolved  Mar 30, 2007  bucoord/volstub.c patch
      77905: resolved  Nov 20, 2007  solaris10 aklog errors out on crossrealm
      80036: resolved  Dec 11, 2007  cvs build issues on solaris
     104471: resolved  Jun 24, 2008  fileserver crash in 1.4.7 on solaris 10
     117659: resolved  Sep 26, 2008  Compilation of osi_vfsops.c fails on rececent OpenSolaris
     119118: resolved  Oct 03, 2008  Compilation of afs_nfsdisp.c fails on recent Opensolaris
     123448: resolved  Oct 22, 2008  'Invalid argument' when copying file larger than cache (OpenSolaris amd64/1.4.8pre2)
     123577: resolved  Oct 30, 2008  patch to remove chdir() from salvage so cores are not left in /vicep*
     124087: resolved  Jan 05, 2009  namei_icreate/gettag race leads to 'CopyOnWrite failed'
     124097: resolved  Jan 09, 2009  h_Enumerate found <count> of <hostCount> hosts
     124456: resolved  Mar 10, 2009  linux vm system hang
     124483: resolved  Mar 17, 2009  DAFS: volume header not properly cleared
     124484: resolved  Mar 17, 2009  DAFS: volumes not salvaged when the first access is from the volserver
     124485: resolved  Mar 17, 2009  DAFS: fileserver cores if restarted during start-up
     124486: resolved  Mar 17, 2009  DAFS: fileserver hangs on shutdown
     124490: resolved  Mar 17, 2009  DAFS: volume moves within a server cause volheaders to be out of sync
     124491: resolved  Mar 17, 2009  DAFS: salvageserver race condition in JudgeEntry
     124538: resolved  Mar 25, 2009  Incorrect ctime usages
     124630: resolved  Apr 15, 2009  starting afsd on large partitions
     124755: resolved  May 09, 2009  Tone down byte range lock warning on Linux
     124766: resolved  May 12, 2009  OpenAFS fails the Connectathon lock tests
     124888: resolved  May 31, 2009  volid-unsigned-int32-20090323 breaks integer cast functions
     125110: resolved  Jul 16, 2009  butc crash
     125113: resolved  Jul 16, 2009  Fedora 11 RPM - compile_et conflict
     125120: resolved  Jul 17, 2009  1.4.11 build error on rhel3
     125155: resolved  Jul 24, 2009  pam_afs.so broken at least in 1.4.11 RHEL 5 Packages
     125156: resolved  Jul 24, 2009  Running bos -noauth requires client to be configured
     125197: resolved  Aug 07, 2009  dkms kernel modules missing debug symbols
     125365: resolved  Sep 04, 2009  ZFS cache usage tracking
     125430: resolved  Sep 25, 2009  Documentation error
     125471: resolved  Oct 06, 2009  Bus errors when writing large mmap'ed file
     125472: resolved  Oct 07, 2009  crash in 1.5.60 demand-attach volserver
     125479: resolved  Oct 08, 2009  volserver race condition in VolMonitor
     125489: resolved  Oct 13, 2009  Makefiles don't work with -j2
     125589: resolved  Nov 04, 2009  clear_inode panics
     125596: resolved  Nov 05, 2009  1.4.11 cache manager panic on solaris
     125767: resolved  Dec 02, 2009  configure script should check for math.h
