---
title: OpenAFS Newsletter, Volume 2, Issue 8, August 2010
---

# OpenAFS Newsletter, Volume 2, Issue 8, August 2010

Welcome to the August issue of the OpenAFS newsletter. This newsletter
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

There is no case study this month. If anyone is interested in being
profiled in this newsletter, please contact Jason Edgecombe.

## General OpenAFS Progress

The AFS registrars agreed that a consensus is present so that elections
may be held for chairs of the afs3-standardization group. The schedule for
the election of the chairs is as follows (courtesy of Jeffrey Hutzelman):

    17-Aug-2010  Nominations close - 23:59 UTC
    24-Aug-2010  Call for votes
    07-Sep-2010  Voting closes     - 23:59 UTC
    14-Sep-2010  Results announced
    01-Oct-2010  New chairs take office

Details may be read at 
[http://michigan-openafs-lists.central.org/archives/afs3-standardization/2010-August/000728.html](http://michigan-openafs-lists.central.org/archives/afs3-standardization/2010-August/000728.html)

Questions should be sent to the afs3-standardization list at 
[http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization](http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization)

OpenAFS now has a buildbot set up.  The buildbot will automatically build
and verify changes in gerrit before they are approved.  Successful changes
are flagged as verified in gerrit.  Buildbot leaves a comment in gerrit
which contains the success or failure of each build slave.  There are
currently three build slaves running on the following platforms: Debian
Lenny 32-bit, IRIX 6.5, and Windows 7 64-bit. The following people were
instrumental in getting buildbot set up:

- Jason Edgecombe - installed, configured, and maintains the buildbot master
on Debian Lenny 32-bit which also runs as a build slave.
- Jeffrey Altman of YFS and Secure Endpoints - hosting of the buildbot master
- Asanka Herath of Secure Endpoints - provided the Windows 7 64-bit build slave
- Chaz Chandler - provided the IRIX 6.5 build slave

The buildbot effort is still a work-in-progress.  Suggestions are welcome.
More build slaves are needed to provide better platform coverage.  Please
contact Jason Edgecombe <jason@rampaginggeek.com> if you would like to
contribute to the buildbot effort.

## Events

### European AFS Conference

European AFS & Kerberos Conference 2010 is glad to invite you to register
for this year's event, which will take place in Pilsen, Czech Republic,
from September 13 to September 15. The conference is being hosted by
Centre for Information Technology, University of West Bohemia.

See the conference WWW pages at [http://afs2010.civ.zcu.cz](http://afs2010.civ.zcu.cz) for further
details and breaking news.

Take advantage of the early registration rates, available until July
31\. Registration can be done on-line at
[http://afs2010.civ.zcu.cz/register/](http://afs2010.civ.zcu.cz/register/).

There are still some available agenda slots. Everyone is welcome to share
their experiences and ideas!

Submit your talk to afs2010@civ.zcu.cz. The "Call for Participation" will
end Monday August 2, 2010. Acceptances will be made based upon quality,
applicability, and fit with other submissions.

We are looking forward to seeing you in Pilsen!

The Workshop Organizers,

[http://afs2010.civ.zcu.cz/](http://afs2010.civ.zcu.cz/)

afs2010@civ.zcu.cz

## AFS Protocol Standardization

Informal drafts that haven't been uploaded to the IETF web site:

Rx Spec:

[http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html](http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html)

This draft is in the very early stages. Mike Meffie and Tom Keiser are the
current owners of this proposal. A formal specification of Rx is needed as
a basis for other IETF proposals.

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization](http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names)

Status: Third Draft

draft-brashear-afs3-pts-extended-names continues to be available for
review. There is still discussion about the technical content and
background references.

### AFS Callback Extensions

[http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo](http://tools.ietf.org/html/draft-benjamin-extendedcallbackinfo)

Status: Active - Waiting on RPC refresh

The callback draft is stable.  There is a published implementation. My
understanding is that it is accepted with the requirement that it be
adjusted to use RPC refresh data types, which means AFSFetchStatus64 and
the new 100ns time data type.  This is regarded as "trivial" but at the
same time, the spec can't be standardized as is.  It is planned for merge
in, IIRC, 1.9/1.10.

\--Matt Benjamin

### RXGK

[http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk](http://tools.ietf.org/html/draft-wilkinson-afs3-rxgk)

Status: Active

Rxgk is a security layer for AFS which will support strong encryption and
authentication through Kerberos v5, GSI and any other GSSAPI security
mechanism.

Changes which are considered suitable for the 1.5.x series are in git -
look for changes with author sxw@your-file-system.com. A development tree,
which will be frequently re-based, is at
http://github.com/your-file-system/openafs-rxgk

Last Update: Jan 9, 2010

### AFS3 ACL Rights

[http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions](http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions)

Status: Second draft

Last update: January 13, 2010

This draft calls for volume-level restrictions on what users with 'a'
administrator rights to a folder may do. For example, you may want to
prevent users from granting 'w' write access to 'system:anyuser', which
would give anyone in the world with an AFS client write access.

### Rx Security Object Providing Cleartext Peer Identity Assertions

[http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear](http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear)

Status: Third draft

Last Update: April 17, 2010

I released a new version of the Rx Clear security class I-D the other
day.  I am hereby soliciting comments on this new version of the
draft.

[http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear](http://tools.ietf.org/html/draft-tkeiser-rxrpc-sec-clear)

The major changes in this version of the document are:

- new introductory section that better explains the relationship
between Rx and AFS-3 so that the document is more approachable for
novices
- additional prose in the security considerations section which better
explains how this security object changes the attack vectors, as well
as a brief mention of securing rxnull/rxclear with IPsec
- flesh out the AFS assigned numbers registrar section with formal
specifications for each newly requested registry
- change the endpoint identifier type enumeration from 32-bits to
8-bits, as the larger size seemed quite wasteful
- mark several security header fields as reserved for future use
- I added a number of informative references to Transarc and CMU ITC
tech reports

\--Tom

### AFSVol Tag-Length-Value Remote Procedure Call Extensions

[http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv](http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv)

Status: Fourth Draft

Last Update: August 4, 2010



### AFS Byte-Range File Locking

[http://tools.ietf.org/html/draft-mbenjamin-afs-file-locking](http://tools.ietf.org/html/draft-mbenjamin-afs-file-locking)

Status: Fifth Draft

This draft proposes protocol extensions to support byte-range and
mandatory locking.

The first draft was submitted on May 5, 2010.

## Projects

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

The runtime option to enable fast-restart-like functionality with DAFS has
been merged (gerrit 2277), as has DAFS documentation for the Unix Quick
Start Guide (gerrit 2508). The build system now builds relevant components
in DAFS and non-DAFS variants alongside each other, and we have made
progress towards having fssync-debug conditionally execute the correct
variant (gerrit 2480), but it's not merged yet. The fix for salvaging
attached volumes (gerrit 2329) has made more progress but is also still
not yet merged. I believe all DAFS changes intended for 1.6 are now either
merged or are undergoing review in gerrit.

\--Andrew

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

We now have a mechanism for assembling the man pages from multiple POD
fragments, which was used to avoid too much duplication of documentation
between the regular and demand-attach versions of the servers.  This will
eventually be used for the common flags for various subcommands of
binaries, but only one command has been converted so far.

\--Russ

### Per-File ACLs

Project Contacts:

- Marc Dionne <marc.c.dionne@gmail.com>

Not much progress has happened since the workshop in May.  The current
prototype code is still up on github at
[http://github.com/mdionne/openafs](http://github.com/mdionne/openafs).

\--Marc

### Google Summer of Code 2010

OpenAFS received five slots for the 2010 Google Summer of Code.

Go to [http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs](http://socghop.appspot.com/gsoc/org/home/google/gsoc2010/openafs)
for more information about the GSoC projects.

#### Unix Support for AppleDouble files (Posix Attributes)

Student Developer: Kelli Ireland <kelli.ireland@gmail.com>

Mentor: Derrick Brashear <shadow@gmail.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017582.html)

No update. --Ed.

#### Encrypted Storage

Student Developer: Sanket Agarwal <sanket@sanketagarwal.com>

Mentor: Simon Wilkinson <sxw@inf.ed.ac.uk>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017424.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017424.html)

My task is to develop encrypted storage.

The task was subdivided into parts, firstly I was set to develop a prototype
for extents and chunking central for Encryption. This part is complete.
Secondly, I have to implement the Metadata file which stores information of
the files encrypted, this is what I am presently pursuing. Thirdly I will
have to integrate the Encryption module and forthly a user interface.

I am done with phase 1 and well into phase 2. Though due to unavailability of
Simon and Derrick off late, I haven't been able make much recent progress. I
hope to complete at least phase 3 by the hard deadline of 16th August for
Linux kernel. Extending will take time but conceptually will work for all
platforms. Note that my prototype is usable for all sort of kernels, those
which support Page Caching and those which not. The code was developed in
such a manner. I do not claim to complete the project within time BUT I will
complete it soon and I am dedicated to that. Kernel development has been a
bit time consuming.

\--Sanket

#### Apply the kafs project of OpenAFS

Student Developer: Wang Lei <wang840925@gmail.com>

Mentor: David Howells <dhowells@redhat.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-April/017493.html](https://lists.openafs.org/pipermail/openafs-devel/2010-April/017493.html)

In the past month, we have almost implemented auto-cell mount operation
add an error check for DNS query module to handle the errors from
user-space tools.

\--Wang Lei

Most of these patches have now gone in upstream in the current Linux
kernel merge window.

\--David

#### Port OpenAFS to NetBSD

Student Developer: Matt Smith <matt.j.sm@gmail.com>

Mentor: Matt Benjamin <matt@linuxbox.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html](https://lists.openafs.org/pipermail/openafs-devel/2010-March/017450.html)

The LKM & afsd now run without crashing the kernel. When attempting the
view /afs, the call hangs. However, we are able to determine that it is
properly retrieving the dirents that should be inside of the folder ( . ,
.. , and a test cell). Currently, I am working to try and determine
exactly why the syscall fails to return.

\--Matt Smith

#### An open source version of the Microsoft Safe String Library

Student Developer: Jonas Sundberg <jonas.sundberg@gmail.com>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html](https://lists.openafs.org/pipermail/openafs-devel/2010-May/017602.html)

The last month of the project has mainly been spent on writing additional
tests and verifying that the Microsoft implementation passes the tests to
make sure that the implementations are compatible.  Also, some
documentation on the testing process and differences from the Microsoft
implementation have been written.

\--Jonas

### Projects with no progress or no update

Each project without progress this month is listed along with the month of
the last update.

- Active Directory Back-end for Ptserver - November 2009
- Extended Callback Information - January 2010
- Disconnected AFS support - February 2010
- Mac OS X OpenAFS Preference Pane - April 2010
- Rx OSD integration & Raw Vicep Access in Clients - May 2010
- Per-File ACLs - May 2010
- S3 Front-end for AFS - July 2010
- Virtual Machine Images - July 2010
- User-space cache manager - July 2010 (waiting on 1.6.x branch)
- Kerberos v5 and multiple encryption types - July 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 71 (last month: 74)

    Patches merged into the master branch:
    Month   Number of Commits
    2010-08   55 (Partial month)
    2010-07  160
    2010-06  171
    2010-05  139
    2010-04  160
    2010-03  140
    2010-02  156
    2010-01  103
    2009-12   72
    2009-11   85
    2009-10  154
    2009-09  142
    2009-08   78

    Patches merged into the stable 1.4.x branch:
    Month   Number of Commits
    2010-08   8 (Partial month)
    2010-06   2
    2010-05  15
    2010-04   4
    2010-03  28
    2010-02  35
    2010-01  11
    2009-12  92
    2009-11  21
    2009-10   7
    2009-09   8
    2009-08  17

### Patches waiting for review

    Date       Author          Change# Description
    2010-08-12 Michael Meffie   (2536) clean up stale defines in volser header
    2010-08-12 Andrew Deason    (2423) Use afs_sfsize_t for *_SIZE results
    2010-08-12 Andrew Deason    (2548) libafs: Set tvcp->callback before BulkStatus
    2010-08-12 Jeffrey Altman   (2541) Windows: Only Local System Account may set tokens for alternate ids
    2010-08-12 Jeffrey Altman   (2540) Windows Change Log for 1.5.76
    2010-08-12 Derrick Brashear (2537) openafs 1.5.76
    2010-08-11 Andrew Deason    (2424) GetInodeSummary: free inode info
    2010-08-11 Michael Meffie   (2431) Calculate midnight (for volume stats) based on standard functions
    2010-08-06 Jeffrey Hutzelman (2288) Fast restart for Ubik database servers
    2010-08-06 Andrew Deason    (1864) Parallel I/O extensions to namei backend
    2010-08-06 Matt Benjamin    (2011) Extended callback implementation
    2010-08-06 sanket           (1777) Add xml functionality to the vos examine command
    2010-08-06 Derrick Brashear (1625) preliminary support for pinned vcaches
    2010-08-06 Derrick Brashear (1553) dynamic volume allocation
    2010-08-06 Michael Meffie   (1001) return an error from afs_readdir when out of buffers
    2010-08-06 Jeffrey Hutzelman (2279) Include user and build host in version string
    2010-08-06 Simon Wilkinson  (1074) Unix CM: Include memcache's tiov in rxfs_context
    2010-08-06 Derrick Brashear (2463) death to trailing whitespace
    2010-08-06 Jeffrey Altman   (1742) Make -printuuid an option for all vos commands
    2010-08-06 Benjamin Kaduk   (2321) FBSD: bandaid around vcache opens tracking
    2010-08-06 Andrew Deason    (2250) vol-salvage: Move global vars into SalvInfo struct
    2010-08-06 Christof Hanke   (1970) Add output-table to libcmd
    2010-08-06 Derrick Brashear (2436) death to register
    2010-08-06 Michael Meffie   (215) rxdebug: show delayed abort packet count for rx peers
    2010-08-06 Andrew Deason    (2480) fssync-debug: exec DAFS version if DAFS detected
    2010-08-06 Andrew Deason    (2484) Fix util test dependencies
    2010-08-06 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2010-08-06 Andrew Deason    (1865) Allow salsrv salvage I/O to occur in parallel
    2010-08-06 Andrew Deason    (1869) Remove the global tempHeader/stuff structures
    2010-08-06 Andrew Deason    (1863) Provide an abstract thread pool object
    2010-08-06 Derrick Brashear (1201) basic kernel event system for afs cm
    2010-08-06 Andrew Deason    (1862) Provide an abstract work queue object
    2010-08-06 Matt Benjamin    (2071) VICE error table
    2010-08-06 Jeffrey Altman   (2089) Convert from using nvldbentry to uvldbentry
    2010-08-06 Andrew Deason    (2104) vlserver: Add a struct for trans-specific data
    2010-08-06 Russ Allbery     (2146) Add replacement mkstemp and use it
    2010-08-06 Matt Benjamin    (2216) unix cm  rx-oblivious connection pooling
    2010-08-06 Christof Hanke   (1975) Example usage of the tabular output in libcmd
    2010-08-06 Hartmut Reuter   (70) preparing rxosd integration: change in AFSFetchStatus
    2010-08-06 Andrew Deason    (2107) ubik: Drop dbase versionLock during I/O and sleeps
    2010-08-06 Andrew Deason    (2230) ubik: Abstract buffer matching and pass trans ptrs
    2010-08-06 Andrew Deason    (2106) vlserver: Allow reading during ubik writes
    2010-08-06 Andrew Deason    (2246) Move FUSE autoconf code to acinclude.m4
    2010-08-06 Derrick Brashear (2307) solaris build userland with CC
    2010-08-05 Derrick Brashear (1172) linux mmap anti-deadlock shouldn't break StoreAllSegments
    2010-08-05 Andrew Deason    (2049) Add documentation for AFS::ukernel
    2010-08-05 Matt Benjamin    (376) K5SSL by Marcus Watts
    2010-08-05 Matt Benjamin    (435) clear stat flag on renamed directories
    2010-08-05 Dan Hyde         (1191) runningCalls: VOL_COUNT_LOCK vs VTRANS_LOCK
    2010-08-05 Jeffrey Altman   (1965) Windows: add BSD getopt to afsutil.lib
    2010-08-05 Andrew Deason    (2048) Add AFS::ukernel libuafs perl bindings
    2010-08-05 Andrew Deason    (2503) XDR: decouple from system XDR implementation
    2010-08-05 Chaz Chandler    (2372) libafscp: code cleanup
    2010-08-05 Michael Meffie   (2312) print assertion expression
    2010-07-26 Andrew Deason    (2161) libafs: consistently hold vnode refs
    2010-07-26 Rainer Toebbicke (1311) Lockless path through afs_linux_dentry_revalidate
    2010-07-26 Andrew Deason    (2209) VGetVolume_r: do not wait for offlining volumes
    2010-07-26 Simon Wilkinson  (2290) Linux: Make keyring destructor remove all tokens
    2010-07-26 Andrew Deason    (2108) ubik: Protect ubik_servers in urecovery_Interact
    2010-07-26 Jeffrey Hutzelman (2287) Add -ubiknocoord option to prevent becoming coordinator
    2010-07-26 Michael Meffie   (147) Fix bosserver directory creation
    2010-07-25 Chaz Chandler    (2451) afsio: rewrite using libafscp
    2010-07-25 Michael Meffie   (1562) ihandle positional read and write
    2010-07-25 Andrew Deason    (2105) vlserver: Access cache via vl_ctx
    2010-07-25 Andrew Deason    (2368) viced: Ignore client loopback alternate addresses
    2010-07-25 Derrick Brashear (2344) viced install signal handler earlier
    2010-07-08 Chaz Chandler    (2371) libafscp: a library for "clientless" operations
    2010-07-08 Derrick Brashear (2366) rx mtu discovery tuning beyond ifmtu
    2010-07-07 Andrew Deason    (2329) DAFS: Fix demand-salvages of attached volumes
    2010-06-22 Andrew Deason    (2231) ubik: Fix buffers for reading-during-writes



### Patches merged into the master branch

    Date       Author          Change# Description
    2010-08-12 Chaz Chandler    (2516) autoconf detection of label support
    2010-08-12 Marc Dionne      (2546) Linux: avoid oops in memcpy_toiovec
    2010-08-12 Marc Dionne      (2545) Linux: Rework statfs super block operations configure test
    2010-08-12 Marc Dionne      (2544) Linux: switch to evict_inode
    2010-08-12 Marc Dionne      (2543) Linux: adapt to truncate sequence changes
    2010-08-12 Marc Dionne      (2542) Linux: use %pI4 if NIPQUAD is not available
    2010-08-12 Andrew Deason    (2533) viced: VNOVOL on deleted volumes
    2010-08-12 Derrick Brashear (2538) disable pmtu error gathering
    2010-08-12 Jeffrey Altman   (2539) Windows: comparisons of nul strings should match
    2010-08-12 Andrew Deason    (2531) volser: Ignore duplicate file tags when restoring
    2010-08-11 Simon Wilkinson  (2535) LINUX: More flock fixes
    2010-08-11 Simon Wilkinson  (2534) LINUX: Use correct type of error in flock code
    2010-08-11 Derrick Brashear (2515) fs discon support alternate uid
    2010-08-11 Derrick Brashear (2501) macos disconnected vnode holding fix
    2010-08-11 Jeffrey Altman   (2532) Windows: cm_Analyze should treat VOFFLINE like VMOVED or VNOVOL
    2010-08-11 Andrew Deason    (2530) salvage: update inodes array after CopyAndSalvage
    2010-08-11 Andrew Deason    (2529) salvage: Remove redundant 'code' declaration
    2010-08-11 Andrew Deason    (2528) salvage: Do not look at not-found root dir
    2010-08-11 Andrew Deason    (2527) salvage: Zero corrupted header
    2010-08-06 Andrew Deason    (2524) tviced: Fix serialize_state.o objdir
    2010-08-06 Andrew Deason    (2523) Eliminate $< outside of pattern rules
    2010-08-06 Andrew Deason    (2522) Fix objdir install/dest targets
    2010-08-06 Andrew Deason    (2521) tubik: Fix objdir builds
    2010-08-06 Andrew Deason    (2520) Fix afsd.fuse for objdir builds
    2010-08-06 Andrew Deason    (2519) rxgen: Error out if cpp exits with error
    2010-08-05 Derrick Brashear (2470) namei decodevolume allow low volume ids
    2010-08-05 Jeffrey Altman   (2525) Windows: add flags field to smb_ioctlProc_t function signature
    2010-08-05 Simon Wilkinson  (2471) Unix CM: Remove erroneous comment
    2010-08-05 Jeffrey Altman   (2518) Windows: optimize buf_FlushCleanPages
    2010-08-05 Andrew Deason    (2517) Unix: docbook revision tag requires a date
    2010-08-04 Andrew Deason    (2508) Add DAFS docs to the Unix Quick Start guide
    2010-08-04 Andrew Deason    (2506) HPUX: Add limits.h to sysincludes
    2010-08-04 Derrick Brashear (2514) fix unlabelled xdr field order on sun457 kernel for now
    2010-08-04 Derrick Brashear (2513) discon remove dirty vcaches from queue when discarding
    2010-08-04 Derrick Brashear (2512) reorder vcache references in discondiscardallshadows
    2010-08-04 Derrick Brashear (2511) discon getparentvcache leak fix
    2010-08-04 Andrew Deason    (2483) util: add afs_exec_alt
    2010-08-04 Derrick Brashear (2510) discon needs static_inline macro
    2010-08-04 Derrick Brashear (2509) darwin unused prototype
    2010-08-04 Andrew Deason    (2507) tbudb: Use INSTALL_PROGRAM, not INSTALL -f
    2010-08-03 Jeffrey Altman   (2505) Windows: Reduce complexity of Freelance Callback Logic
    2010-08-03 Jeffrey Altman   (2504) Windows: When processing pioctl paths ensure callbacks are obtained
    2010-08-02 Derrick Brashear (2502) fs disconnected remove ifdefs
    2010-08-02 Jeffrey Altman   (2500) Windows: docbook revision tag requires a date
    2010-08-02 Asanka Herath    (2492) Windows: Don't configure client when not installing client
    2010-08-02 Andrew Deason    (2497) SOLARIS: let xlator load if amd64/nfssrv is loaded
    2010-08-02 Andrew Deason    (2488) ptserver: Do not use cell for entry name len check
    2010-08-02 Asanka Herath    (2495) Windows: Fix MC options
    2010-08-02 Jeffrey Altman   (2491) Windows: Do not reference cm_data.rootSCachep directly
    2010-08-02 Jeffrey Altman   (2490) Windows: Update root.afs scache dv when Freelance dir bufs are regenerated
    2010-08-02 Jason Edgecombe  (2496) Factor out the common text in vos_addsite, vos_copy, and vos_zap
    2010-08-02 Asanka Herath    (2493) Windows: Build preprocessed POD documentation
    2010-08-02 Jeffrey Altman   (2499) Windows aklog: remove lstat preprocessor definition
    2010-08-02 Jeffrey Altman   (2498) Windows aklog: include afs/pterror.h
    2010-08-01 Asanka Herath    (2494) Skip over 'fragments' directory when scanning for PODs
    2010-07-31 Andrew Deason    (2485) ptserver: Allow longer foreign user names
    2010-07-31 Andrew Deason    (2487) Document krb.excl
    2010-07-31 Benjamin Kaduk   (2489) FBSD: update ifa_ifwithnet usage
    2010-07-30 Andrew Deason    (2476) viced: Correct unblessed attach2 errors
    2010-07-29 Andrew Deason    (2482) Document the 'vos offline' -busy and -sleep opts
    2010-07-29 Andrew Deason    (2481) Remove bless-related options from vos manpages
    2010-07-29 Andrew Deason    (2479) Install DAFS and non-DAFS fssync-debug
    2010-07-29 Derrick Brashear (2478) macos prefs pane improved error handling
    2010-07-29 Andrew Deason    (2477) vol-bless: Detach, not put, volumes on completion
    2010-07-28 Marc Dionne      (2474) gcc 4.5: Sequence point warning fixes
    2010-07-26 Derrick Brashear (2473) unix blacklistonce should default to fail if no fid
    2010-07-22 Andrew Deason    (2469) salvage: Zero root/readme vnodes before writing
    2010-07-22 Andrew Deason    (2461) autoconf: Force absolute INSTALL
    2010-07-22 Andrew Deason    (2467) Remove tsalvaged warning inhibition
    2010-07-22 Andrew Deason    (2466) AFS_INT64_FMT takes a afs_int64, not int64_t
    2010-07-21 Andrew Deason    (2462) Log lex/flex detection errors in the config log
    2010-07-21 Derrick Brashear (2456) vlserver - Don't overflow buffer with backup pattern
    2010-07-21 Andrew Deason    (2458) Remove an outdated inode comment block
    2010-07-21 Andrew Deason    (2459) SOLARIS: do not ignore libafs build failures
    2010-07-21 Russ Allbery     (2460) Don't cd around invocations of install-man
    2010-07-21 Andrew Deason    (2457) libafs: fix IOPEN for amd64 solaris
    2010-07-20 Andrew Deason    (2454) ubik: Make ugen_ClientInit honor noAuthFlag
    2010-07-20 Andrew Deason    (2453) bos: Do not assume DAFS just if DAFS bnode exists
    2010-07-20 Andrew Deason    (2452) bozo: Clean up bnode parms for each bnode
    2010-07-20 Jeffrey Altman   (2450) Windows: Build Demand Attach File Service
    2010-07-20 Derrick Brashear (2448) vol AttachByName should mimic other volpkg errors
    2010-07-19 Derrick Brashear (2449) ShakeLooseVCaches needs to avoid CVInit vcaches
    2010-07-18 Derrick Brashear (2442) document dasalvager
    2010-07-18 Derrick Brashear (2441) document davolserver
    2010-07-18 Derrick Brashear (2447) dafileserver synopsis
    2010-07-18 Derrick Brashear (2425) document dafileserver
    2010-07-18 Andrew Deason    (2338) vos status: report human-readable last*Time
    2010-07-18 Andrew Deason    (2337) vos status: add lastActiveTime field
    2010-07-18 Andrew Deason    (2336) vos status: actually show created time
    2010-07-18 Simon Wilkinson  (2446) dir: Add printf format checks to log
    2010-07-18 Simon Wilkinson  (2445) budb: Add printf format checks to logging fns
    2010-07-18 Simon Wilkinson  (2444) vol: Fix logging functions
    2010-07-16 Simon Wilkinson  (2443) Linux: Load exportfs first
    2010-07-16 Russ Allbery     (2437) Rename configure.in to configure.ac
    2010-07-16 Russ Allbery     (2440) Add include method for POD documentation
    2010-07-16 Russ Allbery     (2439) Fix unterminated B<> sequence in bos addhost man page
    2010-07-16 Russ Allbery     (2438) Flesh out the configuration documentation
    2010-07-15 Russ Allbery     (2434) Add new demand-attach binaries to .gitignore
    2010-07-15 Russ Allbery     (2433) Fix .version generation for make libafs_tree
    2010-07-15 Russ Allbery     (2432) Move build support files into build-tools
    2010-07-15 Derrick Brashear (2435) afspag version of rx_knet.o
    2010-07-14 Russ Allbery     (2429) Debian: Install the demand-attach versions of the binaries
    2010-07-14 Russ Allbery     (2428) Use the full version number for Debian packages
    2010-07-14 Russ Allbery     (2427) make dpkg should only build binary packages
    2010-07-14 Russ Allbery     (2426) Update Debian packaging to 1.5.75-2
    2010-07-14 Michael Meffie   (2349) man: document bos addhost -clone
    2010-07-14 Russ Allbery     (2420) Fix ktime test on 64-bit systems
    2010-07-14 Andrew Deason    (2376) RX: ignore all local 127/8 IFF_LOOPBACK interfaces
    2010-07-14 Andrew Deason    (2367) Treat all 127.0/16 addresses as loopback
    2010-07-14 Russ Allbery     (2419) Rewrite FUSE macro to skip FUSE if not found unless --enabled
    2010-07-14 Marc Dionne      (2417) Linux: use an int pointer for the size argument to getsockopt
    2010-07-14 Jeffrey Hutzelman (2275) Don't overflow a buffer on the server's stack at startup
    2010-07-14 Marc Dionne      (2415) rx_user.c: Remove unused variable
    2010-07-14 Derrick Brashear (2403) demand attach build always
    2010-07-14 Derrick Brashear (2414) linux rx pmtu fixes
    2010-07-14 Derrick Brashear (2413) simple fuse enable change
    2010-07-14 Andrew Deason    (2277) Add -unsafe-nosalvage fileserver option
    2010-07-14 Simon Wilkinson  (2404) Check for crypt in external library
    2010-07-14 Russ Allbery     (2405) Update Debian packaging to 1.5.75-1
    2010-07-14 Derrick Brashear (2400) enable pmtu in configure by default
    2010-07-14 Derrick Brashear (2411) afs sunpro not always c99
    2010-07-14 Derrick Brashear (2410) xdr sunpro not always c99
    2010-07-14 Russ Allbery     (2406) make dpkg should not depend on dest
    2010-07-14 Derrick Brashear (2399) simple is-lex-flex autoconf test
    2010-07-14 Russ Allbery     (2408) Link libafsauthent with -lresolv if required
    2010-07-13 Russ Allbery     (2402) Link libafsauthent with -lresolv if required
    2010-07-13 Derrick Brashear (2401) disconnected fix prototype warning
    2010-07-13 Derrick Brashear (2398) 64bit macos new config.guess support
    2010-07-13 Derrick Brashear (2397) unix disconnected mode always
    2010-07-13 Derrick Brashear (2396) linux cache bypass by default
    2010-07-13 Jeffrey Altman   (2388) DAFS: variable declarations in C must be a top of block
    2010-07-13 Jeffrey Altman   (2390) Windows: Generate a valid <revision> block using mkvers.c
    2010-07-13 Jeffrey Altman   (2391) Windows: Permit docbook validation using xmllint
    2010-07-13 Jeffrey Altman   (2394) Correct DTD validation errors in the UserGuide
    2010-07-13 Jeffrey Altman   (2393) Commit DTD validation errors in the Windows Release Notes
    2010-07-13 Jeffrey Altman   (2392) Correct DTD validation errors in the AdminGuide
    2010-07-13 Jason Edgecombe  (2385) Add the July 2010 newsletter
    2010-07-12 Simon Wilkinson  (2389) Linux: Use inode lock compat function
    2010-07-12 Derrick Brashear (2387) fix dumptool on macos
    2010-07-12 Derrick Brashear (2386) rx getaddr loopback change fallout
    2010-07-12 Andrew Deason    (2375) Consolidate loopback address tests
    2010-07-12 Michael Meffie   (1949) xstat: fix large integer output
    2010-07-12 Andrew Deason    (2239) Provide man pages for more fssync-debug commands
    2010-07-12 Michael Meffie   (1786) viced: host hash address collisions
    2010-07-12 Matt Benjamin    (2229) An RPC test dispatch library for vice
    2010-07-12 Andrew Deason    (2370) GetInodeSummary: free inode info
    2010-07-12 Simon Wilkinson  (2384) Linux: Actually use freezer compatibility func
    2010-07-12 Simon Wilkinson  (2383) Linux: Use freezer compatibility macros in RX
    2010-07-10 Jason Edgecombe  (2382) Fix an error. Replace "May" with "June" in the June newsletter
    2010-07-10 Russ Allbery     (2378) Update config.guess and config.sub to 2009-12-30 and 2010-01-22
    2010-07-10 Russ Allbery     (2377) Make config.sub executable
    2010-07-10 Russ Allbery     (2381) Terminate the DARWIN80 #if in afs_osidnlc.c
    2010-07-10 Russ Allbery     (2379) Fix ktime test for errors
    2010-07-10 Russ Allbery     (2380) Include linux/freezer.h in rx_kmutex.c
    2010-07-09 Andrew Deason    (2357) Use afs_sfsize_t for *_SIZE results
    2010-07-09 Benjamin Kaduk   (2373) Remove incorrect critical section use in dnlc_lookup
    2010-07-09 Michael Meffie   (2374) wiki url changed
    2010-07-09 Michael Meffie   (2369) build fix on older linux
    2010-07-08 Alexander Ivan Redinger (2348) SOURCE-MAP updates
    2010-07-08 Jonathan Billings (2364) Update the Red Hat spec file to include fssync-debug man pages
    2010-07-08 Simon Wilkinson  (2320) vos: Don't call SubEnumerate twice
    2010-07-08 Derrick Brashear (2363) macos relnotes fix dangling link to redangle
    2010-07-08 Andrew Deason    (2359) Fix VPrintDiskStats_r logging
    2010-07-08 Andrew Deason    (2358) viced: Remove stray \r
    2010-07-08 Russ Allbery     (2356) Remove a few erroneous NEWS entries for 1.5.75
    2010-07-08 Benjamin Kaduk   (2362) Fix build
    2010-07-08 Benjamin Kaduk   (2360) FBSD: sync with NFS for *pages vnops
    2010-07-08 Jeffrey Altman   (2361) windows web page update for 1.5.75
    2010-07-07 Russ Allbery     (2355) Add NEWS entries for 1.5.75
    2010-07-07 Andrew Deason    (2353) klog: refactor klog_prompter
    2010-07-07 Derrick Brashear (2354) update macos 1.5.75 info
    2010-07-07 Andrew Deason    (2352) Fix shlibafsrpc des.c hp-ux special case
    2010-07-07 Andrew Deason    (2351) HPUX: correct PostPopulateVCache vfsp set
    2010-07-07 Andrew Deason    (2350) HPUX: include proc_iface.h for proc_t
    2010-07-07 Andrew Deason    (2339) UINT_MAX requires limits.h
    2010-07-07 Derrick Brashear (2343) kernel InitPeerParams has bogus branching and dup code
    2010-07-07 Derrick Brashear (2342) 1.5.75 web update
    2010-07-06 Andrew Deason    (2341) HPUX: make osi_procname a stub
    2010-07-06 Andrew Deason    (2340) Fix stray static inline
    2010-07-06 Derrick Brashear (2335) fix newline conventions
    2010-07-06 Derrick Brashear (2334) rxkad heimdal cleanup
    2010-07-06 Jeffrey Altman   (2333) Windows: update release notes for 1.5.75
    2010-07-06 Jeffrey Altman   (2332) Windows: ChangeLog for 1.5.75
    2010-07-06 Derrick Brashear (2328) make openafs 1.5.75
    2010-07-04 Benjamin Kaduk   (2331) FBSD: always close the rx socket when shutting down
    2010-07-04 Benjamin Kaduk   (2330) Do not recurse on the glock in rxk_NewSocketHost
    2010-07-03 Jonathan Billings (2305) Removed kpasswd from openafs-file-list
    2010-07-02 Derrick Brashear (2327) update VAllocVnode logging
    2010-07-02 Andrew Deason    (2286) DAFS: Salvage VG on volume creation error
    2010-07-02 Andrew Deason    (2285) DAFS: Allow FSSYNC salvages on unknown volumes
    2010-07-02 Marc Dionne      (2324) Linux: cache bypass: fix FCSBypass tests
    2010-07-02 Marc Dionne      (2323) Linux: cache bypass: warning fix in afs_bypasscache.c
    2010-07-02 Andrew Deason    (2284) DAFS: Log attempted salvage requests
    2010-07-02 Matt Benjamin    (2215) cache-bypass  explicitly reference pages involved in background i/o
    2010-07-02 Simon Wilkinson  (2316) Build: Let configure pick our lex and yacc
    2010-07-02 Simon Wilkinson  (2283) Build: Rework git version detection
    2010-07-02 Andrew Deason    (2276) vol: Move destroyMe check outside of inUse check
    2010-07-02 Derrick Brashear (2291) VAllocVnode error handling
    2010-07-02 Rainer Toebbicke (2243) Do not call afs_FlushVCBs with afs_xvcache held
    2010-07-02 Derrick Brashear (1959) bosserver force corefiles
    2010-07-02 Marc Dionne      (2325) Linux: cache bypass: remove warning print before panic
    2010-07-02 Marc Dionne      (2322) Linux: cache bypass: warning fixes in afs_pioctl.c
    2010-07-02 Marc Dionne      (2319) Linux: cache bypass: deal with the afs_serverHasNo64Bit case
    2010-07-02 Rainer Toebbicke (2244) Protect truncate_inode_pages when called from osi_VM_FlushPages
    2010-07-02 Marc Dionne      (2317) Linux: cache bypass: avoid unused variable warnings
    2010-07-02 Marc Dionne      (2318) Linux: cache bypass: warning cleanup in afs_daemons.c
    2010-07-02 Simon Wilkinson  (2298) Linux: Fix pagevec use in cache-bypass
    2010-07-01 Benjamin Kaduk   (2315) FBSD: do not recurse on the afs_xvcache write lock
    2010-07-01 Andrew Deason    (2314) Document fs -human
    2010-07-01 Andrew Deason    (2313) fs diskfree displays 'total' not 'kbytes'
    2010-07-01 Andrew Deason    (2311) fs: Correct human-readable output alignment
    2010-07-01 Tom Keiser       (2309) nuke configure options from AIX param files
    2010-07-01 Derrick Brashear (2306) update ticket5 from heimdal
    2010-07-01 Andrew Deason    (2278) Remove --enable-fast-restart configure option
    2010-07-01 Tom Keiser       (2308) DAFS: fix VOL_HDR_IN_LRU state bit tracking

### Patches merged into the stable 1.4.x branch

    Date       Author          Change# Description
    2010-08-13 Marc Dionne      (2553) Linux: Rework statfs super block operations configure test
    2010-08-13 Marc Dionne      (2552) Linux: switch to evict_inode
    2010-08-13 Marc Dionne      (2551) Linux: use %pI4 if NIPQUAD is not available
    2010-08-12 Marc Dionne      (2550) Linux: adapt to truncate sequence changes
    2010-08-12 Marc Dionne      (2549) Linux: 2.6.35 - fsync no longer takes a dentry
    2010-08-11 Andrew Deason    (2422) viced: print uuid string, not uuid itself
    2010-08-11 Andrew Deason    (2526) Include com_err.h in dumpstuff.c
    2010-08-11 Derrick Brashear (2465) vol AttachByName should mimic other volpkg errors
