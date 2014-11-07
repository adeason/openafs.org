---
title: OpenAFS Newsletter, Volume 4, Issue 4, October 2012
layout: page
category: newsletter
permalink: /newsletter/newsletter-2012-10-volume004-issue04.html
---

# OpenAFS Newsletter, Volume 4, Issue 4, October 2012

## /afs/Introduction

Happy Fall, AFSers!

This edition of the newsletter is full of good stuff. Below is our regular "Did You Know..." and the final part of our case study on
Windows Roaming Profiles. I've had a lot of fun reading the previous parts and comparing notes on the challenges of Windows Roaming Profiles and
OpenAFS. As Part III was written by yours truly this time around, I tried to include some of what was different and unique about
Windows Roaming Profiles to our site here.

OpenAFS is announcing a new initiative to form an OpenAFS Foundation. This is really exciting news, and you can find more details on the initiative itself and how you can participate in the below Foundation Creation Committee announcment. While major milestones will also appear in the newsletter, to keep up with the day to day happenings, you should join the foundation-discuss@openafs.org mailing list.



And we hope you enjoy an OpenAFS retrospective from former Gatekeeper and Elder, Russ Allbery.

Like OpenAFS itself, this newsletter is a community resource. If you have comments, ideas for topics, bits you would like to share with the community, then send along an email to newsletter (at) openafs.org .

## Foundation Creation Committee

A new initiative has been started to
form an OpenAFS Foundation, and that a Creation Committee will work
toward completing this task within the next year.

First of all, we would like to acknowledge the past work on this
effort and thank the individuals who worked on creating a foundation.
While their efforts did not result in an actual foundation so far,
they have been pioneers in unknown territory and achieved repeated
community discussions, gathered vast amounts of information,
evangelized OpenAFS to garner industry support—including some Fortune
500 companies—and those are just the highlights.   On the behalf of
the community, we want to take this opportunity to thank Russ Allbery,
Jeff Altman, Derrick Brashear, Laura Stentz, and all previous Elders
for their tireless efforts.  While the extent of their contributions
may not be visible to all, the OpenAFS project would not be what it is
today without them.

It has been quite some time since an official communication occurred
by the Elders regarding the proposed setting up of a Foundation to
support OpenAFS.  Recently, there has been another wave of discussions
on the openafs-info list on the start of a foundation and related
topics, fueled by a lot of passion and the shared understanding that
OpenAFS can/could benefit from a non-profit foundation.  We believe
the flavor of a 501c3 non-profit organization, while hardest to get
awarded by the IRS, is the best fit for our needs.

For those unfamiliar with the nuts-and-bolts creation of a non-profit
foundation, here is a high-level description of the process, for which
we are pursuing a somewhat different overall strategy especially
catalyzed by Margarete Ziemer:

- A name needs to be chosen.
- The foundation needs to be incorporated.  Incorporation fee must
be paid. Depending on which state we incorporate in, which has certain
benefits and drawbacks, more or less upfront work is required.
- A provisional Board of Directors needs to be established, to be
guiding the process of establishing the Mission, Vision, Bylaws, etc.
of the foundation.  This provisional BOD will be active until the
first successful elections have been completed, and at that point, the
leadership will be transferred to the official BOD.  In our case, the
Creation Committee will take that function (see below).
- An application to be awarded non-profit status by the IRS (Form
1023) needs to be filed.   This requires submission of Bylaws, Mission
and Vision statements, which all have to be matching the IRS’
requirements for non-profit organizations.  It takes between weeks and
years for the IRS to award the permanent non-profit status, but a
temporary one can be issued in the interim.
- A bank account needs to be opened.
- An independent accounting firm needs to be found.  This should be
reasonably-priced firm to oversee future tax returns and future
non-profit-status-related filings of forms with the IRS.
Alternatively, it could be some larger accounting firm willing to take
on the foundation pro-bono.
- An independent law firm needs to be solicited to take on the
foundation.  Just like with an accounting firm, we should seek either
a reasonably-priced one or one with a big name and with a pro-bono
program, which would save the foundation a bundle.
- Permissions to do business, on a state-by-state level, must be
filed with the IRS.
- Permissions to do fundraising, state by state, must be filed with the IRS.
- Permission to do advertising bulk mails should be obtained.
- A foundation website needs to be created.

