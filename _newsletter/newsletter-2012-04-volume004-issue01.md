---
title: OpenAFS Newsletter, Volume 4, Issue 1, April 2012
layout: page
---

# OpenAFS Newsletter, Volume 4, Issue 1, April 2012

Welcome back to the OpenAFS newsletter!

I want to begin by thanking Jason Edgecombe for all his hard work on the
newsletter over the past years. It is with his guidance and support as well as
the support of the OpenAFS Gatekeepers, that I am picking up where Jason left
off. 

In the revised newsletter, you will see many of the same features of past
issues. I hope to also include some new features such as AFS case studies,
question and answer, and so on. If you have any suggestions, please let me
know.

This newsletter is very much a community resource. Any contributions for future
issues, thoughts, or feedback, please send 'em along. If there is something you
would like to see featured, please let me know. I can be reached at:
botsch(at)cnf.cornell.edu.

As always, past issues can be found at: [http://www.openafs.org/newsletter/](http://www.openafs.org/newsletter/)

## Case Study: High Availability with OpenAFS

As part of a layered setup, OpenAFS adds another important level of redundancy to the
SysAdmin's High Availability setup. SysAdmins are already familiar with
OpenAFS's ReadOnly data replication feature. And despite not yet having
official ReadWrite data replication support, OpenAFS can also provide failover
for ReadWrite data.

"For some of the 10k+ users of AFS at CERN, the high-availability (HA)
of their data is of utmost importance" writes Arne Wiebalck of CERN. 

And Ken Dreyer of US Geological Survey writes that "we use AFS to distribute
website content to web servers in three geographic regions ... it's acceptable
to have a little bit of downtime, but we need to be able to recover with a
minimum of hassle if we had an outage ... to meet our team's mission of highly
available web content."

Ken and Arne describe their similar approaches to High Availability with
OpenAFS.

Both Ken and Arne advise beginning one's high availability setup at the physical
disk level. "The first level is our SANs: we have several SAS disks set up in a
RAID array, so that if a disk fails, we can have on-site techs replace the disk
in the SAN. This is a fairly standard enterprise-level practice, and it could be
done with any fileserver technology, so it's not really AFS-specific" writes
Ken.

Next, Ken and Arne move to protecting against failure of the server hardware
itself. While AFS's built in ReadOnly data replication coupled with AFS's
location independence ensure a short failover time to another server, one is
still down a production server. And the normal built in mechanism only works
with ReadOnly replicated data. Also depending on the number of servers, certain
AFS operations which write to the backend AFS databases will no longer be
available.  ReadWrite data stored on the down server is offline. And if the
server is the only one in a particular physical location, additional network
spans over a WAN add latency for transfers of replicated ReadOnly data from a
redundant server.

Enter level 2, server address redundancy. Both Ken and Arne fail over the IP
address / server identity to another physical or virtual server.

Arne writes that "Protection against hardware failures (individual disks, entire
arrays or servers) is done via the server setup: pairs of servers with mirroring
over shared external SAS arrays. Here, fail-over times between servers were
reduced enormously by exchanging the servers' sysid. This allows the servers to
take over each other's identity and avoids the otherwise required (lengthy) VDLB
synchronisation."

