---
title: OpenAFS Newsletter, Volume 3, Issue 7, July 2011
---

# OpenAFS Newsletter, Volume 3, Issue 7, July 2011

Welcome to the July issue of the OpenAFS newsletter. This newsletter
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

OpenAFS 1.6.0pre7 was released. It is available from
[http://www.openafs.org/release/openafs-1.6.0pre7.html](http://www.openafs.org/release/openafs-1.6.0pre7.html). 1.6.0pre7
includes support for the recently released Mac OS 10.7 (Lion).

OpenAFS 1.4.14.1 was released. It is available from
[http://www.openafs.org/dl/openafs/1.4.14.1/](http://www.openafs.org/dl/openafs/1.4.14.1/).

Volunteering time to OpenAFS doesn't take much time. Here is a list of
small tasks that would help the project:
[http://openafs-wiki.stanford.edu/AFSLore/afslore/tinysimpletasks/](http://openafs-wiki.stanford.edu/AFSLore/afslore/tinysimpletasks/)

Steven Jenkins has taken over the care and feeding of the AFS-Monitor Perl
module. Any patches should be sent to Steven. A git repo is set up at
[http://github.com/stevenjenkins/AFS-Monitor](http://github.com/stevenjenkins/AFS-Monitor)

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

A -04 revision is now in the proofreading stage.

\--Ed. (Paraphrased from Tom)

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

Call for consensus.

\--Andrew Deason

### AFS-3 Extensible XDR Discriminated Union Primitive Type

Status: Third Draft

Last Update: June 2, 2011

[http://datatracker.ietf.org/doc/draft-keiser-afs3-xdr-union/](http://datatracker.ietf.org/doc/draft-keiser-afs3-xdr-union/)

I pushed a new revision of draft-keiser-afs3-xdr-union:

[http://tools.ietf.org/html/draft-keiser-afs3-xdr-union-02](http://tools.ietf.org/html/draft-keiser-afs3-xdr-union-02)

This revision incorporates the following two changes:

- modify section on error handling (3.4.1) to make length mismatches a fatal
error
- add a "use case" section (1.1) to discuss trade-offs associated with using
this type

Any comments are welcome.

\--Tom

The -03 draft should be published soon.

\--Ed.

### AFS-3 Rx RPC XDR Primitive Type Definitions

Status: First Draft

Last Update: June 2, 2011

[http://tools.ietf.org/html/draft-keiser-afs3-xdr-primitive-types](http://tools.ietf.org/html/draft-keiser-afs3-xdr-primitive-types)

I have published a new i-d that attempts to define the xdr primitives used in our existing RPC-L grammar:

- afs\_(u)int{8,16,32,64}
- (unsigned) char
- (unsigned) short
- afsUUID

Please see
[http://tools.ietf.org/html/draft-keiser-afs3-xdr-primitive-types-00](http://tools.ietf.org/html/draft-keiser-afs3-xdr-primitive-types-00). Comments
are hereby solicited.

Cheers,

\--Tom

## Projects

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Derrick Brashear added support for section 3 man pages.  The -creation and
\-lastupdate flags were added to the __vos restore__ man page.

Kodiak Firesmith and Chas Williams generated mobile-friendly PDF's of the
OpenAFS documentation. These files are available at

    /afs/cmf/users/chas/public/auarf000.epub
    /afs/cmf/users/chas/public/auarf000.mobi
    /afs/cmf/users/chas/public/auarf000.pdf

Chas submitted Gerrit \#4887 to add mobi and epub support for the User,
quickstart, and Administrator Guides.

Jeffrey Altman updated the scripts for generating PDF documentation to use
xsltproc and fop.

### \*BSD Support

Project Contacts:

- Ben Kaduk <kaduk@mit.edu>

A bug was fixed in the FreeBSD code by avoiding an extra flush.

### User-space cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

The libuafs perl bindings in gerrit 2048 have been merged into the tree,
so you should be able to build them if you pull from the OpenAFS master
branch, and have SWiG installed. It may see some changes to fix some
cross-platform issues, but it should be likely to work on at least Linux
and OS X. The "afsload" testing/simulation tool that I presented on during
the 2011 Best Practices Workshop was submitted in gerrit 4906 and has also
been merged into the tree. You can find it in src/libuafs/afsload/ on the
master branch.

An experimental Firefox plugin for browsing AFS via libuafs has been
submitted in gerrit 5039.

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Kerberos v5 and multiple encryption types - July 2010
- Per-File ACLs - August 2010
- Rx OSD integration & Raw Vicep Access in Clients - November 2010
- Mac OS X OpenAFS Preference Pane - February 2011
- Virtual Machine Images - March 2011
- S3 Front-end for AFS - April 2011
- Extended Callback Information - June 2011

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Patches merged into the master branch:
    Month   Number of Commits
    2011-07  101 (Partial month)
    2011-06  122
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

    Patches merged into the stable 1.6.x branch:
    Month   Number of Commits
    2011-07   62 (Partial month)
    2011-06   15
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
    2011-07    1 (Partial month)
    2011-06    4
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

### Patches merged into the master branch

    Date       Committer        Change# Description
    2011-07-23 Simon Wilkinson   (5081) ubik: ServerInitCommon is an internal function...
    2011-07-23 Simon Wilkinson   (5076) ptserver: Don't print undefined value
    2011-07-23 Simon Wilkinson   (5077) libcmd: Don't store values that we don't need
    2011-07-23 Simon Wilkinson   (5078) libcmd: Don't increment array then discard result
    2011-07-23 Simon Wilkinson   (5080) bozo: Don't initialise variables unecessarily
    2011-07-23 Simon Wilkinson   (5079) viced.c: Don't store results of reads unecessarily
    2011-07-22 Andrew Deason     (5059) libafs: Remove unused volume "states" flags
    2011-07-22 Derrick Brashear  (5069) aklog: check ccache errors in get_user_realm
    2011-07-22 Derrick Brashear  (5065) macos: avoid KLRenewInitialTickets crash in Lion
    2011-07-22 Andy Cobaugh      (5026) rpm: remove postinstall message from openafs-client
    2011-07-22 Jeffrey Altman    (5062) Windows: do not leak space allocation
    2011-07-22 Jeffrey Altman    (5061) Windows: smb_ReceiveNTTranCreate path not found
    2011-07-22 Jeffrey Altman    (5055) Windows: improve shutdown time
    2011-07-22 Jeffrey Altman    (5054) Windows: cm_daemonCheckOfflineVol fix
    2011-07-22 Jeffrey Altman    (5053) Windows: Add shutdown event log message
    2011-07-22 Jeffrey Altman    (5052) Window: breakout CM error codes into separate header
    2011-07-22 Andrew Deason     (4899) afsd: Add the -rxmaxfrags option
    2011-07-22 Benjamin Kaduk    (5058) FBSD: in libafs, define LIBAFSNONFS
    2011-07-22 Derrick Brashear  (5066) macos: krb5_524 is uselessly stubbed
    2011-07-21 Derrick Brashear  (5056) redhat: support epel yum configs in mockbuild
    2011-07-20 Andrew Deason     (5048) Revert "afs: Use 64-bit inode numbers"
    2011-07-19 Russ Allbery      (5044) Add additional NEWS entries for 1.6.0pre5 through 1.6.0pre7
    2011-07-18 Benjamin Kaduk    (5042) FBSD: update to using bsd.kmod.mk
    2011-07-18 Benjamin Kaduk    (5040) libafs: switch to hardcoded source names with CRULE
    2011-07-18 Benjamin Kaduk    (5034) FBSD: use better casts in vop_advlock
    2011-07-18 Simon Wilkinson   (5031) vlserver: Handle logging of non-rxkad classes
    2011-07-18 Simon Wilkinson   (5030) tests: Fix error in man check specification
    2011-07-18 Simon Wilkinson   (5029) tests: Add tests for the vlserver
    2011-07-17 Benjamin Kaduk    (5036) FBSD: Use correct path for ufsmount.h include
    2011-07-17 Benjamin Kaduk    (5035) FBSD: cast pointers appropriately
    2011-07-17 Benjamin Kaduk    (5033) FBSD: Remove include directive for nonexistent file
    2011-07-17 Simon Wilkinson   (5037) Fix broken make dest rules
    2011-07-17 Andrew Deason     (5038) UKERNEL: Avoid using parameters named "new"
    2011-07-17 Michael Meffie    (5020) audit: remove uneeded strncpy
    2011-07-15 Garrett Wollman   (5025) util: try again to satisfy the gatekeepers
    2011-07-15 Garrett Wollman   (5005) util: clean up two #ifs
    2011-07-15 Simon Wilkinson   (5028) Make --enable-pthreaded-ubik do what it claims
    2011-07-15 Simon Wilkinson   (5027) Fix pthreaded ubik dest and install rules
    2011-07-14 Andrew Deason     (5023) util: Include pthread.h in afsutil_prototypes.h
    2011-07-14 Benjamin Kaduk    (5022) Install afszcm.cat for i386_fbsd make dest
    2011-07-14 Derrick Brashear  (5013) volser: remove pragma requiring ultranew gcc
    2011-07-14 Marc Dionne       (5012) Linux: remove unused variable
    2011-07-14 Simon Wilkinson   (5003) rxkad: Suppress warnings for ticket5.c
    2011-07-14 Michael Meffie    (4975) tests: fix cmd test case
    2011-07-14 Simon Wilkinson   (5002) volser: fix set-but-unused variable warning
    2011-07-14 Jeffrey Altman    (4985) Windows: not safe to dereference before locking
    2011-07-14 Simon Wilkinson   (4987) libafs: Remove unused NAT markeddown code
    2011-07-14 Simon Wilkinson   (5004) Add PERLUAFS to libuafs's git ignore
    2011-07-13 Simon Wilkinson   (5000) volser: Actually return errors from ListOneVolume
    2011-07-13 Jeffrey Altman    (4954) Windows: ChangeLog for 1.5.9907
    2011-07-13 Simon Wilkinson   (5001) vol: Initialise list before error exit when cloning
    2011-07-13 Simon Wilkinson   (4999) Mark nearInode as unused
    2011-07-13 Simon Wilkinson   (4988) libafs: Remove unused DNLC LRU code
    2011-07-13 Simon Wilkinson   (4998) Don't split int64s when we don't need to
    2011-07-13 Simon Wilkinson   (4997) afsio: Remove unused 'code' value
    2011-07-13 Simon Wilkinson   (4989) libafs: Fix statistics for PrefetchFromTape pioctl
    2011-07-13 Simon Wilkinson   (4996) uss: Remove unused variables
    2011-07-13 Simon Wilkinson   (4995) scout: Remove unused error codes
    2011-07-13 Simon Wilkinson   (4994) libadmin: Remove unused error codes
    2011-07-13 Simon Wilkinson   (4990) libafs: Fix warnings in PPrefetchFromTape
    2011-07-13 Simon Wilkinson   (4991) libafs: Remove support for length optimisation
    2011-07-13 Simon Wilkinson   (4993) bozo: Remove unused error codes assignments
    2011-07-13 Simon Wilkinson   (4992) afsmonitor: Fix set-but-unused variable warnings
    2011-07-13 Garrett Wollman   (4966) util: introduce a common interface for setting thread names
    2011-07-13 Simon Wilkinson   (4984) Add make dist and make srpm targets
    2011-07-13 Simon Wilkinson   (4983) rpms: Use git version information
    2011-07-12 Ken Dreyer        (4925) Red Hat: update build script for newer Fedora versions
    2011-07-12 Derrick Brashear  (4973) macos: note additional vfs features
    2011-07-12 Derrick Brashear  (4971) macos: fix shlib link list
    2011-07-12 Antoine Verheijen (4958) Remove pre-existing assert macro in hcrypto header.
    2011-07-12 Michael Meffie    (4965) salvager: do not redefine SalvageVolumeGroup
    2011-07-12 Andrew Deason     (4921) afs: Use 64-bit inode numbers
    2011-07-12 Simon Wilkinson   (4970) rpms: Fix handling of x86 architectures
    2011-07-12 Simon Wilkinson   (4969) rpms: Fix our %version handling
    2011-07-12 Michael Meffie    (4968) salvager: check namei linktable header magic
    2011-07-12 Jeffrey Altman    (4967) Windows: always open dscp in smb_ReceiveNTTranCreate
    2011-07-11 Garrett Wollman   (4950) viced: If platform supports setting a thread title, do so
    2011-07-11 Jeffrey Altman    (4964) Windows: Move file server lock releases to daemon
    2011-07-10 Ken Dreyer        (4926) Red Hat: use repoquery to find kernels in build script
    2011-07-10 Antoine Verheijen (4956) OpenBSD: Add <sys/queue.h> header for <sys/lockf.h>
    2011-07-10 Garrett Wollman   (4959) viced: indent nested preprocessor directives
    2011-07-10 Jeffrey Altman    (4963) rx: prevent connection channel assignment race
    2011-07-09 Jeffrey Altman    (4961) windows: include cmp_Cmd_Ref_3_en_US component
    2011-07-09 Jeffrey Altman    (4955) Windows: out of order lock smb v3 locking
    2011-07-09 Andrew Deason     (2048) Add AFS::ukernel libuafs perl bindings
    2011-07-09 Andrew Deason     (4906) Add afsload
    2011-07-09 Andrew Deason     (3898) doc: Add support for section 3 man pages
    2011-07-09 Andrew Deason     (3902) Add documentation for AFS::ukernel
    2011-07-07 Jeffrey Altman    (4924) Windows: Improve logging for StoreMini and cm_BufWrite
    2011-07-07 Jeffrey Altman    (4923) Windows: Refactor cm_Unlock*() to avoid code duplication
    2011-07-07 Jeffrey Altman    (4922) Windows: Do not probe new servers from cm_UpdateVolumeLocation
    2011-07-07 Andrew Deason     (4920) afs: Consolidate afs_calc_inum
    2011-07-07 Andrew Deason     (4919) afs: Use afs_calc_inum everywhere
    2011-07-07 Andrew Deason     (4902) afs: Use cell for md5 inode numbers
    2011-07-06 Andrew Deason     (4905) uss: Suppress more warnings from lex.yy.c
    2011-07-06 Andrew Deason     (4901) afs: Ensure afs_calc_inum yields nonzero ino
    2011-07-06 Anders Kaseorg    (4843) Treat Linux 3 as Linux 2.6
    2011-07-06 Andrew Deason     (4904) Add a few missing .gitignore entries
    2011-07-02 Andrew Deason     (4903) vol: Don't always FDH_REALLYCLOSE on linktable ops
    2011-07-02 Andrew Deason     (4900) DAFS: Do not clear salv state on fssync salvage
    2011-07-01 Chas Williams - CONTRACTOR (4887) doc: epub and mobi support
    2011-06-30 Andrew Deason     (4889) Remove nonsensical bozon-lock defines
    2011-06-30 Andrew Deason     (4896) SOLARIS: Granular multiPage detection
    2011-06-30 Andrew Deason     (4888) Remove support for Solaris pre-8
    2011-06-30 Jeff Blaine       (4897) Change wiki ref to wiki.openafs.org from stanford.edu
    2011-06-28 Jeff Blaine       (4850) Styling tweak for generated HTML man pages
    2011-06-28 Jeff Blaine       (4846) Introduce TAP tests of man pages for command_subcommand
    2011-06-28 Jeffrey Altman    (4890) rx: race in rx_multi processing
    2011-06-28 Jeff Blaine       (4827) Change -n to -dryrun for backup subcommands
    2011-06-28 Jeffrey Altman    (4754) vos: refactor ListAddrs
    2011-06-27 Jeffrey Altman    (4891) Windows: MergeStatus before SyncOpDone
    2011-06-25 Jeffrey Altman    (4884) Windows: TRANS2_FIND_FIRST2 for _._AFS_IOCTL_._
    2011-06-25 Jeffrey Altman    (4886) Windows: Fix SMB_COM_NEGOTIATE for MS11-043
    2011-06-23 Derrick Brashear  (4837) Revert "Rx: When call receive is done, send ack all packet"
    2011-06-22 Andrew Deason     (4875) Build a separate copy of vlib for dasalvager
    2011-06-22 Chas Williams - CONTRACTOR (4822) doc: fix dependencies
    2011-06-22 Chas Williams - CONTRACTOR (4831) doc: fix some broken link specifications
    2011-06-22 Chas Williams - CONTRACTOR (4821) doc: prefer fop to generate pdf from docbook
    2011-06-22 Jeffrey Altman    (4879) roken: add search.h to .gitignore
    2011-06-22 Andrew Deason     (4874) DAFS: Do not attach a specialStatus'd vol
    2011-06-22 Andrew Deason     (4876) salvager: Clear summary in RecordHeader
    2011-06-22 Andrew Deason     (4878) dir: Remove extraneous printf from Create
    2011-06-22 Andrew Deason     (4877) dir: Fix DRead
    2011-06-22 Andrew Deason     (4873) vol: Do not overwrite specialStatus in attach2
    2011-06-22 Simon Wilkinson   (4864) rx: Make clock_Add correctly add to itself
    2011-06-22 Simon Wilkinson   (4861) rx: Compute smoothed RTT per call, not per peer.
    2011-06-22 Simon Wilkinson   (4869) rx: Exit fast restart on non-duplicate ACK
    2011-06-22 Simon Wilkinson   (4868) rx: Don't limit the # of packets sent in recovery
    2011-06-22 Simon Wilkinson   (4867) rx: Don't wait for TQ busy when entering recovery
    2011-06-22 Simon Wilkinson   (4866) rx: Enter loss recovery when we retransmit
    2011-06-22 Simon Wilkinson   (4865) rx: Add Karn-style backoffs to RX retransmits
    2011-06-22 Simon Wilkinson   (4863) rx: Remove resending logic into its own function
    2011-06-22 Simon Wilkinson   (4862) rx: Change the way that the RTT timer is applied
    2011-06-21 Simon Wilkinson   (4872) rx: Make testclient build on Unix
    2011-06-21 Simon Wilkinson   (4871) rx: Reverse the consumption order of idle queue
    2011-06-21 Derrick Brashear  (4870) macos: package shared libraries
    2011-06-20 Simon Wilkinson   (4860) rx: Remove incorrect backoff code
    2011-06-20 Simon Wilkinson   (4859) rx: Account for delayed ACKS when computing RTO
    2011-06-20 Simon Wilkinson   (4858) rx: Make rx_softAckDelay & rx_lastAckDelay private
    2011-06-20 Jeff Blaine       (4852) Documented vos restore -creation and -lastupdate
    2011-06-20 Ken Dreyer        (4844) Enable -afsdb in the Red Hat packages.
    2011-06-20 Benjamin Kaduk    (4849) FBSD: do not install kdump
    2011-06-20 Benjamin Kaduk    (4847) FBSD: do not FlushAllVCaches
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

### Patches merged into the stable 1.6.x branch

    Date       Committer        Change# Description
    2011-07-22 Derrick Brashear  (5072) aklog: check ccache errors in get_user_realm
    2011-07-22 Derrick Brashear  (5071) macos: avoid KLRenewInitialTickets crash in Lion
    2011-07-22 Derrick Brashear  (5070) macos: krb5_524 is uselessly stubbed
    2011-07-22 Derrick Brashear  (5068) Red Hat: update build script for newer Fedora versions
    2011-07-22 Derrick Brashear  (5067) redhat: support epel yum configs in mockbuild
    2011-07-19 Russ Allbery      (5045) Add additional NEWS entries for 1.6.0pre5 through 1.6.0pre7
    2011-07-15 Benjamin Kaduk    (5024) Install afszcm.cat for i386_fbsd make dest
    2011-07-14 Derrick Brashear  (5019) Revert "windows: include cmp_Cmd_Ref_3_en_US component"
    2011-07-14 Derrick Brashear  (5011) make 1.6.0pre7
    2011-07-14 Derrick Brashear  (5010) Windows: ChangeLog for 1.5.9907
    2011-07-14 Derrick Brashear  (5009) Add make dist and make srpm targets
    2011-07-14 Derrick Brashear  (5008) rpms: Use git version information
    2011-07-14 Derrick Brashear  (5007) vol: Initialise list before error exit when cloning
    2011-07-14 Derrick Brashear  (5015) volser: remove pragma requiring ultranew gcc
    2011-07-14 Derrick Brashear  (5006) volser: Actually return errors from ListOneVolume
    2011-07-14 Jeffrey Altman    (5014) Windows: not safe to dereference before locking
    2011-07-13 Derrick Brashear  (4986) Revert "rx: prevent connection channel assignment race"
    2011-07-13 Derrick Brashear  (4981) rx: prevent connection channel assignment race
    2011-07-13 Derrick Brashear  (4982) macos: note additional vfs features
    2011-07-13 Derrick Brashear  (4980) OpenBSD: Add <sys/queue.h> header for <sys/lockf.h>
    2011-07-13 Derrick Brashear  (4979) Red Hat: use repoquery to find kernels in build script
    2011-07-13 Derrick Brashear  (4977) Windows: always open dscp in smb_ReceiveNTTranCreate
    2011-07-13 Derrick Brashear  (4976) salvager: check namei linktable header magic
    2011-07-09 Jeffrey Altman    (4962) windows: include cmp_Cmd_Ref_3_en_US component
    2011-07-09 Jeffrey Altman    (4960) Windows: out of order lock smb v3 locking
    2011-07-09 Jeffrey Altman    (4953) Windows: Improve logging for StoreMini and cm_BufWrite
    2011-07-09 Jeffrey Altman    (4952) Windows: Refactor cm_Unlock*() to avoid code duplication
    2011-07-09 Jeffrey Altman    (4951) Windows: Do not probe new servers from cm_UpdateVolumeLocation
    2011-07-09 Derrick Brashear  (4949) vol: Don't always FDH_REALLYCLOSE on linktable ops
    2011-07-09 Derrick Brashear  (4948) DAFS: Do not clear salv state on fssync salvage
    2011-07-09 Andrew Deason     (4927) SOLARIS: Granular multiPage detection
    2011-07-09 Derrick Brashear  (4946) Revert "Rx: When call receive is done, send ack all packet"
    2011-07-09 Derrick Brashear  (4945) DAFS: Do not attach a specialStatus'd vol
    2011-07-09 Derrick Brashear  (4944) salvager: Clear summary in RecordHeader
    2011-07-09 Derrick Brashear  (4943) Build a separate copy of vlib for dasalvager
    2011-07-09 Derrick Brashear  (4942) vol: Do not overwrite specialStatus in attach2
    2011-07-09 Derrick Brashear  (4941) rx: Exit fast restart on non-duplicate ACK
    2011-07-09 Derrick Brashear  (4940) rx: Don't limit the # of packets sent in recovery
    2011-07-09 Derrick Brashear  (4939) rx: Don't wait for TQ busy when entering recovery
    2011-07-09 Derrick Brashear  (4938) rx: Enter loss recovery when we retransmit
    2011-07-09 Derrick Brashear  (4937) rx: Add Karn-style backoffs to RX retransmits
    2011-07-09 Derrick Brashear  (4936) rx: Make clock_Add correctly add to itself
    2011-07-09 Derrick Brashear  (4935) rx: Remove resending logic into its own function
    2011-07-09 Derrick Brashear  (4934) rx: Don't let timeouts force fast recovery
    2011-07-09 Derrick Brashear  (4933) rx: complete fix for starting rexmit timers
    2011-07-09 Derrick Brashear  (4932) RX: rxi_PrepareSendPacket drops call lock; WaitforTQ required
    2011-07-09 Derrick Brashear  (4931) rx: Fix resend accounting
    2011-07-09 Derrick Brashear  (4930) rx: Don't maintain maxSerial
    2011-07-09 Derrick Brashear  (4929) Rx: Consolidate wait for tq busy and make its use uniform
    2011-07-08 Derrick Brashear  (4947) Change wiki ref to wiki.openafs.org from stanford.edu
    2011-07-07 Derrick Brashear  (4918) rx: Change the way that the RTT timer is applied
    2011-07-07 Derrick Brashear  (4917) rx: Use a structure for the xmit list
    2011-07-07 Derrick Brashear  (4916) rx: Compute smoothed RTT per call, not per peer.
    2011-07-07 Derrick Brashear  (4915) rx: Reorganise transmit queue walk
    2011-07-07 Derrick Brashear  (4914) rx: Add RX_CALL_ACKALL_SENT flag and rxi_SendAck processing
    2011-07-07 Derrick Brashear  (4913) rx: do not rxi_AckAll for one data packet call
    2011-07-07 Derrick Brashear  (4912) rx: Reverse the consumption order of idle queue
    2011-07-07 Derrick Brashear  (4911) rx: Remove incorrect backoff code
    2011-07-07 Derrick Brashear  (4910) rx: Account for delayed ACKS when computing RTO
    2011-07-07 Derrick Brashear  (4909) rx: Make rx_softAckDelay & rx_lastAckDelay private
    2011-07-07 Derrick Brashear  (4908) Documented vos restore -creation and -lastupdate
    2011-07-07 Anders Kaseorg    (4907) Treat Linux 3 as Linux 2.6
    2011-06-28 Jeffrey Altman    (4895) Windows: MergeStatus before SyncOpDone
    2011-06-28 Jeffrey Altman    (4894) Windows: TRANS2_FIND_FIRST2 for _._AFS_IOCTL_._
    2011-06-28 Jeffrey Altman    (4893) Windows: Fix SMB_COM_NEGOTIATE for MS11-043
    2011-06-28 Jeffrey Altman    (4892) Windows: shell extension is multithreaded
    2011-06-20 Benjamin Kaduk    (4855) Unbreak make dest for FBSD
    2011-06-20 Benjamin Kaduk    (4853) FBSD: do not install kdump
    2011-06-20 Derrick Brashear  (4856) Enable -afsdb in the Red Hat packages.
    2011-06-20 Benjamin Kaduk    (4854) FBSD: do not FlushAllVCaches
    2011-06-20 Benjamin Kaduk    (4848) Also install afszcm.cat for i386_fbsd
    2011-06-06 Derrick Brashear  (4794) doc: let configure find the XML tools if possible
    2011-06-06 Derrick Brashear  (4793) kvno invocation correction, language cleanup, afs/cell principal preferred
    2011-06-06 Derrick Brashear  (4792) vos: print_addrs never receives multi-homed addrs
    2011-06-06 Derrick Brashear  (4791) xstat: cope with different size timeval structures
    2011-06-05 Derrick Brashear  (4786) linux: rpm: Fix SELinux attributes on /afs when installing openafs-client package
    2011-06-05 Derrick Brashear  (4785) Enable gencat for i386_fbsd_*

### Patches merged into the stable 1.4.x branch

    Date       Committer        Change# Description
    2011-07-10 Andrew Deason     (4928) SOLARIS: Granular multiPage detection
    2011-06-20 Andrew Deason     (4394) Fileserver: Don't sync every 10 seconds
    2011-06-07 Andrew Deason     (4436) afs: Avoid memory leak on recursive write flock
    2011-06-07 Andrew Deason     (4435) afs: Retry unlock after afs_StoreAllSegments
    2011-06-07 Andrew Deason     (4813) make bozo honor -rxbind correctly
