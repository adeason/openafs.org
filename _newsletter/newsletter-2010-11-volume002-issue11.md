---
title: OpenAFS Newsletter, Volume 2, Issue 11, November 2010
layout: page
---

# OpenAFS Newsletter, Volume 2, Issue 11, November 2010

Welcome to the October issue of the OpenAFS newsletter. This newsletter
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

On October 28th, several people toasted to the celebrate the 10th
anniversary of OpenAFS. May OpenAFS have many more years ahead of it.

1.5.78 was released on November 4. This release includes numerous fixes.

The final vote counts for the afs3-standardization group are
in. Congratulations to Hartmut Reuter and Doug Engert, who are the new chairs.

Chaz Chandler wrote a how-to guide on setting up a buildbot buildslave,
which prompted several people to offer buildslaves. Thanks to many
volunteers, we have working buildslaves for AIX on the POWER architecture,
Fedora Linux on ARM, Debian on ARM. Slaves for RHEL5 x86\_64, OpenSuSE, Mac
OS 10.5 PPC, and MacOS 10.6 x86\_64 are up and working out setup issues.

The IRIX buildslaves now run each build using multiple
processes. Buildbot, now, builds recent gerrit changes that were missed
while buildbot was down.

## AFS Protocol Standardization

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization](http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization)

### PTS Alternate Authentication

