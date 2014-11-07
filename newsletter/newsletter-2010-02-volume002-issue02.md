---
title: OpenAFS Newsletter, Volume 2, Issue 2, February 2010
---

# OpenAFS Newsletter, Volume 2, Issue 2, February 2010

Welcome to the tenth issue of the OpenAFS newsletter. This newsletter
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

There were two OpenAFS releases on February 1st. One was 1.5.71, and the
other was 1.4.12rc2. Due to some late breaking Linux issues with 1.5.71,
using that version on Linux is discouraged. Testing of 1.4.12rc2 and
future 1.5.x versions on all platforms is encouraged. Please report any
bugs.

Some questions about the timeline of IPv6 came up. IPv6 is part of the
RxTCP project which is planned for implementation in 2011. See
[http://www.openafs.org/roadmap.html](http://www.openafs.org/roadmap.html) for more details.

## Events

### Annual Best Practices Workshop

Plans are already underway for the seventh Workshop, to be held May 24-28,
2010, at the University of Illinois at Urbana-Champaign.  We hope to see
you there.

Web site: [http://workshop.openafs.org/afsbpw10/index.html](http://workshop.openafs.org/afsbpw10/index.html)

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

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names)

Status: Active - Third call for review

Third call for review; I'm gonna ask for a last call later in the
month as so far all review comment has been incorporated, unless
something comes up.

\--Derrick Brashear

### AFS Callback Extensions

[http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo](http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo)

Status: Active - Needs more discussion

We need to decide whether we're going to wait for the RPC refresh changes
before publishing extended callbacks. My belief is that that's the only
factor currently delaying this document. The question here, essentially,
is whether anyone would deploy extended callbacks before deploying updated
RPCs. To date, nobody has said they would do so.

\--Simon Wilkinson

### DNS SRV Resource Records for AFS

[http://tools.ietf.org/html/draft-allbery-afs-srv-records](http://tools.ietf.org/html/draft-allbery-afs-srv-records)

Status: Submitted to IETF

Last call will complete on February 5th, after which (probably the next
weekend), I'll upload a new version of the draft.  At that point, the
document will go forward to the IESG for review and approval (possibly
after futher changes).

I have read and responded to all of the Last Call feedback received.  The
changes due to the Last Call feedback are mostly minor.  Various people
reviewing the document would have liked to have a reference to the AFS
protocol specification.  I think we all agree that it would be lovely to
have such a thing!

\--Russ (Received Feb 1, 2010)

### RXGK

[http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk](http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk)

Status: Active

Rxgk is a security layer for AFS which will support strong encryption and
authentication through Kerberos v5, GSI and any other GSSAPI security
mechanism.

Documents describing rxgk have been published and are being discussed on
the afs3-standardization list. To date, no major objections have been
raised in both public, and private, review.

Implementation work on rxgk has commenced - this is proceeding in a number
of parallel tracks:

- 1

Changes are being made to the OpenAFS code base to support multiple
security layers - these changes will aid the integration of both rxgk and
any other new RX security mechanism. These are being submitted to
OpenAFS's gerrit as they occur, and are already being merged into the
development tree - look for commits by sxw@your-file-system.com if you
wish to track these.

- 2

A new cryptography framework for OpenAFS is being developed. Whilst we
are keen to avoid using our own cryptography code, in some situations such
as the kernel, we have no choice. So, the intention is to provide a
multi-layered cryptography framework where each layer can be replaced with
native routines. As a foundation, we will be using Heimdal's libcrypto
library to provide a set of EVP-style functions to the rest of the OpenAFS
code. We will use this in the kernel, and where a compatible library is
not available in userspace. On top of this, we will provide a library
offering RFC3961 style encryption functions. The current intention is to
base this on Heimdal's crypto.c. rxgk will then be built on top of this
library.

- 3

rxgk itself is being implemented on top of this base. An initial
implementation of the key negotiation mechanism is complete, and work has
commenced on writing the block encryption layer.

\--Simon

### AFS3 ACL Rights

[http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions](http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions)

Status: Second draft

Andrew Deason has published an IETF draft to provide a common document for
discussion of the proposed new ACL rights to prevent users with admin
rights on a folder from giving rights to system:anyuser.

### Rx Security Object Providing Cleartext Peer Identity Assertions

[http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear](http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear)

Status: BCP

There are a number of anonymous RxRPC applications which require identity
assertions in order to ensure that the desired peer receives and processes
the procedure call.  This memo defines a replacement for the rxnull
security class which provides a means for mutually agreeing upon who is
communicating, without incurring cryptographic overhead.  It should be
noted that, much like rxnull, this security object is not suitable for use
in a distributed environment due to its inability to provide integrity
protection.

## Projects

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

Performance improvements are being worked on in gerrit 1092 (parallel
preattach optimization) and gerrit 880 (volume group cache). 1092 is
nearly done (just undergoing review) while 880 needs some more work on
the underlying lock work (gerrit 1237). Development documentation has
begun to emerge, starting with FSSYNC docs (gerrit 1236).

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Simon Wilkinson added the -files and -excessive options to the
fs\_getcacheparms man page and updated the man pages and XML documentation
to reflect that new versions don't perform a weekly restart of the
bosserver. Asanka Herath fixed a typo in the Admin guide.

### Pthreaded Ubik

Project Contact:

- Steven Jenkins <steven.jenkins@gmail.com>
- Andrew Deason <adeason@sinenomine.net>

Pthreaded ubik now compiles again on master without warnings. While
there are no known issues with pthreaded ubik itself at this point,
portions of the vlserver code are known not to be threadsafe. Work is
ongoing on making the vlserver threadsafe and thus safe to use with
pthreaded ubik.

\--Andrew

### Kerberos v5 and multiple encryption types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

rxk5 test environment -> upgraded.

build logic for openafs -> fixes so can now build "out of tree".

Now looking at kerberos integration issues.

The plan is to deliver "separated" patches around may.  Patches will be
against some recent version of openafs as of that time.

\--Marcus

### Disconnected AFS support

Project Contacts:

- Simon Wilkinson <sxw@inf.ed.ac.uk>
- Dragos Tatulea <dragos.tatulea@gmail.com>

Simon started some discussion on the afs3-standardization list about
adding a VL\_WhoAmI RPC to aid with reconstructing ACL's in disconnected
mode.

### Per-File ACLs

Project Contacts:

- Marc Dionne <marc.c.dionne@gmail.com>

I did some work on it last summer which included a basic working
prototype, and there has also been some discussion of the expected
semantics, compatibility and implementation issues.

I'm proposing to do a talk on the subject at the next workshop, and hope
to revive the issue and move it forward in the meantime by trying to get
some consensus on the expected semantics, formalising the protocol
changes, and make progress on the coding front.

\--Marc

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Rx OSD integration & Raw Vicep Access in Clients - August 2009
- S3 Front-end for AFS - November 2009
- Active Directory Backend for Ptserver - November 2009
- Virtual Machine Images - November 2009
- SetAG - December 2009
- Userspace cache manager - December 2009
- \*BSD Support - January 2010
- Mac OS X OpenAFS Preference Pane - January 2010
- Extended Callback Information - January 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 51 (last month: 27)

    Patches merged into the master branch:
    Month   Number of Commits
    2010-02   43 (Partial month)
    2010-01  103
    2009-12   72
    2009-11   85
    2009-10  154
    2009-09  142
    2009-08   78
    2009-07  181

    Patches merged into the stable branch:
    Month   Number of Commits
    2010-02  12 (Partial month)
    2010-01  11
    2009-12  92
    2009-11  21
    2009-10   7
    2009-09   8
    2009-08  17
    2009-07   5

### Patches waiting for review

    Date       Author          Change# Description
    2010-02-09 Andrew Deason    (1264) Abstract /vicepX header traversal
    2010-02-09 Andrew Deason     (880) DAFS: Maintain viced volume group hierarchy cache
    2010-02-08 Andrew Deason    (1263) salvager: avoid needing temp files to stay around
    2010-02-08 Antoine Verheijen (1262) Fix segmentation fault in vsu_GetVolumeID
    2010-02-08 Andrew Deason    (1238) Consolidate code for reading/writing vol headers
    2010-02-08 Andrew Deason    (1237) Add a general file-level locking API
    2010-02-08 Andrew Deason    (1236) Document FSSYNC commands
    2010-02-08 Antoine Verheijen (1261) Add support for OpenBSD 4.6
    2010-02-08 Antoine Verheijen (1260) OpenBSD: allow for more graceful shutdown
    2010-02-08 Antoine Verheijen (1259) OpenBSD: fix lookup of network interfaces
    2010-02-08 Antoine Verheijen (1255) OpenBSD: don't use pthreads
    2010-02-08 Antoine Verheijen (1258) OpenBSD: move AFS memory type offet
    2010-02-08 Antoine Verheijen (1257) OpenBSD: don't use AFS_GLOBAL_SUNLOCK on single processor system
    2010-02-08 Antoine Verheijen (1256) OpenBSD: allow code optimization to be turned off
    2010-02-08 Rainer Toebbicke (1252) afs_TruncateAllSegments() make sure correct afs_size_t comparison is used when selecting dcache entries for truncation
    2010-02-08 Andrew Deason    (1254) salvager: alias -f to -force
    2010-02-08 Andrew Deason    (1235) Create missing root directory when ORPH_ATTACH
    2010-02-08 Michael Meffie   (1001) return an error from afs_readdir when out of buffers
    2010-02-06 Dan Hyde         (1212) VTRANS_LOCK not needed in TryUnlock
    2010-02-05 Derrick Brashear (1225) internationalize comerr
    2010-02-05 Derrick Brashear (1234) afsdb kernel timeout
    2010-02-05 Derrick Brashear (1066) darwin rxevent sleep instead of polling
    2010-02-05 Simon Wilkinson  (1244) Refactor afs_ioctl code
    2010-02-05 Simon Wilkinson  (1243) UKERNEL: End the #define u insanity
    2010-02-05 Simon Wilkinson  (1242) Add rx security index enum
    2010-02-05 Simon Wilkinson  (1241) Unix CM: Simplify #ifdef ladder in lock.h
    2010-02-05 Simon Wilkinson  (1240) Unix CM: Indent #ifdef ladder in lock.h
    2010-02-05 Simon Wilkinson  (1239) Unix CM: Reorganise security object code
    2010-02-05 Dan Hyde         (1213) VOL_LOCK needed when traversing DiskPartitionList
    2010-02-04 Derrick Brashear (1233) provide afs_osi_TimedSleep
    2010-02-03 Dan Hyde         (1191) runningCalls: VOL_COUNT_LOCK vs VTRANS_LOCK
    2010-02-03 Derrick Brashear (1172) linux mmap anti-deadlock shouldn't break StoreAllSegments
    2010-02-03 Derrick Brashear (1201) basic kernel event system for afs cm
    2010-02-02 Simon Wilkinson  (1072) Unix CM: Conflate rxfs_[store,fetch]Variables
    2010-01-29 Michael Meffie   (1092) DAFS: avoid volume lock contention during initialization
    2010-01-27 Adam Megacz      (1118) Have bosserver catch SIGTERM and shut down gracefully.
    2010-01-20 Simon Wilkinson  (1074) Unix CM: Include memcache's tiov in rxfs_context
    2010-01-14 Jeffrey Altman   (1084) Windows: Permit AFSCache file to be encrypted
    2010-01-14 Chas Williams - CONTRACTOR (1080) LINUX: you dont need to memset() after allocating credentials
    2010-01-14 Derrick Brashear  (451) macos knote fsevents hinting
    2009-11-29 Andrew Deason     (875) Make ubik use unsigned addresses
    2009-11-18 Andrew Deason     (709) Break origin's callback for RXAFS_Rename target
    2009-11-04 Andrew Deason     (436) Avoid unnecessarily updating .. in SAFSS_Rename
    2009-11-04 Evan Broder       (778) Increase the maximum number of sysnames
    2009-11-04 Michael Meffie    (215) Print throttled packet counts with rxdebug
    2009-10-26 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2009-09-09 Matt Benjamin     (435) clear stat flag on renamed directories
    2009-08-29 Matt Benjamin     (376) K5SSL by Marcus Watts
    2009-07-29 Michael Meffie    (147) Fix bosserver directory creation
    2009-07-24 Hartmut Reuter     (70) preparing rxosd integration: change in AFSFetchStatus



### Patches merged into the master branch

    Date       Author          Change# Description
    2010-02-08 Andrew Deason    (1253) tubik: Initialize mutexes and cvs
    2010-02-07 Derrick Brashear (1251) darwin vnodeops cleanup
    2010-02-07 Derrick Brashear (1249) macos package allow backrev
    2010-02-06 Derrick Brashear (1248) fetchstore reorg
    2010-02-06 Derrick Brashear (1247) set storeproc for non-linux
    2010-02-05 Derrick Brashear (1246) decode-panic deal with kextload
    2010-02-05 Jeffrey Altman   (1245) Windows: Remove use of AFS_AFSDB_ENV from kauth/user_nt.c
    2010-02-04 Derrick Brashear (1230) macos prefs pane spelling
    2010-02-04 Marc Dionne      (1229) Don't clear afs_stats_cmperf too early during shutdown
    2010-02-04 Derrick Brashear (1228) fakestat should preclude afsdb lookups too
    2010-02-03 Derrick Brashear (1227) macos installer scripts shouldn't echo
    2010-02-03 Derrick Brashear (1226) format fallout
    2010-02-03 Simon Wilkinson  (1224) Fix fs storebehind on files with 2 or more servers
    2010-02-03 Simon Wilkinson  (1223) Fix pioctl input and output handling
    2010-02-03 Simon Wilkinson  (1222) Make twiddle build
    2010-02-03 Simon Wilkinson  (1221) Add xdr_len, to work out required buffer size
    2010-02-03 Simon Wilkinson  (1220) Add xdr_mem to the Unix build
    2010-02-03 Simon Wilkinson   (796) Add printf format checks to the rest of tree
    2010-02-03 Simon Wilkinson   (795) Add printf format checks to rx
    2010-02-03 Simon Wilkinson  (1219) Add interface to select client security objects
    2010-02-03 Simon Wilkinson   (792) Add printf format checks to the cache manager
    2010-02-03 Simon Wilkinson   (794) Add printf format checks to afs_com_err()
    2010-02-03 Simon Wilkinson   (793) Add printf format checks to util's log functions
    2010-02-03 Simon Wilkinson  (1218) Don't pass tokens around the backup system
    2010-02-03 Simon Wilkinson  (1177) Common interface for server security objects
    2010-02-03 Simon Wilkinson  (1217) Document the extra options to fs getcacheparms
    2010-02-02 Simon Wilkinson  (1208) Add a set of strings for the InstallationCheck
    2010-02-02 Andrew Deason    (1211) Squash pthreaded ubik warnings
    2010-02-02 Andrew Deason    (1210) Use -A and -u in pthreaded ubik rxgen
    2010-02-02 Andrew Deason    (1209) Build utst_client for pthreaded ubik
    2010-02-02 Simon Wilkinson  (1206) Don't echo from the InstallationCheck script
    2010-02-02 Simon Wilkinson  (1205) Remove internal vldbClientInit prototype
    2010-02-02 Derrick Brashear (1200) icl 64 bit platform rationalization
    2010-02-02 Derrick Brashear (1199) icl trace code deduplication
    2010-02-02 Simon Wilkinson  (1204) Fix USS to use volser prototypes
    2010-02-02 Simon Wilkinson  (1202) xdr_proc_t really is different on linux26_i386
    2010-02-02 Simon Wilkinson  (1203) Darwin: Stop CM builds when errors occur
    2010-02-02 Marc Dionne      (1195) Linux: warning fix in osi_file.c
    2010-02-02 Simon Wilkinson  (1194) Linux: Fix breakage in llseek error handling
    2010-02-01 Derrick Brashear (1190) call afs_osi_suser correctly in PNewUuid
    2010-02-01 Derrick Brashear (1185) make 1.5.71 for unix
    2010-02-01 Jeffrey Altman   (1184) Windows: ChangeLog and Version Number for 1.5.71
    2010-02-01 Simon Wilkinson  (1073) Unix CM: Always use ->storeproc()
    2010-01-31 Derrick Brashear (1182) rx idledeadtime don't track window wait
    2010-01-29 Simon Wilkinson  (1181) Darwin: Don't use ARCHFLAGS to determine arch
    2010-01-29 Derrick Brashear (1180) macos prefpane fat binary arch selection correction
    2010-01-29 Derrick Brashear (1173) linux cache file open fail print error
    2010-01-29 Derrick Brashear (1179) xdrproc_t probably not really different on linux26
    2010-01-29 Derrick Brashear (1178) further irix updates
    2010-01-28 Derrick Brashear (1176) afsd missing close brace
    2010-01-28 Derrick Brashear (1174) irix cc defaults to pre-c99
    2010-01-28 Derrick Brashear (1171) ignore generated macos packaging description file
    2010-01-28 Derrick Brashear (1175) irix can't have vprintf in the kernel
    2010-01-28 Jeffrey Altman   (1164) Windows: drop cm_Freelance_Lock before call to cm_FreelanceAddMount
    2010-01-27 Jeffrey Altman   (1170) Windows: export xdr_serverList and xdr_Capabilities from afsrpc.dll
    2010-01-27 Marc Dionne      (1167) Linux: don't count pag keys against root's keyring quotas
    2010-01-27 Derrick Brashear (1169) init pthread mutexes only if an initializer exists
    2010-01-27 Derrick Brashear (1166) initialize pthread mutexes to avoid compiler common variable stupidity
    2010-01-27 Derrick Brashear (1133) switch to always attempting cache-config-by-path
    2010-01-27 Simon Wilkinson  (1168) XDR memory management fixes
    2010-01-27 Derrick Brashear (1160) rx ResetCall should wait if it says it will
    2010-01-27 Derrick Brashear (1159) rx avoid discarding packets while tq is busy
    2010-01-27 Jeffrey Altman   (319) Use xdr_alloc and xdr_free within ptuser
    2010-01-26 Derrick Brashear (1165) viced detailed stats should record stored bytes correctly
    2010-01-25 Derrick Brashear (1158) darwin80 if changes cleanup
    2010-01-25 Derrick Brashear (1157) darwin rx if structure fix
    2010-01-25 Derrick Brashear (1154) pagsh dependencies don't get to include system libs
    2010-01-25 Simon Wilkinson  (1155) Linux: Handle llseek failure
    2010-01-24 Derrick Brashear (1153) unix 1.5.70
    2010-01-24 Jeffrey Altman   (1146) Windows: 1.5.70
    2010-01-23 Marc Dionne      (1151) Linux Keyrings: don't ignore error code from session keyring creation
    2010-01-23 Marc Dionne      (1150) Add missing dependencies for pagsh in Makefile
    2010-01-22 Simon Wilkinson  (1149) Revert "Fix afs_AccessOK for dropbox case"
    2010-01-22 Simon Wilkinson  (1147) Don't throw data away in afs_StoreMini
    2010-01-22 Andrew Deason    (1143) Fix afs_AccessOK for dropbox case
    2010-01-22 Derrick Brashear (1101) abstract rx if structure access
    2010-01-22 Russ Allbery     (1144) Enable weak enctypes for klog.krb5 if supported by Kerberos
    2010-01-22 Derrick Brashear (1132) simplify ufs cache mechanisms available
    2010-01-22 Russ Allbery     (1141) Enable weak enctypes for aklog if supported by Kerberos
    2010-01-22 Marc Dionne      (1140) afs_vnop_attrs: syntax error in conditional expression
    2010-01-22 Jeffrey Altman   (1142) Windows: AFS_AFSDB_ENV preprocessor symbol no longer exists
    2010-01-21 Jeffrey Altman   (1139) Windows: add build and clean rule for bc.h
    2010-01-21 Jeffrey Altman   (1138) Windows: Windows v6.0 SDK does not define __RPC__out
    2010-01-21 Jeffrey Altman   (1136) Undo labeling of elements of rx structures for Windows
    2010-01-21 Jeffrey Altman   (1135) Install bucoord/bc.h to permit Windows to build
    2010-01-21 Marc Dionne      (1134) Warning cleanup: implicit function declarations in butc and bucoord
    2010-01-21 Simon Wilkinson  (1126) Label elements of rx structures
    2010-01-20 Derrick Brashear (1125) batch panic decoding for MacOS
    2010-01-20 Derrick Brashear (1122) macos set don't backup attribute on cache files
    2010-01-20 Simon Wilkinson  (1131) Fix so that UKERNEL can keep using system xdr
    2010-01-20 Russ Allbery     (1129) Avoid executable headers in local include tree
    2010-01-19 Jeffrey Altman   (1124) Windows: Help text update for Network Identity Manager Provider
    2010-01-19 Asanka Herath    (1121) Windows: Add a context menu for the AFS icon
    2010-01-19 Jeffrey Altman   (1115) Windows: Version number update for 1.5.69
    2010-01-19 Jeffrey Altman   (1114) Windows: ChangeLog for 1.5.69
    2010-01-19 Derrick Brashear (1123) make 1.5.69 for unix
    2010-01-17 Derrick Brashear (1120) create debugging kext package for MacOS
    2010-01-17 Marc Dionne      (1116) More pam warning cleanups - test_pam.c
    2010-01-17 Marc Dionne      (1117) up.c: remove unused variable pageSize
    2010-01-17 Marc Dionne      (1119) uss: Fix IP address parsing and cleanup warnings
    2010-01-16 Asanka Herath    (1105) Windows: Query the MTU value from the registry
    2010-01-16 Simon Wilkinson  (1112) Don't double free call structure
    2010-01-16 Simon Wilkinson  (1110) Linux: Add missing prototype
    2010-01-16 Simon Wilkinson  (1109) Unix CM: Fix negative file length case, again
    2010-01-16 Jeffrey Altman   (1107) Rx: Correct AFS_NT40_ENV rx_GetIFInfo max MTU assignments
    2010-01-16 Jeffrey Altman   (1108) Rx: Do not drop call lock in rx_WriteProc* and rx_ReadProc*
    2010-01-15 Jeffrey Altman   (1106) Rx: Remove last remnants of DJGPP support
    2010-01-15 Marc Dionne       (847) src/pam warning fixes
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

### Patches merged into the stable branch

    Date       Author          Change# Description
    2010-02-07 Derrick Brashear (1250) macos package allow backrev
    2010-02-04 Derrick Brashear (1232) fakestat should preclude afsdb lookups too
    2010-02-04 Derrick Brashear (1231) macos prefs pane spelling
    2010-02-02 Derrick Brashear (1216) no debian packaging in 1.4.x
    2010-02-02 Derrick Brashear (1215) Add a set of strings for the InstallationCheck
    2010-02-02 Derrick Brashear (1214) create debugging kext package for MacOS
    2010-02-02 Derrick Brashear (1207) Don't echo from the InstallationCheck script
    2010-02-02 Derrick Brashear (1197) afs_vnop_attrs: syntax error in conditional expression
    2010-02-01 Derrick Brashear (1193) call afs_osi_suser correctly in PNewUuid
    2010-02-01 Derrick Brashear (1186) make 1.4.12 rc2
    2010-02-01 Derrick Brashear (1183) rx idledeadtime don't track window wait
    2010-01-22 Russ Allbery     (1148) Enable weak enctypes for klog.krb5 if supported by Kerberos
    2010-01-22 Derrick Brashear (1137) linux mmap anti-deadlock should issue error rather than write returns
    2010-01-22 Russ Allbery     (1145) Enable weak enctypes for aklog if supported by Kerberos
    2010-01-16 Simon Wilkinson  (1113) Don't double free call structure
    2010-01-14 Simon Wilkinson  (1102) Spec file changes
    2010-01-14 Simon Wilkinson  (1099) Don't install compile_et into its own directory
    2010-01-14 Derrick Brashear  (994) Linux: kmem_cache_create fix and cleanup
    2010-01-12 Derrick Brashear (1091) make 1.4.12rc1
    2010-01-08 Derrick Brashear (1081) linux kernel lacks uintptr
    2010-01-07 Andrew Deason    (1076) avoid leaking stat info
    2010-01-07 Derrick Brashear (1053) viced host always hash on add

## Resolved Tickets

Here is a list of tickets that have been resolved since January 1, 2010:

    ticket # state     created       title
      62986: resolved  Jun 06, 2007  tokens being discarded with error 19270407
     124097: resolved  Jan 09, 2009  h_Enumerate found <count> of <hostCount> hosts
     124483: resolved  Mar 17, 2009  DAFS: volume header not properly cleared
     124484: resolved  Mar 17, 2009  DAFS: volumes not salvaged when the first access is from the volserver
     124485: resolved  Mar 17, 2009  DAFS: fileserver cores if restarted during start-up
     124486: resolved  Mar 17, 2009  DAFS: fileserver hangs on shutdown
     124490: resolved  Mar 17, 2009  DAFS: volume moves within a server cause volheaders to be out of sync
     124491: resolved  Mar 17, 2009  DAFS: salvageserver race condition in JudgeEntry
     124951: resolved  Jun 18, 2009  1.4.11pre1 on openSuSE fails rpmlint.
     124975: resolved  Jun 23, 2009  fix rxgen in various Makefiles in HEAD
     124977: resolved  Jun 23, 2009  properly initialize pthreaded ubik mutexes & condvars
     125365: resolved  Sep 04, 2009  ZFS cache usage tracking
     126251: resolved  Jan 25, 2010  Snow Leopard openafs 1.5.70 kext error
     126317: resolved  Feb 01, 2010  OpenAFS-1.4.12pre2  afs_vnop_attrs.c fails to compile on sun4x_515, sunx86_510 and sun4x_59
     126322: resolved  Feb 02, 2010  Less than useful error message when using 10.5 installer on 10.6
