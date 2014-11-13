---
title: Pending and desired OpenAFS projects
---

This page describes some of the projects that are currently known to be
in progress or discussed within the OpenAFS development community.  This
list is by no means complete.  Additional sources of information
regarding on-going and future plans can be found on the [road
map](roadmap.html) and the [Google Summer of Code](gsoc.html) pages.

Pending projects
----------------

The following are items known to be in progress, and, where available, a
point of contact.

Hierarchical Storage Management Integration

Provide support for storing AFS files into a HSM system (DMF is the
first targeted HSM system). Contact Ken Hornstein
(kenh@cmf.nrl.navy.mil) for more information. This project has been made
possible in part by support from SGI.

Disconnected AFS Operations

Provides the ability to use AFS while not connected to a network.
Significant work was completed during the 2008 Google Summer of Code and
currently resides in the OpenAFS Git repository as part of the
openafs-devel-1\_5\_x branch.  The current implementation is functional
for read/write volume operations but cannot support hard linked
objects.  There is also no method of pinning objects to the cache or
applying conflict resolution policies if the content of the volume on
the file changes while the disconnected client modified the same
objects.  Contact Simon Wilkinson (sxw@inf.ed.ac.uk) for more
information.

FreeBSD port

Server ported. Cache manager support is not yet complete.

NetBSD port

Server ported. No timeline available.

OpenBSD port

In progress. Cache manager works but not recommended for production use.

Better Documentation

In progress. On-going projects have produced a complete set of new [man
pages](http://www.openafs.org/manpages/), a replacement for the Unix
Quick Start Guide, and progress on a new Administrator's Guide.  Contact
Russ Allbery if you'd like to contribute

Kerberos v5 and multiple encryption types

In progress. Add Kerberos v5 and additional encryption type support.
Contact Marcus Watts or Matt Benjamin

RxUDP Improvements

In progress. Your File System Inc. was awarded a SBIR grant to improve
the performance characteristics of the Rx RPC mechanism.  During Phase I
many implementation deficiencies were corrected and maximum throughput
was raised from 60MB/second to 240MB/second. 

RxTCP

[In
progress.](http://workshop.openafs.org/afsbpw06/talks/kenh-rxtcp.pdf)
Implement Rx API on top of TCP/IP in order to gain performance on high
speed networks and improve the behavior of AFS across firewalls and
network address translators.  Ken Hornstein began the effort.  Contact
Jeffrey Altman for additional information.

HostAFSd

In progress. Implement an AFS server that exports portions of the local
file system to AFS clients. Contact Derrick Brashear.

Native Windows file system support

In Progress.  Implement AFS as a Windows Network Redirector and File
System Filter instead of as a virtual SMB server.  Contact Jeffrey
Altman and Peter Scott for additional information.

Better server preference support

In progress.  Allow selectable continuous or on-demand server
preferences in clients based on available information about Rx
connection round trip times instead of classful networking approach
currently used.  This project is being worked on by Jacob
Thebault-Spieker as a 2009 Google Summer of Code project.  Contact
Derrick Brashear (shadow@dementia.org)

Proposed projects
-----------------

The following are items which have been proposed, but which are not yet
in progress. A point of contact is included where appropriate.

IPv6 support

Make AFS support IPv6.

Multiple volume versions

Support for multiple "clones" of a single volume.

Selectable UBIK best host algorithm

Change lowest IP metric to something administrator-selectable.

Volume dump editor

Tool to allow editing volume dumps.

Partition UUIDs

Create partition UUIDs such that the vldb can be rapidly updated if a
disk is moved from one machine to another. Contact Derrick Brashear
(shadow@dementia.org).

Directory format extensions to support Unicode filenames

http://www.afsig.se/afsig/space/AFS+directory+format+extensions

Protection Server database extensions and RPCs

To support multiple security class authentication name to AFS ID
associations