[http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names](http://tools.ietf.org/html/draft-brashear-afs3-pts-extended-names)

Status: Seventh Draft

Last update: August 31, 2010

A request for last call will happen soon.

\--Derrick

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

Status: Active

Last Draft Update: Jan 9, 2010

A working implementation of rxgk was demonstrated at the European AFS &
Kerberos Workshop in Pilsen. Whilst there is still work to be done, both
on completing the implementation, and on getting the code into the OpenAFS
tree, this is an important milestone. Slides from the Pilsen talk are
available on their web site, the current rxgk code is, as always,
available on github.

\--Simon Wilkinson

### AFS3 ACL Rights

[http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions](http://tools.ietf.org/html/draft-deason-afs3-acl-restrictions)

Status: Second draft

Last update: January 13, 2010

We're waiting for the afs3-standardization structure to solidify before
proceeding with this. So, no progress right now.

\--Andrew Deason

### Rx Security Object Providing Clear-text Peer Identity Assertions

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

The other week I submitted a new draft to the IETF which implements
the aforementioned changes (as well as a few others).  The new draft
is available at the following URLs:

- [http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv-03](http://tools.ietf.org/html/draft-tkeiser-afs3-volser-tlv-03)
- [http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-03.html](http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-03.html)
- [http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-03.xml](http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-03.xml)
- [http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-02-03.xml.diff](http://openafs.sinenomine.net/~tkeiser/i-d/draft-tkeiser-afs3-volser-tlv-02-03.xml.diff)
- [file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.txt](file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.txt)
- [file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.html](file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.html)
- [file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.xml](file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-03.xml)
- [file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-02-03.xml.diff](file:///afs/sinenomine.net/user/tkeiser/public\_html/i-d/draft-tkeiser-afs3-volser-tlv-02-03.xml.diff)

The complete revision history is as follows:

- split unsigned 64-bit type down into several more descriptive types
that allow the TLV data stream to be more self-describing.
- add a signed 64-bit integer type to allow for relative timestamps
- now that we have more descriptive types, use them in a number of places
- change AFSVOL\_TLV\_TAG\_VOL\_TRANS\_CALL\_VALID into a boolean type payload
- make sure rxgen can parse the XDR in the appendix
- make sure generated C code compiles and links
- add in-text cites for AFS3-VVL, AFS3-FSCM, DAFS, and OSD.
- provide motivations for GetCapabilities RPC
- provide protocol semantic definitions for each newly allocated capability bit
- allocate AFSVOL\_TLV\_FLAG\_MORE bit to notify caller when we can't
send all tags due to AFSVOL\_TLV\_TAG\_MAX length limit

Any comments or feedback are appreciated.

\--Tom

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

A fix for salvaging attached volumes (gerrit 2329) was merged, and an
issue was found with it that was fixed and merged in gerrit 3272.
fssync-debug will now automatically run the DAFS-specific version with
the merged gerrit 2480. Some salvage-related parallel I/O extensions
were added in gerrit 1864, but are not yet enabled. A fix for releasing
a volume reference prematurely was merged in gerrit 2968.

\--Andrew

Since DAFS is now part of the main development stream, this section will
not appear in future newsletters.

\--Editor

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

The Quickstart Guide was updated to include requirements for partitions
and how to use the AlwaysAttach file to override those requirements. There
was a minor update to the RedHat and Fedora installation instructions to
use Yum instead of RPM. A reference to the salvager command was changed to
dasalavager for the DAFS context, and some commands in the DAFS file
server instructions were fixed. The RPM package names in the guide were
updated to reflect the ones available from the OpenAFS web site.

The fs minidump man page was updated to show the default location of the
dump file.

\--Jason

### Virtual Machine Images

Project Contact:

- Fabrizio Manfredi <fabrizio.manfredi@gmail.com>

We have update the vm images with the openafs 1.5.77. The files are
available at http://sourceforge.net/projects/s3afs/files/

\--Fabrizio

### Rx OSD integration & Raw Vicep Access in Clients

Project Contacts:

- Hartmut Reuter <reuter@rzg.mpg.de>
- Felix Frank <Felix.Frank@Desy.de>
- Christof Hanke <hanke@rzg.mpg.de>

Since the OpenAFS meeting in Pilsen I have started to send code for RXOSD
to gerrit. So the integration of OpenAFS/OSD starts to be in progress.

The new client will unconditionally be prepared for RXOSD and VICEP-access
so that it can be used in all cells whether they use RXOSD or not.

The server side will require expicit --enable-object-storage and/or
\--enable-vicep-access, however, because I suppose that most cells also in
the future will prefere to run their cell without these new features.

\--Hartmut

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

- Active Directory Back-end for Ptserver - November 2009
- Extended Callback Information - January 2010
- Mac OS X OpenAFS Preference Pane - April 2010
- S3 Front-end for AFS - July 2010
- User-space cache manager - July 2010 (1.6 still not released yet)
- Kerberos v5 and multiple encryption types - July 2010
- Per-File ACLs - August 2010

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Patches merged into the master branch:
    Month   Number of Commits
    2010-11   61 (Partial month)
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
    2009-10  154
    2009-09  142

    Patches merged into the stable 1.4.x branch:
    Month   Number of Commits
    2010-11   5 (Partial month)
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
    2009-10   7
    2009-09   8

### Patches merged into the master branch

    Date       Author          Change# Description
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
    2010-11-15 Marc Dionne      (3298) Lockless path through afs_linux_dentry_revalidate
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
    2010-10-31 Simon Wilkinson  (3204) Import of code from heimdal
    2010-10-31 Simon Wilkinson  (3202) auth: Use Kernel XDR for kernel tokens
    2010-10-31 Simon Wilkinson  (3201) util: netutils never builds in the kernel ...
    2010-10-31 Simon Wilkinson  (3190) Import of code from heimdal
    2010-10-31 Simon Wilkinson  (3203) Import still more files from libroken
    2010-10-31 Marc Dionne      (3199) Linux: remove stale prototype and references for read_super
    2010-10-30 Jason Edgecombe  (3158) Quickstart Guide: Add some verbiage about /vicepXX/AlwaysAttach
    2010-10-30 Marc Dionne      (3198) rxosd: allow parallel make
    2010-10-30 Rod Widdowson    (3197) QuickStart Unix: use dafs type and name for demand attach file services
    2010-10-30 Benjamin Kaduk   (3196) FBSD: correct and simplify vcache eviction routines
    2010-10-30 Benjamin Kaduk   (3195) FBSD: lock interlock around v_usecount accesses
    2010-10-30 Derrick Brashear (3163) RPM scripts should allow newbinary restart to restart
    2010-10-29 Derrick Brashear (3192) What the cache manager needs to know about rxosd
    2010-10-29 Chas Williams - CONTRACTOR (3012) afs: clean afs_osi_Alloc() usage
    2010-10-29 Chas Williams - CONTRACTOR (3010) afs: afs_osi_Alloc_NoSleep() cleanup
    2010-10-29 Chas Williams - CONTRACTOR (3011) afs: simplify afs_osi_alloc.c
    2010-10-29 Rod Widdowson    (3193) windows: terminate multi_sz correctly
    2010-10-29 Rod Widdowson    (3176) windows: native versions of ih_pread and ih_pwrite
    2010-10-29 Jeffrey Altman   (3179) vol: Use OSI_NULLSOCKET and not -1 to indicate invalid fssync fd
    2010-10-29 Jeffrey Altman   (3178) vol: Always use INVALID_FD to indicate an invalid fd
    2010-10-29 Phillip Moore    (3009) Fix fs bypassthreshold to accept a size of -1 to disable
    2010-10-29 Phillip Moore    (3008) fs getfid defaults to '.', like other path-related commands
    2010-10-29 Phillip Moore    (3007) fs getfid output changed for consistency with Windows implementation
    2010-10-29 Phillip Moore    (3005) Makes fs getfid error handling consistent with other fs commands
    2010-10-29 Jeffrey Altman   (3181) Windows: Finish converting vol apps to pthread only
    2010-10-29 Simon Wilkinson  (3189) Import: Add roken files from heimdal
    2010-10-29 Simon Wilkinson  (3188) shlib-build: Add ignore option
    2010-10-29 Marc Dionne      (3185) ubik: Set but not used variables
    2010-10-29 Marc Dionne      (3184) bucoord: Set but not used variables
    2010-10-29 Marc Dionne      (3183) xstat: Set but not used variables
    2010-10-29 Benjamin Kaduk   (3186) FBSD: fix dumb panic when we can't pfind rxk_Listener
    2010-10-28 Derrick Brashear (3149) explain yacc build product dependency so it is not removed
    2010-10-28 Marc Dionne      (3165) bucoord: parallel make fix
    2010-10-28 Rod Widdowson    (3182) Windows:  fix built in touch
    2010-10-27 Rod Widdowson    (3175) windows: preserve lasterror prior to calling free
    2010-10-27 Derrick Brashear (3174) don't duplicate work of ctime_s
    2010-10-27 Derrick Brashear (3173) viced don't double-print start time
    2010-10-27 Simon Wilkinson  (3100) Import of code from heimdal
    2010-10-27 Simon Wilkinson  (3099) Improve commit messages for git imports
    2010-10-27 Derrick Brashear (3001) down with assert, up with osi_Assert
    2010-10-27 Jason Edgecombe  (3164) Quickstart Guide: misc. fixes
    2010-10-27 Derrick Brashear (3162) kill defunct tools directory
    2010-10-27 Jeffrey Altman   (3161) Windows: 1.5.78 Change Log summary
    2010-10-26 Jason Edgecombe  (3159) Quickstart guide: use yum install from openafs repo
    2010-10-26 Jeffrey Altman   (3148) Windows: Fix math error in rx_Writev processing
    2010-10-26 Simon Wilkinson  (3138) rx: Don't let timeouts force fast recovery
    2010-10-26 Simon Wilkinson  (3137) rx: Fix starting of transmit timers
    2010-10-26 Simon Wilkinson  (3136) rx: Refactor transmit queue wakeup
    2010-10-26 Simon Wilkinson  (3135) rx: Fix resend accounting
    2010-10-26 Simon Wilkinson  (3134) rx: Use a structure for the xmit list
    2010-10-26 Jeffrey Altman   (3147) Windows: move debug break in afsd_notifier
    2010-10-26 Benjamin Kaduk   (3145) Fix build on systems with .y.o rules
    2010-10-26 Benjamin Kaduk   (3035) FBSD: band-aid vnode locking in lookup
    2010-10-26 Benjamin Kaduk   (3146) Complete change from dcb40c9fb8 for FBSD
    2010-10-24 Derrick Brashear (2991) add objc build rules to make-type makefiles
    2010-10-24 Jeffrey Altman   (3034) Windows: Add version number to event log start pending message
    2010-10-23 Jeffrey Altman   (3033) Windows: register idle dead timeout error
    2010-10-23 Simon Wilkinson  (3031) rx: Tidy up variables in RTT calc
    2010-10-23 Simon Wilkinson  (3030) rx: Fix bracing on rx_clock macro arguments
    2010-10-23 Simon Wilkinson  (3029) rx: More improvments to RTT calculation
    2010-10-23 Jeffrey Altman   (3032) Windows: Make Rx PMTU discovery configurable; disable by default
    2010-10-23 Asanka Herath    (2977) Windows: Backup and restore configuration across installs
    2010-10-23 Jeffrey Altman   (3027) Rx: Fix socket() handling so errors are properly detected
    2010-10-23 Jeffrey Altman   (3026) Rx: Treat rx_minPeerTimeout not as a minimum but as padding
    2010-10-22 Derrick Brashear (3028) linux fh_to_dentry can return err
    2010-10-22 Chas Williams - CONTRACTOR (3023) afs: fix SOLARIS builds conflicting 'u' define
    2010-10-22 Jeffrey Altman   (2999) Windows: Use rx_Readv / rx_Writev
    2010-10-21 Jeffrey Altman   (3025) Windows: Fix i386_w2k and i386_nt40 path construction
    2010-10-21 Jeffrey Altman   (3022) Windows: Improve cm_SyncOpDone logging
    2010-10-21 Jeffrey Altman   (3021) Windows: remove unnecessary prototype from smb.c
    2010-10-21 Jeffrey Altman   (3020) Windows: optimize cm_BkgDaemon()
    2010-10-21 Jeffrey Altman   (3019) Windows: remove warnings from cm_daemon.c
    2010-10-21 Jeffrey Altman   (3018) Windows: prototype cm_PerformanceTuningInit()
    2010-10-21 Jeffrey Altman   (3017) Rx: prototype rx_StateClienThread()
    2010-10-21 Chas Williams - CONTRACTOR (3015) rx: remove spurious compare for maxDgramPackets
    2010-10-21 Jeffrey Altman   (3016) Rx: rx_stats_active not RXDEBUG
    2010-10-19 Chas Williams - CONTRACTOR (2998) Allow private implementations of osi_AllocSmall/LargeSpace
    2010-10-19 Derrick Brashear (3006) atomic mutex don't recursive enter
    2010-10-18 Derrick Brashear (3000) afs assert should use afs abort
    2010-10-18 Simon Wilkinson  (2960) rx: Simplify round trip time calculation
    2010-10-18 Andrew Deason    (2982) RX: Add rx_InterruptCall
    2010-10-18 Jeffrey Altman   (2997) Rx: Do not compute RTT on non-last packets of a jumbogram
    2010-10-18 Simon Wilkinson  (2958) Rx: Reject out of order ACK packets
    2010-10-18 Derrick Brashear (2996) vutil use lockfile mutex macros for lockfile mutex
    2010-10-18 Derrick Brashear (2944) shakeloosevcaches drop xvcache during dentry ops
    2010-10-17 Derrick Brashear (2995) rename afs/assert.h to afs/afs_assert.h
    2010-10-16 Andrew Deason    (2993) pts: Prevent creating negative user ids
    2010-10-15 Andrew Deason    (2994) pts: Specifically check for group id 0
    2010-10-15 Russ Allbery     (2985) Return SRV record ports in network byte order
    2010-10-15 Derrick Brashear (2965) OSX prefspane use Kerberos Preferences for defaults
    2010-10-15 Chas Williams - CONTRACTOR (2981) Rx: fix dpf() usage with regard to trailing \n's
    2010-10-15 Jeffrey Altman   (2988) Util: include assert.h in pthreads_nosig.h when required
    2010-10-15 Jeffrey Altman   (2987) Rx: use osi_Assert/osi_Panic instead of assert
    2010-10-15 Marc Dionne      (2989) LINUX/osi_vnodeops.c: minor coding style fixes
    2010-10-14 Jeffrey Altman   (2978) Rx: function return type on separate line
    2010-10-14 Andrew Deason    (1864) Parallel I/O extensions to namei backend
    2010-10-14 Marc Dionne      (2975) Linux: fix statfs configure test
    2010-10-14 Tom Keiser       (2980) rx: fix typo in rx_atomic Solaris backend
    2010-10-14 Simon Wilkinson  (2959) rx: Don't count unknown packets as missing
    2010-10-14 Jeffrey Altman   (2966) Rx: Consolidate wait for tq busy and make its use uniform
    2010-10-14 Simon Wilkinson  (2957) rx: Don't malloc the xmit list
    2010-10-14 Andrew Deason    (2973) LINUX: old kernel warning fixes
    2010-10-14 Tom Keiser       (2968) don't release Volume lightweight ref too early
    2010-10-14 Hans-Werner Paulsen (2972) wrong rule to make afsd_fuse
    2010-10-14 Marc Dionne      (2976) Linux: fix aklog -setpag to work with ktc_SetTokenEx
    2010-10-14 Andrew Deason    (2947) RX: Force sane timeout values
    2010-10-14 Andrew Deason    (2967) RX: Adjust all timeouts for RTT
    2010-10-13 Tom Keiser       (2970) trailing commas make xlc a sad panda
    2010-10-13 Tom Keiser       (2971) update fssync-debug to handle the VOL_LOCKED flag
    2010-10-13 Chas Williams - CONTRACTOR (2943) Use bigger I/O sizes for the memcache
    2010-10-13 Simon Wilkinson  (2963) hcrypto: Tidy up some merge conflicts
    2010-10-13 Andrew Deason    (2946) LINUX: Build fixes for older kernels
    2010-10-12 Simon Wilkinson  (2956) rx: Don't call gettimeofday for every packet ack
    2010-10-12 Jeffrey Altman   (2964) Windows: Build hcrypto shared library
    2010-10-12 Jeffrey Altman   (2961) Windows: Cleanup build scripts; no include\afs or include\rx
    2010-10-12 Simon Wilkinson  (2962) Fix rxperf includes
    2010-10-11 Simon Wilkinson  (2955) rx: Indent dpf definition
    2010-10-11 Simon Wilkinson  (2954) Import of code from heimdal
    2010-10-11 Simon Wilkinson  (2953) Heimdal: Import rand-w32.c for hcrypto on Windows
    2010-10-11 Jeffrey Altman   (2950) Windows: Do not issue RXAFS change RPCs on known RO volumes
    2010-10-11 Simon Wilkinson  (2896) Unix: Rework build system
    2010-10-11 Andrew Deason    (2480) fssync-debug: exec DAFS version if DAFS detected
    2010-10-11 Phillip Moore    (2948) Extract the .version file when building the srpm file
    2010-10-11 Benjamin Kaduk   (2951) Revert "FBSD: in lookup, when ISDOTDOT, unlock dvp"
    2010-10-06 Benjamin Kaduk   (2942) FBSD: in lookup, when ISDOTDOT, unlock dvp
    2010-10-06 Phillip Moore    (2940) Added missing CLI argument dropped during last commit.
    2010-10-05 Jeffrey Altman   (2913) Windows: do not leak cm_volume_t objects from LRU queue
    2010-10-05 Phillip Moore    (2914) Quick Start Guide updated for RHEL rpms, and CLI syntax
    2010-10-05 Christof Hanke   (2912) volserver: Do not return ENOMEM on AIX from XVolListPartitions
    2010-10-05 Jeffrey Altman   (2910) Windows: Kill AFS_LARGEFILES preprocessor symbol
    2010-10-05 Jeffrey Altman   (2880) rx: Reduce dependence on call->lock
    2010-10-05 Simon Wilkinson  (2908) Irix: Make compiler less chatty
    2010-10-05 Simon Wilkinson  (2904) hcrypto: Fix builds on Irix
    2010-10-05 Simon Wilkinson  (2907) Import of code from heimdal
    2010-10-05 Simon Wilkinson  (2906) Yet more imports from libroken
    2010-10-05 Simon Wilkinson  (2870) Kill AFS_64BIT_ENV
    2010-10-05 Simon Wilkinson  (2909) Revert "util: Add base64 from Heimdal's roken"
    2010-10-05 Simon Wilkinson  (2902) Import yet more files from Heimdal
    2010-10-05 Simon Wilkinson  (2903) Import of code from heimdal
    2010-10-04 Simon Wilkinson  (2901) Heimdal: Fix 32bit build problems
    2010-10-04 Andrew Deason    (2893) vol: Log ignored dirs that look like partitions
    2010-10-04 Simon Wilkinson  (2900) util: Add base64 from Heimdal's roken
    2010-10-04 Simon Wilkinson  (2899) hcrypto: Build fixes
    2010-10-04 Simon Wilkinson  (2898) Import of code from heimdal
    2010-10-04 Simon Wilkinson  (2897) Add more files from Heimdal
    2010-10-04 Simon Wilkinson  (2895) configure: Don't let autoconf pick our CFLAGS
    2010-10-04 Simon Wilkinson  (2894) configure: Restore saved CFLAGS
    2010-10-03 Marc Dionne      (2892) Remove duplicate rx_stats targets in libuafs Makefile
    2010-10-03 Andrew Deason    (2731) vos release: Force full dump on RO_DONTUSE sites
    2010-10-03 Chas Williams - CONTRACTOR (2891) sin_family is not network order
    2010-10-03 Derrick Brashear (2890) rx stats atomic inclusion needs kmutexes for emulation
    2010-10-03 Jeffrey Altman   (2887) Windows: Ensure that cm_NameI errors are acted upon promptly
    2010-10-03 Jeffrey Altman   (2886) Windows: Fix Parent(path) computation to permit mp and symlink creation
    2010-10-03 Derrick Brashear (2885) add rxstats to kernel
    2010-10-03 Marc Dionne      (2888) Conditionalize include of string.h in rx_stats.c
    2010-10-03 Marc Dionne      (2889) Linux: correct use of atomic_add and atomic_sub functions
    2010-10-02 Jeffrey Altman   (2882) Rx: Fix RXDEBUG_PACKET builds
    2010-10-02 Jeffrey Altman   (2881) Rx: raise rx_minPeerTimeout to 20ms
    2010-10-02 Jeffrey Altman   (2871) Rx: When call receive is done, send ack all packet
    2010-10-02 Jeffrey Altman   (2837) Rx: protect rx_conn and rx_call refCount field with rx_refcnt_mutex
    2010-10-02 Derrick Brashear (2884) darwin kernel atomics
    2010-10-02 Chas Williams - CONTRACTOR (2877) add option to rxperf to use rx_Readv() instead of rx_Read()
    2010-10-02 Jeffrey Altman   (2883) Windows: Pass Volume Root Fid to cm_Analyze after RXAFS_GetVolumeStatus
    2010-10-02 Andrew Deason    (1863) Provide an abstract thread pool object
    2010-10-02 Andrew Deason    (1862) Provide an abstract work queue object
    2010-10-02 Derrick Brashear (2875) exempt instant timeouts from mtu discovery
    2010-10-02 Andrew Deason    (2759) DAFS: Raise LogLevel for per-chain vol stats
    2010-10-01 Chas Williams - CONTRACTOR (2876) rename some variables in rxperf

### Patches merged into the stable 1.4.x branch

    Date       Author          Change# Description
    2010-11-16 Marc Dionne      (3313) Linux: fix statfs configure test
    2010-11-15 Anders Kaseorg   (3308) Linux: Fix prototypes for afs_xsetgroups and sys_setgroupsp and friends
    2010-11-15 Anders Kaseorg   (3307) Linux: Fix prototypes for sys_setgroups_stub and sys32_setgroups_stub
    2010-11-15 Alejandro R. Sedeno (3288) Linux: use DEFINE_MUTEX for afs_linux_alloc_sem on newer kernels
    2010-11-15 Derrick Brashear (3286) Do not call afs_FlushVCBs with afs_xvcache held
    2010-10-27 Michael Meffie   (2431) Calculate midnight (for volume stats) based on standard functions
    2010-10-27 Derrick Brashear (2945) shakeloosevcaches drop xvcache during dentry ops
    2010-10-27 Andrew Deason    (2424) GetInodeSummary: free inode info
    2010-10-27 Andrew Deason    (2209) VGetVolume_r: do not wait for offlining volumes
    2010-10-27 Simon Wilkinson  (2290) Linux: Make keyring destructor remove all tokens
    2010-10-11 Andrew Deason    (2879) Use afs_foff_t for offsets
    2010-10-11 Andrew Deason    (2423) Use afs_sfsize_t for *_SIZE results