This list, while by no means complete, may serve as a mere indicator
of the complexity of the incorporation task, which sounds simple, yet
is anything but easy.  We will strive for completing the creation of
this Foundation and transition to the first BOD in less than one year.

With the support of the Elders, a new group (the Creation Committee)
has been formed to facilitate the creation of a Foundation.  As
mentioned above, this Creation Committee will take on the function of
a provisional BOD until the first properly elected board. The members,
of whom you can find bios at the end of this note, are: Derrick
Brashear, Todd DeSantis, Tom Keiser, Roman Mitz and Margarete Ziemer .
 The Creation Committee will transition leadership of the foundation
fully to the elected Board of Directors once it exists.

You can reach the Creation Committee with specific questions,
comments, or ideas at foundation@openafs.org. We are also creating a
community discussion list which anyone can join at
foundation-discuss@openafs.org.  Going forward, we pledge continuing
communication and we will be aiming for updates on at least a monthly
basis.

It is always difficult to re-kindle the excitement for a long-term
project, and to look at a long history with nothing but a keen eye on
learning for tomorrow.  Yet we are asking you to help us move OpenAFS
forward and give it the place, care, and appreciation it deserves in
general, beyond the current user and developer community.  We are
asking for, and counting on, your input in our moving toward our
mutual goal: to constructively protect, grow, and strengthen OpenAFS

Roman Mitz, on the behalf of the Creation Committee



## Changes to OpenAFS Elders

"The 'Council of Elders' is responsible for the overall direction of the OpenAFS project." Recently, two of our Elders stepped down: Jeffrey Altman and Russ Allbery. OpenAFS very much appreciates the contributions of the outgoing Elders, who are now designated as Elders Emeritae.

The current list of Elders can be found at:

http://www.openafs.org/credits.html



## Changes to OpenAFS Gatekeepers

"Gatekeepers are responsible for the day-to-day maintenance of the OpenAFS code."

Russ Allbery has stepped down as an OpenAFS Gatekeeper. And OpenAFS welcomes Ken Dreyer to the Gatekeepers.

The current list of Gatekeepers can be found at:

http://www.openafs.org/credits.html

## Introducing Ken Dreyer

I am a system administrator for the US Geological Survey and work
primarily on USGS's general web application hosting platform. This
platform is built on AFS and is distributed across the United States.

I'm interested in anything to do with AFS, Kerberos, and open source
in general. I'm a package maintainer for the Fedora and EPEL projects,
and I'm also a co-maintainer for the OpenAFS packages in RPM Fusion.
At USGS I also lead the efforts to get USGS on GitHub, and to
legitimize open source publishing and collaboration across the bureau
overall.

As a relative newcomer to OpenAFS and open source development, I'm
interested in practical ways to lower the barriers to entry for other
newcomers to open source, OpenAFS included. This is also why I enjoy
packaging: it makes open source more accessible to newbies. My
immediate vision for my role as OpenAFS Gatekeeper is 1) to redesign
the openafs.org website, 2) assist Derrick and Jeff in the Gerrit
grind, particularly around documentation.



## An OpenAFS Retrospective from Russ Allbery

I don't really remember exact dates and the like at this late date for all
the milestones when I became involved in AFS.  When I first came to
Stanford in 1993, we were still mostly using NFS for home directories but
were just starting to deploy AFS more broadly.  I remember running our
convertoafs process probably sometime around 1994 or 1995.