According to [http://doc.openafs.org/Reference/5/sysid.html](http://doc.openafs.org/Reference/5/sysid.html),

	Each time the File Server restarts, it builds a list of interfaces on the
	local machine ... [and] The File Server records the resulting list in the
	binary-format sysid file and registers the interfaces in the VLDB.

	When the Cache Manager requests volume location information, the Volume
	Location (VL) Server provides all of the interfaces registered for each
	server machine that houses the volume.



Ken agrees that "The method of using multiple servers hooked a SAN is
not strictly unique to AFS, but the key is that AFS provides us with a level of
fileserver transparency. Even without the virtual IPs, the names and numbers of
fileservers are abstracted away from our clients, so we have more breathing room
when it comes to outages, or when we scale out using virtualization." At ANL,
Ken has "four AFS fileservers hooked into our SAN. Three fileservers are active,
and one is a warm spare.  If we have hardware problems with one fileserver, we
take that one offline and use the fourth. Each fileserver has "virtual" IPs
associated with it. We run the AFS fileservice on these virtual IP addresses, so
that if a physical server dies, we can move the "virtual" IP to a different
fileserver, re-assign the data on the SAN, and continue to serve data via the
fileserver that way."

But what happens when the server IP failover process itself goes awry? Or when a
larger problem with the SAN keeps disk inaccessible to one or more servers?
That's where AFS's built in data replication and redundancy features, both old
and new, come into play.

"AFS replications provide our third level of redundancy. We have three
geographic regions, each with a SAN hardware stack as described above.  We use
AFS's replication ("vos release") to distribute read-only volumes to each
region. Almost all of our volume replications are done via cron tasks using
\-localauth, every 15 minutes. We have some algorithms in place that distribute
these replications so that we don't overwhelm our master VLDB server. In fact if
I'm remembering right, we recently put in some checks with rxdebug to ensure
that the master VLDB is able to keep up with the replication load" writes Ken.

But Ken's approach does have one minor drawback. "We serve all production
websites from read-only volumes, so that if we lose a region due to a network
outage or hardware failure, the websites stay online.  For these websites,
changes only show up 'live' every 15 minutes." Here is how Ken quantifies the
tradeoff: "We have to trade instantly-visible updates for high-availability."

For those instances where instantly-visible updates are the higher priority, Ken
takes a slightly modified approach. He writes that "we have a couple of websites
in AFS where the users are more interested in instantly viewing their changes,
rather than seamless high availability. For these cases, we are able to mount
the underlying AFS volumes explicitly as read-write, using fs mount's '-rw'
flag. The volumes are still replicated every 15 minutes, but it happens 'behind
the scenes'. The users don't know about the details, and because AFS provides a
global namespace, these locations look like anything else in the file system.

"If we have a prolonged outage, such as an entire SAN failure, then my team uses
'vos convertROtoRW' to convert another region's  RO copies to RW. In these
cases, assuming the users 'save early and often', hopefully we can minimize the
amount of work lost. The big advantage to 'vos convertROtoRW' is that it is very
fast, compared to the older 'dump / restore' method for converting RO volumes to
RW."

Whereas Ken makes use of 'convertROtoRW', Arne makes use of the relatively
new OpenAFS feature, shadow volumes. Arne writes that " 'volume shadowing' is
implemented to allow for quick user-driven recovery in case a volume is not
accessible. For this, registered volumes are vos shadow'ed at regular intervals
and users can re-instantiate the shadow to the original by an authenticated
remote procedure call." 

However, both Ken's and Arne's approaches each are not without their own set of
challenges.

Shadow volumes are invisible copies and not present in the Volume Location
Database. One has to, through some other means, keep track of where on disk
these shadow volumes
are. One may also bump against volume name length limitations. Arne writes that
"Due to the length limitation of the volume name, the approach to use shadow
volumes for HA requires some (external) mapping of original name to shadow name
in order to allow for a unique association of original and shadow volume name on
restores." And one needs to be sure the original ReadWrite volume does not
suddently reappear. Additional warnings are in the "vos shadow" documentation.

And what of Ken's approach? "It has its downsides" writes Ken. Such as, again,
the original ReadWrite volume needs to stay gone -- there is no method to downconvert a
ReadWrite volume to a ReadOnly volume. Ken, however, is optimistic. "It's not
true multi-master RW, but it works in a pinch."

No matter whether an individual disk fails, a SAN array decides to take a nap,
an individual server falls over, or something wonky corrupts an OpenAFS volume
itself, Ken and Arne are well prepared. And it is thanks to the robust and fault
tolerant design of OpenAFS that Ken and Arne carry a much larger toolbag for
when the inevitable computer disaster strikes.

## OpenAFS 1.6.1 Released

The OpenAFS Gatekeepers are pleased to announce the availability of OpenAFS
version 1.6.1.  Source files and available binaries can be accessed via
the web at:

       http://www.openafs.org/dl/openafs/1.6.1/

or via AFS at:

       /afs/grand.central.org/software/openafs/1.6.1/
       \\afs\grand.central.org\software\openafs\1.6.1\

OpenAFS 1.6.1 is the second of a new series of stable releases of
OpenAFS. Sites running 1.6.0 or prereleases of 1.6.1 are urged
to upgrade; The 1.6.0 fileserver has a bug which can under some
circumstances cause data loss in replicated volumes.

### Highlights

Sites running 1.6.0 fileserver are urged to update immediately to avoid data
loss. A bug which can lose data on a fileserver for volumes which are
replicated or backed up has been fixed.

Sites running 1.6.0 UNIX clients are urged to update immediately to
avoid excess network traffic.

Updated idle dead handling to avoid issues with retrying calls which could
succeed but error and then error on a retry.

Fix salvaging of volumes with large numeric IDs.

Further correct tracking of alternate and changed addresses in the fileserver.

Do not perform Rx keepalives during disk IO to allow timeouts to occur in event IO cannot complete.

More available in the OpenAFS Release Notes at
[http://www.openafs.org/dl/openafs/1.6.1/RELNOTES-1.6.1](http://www.openafs.org/dl/openafs/1.6.1/RELNOTES-1.6.1)

### Known Issues

Even OpenAFS has bugs. This newsletter, we'll highlight the following:
in 1.6.1...

	(indented text credited to Jeffrey Altman on openafs-info)

#### Idle Dead Timeouts

	1.6.1pre2 contained a fix for the idle dead issues. 

	A request to a file server for a non-replicated object will use a timeout of
	20 minutes.  If your file servers are not responding in that time period
	(unless your data is offline in an hierarchical storage management system),
	then you have bigger problems.

	If the request is against a replicated object (read/only) then a shorter
	timeout is used but a retry will not be sent to the same file server that
	failed to respond in a timely manner.



#### Vnode Lock Contention Typing Up All the Server Threads

OpenAFS file servers have a limited thread pool size. At the present time, "all
threads can become blocked on a single vnode". Unfortunately, this issue is not
yet fixed.

#### Client Side "RX Busy" Packet Processing

	A client can receive the response to a call and issue the next call on the
	same call channel before the file server has finished cleaning up the prior
	call which results in an RX BUSY packet being sent to the client. There is a
	race in the file server that has existed since the beginning of time.
	Simon and [Jeffrey] have researched several solutions but none of them are
	appealing because they all introduce additional contention with the file
	server's rx listener thread which slows down the file server's ability to
	process incoming packets.

But fixed:

	[The] UNIX client was failing to unconditionally retry requests when an RX
	BUSY packet is received.



## OpenAFS 1.7.10 for Windows Released

OpenAFS 1.7.10 is the latest in a new series of OpenAFS clients for the
Microsoft Windows platform that is implemented as a native file system.

Below you will find some of the major benefits of the 1.7.x series of OpenAFS
for Windows and a few of the highlights of the new 1.7.10 release. Keep in mind
that OpenAFS for Windows also has some limitations. Please read the OpenAFS for
Windows release announcements and release notes for more information.

### Major Benefits of OpenAFS 1.7.x for Windows

Significantly faster than previous release series (up to 800MB/second read
throughput from Solid State Disk backed cache)

	The transaction rate and throughput performance of the SMB client was
	limited by the "SMB client <-> loopback <-> SMB server" performance:
	54MB/sec maximum on 32-bit systems and 63MB/sec on 64-bit systems.  The IFS
	client is capable of throughput rates to/from cache up to 800MB/sec
	depending on the system I/O bus and backing store capabilities.  Read
	performance of uncached data from file servers on a 1Gbit/second network
	link have been observed in excess of 74MB/seconds.

Does not require the installation of the Microsoft Windows Loopback Adapter

	Prior OpenAFS clients for Microsoft Windows were implemented as an SMB to
	AFS gateway whereby the OpenAFS service published a local SMB Server named
	\\AFS on a private network address and all requests to browse, read, or
	write the \\AFS name space were managed by Microsoft's SMB client.  One of
	the requirements of this model is the use of a Microsoft Loopback Adapter
	statically bound to a private IP address.  This ensured that under most
	circumstances there would be a network path for the SMB client to
	communicate with the AFS SMB server even if the machine was disconnected
	from physical networks.

	The loopback adapter approach worked quite well for Windows XP and 2003 but
	by the time Windows 7 and Server 2008 R2 were released the loopback adapter
	had been converted to a plug'n'play device and it is no longer a stable
	network path when the machine is disconnected from physical networks or when
	the machine is returned from a sleep state.

	With the introduction of a native AFS installable file system
	driver(afsredir.sys / afsredirlib.sys) there is no requirement to install
	the Microsoft Loopback Adapter.  This will be a significant relief to sites
	that use software license tracking software that is confused by the use of a
	single private network address on all machines.

Provides support for kernel enforced Process and Thread Authentication Groups

	AFS Tokens are associated with Windows user names in the SMB client.  With
	the IFS client, tokens are associated with Authentication Groups.  By
	default, an authentication group is allocated for each User SID and Logon
	Session Id combination.  In addition, it is possible for    processes to
	create additional Authentication Groups.  Each thread in a process can
	select an Authentication Group within the process as the active
	Authentication Group.  This will permit AFS aware IIS modules to associate
	AFS credentials with a particular incoming request.  An IIS implementation
	of File Drawers will be the preferred implementation once it is developed.

	One of the significant benefits of Authentication Groups within the Windows
	environment is that Windows services (svchost.exe, csrss.exe, etc.) which
	impersonate user processes will seamlessly gain access to the user's AFS
	credentials for the lifetime of the impersonation.

	The use of Authentication Groups will finally permit a single Windows user
	account to logon to a Terminal Server multiple times and maintain
	independent credential sets.  This is a critical piece of functionality for
	sites that map arbitrary non-AD Kerberos principals to a single local
	machine account.

No Delays After a Resume from Sleep

	Windows Vista and 7 shutdown the network stack when the machine is
	suspended.  This causes problems for applications that are actively using
	files in the \\AFS name space when the machine suspended.  With the IFS
	driver, open file handles are maintained through the sleep state and are
	immediately available when the machine wakes.

No "AFS" Server Name Collisions

	When relying on the Microsoft SMB client to resolve the \\AFS server name it
	was critical that no machine in the active DNS domain or sharing the same
	WINS server be assigned the name "AFS".  Doing so could result in requests
	intended for the local AFS SMB gateway service being sent to the remote
	system.

	This is no longer an issue with the IFS driver.  The driver registers
	ownership with the Multiple UNC Provider (MUP) for all UNC paths beginning
	with \\AFS.

Symlinks to UNC Paths permit a cohesive name space

	It has always been possible to create reparse points in Microsoft's DFS name
	space that refer to \\AFS paths.  It is now possible to create symlinks in
	AFS that refer to arbitrary UNC paths.  This permits the construction of a
	cohesive name space that spans across both AFS and DFS storage.

Reparse Points

	AFS Mount Points and Symlinks are exported by the file system as Windows
	reparse points with a Microsoft assigned tag value. Tools that are OpenAFS
	reparse point aware query AFS symlinks and mount points without requiring
	knowledge of AFS pioctls.

	In a future release, mount points and symlinks will be first class objects
	that can be created and removed using the Win32 File API.

AFS Volumes are Windows File Systems

	Each AFS volume is represented in the Windows kernel as a distinct file
	system.  This will permit AFS volume quotas to viewed as Windows file system
	quotas in a future release.



### Highlights of 1.7.9 and 1.7.10.

Improved compatibility with anti-virus and other anti-malware products.

Fixed kernel deadlocks with Trend Micro

BSOD issues fixed

Corrected processing of symlinks containing ".." components

Correct an RX deadlock introduced in 1.7.9

Redesigned AFS PIOCTL processing to workaround broken SMB protocol
implementations.Ensure that file data is flushed to the file server before file
locks are released

Prevent afsd\_service crash if a file is marked delete on close and the file
server is unreachable

## Project Updates

### Documentation Project

	No recent process and on hold indefinitely.

		--Russ Allbery

	We have documentation.  It needs improvement.   End users should read it and
	contribute.

		--Jeffrey Altman

### Per-File ACLs

	There is some functional code, but:

	(1) Some effort is needed to standardize the protocol changes that are needed

	(2) The way that ACLs are stored on disk needs to be adapted to fit what was
	agreed on at the Pittsburgh hackathon in April 2011.  This remains to be
	done.

		--Marc Dionne

### Read-Write Replication

	The work used the code produced during the 2008 Google Summer of Code by
	Vishal Powar as a starting point.  This work is being funded by YFS.

	Current Status:

	(1) There is functional code for basic read-write replication.

	(2)  A few inital batches of changes have been submitted for review, and
	some first commits have been merged.  The rest of the code will be submitted
	gradually as things get merged.

	(3) A description of the implementation needs to be completed and submitted
	to developers on openafs-devel to help with code review.

	(4) The main aspects that will be lacking in this first version are refined
	controls to start and stop replication, and dealing more cleanly and
	automatically with various issues like errors, congestion, low bandwidth,
	etc.

	(5) Some more advanced features are also planned and have been implemented
	for testing, for instance parallel reading from a set of read-write
	replicas.

		--Marc Dionne

### TCP Out of Band Support

	The current onus is on me to submit a protocol draft to the standards group;
	I have a document that needs to be sanitized and checked for correctness.
	For this, I am giving myself an informal deadline of April 20th, though I
	hope to have it sooner. Just as a data point, the current implementation
	includes a 1.4 Linux client, a 1.4 Linux fileserver, and a 1.6 Linux client;
	the latter two are undergoing testing.	

		--Andrew Deason

### Extended Callbacks

	An updated Extended Callback Information draft was published.

		--Matt W. Benjamin

	Blocked on standardization.  It can't move forward until there is a secure
	callback channel which requires that rxgk be completed.

		--Jeffrey Altman

### RXGK proposal (draft-wilkinson-afs3-rxgk)

	The code for rxgk is complete, and being tested in a couple of cells.
	Inclusion in OpenAFS is dependent upon the various standards documents
	making their way through the afs3-standardisation process, which is the main
	hold up. A number of last-minute issues were raised during a last call a few
	months ago. Whilst consensus appears to exist for the majority of the
	document, a new version of the drafts will be required to address these
	issues.

		--Simon Wilkinson

## Gerrit Activity

### Statistics

#### Patches merged into the master branch

	Month	Number of commits   
	2012-04		146				
	2012-03		51 			
	2012-02		75 			
	2012-01		85 			
	2011-12		121 			
	2011-11		116 			
	2011-10		67 			

#### Patches merged into the devel 1.7.x branch

	Month	Number of commits		
	2012-04		68  				
	2012-03		25 				
	2012-02		43 				
	2012-01		73 				
	2011-12		63 				
	2011-11		206 				



#### Patches merged into the stable 1.6.x branch

	Month	Number of commits		
	2012-04		2 				
	2012-03		19 				
	2012-02		72 				
	2012-01		21 				
	2011-12		83 				
	2011-11		78 				
	2011-10		32 				

#### Patches merged into the stable 1.4.x branch

	Month	Number of commits		
	2012-04		1 				
	2012-02		1 				
	2012-01		2 				
	2011-11		1 				
	2011-10		5 				





### Patches merged into the master branch

    Date       Committer        Change# Description
    2012-04-16 Michael Meffie    (5744) auth: local realms configuration
    2012-04-16 Simon Wilkinson   (7206) rx: Remove surplus call to FindPeer
    2012-04-16 Andrew Deason     (6986) rx: dec rx_nWaiting on clearing RX_CALL_WAIT_PROC
    2012-04-16 Jeffrey Altman    (7218) rx: conn_call_lock leak
    2012-04-16 Michael Meffie    (6875) auth: get local cell internal function
    2012-04-16 Jason Edgecombe   (7202) TESTS: Add the libwrap script to "make check" to handle library paths
    2012-04-15 Jeffrey Altman    (7210) Windows: pioctl use GetFileAttributes
    2012-04-15 Jeffrey Altman    (7209) Windows: _._AFS_IOCTL_._ hidden and system
    2012-04-15 Jeffrey Altman    (7208) Windows: Remove PurgeContent param AFSVerifyEntry
    2012-04-15 Jeffrey Altman    (7207) Windows: Flush data and then drop locks
    2012-04-14 Michael Meffie    (7204) Build: error if solariscc is not found
    2012-04-14 Michael Meffie    (7203) Build: check for gencat
    2012-04-14 Simon Wilkinson   (7195) rx: Rework code which pulls packet from recv queue
    2012-04-14 Simon Wilkinson   (7194) rx: Tidy up currentPacket handling
    2012-04-13 Derrick Brashear  (7201) aklog: heimdal kvno is unsigned
    2012-04-12 Simon Wilkinson   (5815) Remove redundant header includes
    2012-04-12 Jeffrey Altman    (7143) Windows: Refactor AFSValidateEntry
    2012-04-12 Michael Meffie    (6980) volscan: index offset output column
    2012-04-12 Michael Meffie    (6979) volscan: option to ignore dir vnode magic
    2012-04-11 Jeffrey Altman    (7189) Windows: missing brace in RDR_CleanupFileEntry
    2012-04-11 Andrew Deason     (6946) salvager: Trust inode-based special data over OGM
    2012-04-11 Andrew Deason     (6945) namei: Abstract out OGM functions a bit more
    2012-04-11 Derrick Brashear  (6714) libafs: dont handle outstatus on write error
    2012-04-11 Michael Meffie    (6847) Build: link libaudit before util
    2012-04-11 Michael Meffie    (6861) viced: fix log message for MapName_r
    2012-04-11 Michael Meffie    (7187) doc: distributed files are under dest
    2012-04-11 Jeffrey Altman    (7186) Windows: Do not delete in CleanupFile if error
    2012-04-11 Simon Wilkinson   (7137) afsd: Move to newer cmd syntax
    2012-04-10 Michael Meffie    (7138) libafs: log error code when marking server down
    2012-04-10 Simon Wilkinson   (7131) Rework the ugen_* interface
    2012-04-10 Marc Dionne       (6675) viced: Make Update_TargetVnodeStatus usable by replication code
    2012-04-10 Marc Dionne       (6673) viced: Make GetVolumePackageWithCall usable by replication code
    2012-04-10 Marc Dionne       (6672) vol: Allow VAllocVnode of specific vnodes
    2012-04-10 Simon Wilkinson   (7067) rxkad: Move conversion functions to own file
    2012-04-10 Simon Wilkinson   (7068) rxkad: Remove DES include from header file
    2012-04-10 Jeffrey Altman    (7172) Windows: AFSValidateProcessEntry, ullProcessId 64-bit
    2012-04-10 Simon Wilkinson   (7139) roken: Add rk_getprogname to Windows mapfile
    2012-04-10 Simon Wilkinson   (7070) shlibafsauthent: Add a load more objects
    2012-04-10 Simon Wilkinson   (7069) opr: Install the queue.h header
    2012-04-10 Jeffrey Altman    (7148) Windows: report error on panic
    2012-04-10 Jeffrey Altman    (7147) Windows: correct afsredir log entries
    2012-04-10 Simon Wilkinson   (7136) Generalise the new background daemon code
    2012-04-10 Andrew Deason     (7140) vos: Do not try to remove backup volume id 0
    2012-04-10 Simon Wilkinson   (7145) Import of code from heimdal
    2012-04-10 Simon Wilkinson   (7144) Import the expand_path.c file from Heimdal
    2012-04-10 Marc Dionne       (7142) tests: remove unused variable in tests/util/ktime-t.c
    2012-04-10 Simon Wilkinson   (7004) rx: Remove the unused packet skew code
    2012-04-10 Simon Wilkinson   (7006) rx: Remove packet burst elements from peer struct
    2012-04-10 Simon Wilkinson   (7003) rx: Hide internal packet functions
    2012-04-10 Simon Wilkinson   (7002) rx: Hide struct rx_peer from the rest of the tree
    2012-04-09 Simon Wilkinson   (7132) Move configuration parsing into libcmd
    2012-04-09 Simon Wilkinson   (7011) rxperf: Build again
    2012-04-09 Simon Wilkinson   (7010) roken: Prefix getopt and getprogname
    2012-04-09 Simon Wilkinson   (7009) all needs to be first rule in the Makefile
    2012-04-09 Simon Wilkinson   (7066) bos: Change to using char casts for ka functions
    2012-04-09 Simon Wilkinson   (7065) shlibafsrpc: Add additional XDR functions
    2012-04-09 Jeffrey Altman    (7130) rx: remove peer burst elements from rx/test
    2012-04-09 Simon Wilkinson   (6999) rx: rxi_AckAll isn't an event handler
    2012-04-09 Simon Wilkinson   (6998) rx: Tidy up function scope in rx.c
    2012-04-09 Simon Wilkinson   (7001) rx: Remove trailing else from RX_KERNEL_TRACE
    2012-04-09 Simon Wilkinson   (7129) kas: Don't require config for help
    2012-04-09 Marc Dionne       (7123) tools: return error code in xfclose
    2012-04-09 Simon Wilkinson   (7000) rx: Remove unused ACKHACK macro
    2012-04-09 Simon Wilkinson   (7128) tests: waitpid requires sys/wait.h
    2012-04-09 Simon Wilkinson   (7127) tests: rx needs roken
    2012-04-09 Simon Wilkinson   (7107) cmd: Don't leak memory when constructing help string
    2012-04-09 Simon Wilkinson   (7106) ktime: Don't leak token list
    2012-04-09 Simon Wilkinson   (7105) budb: Don't leak memory
    2012-04-09 Simon Wilkinson   (7104) vol-dump: Don't leak memory
    2012-04-09 Simon Wilkinson   (7103) vol-dump: Make static things static
    2012-04-09 Simon Wilkinson   (7102) auth: Don't leak key on file parse error
    2012-04-09 Simon Wilkinson   (7101) opr: Flag assertion error handles as noreturn
    2012-04-09 Simon Wilkinson   (7100) pts: Don't malloc(0) when there's nothing to do
    2012-04-09 Simon Wilkinson   (7099) bucoord: Don't malloc(0) if there's no work to do
    2012-04-09 Simon Wilkinson   (7098) auth: Handle empty lists of keys
    2012-04-09 Simon Wilkinson   (7097) Unix CM: We're disconnected if RW disconnected too
    2012-04-09 Simon Wilkinson   (7096) auth: Make sure we get AF_INET addresses from DNS
    2012-04-09 Simon Wilkinson   (7095) vos: Initialise total counters
    2012-04-09 Simon Wilkinson   (7094) vol: Don't return an uninited val from LookupNode
    2012-04-09 Simon Wilkinson   (7093) fs: Fix bad frees
    2012-04-09 Simon Wilkinson   (7092) cmd: Use strl* rather than strn* to avoid overrun
    2012-04-09 Simon Wilkinson   (7091) autoconf: One CC to rule them all
    2012-04-09 Simon Wilkinson   (7090) afs: Handle reading past the end of a file
    2012-04-09 Simon Wilkinson   (7089) xdr: Len can never be negative
    2012-04-09 Simon Wilkinson   (7088) rx: Remove needless braces
    2012-04-09 Simon Wilkinson   (7087) rx: Handle negative returns on packet reads
    2012-04-09 Simon Wilkinson   (7086) venus: Make clang happy with strlcpy use
    2012-04-09 Simon Wilkinson   (7085) viced: Remove pointless braces
    2012-04-09 Simon Wilkinson   (7084) vlserver: unsigned values are always >0
    2012-04-09 Simon Wilkinson   (7083) vol: Call memset with the correct size
    2012-04-09 Simon Wilkinson   (7005) rxgen: Tidy up server side freeing
    2012-04-09 Simon Wilkinson   (7125) fileserver: Fix NeverAttach support
    2012-04-08 Jason Edgecombe   (7126) DOC: Factored common text out of the vos_backup and vos_dump man pages
    2012-04-08 Simon Wilkinson   (7078) pam: Use &, not && for bitwise operations
    2012-04-08 Simon Wilkinson   (7079) pam: Don't check if unsigned is < 0
    2012-04-08 Simon Wilkinson   (7080) ptserver: Remove redundant braces
    2012-04-08 Simon Wilkinson   (7081) vice & vol: Cast FDH_SYNC results to void
    2012-04-08 Simon Wilkinson   (7082) vol: Remove unneeded braces
    2012-04-08 Simon Wilkinson   (7118) tools: Use native 64 bit integer
    2012-04-08 Derrick Brashear  (7116) ubik: utst needs opr for assert in util
    2012-04-07 Jason Edgecombe   (7108) Fileserver: Add the /vicepXX/NeverAttach flag to skip mounting a partition
    2012-04-07 Simon Wilkinson   (7072) util: LogCommandLine has to have a command line
    2012-04-07 Jeffrey Altman    (7111) Windows: Disk Full errors instead of Quota Exceeded
    2012-04-07 Simon Wilkinson   (7117) tools: Add roken.h to afsdump
    2012-04-07 Simon Wilkinson   (7115) tools: Rename u_int64 to solve AIX problem
    2012-04-07 Jeffrey Altman    (7109) Windows: AFSCheckCellName one level of indirection
    2012-04-07 Simon Wilkinson   (7077) libafscp: Use strdup, rather than rolling our own
    2012-04-07 Simon Wilkinson   (7076) libadmin: Clear structures according to their size.
    2012-04-07 Simon Wilkinson   (7075) libadmin: read returns an ssize_t, not a size_t
    2012-04-07 Simon Wilkinson   (7074) Unix CM: Purge needless brackets
    2012-04-07 Simon Wilkinson   (7073) DARWIN: Make crfree() an inline function
    2012-04-07 Simon Wilkinson   (7071) Salvager: Don't use garbage vnodes when Testing
    2012-04-07 Derrick Brashear  (7043) tools: move useful tools from test dir to tools dir
    2012-04-06 Jeffrey Altman    (7021) Windows: Name Array store mount point and volume root
    2012-04-06 Jeffrey Altman    (7016) Windows: do not call time() in a loop
    2012-04-06 Jeffrey Altman    (7049) Windows: CleanACLEnt requires cm_scache write locked
    2012-04-06 Jeffrey Altman    (6996) Windows: Add per object per user EACCES caching
    2012-04-06 Jeffrey Altman    (7018) Windows: Fail recursive path evaluation with access denied
    2012-04-06 Jeffrey Altman    (7057) Windows: Check Avail Space on extending SetEndOfFile
    2012-04-06 Andrew Deason     (7054) viced: Do not offline volume on successful IH_DEC
    2012-04-05 Jeffrey Altman    (7052) Windows: Redirector must query volume size when asked
    2012-04-05 Jeffrey Altman    (7051) Windows: cm_AddACLCache lock ordering
    2012-04-05 Jeffrey Altman    (7050) rx: fix bad merge 95c38dff3740d7e24971ceb5875c06e7abfce102
    2012-04-05 Jeffrey Altman    (7048) Windows: AFSVerifyEntry purge file data on DV change
    2012-04-04 Andrew Deason     (7047) xstat_cm_test: Print all call info stats
    2012-04-03 Jeffrey Altman    (7012) Windows: Redirector Dir Enumeration Bug
    2012-04-03 Simon Wilkinson   (6997) rx: Get rid of some uneccessary temporary vars
    2012-04-03 Derrick Brashear  (6991) linux: make mockbuild more reliable
    2012-04-03 Derrick Brashear  (6985) linux: update spec requirements
    2012-04-03 Andrew Deason     (7042) SOLARIS: Correct misplaced osi_machdep.h #endif
    2012-04-03 Jeffrey Altman    (7037) Windows: cm_GetNewSCache must return NULL on failure
    2012-04-03 Jeffrey Altman    (7022) viced: AFSDisk, AFSFetchVolumeStatus Int31 PartSize
    2012-04-03 Jeffrey Altman    (6543) Rx: give grow mtu its own call ref count type
    2012-04-03 Jeffrey Altman    (6629) rx: conn->callNumber protected by conn_call_lock
    2012-04-03 Jeffrey Altman    (6443) Rx: rxi_FreeCall conn_call_lock vs call->lock deadlock
    2012-04-03 Jeffrey Altman    (7020) Windows: Pass name array to AFSRetrieveFileInformation
    2012-04-03 Jeffrey Altman    (7017) Windows: Use hash when comparing File IDs in redirector
    2012-04-03 Jeffrey Altman    (7007) Windows: optimize InitCallback3 processing
    2012-04-03 Jeffrey Altman    (6993) Windows: add parent FID to cm_GetSCache
    2012-04-03 Jeffrey Altman    (6995) Windows: Record callback issued time
    2012-04-03 Jeffrey Altman    (7008) Windows: Freelance HaveAccessRights
    2012-04-03 Jeffrey Altman    (6994) Windows: Implement cm_TGTLifeTime()
    2012-04-03 Jeffrey Altman    (7015) Windows FindACLCache must hold scp write locked
    2012-04-03 Jeffrey Altman    (7014) Windows: fix indentation
    2012-04-01 Jeffrey Altman    (6943) rx: handle clock reversals for call timeouts
    2012-04-01 Simon Wilkinson   (6992) viced: Do error translation for InlineBulkStatus
    2012-03-30 Jeffrey Altman    (6988) Windows: avoid deadlock with Trend Micro
    2012-03-30 Jeffrey Altman    (6987) Windows: Use ulFilter in AFSInvalidateObject
    2012-03-28 Jeffrey Altman    (6970) Windows: ObjectInformation.ObjectReferenceCount comparison
    2012-03-28 Jeffrey Altman    (6973) Windows: Add Name Array Processing Trace Subsystem
    2012-03-28 Jeffrey Altman    (6962) Windows: AFSInvalidateObject can overwrite input param
    2012-03-28 Jeffrey Altman    (6959) windows: ObjectInformationCB.ObjectReferenceCount
    2012-03-28 Michael Meffie    (6963) remove athena env conditionals
    2012-03-27 Jeffrey Altman    (6969) Windows: Fix VNOSERVICE EventLog parameters
    2012-03-27 Jeffrey Altman    (6967) Windows: CreateProcessNotify verify changes
    2012-03-27 Derrick Brashear  (6971) macos: iterate mdfound packagemakers when spaces are present
    2012-03-27 Derrick Brashear  (6966) macos: find packagemaker instead of assuming path
    2012-03-26 Andrew Deason     (6937) afs: Set DWriting when truncating a dcache entry
    2012-03-26 Andrew Deason     (6936) afs: Slight adjustments in afs_GetDCache
    2012-03-26 Andrew Deason     (6882) afs: Do not limit fetches based on vcache length
    2012-03-26 Andrew Deason     (6881) afs: Log a message on invalid FetchStatus receipt
    2012-03-26 Andrew Deason     (6880) afs: Sanity-check some AFSFetchStatus structures
    2012-03-26 Chas Williams - CONTRACTOR (6923) Finish removing sunos 4.x references and build cruft
    2012-03-26 Andrew Deason     (6871) viced: Do not ignore all InlineBulkStatus errors
    2012-03-25 Jeffrey Altman    (6927) Windows: Assign AuthGroup during Process Create
    2012-03-25 Jeffrey Altman    (6926) Windows: Refactor AFSProcessSupport
    2012-03-25 Jeffrey Altman    (6951) doc: correct implicit ACL permissions volume owner
    2012-03-24 Jeffrey Altman    (6950) softsig: not used on windows
    2012-03-24 Simon Wilkinson   (6949) tests: Add opr to the command test libraries
    2012-03-24 Simon Wilkinson   (6948) libafsrpc: Export connection accessor fuctions
    2012-03-23 Chas Williams - CONTRACTOR (6925) opr: should be built as shared
    2012-03-22 Jeffrey Altman    (6938) Windows: Client handling of VNOSERVICE
    2012-03-22 Jeffrey Altman    (6930) Windows: AFSRedir Debug for STATUS_NOT_A_DIRECTORY
    2012-03-22 Marc Dionne       (6931) Linux 3.4: Switch to d_make_root
    2012-03-21 Ken Dreyer        (6903) doc: remove references to AFS's NTP daemon
    2012-03-21 Michael Meffie    (6924) build on solaris 10 again
    2012-03-17 Jeffrey Altman    (6914) Windows: invalidate correct objects during dir verification
    2012-03-15 Derrick Brashear  (6911) osx: deal with more kerberos damage
    2012-03-15 Andrew Deason     (6888) afs: Never #define away afsd_dynamic_vcaches
    2012-03-15 Jeffrey Altman    (6904) rx: hold call->lock across RXS_PreparePacket
    2012-03-13 Jeffrey Altman    (6893) Windows: Drop resource across AFSCleanupFcb
    2012-03-13 Jeffrey Altman    (6886) Windows: Wait for memory allocation if necessary
    2012-03-13 Jeffrey Altman    (6883) Windows: Correct Data Version change synchronization
    2012-03-12 Paul Smeddle      (6894) Make volscan's column delimiter option work
    2012-03-12 Jeffrey Altman    (6884) viced: fix inverted lockCount assignment
    2012-03-08 Jonathan Billings (6887) redhat: Don't replace modified configuration files during rpm update
    2012-03-07 Chas Williams - CONTRACTOR (6874) rxgen: fix to use rx accessor routines
    2012-03-04 Michael Meffie    (6860) viced: fix -realm option arg parse
    2012-03-04 Michael Meffie    (6845) viced: fix log message in hpr initialize
    2012-03-04 Derrick Brashear  (6868) macos: don't crash on krb5 damage
    2012-03-03 Jeffrey Altman    (6859) Windows: add __try..__except
    2012-03-03 Jeffrey Altman    (6858) Windows: fix indentation
    2012-03-03 Jeffrey Altman    (6856) Windows: Avoid deadlock in invalidation path
    2012-03-03 Dave Botsch       (6851) Fixes dkms.conf for Redhat Enterprise
    2012-03-02 Jeffrey Altman    (6852) unix: always retry RX_CALL_BUSY
    2012-03-01 Jeffrey Altman    (6846) Windows: Workaround Win7 SMB Reconnect Bug
    2012-03-01 Andrew Deason     (2368) viced: Ignore client loopback alternate addresses
    2012-02-27 Andrew Deason     (6787) salvager: Do not fork for single VG salvage
    2012-02-24 Jeffrey Altman    (6792) Windows: Fix an ExtentResource trace message
    2012-02-24 Jeffrey Altman    (6791) Windows: cm_UpdateCell never applies to Freelance mode
    2012-02-24 Jeffrey Altman    (6782) Windows: Redirector opens must set a valid FsContext
    2012-02-24 Jeffrey Altman    (6781) Windows: remove AFSOpenRedirector from AFSRedirLib
    2012-02-24 Jeffrey Altman    (6780) Windows: do not bugcheck in AFSExAllocatePoolWithTag
    2012-02-24 Jeffrey Altman    (6779) Windows: Revert "AFSRedir DebugFlags Turn on BugCheck"
    2012-02-24 Andrew Deason     (6790) Rewrite make_h_tree.pl in shell script
    2012-02-24 Andrew Deason     (6786) salvager: Remove VolumeSummary->fileName
    2012-02-24 Andrew Deason     (6785) salvager: Remove PrintVolumeSummary
    2012-02-24 Andrew Deason     (6784) salvager: Do not require MaybeZapVolume fileName
    2012-02-24 Andrew Deason     (6783) salvager: Do not set fileName on header fixup
    2012-02-23 Andrew Deason     (6776) LINUX: Use afs_convert_code in afs_notify_change
    2012-02-23 Andrew Deason     (6775) LINUX: move afs_notify_change to osi_vnodeops.c
    2012-02-22 Derrick Brashear  (6749) libafs: retry retriable RPCs instead of abandoning
    2012-02-22 Derrick Brashear  (6706) libafs: ensure one nat ping connection per srvAddr
    2012-02-22 Jeffrey Altman    (6747) Windows: invalidate data version on link creation
    2012-02-22 Jeffrey Altman    (6744) Windows: AFSPerformObjectInvalidate hold ExtentsResource shared
    2012-02-21 Jeffrey Altman    (6741) Windows: fsLockCount not accurate
    2012-02-21 Jeffrey Altman    (6740) viced: lockcount only valid if not expired
    2012-02-21 Marc Dionne       (6743) volser: Remove unused variable
    2012-02-20 Andrew Deason     (6733) viced: Relax "h_TossStuff_r failed" warnings
    2012-02-20 Andrew Deason     (6729) viced: Remove extraneous h_AHTAHT_r in h_GetHost_r
    2012-02-20 Andrew Deason     (6728) viced: Set h_GetHost_r probefail if MPAA_r fails
    2012-02-20 Andrew Deason     (6727) viced: Correctly update addrs on alt addr probe
    2012-02-20 Andrew Deason     (6726) viced: Delete dup host before probing old host
    2012-02-20 Derrick Brashear  (6254) vos: allow releases without offline time
    2012-02-20 Derrick Brashear  (6253) vos: refactor code
    2012-02-20 Andrew Deason     (6707) Rx: Avoid lastBusy/PEER_BUSY discrepancy
    2012-02-20 Derrick Brashear  (6251) vol: allow clones of readonly volumes
    2012-02-20 Derrick Brashear  (6250) volser: allow clonevol purge id to be new id
    2012-02-20 Derrick Brashear  (6249) volser: allow cloning non-rw volumes
    2012-02-19 Jeffrey Altman    (6737) Windows: Dereg Lanman and Lsa reg values for afsredir
    2012-02-18 Ken Dreyer        (6697) doc: replace hostnames with IETF example hostnames
    2012-02-18 Jeffrey Altman    (6734) Windows: Explorer Shell Set Unix Mode bits
    2012-02-17 Jeffrey Altman    (6725) Windows: remove unnecessary DirectoryEnumEvent
    2012-02-17 Jeffrey Altman    (6724) Windows: VolumeCB->ObjectInfoTree.TreeLock Deadlock
    2012-02-16 Michael Meffie    (6722) volinfo: initialize vnode details
    2012-02-16 Derrick Brashear  (6713) libafs: kill rxevent daemon even in upcall mode
    2012-02-16 Ken Dreyer        (6721) doc: refer to aklog instead of klog
    2012-02-15 Jeffrey Altman    (6715) Windows: disable afsdhook.dll reload by daemon
    2012-02-15 Jeffrey Altman    (6712) Windows: remove install9x rules
    2012-02-15 Jeffrey Altman    (6711) Windows: remove AFS_WIN95_ENV
    2012-02-15 Jeffrey Altman    (6710) Windows: add KTC_TOKEN_MUTEX_FAIL error code
    2012-02-15 Jeffrey Altman    (6708) Windows: avoid GetComputerNameW call for all ioctl
    2012-02-14 Andrew Deason     (6709) RedHat: Fail openafs-client 'stop' on rmmod error
    2012-02-12 Ken Dreyer        (6691) doc: add section on direct volume access
    2012-02-12 Jeffrey Altman    (6703) doc: fix AdminGuide
    2012-02-11 Jeffrey Altman    (6699) Windows: default cell grand.central.org
    2012-02-11 Jeffrey Altman    (6698) Windows: reset version to 0.0.0 on master
    2012-02-11 Jeffrey Altman    (6696) Windows: AFSRemoveFcb() cannot race
    2012-02-10 Jeffrey Altman    (6692) Windows: Perform rename to self check earlier
    2012-02-08 Andrew Deason     (6389) viced: Keep H_LOCK while locking host in h_Alloc_r
    2012-02-08 Jonathan A. Kollasch (6689) libafsauthent, tvolser: fix objdir build
    2012-02-08 Marc Dionne       (6674) viced: Allow null host for BreakCallBack
    2012-02-07 Jeffrey Altman    (6685) Windows: Release Notes corrections
    2012-02-07 Jeffrey Altman    (6668) Windows: OpenAFS reparse points are surrogates
    2012-02-07 Marc Dionne       (6676) RW Replication: Add basic definitions
    2012-02-07 Andrew Deason     (6671) Disable kernel opt by default on Solaris 10 and 11
    2012-02-07 Marc Dionne       (5551) vol: remove OPENAFS_VOL_STATS
    2012-02-07 Andrew Deason     (6670) Rx: Add missing rx_packet.h includes
    2012-02-07 Andrew Deason     (6669) SOLARIS: Use kcred instead of afs_osi_cred
    2012-02-06 Jeffrey Altman    (6661) Windows: Avoid race during PIOCtl DirNode allocation
    2012-02-06 Jeffrey Altman    (6660) Windows: Hold Fcb references prior to service call
    2012-02-05 Jeffrey Altman    (6664) Windows: Do not build NSIS by default
    2012-02-03 Jeffrey Altman    (6651) Windows: add buf_InvalidateBuffers
    2012-02-03 Jeffrey Altman    (6650) Windows: fix cm_DirOpDelBuffer assert
    2012-02-03 Jeffrey Altman    (6649) Windows: buffer DV ranges do not work for directories
    2012-02-03 Jeffrey Altman    (6648) Windows: update btree debugging code
    2012-02-03 Jeffrey Altman    (6647) Windows: Do not open file if shutdown in progress
    2012-02-03 Jeffrey Altman    (6646) Windows: AFSRedir DebugFlags Turn on BugCheck
    2012-02-03 Jeffrey Altman    (6645) Windows: Improve AFSNotifyDelete
    2012-02-03 Jeffrey Altman    (6644) Windows: do not lower case direct volume references
    2012-02-01 Tom Keiser        (6638) com_err: correctly deal with lack of libintl
    2012-02-01 Christof Hanke    (6628) linux: fix probing for noop_fsync
    2012-01-29 Jeffrey Altman    (6632) man-pages: add fs_getverify and fs_setverify
    2012-01-29 Jeffrey Altman    (6630) Windows: do not panic if afsredir not ready during shutdown
    2012-01-29 Jeffrey Altman    (6627) Windows: Increase size of worker thread pools
    2012-01-29 Jeffrey Altman    (6626) Windows: Run Workers until empty task queue
    2012-01-29 Jeffrey Altman    (6624) Windows: Release Notes for 1.7.5
    2012-01-27 Jeffrey Altman    (6618) Windows: DriveSubstitution handle too small buffer
    2012-01-27 Jeffrey Altman    (6617) Windows: Invalidate all volumes at library init
    2012-01-27 Jeffrey Altman    (6616) Windows: Refactor and consolidate afsredir invalidation
    2012-01-27 Jeffrey Altman    (6595) Windows: Stop the thundering herd
    2012-01-24 Marc Dionne       (6615) vlserver: Consolidate VLDB entry server flag definitions
    2012-01-23 Simon Wilkinson   (5816) viced: Remove the LWP fileserver
    2012-01-23 Andrew Deason     (6548) vol: remove SYNC fatal_error processing
    2012-01-23 Derrick Brashear  (6546) libafs: add replicated connection pool
    2012-01-23 Jeffrey Altman    (6601) Windows: store data verification mode
    2012-01-23 Jeffrey Altman    (6559) Windows: make lock reader history debug only
    2012-01-23 Jeffrey Altman    (6600) Windows: VIOC_GETUNIXMODE = smb_IoctlGetUnixMode
    2012-01-23 Jeffrey Altman    (6599) Windows: fix fs setcrypt help message
    2012-01-23 Jeffrey Altman    (6598) Windows; release BIOD after status merge
    2012-01-23 Derrick Brashear  (6515) viced: disable rx keepalives during disk io
    2012-01-23 Jeffrey Altman    (6603) Revert "Windows: disable memory extent interface"
    2012-01-22 Marc Dionne       (5550) viced: remove FS_STATS_DETAILED
    2012-01-20 Jeffrey Altman    (6563) Windows: failover and retry for VBUSY
    2012-01-20 Jeffrey Altman    (6118) Windows: improved idle dead time handling
    2012-01-20 Jeffrey Altman    (6128) rx: RX_CALL_IDLE and RX_CALL_BUSY
    2012-01-20 Peter Scott       (6573) Windows Asynchronous purging of file content after a DV change
    2012-01-19 Jeffrey Altman    (6576) Windows: cm_buf refcnt must hold buf_globalLock
    2012-01-19 Jeffrey Altman    (6575) Windows: Redesign daemon thread queue management
    2012-01-19 Jeffrey Altman    (6562) Windows: prevent race assigning Fcb in AFSInitFcb()
    2012-01-19 Jeffrey Altman    (6556) Windows: cm_EndCallbackGrantingCall refactoring
    2012-01-18 Jeffrey Altman    (6558) Windows: deadlock bet. DirEntry lock + DirectoryNodeHdr.TreeLock
    2012-01-18 Peter Scott       (6571) Windows: Correctly mark extents dirty when using the non-persistent AFS cache
    2012-01-18 Peter Scott       (6528) Windows: Performing async work after cache invalidation
    2012-01-18 Marc Dionne       (6568) Parallel build fixes
    2012-01-18 Marc Dionne       (6567) Linux 3.3: use umode_t for mkdir and create inode ops
    2012-01-18 Marc Dionne       (6566) Linux: use standard macro for set_nlink configure test
    2012-01-18 Derrick Brashear  (6565) volinfo: fix formating of placeholder printfs
    2012-01-18 Marc Dionne       (6564) rx: Correctly test for end of call queue
    2012-01-18 Jeffrey Altman    (6557) Windows: disable memory extent interface
    2012-01-18 Jeffrey Altman    (6555) Windows: restrict service to 2 cpus by default
    2012-01-18 Jeffrey Altman    (6554) Windows: AFS_SERVER_FLUSH_DELAY AFS_SERVER_PURGE_DELAY
    2012-01-18 Jeffrey Altman    (6553) Windows: AFSParseName edge cases
    2012-01-18 Jeffrey Altman    (6552) Windows: afs root is always a directory
    2012-01-17 Ken Dreyer        (6561) fix spelling in comments
    2012-01-11 Andrew Deason     (6530) DAFS: Fix SYNC_FAILED VScheduleSalvage_r log
    2012-01-11 Andrew Deason     (6529) vol: Fix VCreateVolume special inode cleanup
    2012-01-11 Jeffrey Altman    (6498) Windows: dir buffers out of date - mark them as such
    2012-01-11 Jeffrey Altman    (6514) Windows: Avoid file server rpcs on deleted files
    2012-01-11 Jeffrey Altman    (6508) Windows: use local var for interlocked result
    2012-01-11 Jeffrey Altman    (6507) Windows: AFSParseMountPointTarget buffer overrun
    2012-01-11 Jeffrey Altman    (6460) Windows: Directory Enumeration, DVs, and TreeLocks
    2012-01-11 Jeffrey Altman    (6506) Windows: correct log messages in AFSCleanup
    2012-01-11 Jeffrey Altman    (6505) Windows: Return Dir Data Version from AFSCleanup
    2012-01-11 Jeffrey Altman    (6504) Windows: reorg open handle counts and Fcb->NPFcb->Resource
    2012-01-11 Jeffrey Altman    (6503) Windows: Permit renames of open files
    2012-01-11 Jeffrey Altman    (6502) Windows: Do not prime the service directory cache
    2012-01-11 Jeffrey Altman    (6501) Windows: More specific error values
    2012-01-11 Jeffrey Altman    (6500) Windows: do not flush dirty extents without permission
    2012-01-09 Marc Dionne       (6519) libuafs: only rebuild h directory when needed
    2012-01-09 Derrick Brashear  (6525) opr: fix generated target
    2012-01-09 Marc Dionne       (6523) opr: add buildtools target
    2012-01-08 Andrew Deason     (6524) Make libjafs buildable again
    2012-01-07 Derrick Brashear  (6510) afs: discard cached state when we are unsure of validity
    2012-01-07 Derrick Brashear  (6516) afs: put back conn if not using in checkserver loop
    2012-01-07 Derrick Brashear  (6517) rx: add and export a public keepalive toggle
    2012-01-06 Chaskiel Grundman (6444) Make src/opr objdir safe
    2012-01-06 Derrick Brashear  (6497) afs: increase idledead time
    2012-01-05 Derrick Brashear  (6509) ukernel: enable nat ping again
    2012-01-05 Marc Dionne       (6513) Use offsetof() in set_header_word to get field offset
    2012-01-05 Simon Wilkinson   (6511) afs: Negate codes using a clear, standard method
    2012-01-05 Marc Dionne       (6512) vol: initialize readmeinode
    2012-01-03 Michael Meffie    (6330) Unix CM: reset blacklist on hard-mount retry
    2012-01-03 Andrew Deason     (6385) DAFS: Atomically re-hash vnode in VGetFreeVnode_r
    2012-01-03 Andrew Deason     (6431) afs: Grab a reference to setp in afs_icl_Event4
    2012-01-03 Geoffrey Thomas   (6491) linux: fsync on a directory should return 0, not EINVAL
    2012-01-03 Geoffrey Thomas   (6247) rpm: Don't attempt to restart on upgrade when using systemd
    2012-01-01 Jeffrey Altman    (6446) Windows: STATUS_OBJECT_PATH_INVALID == invalid parent directory
    2012-01-01 Peter Scott       (6447) Windows: Support correct status codes from service
    2012-01-01 Peter Scott       (6445) Windows: Handle invalid node types
    2012-01-01 Jeffrey Altman    (6459) Windows: AFSFileUpdateResultCB ParentDataVersion
    2012-01-01 Jeffrey Altman    (6457) Windows: renames that overwrite existing target
    2012-01-01 Jeffrey Altman    (6455) Windows: AFSDirEnumResp and AFSDirEnumEntry changes
    2012-01-01 Jeffrey Altman    (6454) Windows: Add AFSFileEvalResultCB
    2012-01-01 Jeffrey Altman    (6453) Windows: Add AFSFileCleanupResultCB
    2012-01-01 Jeffrey Altman    (6432) Windows: RequestExtents avoid bufWrite if rdr held
    2012-01-01 Jeffrey Altman    (6433) Windows: Request extents readability
    2011-12-31 Jeffrey Altman    (6462) Windows: avoid race during Fcb cleanup
    2011-12-31 Jeffrey Altman    (6461) Windows: avoid deadlock if bulk error during enum
    2011-12-31 Jeffrey Altman    (6458) Windows: AFSInsertHashEntry can fail
    2011-12-31 Jeffrey Altman    (6456) Windows: additional AFSValidateEntry logging
    2011-12-31 Jeffrey Altman    (6452) Windows: add DV and error status to dir enumerations
    2011-12-31 Jeffrey Altman    (6451) Windows: protect merge status against dscp == scp
    2011-12-31 Jeffrey Altman    (6450) Windows: protect dir ops by CM_SCACHESYNC_STOREDATA
    2011-12-31 Jeffrey Altman    (6449) Windows: init scache DV=CM_SCACHE_VERSION_BAD
    2011-12-31 Jeffrey Altman    (6442) Windows: afsredirlib log messages
    2011-12-31 Jeffrey Altman    (6441) Windows: Symlink resolve failure error
    2011-12-31 Jeffrey Altman    (6440) Windows: Make idle dead timeout very long
    2011-12-31 Jeffrey Altman    (6439) Windows: replace strdup with xdr_alloc in callback processing
    2011-12-31 Jeffrey Altman    (6438) windows: osi_TSignalForMLs simplify
    2011-12-31 Jeffrey Altman    (6437) Windows: osisleep do not tamper with queues
    2011-12-31 Jeffrey Altman    (6436) Windows: osi_sleepInfo tid type
    2011-12-31 Jeffrey Altman    (6435) Windows: add osi_TWaitExt(), fix osi_TWait()
    2011-12-31 Jeffrey Altman    (6434) Windows: use waiters counter instead of osi_TEmpty
    2011-12-31 Jeffrey Altman    (6430) Windows: kauth search for kerberos iv port first
    2011-12-27 Andrew Deason     (6410) klog.krb5: cast get_cred_keylen to unsigned
    2011-12-27 Andrew Deason     (6413) afs: Panic on afs_conn refcount imbalance
    2011-12-27 Andrew Deason     (6419) afs: Add afs_WriteDCache sanity checks
    2011-12-27 Andrew Deason     (6418) afs: Cope with afs_GetValidDSlot errors
    2011-12-27 Andrew Deason     (6417) afs: Do not always ignore errors in afs_GetDSlot
    2011-12-27 Andrew Deason     (6416) afs: Remove second argument to afs_GetDSlot
    2011-12-27 Andrew Deason     (6412) afs: Indicate error from afs_osi_Read/Write better
    2011-12-27 Andrew Deason     (6411) afs: afs_osi_Read/Write returns negative on error
    2011-12-27 Andrew Deason     (6422) fuse: Autodetect Solaris 11 FUSE
    2011-12-27 Andrew Deason     (6421) afsd.fuse: Solaris 11 support
    2011-12-27 Andrew Deason     (6400) afsd: Parse cacheinfo during argument parsing
    2011-12-27 Andrew Deason     (6390) fuse: Add -oallow_other by default where possible
    2011-12-25 Jeffrey Altman    (6424) Windows: avoid race in cm_GetNewSCache
    2011-12-25 Jeffrey Altman    (6423) Windows: cm_BufWrite() must wait in cm_SyncOp()
    2011-12-25 Peter Scott       (6420) Windows: Avoid bottleneck on VolumeLock
    2011-12-25 Simon Wilkinson   (6425) rx: Don't adjust non-existent events
    2011-12-22 Jeffrey Altman    (6399) Windows: AFSCleanup extent processing
    2011-12-22 Jeffrey Altman    (6398) Windows: AFSRetrieveValidAuthGroup FILE_READ_DATA
    2011-12-22 Jeffrey Altman    (6397) Windows: AFSRequestExtentsAsync retry with alt authgroup
    2011-12-22 Jeffrey Altman    (6396) Windows: Use AuthGroups for extent request error reporting
    2011-12-22 Jeffrey Altman    (6395) Windows: Explicit permission check on extent release
    2011-12-22 Jeffrey Altman    (6394) Windows: RDR_CleanupFileEntry restrict extent claw back
    2011-12-22 Jeffrey Altman    (6393) Windows: remove unused AFSRequestExtents()
    2011-12-22 Jeffrey Altman    (6392) Windows: Bad DV invalidate only when new DV not 0
    2011-12-22 Jeffrey Altman    (6391) Windows: Define times in terms of AFS_ONE_SECOND
    2011-12-20 Andrew Deason     (6387) Include afsconfig.h before anything else
    2011-12-19 Jeffrey Altman    (6377) Windows: avoid deadlock during SetRenameInformation
    2011-12-18 Jeffrey Altman    (6375) Windows: terminate HOSTS/LMHOSTS with newline
    2011-12-18 Peter Scott       (6333) Windows: Track AuthGroup in Context Control Block
    2011-12-18 Jeffrey Altman    (6365) Windows: Tear down extents upon file deletion
    2011-12-18 Jeffrey Altman    (6364) Windows: notify file size change if flushed
    2011-12-18 Jeffrey Altman    (6363) Windows: forget data version only for flushing
    2011-12-18 Jeffrey Altman    (6362) Windows: fix indentation
    2011-12-18 Jeffrey Altman    (6361) Windows: AFSSetRenameInfo log message
    2011-12-18 Jeffrey Altman    (6360) Windows: return error to system paging requests
    2011-12-17 Jeffrey Altman    (6352) Windows: log volume and authgroup for redir open
    2011-12-17 Jeffrey Altman    (6359) Windows: save fid/type for redirector invalidation
    2011-12-17 Jeffrey Altman    (6351) Windows: move to head of queue no-op if not in queue
    2011-12-17 Jeffrey Altman    (6350) Windows: Properly convert FID structures
    2011-12-17 Jeffrey Altman    (6344) Windows: propagate directory enumeration failures
    2011-12-17 Peter Scott       (6343) Windows Problem with cross-directory rename
    2011-12-17 Jeffrey Altman    (6337) vol: fix a08c3207255756c825ab69a19e04f79dd879c646
    2011-12-17 Jeffrey Altman    (6332) Windows: Update Adv Firewall Rules
    2011-12-16 Andrew Deason     (6335) afs: Clear VHardMount on ResetVolumeInfo
    2011-12-16 Andrew Deason     (6334) viced: Yell when we GetSomeSpace_r
    2011-12-15 Jeffrey Altman    (6339) Revert "Windows: cs_CZ localization"
    2011-12-15 Jeffrey Altman    (6227) Windows: cs_CZ localization
    2011-12-15 Michael Meffie    (5102) volscan: print vnode metadata information
    2011-12-14 Michael Meffie    (5532) bozo: preserve all options over restart
    2011-12-14 Michael Meffie    (5534) bozo: retry start after error stops
    2011-12-14 Andrew Deason     (3892) volser: Do not reset copyDate in ReClone
    2011-12-14 Garrett Wollman   (5121) util: simplify thread-name interface
    2011-12-14 Jonathan A. Kollasch (5595) build tsalvaged, tvolser, and dvolser targets on *nbsd*
    2011-12-14 Simon Wilkinson   (6116) Unix CM: Log reason for marking server up or down
    2011-12-14 Jeffrey Altman    (6248) Windows: AFSRDFSProvider stack overrun
    2011-12-14 Derrick Brashear  (6252) vos: fix code to not triple-negate
    2011-12-14 Michael Meffie    (5101) volinfo: implement -checkout option
    2011-12-14 Michael Meffie    (6108) vol: log error reason on header read failure
    2011-12-14 Derrick Brashear  (6256) libafs: disable mtu discovery
    2011-12-14 Derrick Brashear  (6255) libafs: only do pings for default conn with root uid
    2011-12-10 Jeffrey Altman    (6244) Windows: memory leak when setting tokens via smb
    2011-12-10 Jeffrey Altman    (6243) Windows: Suspend/Resume for afsd_service
    2011-12-09 Karl Ramm         (6223) Print "waiting for job termination" at most once.
    2011-12-08 Jeffrey Altman    (6237) Windows: increase timeout for extent request retries
    2011-12-08 Jeffrey Altman    (6236) Windows: include owner/group in Security DACL
    2011-12-05 Jeffrey Altman    (6230) afs: prevent nat pings on destroyed connections
    2011-12-04 Jeffrey Altman    (6222) Windows: Release Notes Updates
    2011-12-04 Jeffrey Altman    (6219) rx: Make CALL_RELE and CALL_HOLD lock refcnt mutex
    2011-12-04 Benjamin Kaduk    (6203) FBSD: switch afsi_SetServerIPRank implementation
    2011-12-04 Jeffrey Altman    (6218) rx: Helper function for decrementing conn refcnt
    2011-12-04 Simon Wilkinson   (6182) rx: Hide the rx_packet.h
    2011-12-04 Jeffrey Altman    (6209) Windows: define MIN and MAX
    2011-12-04 Simon Wilkinson   (6181) rx: Make the rx_call structure private
    2011-12-04 Simon Wilkinson   (6180) rx: Make struct rx_connection private
    2011-12-04 Jeffrey Altman    (6208) Windows: apply Nat Pings only to cm_rootUser connections
    2011-12-04 Jeffrey Altman    (6207) Windows: track cm_rootUser connections
    2011-12-04 Jeffrey Altman    (6205) rx: rx_conn/rx_peer refCount signed
    2011-12-03 Simon Wilkinson   (6206) rx: Some kernels have no reschedule function
    2011-12-03 Jeffrey Altman    (6195) Windows: npdll connected query returns no usage
    2011-12-03 Simon Wilkinson   (6196) Windows: Use roken's min and max
    2011-12-03 Edward Z. Yang    (6093) Add OpenAFS to the dependencies of remote-fs.
    2011-12-03 Benjamin Kaduk    (6193) Remove dead code from rxi_FindIfnet()
    2011-12-03 Simon Wilkinson   (6091) rx: Refactor MaxMTU error checking
    2011-12-03 Andrew Deason     (6179) salvager: Create link table with volume group id
    2011-12-03 Andrew Deason     (6168) DAFS: Ensure logging on attach2 errors
    2011-12-03 Andrew Deason     (6167) DAFS: Avoid unnecessary preattach on FSYNC_VOL_ON
    2011-12-03 Andrew Deason     (6166) DAFS: Log more for VPreAttachVolumeByVp odd states
    2011-12-03 Andrew Deason     (6165) DAFS: Ensure GetVolume errors on ERROR volumes
    2011-12-03 Andrew Deason     (6164) DAFS: Do not transition to ERROR on trivial errors
    2011-12-03 Jeffrey Altman    (6183) Windows: GetInfoTip really set return to NULL
    2011-12-02 Jeffrey Altman    (6178) Windows: memset in RDR_RequestFileExtentsAsync
    2011-12-02 Jeffrey Altman    (6177) Windows: cm_MergeStatus redirector invalidation
    2011-12-02 Jeffrey Altman    (6176) Windows: cm_MergeStatus use new DV to purge buffers
    2011-12-02 Jeffrey Altman    (6175) Windows: use interlocked increment on cm_buf_t refcnt
    2011-12-02 Jeffrey Altman    (6174) Windows: buf_GetNewLocked should use cleaned cm_buf
    2011-12-02 Jeffrey Altman    (6173) Windows: fix buf_Recycle() comment
    2011-12-02 Jeffrey Altman    (6172) Windows: buf_CleanAsync is not async; rename it
    2011-12-02 Jeffrey Altman    (6171) Windows: convert buf_IncrSyncer to pthreads
    2011-12-01 Jeffrey Altman    (6159) Windows: invalidate rdr for CM_SCACHE_VERSION_BAD
    2011-12-01 Jeffrey Altman    (6158) Windows: do not set CM_SCACHEFLAG_EACCES twice
    2011-12-01 Derrick Brashear  (6163) afsd.fuse: link libopr
    2011-12-01 Andrew Deason     (6162) SOLARIS: Define BSD_COMP for non-UKERNEL on 5.11
    2011-12-01 Derrick Brashear  (6157) remove CopyOnWrite2 and unused vars
    2011-11-30 Derrick Brashear  (6135) viced: disable accelerated copyonwrite
    2011-11-30 Jeffrey Altman    (6132) Windows: Wix disable integrated logon by default
    2011-11-29 Jeffrey Altman    (6142) Windows: AFSRDFSProvider log to file
    2011-11-29 Jeffrey Altman    (6141) Windows: NPEnumResources no Printer support
    2011-11-29 Jeffrey Altman    (6140) Windows: NPGetConnectionCommon buffer too small
    2011-11-29 Jeffrey Altman    (6139) Windows: no drive subst for NPCancelConnection
    2011-11-29 Jeffrey Altman    (6138) Windows: refactor NPCancelConnection
    2011-11-29 Jeffrey Altman    (6137) Windows: Mount Point and Symlink Overlay Icons
    2011-11-29 Simon Wilkinson   (5841) rx: Use a red black tree for the event stack
    2011-11-29 Simon Wilkinson   (5842) Unix CM: Build rbtrees in kernel
    2011-11-29 Andrew Deason     (6136) udebug: Fix endianness when fudging lastYesHost
    2011-11-29 Jeffrey Altman    (6134) Windows: FSync not CleanVnode during Cleanup
    2011-11-29 Jeffrey Altman    (6133) Windows: Wix cell names can be greater than 120 chars
    2011-11-29 Jeffrey Altman    (6131) Windows: cache format version change
    2011-11-29 Jeffrey Altman    (6130) Windows: osi_mutex / osi_rwlock changes
    2011-11-28 Jeffrey Altman    (6119) Windows: convert daemons threads to pthreads
    2011-11-28 Benjamin Kaduk    (6127) FBSD: cleanup dvp locking for ISDOTDOT
    2011-11-28 Derrick Brashear  (6126) namei: force-close fd on read or write error
    2011-11-27 Edward Z. Yang    (6120) Linux: 3: Update specfile to know about 3.* kernels.
    2011-11-25 Simon Wilkinson   (6117) Unix CM: Fix PutVolume in afs_BlackListOnce
    2011-11-23 Jeffrey Altman    (6110) Windows: add trace logging to Pioctl File Info Query
    2011-11-23 Jeffrey Altman    (6109) Windows: _._AFS_IOCTL_._ size is zero
    2011-11-22 Jeffrey Altman    (6105) Windows: RDR_InvalidateObject do not hold locks
    2011-11-22 Jeffrey Altman    (6103) Windows: cm_GetSCache do not release unheld lock
    2011-11-22 Jeffrey Altman    (6102) Windows: Use Jenkins' Hash
    2011-11-21 Simon Wilkinson   (6095) opr: Add Bob Jenkins's hash functions
    2011-11-21 Anders Kaseorg    (6096) Linux: 3.2: Use set_nlink to update i_nlink
    2011-11-19 Andrew Deason     (6051) afs: Leave cellnum alone for explicit mtpt cell
    2011-11-18 Derrick Brashear  (5843) namei: tweak getlinkbyte error handling
    2011-11-18 Michael Meffie    (5743) auth: avoid excessive stat of cellservdb
    2011-11-18 Michael Meffie    (5803) vol: rate-limit volume usage updates
    2011-11-18 Jeffrey Altman    (6075) Windows: RDR_RequestFileExtentsAsync unheld lock
    2011-11-18 Jeffrey Altman    (6072) Windows: must obtain and release an actual lock
    2011-11-18 Jeffrey Altman    (6071) Windows: non-release only worker threads can release
    2011-11-16 Jeffrey Altman    (6059) auth: initKeys before first error exit path
    2011-11-16 Jeffrey Altman    (6065) Windows: Do not install IBM AFS HLP files
    2011-11-16 Jeffrey Altman    (6054) Windows: buf_CleanAsyncLocked dirty range only
    2011-11-16 Jeffrey Altman    (6053) Windows: create scache->redirMx to reduce contention
    2011-11-16 Jeffrey Altman    (6058) Windows: Increase default number of daemon threads
    2011-11-16 Jeffrey Altman    (6057) Windows: cm_SetupStoreBIOD use firstModOffset chunk
    2011-11-16 Jeffrey Altman    (6056) Windows: Fairness for background operations
    2011-11-16 Andrew Deason     (6050) vlserver: Avoid atoi for vol ids
    2011-11-15 Jeffrey Altman    (6048) Windows: Create default Security Descriptor
    2011-11-15 Jeffrey Altman    (6046) Windows: interlocked refCount increment in cm_GetSCache
    2011-11-14 Jeffrey Altman    (6016) Windows: netidmgr krb5_cc_get_principal can fail
    2011-11-13 Jeffrey Altman    (6004) Windows: smb_ReceiveNTCreateX create smb_fid earlier
    2011-11-13 Jeffrey Altman    (6003) Windows: cm_GetSCache avoid holding cm_scacheLock
    2011-11-13 Jeffrey Altman    (6002) Windows: avoid null ptr in RDR_RequestFileExtentsAsync
    2011-11-13 Jeffrey Altman    (6001) Windows: Track active RPCs per scache_t
    2011-11-13 Jeffrey Altman    (6000) Windows: fix locking hierarchy in service
    2011-11-12 Andrew Deason     (5790) afs: Do not use separate array for srvAddrs
    2011-11-12 Simon Wilkinson   (5840) rx: Turn the rxevent_Cancel macro into a function
    2011-11-12 Simon Wilkinson   (5839) rx: New signature for rx event functions
    2011-11-12 Simon Wilkinson   (5838) opr: Add a red/black tree implementation
    2011-11-12 Simon Wilkinson   (5837) rx: Add a helper function for delayed acks
    2011-11-12 Simon Wilkinson   (5836) opr: Add opr_containerof
    2011-11-11 Jeffrey Altman    (5823) Windows: Enforce Share Access
    2011-11-11 Jeffrey Altman    (5812) Windows: Add Vista/Win7 Firewall Configuration
    2011-11-11 Michael Meffie    (1562) ihandle positional read and write
    2011-11-11 Andrew Deason     (5835) SOLARIS: Do not build x86 kernel module on 5.11
    2011-11-11 Andrew Deason     (5833) namei: Remove extraneous rmdir
    2011-11-11 Andrew Deason     (5832) vol: Remove O_EXCL|O_TRUNC combinations
    2011-11-11 Jeffrey Altman    (5829) Windows: FSCTL_SET_REPARSE_POINT not yet implemented
    2011-11-11 Jeffrey Altman    (5828) Windows: FSCTL_SET_REPARSE_POINT error
    2011-11-11 Jeffrey Altman    (5827) Windows: FSCTL_IS_PATHNAME_VALID return success
    2011-11-10 Jeffrey Altman    (5826) Windows: these fsctl cmds are not implemented
    2011-11-10 Jeffrey Altman    (5825) Windows: Additional trace logging
    2011-11-10 Jeffrey Altman    (5824) Windows: service must set reparse point attribute
    2011-11-10 Peter Scott       (5834) Windows: Correctly increment PIOCtl DE
    2011-11-10 Peter Scott       (5830) Windows: FileNetworkPhysicalNameInfo implementation
    2011-11-10 Jeffrey Altman    (5741) Windows: improve store data parallelism
    2011-11-10 Andrew Deason     (5822) volser: Preserve needsSalvaged during restore
    2011-11-09 Derrick Brashear  (5818) viced: avoid bogus handle in rename
    2011-11-09 Andrew Deason     (5817) regen: Fail on failures
    2011-11-09 Andrew Deason     (4486) Add "pretty" build option
    2011-11-09 Andrew Deason     (5819) Specify pattern rules in addition to suffix rules
    2011-11-09 Andrew Deason     (5801) Add setenv/unsetenv to roken
    2011-11-07 Derrick Brashear  (5814) dafs: avoid null deref getting volume header
    2011-11-05 Andrew Deason     (5800) salvager: Implement AskDAFS via SYNC flags
    2011-11-05 Derrick Brashear  (5813) redhat: make rpms build on pre-f15 again
    2011-11-05 Derrick Brashear  (5807) ukernel: handle pioctl errors properly in ktc
    2011-11-05 Andrew Deason     (5811) libafsauthent: Remove obsolete HP-UX workaround
    2011-11-05 Andrew Deason     (5810) volser: Remove debugging log messages
    2011-11-04 Simon Wilkinson   (5794) Unix CM: Fix dir buffer leak in afs_readdir
    2011-11-04 Andrew Deason     (5808) DAFS: Deal with exclusive-state volume headers
    2011-11-04 Jeffrey Altman    (5806) Windows: NPCancelConnection set correct length
    2011-11-04 Peter Scott       (5805) Windows: Failed to release correct lock
    2011-11-04 Jeffrey Altman    (5804) Windows: do not leak resource in AFSQueryDirectory
    2011-11-04 Jeffrey Altman    (5802) Windows: KFW_AFS should use API: ccache
    2011-11-04 Jeffrey Altman    (5799) Windows: Simplify KFW_AFS_klog
    2011-11-04 Ken Dreyer        (5745) doc: limitations of addsite on different partitions
    2011-11-04 Derrick Brashear  (5593) ukernel: install our sysincludes to root.perf
    2011-11-03 Andrew Deason     (5798) Import of code from heimdal
    2011-11-03 Andrew Deason     (5786) Solaris: Specify ARCHFLAGS in CFLAGS
    2011-11-03 Andrew Deason     (5785) Do OPENAFS_OSCONF before compiler autoconf tests
    2011-11-03 Andrew Deason     (5787) Remove -settime/RXAFS_GetTime client support
    2011-11-03 Michael Meffie    (5742) opr: queue swap
    2011-11-03 Andrew Deason     (5797) external: trigger git commit-msg hooks on import
    2011-11-03 Andrew Deason     (5796) external: commit imports with --no-verify
    2011-11-03 Andrew Deason     (5795) Import setenv.c and unsetenv.c from roken
    2011-11-03 Jeffrey Altman    (5793) Windows: always set reparse point attrib for symlink
    2011-11-03 Jeffrey Altman    (5792) Windows: fix deadlock in symlink Attrib retrieval
    2011-11-03 Jeffrey Altman    (5791) Windows: remember when a reparse point is opened
    2011-11-02 Jeffrey Altman    (5784) Windows: Mount points are always directories
    2011-11-02 Jeffrey Altman    (5783) Windows: add AFSRetrieveParentPath()
    2011-11-02 Peter Scott       (5782) Windows: Retrieve file attributes on symlinks
    2011-11-02 Jeffrey Altman    (5619) klog.krb5: enforce DES for rxkad
    2011-11-02 Jonathan A. Kollasch (5596) kdump-build: don't install when it hasn't been built for *bsd*
    2011-11-01 Peter Scott       (5775) Windows: DE Reference count added during create
    2011-11-01 Peter Scott       (5748) Windows: correct ordering of reparse point tests
    2011-11-01 Jeffrey Altman    (5774) Windows: change AFSProcessUserFsRequest default
    2011-11-01 Peter Scott       (5736) Windows: Directory Entry Processing
    2011-11-01 Jeffrey Altman    (5773) Windows: log FSCTL_CSC_INTERNAL requests
    2011-11-01 Jeffrey Altman    (5772) Windows: add braces to case statements
    2011-11-01 Jeffrey Altman    (5739) Windows: additional trace logging for afsredirlib
    2011-11-01 Jeffrey Altman    (5738) Windows: Reimplement AFSGenerateCRC()
    2011-10-30 Marc Dionne       (5740) Linux: 3.1: update RCU path walking detection in permission i_op
    2011-10-29 Simon Wilkinson   (5737) rx: Remove the ADAPT_WINDOW code
    2011-10-28 Jeffrey Altman    (5735) Windows: cm_Rename break in 9cf7a628c2ff178b2fa236d2c0a41ca9be315036
    2011-10-28 Jeffrey Altman    (5734) Windows: out of date version not in current chunk
    2011-10-27 Edward Z. Yang    (5637) linux: Update Packaging to build OpenAFS services for Fedora's systemd
    2011-10-27 Jeffrey Altman    (5733) Windows: only flush buffers on shutdown if running
    2011-10-26 Jeffrey Altman    (5731) Windows: Do not EEXIST exact match during rename
    2011-10-26 Jeffrey Altman    (5732) opr: build on Windows after queue.h move
    2011-10-25 Simon Wilkinson   (5656) opr: Move queue header out of util
    2011-10-25 Rod Widdowson     (5652) Windows: Look for 8.3 name when doing a rename
    2011-10-25 Peter Scott       (5640) Windows: New Trace for DirEntry tracking problem
    2011-10-25 Jeffrey Altman    (5627) Windows: Free work item memory with tag value
    2011-10-25 Jeffrey Altman    (5626) Windows: free pointer after last reference
    2011-10-25 Jeffrey Altman    (5730) Windows: close leak in AFSPrimaryVolumeWorkerThread
    2011-10-25 Jeffrey Altman    (5625) Windows: AFSInitPIOCtlDirectoryCB free in try_exit
    2011-10-25 Jeffrey Altman    (5727) Windows: afsredir only wants shortName if not 8.3
    2011-10-25 Jeffrey Altman    (5642) Windows: Use SetFlag macro when setting flag
    2011-10-25 Jeffrey Altman    (5641) Windows: minor type in trace output
    2011-10-25 Jeffrey Altman    (5638) Windows: AFSRemoveCaseInsensitiveDirEntry corrections
    2011-10-25 Jeffrey Altman    (5624) Windows: AFSEvaluateTargetByName free buffer if no return
    2011-10-25 Jeffrey Altman    (5623) Windows: remove unused code block
    2011-10-25 Jeffrey Altman    (5621) Windows: re-indent afsredir log message params
    2011-10-25 Rod Widdowson     (5651) Windows:  Defer deref of a directoryEntry
    2011-10-25 Rod Widdowson     (5646) Windows: Set new file index correctly during rename
    2011-10-24 Marc Dionne       (5650) cache bypass: don't define iovecp for UKERNEL
    2011-10-24 Michael Meffie    (5615) DAFS: fssync online requires a partition name argument
    2011-10-24 Jacob Thebault-Spieker (5049) allow cloning of any volume to any volume with same parent ID
    2011-10-24 Michael Meffie    (5555) bozo: build notifier sample program
    2011-10-24 Michael Meffie    (5533) bozo: test program update
    2011-10-24 Andrew Deason     (5319) DAFS: Remove VOL_SALVAGE_INVALIDATE_HEADER
    2011-10-24 Jacob Thebault-Spieker (5046) remove check for disallowing clones of backup or ro volumes
    2011-10-24 Andrew Deason     (5614) viced: Check for HOSTDELETED in stillborn check
    2011-10-24 Andrew Deason     (5594) volser: Remove ExtractVolId
    2011-10-24 Andrew Deason     (5620) vos offline: Bring volume back online for -busy
    2011-10-24 Andrew Deason     (5616) vlserver: Log to VLLog by default, not PtLog
    2011-10-24 Derrick Brashear  (5658) bypasscache: allow arbitrary sized iovecs
    2011-10-24 Derrick Brashear  (5600) ukernel: get an ip address even when dns and hosts suck
    2011-10-24 Derrick Brashear  (5554) bypasscache: do errors correctly
    2011-10-24 Rod Widdowson     (5649) Windows: Remove unused cleanup flag
    2011-10-24 Simon Wilkinson   (5661) roken: Add *progname() to shared library exports
    2011-10-24 Marc Dionne       (5666) dir: add missing return in DRead
    2011-10-24 Simon Wilkinson   (5665) tests: volser doesn't need rxgk yet
    2011-10-24 Simon Wilkinson   (5664) tests: Add opr library for ktime test
    2011-10-24 Simon Wilkinson   (5663) rpm: Add new libraries
    2011-10-24 Simon Wilkinson   (5662) rpm: Turn on debugging
    2011-10-24 Simon Wilkinson   (5660) rx: Define afs_kmutex_t for LWP too
    2011-10-24 Simon Wilkinson   (5659) dir: Don't leak a buffer on a failed Enumerate
    2011-10-24 Derrick Brashear  (5604) rx: ackall handling
    2011-10-24 Derrick Brashear  (5598) ukernel: set close-on-exec on our socket
    2011-10-24 Derrick Brashear  (5602) linux: makesrpm should cope with releases with letters
    2011-10-23 Derrick Brashear  (5605) ukernel: add morepackets check in listener
    2011-10-23 Andrew Deason     (5648) LINUX: Fix afs_linux_pag_to_groups signature
    2011-10-23 Andrew Deason     (5238) LINUX: Revert group changes on keyring failure
    2011-10-23 Andrew Deason     (5645) viced: Do not swallow errors on StoreData recovery
    2011-10-23 Derrick Brashear  (5606) ukernel: set pthread stacksize to an integer multiple of 8k
    2011-10-23 Simon Wilkinson   (5655) dir: Remove double release in FindBlobs
    2011-10-23 Derrick Brashear  (5612) afs: don't try GetDownD if nothing to get
    2011-10-23 Derrick Brashear  (5613) ukernel: don't define rdwr env on linux
    2011-10-23 Derrick Brashear  (5599) afs: on uuid init fail, don't leave garbage behind
    2011-10-23 Derrick Brashear  (5603) rx: Don't clear the receive queue when out of packets
    2011-10-23 Benjamin Kaduk    (5657) FBSD: typo fix
    2011-10-23 Andrew Deason     (4482) auth: Get correct viceid in legacy GetToken
    2011-10-23 Andrew Deason     (4481) auth: Force correct evenness on rxkad tokens
    2011-10-23 Simon Wilkinson   (5654) docs: Refer to dafs binaries by their real names
    2011-10-23 Simon Wilkinson   (5653) ptserver: Don't check for noauth before rebuilding
    2011-10-23 Benjamin Kaduk    (5572) FBSD: deal with kernel API rename
    2011-10-23 Andrew Deason     (4483) aklog_dynamic_auth: Support new SetToken pioctl



### Patches merged into the devel 1.7.x branch

    Date       Committer        Change# Description
    2012-04-16 Jeffrey Altman    (7222) rx: Remove surplus call to FindPeer
    2012-04-16 Jeffrey Altman    (7221) rx: dec rx_nWaiting on clearing RX_CALL_WAIT_PROC
    2012-04-16 Jeffrey Altman    (7219) rx: conn_call_lock leak
    2012-04-15 Jeffrey Altman    (7217) DOC: Factored common text out of the vos_backup and vos_dump man pages
    2012-04-15 Jeffrey Altman    (7216) Windows: pioctl use GetFileAttributes
    2012-04-15 Jeffrey Altman    (7215) Windows: _._AFS_IOCTL_._ hidden and system
    2012-04-15 Jeffrey Altman    (7214) Windows: Remove PurgeContent param AFSVerifyEntry
    2012-04-15 Jeffrey Altman    (7213) Windows: Flush data and then drop locks
    2012-04-15 Jeffrey Altman    (7212) rx: Rework code which pulls packet from recv queue
    2012-04-15 Jeffrey Altman    (7211) rx: Tidy up currentPacket handling
    2012-04-12 Jeffrey Altman    (7193) Windows: missing brace in RDR_CleanupFileEntry
    2012-04-12 Jeffrey Altman    (7192) Windows: Do not delete in CleanupFile if error
    2012-04-12 Jeffrey Altman    (7191) doc: distributed files are under dest
    2012-04-10 Jeffrey Altman    (7174) Windows: AFSValidateProcessEntry, ullProcessId 64-bit
    2012-04-10 Jeffrey Altman    (7173) roken: Add rk_getprogname to Windows mapfile
    2012-04-10 Jeffrey Altman    (7171) rx: Remove packet burst elements from peer struct
    2012-04-10 Jeffrey Altman    (7170) rx: Remove the unused packet skew code
    2012-04-10 Jeffrey Altman    (7169) rx: Hide internal packet functions
    2012-04-10 Jeffrey Altman    (7168) rx: Hide struct rx_peer from the rest of the tree
    2012-04-10 Jeffrey Altman    (7167) shlibafsrpc: Add additional XDR functions
    2012-04-10 Jeffrey Altman    (7166) libafsrpc: Export connection accessor fuctions
    2012-04-10 Jeffrey Altman    (7165) rxperf: Build again
    2012-04-10 Jeffrey Altman    (7164) rx: remove peer burst elements from rx/test
    2012-04-10 Jeffrey Altman    (7163) rx: rxi_AckAll isn't an event handler
    2012-04-10 Jeffrey Altman    (7162) rx: Tidy up function scope in rx.c
    2012-04-10 Jeffrey Altman    (7161) rx: Remove trailing else from RX_KERNEL_TRACE
    2012-04-10 Jeffrey Altman    (7160) rx: Remove unused ACKHACK macro
    2012-04-10 Jeffrey Altman    (7159) tests: rx needs roken
    2012-04-10 Jeffrey Altman    (7158) rx: Remove needless braces
    2012-04-10 Jeffrey Altman    (7157) rx: Handle negative returns on packet reads
    2012-04-10 Jeffrey Altman    (7156) rxgen: Tidy up server side freeing
    2012-04-10 Jeffrey Altman    (7155) rx: Get rid of some uneccessary temporary vars
    2012-04-10 Jeffrey Altman    (7154) Rx: Avoid lastBusy/PEER_BUSY discrepancy
    2012-04-10 Jeffrey Altman    (7153) Rx: Add missing rx_packet.h includes
    2012-04-10 Jeffrey Altman    (7152) Remove dead code from rxi_FindIfnet()
    2012-04-10 Jeffrey Altman    (7151) Windows: report error on panic
    2012-04-10 Jeffrey Altman    (7150) Windows: correct afsredir log entries
    2012-04-10 Jeffrey Altman    (7149) Windows: Refactor AFSValidateEntry
    2012-04-07 Jeffrey Altman    (7114) Windows: Version 1.7.9
    2012-04-07 Jeffrey Altman    (7113) Windows: 1.7.9 ChangeLog
    2012-04-07 Jeffrey Altman    (7112) Windows: Disk Full errors instead of Quota Exceeded
    2012-04-07 Jeffrey Altman    (7110) Windows: AFSCheckCellName one level of indirection
    2012-04-06 Jeffrey Altman    (7064) Windows: CleanACLEnt requires cm_scache write locked
    2012-04-06 Jeffrey Altman    (7063) Windows: Name Array store mount point and volume root
    2012-04-06 Jeffrey Altman    (7062) Windows: do not call time() in a loop
    2012-04-06 Jeffrey Altman    (7061) Windows: Add per object per user EACCES caching
    2012-04-06 Jeffrey Altman    (7060) Windows: Fail recursive path evaluation with access denied
    2012-04-06 Jeffrey Altman    (7059) Windows: Check Avail Space on extending SetEndOfFile
    2012-04-06 Jeffrey Altman    (7058) Windows: AFSVerifyEntry purge file data on DV change
    2012-04-06 Jeffrey Altman    (7056) Windows: Redirector must query volume size when asked
    2012-04-06 Jeffrey Altman    (7055) Windows: cm_AddACLCache lock ordering
    2012-04-05 Jeffrey Altman    (7053) rx: fix bad merge 95c38dff3740d7e24971ceb5875c06e7abfce102
    2012-04-03 Jeffrey Altman    (7044) Windows: Redirector Dir Enumeration Bug
    2012-04-03 Jeffrey Altman    (7041) Windows: cm_GetNewSCache must return NULL on failure
    2012-04-03 Jeffrey Altman    (7040) Rx: give grow mtu its own call ref count type
    2012-04-03 Jeffrey Altman    (7039) rx: conn->callNumber protected by conn_call_lock
    2012-04-03 Jeffrey Altman    (7038) Rx: rxi_FreeCall conn_call_lock vs call->lock deadlock
    2012-04-03 Jeffrey Altman    (7036) Windows: Pass name array to AFSRetrieveFileInformation
    2012-04-03 Jeffrey Altman    (7035) Windows: Use hash when comparing File IDs in redirector
    2012-04-03 Jeffrey Altman    (7034) Windows FindACLCache must hold scp write locked
    2012-04-03 Jeffrey Altman    (7033) Windows: fix indentation
    2012-04-03 Jeffrey Altman    (7032) Windows: Freelance HaveAccessRights
    2012-04-03 Jeffrey Altman    (7031) Windows: optimize InitCallback3 processing
    2012-04-03 Jeffrey Altman    (7030) Windows: Record callback issued time
    2012-04-03 Jeffrey Altman    (7029) Windows: Implement cm_TGTLifeTime()
    2012-04-03 Jeffrey Altman    (7028) Windows: add parent FID to cm_GetSCache
    2012-04-03 Jeffrey Altman    (7027) viced: AFSDisk, AFSFetchVolumeStatus Int31 PartSize
    2012-04-03 Jeffrey Altman    (7026) rx: handle clock reversals for call timeouts
    2012-03-30 Jeffrey Altman    (6990) Windows: avoid deadlock with Trend Micro
    2012-03-30 Jeffrey Altman    (6989) Windows: Use ulFilter in AFSInvalidateObject
    2012-03-29 Jeffrey Altman    (6984) Windows: ObjectInformation.ObjectReferenceCount comparison
    2012-03-29 Jeffrey Altman    (6981) windows: ObjectInformationCB.ObjectReferenceCount
    2012-03-29 Jeffrey Altman    (6982) Windows: AFSInvalidateObject can overwrite input param
    2012-03-29 Jeffrey Altman    (6983) Windows: Add Name Array Processing Trace Subsystem
    2012-03-28 Jeffrey Altman    (6977) Windows: CreateProcessNotify verify changes
    2012-03-28 Jeffrey Altman    (6976) Windows: Fix VNOSERVICE EventLog parameters
    2012-03-25 Jeffrey Altman    (6956) Windows: Assign AuthGroup during Process Create
    2012-03-25 Jeffrey Altman    (6955) Windows: Refactor AFSProcessSupport
    2012-03-25 Jeffrey Altman    (6953) doc: correct implicit ACL permissions volume owner
    2012-03-22 Jeffrey Altman    (6942) Windows: AFSRedir Debug for STATUS_NOT_A_DIRECTORY
    2012-03-22 Jeffrey Altman    (6939) Windows: Client handling of VNOSERVICE
    2012-03-17 Jeffrey Altman    (6920) Windows: invalidate correct objects during dir verification
    2012-03-16 Jeffrey Altman    (6915) rx: hold call->lock across RXS_PreparePacket
    2012-03-15 Jeffrey Altman    (6906) Windows: 1.7.8 (1.7.0800) Version
    2012-03-15 Jeffrey Altman    (6905) Windows: Change log for 1.7.8
    2012-03-14 Jeffrey Altman    (6902) rxgen: fix to use rx accessor routines
    2012-03-14 Jeffrey Altman    (6901) Windows: Drop resource across AFSCleanupFcb
    2012-03-14 Jeffrey Altman    (6900) Windows: Wait for memory allocation if necessary
    2012-03-14 Jeffrey Altman    (6899) Windows: Correct Data Version change synchronization
    2012-03-04 Jeffrey Altman    (6867) Windows: add __try..__except
    2012-03-04 Jeffrey Altman    (6866) Windows: fix indentation
    2012-03-04 Jeffrey Altman    (6865) Windows: Avoid deadlock in invalidation path
    2012-03-01 Jeffrey Altman    (6850) Windows: Workaround Win7 SMB Reconnect Bug
    2012-02-26 Jeffrey Altman    (6837) Windows: Fix an ExtentResource trace message
    2012-02-26 Jeffrey Altman    (6836) Windows: cm_UpdateCell never applies to Freelance mode
    2012-02-26 Jeffrey Altman    (6835) Windows: Redirector opens must set a valid FsContext
    2012-02-26 Jeffrey Altman    (6834) Windows: remove AFSOpenRedirector from AFSRedirLib
    2012-02-26 Jeffrey Altman    (6833) Windows: do not bugcheck in AFSExAllocatePoolWithTag
    2012-02-26 Jeffrey Altman    (6832) Windows: Revert "AFSRedir DebugFlags Turn on BugCheck"
    2012-02-23 Jeffrey Altman    (6774) Windows: 1.7.7 Release Notes
    2012-02-23 Jeffrey Altman    (6773) Windows: version 1.7.7 (1.7.07000)
    2012-02-22 Jeffrey Altman    (6748) Windows: invalidate data version on link creation
    2012-02-22 Jeffrey Altman    (6746) Windows: AFSPerformObjectInvalidate hold ExtentsResource shared
    2012-02-22 Jeffrey Altman    (6745) Windows: fsLockCount not accurate
    2012-02-19 Jeffrey Altman    (6739) Windows: Dereg Lanman and Lsa reg values for afsredir
    2012-02-18 Jeffrey Altman    (6736) doc: replace hostnames with IETF example hostnames
    2012-02-18 Jeffrey Altman    (6735) Windows: Explorer Shell Set Unix Mode bits
    2012-02-18 Jeffrey Altman    (6732) Windows: remove unnecessary DirectoryEnumEvent
    2012-02-18 Jeffrey Altman    (6731) Windows: VolumeCB->ObjectInfoTree.TreeLock Deadlock
    2012-02-18 Jeffrey Altman    (6730) doc: refer to aklog instead of klog
    2012-02-15 Jeffrey Altman    (6720) Windows: disable afsdhook.dll reload by daemon
    2012-02-15 Jeffrey Altman    (6719) Windows: remove install9x rules
    2012-02-15 Jeffrey Altman    (6718) Windows: remove AFS_WIN95_ENV
    2012-02-15 Jeffrey Altman    (6717) Windows: add KTC_TOKEN_MUTEX_FAIL error code
    2012-02-15 Jeffrey Altman    (6716) Windows: avoid GetComputerNameW call for all ioctl
    2012-02-12 Jeffrey Altman    (6704) doc: fix AdminGuide
    2012-02-11 Jeffrey Altman    (6702) Windows: AFSRemoveFcb() cannot race
    2012-02-11 Jeffrey Altman    (6700) doc: add section on direct volume access
    2012-02-11 Jeffrey Altman    (6695) Windows: Perform rename to self check earlier
    2012-02-07 Jeffrey Altman    (6688) Windows: Version 1.7.6 (aka 1.7.0600)
    2012-02-07 Jeffrey Altman    (6687) Windows: 1.7.6 change log
    2012-02-07 Jeffrey Altman    (6686) Windows: Release Notes corrections
    2012-02-07 Jeffrey Altman    (6684) Windows: OpenAFS reparse points are surrogates
    2012-02-06 Jeffrey Altman    (6667) Windows: Avoid race during PIOCtl DirNode allocation
    2012-02-06 Jeffrey Altman    (6666) Windows: Hold Fcb references prior to service call
    2012-02-05 Jeffrey Altman    (6665) Windows: Do not build NSIS by default
    2012-02-05 Jeffrey Altman    (6663) Windows: Increase size of worker thread pools
    2012-02-05 Jeffrey Altman    (6662) Windows: Run Workers until empty task queue
    2012-02-04 Jeffrey Altman    (6659) Windows: add buf_InvalidateBuffers
    2012-02-04 Jeffrey Altman    (6658) Windows: fix cm_DirOpDelBuffer assert
    2012-02-04 Jeffrey Altman    (6657) Windows: buffer DV ranges do not work for directories
    2012-02-04 Jeffrey Altman    (6656) Windows: update btree debugging code
    2012-02-04 Jeffrey Altman    (6655) Windows: Do not open file if shutdown in progress
    2012-02-04 Jeffrey Altman    (6654) Windows: AFSRedir DebugFlags Turn on BugCheck
    2012-02-04 Jeffrey Altman    (6653) Windows: Improve AFSNotifyDelete
    2012-02-04 Jeffrey Altman    (6652) Windows: do not lower case direct volume references
    2012-01-29 Jeffrey Altman    (6635) Windows: Version 1.7.5 (1.7.0500)
    2012-01-29 Jeffrey Altman    (6634) Windows: change log for 1.7.5
    2012-01-29 Jeffrey Altman    (6633) man-pages: add fs_getverify and fs_setverify
    2012-01-29 Jeffrey Altman    (6631) Windows: do not panic if afsredir not ready during shutdown
    2012-01-29 Jeffrey Altman    (6625) Windows: Release Notes for 1.7.5
    2012-01-27 Jeffrey Altman    (6622) Windows: Stop the thundering herd
    2012-01-27 Jeffrey Altman    (6621) Windows: DriveSubstitution handle too small buffer
    2012-01-27 Jeffrey Altman    (6620) Windows: Invalidate all volumes at library init
    2012-01-27 Jeffrey Altman    (6619) Windows: Refactor and consolidate afsredir invalidation
    2012-01-23 Jeffrey Altman    (6608) Windows: make lock reader history debug only
    2012-01-23 Jeffrey Altman    (6607) Windows: store data verification mode
    2012-01-23 Jeffrey Altman    (6606) Windows: VIOC_GETUNIXMODE = smb_IoctlGetUnixMode
    2012-01-23 Jeffrey Altman    (6605) Windows: fix fs setcrypt help message
    2012-01-23 Jeffrey Altman    (6604) Windows; release BIOD after status merge
    2012-01-23 Jeffrey Altman    (6602) Revert "Windows: disable memory extent interface"
    2012-01-20 Jeffrey Altman    (6594) Windows: failover and retry for VBUSY
    2012-01-20 Jeffrey Altman    (6592) Windows: improved idle dead time handling
    2012-01-20 Jeffrey Altman    (6591) rx: RX_CALL_IDLE and RX_CALL_BUSY
    2012-01-20 Jeffrey Altman    (6590) Windows Asynchronous purging of file content after a DV change
    2012-01-20 Jeffrey Altman    (6589) Windows: cm_buf refcnt must hold buf_globalLock
    2012-01-20 Jeffrey Altman    (6588) Windows: Redesign daemon thread queue management
    2012-01-20 Jeffrey Altman    (6587) Windows: prevent race assigning Fcb in AFSInitFcb()
    2012-01-20 Jeffrey Altman    (6586) Windows: cm_EndCallbackGrantingCall refactoring
    2012-01-20 Jeffrey Altman    (6585) Windows: deadlock bet. DirEntry lock + DirectoryNodeHdr.TreeLock
    2012-01-20 Jeffrey Altman    (6584) Windows: Correctly mark extents dirty when using non-persistent AFS cache
    2012-01-20 Jeffrey Altman    (6583) Windows: Performing async work after cache invalidation
    2012-01-20 Jeffrey Altman    (6582) rx: Correctly test for end of call queue
    2012-01-20 Jeffrey Altman    (6581) Windows: disable memory extent interface
    2012-01-20 Jeffrey Altman    (6580) Windows: restrict service to 2 cpus by default
    2012-01-20 Jeffrey Altman    (6579) Windows: AFS_SERVER_FLUSH_DELAY AFS_SERVER_PURGE_DELAY
    2012-01-20 Jeffrey Altman    (6578) Windows: AFSParseName edge cases
    2012-01-20 Jeffrey Altman    (6577) Windows: afs root is always a directory
    2012-01-12 Jeffrey Altman    (6544) rx: add and export a public keepalive toggle
    2012-01-12 Jeffrey Altman    (6542) Windows: dir buffers out of date - mark them as such
    2012-01-12 Jeffrey Altman    (6541) Windows: Avoid file server rpcs on deleted files
    2012-01-12 Jeffrey Altman    (6540) Windows: use local var for interlocked result
    2012-01-12 Jeffrey Altman    (6539) Windows: AFSParseMountPointTarget buffer overrun
    2012-01-12 Jeffrey Altman    (6538) Windows: Directory Enumeration, DVs, and TreeLocks
    2012-01-12 Jeffrey Altman    (6537) Windows: correct log messages in AFSCleanup
    2012-01-12 Jeffrey Altman    (6536) Windows: Return Dir Data Version from AFSCleanup
    2012-01-12 Jeffrey Altman    (6535) Windows: reorg open handle counts and Fcb->NPFcb->Resource
    2012-01-12 Jeffrey Altman    (6534) Windows: Permit renames of open files
    2012-01-12 Jeffrey Altman    (6533) Windows: Do not prime the service directory cache
    2012-01-12 Jeffrey Altman    (6532) Windows: More specific error values
    2012-01-12 Jeffrey Altman    (6531) Windows: do not flush dirty extents without permission
    2012-01-04 Jeffrey Altman    (6490) Windows: Support correct status codes from service
    2012-01-04 Jeffrey Altman    (6489) Windows: Handle invalid node types
    2012-01-04 Jeffrey Altman    (6488) Windows: AFSFileUpdateResultCB ParentDataVersion
    2012-01-04 Jeffrey Altman    (6487) Windows: renames that overwrite existing target
    2012-01-04 Jeffrey Altman    (6486) Windows: AFSDirEnumResp and AFSDirEnumEntry changes
    2012-01-04 Jeffrey Altman    (6485) Windows: Add AFSFileEvalResultCB
    2012-01-04 Jeffrey Altman    (6484) Windows: Add AFSFileCleanupResultCB
    2012-01-04 Jeffrey Altman    (6483) Windows: STATUS_OBJECT_PATH_INVALID == invalid parent directory
    2012-01-04 Jeffrey Altman    (6482) Windows: Request extents readability
    2012-01-04 Jeffrey Altman    (6481) Windows: RequestExtents avoid bufWrite if rdr held
    2012-01-04 Jeffrey Altman    (6480) Windows: avoid race during Fcb cleanup
    2012-01-04 Jeffrey Altman    (6479) Windows: avoid deadlock if bulk error during enum
    2012-01-04 Jeffrey Altman    (6478) Windows: AFSInsertHashEntry can fail
    2012-01-04 Jeffrey Altman    (6477) Windows: additional AFSValidateEntry logging
    2012-01-04 Jeffrey Altman    (6476) Windows: add DV and error status to dir enumerations
    2012-01-04 Jeffrey Altman    (6475) Windows: protect merge status against dscp == scp
    2012-01-04 Jeffrey Altman    (6474) Windows: protect dir ops by CM_SCACHESYNC_STOREDATA
    2012-01-04 Jeffrey Altman    (6473) Windows: init scache DV=CM_SCACHE_VERSION_BAD
    2012-01-04 Jeffrey Altman    (6472) Windows: afsredirlib log messages
    2012-01-04 Jeffrey Altman    (6471) Windows: Symlink resolve failure error
    2012-01-04 Jeffrey Altman    (6470) Windows: Make idle dead timeout very long
    2012-01-04 Jeffrey Altman    (6469) Windows: replace strdup with xdr_alloc in callback processing
    2012-01-04 Jeffrey Altman    (6468) windows: osi_TSignalForMLs simplify
    2012-01-04 Jeffrey Altman    (6467) Windows: osisleep do not tamper with queues
    2012-01-04 Jeffrey Altman    (6466) Windows: osi_sleepInfo tid type
    2012-01-04 Jeffrey Altman    (6465) Windows: add osi_TWaitExt(), fix osi_TWait()
    2012-01-04 Jeffrey Altman    (6464) Windows: use waiters counter instead of osi_TEmpty
    2012-01-04 Jeffrey Altman    (6463) Windows: kauth search for kerberos iv port first
    2011-12-25 Jeffrey Altman    (6429) Windows: Avoid bottleneck on VolumeLock
    2011-12-25 Jeffrey Altman    (6428) Windows: avoid race in cm_GetNewSCache
    2011-12-25 Jeffrey Altman    (6427) Windows: cm_BufWrite() must wait in cm_SyncOp()
    2011-12-25 Jeffrey Altman    (6426) rx: Don't adjust non-existent events
    2011-12-22 Jeffrey Altman    (6409) Windows: AFSCleanup extent processing
    2011-12-22 Jeffrey Altman    (6408) Windows: AFSRetrieveValidAuthGroup FILE_READ_DATA
    2011-12-22 Jeffrey Altman    (6407) Windows: AFSRequestExtentsAsync retry with alt authgroup
    2011-12-22 Jeffrey Altman    (6406) Windows: Use AuthGroups for extent request error reporting
    2011-12-22 Jeffrey Altman    (6405) Windows: Explicit permission check on extent release
    2011-12-22 Jeffrey Altman    (6404) Windows: RDR_CleanupFileEntry restrict extent claw back
    2011-12-22 Jeffrey Altman    (6403) Windows: remove unused AFSRequestExtents()
    2011-12-22 Jeffrey Altman    (6402) Windows: Bad DV invalidate only when new DV not 0
    2011-12-22 Jeffrey Altman    (6401) Windows: Define times in terms of AFS_ONE_SECOND
    2011-12-19 Jeffrey Altman    (6381) Windows: version 1.7.4
    2011-12-19 Jeffrey Altman    (6380) Windows: ChangeLog for 1.7.4
    2011-12-19 Jeffrey Altman    (6379) Windows: avoid deadlock during SetRenameInformation
    2011-12-19 Jeffrey Altman    (6378) Windows: terminate HOSTS/LMHOSTS with newline
    2011-12-18 Jeffrey Altman    (6374) Windows: Track AuthGroup in Context Control Block
    2011-12-18 Jeffrey Altman    (6366) Windows: save fid/type for redirector invalidation
    2011-12-18 Jeffrey Altman    (6373) Windows: Tear down extents upon file deletion
    2011-12-18 Jeffrey Altman    (6372) Windows: notify file size change if flushed
    2011-12-18 Jeffrey Altman    (6371) Windows: forget data version only for flushing
    2011-12-18 Jeffrey Altman    (6370) Windows: fix indentation
    2011-12-18 Jeffrey Altman    (6369) Windows: AFSSetRenameInfo log message
    2011-12-18 Jeffrey Altman    (6368) Windows: return error to system paging requests
    2011-12-18 Jeffrey Altman    (6367) Windows: log volume and authgroup for redir open
    2011-12-17 Jeffrey Altman    (6357) Windows: move to head of queue no-op if not in queue
    2011-12-17 Jeffrey Altman    (6356) Windows: Properly convert FID structures
    2011-12-17 Jeffrey Altman    (6355) Windows: propagate directory enumeration failures
    2011-12-17 Jeffrey Altman    (6354) Windows Problem with cross-directory rename
    2011-12-17 Jeffrey Altman    (6353) Windows: Update Adv Firewall Rules
    2011-12-14 Jeffrey Altman    (6258) Windows: AFSRDFSProvider stack overrun
    2011-12-10 Jeffrey Altman    (6246) Windows: memory leak when setting tokens via smb
    2011-12-10 Jeffrey Altman    (6245) Windows: Suspend/Resume for afsd_service
    2011-12-08 Jeffrey Altman    (6239) Windows: increase timeout for extent request retries
    2011-12-08 Jeffrey Altman    (6238) Windows: include owner/group in Security DACL
    2011-12-04 Jeffrey Altman    (6226) Windows: version 1.7.3 (1.7.0300)
    2011-12-04 Jeffrey Altman    (6225) Windows: Release Notes Updates
    2011-12-04 Jeffrey Altman    (6224) windows: 1.7.3 change log
    2011-12-04 Jeffrey Altman    (6221) rx: Make CALL_RELE and CALL_HOLD lock refcnt mutex
    2011-12-04 Jeffrey Altman    (6220) rx: Helper function for decrementing conn refcnt
    2011-12-04 Jeffrey Altman    (6217) rx: Hide the rx_packet.h
    2011-12-04 Jeffrey Altman    (6216) Windows: define MIN and MAX
    2011-12-04 Jeffrey Altman    (6215) rx: Make the rx_call structure private
    2011-12-04 Jeffrey Altman    (6214) rx: Make struct rx_connection private
    2011-12-04 Jeffrey Altman    (6213) Windows: apply Nat Pings only to cm_rootUser connections
    2011-12-04 Jeffrey Altman    (6212) Windows: track cm_rootUser connections
    2011-12-04 Jeffrey Altman    (6211) rx: rx_conn/rx_peer refCount signed
    2011-12-04 Jeffrey Altman    (6210) rx: Some kernels have no reschedule function
    2011-12-03 Jeffrey Altman    (6202) Windows: npdll connected query returns no usage
    2011-12-03 Jeffrey Altman    (6201) Windows: Use roken's min and max
    2011-12-03 Jeffrey Altman    (6200) rx: Refactor MaxMTU error checking
    2011-12-03 Jeffrey Altman    (6192) Windows: GetInfoTip really set return to NULL
    2011-12-03 Jeffrey Altman    (6191) Windows: memset in RDR_RequestFileExtentsAsync
    2011-12-03 Jeffrey Altman    (6190) Windows: cm_MergeStatus redirector invalidation
    2011-12-03 Jeffrey Altman    (6189) Windows: cm_MergeStatus use new DV to purge buffers
    2011-12-03 Jeffrey Altman    (6188) Windows: use interlocked increment on cm_buf_t refcnt
    2011-12-03 Jeffrey Altman    (6187) Windows: buf_GetNewLocked should use cleaned cm_buf
    2011-12-03 Jeffrey Altman    (6186) Windows: fix buf_Recycle() comment
    2011-12-03 Jeffrey Altman    (6185) Windows: buf_CleanAsync is not async; rename it
    2011-12-03 Jeffrey Altman    (6184) Windows: convert buf_IncrSyncer to pthreads
    2011-12-01 Jeffrey Altman    (6170) Windows: invalidate rdr for CM_SCACHE_VERSION_BAD
    2011-12-01 Jeffrey Altman    (6169) Windows: do not set CM_SCACHEFLAG_EACCES twice
    2011-11-30 Jeffrey Altman    (6156) Windows: AFSRDFSProvider log to file
    2011-11-30 Jeffrey Altman    (6155) Windows: NPEnumResources no Printer support
    2011-11-30 Jeffrey Altman    (6154) Windows: NPGetConnectionCommon buffer too small
    2011-11-30 Jeffrey Altman    (6153) Windows: no drive subst for NPCancelConnection
    2011-11-30 Jeffrey Altman    (6152) Windows: refactor NPCancelConnection
    2011-11-30 Jeffrey Altman    (6151) Windows: Mount Point and Symlink Overlay Icons
    2011-11-30 Jeffrey Altman    (6150) Windows: Wix disable integrated logon by default
    2011-11-30 Jeffrey Altman    (6149) rx: Use a red black tree for the event stack
    2011-11-30 Jeffrey Altman    (6148) Unix CM: Build rbtrees in kernel
    2011-11-30 Jeffrey Altman    (6147) udebug: Fix endianness when fudging lastYesHost
    2011-11-30 Jeffrey Altman    (6146) Windows: FSync not CleanVnode during Cleanup
    2011-11-30 Jeffrey Altman    (6145) Windows: Wix cell names can be greater than 120 chars
    2011-11-30 Jeffrey Altman    (6144) Windows: cache format version change
    2011-11-30 Jeffrey Altman    (6143) Windows: osi_mutex / osi_rwlock changes
    2011-11-28 Jeffrey Altman    (6129) Windows: convert daemons threads to pthreads
    2011-11-23 Jeffrey Altman    (6115) Windows: add trace logging to Pioctl File Info Query
    2011-11-23 Jeffrey Altman    (6114) Windows: _._AFS_IOCTL_._ size is zero
    2011-11-23 Jeffrey Altman    (6113) Windows: RDR_InvalidateObject do not hold locks
    2011-11-23 Jeffrey Altman    (6112) Windows: cm_GetSCache do not release unheld lock
    2011-11-23 Jeffrey Altman    (6111) Windows: Use Jenkins' Hash
    2011-11-23 Jeffrey Altman    (6107) auth: avoid excessive stat of cellservdb
    2011-11-23 Jeffrey Altman    (6106) opr: Add Bob Jenkins's hash functions
    2011-11-18 Jeffrey Altman    (6077) Windows: Version 1.7.2a (1.7.0201)
    2011-11-18 Jeffrey Altman    (6076) Windows: RDR_RequestFileExtentsAsync unheld lock
    2011-11-18 Jeffrey Altman    (6074) Windows: must obtain and release an actual lock
    2011-11-18 Jeffrey Altman    (6073) Windows: non-release only worker threads can release
    2011-11-16 Jeffrey Altman    (6070) Windows: Version 1.7.2 (1.7.0200)
    2011-11-16 Jeffrey Altman    (6069) Windows: 1.7.2 Change Log
    2011-11-16 Jeffrey Altman    (6068) auth: initKeys before first error exit path
    2011-11-16 Jeffrey Altman    (6066) Windows: Do not install IBM AFS HLP files
    2011-11-16 Jeffrey Altman    (6064) Windows: buf_CleanAsyncLocked dirty range only
    2011-11-16 Jeffrey Altman    (6063) Windows: create scache->redirMx to reduce contention
    2011-11-16 Jeffrey Altman    (6062) Windows: Increase default number of daemon threads
    2011-11-16 Jeffrey Altman    (6061) Windows: cm_SetupStoreBIOD use firstModOffset chunk
    2011-11-16 Jeffrey Altman    (6060) Windows: Fairness for background operations
    2011-11-15 Jeffrey Altman    (6049) Windows: Create default Security Descriptor
    2011-11-15 Jeffrey Altman    (6047) Windows: interlocked refCount increment in cm_GetSCache
    2011-11-14 Jeffrey Altman    (6018) Windows: netidmgr krb5_cc_get_principal can fail
    2011-11-14 Jeffrey Altman    (6017) Windows: missing braces in AFSFSControl
    2011-11-13 Jeffrey Altman    (6015) Windows: smb_ReceiveNTCreateX create smb_fid earlier
    2011-11-13 Jeffrey Altman    (6014) Windows: cm_GetSCache avoid holding cm_scacheLock
    2011-11-13 Jeffrey Altman    (6013) Windows: avoid null ptr in RDR_RequestFileExtentsAsync
    2011-11-13 Jeffrey Altman    (6012) Windows: Track active RPCs per scache_t
    2011-11-13 Jeffrey Altman    (6011) Windows: fix locking hierarchy in service
    2011-11-13 Jeffrey Altman    (6010) afs: Do not use separate array for srvAddrs
    2011-11-13 Jeffrey Altman    (6009) rx: Turn the rxevent_Cancel macro into a function
    2011-11-13 Jeffrey Altman    (6008) rx: New signature for rx event functions
    2011-11-13 Jeffrey Altman    (6007) opr: Add a red/black tree implementation
    2011-11-13 Jeffrey Altman    (6006) rx: Add a helper function for delayed acks
    2011-11-13 Jeffrey Altman    (6005) opr: Add opr_containerof
    2011-11-13 Jeffrey Altman    (5999) Windows: add braces to case statements
    2011-11-13 Jeffrey Altman    (5998) Windows: Add Vista/Win7 Firewall Configuration
    2011-11-13 Jeffrey Altman    (5997) Windows: Enforce Share Access
    2011-11-13 Jeffrey Altman    (5996) namei: Remove extraneous rmdir
    2011-11-13 Jeffrey Altman    (5995) vol: Remove O_EXCL|O_TRUNC combinations
    2011-11-13 Jeffrey Altman    (5994) Windows: FSCTL_SET_REPARSE_POINT not yet implemented
    2011-11-13 Jeffrey Altman    (5993) Windows: FSCTL_SET_REPARSE_POINT error
    2011-11-13 Jeffrey Altman    (5992) Windows: FSCTL_IS_PATHNAME_VALID return success
    2011-11-13 Jeffrey Altman    (5991) Windows: these fsctl cmds are not implemented
    2011-11-13 Jeffrey Altman    (5990) Windows: Additional trace logging
    2011-11-13 Jeffrey Altman    (5989) Windows: service must set reparse point attribute
    2011-11-13 Jeffrey Altman    (5988) Windows: Correctly increment PIOCtl DE
    2011-11-13 Jeffrey Altman    (5987) Windows: FileNetworkPhysicalNameInfo implementation
    2011-11-13 Jeffrey Altman    (5986) Windows: improve store data parallelism
    2011-11-13 Jeffrey Altman    (5985) volser: Preserve needsSalvaged during restore
    2011-11-13 Jeffrey Altman    (5984) viced: avoid bogus handle in rename
    2011-11-13 Jeffrey Altman    (5983) regen: Fail on failures
    2011-11-13 Jeffrey Altman    (5982) Add "pretty" build option
    2011-11-13 Jeffrey Altman    (5981) Specify pattern rules in addition to suffix rules
    2011-11-13 Jeffrey Altman    (5980) Add setenv/unsetenv to roken
    2011-11-13 Jeffrey Altman    (5979) dafs: avoid null deref getting volume header
    2011-11-13 Jeffrey Altman    (5978) salvager: Implement AskDAFS via SYNC flags
    2011-11-13 Jeffrey Altman    (5977) ukernel: handle pioctl errors properly in ktc
    2011-11-13 Jeffrey Altman    (5976) libafsauthent: Remove obsolete HP-UX workaround
    2011-11-13 Jeffrey Altman    (5975) volser: Remove debugging log messages
    2011-11-13 Jeffrey Altman    (5974) Unix CM: Fix dir buffer leak in afs_readdir
    2011-11-13 Jeffrey Altman    (5973) DAFS: Deal with exclusive-state volume headers
    2011-11-13 Jeffrey Altman    (5972) Windows: NPCancelConnection set correct length
    2011-11-13 Jeffrey Altman    (5971) Windows: do not leak resource in AFSQueryDirectory
    2011-11-13 Jeffrey Altman    (5970) Windows: Failed to release correct lock
    2011-11-13 Jeffrey Altman    (5969) doc: limitations of addsite on different partitions
    2011-11-13 Jeffrey Altman    (5968) Import of code from heimdal
    2011-11-13 Jeffrey Altman    (5967) Solaris: Specify ARCHFLAGS in CFLAGS
    2011-11-13 Jeffrey Altman    (5966) Do OPENAFS_OSCONF before compiler autoconf tests
    2011-11-13 Jeffrey Altman    (5965) Remove -settime/RXAFS_GetTime client support
    2011-11-13 Jeffrey Altman    (5964) opr: queue swap
    2011-11-13 Jeffrey Altman    (5963) external: trigger git commit-msg hooks on import
    2011-11-13 Jeffrey Altman    (5962) external: commit imports with --no-verify
    2011-11-13 Jeffrey Altman    (5961) Import setenv.c and unsetenv.c from roken
    2011-11-13 Jeffrey Altman    (5960) Windows: fix deadlock in symlink Attrib retrieval
    2011-11-13 Jeffrey Altman    (5959) Windows: always set reparse point attrib for symlink
    2011-11-13 Jeffrey Altman    (5958) Windows: remember when a reparse point is opened
    2011-11-13 Jeffrey Altman    (5957) Windows: Mount points are always directories
    2011-11-13 Jeffrey Altman    (5956) Windows: Retrieve file attributes on symlinks
    2011-11-13 Jeffrey Altman    (5955) Windows: add AFSRetrieveParentPath()
    2011-11-13 Jeffrey Altman    (5954) kdump-build: don't install when it hasn't been built for *bsd*
    2011-11-13 Jeffrey Altman    (5953) klog.krb5: enforce DES for rxkad
    2011-11-13 Jeffrey Altman    (5952) Windows: DE Reference count added during create
    2011-11-13 Jeffrey Altman    (5951) Windows: change AFSProcessUserFsRequest default
    2011-11-13 Jeffrey Altman    (5950) Windows: correct ordering of reparse point tests
    2011-11-13 Jeffrey Altman    (5949) Windows: log FSCTL_CSC_INTERNAL requests
    2011-11-13 Jeffrey Altman    (5948) Windows: Directory Entry Processing
    2011-11-13 Jeffrey Altman    (5947) Windows: additional trace logging for afsredirlib
    2011-11-13 Jeffrey Altman    (5946) Windows: Reimplement AFSGenerateCRC()
    2011-11-13 Jeffrey Altman    (5945) Linux: 3.1: update RCU path walking detection in permission i_op
    2011-11-13 Jeffrey Altman    (5944) rx: Remove the ADAPT_WINDOW code
    2011-11-13 Jeffrey Altman    (5943) Windows: cm_Rename break in 9cf7a628c2ff178b2fa236d2c0a41ca9be315036
    2011-11-13 Jeffrey Altman    (5942) Windows: out of date version not in current chunk
    2011-11-13 Jeffrey Altman    (5941) Windows: only flush buffers on shutdown if running
    2011-11-13 Jeffrey Altman    (5940) Windows: Do not EEXIST exact match during rename
    2011-11-13 Jeffrey Altman    (5939) opr: build on Windows after queue.h move
    2011-11-13 Jeffrey Altman    (5938) Windows: Look for 8.3 name when doing a rename
    2011-11-12 Jeffrey Altman    (5937) Windows: New Trace for DirEntry tracking problem
    2011-11-12 Jeffrey Altman    (5936) Windows: Free work item memory with tag value
    2011-11-12 Jeffrey Altman    (5935) Windows: free pointer after last reference
    2011-11-12 Jeffrey Altman    (5934) Windows: AFSInitPIOCtlDirectoryCB free in try_exit
    2011-11-12 Jeffrey Altman    (5933) Windows: close leak in AFSPrimaryVolumeWorkerThread
    2011-11-12 Jeffrey Altman    (5932) Windows: afsredir only wants shortName if not 8.3
    2011-11-12 Jeffrey Altman    (5931) Windows: Use SetFlag macro when setting flag
    2011-11-12 Jeffrey Altman    (5930) Windows: minor typo in trace output
    2011-11-12 Jeffrey Altman    (5929) Windows: AFSRemoveCaseInsensitiveDirEntry corrections
    2011-11-12 Jeffrey Altman    (5928) Windows: AFSEvaluateTargetByName free buffer if no return
    2011-11-12 Jeffrey Altman    (5927) Windows: remove unused code block
    2011-11-12 Jeffrey Altman    (5926) Windows: re-indent afsredir log message params
    2011-11-12 Jeffrey Altman    (5925) Windows:  Defer deref of a directoryEntry
    2011-11-12 Jeffrey Altman    (5924) Windows: Set new file index correctly during rename
    2011-11-12 Jeffrey Altman    (5923) allow cloning of any volume to any volume with same parent ID
    2011-11-12 Jeffrey Altman    (5922) remove check for disallowing clones of backup or ro volumes
    2011-11-12 Jeffrey Altman    (5921) bozo: build notifier sample program
    2011-11-12 Jeffrey Altman    (5920) bozo: test program update
    2011-11-12 Jeffrey Altman    (5919) DAFS: Remove VOL_SALVAGE_INVALIDATE_HEADER
    2011-11-12 Jeffrey Altman    (5918) DAFS: fssync online requires a partition name argument
    2011-11-12 Jeffrey Altman    (5917) volser: Remove ExtractVolId
    2011-11-12 Jeffrey Altman    (5916) viced: Check for HOSTDELETED in stillborn check
    2011-11-12 Jeffrey Altman    (5915) vlserver: Log to VLLog by default, not PtLog
    2011-11-12 Jeffrey Altman    (5914) vos offline: Bring volume back online for -busy
    2011-11-12 Jeffrey Altman    (5913) cache bypass: don't define iovecp for UKERNEL
    2011-11-12 Jeffrey Altman    (5912) Windows: Remove unused cleanup flag
    2011-11-12 Jeffrey Altman    (5911) bypasscache: allow arbitrary sized iovecs
    2011-11-12 Jeffrey Altman    (5910) bypasscache: do errors correctly
    2011-11-12 Jeffrey Altman    (5909) ukernel: get an ip address even when dns and hosts suck
    2011-11-12 Jeffrey Altman    (5908) dir: add missing return in DRead
    2011-11-12 Jeffrey Altman    (5907) tests: volser doesn't need rxgk yet
    2011-11-12 Jeffrey Altman    (5906) tests: Add opr library for ktime test
    2011-11-12 Jeffrey Altman    (5905) roken: Add *progname() to shared library exports
    2011-11-12 Jeffrey Altman    (5904) rx: Define afs_kmutex_t for LWP too
    2011-11-12 Jeffrey Altman    (5903) dir: Don't leak a buffer on a failed Enumerate
    2011-11-12 Jeffrey Altman    (5902) LINUX: Fix afs_linux_pag_to_groups signature
    2011-11-12 Jeffrey Altman    (5901) LINUX: Revert group changes on keyring failure
    2011-11-12 Jeffrey Altman    (5900) viced: Do not swallow errors on StoreData recovery
    2011-11-12 Jeffrey Altman    (5899) opr: Move queue header out of util
    2011-11-12 Jeffrey Altman    (5898) dir: Remove double release in FindBlobs
    2011-11-12 Jeffrey Altman    (5897) afs: don't try GetDownD if nothing to get
    2011-11-12 Jeffrey Altman    (5896) ukernel: don't define rdwr env on linux
    2011-11-12 Jeffrey Altman    (5895) ukernel: set pthread stacksize to an integer multiple of 8k
    2011-11-12 Jeffrey Altman    (5894) ukernel: add morepackets check in listener
    2011-11-12 Jeffrey Altman    (5893) afs: on uuid init fail, don't leave garbage behind
    2011-11-12 Jeffrey Altman    (5892) ukernel: set close-on-exec on our socket
    2011-11-12 Jeffrey Altman    (5891) auth: Get correct viceid in legacy GetToken
    2011-11-12 Jeffrey Altman    (5890) auth: Force correct evenness on rxkad tokens
    2011-11-12 Jeffrey Altman    (5889) docs: Refer to dafs binaries by their real names
    2011-11-12 Jeffrey Altman    (5888) ptserver: Don't check for noauth before rebuilding
    2011-11-12 Jeffrey Altman    (5887) Windows AFSRDR: Log before decrementing refcount
    2011-11-12 Jeffrey Altman    (5886) ukernel: don't enforce thread lockers in remove vop
    2011-11-12 Jeffrey Altman    (5885) ukernel: install our sysincludes to root.perf
    2011-11-12 Jeffrey Altman    (5884) ukernel: add uafs_access
    2011-11-12 Jeffrey Altman    (5883) volinfo: fix bad format string
    2011-11-12 Jeffrey Altman    (5882) vol_split: avoid using stale open directory vnodes
    2011-11-12 Jeffrey Altman    (5881) bozo: bosserver man page updates
    2011-11-12 Jeffrey Altman    (5880) bypasscache: free in order
    2011-11-12 Jeffrey Altman    (5879) doc: fileserver synopsis typo
    2011-11-12 Jeffrey Altman    (5878) bypasscache for ukernel
    2011-11-12 Jeffrey Altman    (5877) aklog_dynamic_auth: Support new SetToken pioctl
    2011-11-12 Jeffrey Altman    (5876) Remove a few extra trailing backslashes
    2011-11-12 Jeffrey Altman    (5875) vol: Only check "logging" on vice partitions
    2011-11-12 Jeffrey Altman    (5874) FSSYNC-Client:  Consistent use of partition name
    2011-11-12 Jeffrey Altman    (5873) DAFS: Do not serialize state for invalid hosts
    2011-11-12 Jeffrey Altman    (5872) DAFS: Skip hosts with invalid flags on restore
    2011-11-12 Jeffrey Altman    (5871) DAFS: Add explicit 'valid' field for index maps
    2011-11-12 Jeffrey Altman    (5870) viced: Assert valid statistics indices
    2011-11-12 Jeffrey Altman    (5869) viced: Use xfer indices for xfer data
    2011-11-12 Jeffrey Altman    (5868) rx: add post RPC procedure capability
    2011-11-12 Jeffrey Altman    (5867) viced: remove duplicate declaration
    2011-11-12 Jeffrey Altman    (5866) Windows: Remove spurious use of CRTL
    2011-11-12 Jeffrey Altman    (5865) Remove references to afs_assert.h
    2011-11-12 Jeffrey Altman    (5864) ukernel: output dataversion in stat struct if possible
    2011-11-12 Jeffrey Altman    (5863) ukernel: make web enhancements the default
    2011-11-12 Jeffrey Altman    (5862) Windows: Fix comment about DiskPartition64
    2011-11-12 Jeffrey Altman    (5861) bozo: report bosserver -rxbind address
    2011-11-12 Jeffrey Altman    (5860) Windows: do not install afs_assert.h
    2011-11-12 Jeffrey Altman    (5859) bozo: fix overrun from -rxbind on restart
    2011-11-12 Jeffrey Altman    (5858) volinfo: refactor vnode handling
    2011-11-12 Jeffrey Altman    (5857) volinfo: release volume header ihandles when done
    2011-11-12 Jeffrey Altman    (5856) Clean up assertion
    2011-11-12 Jeffrey Altman    (5855) Move abort() into opr
    2011-11-12 Jeffrey Altman    (5854) bozo: bosserver -pidfiles option
    2011-11-12 Jeffrey Altman    (5853) bozo: remove duplicate prototype
    2011-11-12 Jeffrey Altman    (5852) Fix buffer leak in dir/buffers.c
    2011-11-12 Jeffrey Altman    (5851) viced: fix incorrect error message
    2011-11-12 Jeffrey Altman    (5850) bozo: pass -rxbind on restart
    2011-11-12 Jeffrey Altman    (5849) salvager: fix filesystem path truncation
    2011-11-12 Jeffrey Altman    (5848) ntohs ubik header size
    2011-11-12 Jeffrey Altman    (5847) dir: remove unnecessary cast from malloc
    2011-11-12 Jeffrey Altman    (5846) rx: arrange for Finalize to really stop running calls
    2011-11-11 Jeffrey Altman    (5845) rx: Don't clear the receive queue when out of packets
    2011-11-11 Jeffrey Altman    (5844) rx: ackall handling



### Patches merged into the stable 1.6.x branch

    Date       Committer        Change# Description
    2012-04-04 Andrew Deason     (7045) SOLARIS: Correct misplaced osi_machdep.h #endif
    2012-04-03 Jeffrey Altman    (7023) viced: AFSDisk, AFSFetchVolumeStatus Int31 PartSize
    2012-03-28 Jeffrey Altman    (6974) Windows: Fix VNOSERVICE EventLog parameters
    2012-03-27 Derrick Brashear  (6972) macos: iterate mdfound packagemakers when spaces are present
    2012-03-27 Derrick Brashear  (6968) macos: find packagemaker instead of assuming path
    2012-03-26 Derrick Brashear  (6965) osx: deal with more kerberos damage
    2012-03-26 Derrick Brashear  (6957) viced: Do not ignore all InlineBulkStatus errors
    2012-03-25 Jeffrey Altman    (6952) doc: correct implicit ACL permissions volume owner
    2012-03-22 Jeffrey Altman    (6940) Windows: Client handling of VNOSERVICE
    2012-03-22 Derrick Brashear  (6932) Linux 3.4: Switch to d_make_root
    2012-03-21 Andrew Deason     (6918) LINUX: Use afs_convert_code in afs_notify_change
    2012-03-21 Andrew Deason     (6917) LINUX: move afs_notify_change to osi_vnodeops.c
    2012-03-16 Derrick Brashear  (6910) afs: Never #define away afsd_dynamic_vcaches
    2012-03-16 Derrick Brashear  (6909) rx: hold call->lock across RXS_PreparePacket
    2012-03-15 Jonathan Billings (6889) redhat: Don't replace modified configuration files during rpm update
    2012-03-12 Jeffrey Altman    (6891) viced: fix inverted lockCount assignment
    2012-03-04 Jeffrey Altman    (6872) Windows: 1.6.1pre4 change log
    2012-03-04 Derrick Brashear  (6870) macos: don't crash on krb5 damage
    2012-03-03 Derrick Brashear  (6862) Fixes dkms.conf for Redhat Enterprise
    2012-03-02 Jeffrey Altman    (6853) unix: always retry RX_CALL_BUSY
    2012-03-01 Jeffrey Altman    (6848) Windows: Workaround Win7 SMB Reconnect Bug
    2012-02-26 Jeffrey Altman    (6841) Windows: disable Adv ICF support if not supported
    2012-02-26 Jeffrey Altman    (6838) Windows: ChangeLog for 1.6.1pre3
    2012-02-26 Jeffrey Altman    (6831) Windows: failover and retry for VBUSY
    2012-02-26 Jeffrey Altman    (6830) Windows: improved idle dead time handling
    2012-02-26 Jeffrey Altman    (6829) Windows: cm_UpdateCell never applies to Freelance mode
    2012-02-26 Jeffrey Altman    (6828) Windows: fix cm_DirOpDelBuffer assert
    2012-02-26 Jeffrey Altman    (6827) Windows: buffer DV ranges do not work for directories
    2012-02-26 Jeffrey Altman    (6826) Windows: VIOC_GETUNIXMODE = smb_IoctlGetUnixMode
    2012-02-26 Jeffrey Altman    (6825) Windows: fix fs setcrypt help message
    2012-02-26 Jeffrey Altman    (6824) Windows; release BIOD after status merge
    2012-02-26 Jeffrey Altman    (6823) Windows: cm_buf refcnt must hold buf_globalLock
    2012-02-26 Jeffrey Altman    (6822) Windows: restrict service to 2 cpus by default
    2012-02-26 Jeffrey Altman    (6821) Windows: dir buffers out of date - mark them as such
    2012-02-26 Jeffrey Altman    (6820) Windows: replace strdup with xdr_alloc in callback processing
    2012-02-26 Jeffrey Altman    (6819) Windows: kauth search for kerberos iv port first
    2012-02-26 Jeffrey Altman    (6818) Windows: cm_BufWrite() must wait in cm_SyncOp()
    2012-02-26 Jeffrey Altman    (6817) Windows: terminate HOSTS/LMHOSTS with newline
    2012-02-26 Jeffrey Altman    (6816) Windows: Update Adv Firewall Rules
    2012-02-26 Jeffrey Altman    (6815) Windows: memory leak when setting tokens via smb
    2012-02-26 Jeffrey Altman    (6814) Windows: apply Nat Pings only to cm_rootUser connections
    2012-02-26 Jeffrey Altman    (6813) Windows: track cm_rootUser connections
    2012-02-26 Jeffrey Altman    (6812) Windows: fix buf_Recycle() comment
    2012-02-26 Jeffrey Altman    (6811) Windows: buf_CleanAsync is not async; rename it
    2012-02-26 Jeffrey Altman    (6810) Windows: Wix cell names can be greater than 120 chars
    2012-02-26 Jeffrey Altman    (6809) Windows: cm_GetSCache do not release unheld lock
    2012-02-26 Jeffrey Altman    (6808) Windows: buf_CleanAsyncLocked dirty range only
    2012-02-26 Jeffrey Altman    (6807) Windows: cm_SetupStoreBIOD use firstModOffset chunk
    2012-02-26 Jeffrey Altman    (6806) Windows: smb_ReceiveNTCreateX create smb_fid earlier
    2012-02-26 Jeffrey Altman    (6805) Windows: fix locking hierarchy in service
    2012-02-26 Jeffrey Altman    (6804) Windows: log SMB or RDR in use at startup
    2012-02-26 Jeffrey Altman    (6803) Windows: Add version number to event log start pending message
    2012-02-26 Jeffrey Altman    (6802) Windows: afslogon network provider debug registry value
    2012-02-26 Jeffrey Altman    (6801) Windows: afslogon.dll is not a file system interface
    2012-02-26 Jeffrey Altman    (6800) Windows: torture error reporting
    2012-02-26 Jeffrey Altman    (6799) Windows: change buf_Find*() signature to accept cm_fid_t
    2012-02-26 Jeffrey Altman    (6798) Windows: do not drop lock unnecessarily
    2012-02-26 Jeffrey Altman    (6797) Windows: cm_serverLock read required not write
    2012-02-26 Jeffrey Altman    (6796) Windows: be explicit when mapping sharing violation
    2012-02-26 Jeffrey Altman    (6795) Windows: avoid duplicate volume update queries
    2012-02-26 Jeffrey Altman    (6794) Windows: fix condition calls to osi_Log
    2012-02-25 Derrick Brashear  (6793) Rewrite make_h_tree.pl in shell script
    2012-02-23 Andrew Deason     (6778) salvager: Do not abort on large volume IDs
    2012-02-23 Derrick Brashear  (6777) libafs: retry retriable RPCs instead of abandoning
    2012-02-23 Derrick Brashear  (6772) libafs: ensure one nat ping connection per srvAddr
    2012-02-23 Derrick Brashear  (6771) volser: Remove unused variable
    2012-02-23 Derrick Brashear  (6770) viced: Relax "h_TossStuff_r failed" warnings
    2012-02-23 Derrick Brashear  (6769) viced: Remove extraneous h_AHTAHT_r in h_GetHost_r
    2012-02-23 Derrick Brashear  (6768) viced: Set h_GetHost_r probefail if MPAA_r fails
    2012-02-23 Derrick Brashear  (6767) viced: Correctly update addrs on alt addr probe
    2012-02-23 Derrick Brashear  (6766) viced: Delete dup host before probing old host
    2012-02-23 Derrick Brashear  (6765) vos: allow releases without offline time
    2012-02-23 Derrick Brashear  (6764) vos: refactor code
    2012-02-23 Derrick Brashear  (6763) Rx: Avoid lastBusy/PEER_BUSY discrepancy
    2012-02-23 Derrick Brashear  (6762) vol: allow clones of readonly volumes
    2012-02-23 Derrick Brashear  (6761) volser: allow clonevol purge id to be new id
    2012-02-23 Derrick Brashear  (6760) volser: allow cloning non-rw volumes
    2012-02-23 Derrick Brashear  (6759) libafs: kill rxevent daemon even in upcall mode
    2012-02-23 Derrick Brashear  (6758) doc: refer to aklog instead of klog
    2012-02-23 Derrick Brashear  (6757) RedHat: Fail openafs-client 'stop' on rmmod error
    2012-02-23 Derrick Brashear  (6756) doc: fix AdminGuide
    2012-02-23 Derrick Brashear  (6755) doc: add section on direct volume access
    2012-02-23 Derrick Brashear  (6754) viced: Keep H_LOCK while locking host in h_Alloc_r
    2012-02-23 Derrick Brashear  (6753) viced: Allow null host for BreakCallBack
    2012-02-23 Derrick Brashear  (6752) com_err: correctly deal with lack of libintl
    2012-02-23 Derrick Brashear  (6751) linux: fix probing for noop_fsync
    2012-02-23 Derrick Brashear  (6750) viced: lockcount only valid if not expired
    2012-02-08 Andrew Deason     (6683) Disable kernel opt by default on Solaris 10 and 11
    2012-02-08 Andrew Deason     (6682) SOLARIS: Use kcred instead of afs_osi_cred
    2012-02-07 Andrew Deason     (6642) afs: Panic on afs_conn refcount imbalance
    2012-02-07 Andrew Deason     (6641) Unix CM: reset blacklist on hard-mount retry
    2012-02-05 Simon Wilkinson   (6640) Linux: rpm: Update openafs.spec.in to include changes to installed files
    2012-02-05 Andrew Deason     (6643) SOLARIS: Do not build x86 kernel module on 5.11
    2012-01-24 Derrick Brashear  (6614) make openafs 1.6.1pre2
    2012-01-24 Derrick Brashear  (6613) viced: disable rx keepalives during disk io
    2012-01-24 Derrick Brashear  (6612) rx: RX_CALL_IDLE and RX_CALL_BUSY
    2012-01-24 Derrick Brashear  (6611) RX: Avoid timing out non-kernel busy channels
    2012-01-24 Derrick Brashear  (6610) libafs: add replicated connection pool
    2012-01-24 Derrick Brashear  (6609) vol: remove SYNC fatal_error processing
    2012-01-23 Derrick Brashear  (6570) rx: Correctly test for end of call queue
    2012-01-23 Derrick Brashear  (6569) Linux: use standard macro for set_nlink configure test
    2012-01-16 Derrick Brashear  (6550) vol: Fix VCreateVolume special inode cleanup
    2012-01-16 Derrick Brashear  (6549) DAFS: Fix SYNC_FAILED VScheduleSalvage_r log
    2012-01-11 Derrick Brashear  (6522) rx: add and export a public keepalive toggle
    2012-01-11 Derrick Brashear  (6521) afs: put back conn if not using in checkserver loop
    2012-01-11 Derrick Brashear  (6527) Make libjafs buildable again
    2012-01-11 Derrick Brashear  (6526) libuafs: only rebuild h directory when needed
    2012-01-09 Derrick Brashear  (6520) afs: discard cached state when we are unsure of validity
    2012-01-07 Derrick Brashear  (6495) DAFS: Atomically re-hash vnode in VGetFreeVnode_r
    2012-01-07 Derrick Brashear  (6494) afs: Grab a reference to setp in afs_icl_Event4
    2012-01-07 Michael Meffie    (6386) xstat: cm xstat time values are 32 bit
    2012-01-07 Derrick Brashear  (6518) afs: increase idledead time
    2012-01-03 Derrick Brashear  (6493) linux: fsync on a directory should return 0, not EINVAL
    2012-01-03 Derrick Brashear  (6492) rpm: Don't attempt to restart on upgrade when using systemd
    2011-12-27 Andrew Deason     (6414) libafs: memset dirHeader->hashTable
    2011-12-20 Andrew Deason     (6388) Include afsconfig.h before anything else
    2011-12-19 Andrew Deason     (6376) aklog: Add replacement setenv/unsetenv
    2011-12-17 Andrew Deason     (6348) afs: Clear VHardMount on ResetVolumeInfo
    2011-12-17 Derrick Brashear  (5809) make openafs 1.6.1pre1
    2011-12-17 Andrew Deason     (6347) libafs: Rate-limit hard-mount waiting messages
    2011-12-17 Andrew Deason     (6346) libafs: Remove unused volume "states" flags
    2011-12-17 Andrew Deason     (6345) libafs: Avoid using changing unixuser ticket data
    2011-12-16 Derrick Brashear  (6295) pam: Fix password torching const-ness
    2011-12-16 Derrick Brashear  (6293) pam: Clear up PAM_CONST related warnings on Linux
    2011-12-16 Derrick Brashear  (6319) SOLARIS: Define BSD_COMP for non-UKERNEL on 5.11
    2011-12-16 Derrick Brashear  (6318) vlserver: Avoid atoi for vol ids
    2011-12-16 Derrick Brashear  (6313) rx: arrange for Finalize to really stop running calls
    2011-12-16 Derrick Brashear  (6312) RPM: Fix dkms support on Fedora 15
    2011-12-16 Derrick Brashear  (6324) DAFS: Ensure logging on attach2 errors
    2011-12-16 Derrick Brashear  (6325) salvager: Create link table with volume group id
    2011-12-16 Derrick Brashear  (6326) libafs: only do pings for default conn with root uid
    2011-12-16 Derrick Brashear  (6327) libafs: disable mtu discovery
    2011-12-16 Derrick Brashear  (6320) DAFS: Do not transition to ERROR on trivial errors
    2011-12-16 Derrick Brashear  (6321) DAFS: Ensure GetVolume errors on ERROR volumes
    2011-12-16 Derrick Brashear  (6322) DAFS: Log more for VPreAttachVolumeByVp odd states
    2011-12-16 Derrick Brashear  (6323) DAFS: Avoid unnecessary preattach on FSYNC_VOL_ON
    2011-12-16 Derrick Brashear  (6328) vol: log error reason on header read failure
    2011-12-16 Derrick Brashear  (6315) solaris: libafs depends on fs/ufs
    2011-12-16 Derrick Brashear  (6314) ntohs ubik header size
    2011-12-16 Derrick Brashear  (6292) make afsdump_scan get ACLs right
    2011-12-16 Derrick Brashear  (6329) vos: fix code to not triple-negate
    2011-12-16 Derrick Brashear  (6316) cache bypass: don't define iovecp for UKERNEL
    2011-12-16 Derrick Brashear  (6311) aklog: strlen(NULL) doesn't work
    2011-12-16 Derrick Brashear  (6298) viced: Check vnode length on Rename and Link
    2011-12-16 Derrick Brashear  (6310) ihandle: OPEN fdPs are not counted in ihP refcount
    2011-12-16 Derrick Brashear  (6309) xserver lock order violation
    2011-12-16 Derrick Brashear  (6308) xvcb lock order violation
    2011-12-16 Derrick Brashear  (6307) aklog: work around lion kerberos disaster
    2011-12-16 Derrick Brashear  (6306) ihandle: Actually assert active fdPs are not AVAIL
    2011-12-16 Derrick Brashear  (6305) LINUX  vcache lock ordering in afs_linux_readdir
    2011-12-16 Derrick Brashear  (6304) butc: initialize startTime before it is used
    2011-12-16 Derrick Brashear  (6303) afsd: Fail gracefully on mtab open failure
    2011-12-16 Derrick Brashear  (6302) vos: Don't leak/overflow bulkaddrs
    2011-12-16 Derrick Brashear  (6301) volinfo: fix size totals when saving inodes
    2011-12-16 Derrick Brashear  (6300) libafs: Always use anonymous VL connections
    2011-12-16 Derrick Brashear  (6299) viced: Don't VTakeOffline_r without glock
    2011-12-16 Derrick Brashear  (6296) viced: Do not try to reuse deleted client
    2011-12-16 Derrick Brashear  (6294) pam: Password is const in setcred
    2011-12-16 Derrick Brashear  (6291) pam: Use PAM_CONST more often
    2011-12-16 Derrick Brashear  (6290) pam: Check for null upwd from getpwnam_r
    2011-12-16 Derrick Brashear  (6289) pam: Use POSIX getpwnam_r on Solaris
    2011-12-16 Derrick Brashear  (6288) kernel upcall rx env should shut down event daemon
    2011-12-16 Derrick Brashear  (6286) DAFS: Request salvage on detach for volser
    2011-12-16 Derrick Brashear  (6285) volser: Avoid assert on ViceCreateRoot failure
    2011-12-16 Derrick Brashear  (6284) DAFS: Do not give back vol to viced after salvage
    2011-12-16 Derrick Brashear  (6283) afsd: Trim trailing slashes on Linux mntent
    2011-12-16 Derrick Brashear  (6282) ubik: don't rely on timeout value after select()
    2011-12-16 Derrick Brashear  (6281) Irix: Supress some more warnings in kernel builds
    2011-12-16 Derrick Brashear  (6280) fsprobe: Fix usage message
    2011-12-16 Derrick Brashear  (6279) fsprobe: call RXAFS_GetTime directly
    2011-12-16 Derrick Brashear  (6278) Linux: Fix USE_UCONTEXT detection
    2011-12-16 Derrick Brashear  (6273) vol: remove warning on use of DFlushVolume
    2011-12-16 Derrick Brashear  (6268) vol: Move VOL_CV_TIMEDWAIT to volume_inline.h
    2011-12-15 Derrick Brashear  (6276) vol: Add timeouts to SYNC server select() calls
    2011-12-15 Derrick Brashear  (6275) namei: Log ListViceInodes write failures
    2011-12-15 Derrick Brashear  (6274) macos: dont want bind 8 compat on leopard
    2011-12-15 Derrick Brashear  (6317) doc: limitations of addsite on different partitions
    2011-12-15 Derrick Brashear  (6297) doc: Add aklog_dynamic_auth manpage
    2011-12-15 Derrick Brashear  (6271) LINUX: afs_linux_put_link is void
    2011-12-15 Derrick Brashear  (6270) DAFS: listvol + unsalvagable volumes = intolerable delay
    2011-12-15 Derrick Brashear  (6269) LINUX: Reduce stack depth on recursive symlink res
    2011-12-15 Derrick Brashear  (6267) rxgen: add *TranslateOpcode functions to XDR code
    2011-12-15 Derrick Brashear  (6287) fix manpage for udebug -servers
    2011-12-15 Derrick Brashear  (6277) macos: no more startupitems
    2011-12-14 Derrick Brashear  (6265) vol: Add interfaces for registering RX calls
    2011-12-14 Derrick Brashear  (6264) vol: Add VGetVolumeTimed
    2011-12-14 Derrick Brashear  (6263) rx: Call rxgen_consts.h by its proper name
    2011-12-14 Derrick Brashear  (6262) udebug: Always show tidCounter
    2011-12-14 Derrick Brashear  (6261) ubik: add interface for reading during write locks
    2011-12-14 Derrick Brashear  (6260) ubik: Fix buffers for reading-during-writes
    2011-12-14 Derrick Brashear  (6259) ubik: Abstract buffer matching and pass trans ptrs
    2011-12-13 Derrick Brashear  (6232) afs: prevent nat pings on destroyed connections
    2011-12-09 Benjamin Kaduk    (6235) FBSD: switch afsi_SetServerIPRank implementation
    2011-12-09 Benjamin Kaduk    (6234) FBSD: cleanup dvp locking for ISDOTDOT
    2011-12-09 Benjamin Kaduk    (6233) FBSD: typo fix
    2011-12-01 Derrick Brashear  (6161) remove CopyOnWrite2 and unused vars
    2011-12-01 Derrick Brashear  (6160) viced: disable accelerated copyonwrite
    2011-11-28 Derrick Brashear  (6124) Unix CM: Fix PutVolume in afs_BlackListOnce
    2011-11-28 Derrick Brashear  (6123) afs: Leave cellnum alone for explicit mtpt cell
    2011-11-28 Derrick Brashear  (6122) dafs: avoid null deref getting volume header
    2011-11-28 Derrick Brashear  (6121) Linux: 3: Update specfile to know about 3.* kernels.
    2011-11-22 Marc Dionne       (6104) Linux: make sure backing_dev_info is zeroed
    2011-11-21 Anders Kaseorg    (6098) Linux: 3.1: adapt to fsync changes
    2011-11-21 Anders Kaseorg    (6099) Linux: 3.2: Use set_nlink to update i_nlink
    2011-11-21 Anders Kaseorg    (6097) Linux: d_delete now takes a const argument
    2011-11-20 Derrick Brashear  (6090) redhat: make rpms build on pre-f15 again
    2011-11-20 Derrick Brashear  (6089) linux: Update Packaging to build OpenAFS services for Fedora's systemd
    2011-11-20 Derrick Brashear  (6088) Linux: 3.1: update RCU path walking detection in permission i_op
    2011-11-20 Derrick Brashear  (6087) klog.krb5: enforce DES for rxkad
    2011-11-20 Derrick Brashear  (6086) Solaris: Specify ARCHFLAGS in CFLAGS
    2011-11-20 Derrick Brashear  (6085) DAFS: Deal with exclusive-state volume headers
    2011-11-20 Derrick Brashear  (6084) ukernel: handle pioctl errors properly in ktc
    2011-11-20 Derrick Brashear  (6083) salvager: Implement AskDAFS via SYNC flags
    2011-11-20 Derrick Brashear  (6082) regen: Fail on failures
    2011-11-20 Derrick Brashear  (6081) viced: avoid bogus handle in rename
    2011-11-20 Derrick Brashear  (6080) volser: Preserve needsSalvaged during restore
    2011-11-19 Derrick Brashear  (6079) namei: Remove extraneous rmdir
    2011-11-19 Derrick Brashear  (6078) namei: tweak getlinkbyte error handling
    2011-11-15 Jeffrey Altman    (6045) Windows: Track active RPCs per scache_t
    2011-11-15 Jeffrey Altman    (6044) Windows: Add Vista/Win7 Firewall Configuration
    2011-11-15 Jeffrey Altman    (6043) Windows: cm_Rename break in 9cf7a628c2ff178b2fa236d2c0a41ca9be315036
    2011-11-15 Jeffrey Altman    (6042) Windows: out of date version not in current chunk
    2011-11-15 Jeffrey Altman    (6041) Windows: only flush buffers on shutdown if running
    2011-11-15 Jeffrey Altman    (6040) Windows: Do not EEXIST exact match during rename
    2011-11-15 Jeffrey Altman    (6039) Windows: validate buffer hash tables in cm_MergeStatus
    2011-11-15 Jeffrey Altman    (6038) Windows: record history of read lock threads
    2011-11-15 Jeffrey Altman    (6037) Windows: ignore SYNCHRONIZE privilege in cm_CheckNTOpen
    2011-11-15 Jeffrey Altman    (6036) Windows: permit offline volume check to be disabled
    2011-11-15 Jeffrey Altman    (6035) Windows: add clean rule to src/afs/NTMakefile
    2011-11-15 Jeffrey Altman    (6034) Windows: correct comments in cm_BkgStore
    2011-11-15 Jeffrey Altman    (6033) Windows: remove CM_BUF_CMBKGFETCH flag
    2011-11-15 Jeffrey Altman    (6032) Windows: use lock conversion in cm_EndDirOp
    2011-11-15 Jeffrey Altman    (6031) Windows: cm_SymLink export created cm_scache_t
    2011-11-15 Jeffrey Altman    (6030) Windows: correct cm_buf use of Head/Tail queues
    2011-11-15 Jeffrey Altman    (6029) Windows: remove dead code from cm_scache.c
    2011-11-15 Jeffrey Altman    (6028) Windows: add logging to smb_IoctlRead
    2011-11-15 Jeffrey Altman    (6027) Windows: remove potential data loss warning with cast
    2011-11-15 Jeffrey Altman    (6026) windows: pass cm_req_t through background ops
    2011-11-15 Jeffrey Altman    (6025) Windows: correct log message in buf_Sync()
    2011-11-15 Jeffrey Altman    (6024) Windows: buf_SetDirty do nothing if length is zero
    2011-11-15 Jeffrey Altman    (6023) Windows: remove MULTIHOMED ifdef
    2011-11-15 Jeffrey Altman    (6022) Windows: missing ! in update volume location
    2011-11-15 Jeffrey Altman    (6021) Windows: improve handling of volume rename
    2011-11-15 Jeffrey Altman    (6020) Windows: refactor volume location updates
    2011-11-14 Jeffrey Altman    (6019) Windows: netidmgr krb5_cc_get_principal can fail
    2011-11-11 Andrew Deason     (5831) volser: Remove debugging log messages
    2011-11-09 Simon Wilkinson   (5820) rx: Don't clear the receive queue when out of packets
    2011-11-04 Andrew Deason     (5788) afs: Only use actual connections for GetTime calls
    2011-11-02 Andrew Deason     (5771) make bozo honor -rxbind correctly
    2011-11-02 Andrew Deason     (5770) Suppress cmp component version error messages
    2011-11-02 Andrew Deason     (5769) viced: Check vnode length on dir ops
    2011-11-02 Andrew Deason     (5768) viced: Check vnode length on read and write
    2011-11-02 Andrew Deason     (5767) DAFS: DFlushVolume outside of vol glock
    2011-11-02 Andrew Deason     (5766) afs: Retry unlock after afs_StoreAllSegments
    2011-11-02 Andrew Deason     (5765) afs: Avoid memory leak on recursive write flock
    2011-11-02 Andrew Deason     (5764) vol: avoid MAXINT redefinition warning in vnode.c
    2011-11-02 Andrew Deason     (5763) DAFS: Correct FSYNC_VOL_QUERY_VOP checks
    2011-11-02 Andrew Deason     (5762) salvager: Give back volumes when exiting early
    2011-11-02 Andrew Deason     (5761) DAFS: Do not record vol ops for DELETED vols
    2011-11-02 Andrew Deason     (5760) salvager: Do not AskOnline nonexistent volumes
    2011-11-02 Andrew Deason     (5759) Fix ihandle.c indents
    2011-11-02 Andrew Deason     (5758) vol: Handle large volume IDs in VLockFile
    2011-11-02 Andrew Deason     (5757) vol-salvage: Fix AskOnline error message
    2011-11-02 Andrew Deason     (5756) Give a default reason in *sync-debug
    2011-11-02 Andrew Deason     (5755) ConvertROtoRW: Use old copyDate for creationDate
    2011-11-02 Andrew Deason     (5754) libafs: Set tvcp->callback before BulkStatus
    2011-11-02 Andrew Deason     (5753) ubik: Log a message when we replay the trans log
    2011-11-02 Andrew Deason     (5752) ubik: Replay the transaction log label correctly
    2011-11-02 Andrew Deason     (5751) ubik: Record the last write tid in writeTidCounter
    2011-11-02 Andrew Deason     (5750) DAFS: raise vhashsize limit
    2011-11-02 Andrew Deason     (5749) DAFS: Do not ignore out-of-range -vhashsize
    2011-11-02 Andrew Deason     (5779) Tidy up uio_t meaning
    2011-11-02 Andrew Deason     (5778) SOLARIS: Perform daemon syscalls as kernel threads
    2011-11-02 Andrew Deason     (5777) libafs: Consolidate afs_DaemonOp code
    2011-11-02 Andrew Deason     (5776) libafs: Indent afs_call.c ifdef maze
    2011-10-29 Benjamin Kaduk    (5639) FBSD: deal with kernel API rename
    2011-10-26 Derrick Brashear  (5726) ukernel: get an ip address even when dns and hosts suck
    2011-10-26 Derrick Brashear  (5725) allow cloning of any volume to any volume with same parent ID
    2011-10-26 Derrick Brashear  (5724) remove check for disallowing clones of backup or ro volumes
    2011-10-26 Derrick Brashear  (5723) bozo: test program update
    2011-10-26 Derrick Brashear  (5722) DAFS: Remove VOL_SALVAGE_INVALIDATE_HEADER
    2011-10-26 Derrick Brashear  (5721) DAFS: fssync online requires a partition name argument
    2011-10-26 Derrick Brashear  (5720) volser: Remove ExtractVolId
    2011-10-26 Derrick Brashear  (5719) viced: Check for HOSTDELETED in stillborn check
    2011-10-26 Derrick Brashear  (5718) vos offline: Bring volume back online for -busy
    2011-10-26 Derrick Brashear  (5717) bypasscache: allow arbitrary sized iovecs
    2011-10-26 Derrick Brashear  (5716) bypasscache: do errors correctly
    2011-10-26 Derrick Brashear  (5715) rpm: Turn on debugging
    2011-10-26 Derrick Brashear  (5714) rx: ackall handling
    2011-10-26 Derrick Brashear  (5713) LINUX: Fix afs_linux_pag_to_groups signature
    2011-10-26 Derrick Brashear  (5712) LINUX: Revert group changes on keyring failure
    2011-10-26 Derrick Brashear  (5711) viced: Do not swallow errors on StoreData recovery
    2011-10-26 Derrick Brashear  (5710) linux: makesrpm should cope with releases with letters
    2011-10-26 Derrick Brashear  (5709) afs: don't try GetDownD if nothing to get
    2011-10-26 Derrick Brashear  (5708) ukernel: don't define rdwr env on linux
    2011-10-26 Derrick Brashear  (5707) ukernel: set pthread stacksize to an integer multiple of 8k
    2011-10-26 Derrick Brashear  (5706) ukernel: add morepackets check in listener
    2011-10-26 Derrick Brashear  (5705) afs: on uuid init fail, don't leave garbage behind
    2011-10-26 Derrick Brashear  (5704) ukernel: set close-on-exec on our socket
    2011-10-26 Derrick Brashear  (5703) docs: Refer to dafs binaries by their real names
    2011-10-26 Derrick Brashear  (5702) ptserver: Don't check for noauth before rebuilding
    2011-10-26 Derrick Brashear  (5701) ukernel: don't enforce thread lockers in remove vop
    2011-10-26 Derrick Brashear  (5700) ukernel: install our sysincludes to root.perf
    2011-10-26 Derrick Brashear  (5699) ukernel: add uafs_access
    2011-10-26 Derrick Brashear  (5561) bypasscache for ukernel
    2011-10-26 Derrick Brashear  (5698) vol_split: avoid using stale open directory vnodes
    2011-10-23 Derrick Brashear  (5611) bozo: bosserver man page updates

### Patches merged into the stable 1.4.x branch

    Date       Committer        Change# Description
    2012-04-03 Derrick Brashear  (7024) viced: AFSDisk, AFSFetchVolumeStatus Int31 PartSize
    2012-02-03 Andrew Deason     (6623) rx: Correctly test for end of call queue
    2012-01-23 Andrew Deason     (6415) libafs: memset dirHeader->hashTable
    2012-01-23 Andrew Deason     (6593) libafs: Drop xvcache for AllocCBR
    2011-11-02 Andrew Deason     (5780) afs: Remove afs1_readdir
    2011-10-30 Andrew Deason     (5729) LINUX: Revert group changes on keyring failure
    2011-10-30 Andrew Deason     (5728) Linux: Fix return codes from setpag
    2011-10-24 Simon Wilkinson   (5618) dir: Protect against circular hash chains
    2011-10-24 Simon Wilkinson   (5617) libafs/dir: Verify directory pathnames
    2011-10-21 Andrew Deason     (5647) libafs: Set tvcp->callback before BulkStatus
