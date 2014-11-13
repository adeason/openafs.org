---
title: OpenAFS and Google Summer of Code
---

OpenAFS is a 100% open source globally distributed file system derived
from IBM AFS commercial offering as of 1 November 2000.  Since IBM
released the source code OpenAFS has thrived adding support for new
platforms while enhancing its overall performance, scalability and
usability. 

GSoC 2009
---------

For 2009, OpenAFS has been granted 4 slots. The projects which we
accepted for 2009 are:

1.  Project \#1: Microsoft Management Console: The project is to build a
    Microsoft Management Console to manage OpenAFS settings. This is
    already part of the OpenAFS roadmap on Windows and something I am
    interested in regardless of Summer of Code. Right now, settings for
    OpenAFS can be controlled through the OpenAFS control panel or
    through direct registry modification for some settings. Using the
    control panel does not work well for managed environments, and
    direct registry modification is prone to user errors.

    The solution is to leverage the MMC API to build a console for
    configuring OpenAFS. Issues to be address are whether to use the MMC
    2.0 API or the MMC 3.0 API. The difference is that MMC 3.0 is
    managed and provides better error handling. The management console
    is essentially a user interface for the appropriate settings, so it
    is not tightly coupled to the existing OpenAFS source code.

    From there, the user interface needs to be constructed. There are
    already sample screenshots in the OpenAFS for Windows roadmap as a
    starting point. Once there is a user interface, actually reading and
    writing the settings while leveraging elevation in Windows Vista as
    necessary is the next step.

2.  Project \#2: OpenAFS as a data-driven filesystem. The goal of this
    project is to enable tagging and searching metadata of items in the
    AFS filesystem.
    Assumptions: single filesystem (server) support, assume interfacing
    with existing search tools. An indexer, a search service, and
    documentation and testing with by byproducts of this service. Index
    data should be mobile with the volume data and stored in a manner
    which allows ready access from new services. Lucene is being
    investigated for use in this project.
3.  Project \#3: OpenAFS server preference based on network conditions:
    The OpenAFS cache manager keeps two lists of which servers, the list
    of VLDB servers and the list of file servers. The VLDB server
    prioritization list is derived from the CellServDB or AFSDB DNS. The
    list of file servers is provided by the VLDB, and contains the list
    of servers hosting a requested volume. The order of these lists is
    currently decided based on the outdated assumption that the networks
    will be classful in nature. Unfortunately this type of
    prioritization is no longer useful with current networks, as the
    Internet is no longer classful. This leads to an all but random
    prioritization list.
    This project seeks to change the way the servers in the list are
    ordered based on network conditions between the client and the
    possible servers. Rx peer statistics can help provide information
    about these network conditions. Parts of these statistics can be
    used to indicate which servers are closest, proximity-wise, to the
    client as well as create an estimated throughput capacity for the
    server. These factors can be analyzed to represent performance
    between the cache manager client and the servers. This will allow
    for server prioritization based on the best performance of the
    server and the server's network connection, which subsequently can
    increase access times. This project will implement this
    prioritization on both Windows and Unix platforms, taking into
    account the statistics mechanisms. The Unix implementation will port
    relatively simply to other Unix implementations (AIX, HP-UX, etc.).
4.  Project \#4: Implementing OpenAFS features into the Linux kafs
    kernel module: kafs is a Linux implementation of the AFS protocols.
    While kafs has been maturing, many features contained in OpenAFS are
    still missing from kafs. This project aims to add some of those
    features.

    -   DNS AFSDB support. Sharing the mechanism used by CIFS will be
        investigated.
    -   A common pioctl interface. Sharing a pioctl interface between
        kafs and OpenAFS to allow sharing of userspace binaries such as
        fs.
    -   Implement OpenAFS file system commands. Add support for some
        OpenAFS commands that have not yet been integrated into kafs.
    -   Keyring compatibility. Making a standard keyring implementation
        that would allow the client to obtain authentication tokens that
        would work for both kafs and OpenAFS.

### GSoC 2009 recruiting

