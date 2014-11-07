---
title: OpenAFS Newsletter, Volume 3, Issue 6, June 2011
---

# OpenAFS Newsletter, Volume 3, Issue 6, June 2011

Welcome to the June issue of the OpenAFS newsletter. This newsletter
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

OpenAFS 1.6.0pre6 was released.  It's available at
 [http://www.openafs.org/release/openafs-1.6.0pre6.html](http://www.openafs.org/release/openafs-1.6.0pre6.html)

The first AFS protocol enhancement draft is in the Independent Submission
Editors queue.  Three reviewers have been chosen.  The draft is undergoing
review.  From there, it then goes to the IESG, before making it in to the
RFC Editor queue.

## Events

### Annual Best Practices Workshop

Registration for the AFS & Kerberos Best Practices Workshop 2011 is open.
It will be an on-line event held from June 13 to 17.  Sessions will be
recorded and available for 48 hours.

[http://workshop.openafs.org/afsbpw11/](http://workshop.openafs.org/afsbpw11/)

## AFS Protocol Standardization

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://lists.openafs.org/mailman/listinfo/afs3-standardization](http://lists.openafs.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://datatracker.ietf.org/doc/draft-brashear-afs3-pts-extended-names/](http://datatracker.ietf.org/doc/draft-brashear-afs3-pts-extended-names/)

Status: Tenth Draft - Consensus reached

Last Update: March 7, 2011

This draft is in the RFC Editor's queue.

### AFS Callback Extensions

[http://datatracker.ietf.org/doc/draft-benjamin-extendedcallbackinfo/](http://datatracker.ietf.org/doc/draft-benjamin-extendedcallbackinfo/)

Status: Second draft - Waiting on RPC refresh

Last Update: April 26, 2011

I published an update to this draft during the 2011 Hackathon.  Another
draft will be forthcoming.

\--Matt

### RXGK

[http://datatracker.ietf.org/doc/draft-wilkinson-afs3-rxgk/](http://datatracker.ietf.org/doc/draft-wilkinson-afs3-rxgk/)

Status: Expired (First draft)

Last Update: Jan 9, 2010

An updated draft will be published shortly.

\--Simon Wilkinson

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

- minor updates to Rx grammar, esp. AssertExtendLock
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

Status: Third Draft

Last Update: May 31, 2011

draft-deason-afs3-type-time-02 has been posted and is available at

[http://datatracker.ietf.org/doc/draft-deason-afs3-type-time/](http://datatracker.ietf.org/doc/draft-deason-afs3-type-time/)

I apologize for the delay; this has been sitting on my hard drive for a
few weeks and I thought I had submitted it. The only thing changed
should be the names of the types as discussed. I haven't included any
new paragraph per the discussions with the ISE because honestly I am
rather confused as to what is going on there and who/what we are waiting
on.

\--Andrew Deason

### AFS-3 Extensible XDR Discriminated Union Primitive Type

Status: Third Draft

Last Update: June 2, 2011

[http://datatracker.ietf.org/doc/draft-keiser-afs3-xdr-union/](http://datatracker.ietf.org/doc/draft-keiser-afs3-xdr-union/)

A Use Case section was added. The changes were discussed at the 2011
Pittsburgh Hackathon.

## Projects

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Chas Williams has been updating the XML work-flow along with producing
documentation formats suitable for various ebook readers.  Ken Dreyer
updated the afsd man page to reflect that the -afsdb parameter now uses
DNS SRV records (RFC 5864).  Jeff Blaine has started cleaning up the to-do
list for documentation and some general cleanup.  Michael Meffie and Simon
Wilkinson added some features and corresponding documentation.

### \*BSD Support

Project Contacts:

- Ben Kaduk <kaduk@mit.edu>

The port of the cache manager to NetBSD 5 (and -current) was merged to the
master branch, a big milestone for that work.  The FreeBSD port was added
to the FreeBSD Ports Collection, which has given it higher visibility and
also elicited a few patches that have been contributed back to us.  These
include better support for FreeBSD's virtual network stack (VIMAGE)
feature, as well as an improvement to the cache manager build system to
not require a full kernel object directory.  Closer integration with the
standard way to build a FreeBSD kernel module remains a work in progress.

\--Ben

### Extended Callback Information

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

I've pushed updates for extended callbacks and byte-range locking to the
advlock\_7\_2 branch of openafs-rxgk.  This is YFS sponsored work.

\--Matt



### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Kerberos v5 and multiple encryption types - July 2010
- Per-File ACLs - August 2010
- Rx OSD integration & Raw Vicep Access in Clients - November 2010
- Mac OS X OpenAFS Preference Pane - February 2011
- Virtual Machine Images - March 2011
- User-space cache manager - March 2011
- S3 Front-end for AFS - April 2011

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Patches merged into the master branch:
    Month   Number of Commits
    2011-06   80 (Partial month)
    2011-05   64
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

    Patches merged into the stable 1.6.x branch:
    Month   Number of Commits
    2011-06    6 (Partial month)
    2011-05   48
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
    2011-06    3 (Partial month)
    2011-05    6
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

### Patches merged into the master branch

    Date       Committer        Change# Description
    2011-06-12 Marc Dionne       (4836) Linux: remove typedef from configure test comment
    2011-06-12 Michael Meffie    (4817) volinfo: fix false good magic line
    2011-06-11 Derrick Brashear  (4835) generated: take into account the things needed in master
    2011-06-11 Derrick Brashear  (4834) rxkad ticket5 function rewriting
    2011-06-11 Derrick Brashear  (4833) more death to des
    2011-06-10 Derrick Brashear  (4832) darwin armv6 and armv7 support
    2011-06-09 Jonathan Billings (4814) Linux: rpm: Update openafs.spec.in to include changes to installed files
    2011-06-09 Andrew Deason     (4830) volinfo: PrintFileNames is namei-only
    2011-06-09 Andrew Deason     (4829) libafs: memset dirHeader->hashTable
    2011-06-09 Andrew Deason     (4825) afsd: Fail gracefully on mtab open failure
    2011-06-09 Jonathan A. Kollasch (4828) Remove NetBSD-specific debugging statement
    2011-06-08 Jeff Blaine       (4826) Removed detail of prev. completed work found listed todo list
    2011-06-08 Jeffrey Altman    (4819) Windows: shell extension is multithreaded
    2011-06-07 Chas Williams - CONTRACTOR (4812) doc: fixes for the xsltproc -> fop -> pdf toolchain
    2011-06-07 Benjamin Kaduk    (4815) Also install afszcm.cat for i386_fbsd
    2011-06-07 Simon Wilkinson   (4796) rx: Reorganise transmit queue walk
    2011-06-07 Simon Wilkinson   (4797) rx: Don't maintain maxSerial
    2011-06-07 Jeffrey Altman    (4798) rx: Add RX_CALL_ACKALL_SENT flag and rxi_SendAck processing
    2011-06-07 Jeff Blaine       (4727) Added fstrace subcommand help to binary
    2011-06-07 Jeffrey Altman    (4799) rx: do not rxi_AckAll for one data packet call
    2011-06-07 Simon Wilkinson   (4809) ubik: Use supplied config directory in ugen
    2011-06-07 Simon Wilkinson   (4808) tests: Use a real IP address for the test cell
    2011-06-07 Simon Wilkinson   (4807) tests: Move code to add new DES keys to common
    2011-06-07 Simon Wilkinson   (4806) tests: Move common code to its own directory
    2011-06-07 Simon Wilkinson   (4811) vos: Add the -config option
    2011-06-07 Simon Wilkinson   (4810) cmd: Add support for disabling specific abbrevs
    2011-06-07 Jeffrey Altman    (4783) Windows: refactor fs acl funcs into fs_acl.c
    2011-06-07 Jeffrey Altman    (4778) Windows: Add GetFileInformationByHandleEx to fs_InAFS
    2011-06-07 Jeffrey Altman    (4777) Windows: refactor fs, symlink and fs_utils
    2011-06-06 Jeff Blaine       (4803) Remove completed tasks from todo list, add info about git/gerrit preference
    2011-06-06 Simon Wilkinson   (4805) src/tests: Fix a couple of build issues
    2011-06-06 Simon Wilkinson   (4804) rx: Make private things private
    2011-06-06 Simon Wilkinson   (4802) volinfo: Use new form of cmd_AddParamWithOffset
    2011-06-05 Simon Wilkinson   (4801) rxperf: -S takes an argument
    2011-06-05 Simon Wilkinson   (4800) rxperf: Build again
    2011-06-05 Simon Wilkinson   (4765) viced: Rationalise FS_STATS_DETAILED logging
    2011-06-05 Simon Wilkinson   (4716) viced: Remove old /vice/file/parms config file
    2011-06-05 Simon Wilkinson   (4768) usd: Move to using real 64bit quantities
    2011-06-05 Simon Wilkinson   (4767) usd: Make test program build again
    2011-06-05 Michael Meffie    (2986) xstat: cope with different size timeval structures
    2011-06-05 Simon Wilkinson   (4752) Linux CM: Use kernel allocator directly
    2011-06-05 Simon Wilkinson   (4749) libafs: Tidy up iovec allocation and trimming
    2011-06-05 Simon Wilkinson   (4748) Tidy up uio_t meaning
    2011-06-05 Jeff Blaine       (4740) kvno invocation correction, language cleanup, afs/cell principal preferred
    2011-06-05 Simon Wilkinson   (4757) vos: print_addrs never receives multi-homed addrs
    2011-06-05 Chas Williams - CONTRACTOR (4766) doc: let configure find the XML tools if possible
    2011-06-05 Simon Wilkinson   (4753) Linux CM: Update wait code
    2011-06-05 Simon Wilkinson   (4751) Linux CM: Use kernel allocator directly for events
    2011-06-05 Simon Wilkinson   (4750) Linux CM: Files don't need a page
    2011-06-05 Jonathan Billings (4763) linux: rpm: Fix SELinux attributes on /afs when installing openafs-client package
    2011-06-05 Benjamin Kaduk    (4760) Enable gencat for i386_fbsd_*
    2011-06-05 Michael Meffie    (4741) volinfo: accept -sizeonly for -sizeOnly
    2011-06-05 Michael Meffie    (4739) volinfo: accept vice partition id for -part option
    2011-06-05 Michael Meffie    (4738) volinfo: comments
    2011-06-05 Michael Meffie    (4737) volinfo: fix file size data type
    2011-06-05 Michael Meffie    (4736) volinfo: avoid exit on errors
    2011-06-05 Michael Meffie    (4735) volinfo: refactor mode variables
    2011-06-05 Michael Meffie    (4734) volinfo: refactor volume and vnode handling code
    2011-06-05 Michael Meffie    (4733) volinfo: refactor size counters
    2011-06-05 Michael Meffie    (4732) volinfo: refactor -sizeOnly printing
    2011-06-05 Simon Wilkinson   (4776) vlserver: Add flags to extent address entries
    2011-06-05 Simon Wilkinson   (4775) vlserver: Make space in extent block explicit
    2011-06-05 Simon Wilkinson   (4774) vlserver: Rationalise multi homed host processing
    2011-06-05 Simon Wilkinson   (4773) vlserver: Use correct memsets in vlentry convertor
    2011-06-05 Simon Wilkinson   (4772) vlserver: Clean up abort logic
    2011-06-05 Simon Wilkinson   (4771) vlserver: Use correct base value when replacing
    2011-06-05 Simon Wilkinson   (4770) vlserver: Rename errorcode to code
    2011-06-05 Simon Wilkinson   (4769) vlserver: Tidy up request counting
    2011-06-05 Simon Wilkinson   (4782) aklog: Remove Windows specific code from header
    2011-06-05 Simon Wilkinson   (4781) Build system: Move install definitions to include
    2011-06-05 Simon Wilkinson   (4780) ubik: Initialise global version lock before use
    2011-06-05 Michael Meffie    (4755) cmd: Reorder cmd_AddParmAtOffset arguments
    2011-06-04 Michael Meffie    (2878) xstat: print collection values in debug mode
    2011-06-04 Simon Wilkinson   (4496) fs: add support for relative ACL changes
    2011-06-02 Simon Wilkinson   (4745) dir: Prototype and function name cleanup
    2011-06-02 Simon Wilkinson   (4744) dir: Explicitly state buffer locations for data
    2011-06-02 Simon Wilkinson   (4764) doc: bos != vos
    2011-06-01 Simon Wilkinson   (4756) vos: Don't leak/overflow bulkaddrs
    2011-06-01 Christof Hanke    (4761) libafscp: fix install/dest in sep. Objectdir
    2011-06-01 Jonathan A. Kollasch (4661) Port cache manager to NetBSD-5 and NetBSD-current
    2011-05-27 Derrick Brashear  (4723) macos: bulkstat sysctl
    2011-05-27 Andrew Deason     (4729) make bozo honor -rxbind correctly
    2011-05-26 Christof Hanke    (4719) linux: add read_descriptor_t configure test and ifdef
    2011-05-26 Derrick Brashear  (4722) macos: bulkstat caller reference handling
    2011-05-26 Christof Hanke    (4718) autoconf: add test for typedef'd structs
    2011-05-26 Benjamin Kaduk    (4721) FBSD: VIMAGE support
    2011-05-25 Andrew Deason     (4710) tests: Make -flag the first parm in command-t
    2011-05-25 Andrew Deason     (4709) tests: Use symbolic constants in command-t
    2011-05-25 Andrew Deason     (4708) tests: Correctly pass string args in superuser-t
    2011-05-25 Simon Wilkinson   (4652) cmd: Add cmd_OptionAsUint
    2011-05-24 Andrew Deason     (4711) cmd: Fix parsing positional args
    2011-05-23 Jeffrey Altman    (4706) Windows: ChangeLog for 1.5.9906 (1.6.0pre6)
    2011-05-22 Antoine Verheijen (4671) Replace uintptr_t type cast with uintptrsz in afs_vcache.c
    2011-05-22 Simon Wilkinson   (4651) cmd: Include aliases in help output
    2011-05-22 Michael Meffie    (4696) volinfo: print namei filenames of index files
    2011-05-22 Michael Meffie    (4695) volinfo: remove code duplication in HandleVolumes
    2011-05-22 Michael Meffie    (4694) volinfo: fix volume aux totals output
    2011-05-22 Michael Meffie    (4693) volinfo: print errors to stderr
    2011-05-22 Michael Meffie    (4691) volinfo: fix size totals when saving inodes
    2011-05-22 Michael Meffie    (4690) doc: document volinfo -filenames option
    2011-05-22 Jeff Blaine       (4680) Added -dryrun
    2011-05-21 Michael Meffie    (4689) volinfo: fix -filenames option check
    2011-05-21 Derrick Brashear  (4686) dynroot: mark vnode types on dynroot vnodes
    2011-05-21 Derrick Brashear  (4677) macos: bulkstat redux
    2011-05-20 Andrew Deason     (4685) SOLARIS: Reset syscalls on mod_install failure
    2011-05-19 Andrew Deason     (4636) libafs: Implement unixuser RW locks
    2011-05-19 Andrew Deason     (4666) libafs: Always use anonymous VL connections
    2011-05-19 Jeff Blaine       (4678) Hide -noexecute in favor of -dryrun
    2011-05-19 Jeffrey Altman    (4676) auth: failback to afs3-vlserver for afs3-prserver
    2011-05-18 Jeffrey Altman    (4660) Windows: lock protected fields must be 32-bit
    2011-05-18 Jeffrey Altman    (4659) Windows: add lock assertions to cm_buf.c
    2011-05-18 Jeffrey Altman    (4658) Windows: test return from krb5_cc_start_seq_get
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

### Patches merged into the stable 1.6.x branch

    Date       Committer        Change# Description
    2011-06-06 Derrick Brashear  (4794) doc: let configure find the XML tools if possible
    2011-06-06 Derrick Brashear  (4793) kvno invocation correction, language cleanup, afs/cell principal preferred
    2011-06-06 Derrick Brashear  (4792) vos: print_addrs never receives multi-homed addrs
    2011-06-06 Derrick Brashear  (4791) xstat: cope with different size timeval structures
    2011-06-05 Derrick Brashear  (4786) linux: rpm: Fix SELinux attributes on /afs when installing openafs-client package
    2011-06-05 Derrick Brashear  (4785) Enable gencat for i386_fbsd_*
    2011-05-27 Andrew Deason     (4730) libafs: Do not osi_FlushPages for dirs
    2011-05-26 Derrick Brashear  (4726) linux: add read_descriptor_t configure test and ifdef
    2011-05-26 Derrick Brashear  (4725) autoconf: add test for typedef'd structs
    2011-05-26 Benjamin Kaduk    (4724) FBSD: VIMAGE support
    2011-05-25 Derrick Brashear  (4720) viced: note parms file deprecation
    2011-05-25 Derrick Brashear  (4717) macos: disable bulkstat
    2011-05-25 Derrick Brashear  (4713) des: generated files should not require objects needed in libdes
    2011-05-23 Jeffrey Altman    (4707) Windows: ChangeLog for 1.5.9906 (1.6.0pre6)
    2011-05-23 Antoine Verheijen (4705) Replace uintptr_t type cast with uintptrsz in afs_vcache.c
    2011-05-22 Derrick Brashear  (4703) make 1.6.0pre6
    2011-05-22 Derrick Brashear  (4702) libafs: Flush vcaches in afs_shutdown
    2011-05-22 Derrick Brashear  (4704) xdr symbol fallout
    2011-05-22 Derrick Brashear  (4701) doc: -afsdb uses SRV records
    2011-05-22 Derrick Brashear  (4699) macos: bulkstat redux
    2011-05-22 Derrick Brashear  (4698) dynroot: mark vnode types on dynroot vnodes
    2011-05-22 Derrick Brashear  (4697) volinfo: fix -filenames option check
    2011-05-21 Andrew Deason     (4687) SOLARIS: Reset syscalls on mod_install failure
    2011-05-19 Andrew Deason     (4682) rx: always use/protect the xdr routines in the kernel
    2011-05-19 Jeffrey Altman    (4681) auth: failback to afs3-vlserver for afs3-prserver
    2011-05-18 Jeffrey Altman    (4675) Windows: lock protected fields must be 32-bit
    2011-05-18 Jeffrey Altman    (4674) Windows: add lock assertions to cm_buf.c
    2011-05-18 Jeffrey Altman    (4673) Windows: test return from krb5_cc_start_seq_get
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

### Patches merged into the stable 1.4.x branch

    Date       Committer        Change# Description
    2011-06-07 Andrew Deason     (4436) afs: Avoid memory leak on recursive write flock
    2011-06-07 Andrew Deason     (4435) afs: Retry unlock after afs_StoreAllSegments
    2011-06-07 Andrew Deason     (4813) make bozo honor -rxbind correctly
    2011-05-22 Andrew Deason     (4648) libafs: Get rx conn ref with afs conn ref
    2011-05-22 Andrew Deason     (4649) libafs: Avoid using changing unixuser ticket data
    2011-05-22 Andrew Deason     (4688) SOLARIS: Reset syscalls on mod_install failure
    2011-05-17 Andrew Deason     (4667) unix blacklistonce should default to fail if no fid
    2011-05-05 Andrew Deason     (4622) avoid downward vcache pressure when entries are free
    2011-05-05 Andrew Deason     (4621) libafs: Use vcount, not maxvcount to trim vcaches
