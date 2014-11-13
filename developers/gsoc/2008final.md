---
title: OpenAFS Projects from Google Summer of Code 2008
---


Outcome
-------

OpenAFS applied for the second time to be part of the Google Summer of
Code, and this year was accepted. Ultimately Google opted to fund 6
projects for OpenAFS; Two more were funded with the same rules using
other money including that granted by Google to a sponsoring
organization per student.

-   [Microsoft Management Console Snap-ins, Client and Server](#mmc)
-   [Implementing OpenAFS features into RedHat's kafs kernel
    module](#kafs)
-   [Read/Write replication for OpenAFS](#rwrep)
-   [Per-file ACLs for OpenAFS](#perfile)
-   [Read/Write Disconnected AFS](#discon)
-   [Windows Explorer Shell UI extension updates](#shellex)
-   [OpenAFS servers for Windows](#winserv)
-   [Redesigning the OpenAFS project website](#website)
-   [Extensions for multiple authentication types to the OpenAFS
    ptserver](#ptsext)
-   [Porting OpenAFS to new platforms](#ports)

Background
----------

OpenAFS is a 100% open source globally distributed file system derived
from IBM AFS commercial offering as of 1 November 2000.  Since IBM
released the source code OpenAFS has thrived adding support for new
platforms while enhancing its overall performance, scalability and
usability. 

OpenAFS is a very large and highly complex software project consisting
of close to one million lines of source code that is severely under
documented.  As a result it takes a long time for any developers to
become proficient contributors to the core systems.  Given the time
frames associated with Google Summer of Code the proposed ideas are
primarily projects which exist on the periphery of the code base but are
nevertheless crucial to an improved end user experience.

### Project: Microsoft Management Console Snap-ins, Client and Server

#### Mentor: Asanka Herath

#### Status: Incomplete

A sample MMC snap-in with both client and server functionality was
partially completed.

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

This project does not require any prior knowlege of AFS nor any
knowledge of OpenAFS internals.  By completing this project the
developer will become an expert in the Microsoft Management Console
interfaces and the Microsoft Component Object Model (COM).  This
experience can be reapplied to numerous other applications and will
prove to be an excellent item on a resume.

The programming language for this project is C/C++.  The operating
system is Microsoft Windows.  The project will aim to support Microsoft
Windows versions from XP SP2 to Vista/Server 2008.

Estimated difficulty: *moderate*

### Project: Per-file ACLs for OpenAFS

#### Mentor: Matt Benjamin

#### Status: Incomplete

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

More detail on this project can be found [here](acls.txt).

Estimated difficulty: *moderate*

### Read/Write Disconnected AFS

#### Mentor: Simon Wilkinson

#### Status: Substiantially Complete

Common file operations are implemented. File sets and pinning files in
the cache for offline use remain to be implemented. Contributions are
available in OpenAFS RT.

Disconnected operation for AFS was originally implemented by the
University of Michigan, against an old code base. That implementation,
and the thinking behind it is detailed at http://
www.citi.umich.edu/techreports/reports/citi-tr-93-3.ps.gz. This code has
now significantly bit-rotted, but an ongoing effort is being made to
bring it up the standard of the current code base, and integrate it back
into the core. Disconnected operation is a key feature for many users,
and the ability to operate upon files in the local AFS cache, whilst
away from a normal network connection, is likely to open up many new
applications.

This project would implement a number of significant improvements to the
current disconnected code. Offline authentication tokens are required to
allow local users to access files within AFS whilst disconnected from
the network, without giving them access to everything within the cache.
A journal optimiser would significantly reduce the amount of effort
required to replay operations which occurred whilst disconnected. In
addition, there are many usability issues to be explored, and resolved,
before the code is ready for end user usage.

The implementation language is C, with the majority of the code
executing within the operating system kernel. The AFS kernel module runs
on Mac OS X, Solaris and Linux, amongst other systems - whilst the
student need only work on one of these systems, the completed code
should be capable of running on them all. No initial knowledge of
OpenAFS is required, a successful student will develop a detailed
knowledge of kernel VFS layers, and the issues involved in supporting
disconnected operation.

Estimated difficulty: *moderate to hard*

### Project: Read/Write replication for OpenAFS

#### Mentor: Derrick Brashear

#### Status: Partially Complete

An implementation which needs a working recovery mechanism to use
following an outage or when adding a slave, and selection and tracking
of the master copy for a given replicated volume is available in OpenAFS
RT.

OpenAFS currently provides readonly replication of data. Many sites
would like to use replication on all their data. A proposal exists to
address this, however, no work has yet been done on implementation.

The goal of this project is create readwrite replication for OpenAFS.
The proposal can be read
[here](http://www.student.nada.kth.se/~noora/exjobb/filer.html) and we
are available to answer questions about anyt further. Experience with
systems and network programming is highly desirable, however, experience
with OpenAFS is not necessary.

A student choosing this project will be able to list on a resume and
apply the skills necessary for developing network-distributed systems,
especially with regard to filesystems.

Estimated difficulty: *moderate to hard*

### Project: Implementing OpenAFS features into RedHat's kafs kernel module

#### Mentor: David Howells

#### Status: Partially Complete

Partial documentation of the pioctl functions available through AFS, a
pioctl syscall and VFS entry point for the Linux kernel and some
implemented pioctls for the kAFS call are available.

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

Estimated difficulty: *moderate to hard*

### Project: Updates AFS servers for Windows

#### Mentor: Jeffrey Altman

#### Status: Incomplete

Current releases do not offer an up-to-date, supported set of OpenAFS
servers on Windows. The goal of this project would be to make the
necessary changes to allow OpenAFS servers to be run on Windows.

Estimated difficulty: *easy to moderate*

### Project: Microsoft Windows Explorer Shell User Interface Extensions

#### Mentor: Jeffrey Altman

#### Status: Incomplete

In order for end users to be comfortable using AFS, the Explorer Shell
must provide the same level of functionality that exists for CIFS and
local file systems.  Selecting an object should display a summary of the
object's meta data; the table view should provide options for displaying
ACLs, UNIX mode bits, the owner, group information, symlink and mount
point targets; the properties dialog should permit interactive
modification to meta data values when the user has the appropriate
permissions.  All in all, the user should not notice that AFS is not a
native part of the operating system and the user interface.

Mockups of proposals for the Explorer Shell extension can be found at
[http://www.secure-endpoints.com/openafs-windows-roadmap.html\#shell
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

### Project: Port OpenAFS to new architectures

#### Status: Unclaimed

OpenAFS is a cross-platform distributed filesystem. Obviously we'd like
it to run on \*every\* platform. We currently have no coverage of the
\*BSD OSes. We'd like to fix that.

The goal of this project is port OpenAFS to a new OS of the student's
choice. Experience with kernel programming is a must, however,
experience with OpenAFS is not necessary.

A student choosing this project will be able to list on a resume and
apply the skills necessary for kernel development, especially with
regard to filesystems. Skills applicable to other kernel data access,
manipulation and locking will also be learned.

Estimated difficulty: *moderate to hard*

### Project: OpenAFS website redesign and update

#### Status: Unclaimed

OpenAFS' website is designed around the experience of developers. End
users and administrators may find the web site to be difficult or
frustrating to use.

The goal of this project is to provide a web site which offers an
experience to users tailored to their needs, or, for administrators who
wish to or have deployed OpenAFS, provides ready access to the
information required. At the same time, the web site should be
sustainable given the skillset of people maintaining the site and the
data therein.

Any technology which can be adapted to handle the content of the web
site and the needs of the project is acceptable.

The student will be responsible for determining the needs of the openafs
community that the web site will satisfy. This will be done by working
with the OpenAFS gatekeepers and surveying the community participants.

A student choosing this project will be able to list on a resume and
apply the skills necessary in web site design for any number of projects
with virtually any web site.

Estimated difficulty: *easy to moderate*

### Project: OpenAFS ptserver extensions for additional authentication types

#### Status: Unclaimed

In order that authentication systems other than Kerberos 4 be able to be
first class authentication systems in the OpenAFS space, extensions to
the OpenAFS protections service need to be added.

More detail on this project can be found [here](pts.txt).

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

Estimated difficulty: *moderate*