It is now 2009, the world economy is collapsing, the U.S. dollar has
regained much of its value against other currencies and we suspect that
many of you are thinking about how nice it would be to have US\$4500.00
in your bank account (or perhaps under your mattress) at the end of the
Summer.  If you are considering applying to OpenAFS for a Summer of Code
project and have not already read the [GSoC 2009
FAQ](http://code.google.com/opensource/gsoc/2009/faqs.html) we suggest
that you do so.

As we indicated last year "OpenAFS is a very large and highly complex
software project consisting of close to one million lines of source code
that is severely under-documented.  As a result it takes a long time for
any developers to become proficient contributors to the core systems." 
We discovered during 2008 GSoC that the time it takes for new developers
to come up to speed is even longer than we expected, especially when the
developers have little real world experience working on large system
projects.  Here are some of the things that make OpenAFS development
particularly challenging:

1.  multi-operating system support.  Many operating system APIs are not
    portable between operating system.  OpenAFS includes support for a
    wide range of platforms.  As a result the source code can be quite
    confusing to read.
2.  multi-threaded programming.  OpenAFS makes extensive use of
    multi-threading.  Developing thread-safe code is a challenge for the
    most experienced developers.  It will take a while before you get
    the hang of it.
3.  Kernel programming. Portions of OpenAFS are implemented as kernel
    modules. Developing these can be particularly challenging, as code
    errors can crash the entire machine. Working effectively on kernel
    code will require access to a second machine, or to virtualization
    software.
4.  Distributed systems.  OpenAFS is a highly distributed system with
    clients and services running on multiple machines communicating over
    an esoteric remote procedure call system called Rx. This means
    there's added complexity due to the potential for your work to
    result in mismatches among disparate pieces.
5.  Lack of User Experience.  Unlike a web browser or a game, you aren't
    likely to simply download OpenAFS and configure a working OpenAFS
    cell in under 30 minutes so you can experiment with it. 
    Understanding an application and how it works is crucial to being
    able to develop additional features and functionality that can be
    added to the system. In order to successfully develop for OpenAFS
    you will need to be able to get the components you are developing
    running yourself. 
6.  Infrastructure dependencies.  To deploy a working AFS cell you must
    also have a working DNS and Kerberos deployment.  It is very tricky
    to setup a complete set of OpenAFS client and services on a single
    laptop for the purpose of development.
7.  Programming Languages: OpenAFS is written almost entirely in C (and
    the user interface on Windows is C++) with all of the issues
    surrounding memory allocation and deallocation, pointer
    manipulation, stack management, memory leaks, buffer overruns, etc. 
8.  The mix of Version Control Systems, Debuggers, Build Systems, and
    other development tools will likely be unfamiliar to you. 

Not all of these challenges will apply to all GSoC projects.  In fact,
we have selected project proposals that we believe are manageable by
many students. If you are unsure about any of the above challenges,
OpenAFS has an active and friendly community that will be happy to
provide you with help and guidance. Please join us on \#openafs on
freenode, or openafs@conference.openafs.org on Jabber

Even though OpenAFS is challenging to get familiar with it can be a very
rewarding experience; OpenAFS's functionality offers a chance to learn
many features, concepts and tools, nearly any of which singly could help
you develop your career.  If you are interested in working on OpenAFS
this Summer (and perhaps for the rest of your life) here are some things
that we recommend you do:

1.  If you are unfamiliar with programming in C, see if your University
    has any resources available for assisting their students who want to
    learn C.  If that is not possible, get yourself a good book and try
    your hand at it. "The "C Programming Language, 2nd edition" by
    Kernighan and Ritchie is widely considered to be an excellent
    reference text.
2.  If you have no idea what multi-threading is or what mutexes,
    read/write locks, or critical sections are, go to the library and
    find yourself a book.  Preferably one that does not specialize in
    Java, Win32 or Posix threads, but a good general multi-threading
    text book.  (Search Amazon and read reviews)
3.  Read the IBM AFS documentation.  We are very sorry that it has not
    been re-written to fully describe OpenAFS.  If writing documentation
    were a permitted GSoC project we would put it high on our list but
    unfortunately its not.
4.  Try your hand at building your own DNS, Kerberos and AFS
    infrastructure.  ["Distributed Services with
    OpenAFS"](http://tinyurl.com/cexwea) is an excellent cookbook that
    walks though all of the steps necessary to get all of the pieces up
    and running.

If you apply to OpenAFS please be aware of the following:

1.  You may not have a second job when working on OpenAFS GSoC.  We
    expect a minimum of 30 hours a week of dedicated work on your
    project.  It is likely that you will need to spend significantly
    more time than that when you include all of the time spent
    communicating with your mentor(s) and the community and learning all
    of the things you do not realize you do not know yet.
2.  You must have excellent network connectivity on a regular basis.  It
    is going to be extremely hard to develop for a distributed network
    file system without access to the Internet.  In particular, you are
    going to need to be able to access source code repositories,
    Kerberos KDCs for authentication, and OpenAFS services.  This will
    require that a broad range of udp ports be open for access to the
    external world.  If you are dependent upon your University's network
    and they firewall access to the outside world, it may be very
    difficult or simply not be possible for you to work on OpenAFS. 
    Access to Jabber conference rooms and IRC for communication with
    your mentors and the community are critical.
3.  You must know how to compile a C program and use a debugger at a
    rudimentary level.  For Linux, gcc and gdb.  For Windows, Visual
    Studio 2005.
4.  The time that our mentors spend working with you on a GSoC project
    is extremely valuable.  Mentors have significant work of their own
    that must be completed.  If you are having a problem, communicate it
    early so that it can be addressed.  If you promise to deliver
    something, do so or warn your mentor as soon as you know that you
    will miss the promised delivery date.  If your mentor is not
    available, ask on the IRC channel or the Jabber conference room,
    there are many members of the community that can help.  The OpenAFS
    community will do everything we can to make GSoC a success for you,
    if you put in the effort at the work and the communication, but we
    will fail you if you're not putting that effort in.

Communicating with the OpenAFS Community regarding GSoC
-------------------------------------------------------

You can speak to members of the OpenAFS Community using two forums:

1.  Jabber Conference Room: openafs@conference.openafs.org
2.  Internet Relay Chat: freenode.net \#openafs channel

You may also engage the community via our mailing lists.

AFS & Kerberos Workshop
-----------------------

This year's [AFS & Kerberos Workshop](http://workshop.openafs.org/) is
being held at Stanford University the week of June 1 to 5.   A students
working with OpenAFS for Summer of Code are given free admission to the
tutorials and workshop sessions.   The workshop is an excellent
opportunity to meet the community and learn more about how OpenAFS works
and how it is used.

Project Ideas
-------------

The following are a list of project ideas that members of the OpenAFS
community believe are not only interesting challenges that can be
completed over a Summer but that will provide a much needed feature or
function for OpenAFS end users and administrators.

### 1. Prototype a User Interface for Managing Disconnected Operations

In GSoC 2009, Dragos Tatulea worked with Simon Wilkinson to implement
[read/write disconnected
operations.](http://workshop.openafs.org/afsbpw08/fri_1_3.html) With
disconnected operations the contents of the AFS Cache are available for
use even when it is impossible to communicate with the AFS file
servers.  The challenge for this project is to prototype on Linux or
MacOS X a user interface that will permit a user to specify which files,
directories or volumes are to be available for disconnected use at all
times and which other objects are available for disconnected use as a
side effect of the objects being cached due to recent use.

### 2. Unix or Windows Cache Manager support for Apple Doublefiles (Extended / Posix Attributes)

In order to store arbitrary metadata (aka attributes) with files or
directories in file systems that do not have the necessary native
support Apple developed the [Apple
DoubleFile](http://users.phg-online.de/tk/netatalk/doc/Apple/v2/AppleSingle_AppleDouble.pdf)
format.   AFS does not support arbitrary metadata and on Apple MacOS X
systems, the operating system will create DoubleFiles without additional
support from the AFS Cache Manager.  This project is to implement native
support for Apple DoubleFiles in one or more of the AFS Cache Managers
exporting Posix Attributes on Unix/Linux platforms and Extended
Attributes on Microsoft Windows.  This will permit arbitrary metadata
(for example, icons, thumbnail images, author, copyright info, gps tags,
etc.) to be stored in AFS and shared across multiple operating systems
without requiring changes to the AFS file servers.

### 3. AFS as a Data Driven File System

A challenge of today's data driven computer world is the explosion of
digital data. Somehow this data must be managed and organized. Many
digital document repositories, while good at storing associated metadata
about the documents, do not have an efficient metaphor for working with
the data. Most filesystems, on the other hand, while good at allowing
one to work with the files and data itself, do not have an efficient
metaphor for searching and managing the extended metadata attributes.
And while extended attribute conventions do exist, the extended
attributes are usually not applicable to network filesystems and are
usually not easily searchable.

The overall goal of this project is to extend OpenAFS to both store
extended metadata attributes and to allow one to easily work with and
search these attributes. Corollaries include ease of use client side
tools.

Phase 1 involves prototyping how to design such a system. A system might
be modeled after existing filesystems like HFS+ and ext 2/3 by using the
POSIX extended attributes API as is. Or, a system might embrace the
existing POSIX api while also offering new functionality.

Phase 2 involves implementing the storing of extended attributes in the
filesystem. One might begin working with apple double files, which do
not require modifying the file server, volume headers, or the afs
clients. One can also use existing commandline tools (or easily write
new ones) to work with the extended attributes themselves.

Phase 3 assumes all volumes on a single file server. The student will
work on a backend to collect the metadata and to make the metadata
searchable. This phase includes thinking about keeping track of changes
to file locations, names, and attributes/metadata.

Additional areas of research would involve expanding to a distributed
database scheme for multiple file servers as well as modifications to
afs itself to more natively store the extended attributes in the
filesystem/volumes.

The student should have existing skills in relational database design
and in the C programming language. Work will most likely be done on the
Linux platform.

### 4. Microsoft Management Console for Windows Client Configuration

OpenAFS on Windows has a very out of date Control Panel application that
is used to configure the AFS Cache Manager service.  In addition to
being out of date, the Control Panel is not the appropriate user
interface model for configuring a system service.  On Microsoft Windows,
system wide services should be configured using the Microsoft Management
Console (MMC).  This project is to implement a MMC Add-on for the
OpenAFS Cache Manager.

Mockups of a proposed MMC user interface can be found at
[http://www.secure-endpoints.com/openafs-windows-roadmap.html\#client
service
mmc](http://www.secure-endpoints.com/openafs-windows-roadmap.html#client%20service%20mmc). 
This project consists of multiple components that can be successfully
implemented one at a time.  The successful completion of this project
does not require that all of the proposed MMC pages be implemented.

This project does not require any prior knowledge of AFS nor any
knowledge of OpenAFS internals.  By completing this project the
developer will become an expert in the Microsoft Management Console
interfaces and the Microsoft Component Object Model (COM).  This
experience can be reapplied to numerous other applications and will
prove to be an excellent item on a resume.

The programming language for this project is C/C++.  The operating
system is Microsoft Windows.  The project will aim to support Microsoft
Windows versions from XP SP2 to Vista/Server 2008.

### 5. Read/write volume replication

OpenAFS currently provides readonly replication of data. Many sites
would like to use replication on all their data. A proposal exists to
address this, however, no work has yet been done on implementation.

The goal of this project is create readwrite replication for OpenAFS.
The proposal can be read
[here](http://www.student.nada.kth.se/~noora/exjobb/filer.html) and we
are available to answer questions about anything further. Experience
with systems and network programming is highly desirable, however,
experience with OpenAFS is not necessary.

A student choosing this project will be able to list on a resume and
apply the skills necessary for developing network-distributed systems,
especially with regard to file systems.

 Last year's GSoC project offers code and information which should help
you understand what's already done and what pieces remain for you to
implement to complete this functionality.

### 6. OpenAFS ptserver extensions for additional authentication types

In order that authentication systems other than Kerberos 4 be able to be
first class authentication systems in the OpenAFS space, extensions to
the OpenAFS protections service need to be added.

More detail on this project can be found
[here](/developers/gsoc/pts.txt).

For successful completion of this project, both the RPC additions and
database extensions will need to be completed.

This project does not require any prior knowledge of AFS nor any
knowledge of OpenAFS internals.  By completing this project the
developer will become an expert in the OpenAFS ubik database structure
as well as in the OpenAFS Rx RPC system.  This experience would prove
valuable in dealing with other flat database formats, as well as other
RPC systems used in distributed applications.

The programming language for this project is C.  This is in portable
code which can be run on any POSIX-compliant OS; While MacOS, Linux or
Solaris are suggested as development platforms due to availability of
debugging tools, any supported OpenAFS platform could be used to do this
work.

### 7. Per-file Access Control Lists

Code implementing per-file ACL permission checks on RPCs received at the
server was substantially completed.

AFS supports advanced file permissions, using Access Control Lists
(ACLs) on directories. The traditional AFS permission model is, however,
showing signs of age. The AFS model is inflexible for administrators,
who must store objects with disjoint permissions in separate
directories. The AFS model is also inconsistent with POSIX ACLs (POSIX
1003.1e/1003.2c), DCE DFS, CIFS, and NFSv4
(http://www.ietf.org/rfc/rfc3530.txt), all of which allow ACLs (of
varying types) on a per-file basis. Implementation of this feature will
improve the usability of OpenAFS for administrators, and improve its
interface with modern platforms.

The objective of this SOC project is to more fully specify and then
implement a per-file ACL mechanism for OpenAFS. Engaging with the mentor
and the community, the student will work out details of per-file ACEs,
relationship of per-file and existing per-directory ACLs, select an
on-disk representation for this design in the OpenAFS namei file server,
and, minimally, expose the new representation to clients via the AFS
file server protocol (its FetchACL RPC and supporting code, eg,
RXFetch\_AccessList). The project will close with a validation testing
phase.

This project will provide an interested student with an opportunity to
engage with the OpenAFS codebase and development community in a
significant way, in both design and detailed implementation. The student
will gain exposure to the complete operation (and end-to-end
enhancement) of a major file-system features--from on-disk
representation to remote procedure invocation, to manifestation on the
client.

The student should have existing skills in C program implementation in a
Unix environment, and have minimally completed University courses in
data structures and algorithms, preferably in C.

More detail on this project can be found
[here](/developers/gsoc/acls.txt).

### 8. Implementing OpenAFS features into RedHat's kafs kernel module

The goal of this project would be to bring the Linux kernel kAFS client
as close to feature-parity with the existing OpenAFS port as possible.
Examples include:

-   DNS AFSDB being able to obtain cell server location without using
    configuration files.
-   A common pioctl implementation between kafs and OpenAFS to allow
    sharing of userspace binaries.
-   Making a standard keyring implementation that would allow the client
    to obtain authentication tokens that would work for both kafs and
    OpenAFS.
-   Implement some of the OpenAFS file system commands that have not yet
    been integrated into kafs.
-   A way for OpenAFS and kafs to be running on the same machine using
    different port numbers.
-   Complete the kafs callback interface.

Last year's GSoC project produced partial documentation of the pioctl
functions available through AFS, a pioctl syscall and VFS entry point
for the Linux kernel and implemented some pioctls for the kAFS call..

### 9. Simple Volume and Namespace Management System

Develop a simple Volume and Namespace management system on top of
OpenAFS. OpenAFS can be leveraged to create complex namespaces, and it
is an effective wide-area file system. However, determining exactly how
to configure OpenAFS to scale well across a wide area can be complex.
This project will take a few specific scenarios and develop
parameterized configurations for them that can then be used by OpenAFS
users as blueprints. Specific example: create a single namespace split
across two locations, with tools to manage synchronization and
replication according to some basic policies on who can invoke
replication and how to control the bandwidth utilization.

### 10. Path MTU discovery

OpenAFS uses a UDP based RPC transport called Rx. uses the endpoint
maximum transfer units (MTUs) to determine how large of a packet may be
transmitted without requiring the packet to be broken into fragments on
its journey. The prevalence of IP tunnelling, typically with reduced
MTUs, on modern internet tpographies, means this is often not an
accurate way to determine true maximum packet size. This project would
develop and integrate into Rx a mechanism to discover the MTU of the
path rather than merely the endpoints, resultingly tuning packet sizes
accordingly.

### 11. UPnP support

Network Address Translation, or NAT, is now very common on IPv4 networks
due to inavailability of IP space. Port mappings to edge clients,
especially for UDP, often do not persist, and there are no well-known
mappings to clients behind the NAT device. This sometimes causes
problems with the AFS protocol's use of reverse RPCs to communicate
conherency information. One technology for registering edge usage of
ports is Universal Plug and Play, or UPnP. While not all appliances
support it, integrating use of it into OpenAFS clients would offer great
potential to improve the client experience for users. A project in this
space would develop a new UPnP implementation or utilize a
license-compatible implement along with additional work to integrate its
use into the existing OpenAFS client codebase.

###  12. Surprise Us

Anything else that you want to submit.  Speak with members of the
OpenAFS Community and brainstorm.  Several students from GSoC 2008 or
current Capstone projects have discussed their own idea and we are
looking forward to their submissions.

In 2008 OpenAFS participated in Google's Summer of Code.  [Here are the
projects that were suggested and what transpired.](/developers/gsoc/2008final.html)
