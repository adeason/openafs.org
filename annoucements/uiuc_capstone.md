---
title: Project Ideas for UIUC's Capstone 2008/2009
---

OpenAFS is a 100% open source globally distributed file system that is
derived from the IBM AFS commercial offering as of 1 November 2000. 
Since IBM released the source code as an IBM DeveloperWorks project,
OpenAFS has thrived, adding support for new platforms while enhancing
its overall performance, scalability and usability.  At the present time
OpenAFS servers are supported on Solaris, MacOS X, Linux, HP-UX, AIX,
and  \*BSD Unix variants.  OpenAFS clients are available for Solaris,
MacOS X, Linux, HP-UX, AIX, Microsoft Windows, and ARM based Linux
devices such as Nokias N810 Internet Tablet. 

OpenAFS is the only storage solution that has a successfully deployed
federated authentication and authorization system that permit
individuals from otherwise independent organizations to collaborate at
the file system layer while using the single sign-on credentials managed
by their local organizations.  Hundreds of organizations with academic,
research, not-for-profit, and commercial missions have deployed
thousands of petabytes worth of data within OpenAFS.  This data is
securely accessible by their community members across the Internet and
around the world. 

Since the early 90s when AFS became commercially available first from
Transarc and later from IBM, many file systems have tried to replace its
existing deployments.  An environment of fear, uncertainty and doubt
have limited the success of AFS over the years as prior to 2000 IBM was
consistently announcing the end of life for the product only to offer
extensions on an annual basis.  Since 2000, there have consistently been
doubters saying that OpenAFS could not survive and flourish as an open
source project.  File systems are difficult.  Distributed file systems
are even more so.  Heterogeneous distributed file systems are next to
impossible to maintain and develop without significant resources and
access to the internals of each supported operating system.  Yet,
OpenAFS is approaching its eighth birthday.

OpenAFS is a very large and highly complex software project consisting
of close to one million lines of source code that is severely under
documented.  As a result it takes a long time for any developers to
become proficient contributors to the core systems.   The proposed ideas
are primarily projects which exist on the periphery of the code base but
are nevertheless crucial to an improved end user experience. 

OpenAFS is participating in the UIUC Capstone Program for several
important reasons. First, NCSA and the Student ACM Chapter have a long
history of AFS use.  Second, the ACM Reflections conference has invited
several speakers over the years to discuss OpenAFS and the response from
the attendees has been quite positive with several students asking how
to get involved.  Finally, the UIUC Computer Science students have an
excellent reputation and the OpenAFS community would like to encourage
as many as possible to become members of our development community. 

Due to the diverse operating systems and the need to develop within so
many different layers of the operating system there are opportunities
for students to learn a broad range of skills on the platform of their
choice.  Developers and system administrators with OpenAFS skills are in
high demand.  Successfully completing an OpenAFS project will be a major
bullet point on your resume when it is time to search for a full time
position.

OpenAFS is an international open source project.   Unlike other Capstone
projects, student teams will have the ability to obtain support from the
entire OpenAFS community via mailing lists, an IRC channel, and Jabber
Conference Rooms.  Christopher Clausen will act as an on-site liaison
while the OpenAFS Gatekeepers will provide architectural design
consultations and code review.

The following are a set of project idea that might be selected for a
Capstone Project:

Project Idea 1: Microsoft Windows Explorer Shell User Interface Extensions
--------------------------------------------------------------------------

In order for end users to be comfortable using AFS, the Explorer Shell
must provide the same level of functionality that exists for CIFS and
local file systems.  Selecting an object should display a summary of the
object's meta data; the table view should provide options for displaying
ACLs, UNIX mode bits, the owner, group information, symlink and mount
point targets; the properties dialog should permit interactive
modification to meta data values when the user has the appropriate
permissions.  All in all, the user should not notice that AFS is not a
native part of the operating system and the user interface.

