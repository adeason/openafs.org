---
title: OpenAFS Newsletter, Volume 4, Issue 6, October 2013
category: newsletter
layout: page
permalink: /newsletter/newsletter-2013-10-volume004-issue06.html
---

# OpenAFS Newsletter, Volume 4, Issue 6, October 2013

## /afs/Introduction

While long overdue, I am happy to present to you this current edition of the
OpenAFS newsletter. Valuing quality over quantity, newsletters are released
when we feel we have quality content for you to peruse. And, we certainly feel that about this edition of the newsletter.

The world of OpenAFS keeps plowing ahead, as you will read below with announcements concerning the first steps in retiring single DES and the up coming End of Life of the 1.4 series of OpenAFS.

In addition to our "Did You Know" tidbits, I am excited to present part II of "OpenAFS Tuning" as well as an overview of "tsmafs", a utility helping one to backup and restore AFS with IBM's Tivoli Storage Manager (TSM).

But first, the newsletter starts off with an update from the OpenAFS
Foundation working group.

Feedback, suggestions for future case studies and stories, and offers of contributing pieces should be emailed to: newsletter@openafs.org

Happy Fall!

## Update from the OpenAFS Foundation working group

	Roman Mitz
	Senior Manager, Systems Development
	Carnegie Mellon University

### Update

- A signed agreement has been struck between IBM and representatives of the Creation Committee.
- Our lawyers reviewed, then submitted the incorporation papers for The OpenAFS Foundation, Inc.
- The foundation has been created.
- A bank account has been opened.
- All funds remaining from previous years (not dedicated to the OpenAFS Workshops) have been transferred into the new bank account.
- Working on filing non-profit status with the IRS.

### Details

- Todd has been instrumental in facilitating the complicated process of getting a signed agreement and of having IBM agree that we may use the terms "AFS" and "OpenAFS" in the name and description of the Foundation.  This was a critical step in preventing potential legal issues over naming and terminology in the future, which many of us had been fearing and hoping to avoid.  Future agreements covering other aspects will likely have to be forged, but the first step has been done successfully.
- The firm's team reviewed what our group had compiled to-date as required materials going into the application package for the foundation of the Foundation.  OpenAFS Foundation, Inc., is now incorporated and marked as non-profit-to-be in the incorporation categorization.  This means that the Foundation now exists as a legal, independent entity.  For the purposes of the incorporation, all five of us had to be listed as preliminary directors, but we will hand over this role when the first true board members have been chosen.
- Also, Roman opened an independent bank account for the Foundation with the PNC Bank.  As the minimal number of authorized signors should be two, the Pittsburgh location was the logical choice.
- All moneys previously donated to the cause of OpenAFS were transferred from the previous account at CMU into the new bank account.  Funds for the current OpenAFS Workshops are kept separately in that existing organization.  We are happy that we could meet the fiscal year deadline by Carnegie Mellon, and all went smoothly.  These moneys are now available to the Foundation as operating funds.

### Next steps and how you can help

- The Creation Committee, after having procured a tax ID for the newly incorporated Foundation, will need to compile the packet of materials supporting our application for official non-profit status with the IRS.  It is the IRS that awards this status, if our application is approved; if the approval fails, we will have the opportunity to improve the organization and/or application and re-try at a later date.
- In the not too distant future, the preliminary board (i.e. Our Creation Committee) wants to hand over the baton to the initial Board of Directors.  Thus, we are seeking individuals with a proven track record of business success and with the good connections.  You may help us with suggestions or volunteering; resumes would be most helpful.  The Creation Committee can then contact viable candidates and invite them to serve pro-bono on our initial Board of Directors.

## Did You Know... krb5-auth-dialog

Krb5-auth-dialog is a nifty little application running in the Gnome desktop notification tray. Krb5-auth-dialog can auto renew Kerberos tickets, list existing Kerberos tickets, obtain new Kerberos tickets (via a single click), notify the user when Kerberos tickets are about to finally expire, and via a plugin also obtain and renew AFS tokens when obtaining or renewing Kerberos tickets. The application icon changes from a normal key when one's tickets/tokens are valid and auto-renewable to a key icon with a yellow exclamation when tickets/tokens are close to expiring to a key icon with a red X when tickets/tokens have finally expired.

