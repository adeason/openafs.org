---
title: OpenAFS, Network Identity Manager and Google Summer of Code
---

The OpenAFS community participates in Google Summer of Code by
sponsoring students working on OpenAFS and related open source projects
such as kAFS and Network Identity Manager

[Skip to the list of accepted projects for 2010](#accepted)

What is OpenAFS?
----------------

OpenAFS is a 100% open source globally distributed file system derived
from IBM AFS commercial offering as of 1 November 2000.  Since IBM
released the source code OpenAFS has thrived adding support for new
platforms while enhancing its overall performance, scalability and
usability. 

OpenAFS has a large, mature codebase of over 800,000 lines of code. It
isused by large enterprises, universities, and research
establishmentsworldwide, and plays a part in fields from finance through
space explorationto quantum physics. Developing code for OpenAFS gives
you the opportunity tomake a significant difference to a product that is
in real-world large scaleproduction use, and to learn key development
skills. We have a large,supportive, community of developers who are keen
to see new developers enter our project, and happy to help out as you
get up to speed.

What is Network Identity Manager?
---------------------------------

Network Identity Manager is a client-sidetool designed to simplify the
acquisition and management of network identities and the credentials
used to providesecure identification to network services on Microsoft
Windows.  In 2010, students, faculty, and researchers among others must
be able to access services distributed around the world, managed by
different organizations, and deploying different network authentication
technologies.

As an example, a scientist at the U.S. Department of Energys Fermi
National Labs must be able to access systems that require three
different forms of network credentials:

-   Kerberos v5 ticket granting and service tickets
-   Andrew File System (AFS)tokens
-   Short Lived Credential Services X.509 Public Key Certificates

Traditionally, the acquisition and renewal of each credential type would
be performed using distinct tools. The Kerberos v5 ticket granting
ticket would be obtained and managed by a Kerberos v5 Ticket Manager
(MITs Leash on Windows or Kerberos.app on MacOS X).The AFS Tokens would
be obtained by a tool provided by OpenAFS (aklog or afscreds). The short
lived X.509 certificate would be obtained by a tool designed to work
with either a Kerberized Certificate Authority (KCA) or the Globus
MyProxy Credential Management Service. With each new credential source,
the complexity for the end user is increased.

Network Identity Manager reduces this complexity by implementing a
Single Sign-On (SSO) framework that permits an initial authentication to
retrieve not just a single credential but all of the derivative
credentials necessary for the user to perform their task.There have been
many organization specific tools that have been developed over the years
to obtain mixed credentialsUnlike previous tools what makes NetIdMgr
special is its modularity.Its pluggable framework model does not require
all of the technologies to be integrated by the same organization. Nor
do all users have to be given access to the same combination of identity
and credential provider modules.

GSoC 2010
---------

As always, the [GSoC 2010
FAQ](http://socghop.appspot.com/document/show/gsoc_program/google/gsoc2010/faqs)
is a worthwhile reading for anyone involved or considering involvement
in the Google Summer of Code program.

OpenAFS is a challenging project to develop for. It is a large and
complexproject that has developed over nearly 3 decades. The code must
work across awide variety of different operating systems, and is heavily
multi-threaded inplaces. On Unix, the OpenAFS client runs within the
machine's kernel, whichcan significantly complicate the development
process. As an enterpriseproduct, OpenAFS relies upon significant
underlying infrastructure, which adeveloper needs to get running before
they can test any OpenAFS code. Inaddition, OpenAFS is primarily written
in C, with all of the attendant issuesof memory management and pointer
manipulation.

These challenges mean that students who successfully complete a Summer
ofCode are likely to leave with significant new skills. Real world
experience ofdeveloping for distributed systems, kernel programming,
building testinfrastructures and developing thread safe code are key
skills to develop, andwe're happy to help you to learn them. Please join
us on \#openafs on freenode,in the Jabber conference
openafs@conference.openafs.org, or on theopenafs-devel@openafs.org
mailing list.

### Background reading

If you are interested in working on OpenAFS this Summer (and perhaps for
the rest of your life) here are some things that we recommend you do:

1.  If you are unfamiliar with programming in C, see if yourUniversity
    has any resources available for assisting their studentswho want to
    learn C.  If that is not possible, get yourself agood book and try
    your hand at it. "The "C Programming Language, 2nd edition" by
    Kernighan and Ritchie is widely considered to be an excellent
    reference text.
2.  If you have no idea what multi-threading is or what
    mutexes,read/write locks, or critical sections are, go to the
    library andfind yourself a book.  Preferably one that does not
    specialize in Java, Win32 or Posix threads, but a good general
    multi-threadingtext book.
3.  Read the[IBM AFS documentation/](http://docs.openafs.org). We are
    inthe process of rewriting this documentation to reflect
    thefunctionality that is now available in OpenAFS - we apologise
    that some of it is still out of date.
4.  Try your hand at building your own DNS, Kerberos and AFS
    infrastructure. ["Distributed Services with
    OpenAFS"](http://tinyurl.com/cexwea) is an excellent cookbook that
    walks though all of the steps necessaryto get all of the pieces up
    and running.

### Requirements

If you apply to OpenAFS please be aware of the following:

1.  You may not have a second job when working on OpenAFS GSoC.  We
    expect a minimum of 30 hours a week of dedicated work on your
    project.  It is likely that you will need to spend more time than
    that when you include the time spent communicating with
    yourmentor(s), and on developing new skills necessary to complete
    yourproject.
2.  You must have excellent network connectivity on a regular basis.  It
    is extremely hard to develop for a distributed network file system
    without access to the Internet.  In particular, you needto be able
    to access source code repositories, Kerberos KDCs for
    authentication, and OpenAFS services.  This will require that abroad
    range of both tcp and udp ports be open for access to theexternal
    world.  If you are dependent upon your University'snetwork and they
    firewall access to the outside world, it may be verydifficult for
    you to work on OpenAFS.  Access to Jabber conference rooms and IRC
    for communication with your mentors and the community are critical.
3.  You must know how to compile a C program and use a debugger at a
    rudimentary level.  For Linux, gcc and gdb.  For Windows, Visual
    Studio 2005.
4.  The time that our mentors spend working with you on a GSoC projectis
    extremely valuable. The majority of our mentors are undertakingthat
    role in addition to full time employment. Please make the mostof
    their time. If you are having a problem, tell us about it as soonas
    possible so that it can be addressed.  If you promise to deliver
    something, do so or warn your mentor as soon asyou know that you
    will miss the promised delivery date.  If yourmentor is not
    available, ask on the IRC channel or the Jabberconference room, and
    other members of the community will be happy tohelp.  We will do all
    we can to make GSoC a success for you, ifyou put in the effort at
    the work and the communication, but we willfail you if you're not
    putting that effort in.

Communicating with the OpenAFS Community regarding GSoC
-------------------------------------------------------

You can speak to members of the OpenAFS Community using three forums:

1.  Jabber Conference Room: openafs@conference.openafs.org
2.  Internet Relay Chat: freenode.net \#openafs channel
3.  Mailing list: openafs-devel@openafs.org

Accepted Projects
-----------------

### OpenAFS

The following are a list of projects accepted for Summer of Code 2010
forOpenAFS.

#### An alternate implementation of a userspace helper interface for Linux kafs

##### Student: Weylan (Wang) Lei

During last year's Google Summer of Code, an interface for allowing use
of OpenAFS userspace programs with kafs was developed. This was found to
not be acceptable to the Linux kernel core due to the pioctl ultiplexor
system call. An alternate approach using [gs]etxattr(), add\_key() and
keyctl() and /proc with O\_NODE was done; This year's project aims to
extend upon that work.

#### A port of OpenAFS to NetBSD

##### Student: Matt Smith

Around the same time the original Linux port of AFS was done, a port to
NetBSD was also available. While NetBSD has evolved, the original AFS
port did not keep pace. Since then, a port to NetBSD has been highly
desired. This project will port the OpenAFS client to run on NetBSD.

#### Encrypted storage

##### Student: Sanket Agarwal

The AFS protocol offers encryption for data transport from client to
server.However, that data is stored on the server in cleartext, where it
canpotentially be read by the administrators of that server. This poses
a realworld problem for organisations who wish to outsource the
provision of theirfile storage, whilst keeping their data confidential.
This project wouldaugment the existing AFS client to support encrypting
data blocks beforesending them to the file server. Additional
enhancements would manage user anddata keys in such a way that a user
can share encrypted files with other AFSusers of their choosing, and
protect the names of files, in addition to theircontents. This is a
challenging project, during which the student will gainan in depth
knowledge of kernel programming, distributed systems, andcryptography.

#### Unix or Windows Cache Manager support for Apple Doublefiles (Extended / Posix Attributes)

##### Student: Kelli Ireland

In order to store arbitrary metadata (aka attributes) with files or
directories in file systems that do not have the necessary native
support Apple developed the[Apple
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

#### Implementing Microsoft's Safe String (StrSafe.h) Library for UNIX/Linux

##### Student: Jonas Sundberg

Microsoft has developed a safe C String manipulation library
(StrSafe.h).  The advantages of the Strsafe functions include:

-   The size of the destination buffer is always provided to the
    function to ensure that the function does not write past the end of
    the buffer.
-   Buffers are guaranteed to be null-terminated, even if the operation
    truncates the intended result.
-   All functions return an HRESULT, with only one possible success code
    (S\_OK).
-   Each function is available in a corresponding character count (cch)
    or byte count (cb) version.
-   Most functions have an extended ("Ex") version available for
    advanced functionality.

It is the opinion of the OpenAFS Gatekeepers that the StrSafe.h
functions are superior to anything currently available in all of the
UNIX/Linux and Windows environments supported by OpenAFS.  OpenAFS would
like to be able to make use of the StrSafe.h functions on UNIX/Linux to
improve the code quality of OpenAFS and further enhance the code sharing
across Windows and UNIX/Linux.

This project is to implement from scratch a new implementation of the
StrSafe.h functionality for use on non-Windows platforms based entirely
upon the documentation provided by Microsoft:
http://msdn.microsoft.com/en-us/library/ms647466(VS.85).aspx

Previous Years
--------------

OpenAFS previously participated in the [2008](/developers/gsoc/2008final.html) and
[2009](/developers/gsoc/2009final.html) Summers of Code.