Mockups of proposals for the Explorer Shell extension can be found
at[http://www.secure-endpoints.com/openafs-windows-roadmap.html\#shell
extensions](http://www.secure-endpoints.com/openafs-windows-roadmap.html#shell%20extensions). 
This project consists of multiple components that can be successfully
implemented one at a time.  The successful completion of this project
does not require that all of the proposed extensions be implemented. 

This project does not require any prior knowledge of AFS nor any
knowledge of OpenAFS internals. By completing this project the developer
will become an expert in the Microsoft Windows Explorer Shell interfaces
and the Microsoft Component Object Model (COM).  This experience can be
reapplied to numerous other applications and will prove to be an
excellent item on a resume.

The programming language for this project is C/C++.  The operating
system is Microsoft Windows.  The project will aim to support Microsoft
Windows versions from XP SP2 to Vista/Server 2008.

Estimated difficulty: *moderate*

For more information contact: *openafs at secure-endpoints.com*

Project Idea 2: Read/Write replication for OpenAFS
--------------------------------------------------

Currently, OpenAFS supports replication, but only for read-only data. In
order to increase availability, for instance during server, disk or
network failure, read-write replication is proposed. Prior work in this
area has been done at KTH
(http://www.stacken.kth.se/\~noora/exjobb/report.pdf) and by a Google
Summer of Code student in 2008
(http://code.google.com/soc/2008/openafs/). Some points to consider:

1.  The performance should not deteriorate after replication.
2.  Data consistency should be maintained.
3.  Network load due to replication should be kept to a minimum.
4.  AFS clients should not be aware of replication.

The approach of 'Pessimistic replication (with primary copy) along with
Synchronous updates and Eager recovery' is suggested as appropriate for
AFS by Noora. The pessimistic read one/write all protocol is recommended
in the document. This approach gives emphasis on the consistency across
all the replicated servers, with the requirement that all nodes have
identical copies at all times. This approach is good for scenarios where
most of the servers will be up and the chance of network partition is
low. Also, an approach using a primary copy puts more importance on
stability and availability rather than load balancing. However, in a
scenario where there are large numbers of partitioned networks, problems
may arise:

-   The Synchronous updates are slower and requires participation of all
    the replicated nodes. Participation of all the servers cannot be
    guaranteed.
-   The Eager recovery approach causes all the updates to be completed
    after coming up from a crash or partition. During that period, the
    non-Primary copy being updated is unavailable. This may not be ideal
    in some cases where a server's network frequently is partitioned.
    Instead of using Synchronous updates we can use Asynchronous
    updates. This will be useful if we overcome the problem of write not
    being committed due to Asynchronous nature of the approach. Also we
    can consider Lazy recovery after the node comes up from crash. In
    this approach not all the volumes are updated immediately. The
    volumes are updated when they are next written or the server is
    chosen to be a coordinator for a read or a write.

Some of the other design decisions for the implementation are

1.  A Volume (essentially an arbitrary subset of a complete filesystem)
    is the administrative unit in AFS, hence replication will be done at
    the volume level.
2.  In AFS, file servers are not aware of other file servers.

To provide read-write replication, either the functionality must be
added to the fileserver, or pushing changes to non-primary sites must be
done by the volserver. Suggestions:

-   In OpenAFS 1.5 there is a feature which attempts to do online
    recovery if file system consistency needs to be checked, targeting
    things immediately if they are demanded and otherwise background
    processing until the recovery is completed. The same feature can be
    used to implement any eager recovery, like sorting demands to the
    top.
-   However, lazy replication is an easier starting point.

Implementation Details

1.  Implement updated VL\_GetEntryByName RPC that can be extended to
    support RW replicas and other features that may be required in the
    future. An additional volume type should be supported now, with the
    capability to add more later.
2.  Modify the vlserver to support the new RPC.
3.  Modify the vlserver to support storing the new information which
    would be used in (2).
4.  Modify the AFS client to support the new RPC. Per-vlserver
    capability tracking can be used to determine if the new RPC is
    supported; If not, no readwrite replicas will be used for the cell
    and the old RPC will be used.
5.  Modify the AFS client to track multiple RW sites plus an indication
    of which is the master.
6.  Implement support for periodic checking by the primary copy server
    of secondary server availability. This can be done in one of the
    server "Check" loops.
7.  Implement asynchronous updates of non-primary copy servers.
8.  Implement failure handling process for updates that cannot be
    completed (sent to all the secondary copies), either by keeping a
    queue of pending updates, or just marking the replica out of date
    and pushing a new copy when it is next available.
9.  Implement Lazy Recovery from crashes or network partitions. This can
    be done using the incremental volume release procedure provided in
    AFS if a list of changes is too large or not complete.
10. Implement selection of new primary copy, as necessary. The vlserver
    would be updated to know of the new primary copy and the server
    which is now primary would need to update its information to be
    aware of this. The main issue here would be a mechanism to make sure
    a partitioned machine which was formerly master does not become
    master again, and mechanisms to ensure multiple masters cannot
    happen. An implementation drawing on concepts from ubik is possible.
    Steps through 9 can be used without implementing this other than as
    a hand-run tool to promote a slave copy to master when the admin
    knows the master will not return.

References: --------------
[1][http://www.stacken.kth.se/\~noora/exjobb/report.pdf](http://www.stacken.kth.se/~noora/exjobb/report.pdf)

Estimated difficulty: *moderate to hard*

Primary mentor: *Derrick Brashear* shadow at openafs.org

Primary mentor: *Jeffrey Altman* jaltman at secure-endpoints.com

Project Idea 3: Microsoft Management Console Snap-in for Managing OpenAFS Servers
---------------------------------------------------------------------------------

OpenAFS for Windows includes a server manager tool that is out of date
and suffers from a number of usability problems.  The supported user
interface for administration tools such as these on Windows is a
Microsoft Management Console snap-in.  In addition to having a
consistent user interface, using this framework also facilitates\
extensibility using additional snap-ins as required.  This project aims
to develop a usable AFS server administration snap-in based on the
Microsoft Management Console framework.\
\
The first phase of the project will involve gaining an understanding of
the architecture of AFS and the administration tasks that need to be
performed on deployments of different sizes.  Then a suitable user
interface would be designed guided by the Microsoft Management Console
design guidelines.  Mockups may be used to communicate the design to
interested parties for evaluation and feedback.  It is important that
the the design be usable and compliant with the relevant guidelines.\
\
The implementation phase can begin once a suitable design for the user
interface has been reviewed.  The MMC snap-in architecture is based on\
COM.  It is suggested that the code be developed using ATL and
optionally WTL.  ATL provides a number of templates that will aid in
building an MMC snap-in.  The OpenAFS codebase contains code for a 
server manager application that may be reused for the purpose of
gathering information from and interacting with AFS services.\
\
The programming language for this project is C/C++.  The target
platforms are Microsoft Windows versions from XP SP2 to Vista/Server
2008.  A good understanding of object oriented design and Windows
programming is required for the successful completion of this project.

Screen shots of the existing AFS Server Manager application can be found
at[http://www.secure-endpoints.com/afs/athena.mit.edu/user/a/s/asanka/Public/ja/afssvrmgr/](http://www.secure-endpoints.com/afs/athena.mit.edu/user/a/s/asanka/Public/ja/afssvrmgr/).\
\
Estimated difficulty: moderate\
\
Primary mentor: jaltman at
[secure-endpoints.com](http://secure-endpoints.com)

Project Idea 4: Design and Implement a Regression Test Suite for OpenAFS Clients and Servers
--------------------------------------------------------------------------------------------

One of the most critical software engineering requirements for designing
and implementing robust bug free software is being able to test all of
the code paths to ensure that the expected behaviors are the ones that
are in fact implemented.  Unfortunately, as with many large software
projects, testing like security is something that has been after
thought.  As a result it is often the case that attempts to add
functionality, improve performance, or port the code base to a new
platform results in the introduction of software defects.

This project is to design a testing framework and test suite to test not
on the standard file system behaviors but also functionality specific to
AFS including mount points, volume management, file server operations,
etc.  Each of the user commands documented in the[OpenAFS man
pages](http://www.openafs.org/manpages/index.html) should be exercised
testing for success and failure conditions.  The test framework should
be designed to permit the easy addition of new tests when an error has
been fixed to ensure that the error is never again reintroduced. 

The language for this project is up to the development team.  However,
it should be a language that is available cross platform so that the
same testing framework can be re-used for both the Unix and Windows
cache managers.

Estimated difficulty: moderate

Primary mentor: *Derrick Brashear* shadow at openafs.org

Primary mentor: *Jeffrey Altman* jaltman at secure-endpoints.com

 