At the Cornell NanoScale Facility, we now use the gui krb5-auth-dialog for GUI logins (replacing krenew, which is now only used for ssh logins) to display to the user his or her Kerberos ticket (and AFS token) status.

Krb5-auth-dialog's home page is at [https://honk.sigxcpu.org/piki/projects/krb5-auth-dialog/](https://honk.sigxcpu.org/piki/projects/krb5-auth-dialog/) . Please note that any version included with your favorite linux distribution may not include the AFS plugin.

## Single DES

Until OpenAFS 1.6.5/1.4.15, a major requirement of running an OpenAFS cell was
for the afs/cellname Kerberos principal to use single DES encryption of its
Kerberos tickets. Single DES has been long known to be weak, but for historical
reasons OpenAFS had continued to only support the DES encryption algorithm.

It was recently demonstrated that "the small size of the DES key space permits an attacker to brute force a cell's service key ... in under 1 day at a cost of around $100 using publicly available services". Once the key is compromised, the attacker can "forge traffic from any user within the cell." Including the AFS super user.

Enter rxkad-k5 and rxkad-kdf.

Rxkad-k5 adds support to OpenAFS for non-DES encryption of the afs/cellname
Kerberos principal's ticket. The administrator can use any encryption type
available to the KDC. However, the kerberos session key is still encrypted with
single DES.

Rxkad-kdf allows one to completely disable single DES on the KDC. With Rxkad-kdf, the Kerberos session keys are also no longer DES encrypted.

Once all OpenAFS server and clients are updated to 1.6.5, 1.4.15, or 1.7.26 on Windows and once rxkad-k5 and rxkad-kdf have been properly enabled and deployed on the OpenAFS servers (and afs/cellname Kerberos principal), the administrator can safely disable single DES on the KDC.

However, one should note that even with single DES completely disabled, communications encrypted between OpenAFS clients and servers still use single DES (the single DES key is derived from the stronger encryption types).

