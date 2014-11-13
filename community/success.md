---
title: OpenAFS Success Stories
---

Stanford Linear Accelerator Center
----------------------------------

AFS supports all of the following projects in that most of the tools
(compilers, CVS code trees, etc.) are in AFS as well as some of the data
input and output for their simulations (some Monte Carlo type
simulations but mostly data for GEANT simulations).

Here are three press releases about three very different branches of
science going on at SLAC.

The first is about our biggest experiment, BaBar. They proved a certain
kind of CP ("charge-parity") violation that explains in part the
asymmetry between matter and antimatter. This explains (in part) why
after the Big Bang more matter than antimatter was left over and the
universe could form. BaBar has taken around 2 PetaByte of data sitting
on tape but all their development tools and software code sit in AFS.  
BaBar uses AFS for worldwide collaboration, and distribution of their
coderepositories.

September 28, 2006 - New Form of CP Violation Discovered \
[http://home.slac.stanford.edu/pressreleases/2006/20060928.htm](http://home.slac.stanford.edu/pressreleases/2006/20060928.htm)

The second one is astrophysics research done at KIPAC (Kavli Institute
for Particle Astrophysics and Cosmology). They did mass analysis of
pictures from the Chandra X-ray Observatory and for the first time
directly observed the Dark Matter. The data itself is again not in AFS
but most of the development tools and software code is in AFS.

August 21, 2006 - Dark Matter Observed \
[http://home.slac.stanford.edu/pressreleases/2006/20060821.htm](http://home.slac.stanford.edu/pressreleases/2006/20060821.htm)

The next two are about our Synchrotron Radiation Lab (SSRL). They
highlight the application of SLAC's physics technology for completely
different branches of science.

August 2, 2006 - Modern Technology Reveals Ancient Science \
[http://home.slac.stanford.edu/pressreleases/2006/20060802.htm](http://home.slac.stanford.edu/pressreleases/2006/20060802.htm)

Archimedes Manuscript Yields Secrets Under X-Ray Gaze \
[http://home.slac.stanford.edu/pressreleases/2005/20050518.htm](http://home.slac.stanford.edu/pressreleases/2005/20050518.htm)

SLAC is currently expanding the computer center's relationship with SSRL
to provide AFS space for their tools like Gaussian (sequential and
parallel). They have also started to use our standard software
development tools (compilers, etc.) in AFS space.

Lastly, a very widely used toolkit, GEANT4
([http://geant4.web.cern.ch/geant4/](http://geant4.web.cern.ch/geant4/)),
for the simulation of the passage of particles through matter is being
co-developed at SLAC. Everything they do is in AFS. Among many, many
other things, this toolkit is used for medical simulations of radiation
treatments of tumors in the human body.

A summary of research performed at SLAC in
2006:[http://today.slac.stanford.edu/feature/holiday-message06.asp](http://today.slac.stanford.edu/feature/holiday-message06.asp)

Since 1998, SLAC has stored all user home directories in AFS.  AFS is
available to the several thousand machines in its batch farm and is used
primarily for thedelivery of binaries for batch jobs.

How much data (in TB)?                 5.5TB\
How many users?                          3247 \
How many volumes?                      18621\
How many file servers?                  15 fileservers\
How much storage per file server?   34GB to 1.6TB

ParallellDatorCentrum, Center for Parallel Computers at KTH
-----------------------------------------------------------

One of the computing centers in Sweden for research. Situated at KTH,
Royal Institute of Technology, Stockholm.  Written by Harald Barth.

Historical reasons:
-   In the infancy of network file systems different parts of the
    decentralized computing service groups at KTH were looking for a
    platform independent file system. The choice fell on AFS from back
    then Transarc, a CMU spin-off. Now, 15 years later, I can still read
    the files I saved into AFS as a student from a completely different
    hardware and OS. Compare that to the problems some researchers have
    reading data from "the previous computer system" I only have to bow
    my head for the folks who made the decision back then.
-   Once you have all your data available all the time on all systems it
    is very convenient and all kinds of automated maintenance methods
    make use of the fact. To abandon AFS would make it necessary to
    rewrite all this - accumulated since approximately 1992.

Reasons important back then but not as important any more:
-   As network speed has increased a factor of 100, hard disk speeds
    have only a factor of 10. So local cache on the
    workstations/computing nodes, once a crucial detail of AFS, is not
    the overall important reason to deploy AFS any more.

Reasons still important:
-   Design of location independence. Users access their files though
    globally unique path names which do not change. Period. The file
    system handles all mapping behind the scenes where to find the data.
    This is a central and not optional design point of AFS. This idea
    has been reinvented several times (URLs, for example in grid
    software), but I dare to say that no other system has so completely
    hidden the location details from the user as AFS. As it is hidden,
    the user or the middleware implementer or whoever is not tempted to
    use the information (my data is on bighost-5.edu) in a way which
    might break the system in the future (his data has been moved to
    bighost-6.edu).
-   The volume abstraction. Users files and directories are organized as
    volumes which are mounted as a kind of virtual disks into the global
    file tree. This abstraction allows it to move data between different
    servers online. No more interrupts of long running programs to
    upgrade a software, server or a storage system.
-   Source availability. Since the beginning KTH has had a source
    license (later open source) of AFS. Even if it not used every day,
    the knowledge that you have the means to recover your data even
    should your file system software provider go out of business is a
    soothing experience.
-   System independence. Both server and client OS and versions can be
    exchanged freely. For example no problem to write data on MacOSX,
    store it on a mix of Solaris and Linux servers and read it back on
    Windows.

Challenges for the future:
-   Encryption: AFS has means for data check summing and encryption.
    However the encryption standards of the 90s are not adequate any
    more. Work is in progress to support up to date encryption but could
    be sped up by adding developer time.
-   Network performance: The AFS protocol does not limit the
    implementation of additional network protocols and better bandwidth
    utilization in times where the speed of the network equals or excels
    that of the client HD. Developer time has to be spent to implement
    the mechanisms to do this in the framework of AFS.

AFS usage at PDC in numbers (2007-01-01):

Number of Clients: Unknown. PDC manages 5 clusters with a total of more
than 1200 computing nodes. When the clusters are new, they use to appear
around rank 70 of the top 500 list. All production systems use AFS.
There may be a single digit number of computers which have no access to
the AFS space. Add to that the number of researchers who access their
data from their own workstations from all over the Internet.

Number of simultaneous users: 100-200.\
Number of users with \$HOME in pdc.kth.se AFS space: Approx 3000.\
Amount of data in AFS: Approx 5TB.\
Number of volumes: Approx 6000.\
Number of files: Approx 65 000 000.\
Number of file servers: 11\
Approx storage per server: 1TB\

Pictage Inc.
------------

[http://www.pictage.com/](http://www.pictage.com/)

Pictage's business is worldwide.  They provide services to wedding
photographers who upload the photos they have taken. Pictage then makes
the photos available to the wedding party for photo selection and
printing.  Photos selected for printing are retouched by hand using
Adobe Photoshop.

Pictage uses OpenAFS to store all of the original photos, the processed
photos, and the web content.

Work flow is managed by the use of mount points and symlinks which are
placed within directories assigned to various photographers and their
associated events. 

Pictage storage has exceeded 200TB of data and more then 40 million
files.  They frequently push the limits of the AFS directory structures
running into the directory entry limitations. 

Directory search performance is one of their bottlenecks.  Unlike more
modern file systems, AFS does not use a B+ tree representation and
directory searches within the case-insensitive Microsoft Windows client
are linear in nature.  This wastes significant CPU utilization and clock
time.  Pictage had measured the performance loss on a duo-core Xeon
processor at between 3 and 5 seconds to open a file in Adobe Photoshop
when the directory contains 15,000 entries, because Adobe Photoshop will
request information forthe last 30 files it has seen, thus requiring
heavy usage of AFS directories.   OpenAFS for Windows 1.5.13 added an
optimization for cached files with registered callbacks that avoids the
performance problem for files that are known to exist.  With this
optimization in place, Pictage experienced file open times similar to
those experienced when opening files on the local filesystem.  For files
that do not exist such as Java class files, the optimization does not
apply, and the linear search must still be used.

Number of simultaneous users: 150 AFS client users; 1000 web server
users\
Amount of data in AFS: Approx 215TB\
Amount of AFS storage: 265TB with planned growth to 425TB in twelve
months\
Number of volumes: Approx 800,000.\
Number of files: Approx 200 000 000.\
Number of file servers: 70 with 10 more planned\
Approx storage per server: depending on age of server 1.2TB to 25TB

(statistics as of 22 May 2007)\

NCSA at UIUC
------------

HDF is a project that helps support the research projects that NCSA
provides computing services for.\
\
This page is prettier and has some more concise history: \
[http://www.ncsa.uiuc.edu/News/Access/Archive/backissues/96.1/hdf-tng.html](http://www.ncsa.uiuc.edu/News/Access/Archive/backissues/96.1/hdf-tng.html)\
\
They've recently split off from NCSA to form The HDF Group: \
[http://www.hdfgroup.org/](http://www.hdfgroup.org/)\
[http://www.hdfgroup.org/users5.html](http://www.hdfgroup.org/users5.html)\
[http://www.hdfgroup.org/HDF5/release/platforms5.html](http://www.hdfgroup.org/HDF5/release/platforms5.html)
\
\
Their source tree and everything is in the NCSA AFS cell and the build
process is scripted for all the different architectures they support. 
Their build systems range from clusters to servers to desktop systems
and the binaries can be dropped right into AFS which users grab via
ftp.  They need an authenticated file system that supports all of those
platforms.

NCSA's Security team uses AFS for storing security incidents and
collaborating with off-site users.

And some comments from Christopher Lindsey about future directions:

"I can tell you about possible future direction.\
\
"We've all noticed that the stand-alone University model doesn't
work. Just like businesses that merge, Universities are finding that
they need\
to collaborate with other research institutions to make their
proposalscompetitive.  You throw in concepts like grid computing (i.e.
TeraGrid)\
and you suddenly have a diverse, disparate set of sites that need
to collaborate.\
\
"This is where AFS becomes a player.\
\
"I believe that we currently use it as a giant swap file space for
different projects -- one supercomputer site needs access to security \
net flows, so we put them out there, set the acls, and voila.\
\
"Future projects on supercomputers will leverage AFS as well.  I
don't know how much detail I can go into, but there is a proposal that
will \
be submitted on Jan 22 that will revolutionize how HPC resources
within the TeraGrid are used.  The ubiquity and security of AFS make it
the \
perfect foundation for this project.

"As far as timings, we might be able to do some dprof timings between
here and Argonne Labs over iwire
([http://www.iwire.org/](http://www.iwire.org/)).  Ironically,
the bottleneck there will be the GigE NIC on the AFS servers."

United States Geological Survey
-------------------------------

#### Background

The use of AFS at the United States Geological Survey, USGS, started in
response to a requirement to provide natural hazard information on the
Web so that it could continue being delivered to the public even in the
event of large-scale regional disasters.  The driver for this activity
was the inability of US Geological Survey to provide water level
measurements during hurricane  Floyd in 1999 just when that information
was needed most by emergency managers, because our database servers and
Web servers were rendered useless by power and networking failures in
affected states.

This regionally distributed, "no single point of failure" delivery Web
service relies in part on AFS to provide regionally replicated file
content at "modules" housing AFS file servers and Web servers in Menlo
Park, California, Sioux Falls, South Dakota, and Reston, Virginia.

#### Why are we using AFS

AFS was chosen as it was the only multi-platform software available to
provide geographically distributed content replication, access control,
and user transparency as required by our project.

#### How we are using AFS

Three Web servers at each module have an identical view of read-only
copies of data provided by AFS. Bringing on additional Web serving
capacity is as easy as adding another Web server which is also an AFS
client.  A commercial DNS service with wellness checking, Akamai,
resolves hostnames to these geographically distributed Web servers,
which are checked every minute for availability.  Failure to contact Web
service on any one of these systems results in the corresponding IP
address being taken out of DNS resolution.

This National Web server system known as, NatWeb, delivers Web content
for 150 unique USGS websites. In 2006  NatWeb delivered an average of
1.2 million web pages and 191 gigabytes of data per day, for an annual
total of 453 million pages and 68 terabytes.  It has experienced a
roughly 50% increase in utilization annually for the last three years.
 We serve data as diverse as

-   Toxic Substances Hydrology http://toxics.usgs.gov/,
-   Northern Prairie Wildlife http://www.npwrc.usgs.gov/,
-   The Cascades Volcano Observatory http://vulcan.wr.usgs.gov/,
-   National flood and drought  conditions
    http://water.usgs.gov/waterwatch/ and
-   3D  images of national parks http://3dparks.wr.usgs.gov/.

Our use of AFS is tied nearly exclusively to Web service.  All content
is replicated to all regions.  The R/W master for content is located in
the same region as content maintainers, so R/W and replicated R/O
information is distributed evenly across regions. Any one region can
drop from the network, and the associated Web information will continue
to be served to the public, although updates cannot be accomplished in
this condition without administrator intervention.

#### AFS Site Size

We are a small AFS site by most measures. AFS usage specifics (with some
rounding):

-   500 AFS users
-   1300 volumes
-   0.64 terabytes of data

Our architecture uses custom programming to detect changes to AFS
content. Volumes containing  updated content are automatically released
(replicated to remote locations) every 15 minutes. The file servers
collectively execute over 2000 "vos release"s per day.

#### Architecture

Our server implementation is entirely Sun/Solaris 10 based.  At each of
our three module locations:

-   an AFS database server -- Sun 250
-   3 AFS file servers, and 1 warm spare -- Sun V240
-   all 4 file servers are directly attached to a Sun 3510FC Fibre
    Channel disk array (RAID 5 + 1)
-   3 Web servers -- Sun V210

There are three hostname/IP address pairings by which all AFS file
services are known, as well a separate hostname and IP address which is
always associated with the same computer.  By shutting down AFS
services, and shuttling the appropriate IP address from one system to
another, we can effectively fail over AFS file service from one system
to another.

#### AFS Clients

Our AFS clients fall into two major categories, the Web servers which
serve content to the public, and the content maintainers who have AFS
installed on their desktops.

Our content maintainers are overwhelmingly using Windows XP, with
perhaps 5% using Mac OS X and still smaller numbers using Linux and
Solaris.

#### Staffing

Our entire staff consists of 3 full-time employees, 1 part-time
employee, and one manager. These individuals manage the budget,
hardware, operating system maintenance, security, software updates,
custom programming and user support for both the AFS and Web components
of the service.

Robert Carter, Duke University Office of Information Technology, shared:
------------------------------------------------------------------------

We're using the OpenAFS client code pretty extensively, andhave been
since fairly early in its release cycle. We're running theOpenAFS client
on all of our Windows lab machines (we cheered the day theWindows
clients became available, since we'd never found the funding to
putTransarc clients on our Windows machines, and since the students had
beenclammoring for access to their AFS home directories for quite a
while).We're also using the OpenAFS client on our MacOS X systems,
although itwill be summer before we actually roll out OS X in our campus
labenvironments. We've recently started a publicity campaign on campus
to getstudents and faculty to take advantage of the OpenAFS client
installationon their personal computers wherever possible, viewing AFS
access fromdesktop systems throughout the campus as one of the primary
ways to movetoward decomissioning insecure FTP access to our central
facilities -- wefind that running AFS clients on desktop systems greatly
simplifies ourusers' use of web development tools like DreamWeaver,
since with theclient, they can publish changes directly into their AFS
home directories.

On the whole, we've had very few problems with the client -- most ofthem
related to the installer or to versioning issues with earlier versionsof
the code. We're still working on completing our integration work
withWindows 2000 and XP -- we've established cross-realm trust between
ournascent Active Directory and our existing K5 realm, and we've been
workingon trying to arrange to have AFS tokens derived locally from the
K5 ticketsgranted to users on our Windows systems at login time. So far,
that's notworked quite as well as we'd hoped, but that's purely a
Windows problem,not an OpenAFS problem -- we've worked around it with
some simple scriptingat the client end for now, but I'm hopeful that
when we get a chance to dosome more developement work over the summer,
we may find a means to maketokenization transparent on our Win2K/XP
systems.

We're hoping to do some testing early in the summer with the
OpenAFSserver, and provided that we can get everything to work out, to
startmigrating our server farm from the Transarc server code to the
OpenAFSserver code. We've been using AFS at our site since the early
1990s and we have a modestly-large AFS cell comprising Solaris servers
of various vintage(Solaris 2.6, mostly, with some Solaris 8 on our more
recent acquisitions).

Jimmy Engelbrecht, Kungliga Tekniska Hgskolan Elektro Department, shared:
-------------------------------------------------------------------------

Our cell runs on OpenAFS fileservers on Tru64 5.0a. We have 0.5 - 1 TB
of dataand about 250-400 clients. We are VERY pleased with the
fileserver, it's quite stable, no crashes in the 6 months we've been
running them.

Our 15 Solaris clients are running OpenAFS, we are very pleased withthis
one. (We plan to have about 100 Solaris hosts in a few months.)

Chris Huebsch, volunteer administrator for Dr. Wilhelm Andre Gymnasium, Chemnitz, Germany, shared:
--------------------------------------------------------------------------------------------------

I first used AFS in 1995 during my first year as a student. Now I am
a member of the academic staff at Chemnitz University of Technology.Two
years ago I started helping the Dr. Wilhelm Andre Gymnasium (Gymnasium is
the German word for high school) to build up their computer lab. At that
time we had only 30 workstations and one server using NFS.

Last year (2001) we were very lucky and got enough money to build up a
large intranet. At least large for a school. We now have 4 fileservers
(each with 400 GB hardware RAID) with a total of 1.6 TB AFS space.
Normal school-installations have to live with 50 to 100 GB on Windows NT
or Novell.

We have 1500 users and 100 clients (the next 50 clients are in
sight).The primary platform is Linux. Some workstations run Windows 2000
for the sake of legacy applications.

Before OpenAFS, we used NFS and Samba. There were no real problems with
that solution because we had very little filespace (20 GB) on one server.
But we saw the problems arising with 4 servers and much more capacity:
The load on the server would rise and there was no transparent way to
reorganize the location of the directories without heavy work onthe
users side due to absolute path names in configuration files! Neither NFS
nor Samba provide ACLs in a smooth way. It would have required patching
and installing lots of additional software. And quotas are not
really easy to use. And last but not least: AFS is just cool :-)

OpenAFS saves us a lot of time. This starts with the installation of
our workstations via RedHat KickStart and NFS. Installing 100 clients
in parallel (each requiring about 1.5 GB of binaries) produced
an unsustainable load on one server. So we decided to create an
installvolume and have it replicated on each AFS server. Each AFS
Server machine runs a NFS re-exporter. With a round robin DNS-entry for
theNFS installation server we can quadruple the capacity of our
install source without writing cryptic KickStart configurations.

Of course all the well known benefits of AFS (automatic backups,
fault tolerance, etc.) help us save a lot of time and stress.

One of the school specific problems with AFS is that we need an
operation mode for our workstations and servers allowing users to log in
using AFS authentication, but without allowing access to the home volumes
of the users. We need this mode for writing "electronic tests". We try
to solve this with negative ACLs for a special test-writing-group.

The next problem is to distribute some of the rights
of system:adminstrators without making users members of that group.
For instance we like to give teachers the right to change quotas of
their puplis' volumes but not their own. We think we will solve this with
a middle-layer web page.

At the moment we do not buy any commercial support. But we are trying to
extend our cell through the whole city with 160 sites and 50000 users. At
that time we will need some help.

Since writing this story two years passed by.

Currently we have 1733 volumes on-line, 1585 of them user-volumes.
The aggregated quota is 210GB with 90GB used. The initial user-qouta
is 50MB. With the help of a PHP-based web-tool the qouta can be changed
by a teacher. Basic fs- and vos-operations (setacl, mkmount, release)
are done by this teacher manually at command line-shell.

In this 2 years of operation there was not a single-data-loss because
of AFS (not that there has been any data-loss at all :-) Even the
sudden death of a file-server-machine didn't corrupt data. The second
incident of this kind wasn't event noticed for some time.

The 4 AFS-server-machines (Athlon 1400, 1GB RAM, E1000-Network)
still have an avg-load of 0.02. Obviously there is no need in replacing
them in near future.

3 Months ago we performed an update from RedHat Linux 7.2 to Fedora Core
1. Except some minor troubles with the NFS-reexporters and the cfengine
itworked seamlessly. At the same time OpenAFS 1.2.11 was installed
without any pain at all. OpenAFS 1.2.3 was used before.

We use our file-servers not only for user-files but also for backup
andsystem-maintainance files. Daily system-backup of all servers
(mail,ldap, ...) is done to an AFS-volume for each server. The volume
isreplicated to another fileserver. We use cfengine for
administrative tasks. The cfengine-repository is stored in AFS and
distributed by AFS and not the cfengine-file-server.

The balancer is used to spread load between fileservers by moving volumes
in respect of week-usage and number of volumes.

As a next step we will add an fifth fileserver on a remote location
(onlyconnected with 128 kbit). We hope that by replicating a
ro-db-server and many volumes to that server will be sufficient to keep
things working.

Derrick Brashear, Carnegie Mellon University Computing Services Division and OpenAFS volunteer, shared:
-------------------------------------------------------------------------------------------------------

Computing Services rolled out OpenAFS to both clients and servers early,
and now runs modern versions on Solaris 2.6 servers, as well as on
Solaris 7 and 8 and locally-updated Redhat 6.1 clients. Additionally,
the OpenAFS Windows NT client is being tested general rollout.

Despite often using pre-release versions of the software few problems
have been experienced, and fixes have generally been quickly
forthcoming, either internally done and contributed back to the
community, or thanks to the many active contributors to the ongoing
success of the project.

Matthew E. Hoskins, New Jersey Institute of Technology University Information Systems, shared:
----------------------------------------------------------------------------------------------

University Information Systems (UIS) started testing OpenAFS about
7 months ago for the purpose of binary standardization across our
web, application, and database servers. Those 7 months have been very
stable and we are starting to roll our cell into production. We currently
have\~140gb of vicep space across four servers (2 linux, 2 solaris8).
Thecell gracefully handled two events of failed disks without
interruption.

OpenAFS has and will continue to help me keep our 45 web,
application,and database servers running the same versions of binaries
and scripts.

As our programmers learn of the features and capabilities of OpenAFSthey
increasingly want their workstations added as clients also (mixture of
sun and linux boxes). As trust builds in OpenAFS we will also
startmoving production data into volumes rather than local storage. This
will allow applications to "float" between nodes as necessary.

Our site has been a long time Transarc customer for our academic
cell(2.6Tb, 6 fileservers, 17000 users, 100s of workstations), The
OpenAFS project and its contributors are breathing new life into a
wonderful technology.

Some features that would be of value:

-   OpenAFS documentation on kaserver -\> krb5 migration
-   OpenAFS documentation on setup for new krb5 cells
-   All logging via syslog
-   better end-user command line utilities (An "ls" replacement
    thatbetter described ACLs would be awesome)

I am working on converting all my various perl scripts into a perl module
so i can contribute it and open it up for community development.

Sharing your OpenAFS Story
==========================

Please contact the [OpenAFS
Gatekeepers](mailto:openafs-gatekeepers@openafs.org) to share your
success story.
