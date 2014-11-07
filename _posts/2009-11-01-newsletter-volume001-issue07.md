---
title: OpenAFS Newsletter, Issue 7, November 2009
layout: page
category: newsletter
permalink: /newsletter/newsletter-2009-11-volume001-issue07.html
---

# OpenAFS Newsletter, Issue 7, November 2009

Welcome to the seventh issue of the OpenAFS newsletter. This newsletter
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

In reply to Derrick's request for a pony, here it is: "u". Unfortunately,
a Nethack pony is all that we have the budget for. ;)

## General OpenAFS Progress

OpenAFS 1.5.66 was released on October 24. Key highlights include support
for Windows 7 and Server 2008R2.

October's discussion of the AFS lock icon was concluded. The OpenAFS
provider in Network Identity Manager now includes a lock icon which shows
OpenAFS status and token status similar to the old AFScrds program. The
network mount functionality in AFScreds is now shipped disabled by
default.

Simon Wilkinson and Derrick Brashear put out a call for code reviewers. We
need people to review the pending changes in Gerrit. Everyone is welcome
to review some code. It can help those who aren't familiar with the code
to become more familiar with it. To get started in reviewing, go to
[http://gerrit.openafs.org](http://gerrit.openafs.org) and login using your OpenID
credentials. Download the patch and apply it to the latest git tree, then
compile it and test it. Report your results with each patch in Gerrit. If
you need help getting started, ask on the openafs-devel list, the \#openafs
IRC channel or the Jabber chat room.

Mike Meffie proposed a finer set of access controls to prevent users with
admin rights on a folder from giving overly permissive access to other
users or groups. This is part of a effort to find a safer way to deal with
public facing AFS sites. We want to encourage people to chime in with
their ideas and reach a general census so we can move forward and improve
AFS.

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

## Projects

### AFS Protocol Standardization

Two more proposals came out of the Edinburg AFS Hackathon, but haven't
been discussed much on the afs-standardization list:

- http://www.dementia.org/~shadow/draft-brashear-afs3-pts-extended-names-00.html
- http://openafs.sinenomine.net/~tkeiser/draft-tkeiser-rxrpc-sec-clear-00.html

Mike Meffie reformatted Nickolai Zeldovich's draft Rx protocol
specification (from 2002) as an Internet Draft and, with his permission, is
sharing it.

The reformatted document is available via http and AFS at:

[http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html](http://openafs.sinenomine.net/~mmeffie/rfc/draft-zeldovich-rx-spec-00.html)

/afs/sinenomine.net/user/mmeffie/public/rfc/draft-zeldovich-rx-spec-00.html 

\[Ed.: I give my thanks to Simon Wilkinson for providing an excellent
summary of the current status of the proposals. Most of this section was
taken from one of Simon's emails.\]

Discussion on these proposals is welcome and should be done on the
AFS3-standardization list at
[http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization](http://michigan-openafs-lists.central.org/mailman/listinfo/afs3-standardization)

#### AFS Callback Extensions

[http://www.ietf.org/id/draft-benjamin-extendedcallbackinfo-00.txt](http://www.ietf.org/id/draft-benjamin-extendedcallbackinfo-00.txt)

Status: Active

We need to decide whether we're going to wait for the RPC refresh changes
before publishing extended callbacks. My belief is that that's the only
factor currently delaying this document. The question here, essentially,
is whether anyone would deploy extended callbacks before deploying updated
RPCs. To date, nobody has said they would do so.

\--Simon Wilkinson

#### DNS SRV Resource Records for AFS

[http://www.ietf.org/id/draft-allbery-afs-srv-records-01.txt](http://www.ietf.org/id/draft-allbery-afs-srv-records-01.txt)

Status: Active

I think this is pretty much done from our perspective. In this draft's
case, I think it's perfectly fair to get it published through the IETF, as
an individual submission, given it updates a protocol element (AFSDB
records) that are already specified in an RFC.

We have two problems that are delaying this, and other initiatives:

The first is that there has been no movement since last year on
establishing a clearer footing for the work done on this
\[afs3-standardization\] list. The draft I published suggests that the g.c.o
registrars bootstrap the process, but so far they haven't had sufficient
time to do so. At some point, if they remain unable to get it off the
ground, we're going to have to come up with another mechanism.

There is also a general issue about how to publish the wider set of AFS
protocol documents - the current proposal is that they go through the
independent submission stream, and eventually appear as RFCs. To date, I
don't think we've approached anyone with regards to this plan, and the
whole RFC publishing processing is going through significant change at
present. We need to resolve this before things like extended callbacks can
move forwards.

\--Simon Wilkinson

I've received no responses since version -01 of the draft, so I was about
to ask about what the next step is.  Should I make a last call for
comments here and then approach the IESG about publication?

\--Russ Allbery

### Demand-Attach FileServer (DAFS)

Project Contacts:

- Andrew Deason <adeason@sinenomine.net>
- Tom Keiser <tkeiser@sinenomine.net>
- Mike Meffie <mmeffie@sinenomine.net>

A fix for 124484 (volserver salvages) is in gerrit 787 and is undergoing
review. We believe this to be the last 'critical' DAFS issue, so we would
encourage that anyone with an interest in using DAFS test DAFS with that
fix. There are still other (mostly performance-related) issues we are
continuing to work on, but we know of no other critical DAFS-specific
problems.

\--Andrew

### Mac OS X OpenAFS Preference Pane

Project Contact:

- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

The only update is the automatic link creation on the Desktop for custom
paths. Now, I'm trying to see if I can use FUSE to make these paths
mountable as real volumes.

\--Claudio

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Several man page updates have gone into the tree since last month, but I
don't think there's been any significant progress on the larger documents.

One useful documentation project that we could ask for volunteers to work
on is writing man pages for the new binaries that were added as part of
the demand-attach file server work.

\--Russ

### Kerberos v5 and multiple encryption types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

Simon and I discussed some of the issues yesterday via XMPP.  We agree
there are lots of things Marcus and I can do, but a lot of things become
easier and more useful to do when upstream is ready start thinking about
rxk5 in detail.  Simon pointed out that once 1.6 branches, rxk5 patches
can flow onto head--and that means that folks can start reviewing changes
for potential merge.  Even if it takes a while to get through them, that's
the most efficient process to be on, and the sooner we can start it, the
more productive we can be.

\--Matt

### S3 Front-end for AFS

Project Contacts:

- Fabrizio Manfredi <fabrizio.manfredi@gmail.com>
- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

Small description of S3AFS:

First of all, Amazon S3 provides a simple web services interface that can
be used to store and retrieve any amount of data, at any time, from
anywhere on the web.

S3AFS is a web application, it provides a local implementation of the S3
service. This can be useful if you want to make use of the Amazon S3 web
service interface but host the storage on your own OpenAFS cell. The first
step of the project is mapping the OpenAFS resources to a S3 client, then
you can read your file and directory as a key of a S3 bucket. The second
step is to use OpenAFS as an S3 backend.

We have a basic implementation, without authentication and authz, we now
start to understand how to put Authentication (SetAG) in the java multi
thread env.

Progress:

We have a proof of concept, which was presented at the Workshop in Rome,
and we have finished the design and started coding in Java for the
production release. We hope to release a preview in December without ACL
handling. We have to fix some compilation problems in the Java lib in the
1.5.x, which has not been submitted yet.

\--Fabrizio

### Active Directory Backend for Ptserver

Project Contacts:

- Fabrizio Manfredi <fabrizio.manfredi@gmail.com>
- Claudio Bisegni <Claudio.Bisegni@lnf.infn.it>

Ptserver-Ng is a custom implementation of the ptserver with an Active
Directory backend instead of Ubik db. Today, more institutions ask to me a
more generic interface in special way for ldap connection. The new project
is focused on a plugin architecture for a multi-backend
implementation. The first step is to create a more generic database API
(ptdb) and move all the ubik code into this new infrastructure.  Second
step is to create a proxy read/write backend and more generic AD (read
only) backend.

Status : interface definition (ptdb api)

We have finished the interface definition, we start to move
the existing ubik code, no release date are available.

### Virtual Machine Images

Project Contact:

- Fabrizio Manfredi <fabrizio.manfredi@gmail.com>

I have created a set of virtual machines. In this way, everyone can try and
test OpenAFS without installing it.

You can find the VM at:
http://sourceforge.net/projects/s3afs/files/

\--Fabrizio

### Pthreaded Ubik

Project Contact:

- Steven Jenkins <steven.jenkins@gmail.com>

Steven has changed employers and email addresses.

There are no updates to the Pthreaded Ubik project. It will not appear in
future newsletters unless there is an update.

### Userspace cache manager

Project Contact:

- Andrew Deason <adeason@sinenomine.net>

I'm in the middle of adding support for ACL and mountpoint manipulation
(and in general, making pioctl emulation work). Once that is working to
a certain degree, I should be able to work on getting this suitable for
merging in mainline. If anyone wants to use this before then, just ask.

I'd also like to note that apparently it may be possible to emulate PAGs
in linux userspace. So, a fully-featured FUSE client is not as
impossible as I once thought, and may someday exist.

\--Andrew

### Projects with no progress or no update

- Disconnected AFS support
- Rx OSD integration & Raw Vicep Access in Clients
- Extended Callback Information
- \*BSD Support
- OpenAFS Server Preference Based on Network Conditions

## Gerrit Activity

To review a change, go to http://gerrit.openafs.org/\#change,NUM where NUM
is the Change\# shown in the lists below.

### Statistics

    Number of patches waiting for review: 36

    Patches merged into the master branch:
    Month   Number of Commits
    2009-11   56  (Partial month)
    2009-10  154
    2009-09  142
    2009-08   78
    2009-07  181

    Patches merged into the stable branch:
    Month   Number of Commits
    2009-11  15  (Partial month)
    2009-10   7
    2009-09   8
    2009-08  17
    2009-07   5

### Patches waiting for review

    Date       Author         Change# Description
    2009-11-19 Michael Meffie   (619) volser transaction object race conditions
    2009-11-19 Andrew Deason    (786) Expand ProgramType enumeration
    2009-11-19 Marc Dionne      (847) src/pam warning fixes
    2009-11-18 Andrew Deason    (845) Define afs_maxvcount everywhere
    2009-11-18 Andrew Deason    (846) Define WCOREDUMP in salvsync-server.c
    2009-11-18 Simon Wilkinson  (838) Kernel is always defined
    2009-11-18 Mickey Lane      (840) Fix 2 errors in Windows release Notes
    2009-11-18 Simon Wilkinson  (837) Move GLOCK initialisation to platform directories
    2009-11-18 Andrew Deason    (709) Break origin's callback for RXAFS_Rename target
    2009-11-18 Simon Wilkinson  (796) Add printf format checks to the rest of tree
    2009-11-16 Jeffrey Altman   (829) Windows: Permit custom version numbers and default cellname
    2009-11-15 Jeffrey Altman   (827) Windows: Improvements to background fetch processing
    2009-11-15 Jeffrey Altman   (824) Windows: cm_BkgDaemon requeuing only applies to BkgStore
    2009-11-15 Jeffrey Altman   (828) Windows: buf_DirtyBuffersExist uses fileHashp not allp list pointer
    2009-11-14 Marc Dionne      (730) Linux: Keyrings PAG handling changes
    2009-11-13 Andrew Deason    (736) Correct duplicate special inodes while salvaging
    2009-11-13 Rainer Toebbicke (799) Flexible client buffer growth
    2009-11-13 Simon Wilkinson  (820) Fix prepare and commit_write to do the right thing
    2009-11-12 Andrew Deason    (787) DAFS: Allow non-fileserver to schedule salvages
    2009-11-12 Simon Wilkinson  (792) Add printf format checks to the cache manager
    2009-11-12 Derrick Brashear (783) conservative dynamic vcache fix for 14x
    2009-11-12 Andrew Deason    (776) Check for (hostFlags & HOSTDELETED) after h_Lock_r
    2009-11-12 Simon Wilkinson  (795) Add printf format checks to rx
    2009-11-11 Simon Wilkinson  (726) Linux: Use atomics for credential reference counts
    2009-11-08 Simon Wilkinson  (793) Add printf format checks to util's log functions
    2009-11-08 Simon Wilkinson  (794) Add printf format checks to afs_com_err()
    2009-11-04 Derrick Brashear (451) macos knote fsevents hinting
    2009-11-04 Andrew Deason    (436) Avoid unnecessarily updating .. in SAFSS_Rename
    2009-11-04 Evan Broder      (778) Increase the maximum number of sysnames
    2009-11-04 Michael Meffie   (215) Print throttled packet counts with rxdebug
    2009-10-26 Jacob Thebault-Spieker (433) Add throughput framework to cm_RankServer()
    2009-09-09 Matt Benjamin    (435) clear stat flag on renamed directories
    2009-08-29 Matt Benjamin    (376) K5SSL by Marcus Watts
    2009-08-27 Jeffrey Altman   (319) Use xdr_alloc and xdr_free within ptuser
    2009-07-29 Michael Meffie   (147) Fix bosserver directory creation
    2009-07-24 Hartmut Reuter    (70) preparing rxosd integration: change in AFSFetchStatus

### Patches merged into the master branch

    Date       Author         Change# Description
    2009-11-18 Andrew Deason    (842) Define T_SRV when not defined for us
    2009-11-18 Andrew Deason    (843) src/afs/afs_user.c typo
    2009-11-18 Andrew Deason    (844) AIX: Missing brace in afs_vnop_flock.c
    2009-11-18 Matt Benjamin    (584) viced ihandle boost
    2009-11-18 Simon Wilkinson  (839) Name chunkOps structure elements
    2009-11-18 Michael Meffie   (841) fix for volser transaction object race conditions
    2009-11-18 Simon Wilkinson  (835) Linux: Fix lock ordering
    2009-11-18 Marc Dionne      (836) aklog build fix: com_err.h header
    2009-11-17 Simon Wilkinson  (834) Rationalise our include paths
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
    2009-10-30 Marc Dionne      (753) Linux: remove unused cr->next member in struct afs_cred
    2009-10-29 Simon Wilkinson  (754) Cleanup cache bypass
    2009-10-29 Andrew Deason    (747) Avoid using released hosts
    2009-10-29 Simon Wilkinson  (751) Coding style cleanup
    2009-10-28 Simon Wilkinson  (744) Make afsd.pod reflect reality
    2009-10-28 Simon Wilkinson  (748) Move PMTU header block to top of file
    2009-10-27 Andrew Deason    (717) Avoid prematurely destroying callback_rxcon
    2009-10-26 Marc Dionne      (742) afs_buffer.c: fix uninitialized variable warning
    2009-10-26 Simon Wilkinson  (741) Use fewer #ifdefs for dynamic vcaches
    2009-10-26 Simon Wilkinson  (743) Make cache bypass build again
    2009-10-26 Simon Wilkinson  (738) Remove hardcoded maximum time
    2009-10-26 Simon Wilkinson  (740) Fix dynamic vcache / rxmaxmtu cmd id collision
    2009-10-26 Simon Wilkinson  (739) Remove pininodes
    2009-10-26 Simon Wilkinson  (737) Fix locking in afs_buffer.c
    2009-10-26 Andrew Deason    (735) Dec old special inodes in inode convertROtoRW
    2009-10-26 Matt Benjamin    (268) viced (non atomic) refcount/more-threads
    2009-10-26 Jeffrey Altman   (733) ubik_VL_GetAddrsU does not accept a VLCallBack parameter
    2009-10-26 Andrew Deason    (734) Avoid 'salvageserver -client -showlog' segfault
    2009-10-26 Jeffrey Altman   (729) Updates to Jake's RTT based server ranking (Gerrit 317)
    2009-10-26 Jacob Thebault-Spieker (317) Adds cm_RankUpServers() and cm_RankServer()
    2009-10-26 Simon Wilkinson  (732) Clean up console message
    2009-10-25 Simon Wilkinson  (725) Don't return AOP_WRITEPAGE_ACTIVATE to write()
    2009-10-25 Simon Wilkinson  (724) Use user credentials for Linux writepage()
    2009-10-23 Derrick Brashear (723) windows 1.5.66
    2009-10-23 Derrick Brashear (722) make 1.5.66 for unix
    2009-10-23 Michael Meffie   (718) volser transaction object race conditions
    2009-10-23 Simon Wilkinson  (721) Resolve error return issues in writepage
    2009-10-23 Jeffrey Altman   (715) Remove warning from all calls to afsconf_GetExtendedCellInfo
    2009-10-23 Jeffrey Altman   (720) Windows: Notes for 1.5.66
    2009-10-23 Jeffrey Altman   (719) Windows: Updates to Release Notes
    2009-10-22 Simon Wilkinson  (712) Refactor writepage_sync
    2009-10-22 Derrick Brashear (703) pthread pid casting
    2009-10-22 Jeffrey Altman   (714) Windows: no longer use WinExec in afscreds
    2009-10-22 Jeffrey Altman   (713) rx lwp include assert.h where AFS_NT40_ENV builds can see it
    2009-10-22 Jeffrey Altman   (711) Windows: Update Control Panel to use ShellExecuteEx instead of WinExec
    2009-10-22 Derrick Brashear (710) remove spurious log in icl
    2009-10-22 Simon Wilkinson  (708) Add -Wpointer-arith to warning and checking builds
    2009-10-21 Derrick Brashear (668) rx don't exit
    2009-10-21 Simon Wilkinson  (707) Fix fall out from removal of memset casts
    2009-10-21 Jeffrey Altman   (706) Windows: Update MSI installer properties
    2009-10-21 Jeffrey Altman   (705) Windows: ports in the cache manager are stored in network byte order
    2009-10-21 Asanka Herath    (704) Windows: Set the ARPINSTALLLOCATION property when installing
    2009-10-21 Simon Wilkinson  (701) Don't cast the pointer past to memset
    2009-10-21 Matt Benjamin    (645) Make typedefs of AFS_UCRED and AFS_PROC with renaming
    2009-10-21 Andrew Deason    (693) HPUX: Do not sigwait on critical signals
    2009-10-21 Jeffrey Altman   (700) Windows: Add registry entries for rx_SetMinPeerTimeout, rx_SetMaxRecvWindow, rx_SetMaxSendWindow
    2009-10-21 Jeffrey Altman   (663) Windows: Modify afscreds.exe and afs_config.exe to be UAC compatible
    2009-10-21 Jeffrey Altman   (699) Add rx_SetMinPeerTimeout and rx_GetMinPeerTimeout
    2009-10-21 Simon Wilkinson  (692) Use real names for page lock operations
    2009-10-21 Jeffrey Altman   (697) Windows: Do not permit infinite attempts to obtain a pioctl file handle
    2009-10-21 Jeffrey Altman   (698) Windows: digital signatures are required for resource dlls
    2009-10-21 Jeffrey Altman   (661) Windows: Adjust error return values
    2009-10-20 Derrick Brashear (549) rx window size increase
    2009-10-20 Derrick Brashear (694) afscp warnings cleanup
    2009-10-20 Jeffrey Altman   (696) prevent rx peer timeout from reaching 0.0 seconds
    2009-10-20 Jeffrey Altman   (695) Rx warning removal
    2009-10-20 Jeffrey Altman   (690) Windows: AFS_PTR_FMT is just 'p'
    2009-10-20 Andrew Deason    (691) Avoid 'static __inline' on HPUX
    2009-10-20 Simon Wilkinson  (689) Remove pageoff macro
    2009-10-19 Jeffrey Altman   (686) Add server prefix to bumon.xg; avoid rx_call * vs rx_connection * warning
    2009-10-19 Simon Wilkinson  (687) Return both error codes for rxfs_fetchInit
    2009-10-19 Simon Wilkinson  (685) Always unlock pages when returning from writepage
    2009-10-19 Andrew Deason    (684) Fix a couple more unlink()s in vol-salvage.c
    2009-10-19 Asanka Herath    (683) Windows: Add a token status icon to the NIM plug-in
    2009-10-19 Claudio Bisegni  (682) AFSPreference Pane Mounts View refresh issue
    2009-10-19 Claudio Bisegni  (677) OpenAFS Preference Pane 64bit and Symbolic Link features implemented.
    2009-10-19 Andrew Deason    (681) Fix format warnings in tviced/state_analyzer.c
    2009-10-19 Andrew Deason    (680) Prototype encode_krb5_enc_tkt_part for aklog
    2009-10-19 Andrew Deason    (678) Fix a couple of size_t warnings
    2009-10-19 Andrew Deason    (679) Prototype ka_log
    2009-10-18 Simon Wilkinson  (675) Fix warnings in tviced
    2009-10-18 Andrew Deason    (671) Log error messages in volser i/o errors
    2009-10-18 Simon Wilkinson  (673) More warning fixes for kauth
    2009-10-18 Simon Wilkinson  (672) Update warning management
    2009-10-18 Simon Wilkinson  (676) Use ranlib -c for Mac OS X Leopard
    2009-10-17 Simon Wilkinson  (674) afs_Conn must be called within the analyze loop
    2009-10-17 Jeffrey Altman   (670) Windows: Always compute time remaining in cm_Analyze
    2009-10-17 Jeffrey Altman   (669) Windows: mark volume status online during cm_MergeStatus
    2009-10-16 Marc Dionne      (657) Linux: kmem_cache_create fix and cleanup
    2009-10-16 Andrew Deason    (664) Fix rxgen-generated warnings
    2009-10-16 Derrick Brashear (667) exit less
    2009-10-16 Derrick Brashear (666) snowleopard 64 bit warning death
    2009-10-15 Andrew Deason    (647) Detect and use %zu for size_t when available
    2009-10-15 Andrew Deason    (665) Fix unitialized variable warning in cfghost.c
    2009-10-15 Jeffrey Altman   (654) Windows: AFSVolSync creationDate based readonly volume versioning
    2009-10-15 Jeffrey Altman   (662) Windows does not provide sys/wait.h
    2009-10-15 Andrew Deason    (635) Fix warnings in butc, tbutc, and butm
    2009-10-15 Simon Wilkinson  (639) Fix checked builds with gcc4.2
    2009-10-14 Derrick Brashear (594) add SRV record lookups to unix afsconf support suite also
    2009-10-14 Simon Wilkinson  (660) Add fsint dependency to audit builds
    2009-10-14 Jeffrey Altman   (651) Windows: refactor afs status cloning and clone when fs fetchdata bug detected
    2009-10-14 Jeffrey Altman   (659) Revert "Windows: Readonly Volume Versioning for Windows Cache Manager"
    2009-10-14 Jeffrey Altman   (658) Windows: fix build due to broken src/volser/NTMakefile
    2009-10-14 Marc Dionne      (656) Linux: Remove declaration of unused variable filp
    2009-10-13 Jeffrey Altman   (648) Windows: If SecurityLevel is configured use it for vos.exe and pts.exe
    2009-10-13 Andrew Deason    (650) Use f_bsize for ZFS afs_fsfragsize
    2009-10-13 Simon Wilkinson  (636) Add public protoypes for volser
    2009-10-12 Andrew Deason    (649) Formatting typos in pts.pod
    2009-10-12 Simon Wilkinson  (637) Add afsio to gitignore
    2009-10-12 Jeffrey Altman   (579) Windows: Readonly Volume Versioning for Windows Cache Manager
    2009-10-12 Jeffrey Altman   (643) Windows Explorer Shell Extension: Remove OutputDebugString calls
    2009-10-12 Jeffrey Altman   (646) Windows: Correct lock error codes and log file server lockCount
    2009-10-12 Jeffrey Altman   (580) Improve accuracy of Rx RTT calculation by skipping retransmitted packets
    2009-10-11 Matt Benjamin    (642) Use AFS_PROC consistently
    2009-10-11 Simon Wilkinson  (640) Revert "Linux: kmem_cache_create fix and cleanup"
    2009-10-10 Jeffrey Altman   (607) Windows: use port when finding server by address
    2009-10-10 Jeffrey Altman   (634) Windows: Prevent fs fetchdata offset bug error from propagating to caller
    2009-10-09 Andrew Deason    (597) Fix warnings in kauth/authclient.c
    2009-10-09 Andrew Deason    (600) Fix warnings in rxkad
    2009-10-09 Andrew Deason    (592) Correct and use AFS_SIZET_FMT
    2009-10-09 Marc Dionne      (621) Linux: kmem_cache_create fix and cleanup
    2009-10-08 Andrew Deason    (620) Fix warning in vol/namei_ops.c
    2009-10-08 Davor Ocelic     (618) Update README with solved/pending docs tasks
    2009-10-08 Davor Ocelic     (617) Update backup suite manpages
    2009-10-08 Davor Ocelic     (616) Update fstrace suite manpages
    2009-10-08 Davor Ocelic     (615) Minimal left docs updates for vos suite
    2009-10-08 Andrew Deason    (612) Typo in vos_remsite.pod
    2009-10-08 Davor Ocelic     (610) Add POD links (L<>) in pts.pod and symlink.pod
    2009-10-08 Davor Ocelic     (609) Update vos suite manpages
    2009-10-08 Davor Ocelic     (608) Allow check-pod to work on specific files or dirs
    2009-10-08 Davor Ocelic     (611) Update readme with solved and pending tasks
    2009-10-08 Andrew Deason    (602) Reduce warnings in vos.c
    2009-10-08 Andrew Deason    (599) Remove warnings related to type-punning
    2009-10-08 Jeffrey Altman   (606) Windows: use xdr_alloc to allocate memory for Callback data structs
    2009-10-08 Marc Dionne      (605) authclient.c: fix 64-bit specific warnings
    2009-10-08 Jeffrey Altman   (604) Add missing variable to afsio
    2009-10-08 Derrick Brashear (593) Permit DNS SRV record lookups to be used by the Windows afsconf_GetAfsdbInfo
    2009-10-08 Andrew Deason    (603) xdrproc_t functions take a caddr_t, not caddr_t*
    2009-10-08 Andrew Deason    (601) Ignore libafsrpc warnings for shlibafsrpc also
    2009-10-08 Andrew Deason    (598) Fix warnings in lwp/process.c
    2009-10-08 Andrew Deason    (596) Remove a pointer->integer warning in fstrace.c
    2009-10-08 Andrew Deason    (595) Prototype strcasestr in afsmonitor.c
    2009-10-07 Michael Meffie   (216) Allow gnu-style long options
    2009-10-07 Hartmut Reuter   (590) pioctl with VIOC_FS_CMD removed
    2009-10-07 Jeffrey Altman   (587) Build afsio on Windows; remove many warnings
    2009-10-07 Andrew Deason    (591) Make namei convertROtoRW'd volumes usable
    2009-10-07 Simon Wilkinson  (581) Use page_offset() on Linux
    2009-10-07 Jeffrey Altman   (585) Windows: fs listacl -cmd
    2009-10-06 Jeffrey Altman   (586) documentation for "fs listacl -cmd"
    2009-10-06 Derrick Brashear (577) afs_FindService should handle iana portnames
    2009-10-06 Hartmut Reuter   (556) New option '-cmd' for 'fs listacl'
    2009-10-05 Simon Wilkinson  (582) Use standard Linux paths for all headers
    2009-10-05 Claudio Bisegni  (578) OSX Launchd Startup Manage  with Preference Pane
    2009-10-05 Hartmut Reuter   (555) afsio is a command to pipe data into or out of afs files
    2009-10-04 Marc Dionne      (574) Linux: 2.6.32 - Adapt to writeback changes
    2009-10-04 Marc Dionne      (573) rxfs_storePadd: return 0 on success
    2009-10-03 Simon Wilkinson  (569) Refactor linux readpage support
    2009-10-03 Simon Wilkinson  (568) Rationalise some #ifdefs in the LINUX osi layer
    2009-10-03 Simon Wilkinson  (567) Remove pre-Linux 2.6 support
    2009-10-03 Simon Wilkinson  (572) There can be only one ... MD5
    2009-10-03 Derrick Brashear (565) create LINUX24 directory
    2009-10-03 Derrick Brashear (564) launchdaemon support for MacOS
    2009-10-01 Simon Wilkinson  (566) Remove page past end of file optimisations
    2009-10-01 Andrew Deason    (563) DAFS: Wait until preattach to service FSSYNC reqs

### Patches merged into the stable branch

    Date       Author         Change# Description
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
    2009-10-14 Andrew Deason    (655) Use f_bsize for ZFS afs_fsfragsize
    2009-10-13 Andrew Deason    (653) Remove extra arguments to afs_syscall_call
    2009-10-13 Andrew Deason    (652) Make namei_ops.c build again
    2009-10-08 Andrew Deason    (613) Make namei convertROtoRW'd volumes usable
    2009-09-27 Russ Allbery     (500) viced cap fetchdata len to avoid negative
    2009-09-26 Russ Allbery     (497) h_GetHost_r cleanup cases
    2009-09-23 Andrew Deason    (490) Implement _PC_FILESIZEBITS for solaris pathconf
    2009-09-16 Russ Allbery     (462) Add automatic sysname detection for ARM Linux
    2009-09-15 Russ Allbery     (459) fileserver should actually retry VL_RegisterAddrs on failure
    2009-09-14 Simon Wilkinson  (457) Init the vrequest structure correctly
    2009-09-03 Andrew Deason    (398) Update accessDate on volume access
    2009-09-01 Felix Frank      (342) Fixed out-of-tree builds.
    2009-08-31 Michael Meffie   (386) Build on linux 2.4 again
    2009-08-28 Derrick Brashear (366) macos 10.5 doesn't support compiler kext flag
    2009-08-28 Derrick Brashear (363) update decode-panic for 10.6
    2009-08-28 Derrick Brashear (362) macos 10.6 64 bit support
    2009-08-28 Derrick Brashear (361) macos rc script server handling
    2009-08-28 Derrick Brashear (360) macos 10.6 updates
    2009-08-28 Derrick Brashear (359) macos 10.6 package naming
    2009-08-28 Derrick Brashear (358) macos 10.6 amd64 kmod build fix
    2009-08-28 Derrick Brashear (357) macos 10.6 pam support
    2009-08-28 Derrick Brashear (356) OSX lock initialization cleanup
    2009-08-28 Derrick Brashear (355) MacOS 10.6 support update
    2009-08-10 Andrew Deason    (280) Add additional vlprocs safety checks
    2009-08-10 Andrew Deason    (275) Allow specifying vos create/addsite volume IDs
    2009-08-10 Andrew Deason    (274) Ignore SIGSYS when issuing pioctl syscall
    2009-08-07 Andrew Deason    (273) Correcting formatting typo in vos addsite manpage
    2009-08-07 Andrew Deason    (272) Always display vnode accesses in vos output
    2009-08-07 Andrew Deason    (271) Fixing manpage for vos addsite -valid
    2009-07-24 Russ Allbery     (208) Make ktc_curpag generally available
    2009-07-22 Jeffrey Hutzelman (180) Fix afs_GetVolume() for non-root dynroot FIDs
    2009-07-22 Simon Wilkinson  (174) Remove the RCSID macro
    2009-07-22 Simon Wilkinson  (173) Remove CVS ignore files
    2009-07-22 Simon Wilkinson  (172) Revise git ignore files

## Resolved Tickets

Here is a list of tickets that have been resolved since October 1, 2009:

    ticket # state     created       title
      15160: resolved  Sep 07, 2004  Windows, Global Drives as SYSTEM...
      15714: resolved  Oct 21, 2004  Windows: Remove submount creation as a side effect of AFS drive mapping
      16733: resolved  Dec 08, 2004  Windows; Trojan horse in a 1.3.74  installer
      61118: resolved  May 08, 2007  CPU Load after Starting AFS Service
      73105: resolved  Oct 03, 2007  tokens -h / tokens -help
      82701: resolved  Jan 11, 2008  AFS Client icon disappears from taskbar
      90994: resolved  Mar 20, 2008  Bug:  OpenAFS client for Windows 1.3.5 does not cleanup Registry during Uninstall
      92944: resolved  Apr 03, 2008  [OpenAFS-devel] SELinux biting OpenAFS [Cache manager using the wrong SELinux context]
     119102: resolved  Oct 03, 2008  convert OpenAFS CVS to git
     123575: resolved  Oct 30, 2008  Opening on two windows clients a MS Word Document
     124337: resolved  Feb 11, 2009  Windows 7 beta and AFS drives
     124498: resolved  Mar 18, 2009  panic on solaris 10 running 1.4.8
     125402: resolved  Sep 15, 2009  oafs win 1.5.63 - writing profile to afs failures
     125421: resolved  Sep 23, 2009  Vista ultimate and 1.6.64 "\\AFS not reachable\
     125475: resolved  Oct 08, 2009  OpenAFS on kernel 2.6.32 triggers WARNING at fs/fs-writeback.c:1112
     125486: resolved  Oct 10, 2009  Uninstall.command Open AFS v1.565
     125510: resolved  Oct 17, 2009  OpenAFS on windows permission denied on RO with client not reachable
     125544: resolved  Oct 27, 2009  BUG at osi_file.c:87 with AppArmor
     125555: resolved  Oct 30, 2009  OpenAFS 1.4.11 crash on RHEL 5 update 4 systems