One of my early jobs for Stanford was to help maintain our site-wide
software distribution (all in AFS), which originally was for SunOS,
ULTRIX, AIX, and NeXTSTEP and later added OSF/1 (Digital UNIX (Tru64)),
IRIX, Solaris, HP-UX, and (much later) Linux.  That was called pubsw, and
remnants still linger, although we're moving away from it in favor of
using distribution packages.  That was my first major experience with many
of the unique features of AFS (replicated volumes with support for staging
changes, @sys links, rich access control) and the unique problems with AFS
(patching software to avoid cross-directory hardlinks, or to use access()
to check permissions instead of trusting UNIX file mode bits).  There's a
presentation on the scheme for large-scale software management in AFS that
I and a co-worker developed on my AFS notes page:



    http://www.eyrie.org/~eagle/notes/afs/

I've helped run the AFS infrastructure at Stanford off and on since 1997
and helped release as open source a bunch of the tools that we put
together for maintaining that infrastructure (and still have lots of tools
that I'd like to get to cleaning up and releasing "someday").  I also
ended up taking over the Debian AFS PAM module, which became
pam-afs-session, and taking over maintenance of the Stanford-local version
of kinit, called kstart, which is still useful for running things with
Kerberos tickets and AFS tokens.

My involvement with the maintenance of the core AFS code has always been
somewhat ancillary, since I've never had the time to devote to it that
Jeff and Derrick and others have had.  Probably the biggest projects I
worked on were the conversion of the old IBM reference documentation into
manual pages (with most of the hard work done by other people) and the
libkopenafs library for a simple interface to PAG manipulation.  I tried
to do some code review and sometimes (but not frequently) succeeded.

I still believe strongly in the technology and am still advocating for it
at Stanford.  I think, with some substantial work and improvement, AFS or
a descendent continues to fill a much-needed niche in distributed file
systems that nothing else is satisfying.

## Support for Linux Kernel 3.6

Linux Kernel 3.6 is now out for many a distribution. Of course, this means work for our friendly OpenAFS developers in adding support for the new
kernel version.

All patches needed for Kernel 3.6 are now merged into the Master and the 1.6 branches in GIT. There was a delay in merging in these patches as
some of the buildbot compilers got more picky after an upgrade.

## Libtool Changes



As those of you who've been watching gerrit will have noticed, we're now using libtool to manage some of our libraries on Unix. Whilst I've been discussing doing this for a number of years, I thought it might make sense to describe the motivation, and the current state of the libtool work.

The OpenAFS tree is complex, because code is built in many different configurations as part of the build process. For most library objects, these configurations are:

- LWP
- pthreaded
- pthreaded and position indepedent (PIC)
- kernel
- ukernel
- ukernel PIC

Generally, it isn't safe to link objects that are built in one way with objects that are built in another, as the different compiler options can change the API. In particular, mixing LWP and pthreaded objects within the same binary can cause very unpredictable results. Historically, all of the pthreaded library code has been collected in libafsauthent and libafsrpc. However, the pthreaded ubik servers build their own copies of a lot of various libraries, as well as linking against libafsauthent. Lots of other bits of the code have precarious combinations of LWP and pthread objects

So, we have a tangled mess of libraries, none of which work particularly well with each other, and the situation where individual objects can be built as many as 15 times, and adding a new object to the tree can involve changing lots and lots of Makefiles.

In addition, because our only libraries with map files are libafsauthent and libafsrpc, we have no way of enforcing boundaries between individual modules. As nothing in the tree actually uses the shared versions of libafsauthent and libafsrpc, there's no real testing for the completeness of those map files, either.

I've been talking for a while about fixing this, and over that time it has become clear that libtool is the least-worst option. So, I started taking a look at using libtool to create a cleaner set of libraries. YFS have kindly funded that work, and contributed it to OpenAFS

The idea is that each directory that builds a library builds three versions of each library object - a LWP one, a pthreaded one, and a PIC one. The 'old' library name (libcmd.a for example) remains the LWP library. liboafs\_<library> is then built as the pthreaded variant. libtool takes care of managing the PICness of these objects. libtool aware programs can just use libtool to link against the .la file, but it is also possible to link against the static or shared versions directly. Each directory has its own symbol list, which clearly lists all of the functions and variables from that module which are available to other sections of the code.

libafsrpc and libafsauthent are still available for out-of-tree users, but these are built using the objects already built by libtool, rather than building the tree yet again. All of the directories which used to build their own copies of library objects have been modified to use the ones that libtool has built, so the number of times we build things is much less.

Now that this is done, other work should be possible. We should be able to use the libtool archives, rather than the various \*\_pic.a objects which have appeared in the tree over the last few years. It should be possible to gradually move ukernel towards using user space libraries for its functionality, rather than building half of the tree itself.

And, most importantly, we're one step closer to knowing what our public interface looks like. It is now possible to take the contents of the symbol files, and rearrange header files so our interface is clearly stated.

My hope is that from now on, we'll use the liboafs\_\* libraries for all new code. Doing so is straightforwards - there are a lot of examples in the tree.

\-Simon Wilkinson

## Discussion and Support Resources

If you find yourself stuck, fear not, help is just an internet connection away.

The openafs-info (at) openafs.org mailing list is an open mailing list for "discussing any aspect of using and deploying OpenAFS". List archives are available on many different websites, and you may find that others have even already tackled and solved your problem!

While responses on the mailing list are usually quite rapid, if you need to hold a more real-time discussion, consider either Internet Relay Chat (IRC) or Jabber. Members of the OpenAFS community hang out in the channel \#openafs on the FreeNode IRC network. Members also can be found on the OpenAFS Jabber channel... join room openafs on server conference.openafs.org . In general, you will find the Jabber discussion more oriented towards OpenAFS development and IRC disucssion more oriented towards deploying and using OpenAFS. After asking your question, you should stay around in the discussion channel since everyone in the channel is usually busy with their day job.

Commercial OpenAFS support is also available. A partial listing of commercial support providers can be found at http://www.openafs.org/support.html

OpenAFS documentaion is online at http://doc.openafs.org/ . The Reference Manual is especially useful for seeing what OpenAFS commands are available and what those commands are supposed to do. The Reference Manual also lists the OpenAFS Configuration and Data Files.

Finally, user contributed documentation, hints, and tips are in the AFSLore Wiki. The Wiki is linked at http://wiki.openafs.org/AFSLore/WebHome/

## OS X and Kerberos Configs

One change introduced in recent versions of Mac OS X is the Kerberos library distribution. Previously, Macintoshes shipped with MIT Kerberos. But
starting with Mac OS X 10.7, Macintoshes now ship the Heimdal Kerberos library. While protocol compatible (Kerberos), there are differences in
the underlying API, stubs for MIT Kerberos are missing, and the location of the Kerberos configuration files has changed. Depending on how the
particular application binary was written, you may need one or both of the Kerberos config files. But there is at least one minor difference
which can make the difference in configuration files that can make the difference between a working and not working install.

Previously, the Kerberos configuration file only lived at /Library/Preferences/edu.mit.Kerberos. But now the configuration file may either live in that location or in a more UNIXy location at /etc/krb5.conf . If you are not using Kerberos cross-realm authentication, you can just copy the same configuration file to both locations. If, however, you are using cross-realm authentication, be aware that the \[capaths\] section of the Kerberos configuration files are syntactically slightly different for MIT Kerberos and for Heimdal -- in Heimdal, one must explicitly name the realms instead of using a period to refer to a realm.

## Did You Know... AFS via the Web

FileDrawers is web based access to AFS. Written in php and via mod\_cosign or mod\_kerberos and mod\_waklog, FileDrawers uses a Kerberos identity to
obtain an AFS token on behalf of the user. With SPNEGO and mod\_kerberos, users with a properly configured web browser and Kerberos tickets
already obtained in the desktop environment will be able to access AFS via Single Sign On (SSO).

A future newsletter Case Study will go into more detail about FileDrawers. In the meantime, more information is available at http://www.filedrawers.org and http://www.modwaklog.org/ and http://www.openafs.at/files/slides/2Day\_04/Filedrawers.pdf .

## Case Study - Windows Roaming Profiles - Part III

Microsoft Windows is an important part of the computing infrastructure at the Cornell NanoScale Science and Technology Facility (CNF). To provide
as seamless a computing experience as possible across multiple computing platforms for hundreds of users, CNF endeavoured to integrate Windows
Profiles with the OpenAFS backend file storage.

Before OpenAFS, each windows workstation simply had one shared login for all users. This setup was not only insecure but messy. We at the CNF
decided to move to a multi-login model with Windows XP Roaming Profiles. Roaming Profiles allowed users to have their own Desktop loaded no
matter which workstation logged into. User application settings also traveled from workstaion to workstation with the Roaming Profile.

To ease management of our Windows XP workstations, we placed the workstations in a Windows Server 2003 Domain. And each user was migrated to his
or her own login account in the new Windows Server 2003 domain.

Of course, Roaming Profiles must be stored somewhere on the network. And because CNF had begun using OpenAFS as its main file store, also storing
the Windows Roaming Profiles in OpenAFS made a lot of sense. Already having their own UNIX home directory in AFS, users would also be able to
easily access their Windows files from any AFS-enabled CNF computer (linux, solaris, mac, standalone, SunRay, etc). But this meant making Windows
Roaming Profiles, which really expected to be running off a Windows file server, work with OpenAFS.

We also had the goal of each user having a single username and password to be used across all CNF systems. Experience had shown that with each
new password a user has to remember, the more likely the user is to start sharing the password, writing it down, etc. Cornell University as an
entity was (and still is) using Kerberos for its identity infrastrucutre. All members of the Cornell community already had a login. Cornell also
had a secondary Kerberos infrastructure for "guests" or outside users to obtain Cornell credentials to use computing resources. The
infrastructure for creating and managing both Cornell and Guest user Kerberos identities had already been built by and was maintained by
the central IT organization. So, tying into the central authentication system for CNF user accounts made a lot of sense. Cornell users
would be able to use their existing Cornell username and password to access CNF systems. And outside/external/guest users could use the
central university infrastructrue to obtain Cornell guest credentials for use at the CNF.

So that Windows has permission to access the Roaming Profile stored in OpenAFS, users must authenticate to AFS during the Windows login before
Windows attempts to download the Roaming Profile. The Windows OpenAFS client
calls this Integrated Login. While the central Kerbeos authentication infrastructures were run by Cornell, CNF still ran its own Windows
Server 2003 Domain, its own AFS cell, and its own Kerberos realm for its AFS cell. As a result, not only did OpenAFS Integrated Login need to
just work with Windows talking to the central Kerberos, but OpenAFS Windows Login needed to work with the multiple Kerberos cross-realm
trusts setup between the various Kerberos realms.

The Kerberos setup is as follows:

First, we had a Windows domain: AD.CNF.CORNELL.EDU - because Windows Active Directory uses Kerberos under the hood, this Active Directory domain
corresponded to the AD.CNF.CORNELL.EDU Kerberos realm which was part of and managed in Windows.

Second, we had a local CNF.CORNELL.EDU kerberos realm. This Kerberos realm was the Kerberos realm underlying our AFS
cell, cnf.cornell.edu .

Third, we had the CIT.CORNELL.EDU kerberos realm, where Cornell users already existed with their central Cornell logins.

Fourth, we had the GUEST.CORNELL.EDU kerberos realm, for users external to Cornell needing to access Cornell
resources.

Users in our Active Directory login to Windows using their CIT.CORNELL.EDU or GUEST.CORNELL.EDU credentials. In Windows Active Directory,
each user has a "Kerberos name mapping" as user1@CIT.CORNELL.EDU or user2@GUEST.CORNELL.EDU, allowing the user to use his or her foreign Kerberos
identity to login to Windows. This meant that the AD.CNF.CORNELL.EDU Active Directory Kerberos realm had to trust the CIT.CORNELL.EDU and
GUEST.CORNELL.EDU Kerberos realms.

Users also existed in our AFS cell as "foreign" Kerberos users in either the CIT.CORNELL.EDU or GUEST.CORNELL.EDU Kerberos realms . For example,
there might be in the AFS Proection Database (pts) "user1@cit.cornell.edu" or "user2@guest.cornell.edu" . This meant that the CNF.CORNELL.EDU
Kerberos realm had to trust the CIT.CORNELL.EDU and GUEST.CORNELL.EDU Kerberos realms so that those foreign users could obtain AFS tickets and
tokens in the CNF.CORNELL.EDU realm/cell.

With our somewhat complex setup, Integrated Login did not work straight out of the box. Additional configuration was needed.

First, with all these Kerberos trusts flying around, we needed to tell the OpenAFS client how to map the realm of the logging in user to an AFS
cell name. This is accomplished by setting the TransarcAFSDaemon\\NetworkProvider\\Domain registry keys for each user Kerberos realm. We made the
setting of these keys part of our OpenAFS client install via a MSI "transform". The freely available tool Orca, from Microsoft, was quite
useful in making the required changes to the Windows installer files.



Then, our other big problem was that the central university GUEST.CORNELL.EDU realm used periods in the usernames. While perfectly legal in
Kerberos v5, Kerberos v4 used the period as a separator. And OpenAFS still had this legacy Kerberos v4 limitation. We worked with the OpenAFS
Windows and server code developers to add a flag to each to allow Kerberos principal names container periods. In Windows, this is now turned on
with a Software\\OpenAFS\\CLient\\AcceptDottedPrincipalNames registry key. And on the server side, the OpenAFS servers are started with a
commandline option, -allow-dotted-principals .

To get Roaming Profiles themselves to work, we have to bypass some of the normal Windowsx expectations about the filesystem storing the Windows
Roaming Profiles. Active Directory Group Policy lets us set the necessary parameters for all Windows computers in our Domain. We specifically
enabled allowance of cross-forest user policy and cross-forest roaming user profiles. Due to OpenAFS not supporting native Windows ACLs, we also
had to set "Do Not Check for User Ownership of Roaming Profile Folders".

Those settings got the basic Roaming Profiles working. The next challenges were less part OpenAFS and more part Windows Roaming Profile
challenges. With Roaming Profiles, the entire profile is downloaded to the workstation from the server during login.  And the entire profile is
copied back to the server at logout. The larger the profile, the longer the copy time.  The greater the number of files, the longer the copy time
(copy overhead per file). The smaller the profile, the quicker the user ran into popups about the Profile size and the inability to logoff until
the Profile was back down to a smaller size. The tradeoff quickly became Roaming Profile size versus copy time versus user
inconvenience/frustration.

We settled on around 500 MegaBytes for a reasonable Roaming Profile size. At around 500 MegaBytes, a Roaming
Profile copy would usually take between 30 seconds and 2 minutes. On 32-bit Windows machines, 500 MegaBytes was
also about the maximum size to which we could set the OpenAFS cache. The 64-bit Windows machines did not have this
cache size limitation.

We were also able to decrease the logon / logoff time from Roaming Profile copying by excluding some directories from the Windows Roaming
Profile. For example, Hummingbird Exceed generated lots of tiny little files in the Roaming Profile. Excluding these significantly sped up the
login/logout time. And this did not cause Hummingbird any problems since it would just recreate the files and directories in the local copy of
the Profile.

Another issue with Roaming Profiles was local disk space. After hundreds of users have logged onto your Windows workstation with each user having
a local disk copy of their Roaming Profile, the disk tended to fill up.  We did set a Group Policy option instruction Windows to delete cached
copies of Roaming Profiles, but this often did not happen due to Windows failing to completely close file handles. And even if Windows closed
file handles, sometimes Windows still would simply just decide not to delete the locally cached copy of the Roaming Profile.

Roaming Profiles also exposed more interoperability issues with the Windows OpenAFS clients. Funky characters in
file names, international characters in file names, file names over a certain length, all of these caused failures
with the OpenAFS client and copying the Roaming Profile back to the AFS server. Again, we worked with the Windows
OpenAFS developers to fix or work around these problems. The addition of proper unicode handling in the Windows
OpenAFS client helped a lot.

Windows 7 offered up a new solution to the Roaming Profile problems - Folder Redirection. While Folder Redirection did exist on Windows XP,
Folder Redirection was quite limited in what folders one could redirect and what environment variables one could access in setting the redirected
to location. Windows 7 significantly relaxed the Folder Redirection limitations. But Windows 7 was not without its own unique challenges.

The first Windows 7 challenge was that Windows 7 broke OpenAFS Integreated Login with a foreign
Kerberos realm. Windows 7 left blank the underlying API data field with the logging in user's foreign Kerberos realm. Fortunately, the Windows
OpenAFS developers were able to find another way to obtain the logging in user's foreign Kerberos realm.

The second Windows 7 challenge was Offline File Caching being turned on by default. OpenAFS was not really designed to work in an offline
mode. And with the delayed writing, by Windows, of files back to OpenAFS, a user might have since logged off and his or her OpenAFS tokens
been destroyed as part of the logoff process. So, Windows no longer had permission to write to AFS on behalf of the user.

The third Windows 7 challenge was that Windows 7 no longer included a "Log On To" drop box on the login screen. In Windows XP, a user would
just select their foreign Kerberos realm (CIT.CORNELL.EDU or GUEST.CORNELL.EDU) from the list and only type their short username without
the Kerberos realm. With Windows 7, one can set a default logon Realm for that particular workstation. If the user is in a different foreign
Keberos realm, the user has to type the fully qualified username with the Kerberos realm in all caps. Especially for users in the
GUEST.CORNELL.EDU realm, this could be a painfully long username. We worked around this as best we could by setting some workstations to
default to one Kerberos realm and some to default to the other Kerberos realm. And we included clear signage about which Realm a particular
workstation defaulted to.

The fourth Windows 7 challenge was that OpenAFS does not natively support many Windows file attributes. With Folder Redirection, almost all of
the user's folders are redirected behind the scenes into AFS. Even the user's Desktop is running straight out of AFS. Previously hidden special
Windows files and folders were now visible to the user. For example, each folder the user browsed to would have a previously hidden "desktop.ini"
file. And if a user were to delete files or folders, the parent folder would display a special "$RECYCLE.BIN" file which again was previously
hidden.

The fifth Windows 7 challenge was that the initial login for a user on any particular workstation could take a few minutes. Windows 7 would
appear to hang for a couple of minutes with a message about preparing the user's desktop.

The sixth Windows 7 challenge was that Windows 7 would sometimes break its connection to AFS if its ip address were to change or if its network
were to go down and come back up. For example, if a laptop's wireless was turned off or if the laptop was put to sleep. The new native Windows
OpenAFS client solves this problem.

The big wins with Windows 7, however, were that, first off, logins and logoffs to Windows 7 were generally close to instantenous. And second
off,  even if the Roaming Profile copy failed, the user's data and most of the user's application settings were still stored into AFS (the
exception being some applications which still specifically stored their data in the Roaming Profile). And we have not experienced any issues, to
date, with applications storing their user data straight into AFS.

While much newer versions of the OpenAFS Windows client are available, we are currently standardized on OpenAFS for Windows 1.5.78. The reasoning
is two fold... the first being we have not yet had time to test the native Windows client against all the applications users usually run. And
second, with 1.5.99 and 1.6.x for Windows, we experienced issues with the Roaming Profile failing to copy. While minor because of Folder
Redirection, the failure still affects some important applications. Again, we have not yet had time to troubleshoot and so have not filed bugs.
We are existing in a very happy steady state. One of our next major projects is to put the native Windows OpenAFS client through its paces. We
are very much looking forward to the future of OpenAFS for Windows.
