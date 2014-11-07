---
title: OpenAFS Newsletter, Volume 4, Issue 5, March 2013
---

# OpenAFS Newsletter, Volume 4, Issue 5, March 2013

## /afs/Introduction

We have an exciting lineup for you in this issue of the OpenAFS Newsletter. If you follow the mailing lists, you may be aware of the "ulimit" issue with recent RedHat Enterprise 6 kernels and OpenAFS servers. Dan Van Der Ster of CERN has been kind enough to tell us the exciting tale of how his was first bitten by, then chased, and finally swatted this particular bug. And we have the first part in a series of articles on OpenAFS tuning. If you are looking to squeeze additional performance out of OpenAFS or to just optimize the AFS experience for your users, you should definitely read on.

We start off the newsletter with a rare, but important set of OpenAFS security advisories.

As always, your feedback and suggestions are welcome. Email us at: newsletter@openafs.org

## Security Advisories

OpenAFS servers are subject to two security advisories, both dated 27-Feb-2013. Please take a look at

http://www.openafs.org/security

for details. And update your servers as soon as possible.

## On Fileserver Segfaults, and Making the World Safe

	Dr. Daniel C. van der Ster
	Storage Engineer, CERN IT

\[What follows is a dramatic version of the events first announced in the Nov. 2012 mail to openafs-info with subject "1.4.x, select() and recent RHEL kernels beware"\]

Here at CERN, OpenAFS is a critical IT service hosting home directories, analysis workspaces, and project/application areas -- in total we serve up roughly 180+TBs from around 60 beefy servers. Our users, numbering in the thousands, and like many others in the academic community, depend on AFS to be rock-solid stable for both interactive development work and batch analysis processing.

So, when newly deployed production fileservers start segfaulting every few hours, as it happened in early November 2012, its gets our immediate and urgent attention.

We first noticed this problem the morning of November 6. At 4am, our monitoring detected that one of our new servers had reported a segfault and a restart of the fileserver process. Such errors do happen occasionally in our cell and are probably related to the fact that we run the reasonably aged OpenAFS 1.4.14, or perhaps due to stray neutrinos from the particle collider we have 100 meters beneath our data centre. Normally, fileserver restarts don't wake us up in the middle of the night -- they result in only a short outage. However, when this same fileserver segfaulted again at 5:30am and again every couple hours that day, we started to get very, very worried.

Feeling emboldened by our recent success with a UDP packet loss issue \[1\], we immediately got to work debugging the fileserver core dumps. The first results of our gdb investigation \[2\] showed that most of the hourly segfaults happened on the same line of code:

	#0  0x000000000044c81c in GetHandler (fdsetp=0x6fb920, maxfdp=0x7ffa1d2b3d1c) at ../vol/fssync.c:816 sdf
	816         FD_SET(HandlerFD[i], fdsetp);

At the time of the first crash, HandlerFD\[i\] equalled -33554433, whereas the other three entries of the HandlerFD array were 10, 54, and 1367. Not knowing much about FD\_SET and file descriptors in general, this meant basically nothing to us.

However, later that morning, we noticed something very strange: at around 10am the server restarted again, but this time gdb showed a segfault on a different line of code, namely:

	#0  0x000000000044c1d2 in CallHandler (fdsetp=0x6fb920) at ../vol/fssync.c:746
	746         (*HandlerProc[i]) (HandlerFD[i]);

and value of the function pointer HandlerProc\[i\] was 0x40000000044b556. Now, it doesn't take a lab of 5000 particle physicists to realise that that address is simply the reasonable value 0x44b556 with a single bit set way off in some absurd position. Additionally, in this core dump we found that one of the HandlerFD values was again a large negative value, this time -32769.

Seeing this random bit setting and two large negative numbers for file descriptors, we pulled out our trusty OS X calculators, set them to "Programmer" mode, and got to work. As it turns out, -33554433 in binary is simply all ones with a zero at bit 25, and -32769 is all ones with bit 15 set to zero. So there we had it, three cases of erroneous data all showing random bit flips resulting in segfaults and core dumps. We had isolated the problem: faulty hardware, bad memory chips.

Or had we?