Additional documentation is available on the OpenAFS security advisories page at [http://www.openafs.org/security](http://www.openafs.org/security). See advisory OPENAFS-SA-2013-003.

This first major step in elimination of single DES is an exciting and positive
move forward for OpenAFS.

## OpenAFS 1.4 end-of-life process

OpenAFS 1.6.0 was released in September 2011, and since that time, the
OpenAFS community has focused on pushing the 1.6 series forward. The
OpenAFS project now considers 1.6 superior in terms of stability and
reliability for every AFS user and administrator.

Effective immediately, there will be no new tarball releases of 1.4.

For any future security updates to 1.4, the OpenAFS project will only
provide individual source-code patches. After May 4th, 2014, no
security patches will be issued for 1.4.

We encourage all sites to upgrade to the OpenAFS 1.6 series.

\-the OpenAFS gatekeepers



## Did You Know... OpenAFS RHEL YUM Repositories

If you use RedHat Enterprise Linux or Fedora Linux, you probably install the RPM packages for OpenAFS. Instead of downloading and creating your own local repository of OpenAFS RPMs, you can make use of 3rd party repositories or make use of the existing repositories directly off of the OpenAFS website.

One third party source is elrepo.org at [http://elrepo.org/tiki/tiki-index.php](http://elrepo.org/tiki/tiki-index.php)

To use the openafs.org website directly, you only need a working repository configuration file for YUM. Two good sources for the 1.6.5 release of OpenAFS are at:

https://wiki.ncsa.illinois.edu/display/ITS/OpenAFS+Install+via+RPM+for+RHEL+6

and

https://confluence.cornell.edu/display/CNF/Installing+AFS



## OpenAFS tuning, part II: /vicepX partitions

	Andrew Deason
	Senior Software Engineer, Sine Nomine Associates

In our last installment of the this series ( [http://www.openafs.org/pages/newsletter/newsletter-2013-03-volume004-issue05.html\#openafs\_tuning\_\_part\_i\_\_fileservers\_\_general](http://www.openafs.org/pages/newsletter/newsletter-2013-03-volume004-issue05.html\#openafs\_tuning\_\_part\_i\_\_fileservers\_\_general) ), we explored some of the solutions to
the more serious fileserver performance problems I've seen at various sites. Now
we'll start moving into tips for more modest improvements; while these
improvements are minor compared to the first installment, they are generally
more applicable to more sites, so it's more likely that each tip is relevant to
you.

For this specific installment, we'll be looking at tips related to the /vicepX
partitions on fileservers. This includes a few specific tweaks, and some
information about how /vicepX partitions are used.

As always, this article does not cover anywhere near all possible
performance-related options or tweaks. Stay tuned for more installments to
learn more.

### A few words of caution

It can be helpful to just go looking around in /vicepX to get a better
understanding of what goes on behind the scenes. You can see how the fileserver
interacts with what files by using the _strace/truss_ utilities and by looking at the fileserver's file
descriptor table ( _lsof_ on linux). However, if you do go looking around in /vicepX, __do NOT modify anything in there in any way. Do not modify any data, do not move files around, and do not even chmod/chown anything__. Doing any of those can cause data loss or
cause a volume to become unusable; if you accidentally do something like that,
you should probably salvage the partition to try to correct any breakage.

This installment assumes you are using "namei" fileservers. Fileservers using
the "inode" storage backend are beyond the scope of this article, and are
relatively uncommon these days. If you are not sure which you are using, you're
probably using "namei". While "inode" servers are actually faster, making them
work becomes more difficult as time goes on, and I personally have not had to
deal with any "inode"-specific issues in some time. Some parts of this
installment may be completely wrong for "inode" servers.

### /vicepX filesystem tuning

Since various systems and filesystems vary so much, we cannot hope to provide
exact commands or configuration directives to implement some of these
recommendations. Since this is more of a high-level guide, some tips may mention
optimizing for large files, or optimizing for reading/writing in certain sized
chunks. If no more detail is provided, it is up to you to figure out how to do
that for your particular system.

### Straightforward tweaks

Most systems have a way of mounting a /vicepX partition with the 'noatime'
option, to turn off updating the 'atime' status information whenever a file is
accessed. This is generally a good idea for any filesystem, unless you have some
application that requires 'atime's to be correct. OpenAFS
servers never pay attention to atime, so feel free to turn it off.

Some filesystems, such as Linux's ext\* filesystems, have the option of turning
on or off directory indexing. Regardless of the directory structure inside
volumes, the directories inside /vicepX can get quite large, and OpenAFS almost
always looks up files directly (instead of traversing directory contents). So,
if given a choice, you should turn on directory indexing (so that /vicepX file
accesses are faster).

On systems that have a configurable Directory Name Lookup Cache (DNLC) size
(such as Solaris), you may want to increase the DNLC size from the default,
since the fileserver will cause a lot of lookups in /vicepX if you have a lot
of files. On Solaris, you can check the DNLC hit rate with:

	$ vmstat -s | grep lookups 572512236 total name lookups (cache hits 95%)

and the DNLC size can be changed by altering the 'ncsize' kernel parameter.

### When AFS is the same as local disk

One question that I hear often when talking about performance is "What workload
should I assume when tuning vice partitions?" The easiest answer to this is that
you should generally tune the filesystems the same as if you were accessing your
files on local disk, without AFS.

There are many filesystem and mount options not covered here that are not really
specific to AFS. For example, increasing the commit interval on Linux may
improve performance, but may cause you to lose data that was written longer ago
than the commit interval during an unclean shutdown. That may or may not be
acceptable to you, but it doesn't have much to do with whether you're running
AFS or just using local disk. Many options are similar.

When tuning the filesystem for file size and access patterns, many things are
also still the same for AFS as local disk. Regular files in AFS are stored
inside /vicepX as entire regular files, so there is not much special about
these files.  That is, if you put a PNG file inside a volume in AFS, there will
be a file inside /vicepX on the relevant fileserver that will be that exact PNG
file. The filename will be different, and the file will be inside a
weird-looking directory structure, but the file contents themselves are
identical.

So, this means if you have a volume with lots of tiny files, the /vicepX
partition for that volume ideally would be optimized for lots of tiny files. If
you have huge files, the /vicepX partition should be optimized for huge files.

### When AFS is different

However, of course, there are some differences between accessing files on local
disk and accessing files in AFS via a fileserver. One difference is that,
currently, directories are stored in /vicepX as regular files that are
relatively small (between 2KB and about 2MB, depending on how many directory
entries the directory has). One such "directory" file will exist for every
directory in the volume, which you may want to consider if optimizing the
/vicepX filesystem for file size. This may be slightly different than
optimizing a directory tree on a regular filesystem, since some filesystem
implementations may behave slightly differently when modifying/accessing
directory objects vs plain files. If you have a volume full of mountpoints or
symlinks, keep in mind that each mountpoint or symlink is also stored as a very
small file on the fileserver.

Another difference is file access patterns. Obviously, file server access
patterns will be different due not only to the caching nature of AFS but also
due to the differing directory structure on disk. We almost never walk the
directory structure (walking only occurs during salvaging and certain 'vos'
operations); even if a client runs 'ls -lR', this still results in just reading
regular files and in regular directory lookup operations (since our directory
objects are stored in regular files, and processed by clients).

For considering block sizes / record sizes / etc, the actual sizes used by
client application read() and write() calls don't usually matter. At least
current Unix OpenAFS clients will only ever read or write to regular files on
the fileserver a _chunksize_ at a time (assuming the file is at least as large
as a chunk). So, if a client is configured with a 1 MB chunksize, the client
will only write to files 1 MB at a time. If you don't have any control over
clients, modern Unix clients will typically default to between 256 KB and 1 MB
(or as low as 8 KB for memcache clients).

Within that chunksize limit, the fileserver will issue individual read() or
write() calls in _\-sendsize_ chunks. That is, if -sendsize is set to 32 KB,
the fileserver will read()/write() up to 32 KB at a time for a single client
chunk.

Tuning a filesystem to account for those patterns is specific to each
filesystem. Since performance bottlenecks are often found in different parts of the AFS environment, depending on usage you may not notice any performance differences when tuning the
above.

### /vicepX partitions

Usually, how many /vicepX partitions you have doesn't matter that much, so
administrators tend to create one per physical disk, or per LUN, or per zpool,
etc. However, some server operations are limited per partition, due to a
per-partition lock that needs to be held for some operations. Additionally, if
you've ever looked inside /vicepX, you may have noticed that there is a header
file for each volume that exists on the partition; if you have a lot of volumes
in a partition, the /vicepX directory can grow quite large. So in some cases,
spreading volumes out amongst more /vicepX partitions can be helpful, even if
the number of physical disks/LUNs/etc did not change.

The server operations that may be affected by spreading out volumes over
/vicepX partitions are: server startup (primarily DAFS), server shutdown
(primarily DAFS), volume creation, volume deletion, listing volume information,
and salvages (primarily non-DAFS).  Performance of normal client<->fileserver
reads and writes is generally not affected.

There aren't any easily-viewable metrics to look at to see if you could improve
performance by changing the number of /vicepX partitions, but it's something to
keep in mind if the server isn't going as fast as you would like when performing
lots of the above operations in parallel. You're probably more likely to be
visibly impacted by DAFS startup time than any of the other operations, so this
is one likely thing to look at if that startup time is taking too long.

### More to come

That's all for Part II. Look for Part III in a future OpenAFS Newsletter!

## AFS backup to TSM using tsmafs

	Anders Magnusson
	Consultant/Happy Hacker

TSM (Tivoli Storage Manager) is a very common backup system from IBM. However, backing up AFS with TSM can be a challenge. There were two main existing ways to backup AFS with TSM backups. The first was to do a "vos dump" that was stored in TSM as one or more files. The second was to use the IBM AFS backup client. The IBM client, however, is only supported on an old version of TSM and also requires an AIX TSM server.

Neither of these was good enough for us. Hence, we wrote the tsmafs backup client.



### TSM peculiarities

TSM is quite different in how it works compared to most other backup systems.
It stores individual files instead of partition dumps and keeps track of
versions and numbers for each file. This means that an individual user file can
be directly retrieved out of TSM without the need to restore a parition dump
first and then extract the file.  This also means that no duplicate data is
stored in TSM (on file level), since a file that is backed up will not be
backed up again until it is modified.

The last version of a file that is backed up is set "Active", and all older
versions of the file are set "Inactive". When a file is deleted from AFS space,
all versions in TSM are set "Inactive". Only "Inactive" files are subject to be
removed from TSM when the time or version is passed.

TSM uses a hierarchy of four levels to keep track of and to keep files
together.  This hierarchy must be mapped to the AFS structure in a convenient
way. Our requirement that AFS volumes must be able to move around servers
without affecting the backup system resulted in the below schema:

	TSM name                Normal fileserver       AFS structure
	-------------------------------------------------------------
	NODENAME                Server name             "OpenAFS" (can be overridden)
	FILESPACE               Partition               Cell name (can be overridden)
	High-level name         Path in partition       Volume name/Path in volume
	Low-level name          Filename                Filename

Using the tsmafs utilties first requires the following steps:

### Tsmafs first steps

- Compile and install tsmafs on a machine with the AFS client.
- Create (via the usual tsm tools) an environment that uses _password=generate_, so that the
tsmafs programs don't have to care about tsm auth.  Use the same TSM nodename in
TSM even if you have multiple AFS file servers, so that a moved volume will be
backed up only once.
- Fetch an AFS token for an user that has enough power to read the volumes
that shall be backed up.  This can be, for example, a backup user that belongs to the
system:administrators group.

### Using tabackup

The utility _tabackup_ is used to fetch files out of AFS space and then to store
those files into TSM.

Tabackup only reads AFS backup volumes -- it does not create them. So, you must first create your AFS backup volumes with a command such as "vos backupsys".

Overview of the (most useful) options to tabackup:

- \-v volume

Only backup volume "volume" -- "volume" can contain wildcards, like "staff.r\*",
and the wildcard globbing uses the same syntax as the shell.  If no volume
given, take all volumes. Only one -v argument allowed.

- \-s server

Only backup volumes from AFS "server". The default is all AFS servers.

- \-f filespace

Store volumes in "filespace" instead of the cell name.

- \-p partition

Only backup volumes from AFS "partition". The default is all partitions.

- \-n

Do everything except commiting files to TSM by aborting the transaction before the TSM commit.

- \-i

Only set files inactive, do not backup anything.

- \-I

Do not set files inactive even if they are missing.

- \-x name

Exclude file or directory named "name" from backup. Useful if people want to
store large amount of data without backup in specific sumdirectories (like
"nobackup"). A max of 10 -x options can be given.

### Using tarestore

The utility tarestore is used to retrieve files from TSM. Tarestore cannot create
AFS volumes itself but instead only restore in paths from the current position. Tarestore will
restore Unix permission bits as well as AFS ACL's.

Overview of the (most useful) options to tarestore:

- \-v volume

Restore "volume" from TSM.  Must be given.

- \-f filespace

Restore from "filespace". Must be given.

- \-t time

Set PIT (point-in-time) to "time". Shall be given in ISO format. If not given, use the latest versions.

- \-q

Only query about files, do not retrieve them.

- \-h highlevel

Give the path starting with '/' for the file to find. May contain wildcards (parsed by TSM).

- \-l lowlevel

Give the file name to find.  May contain wildcard.

The _h_ and _l_ options are very useful when helping users. Not uncommon are
questions like "I had a file named 'foo' something seven days ago somewhere in
my home directory, can you restore it for me?". So, just use "-h /\* -l /foo\*" (and
reasonable PIT and volname) and tarestore will find it for you. Easy!

### TODO

There is much functionality that should be added to tsmafs. For example, we would like to do interactive
restores in the same way as the unix restore utility works. As with any software project, there are probably also a large number of bugs needing to be fixed in tsmafs.

### Downloading

As of this writing, the latest version available is: /afs/ltu.se/misc/tsmafs/tsmafs-0.2.tgz
