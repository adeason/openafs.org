---
title: Development Wish List / Road Map for OpenAFS
---

In its ten plus years as an open source project, OpenAFS has established
AFS as an open source success stories.  OpenAFS provides clients for all
of the major operating system distributions and servers on all
UNIX/Linux variants.  Even so, there is still a great deal that must be
finished in order for AFS to acheive first class status on MacOS X and
Microsoft Windows.

The work to be accomplished on OpenAFS falls into six broad categories:

-   [Core Client Functionality](#core)
-   [Human Interfaces](#HI)
-   [AFSv3 Remote Procedure Call Extensions](#protocol)
-   [Server Enhancements and Management Tools](#server)
-   [High Performance Computing Extensions](#HPC)
-   [Miscellaneous](#misc)
-   [Documentation](#documentation)

It is the goal of the OpenAFS Elders to raise resources from the OpenAFS
Community and others to successfully implement all of these functions
over the next three to five years.

An [Implementation and Release Schedule](#release_schedule) is provided
at the end of the page.

A note about the estimates provided on this page.  For many of the
projects the Gatekeepers have designs, partially completed work, or even
fully implemented systems.  The estimates that are provided is the time
necessary to complete the project and/or integrate it into a standard
release of OpenAFS.

1. Core Client Functionality
----------------------------

Core client functionality encompasses the AFS cache manager, file system
interfaces, pioctl interfaces, and credential management.

### Microsoft Windows:

The Microsoft Windows client has received significant attention over the
last four years.  It is a fully functional client that works on all
Microsoft Windows releases from Windows 2000 SP4 through Windows Vista
and Server 2008.  For a summary, see the [OpenAFS for Windows Status
Report](http://www.secure-endpoints.com/#oafw_status_report).  Still,
there are a number of deficiencies that adversely impact the ability of
end users to use AFS to its full existing potential.

-   **Read-only or Read-write disconnected mode:**\
     Microsoft Windows users are used to the "Windows Offline Folders"
    functionality which permits them to synchronize local copies of
    files or folders from a CIFS server to their local disk for use when
    disconnected from the network.  UMichigan long ago implemented a
    read-write disconnected mode for the UNIX AFS client which permits
    users to continue using data within the AFS cache while in an
    offline mode.  Once the client is restored to an online state the
    modifications made to the cache buffers are written back to the file
    server provided that there are no conflicts.   If there are
    conflicts a manual conflict resolution process must be initiated. 
    Conflict resolution is hard but AFS users would gain a great deal
    even if the contents of the AFS cache were available when
    disconnected from the file servers in a read-only manner.\
     Estimate: 3 months\
    Status: no resource commitments

### All UNIX platforms:

-   **read/write disconnected AFS:** \
    Read-only and partial read-write operational support is present in
    the 1.5 release series.  Additional work needs to completed to
    support hard links, conflict resolution, and pinning of objects,
    directory trees or volumes.\
     Status: core functionality substantially complete on Unix platforms
    except for pinning and user interface issues.\
    \
-   **intermediate fileserver - client as fileserver:**\
     Each AFS cache contains up-to-date copies of data when a callback
    is registered with a file server.  In a cluster of clients that are
    reading the same data over a low bandwidth network, it would be more
    efficient if the AFS cache manager could obtain data from a nearby
    up-to-date copy as opposed to reading it from the file server on the
    slow link. \
    Estimate: two to three months.  Requires protocol standardization\
    \
-   **prevent repeated queries of the same volume location data:**\
     The UNIX client does not prevent multiple threads from repeatedly
    querying the same volume location data.\
    \
-   **O\_DIRECT and O\_SYNC:**\
     These fopen flags should be supported.  O\_SYNC should force each
    write to block until the data is sent to the file server.  O\_DIRECT
    should perform a direct write to the file server bypassing the cache
    (and until cache bypass is implemented, it should behave like
    O\_SYNC.)

### MacOS X:

-   PAG support

### Linux:

-   On-going maintenance necessary to keep up with backward incompatible
    changes to the Linux kernel and new interfaces provided and used
    therein.

### Solaris:

-   update client to use system inodes instead of private inode pool.

### BSD:

-   Port the cache manager to NetBSD\
     Estimate: 1 month

### New Client Platforms:

There is a growing demand for pervasive access to data from handset
devices.  Clients for Symbian S60, Windows Mobile, Apple's iOS,
[OpenHandsetAlliance](http://www.openhandsetalliance.com/ "OpenHandsetAlliance")
(aka Android), and Nokia/Intel Maemo/Meego devices will be critical in
the years to come.

### All Platforms:

-   **Client Cache Usage Tracking and Tuning:**\
     The current cache managers implementation an explicit Least
    Recently Used algorithm for recycling objects. This algorithm does
    not take into account:

    -   frequency of use
    -   whether the file is currently open

    \
     By tracking the right statistics, the cache manager would be more
    likely to have the right data cached. One of the extreme examples
    that has been discussed is a maintenance application that runs five
    nights a week at 1am on tens of thousands of machines.  The running
    of this application pounds the volume and file server because every
    machine must reload the application contents into the cache at the
    same time. If the cache manager could predict this utilization based
    upon past history, then the clients could slowly prefetch the data
    ahead of time easing the load on the file servers and improving the
    performance of the application on the local machine.

2. Human Interfaces
-------------------

There have been many discussions about how hard AFS is to use, how end
users don't want AFS and really want a WebDAV solution.   What do those
statements really mean?  First, AFS isn't any harder to use than any
other authenticated file system from the perspective of end users.  If a
user has an "encrypted" local disk she has to authenticate herself by
providing her password.  With the single sign-on solutions available for
OpenAFS there isn't much reason for users today to be running without
tokens when they have network access.  Second, the statement that end
users don't want AFS (as opposed to some other centralize storage
solution) really makes no sense.  End users don't ask for technologies,
they ask for functionality.  If a user wants centralized storage then
the user wants centralized storage. 

Users describe their desires using the technologies that are most
familiar to them which today most often means Windows Shares (CIFS) and
Browser based services.  Why?  Because those are the technologies the
user is presented on his or her operating system's desktop.  The vast
majority of daily users are uncomfortable with command-line operations. 
Improving the ease of use of AFS can be achieved by providing tighter
integration with the operating system desktop environment. 

### Microsoft Windows:

The Secure Endpoints Inc. [*OpenAFS Windows Road Map* web
page](http://www.secure-endpoints.com/openafs-windows-roadmap.html)
provides an number of mock ups of Explorer Shell extensions that can be
used to not only make AFS more accessible to end users but also
significantly improve its ease of use.  By making the Explorer Shell AFS
aware, users will be more comfortable using it. No longer will users
have to use command line techniques to access AFS and manage its
contents and metadata.

One of the most important ideas that was the result of discussions with
Stanford University's Help Desk staff is the concept of Custom Name
Spaces.  On Microsoft Windows a Name Space is a virtual folder that
appears as part of the Explorer Shell.  The objects "My Computer", "My
Documents", "Control Panel", My Network Places", "My Sharing Folders",
etc. are all name spaces.  Stanford University has been shipping for
many years variations of an application now called "Stanford Desktop
Tools".  One of the features of SDT is the ability to search for
classes, users, departments, and projects and map a drive letter to the
associated AFS volume.  Another feature is the ability to quickly map a
drive letter to "my home directory".  A final feature is the most
recently used volume list.

With Name Spaces, we can implement all of this functionality.  We can
define a "recently used volumes list" which is always populated with the
volumes the user most recently read or stored data to.  We can define a
"My Stanford Home Directory" name space that always contains a shortcut
to the volume associated with the user's token for the ir.stanford.edu
cell.  We can also create name spaces for "Stanford Users", "Stanford
Classes", "Stanford Departments", etc.  Other organizations can
distribute their own AFS name spaces that represent important data that
is stored in their cell.  AFS name spaces from multiple organizations
can co-exist on the same system.  Since name spaces are built into the
Explorer Shell they are always easily accessible to the end user because
they become a part of the Desktop.

[A detailed proposal describing an AFS Name Spaces implementation is
available in
PDF.](https://www.secure-endpoints.com/netidmgr/proposal-afs-namespace.pdf)

Users expect to find a Control Panel for Services that support per-user
configuration.  For OpenAFS users can configure the behavior of the AFS
Credential Provider for Network Identity Manager and their Protection
Service Groups.  [For more details
...](http://www.secure-endpoints.com/openafs-windows-roadmap.html#control%20panel)

System-wide configuration of Services are performed via Microsoft
Management Console plug-ins.  [For more details
...](http://www.secure-endpoints.com/openafs-windows-roadmap.html#client%20service%20mmc)

Microsoft Windows Vista User Account Control Privilege Separation.  [For
more details
...](http://www.secure-endpoints.com/openafs-windows-roadmap.html#vista_uac)

### MacOS X:

Apple doesn't permit the same degree of customization of the Finder as
Microsoft does for the Explorer Shell.  However, the Finder can be
customized with an AFS virtual folder and AFS context menus. Likewise,
certain other graphical interfaces which will become available in
Leopard provide opportunities for customization to ease use of AFS.

-   Enhance Finder with an OpenAFS Context menu

3. AFS3 Protocol Feature Enhancements
-------------------------------------

In order for AFS to be treated as a first class file system for MacOS X
and Microsoft Windows it must gain the following functionality:

-   **Removing Directory Limitations:**\
     The current AFS directory format and RPCs suffer from a number of
    limitations that adversely affect the user experience.  A directory
    has a maximum of 64,000 entries if all file names are 16 or fewer
    octets.  Longer names are implemented by consuming an additional
    entry for each additional 32 octets of file name.  Given the ever
    increasing length of file names some cells are filling the directory
    with as few as 10,000 entries.   Some scientific research projects
    require the use of millions of files perhaps containing a single
    data byte within a single directory.

    The current AFS directory format is very inefficient for searching
    when case-insensitivity or Unicode normalization is required.  Under
    these circumstances search time is linear to the number of entries
    in the directory.  Many modern file systems implement the directory
    as a B+ tree to permit O(log n) searching.  The existing format
    places a heavy burden on each and every cache manager.  Each client
    must download a copy of the directory buffers and perform linear
    searching.  This results in heavy use of the CPU when searching
    directories with 500 or more entries.

    Another issue is the lack of support for internationalization.  In
    the current directory format directory entries are stores as a
    sequence of octets without any character set hinting.  A file that
    is stored using a name encoded with ISO 8859-5 or CP437 will not be
    represented correctly to the user on a system that expects UTF-8. 
    Even when file names are stored using UTF-8 it is important to
    recognize that depending on the input mechanisms it is possible for
    a user to enter the same semantic string using different octet
    sequences.  Therefore it is crucial that any implementation of
    Unicode file names support [normalized
    forms](http://en.wikipedia.org/wiki/Unicode_normalization) for
    comparison.   

    Finally, Microsoft Windows and MacOS X are now requiring that first
    class file systems support the concept of multiple data streams per
    file.  These streams are used to store extended attributes, security
    zone information, resource forks, and other forms of meta data in
    addition to providing a general purpose storage mechanism for
    applications.  [For more details
    ...](http://en.wikipedia.org/wiki/Fork_(filesystem))

    At the 2004 AFS Hackathon in Stockholm there was much discussion of
    potential methods of extending the existing directory format to
    support Unicode.  
    [http://www.afsig.se/afsig/space/AFS+directory+format+extensions](http://www.afsig.se/afsig/space/AFS+directory+format+extensions) 
    However, these approaches did not address the directory search
    performance issues, the entry limitations or multiple data streams. 

    The current direction under consideration is to completely replace
    the on disk directory format with an entirely new one consisting of
    data blocks representing nodes in a B+ tree with each block
    containing a variable number of entries.  The new data structure
    would be Unicode aware and support multiple data streams.  Microsoft
    Windows clients would implement extended attributes in a reserved
    data stream.  MacOS X clients would use a reserved stream for the
    resource fork.

    New versions of all of the directory RPCs would be implemented to
    support the new data structure.  Clients that use the new APIs would
    be delivered directory buffers which construct a B+ tree which in
    turn would significantly improve directory search times. 

    For old clients, new implementations of the old RPCs would deliver
    directory data translated to the old linear format up to the maximum
    number of directory entries.  It is possible that old clients will
    not be able to see all the files in a given directory.  \

-   **Extended Attributes:**\
     Extended Attributes are used by MacOS X to store resources and DOS
    Attributes.  When they are not supported by the file system, MacOS X
    is forced to create the .\_ (Apple Double files).  Extended
    Attributes on Microsoft Windows are used to store a variety of
    meta-data about files and directories.  The lack of EA support in
    AFS damages the Windows User Experience.  AFS Cache Managers can
    implement support for extended attributes and store them in hidden
    Apple Double files while waiting for full EA support within AFS
    volumes.\
     [For more details
    ...](http://en.wikipedia.org/wiki/Extended_file_attributes)

    \

-   **Per-file ACLs:**\
    AFS supports per-directory ACLs.  Per-file ACLs would make it
    possible to apply a different set of access constraints on a single
    object within a directory.  At the present time storing multiple
    objects with different access controls requires that they be stored
    in separate directories. The AFS protocol provides partial support
    for this from the AFS/DFS translator, and this is supported in
    clients going back to IBM AFS.

    \

-   **Mandatory Locking and Byte range locks:\
    **Platforms such as Microsoft Windows and MacOS X require that their
    first class file systems support mandatory lock semantics and byte
    ranges.  Applications which rely on these capabilities such as
    Microsoft Office and databases risk data corruption if their data
    files are altered while they are assumed to be under a lock.   AFS
    only provides advisory full file locks and provides no upgradeable
    lock type.  The existing AFS file server lock implementation doesn't
    keep track of which clients were issued locks which results a number
    of situations in which lock counts can become incorrect and produce
    a denial of service on a given file.

    The Windows AFS client in the 1.5 series has added a localized
    implementation of mandatory locking and byte range locks.  Each time
    an application requests a byte range to be locked, the cache manager
    ensures that it has an appropriate full lock on the object.  The
    cache manager than accepts the responsibility of tracking each of
    the locks and doling out a range at a time.\
    Estimate: 2 months. \

-   **Status Data (Callback Registration) Expiration Algorithm
    Improvements:**\
    Status data and callback registration expiration is currently
    determined based upon the number of clients that are accessing the
    data instead of the likelihood that the data is going to change. \
    \
    Status: Implementation in progress.

-   **OPEN/CLOSE File Server RPCs:**\
    New file server RPCs would provide new audit data\

4. Server Enhancements and Management Tools
-------------------------------------------

### All Platforms

-   **LDAP integration:**\
     Protection Server to LDAP Proxy implementation and Direct File
    Server to LDAP implementation.  Separate schemas will be necessary
    depending on whether the LDAP server is OpenLDAP or Active
    Directory.\
     \
     Brett Trotter [\<blt@iastate.edu\>](mailto:blt@iastate.edu) wrote
    an implementation called **ptsldap**.  In July 2005 he had working
    code using the Mozilla LDAP library and was porting it to use
    OpenLDAP instead.

    Additionally, Volker Lendecke implemented a similar project for use
    with Samba, which is not known to have been completed.

    Luke Howard [PADL Ltd.](http://www.padl.com)) developed an AFS
    Protection Service as part of his Active Directory clone, XAD. 
    Ownership of XAD has since been transferred to Novell.  However, it
    is expected that Luke will assist us in developing a new
    implementation in the coming months.

-   **Multiple back-end file server:**\
     Current file servers must be built to support one type of file
    partition, either *inode* or *namei*.  This makes it impossible to
    mix partition types on the same machine for the purpose of
    performance comparison or conversion. This project will make the
    storage back end modular, and allow for additional back ends to be
    provided.\
     Estimate: 1 month\
     \
-   **Posix Extended Attribute File Server Back-end:**\
     Using Posix Extended Attributes to store AFS metadata will provide
    the portability of the *namei* backend with the performance of the
    *inode* backend.   A *PosixEA* backend would not require a special
    fsck which would permit the use of journal logs.\
     \
-   **Multi-Protocol File Server:**\
     The current AFS file server can only communicate using the AFS3
    protocol.  Once all of the functionality in section 3, AFS Protocol
    Feature Enhancements, is implemented, the file server will support
    all of the capabilities necessary to alternative protocol front ends
    including CIFS/SMB2.0 and WebDAV.\
     \
     Estimated: To be determined.\
      
-   **Protection Server enhancements for alternate principal names:**\
     The AFS Protection Service maintains a database that maps user
    names to AFS IDs.  This table needs to be extended to a many-to-one
    relationship of user names to AFS IDs.  In addition, multiple name
    forms must be supported in order to permit different types of user
    authentication.\
     A proposed implementation was sketched out at the AFSig Hackathon
    in Stockholm in 2004
    ([details](http://web.archive.org/web/20060211111127/http://www.afsig.se/snipsnap/space/prdb+extensions))
    \

    Status: Standardization complete.

-   **Volume Server enhancements for large volume names:**\
     Volume names within the existing RPCs and database are too short
    given the number of volumes that are now being deployed in existing
    cells.\
     \
    Estimate: 1 week\
    \
-   **VL Server enhancements for split horizon addressing:**\
     Many sites now provide services from hosts which exist behind a NAT
    to hosts both inside and outside that NAT. The vlserver should
    provide interfaces to allow returning only some addresses to queries
    when responding to volume location requests. \
     \
-   **Volume Server read-only replication optimizations:**\
     A volume release current requires that the entire file be copied
    from the server maintaining the release clone to the replication
    site instead of only copying modified chunks. This is a significant
    performance issue especially as 64-bit file sizes and append only
    files become more common. Modifying the volume replication process
    would provide significant clock time and network traffic savings. 
    Possible approaches include:
    -   data compression of the volume dumps can reduce network
        bandwidth and storage requirements
    -   [rsync/rdiff](http://en.wikipedia.org/wiki/Rsync) style
        replication can be used to reduce the cost of replicating large
        files that have only had small changes since the previous
        replica was created.  This can be coupled with additional
        read-only clone revisions and volume version numbers to produce
        very rdiff streams that can be used to update "old release"
        replicas without requiring a full volume replication.
    -   encrypted volume dumps can increase security when storing dump
        files in external backup systems

    \
     Estimate: 2 to 3 months\

**Read/write volumes and replication:**\
 After optimizing the size of volume dumps it should be possible to
implement a simple read/write replica model in which there is a single
master for each volume to be used for writes and locking and multiple
replicas that can be used for reads.

\
 \

**Partition UUIDs:**\
 Assigning UUIDs to each partition instead of the exsting non-unique
names will permit drives to be migrated between machines with just a
simple update of the volume database before continued use.  This will
eliminate most of the work associated with synchronizing the database
and removing stale entries.\
 Estimate: 1 to 2 weeks\
 \

**Machine Accounts in the Protection Database:**\
 Add the concept of machine accounts to the protection server database
permitting authenticated machine access that does not result in the
client being treated as a member of system:authuser.\
 \

**UBIK improvements or replacements:**\
 UBIK is the database replication protocol used by AFS server for the
synchronizing the volume and protection databases among servers.  It is
an elected single master model in which the selection of the master is
determined strictly based upon the IP addresses of the server subset
which are capable of mutual communication and which are sufficient to
establish quorum.  The server with the lowest IP address is elected
master.  There are a number of scalability and performance issues with
UBIK that must be addressed.

-   **Master Selection Algorithms**\
     Master selection should be configurable based upon the needs of the
    organization and not tied to the IP addressing.  One model involves
    configuring additional state information including priorities based
    upon the servers in the quorum, the time of data, source of network
    traffic, etc.  It should be possible a master to be selected with a
    quorum that is not represented by a fully connected graph.
-   **True Server Multi-homing:**\
     CellServDB changes are required

-   **Increase Record Sizes:**\
     The existing record size results in significant design restrictions
    and imposes undesirable overhead. 
-   **Multi-master Replication:**\
     Single master replication is easier to implement than multiple
    master replication models.  However, multiple master replication
    makes the most efficient use of network resources.
-   **Multi-File Databases:\
    **

### Microsoft Windows

Once AFS is capable of being used as a first class file system for
Microsoft Windows clients it will make sense to support the AFS servers
on the Windows Server platform as there are a large number of Microsoft
Windows only IT organizations that do not have the expertise to manage
UNIX/Linux systems.  The servers are mostly there already.  There is
work that needs to be done on the NTFS Namei implementation and there
needs to be much better integration with power management, plug-n-play
networking, and Windows Event Logging.

Of course if you want to host services on Windows, you must provide a
Microsoft Management Console plug-in to manage them.

[For more details
...](http://www.secure-endpoints.com/openafs-windows-roadmap.html#afs%20servers)\
 \
 Estimate: 4 to 6 weeks

5. High Performance Computing Extensions
----------------------------------------

-   **Asynchronous RX RPCs:**\
     All Rx calls in the existing implementation are synchronous.  The
    currently executing thread must wait for completion.   The maximum
    number of simultaneous requests that can be processed is limited by
    the number of threads that can be allocated to the process.  By
    adding an asynchronous Rx call mode, the file server can be
    redesigned to process requests without blocking threads for callback
    breaks, whoareyou? probes, and getcps calls. This will permit a
    significant reduction in client requests *waiting for threads*.\
     \
     Estimated: 6 weeks for Asynchronous Rx and 3 weeks for file server
    modifications.

-   **Increase RX/UDP Maximum Number of Calls:**\
     RX/UDP has a maximum of four simultaneous calls per connection. 
    The initial number of calls for each connection cannot be increased
    due to the lack of an appropriate negotiation mechanism at the RX
    layer.  However, an application layer negotiation could be used to
    permit the application to hint to the rx connection how many calls
    should be permitted.\
     \
    Requires Standardization\
    \
-   **rxgk:\
    rxgk** is a security class based upon the Generic Security Service
    Application Programming Interface (GSS-API) that attempts to address
    a much broader range of security weaknesses in AFS; not simply the
    use of single DES encryption ciphers.  These include issues such as:

    -   users can impersonate the server to the cache manager since the
        user knows the key obtained from the Kerberos service ticket
    -   neither the AFS clients nor the servers contribute any random
        data to the construction of the key
    -   the desire to support individual keys per service per host
        instead of a single key for all services on all hosts within a
        given cell
    -   the desire to provide data confidentiality and integrity
        protection on anonymous connections as well as authenticated
        ones
    -   the desire to provide for algorithm agility
    -   the desire to allow the server to require the use of crypto by
        the clients
    -   the desire to map multiple authentication names to a single AFS
        ID within the protection database

    **rxgk** is designed but has not yet been fully implemented.  Love
    Hörnquist Åstrand, Magnus Ahltorp, Jeffrey Hutzelman, Derrick
    Brashear and Jeffrey Altman met at KTH the week of 22 Jan 2007 to
    begin implementation of **rxgk** and modify as many of the AFS
    services as possible.  Love presented [a status
    report](http://workshop.openafs.org/afsbpw07/talks/lha.pdf) at the
    2007 AFS & Kerberos Best Practice Workshop and did more work with
    Derrick the following week.

    Status: Standardization in progress.  Implementation substantially
    complete.  promised by MIT.\
    Target: 2.0\
    \

6. Miscellaneous
----------------

-   **HostAFSD and Peer-to-Peer AFS:\
    **One of the things that the Gatekeepers are frequently asked by AFS
    newbies is "why can't I share my local files by AFS?"  Many users
    have experienced either CIFS or NFSv3 file sharing and wish to be
    able to do the same using AFS.  The existing AFS file server back
    ends store files within physical files known as volumes which can be
    migrated, cloned, replicated to any AFS file server within the same
    cell regardless of the operating system, partition file system, or
    hardware. 

    For users that are willing to give up the location independence of
    the data, there isn't much preventing the construction of a file
    server back end that reads and writes from the native file system
    provided that native file system has some way of notifying AFS when
    a file changed.  Change notification is required for the file server
    to be able to callback the clients and report the invalidation of
    their data.

    Another question that needs to be addressed is how to provide for
    authenticated access and access control lists.  Finally, location
    discovery is a challenge that might be addressed with Apple's
    Bonjour and/or dyndns; this work can be extended to provide similar
    ability to discover a local cell for any client.\
     Estimate: 2 months

-   **Backup solutions:**\
     Backup systems in large organizations are often quite institution
    dependent.  When backing up AFS there are two different views. 
    There is how the directory tree is viewed by the end user and the
    AFS volume view.  It is the mapping of these two views that
    frequently results in differing requirements on the backup systems
    that an organization wants to deploy.

    Most off the shelf backup systems only see file systems from the
    viewpoint of the user.  Whereas backing up AFS so that a given
    volume can be restored as needed in a location independent manner is
    much more similar to backing up a distributed database.  Backing up
    the files that the database writes does not allow for the necessary
    granularity of restores that are required.  In addition, backing up
    the database files while they are in use results in data
    inconsistencies.

    Teradactyl is one of the few remaining commercial offerings that
    have integrated support for AFS. VERITAS Net Backup and Tivoli
    Storage Manager have both dropped integrated AFS support. 
    Teradactyl have been a sponsor of the AFS & Kerberos Best Practice
    Workshops for the last couple of years.\

    [http://www.teradactyl.com/Documents/OpenAFSbasics.html](http://www.teradactyl.com/Documents/OpenAFSbasics.html)

    There have also been various efforts to contribute AFS support to
    Amanda, [http://www.amanda.org/](http://www.amanda.org/), and there
    have been efforts to provide an AFS wrapper to Legato Networker.

-   **Object Storage:**\
     The RxOSD-extension to AFS allows to store metadata and actual
    filedata separately. The filedata may also reside on more than one
    server or on HSM-systems. This extension is somewhat based on the
    SCSI-T10-standard. A file stored on OSDs is generally called an
    "object". The AFS-fileserver is extended inasmuch to serve the
    metadata of an object. A new server instance the OSD-server is
    serving the actual file-data. A new server osddb server finally
    keeps track of all registered osd-server. The osddb server is
    somewhat comparable to the vldb-server which gives the location of a
    volume. 
    [http://pfanne.rzg.mpg.de/trac/openAFS-OSD/wiki/Specs](http://pfanne.rzg.mpg.de/trac/openAFS-OSD/wiki/Specs)\
    \
    Status: Integration is in progress.\
    Target: 1.10\
     
-   **Automatic Load Balancing:**\
     CMU has a load balancing tool that could be polished and
    supported.\
     
-   **Official Support for Cell Clones:**\
     Morgan Stanley has often
    [described](http://www.acm.uiuc.edu/conference/2007/speakers#RonIsaacson)
    their Volume Management Service which manages clones of read-only
    cells across multiple data centers.  There are many things that
    could be done to make such deployments easier to manage including
    support for automatic failover between read only cells which are
    known to be clones.

7. Documentation
----------------

-   Installation and Maintenance
-   Reference Manuals
-   Developer Guides
-   End User Guides

Implementation and Schedule
===========================

The implementation schedule for these projects is entirely dependent
upon resource availability.  Please send inquiries, comments, and offers
of support to
[openafs-gatekeepers@openafs.org](mailto:openafs-gatekeepers@openafs.org?subject=OpenAFS%20Roadmap%20Feedback).
Where external contributors have promised contributions, they are
included, as are timelines when those are provided.   The following
release schedule is subject to change.

1.4.15
------

The next release in the previous stable series for UNIX is expected
before December 2011.  This release will correct implementation defects
and will most likely be the last release in the 1.4 series.

1.6.8
-----

The 1.6 series is the current stable series for UNIX and the last stable
series for Microsoft Windows without a native IFS implementation.  \
1.6.8 is the next release in the series and is expected April 2014.

1.7
---

The 1.7 series is the development branch for the Windows IFS
implementation.  The first release on this branch was announced on 15
Sept 2011.  Subsequent releases are expected every two to four weeks
until the code enters maintenance mode after two or three months.

1.8
---

The 1.8 series will become the first stable release of OpenAFS to
include the Windows IFS implementation.  No other new features will be
added to 1.8.

1.9
---

The 1.9 series will replace the 1.5 series as the experimental release
series.  1.9 releases will begin shortly after the 1.7 series has the
Windows IFS implementation committed.  Major new features will be
integrated into 1.9 releases in preparation for the 1.10 stable
release. 

2.0
---

The 2.0 series will replace the 1.6 and 1.8 series as the stable release
series for UNIX and Microsoft Windows.  The 2.0 series are scheduled to
include the rxgk security class including Kerberos v5, RxUDP performance
improvements, PTS authentication name extensions, and extended
callbacks.