We fully expected that, after vos mov'ing the volumes off of this server in order to run some intensive memory tests, the chips would be quickly identified as faulty. We started the memtest86+ process and waited… and waited… and waited for around 3 hours. The test didn't find any errors. Believing that memtest86+ must have been wrong, we ran the user-mode memtester application for another couple of hours. Nothing… Nada! Those memory chips were perfect, and the System Event Logs of the hardware confirmed it: no memory errors reported.

(At this moment I should point out that, in a way, we were relieved at this news. Since, had the memory actually been faulty we might have been faced with a worse problem: random undetectable corruptions of user data in the AFS volumes. So… phew!)

Back to square one. For a brief moment, we started believing in fairy tales -- in the possibility of the aforementioned effects of stray neutrinos being real... that somehow the in-memory copy of the fileserver process had become corrupted and was running random bit-flipped code. The solution to such an error would be a hard reboot of the server itself. But, alas, such a reboot didn't solve anything: the fileserver dumped its core again minutes after the reboot.

At this point we pulled out our textbooks (i.e. Google) and started researching exactly how select() and FD\_SET work, in the hope that someone else had seen a similar problem. Quickly we found an article which described a scenario where FD\_SET can cause single bit corruptions in memory. Basically, on Linux hosts with an FD\_SETSIZE > 1024, when you use FD\_SET it will blindy set bits beyond the range of the FD\_SET. The solution to this problem is to use polling IO rather than select() and FD\_SETs. But alas OpenAFS 1.4 didn't have such code implemented.

This explanation certainly matched what we were observing, but why had this started so suddenly on our new servers whereas our other older servers had been running without incident for months at a time? After a bit more Googling, we found an old OpenAFS ticket \[3\] in which a user was getting segfaults after increasing the number of file descriptors per process from 1024 to 2048. We then checked our servers and found indeed that our older, reliable, servers had 1024 FDs, whereas the newer crashy servers had 4096. Additionally, we noticed that the bad servers were running kernel 2.6.32-279 or newer. And, getting close to the end now, we scanned the change log of RHEL kernel 2.6.32-279 until we saw this patch:

    [kernel] ulimit: raise default hard ulimit on number of files to 4096 (Jarod Wilson) [786307]

where finally, and in a rather hilarious twist, the full comment of the commit mentioned the following:

    Application developers have known for years that select() has
    this flaw, and I'm starting to see desktop apps that really do
    need more file descriptors. It may be time for us to start purging
    dangerous calls to select() from the ubuntu codebase, to make the
    world safe for higher values of ulimit -n.

So there we had it: an upgraded RedHat kernel on our newest servers had increased the ulimit -n from 1024 to 4096 to expose "dangerous applications", and that broke the fileserver so terribly that it wouldn't run for more than a couple hours without a segfault. The trivial workaround was, of course, to set ulimit -Hn and ulimit -Sn to 1024 in the fileserver init script. And after deploying that workaround, we haven't observed another segfault of this nature.

(Editor's note... one can also edit /etc/security/limits.conf adding the line

	*       hard    nofile  1024

to enforce this change to the number of file descriptors).

In closing, it is important to mention that OpenAFS 1.6.2 \[Editor's note, released March 4, 2013\] should have enabled the polling code, which will finally resolve the issue described in this article. Assuming that that code works as described, we can all rest knowing that, as the author of the RHEL ulimit patch has wished, the world will then be a safer place.

\[1\] See "performance and udp buffers" on openafs-info, October 9, 2012.

\[2\] The gory gdb debugging details are documented here: https://afs.web.cern.ch/afs/reports/html/afs200SegFaults.html

\[3\] http://rt.central.org/rt/Ticket/Display.html?id=74708



## Did You Know... IP ACL Gotchas?

IP ACLs are a common way of allowing a host on a particular IP address access to some portion of AFS-space. And used properly, IP ACLs can be a quick way to allow some set of hosts access to a particular subset of AFS-space. But, IP ACLs have a couple of gotchas...

- No encryption is possible. The data connection between the client and server is not encrypted.
- Two hour refresh timer. The fileservers only refresh groups populated by IP ACLs every two hours.
- Wildcarding is IP class based. Your netmask must match the "default" IP class for the particular IP range of your clients. Otherwise, the results of the wildcarding may allow or disallow hosts you did not intend access to AFS-space.

The above are just a few highlights. More can be found on the AFS Wiki at:

http://wiki.openafs.org/IPAccessControl/

## OpenAFS tuning, part I: Fileservers, general

	Andrew Deason
	Senior Software Engineer
	Sine Nomine Associates



In this article, we'll explore some tips on improving fileserver performance.
I'll cover several problems that I've seen at various OpenAFS sites in the past
involving fileserver performance, and I'll explore how to detect these problems
and what to do about them. As we discuss some of these problems, it may seem
that the technical reason underlying the problem and its solution are not a
performance tweak. However, keep in mind that these problems all may look like
performance issues when first encountered.

In a few places, a patch is mentioned that is not yet in a stable OpenAFS
release, but a "gerrit" number is given. If you are comfortable checking out
and patching code, it may be possible in some cases to apply the patch to
existing stable releases of OpenAFS. You should also contact me if you want
more information on these patches, as for some of them I already have them
ported to different OpenAFS releases.

This article by no means covers all performance-related options and tweaks that you can
do to the fileserver. We only cover some of the more serious issues
and improvements I've seen made at various sites. We'll start off with some more
general or high-level recommendations, and move in to adjusting actual options
for the fileserver.

### DAFS

If you want a single fileserver to serve a lot of volumes, you should consider
using the Demand Attach File Server (DAFS). "A lot" of volumes is not well
defined, but if you notice that fileserver startup or shutdown is taking a lot
of time (especially beyond what you consider acceptable downtime for a restart)
and is using a lot of disk I/O, DAFS may drastically speed up startup/shutdown.
Some sites begin seeing these problems when they get into the tens of thousands
volumes per fileserver. Note that this problem is regardless of the traffic to
those volumes; this problem is simply due to the number of volumes on the
server.

If you want to migrate to DAFS, check out Appendix C of the OpenAFS Quick Start
Guide for UNIX.

### Use ReadOnly (RO) Volumes

\[Explaining how RO volumes work and how to use them is beyond the scope of this
article; this section assumes you are familiar with RO volumes.\]

RO volumes are often used as a way to increase availability of a volume, and to
distribute load for a specific volume amongst several servers. However,
sometimes people do not think to use RO volumes when there's only one
fileserver on which the data could reside.

Even with only one RO site, a RO volume could be advantageous to using a
ReadWrite (RW) volume.  When a client reads data from a RO volume, the volume's
data tends to be cached by the client for a longer period of time, and the
amount of resources used on the fileserver for the request is less. The result
is that the scalability of the fileserver increases. The client cache hit rate
also increases. So, for any data that does not change "frequently", RO volumes
can be better all around for performance.

"Frequently" usually means less often than once a day. But, RO volumes may be
beneficial for data that changes even up to around once every few hours. Of
course, using ROs mean you must "vos release" the volumes, so there is some additional
operational overhead and additional complexity. But purely from a performance
point of view, in the above situations RO volumes are usually beneficial.

### Load Balancing

Another general recommendation is to try to distribute load evenly among all
fileservers. There are several ways to determine "load", but one easy way is to use
a metric that OpenAFS already records -- the number of times each volume was
accessed in a day. You can see this metric via the "vos examine" or "vos listvol -long"
commands, on the line that says, for example "_123 accesses in the past day
(i.e., vnode references)_"; this number gets reset at around midnight. Once you
know how many accesses a volume gets in a day, you can try to rearrange volumes
on various fileservers so that the number of accesses they get are roughly
equal.

These statistics should be treated as rough estimates. The accuracy of these
statistics can vary depending on when you query this information. Also, the
data may be slightly out of date as, for performance reasons, the fileserver
only periodically writes this statistical information to disk.  You can get a
bit more consistent information by running 'volinfo' locally on the fileserver,
and looking at the 'week' array, which gives the number of accesses per day for
each day of the past week, of access numbers.

Also note that the above statistics currently get reset whenever a readonly
volume is released. So, for frequently-released volumes, this information is
not as useful. There is a patch proposed to 1.6 (gerrit 9477, commit dfceff1d3a66e76246537738720f411330808d64) to allow for preserving these
statistics across releases, but this patch is not yet in any stable OpenAFS
release.

It is also possible to get more detailed metrics by processing the fileserver's
"audit log" with a script or via DTrace probes on supported platforms. Some
sites record this data raw or with minimal preprocessing in SQL databases for later use in generating reports useful for rearranging volumes. A couple of tools exist to do this rearrangement
automatically: the older "balance" from CMU
[ftp://ftp.andrew.cmu.edu/pub/AFS-Tools](ftp://ftp.andrew.cmu.edu/pub/AFS-Tools), and the newer "afs-balance" from Russ
Allbery: [http://www.eyrie.org/~eagle/software/afs-balance/](http://www.eyrie.org/~eagle/software/afs-balance/).

### Clients Preventing Volumes Offlining

Sites sometimes see a volume release that seems to take a long time, or sites
sometimes see a fileserver that takes a long time to shutdown. While there can
be a few different causes, one specific situation I've seen in
practice is that the delay is due to a client very slowly accessing a volume.
The fileserver must wait for nothing to be using a volume before taking
the volume offline; so, such accesses can prevent a volume from releasing or
a fileserver from shutting down for a significant amount of time.

To see if this is happening to you is not always easy. However, if a fileserver
is taking a long time to shutdown without a lot of disk activity (i.e., it just
appears to be hanging), this may be the reason. Or if a volume release seems to
hang while trying to create a volume transaction (as reported by 'vos release
\-verbose') instead of while transmitting data, this again may be the reason.
Unfortunately, to be completely sure involves taking cores of the fileserver or
capturing wire dumps, which then requires some analysis by a developer.

Currently, addressing this problem is not easy. There are some patches to allow
the fileserver to forcibly "kick off" clients in this situation (gerrit 2984 et
al), but these patches are not yet in any OpenAFS stable release. It is also
possible to identify which clients are causing this problem (again with server
cores/dumps), and fix or blacklist those clients, but that requires ongoing
monitoring.

### Fileserver Options

Here, we move into specific command line options that you can give to the
fileserver to improve performance.

#### \-S and -L

These set many options for "small" and "large" fileserver configurations. For
modern machines, just set -L and you'll get a somewhat reasonable set of options
for many use cases. Using -S, or passing no options to the fileserver and
relying on the defaults, often results in inappropriate settings and may also result
in insufficient resources allocated to the fileserver for good performance.
Whether or not you specify -L, you can still configure specific options to tune
various parameters, some of which are described below.

#### \-p <number of processes> and "calls waiting"

The -p option sets the number of threads that handle incoming RPC requests, and
so also sets how many requests the fileserver can handle at the same time. For
versions 1.4 and earlier, the max you could set was around 128 (and this is what -L
sets). In 1.6 and beyond, there is no practical limit (the actual limit in 1.6.2
is around 16k).

A good starting point is 128 or 256, and is probably what the majority of
fileservers are set to these days. There are not many cases where 128 threads
is too many threads (such as if RAM is very limited), but there are many cases
where 128 threads or more is appropriate. To determine if you should raise the
number of threads, you can look at whether or not the fileserver ever ran out
of threads. For a fileserver running on IP address 192.0.2.1, you would run the
following and see a few basic stats:

	$ rxdebug 192.0.2.1 7000 -noconns

	Trying 192.0.2.1 (port 7000):
	Free packets: 1589, packet reclaims: 64100, calls: 125034, used FDs: 64
	not waiting for packets.
	4 calls waiting for a thread
	2 threads are idle
	50 calls have waited for a thread

Depending on the version of 'rxdebug' and the fileserver being queried, this
output may look slightly different.

If the number next to "_calls waiting for a thread_" or "_calls have waited
for a thread_" are ever above 0, then the fileserver ran out of threads at at
least one point. In the above example output, the fileserver has currently run
out of threads, and 4 requests from the network are waiting for the fileserver
to become less busy before those 4 requests can be serviced. Since the
fileserver was last restarted, 50 requests from the network have arrived while
the fileserver was too busy to service them, and those requests had to wait.

The above output may or may not mean that the number of threads should be
raised. If situations like the above (non-zero "calls waiting") happen often or
happen very severely (lots of calls waiting), that may be a sign that more
threads would benefit the fileserver. To know how often this occurs, it can be
useful to run the above 'rxdebug' command regularly (e.g. every few minutes, or
even every few seconds), to record the output, and to generate notifications or
graphs based on the number of idle threads, calls waiting, and/or calls waited.

If the fileserver never runs out of threads, increasing the number of threads
will do nothing. However, if the number of idle threads gets pretty low, you may
consider raising the number of threads to try to avoid running out of threads
in the future.

One potential point of confusion you should note is that the above example
output lists 2 threads as idle, even though the fileserver is considered as
completely busy (and cannot service any incoming requests). These idle threads
are reserved by the fileserver for different kinds of requests (such as
statistics gathering) and cannot be used for client requests. So, that is why
it is possible for 2 threads to be idle (for statistics) and for there to still
be requests that cannot be serviced due to insufficient free threads. This is
also why you may see e.g. 130 idle threads, even though you only configured
128.

Also note that many different situations can cause the "calls waiting" counter
to rise. If there is a bug in OpenAFS, or there is some network or disk problem
that is causing all activity to block, then increasing the number of threads
will likely not help much (although in some of those situations, increasing the
number of threads can help a bit, it's not really solving the underlying
problem).  Increasing the number of threads is the proper fix when the load
caused by clients has just legitimately increased beyond the capacity of the
configured threads. Determining whether a large number of "calls waiting" is
due to load alone, or due to disk or network problems, is beyond the scope of
this section, and often involves more thorough investigation.

The -p option and the general information in this section is also applicable to
almost any OpenAFS process. It is possible to investigate and adjust the other processes in the same way, although for processes besides the fileserver it may not matter so much.

#### \-busyat <limit>

Related to the -p option and the notion of "calls waiting" is the -busyat
option. This option says that when the number of "calls waiting" is over a
certain point the fileserver will tell the client to stop waiting for a
response and to instead try a different fileserver (or to retry the request at the
same fileserver, if no other fileservers are available).

If you record "calls waiting" information and you find that your site sees very
bursty "calls waiting" spikes, it may be useful to raise the -busyat option.
With a higher -busyat, more clients will wait (versus timing out) for the
fileserver to respond.

However, if you notice that as soon as a fileserver starts to log "calls
waiting" it does not recover for a long period of time, it may be worth it to
reduce the -busyat value. Clients will then not wait for a particular
fileserver to respond when that fileserver will not respond in a timely manner.

#### \-cb <number of callbacks>

This option specifies how many "callback promises" the fileserver will keep
track of in memory. If the number of callback promises required exceeds this
number, the fileserver will prematurely break some callbacks to free up memory.

If you don't know what a "callback promise" is, read on. Every time a client
accesses a file on a fileserver, the fileserver must remember that that client
has accessed that file and that the client possibly has the file contents
cached. With this knowledge, the fileserver can (and must for correct
operation) inform such clients if the file ever changes. The client can then
request a new copy of the changed file.

How callback promises are kept and for how long is not currently tunable and is
more complicated to explain, and so will not be covered here.

In order to determine if you need to raise the number of callbacks, you can try
to determine if the fileserver has ever run out of callback space. Currently (as
of OpenAFS 1.6.2), the only way to see this is by running, for a fileserver
running on 192.0.2.1:

	$ xstat_fs_test 192.0.2.1 -collID 3 -onceonly

	Starting up the xstat_fs service, no debugging, one-shot operation

	------------------------------------------------------------
				   201 DeleteFiles
				 10140 DeleteCallBacks
				  1119 BreakCallBacks
				177433 AddCallBack
					 0 GotSomeSpaces
					80 DeleteAllCallBacks
				   136 nFEs
				   186 nCBs
				 64000 nblks
				  4071 CBsTimedOut
					 0 nbreakers
					 0 GSS1
					 0 GSS2
					 0 GSS3
					 0 GSS4
					 0 GSS5

If the number next to "_GotSomeSpaces_" or any of the "_GSS\*_" fields is
greater than 0, then the fileserver ran out of callback space and had to
prematurely revoke callback promises from clients in order to free up space.
This does not affect cache coherence or data correctness; but this can impact
performance -- for the clients who had their callbacks prematurely revoked,
these clients will now need to contact the fileserver again before using any of
those files. If those files were actively being used by the client, this can
cause more load on the fileserver, and file access on that client will appear
slower (since the client had to hit the network for the file, and could not use
its local cached copy).

Also of note are the _nFEs_, _nCBs_, and _nblks_ fields. The "nblks" field should be
the same as the current -cb option. If nFEs or nCBs ever exceeds nblks, that is
when the fileserver runs out of callbacks. So if you see nFEs or nCBs start to
get close to the "nblks" parameter, that may be cause for concern.
Unfortunately, current releases of OpenAFS (as of 1.6.2) do not record a
high-water-mark statistic for these values. So, the only way to track if you are
getting close to the limit is to periodically run the above xstat\_fs\_test
command. It is also possible to run xstat\_fs\_test easily on an ongoing basis;
see the documentation for xstat\_fs\_test for more information, or look at the
xstat library for creating your own statistics gathering tooling.

So, if you see the GotSomeSpaces counter rise, or you see nFEs/nCBs get too
close to nblks, it may be appropriate to raise the -cb argument to the
fileserver. The only downside to raising this option is the increased memory
usage. But the memory usage increase is quite small, about 64 bytes per -cb,
as of OpenAFS 1.6.2. In larger sites, -cb options in the millions are not that
uncommon.

In future versions of OpenAFS, the fileserver will also log a message in FileLog
when it runs out of callback space (gerrit 6334). However, this behavior has not
yet made it to current stable releases of OpenAFS (as of 1.6.2).

#### \-udpsize <socket buffer size>

This option dictates the size of the UDP receive buffer in the underlying OS. If
the fileserver cannot read packets from the wire quickly enough, the fileserver may drop
packets. Dropped packets can cause serious problems for read/write throughput performance.

The performance in this area was recently explored by Jakub Moscicki,  Dan van
der Ster, and Arne Wiebalck, all of CERN:

http://conferences.inf.ed.ac.uk/eakc2012/slides/CERN\_Site-Report.pdf

They found that the current defaults (as of OpenAFS 1.6.1), are generally not
sufficient for a highly-loaded fileserver, and should be increased to about
16MiB, at least at their site. This increase can be done via the -udpsize
option. Or on Linux this can be changed via the net.ipv4.udp\_\* sysctls.

In general, to see if the UDP receive buffer size should be increased, you can
see if the OS ever ran out of UDP buffer space when receiving packets. How you
do so depends on the underlying OS. On Linux, you can run 'netstat -su' and
look for the 'packet receive errors' statistic in the "Udp" section. On
Solaris, you can run 'netstat -s' and look for the "udpInOverflows" statistic.

If this statistic is rising over time, it may indicate that increasing the UDP
receive buffer would be helpful. And while this statistic alone does not say
that OpenAFS is the application losing packets, in practice OpenAFS processes
tend to be the only application on fileservers that are heavily utilizing UDP
traffic.  (On Solaris, it may be possible to see which specific application is
affected using DTrace, if you want to narrow things down further.) So, the
cause is likely to be related to OpenAFS.  The most likely candidates are the
fileserver and volserver, so you may consider raising this option on both. The
only downside in practice should be the additional memory usage.

#### \-vhashsize <hash size> (DAFS only)

The use of this option is only applicable to the Demand Attach File Server
(DAFS). If you're not using DAFS, this parameter is not configurable (and
non-DAFS fileservers don't generally need to configure this option). The use of
this option is generally only helpful when serving large numbers of volumes;
non-DAFS fileservers aren't capable of serving large numbers of volumes with
reasonable performance for other reasons.

This option controls the size of the hash table used for looking up
volumes in memory. If you specify '-vhashsize N', the size of the hash table
will be 2^N hash buckets. So, specifying 10 gives you 1024 buckets. If set too
low, fileserver startup and accessing volumes can take longer. And if set too
high, the hash table will use up more memory than is necessary. If you have a
large number of volumes on a fileserver (say, over a hundred thousand), you
should aim to make the number of hash buckets to be roughly around the number of
volumes you expect to be on that fileserver. So, for example, if you expect a
fileserver to serve somewhere around 200,000 volumes, try setting -vhashsize to
17.

#### Other options

Beyond the above, there are many more fileserver options which usually have
relatively minor impact on performance (you may see -s, -l, -b, and others).
Those will be covered in later articles in this series. However, the above
options should cover the most severe performance problems I've seen in recent
memory.
