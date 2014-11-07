---
title: OpenAFS Newsletter, Issue 1, May 2009
layout: page
---

# OpenAFS Newsletter, Issue 1, May 2009

This is the first issue of what will hopefully be a monthly summary of the
activity that's happening in the OpenAFS community.

As always, volunteers, patches, bug reports, or any other type of help is
greatly appreciated.

Feedback on this newsletter is welcome. The goal is to summarize the
various development efforts and news of OpenAFS for the community. Please
let Jason know what you would like to see out of this newsletter.

## Upcoming Events

The Sixth Annual International AFS & Kerberos Best Practices Workshop will
be held at Stanford University on June 1-5, 2009.

Ref: http://workshop.openafs.org/afsbpw09/index.html

## Projects

### Disconnected AFS support

Project Contacts:

- Simon Wilkinson <sxw@inf.ed.ac.uk>
- Dragos Tatulea <dragos.tatulea@gmail.com>

Support for disconnection operation on Unix has been integrated into the
1.5.x branch. There are no currently known data loss bugs, and further
testing would be greatly appreciated. Currently, files written whilst
disconnected do not persist across restarts, and there is no user
interface to specify which files should be pinned in the cache to ensure
they're available whilst disconnected. Simon Wilkinson and Dragos Tatulea
(respectively) are working to resolve these.

### Security Releases

Security Officer:

- Simon Wilkinson <sxw@inf.ed.ac.uk>



OpenAFS 1.4.9, 1.4.10 and 1.5.59 were a security release to resolve two
independent issues in the OpenAFS cache manager for Unix, one of which is
a potential remote root exploit. All Unix platforms, excluding Mac OS X
10.4 and 10.5 are affected, and upgrading is strongly recommended.

### Fedora 11 and Linux 2.6.29 support

Project Contact:

- Simon Wilkinson <sxw@inf.ed.ac.uk>

OpenAFS 1.4.10 does not build on Fedora 11, and crashes in some situations
when running on a 2.6.29 kernel. Fixes will be available shortly.

### Newsletter

Project Contact:

- Jason Edgecombe <jason@rampaginggeek.com>

Derrick Brashear, Jason Edgecombe, Jeff Altman, and Simon Wilkinson
discussed the issue of keeping the community better informed by the web
and a monthly email newsletter. Jason volunteered to write the
newsletter. This document is the result.

Ref: http://jabber.openafs.org/openafs@conference.openafs.org/2009-05-04.txt



### Google Summer of Code 2009

OpenAFS received 4 slots for the 2009 Google Summer of Code.

Go to http://socghop.appspot.com/org/home/google/gsoc2009/openafs for more
information about the GSoC projects.

The student projects are:

#### OpenAFS server preference based on network conditions

Student Developer: Jake Thebault-Spieker <summatusmentis@gmail.com>

Mentor: Derrick Brashear <shadow@gmail.com>

This is Jake's second year with GSoC for OpenAFS.

Abstract:

The OpenAFS cache manager keeps two lists of which servers host the files
required. Currently, these lists are ordered based on antiquated network
architecture assumptions that no longer apply to current network
architectures. This project seeks to change the way these lists are
ordered by taking into account network conditions that can be estimated
based on the Rx peer statistics gathering functionality built into
OpenAFS.

Ref: https://lists.openafs.org/pipermail/openafs-devel/2009-April/016590.html

#### OpenAFS Management Console on Windows

Student Developer: Brant Gurganus <brant@gurganus.name>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Abstract:

I propose creating a Microsoft Management Console snap-in for
Windows. This will better integrate OpenAFS with existing Windows
management technology and fits in an overall strategy of improved Windows
integration.

Ref: https://lists.openafs.org/pipermail/openafs-devel/2009-April/016591.html

#### Implementing OpenAFS features into RedHat's kafs kernel module.

Student Developer: Wang Lei <wang840925@gmail.com>

Mentor: David Howells

Abstract:

My project is to implement some OpenAFS features into the Linux kafs
kernel module. The first feature is DNS AFSDB Support which may be
implemented by sharing the mechanism used by CIFS as my mentor's design at
present. The second is implement more functions of the pioctl system-call
on the work of the student of GSoC last year. And the other two are to
implement some OpenAFS fs commonds that were not implemented in kafs and
Keyring compatibility which can work well with both OpenAFS client and
kafs. I have began to read the documatations of pioctl/ioctl of the
OpenAFS, and I will start my work with the implement of this system
call. There are a lot of pioctls to implement and I think that can help me
to understand OpenAFS well.

Ref: https://lists.openafs.org/pipermail/openafs-devel/2009-April/016595.html

#### Adding Searching and Indexing Searching Features

Student Developer: Reeni Kaushik <kaushik1@illinois.edu>

Mentor: Dave Botsch

Abstract:

My interest lies in the area of File Systems and I am especially
interested in working on the project "AFS as a Data Driven File System".

Ref: https://lists.openafs.org/pipermail/openafs-devel/2009-April/016596.html



### Kerberos v5 and multiple encryption types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

We are finalizing work to bring the rxk5 change set to parity with
openafs-devel-1\_5\_x, at which time we will pull the rxk5-devel and
probably rxk5 branch tags forward.  (This may take place in the next day
or so, in fact, thanks to a bunch of merge work by Marcus over the
weekend.)  Our intention is to have rxk5 ready to merge with 1.5 in the
near future.  In addition, we are working on a draft description of
'rxk5ng', a superset of rxk5 addressing authorization of currently
unsecured call channels (anonymous file accesses, callbacks), cache
poisoning, and departmental servers. --Matt

(Ed: This was received on May 10)

### \*BSD Support

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

The OpenBSD port has been updated to support OpenBSD 4.4 and 4.5.  I
have added a userland port (no client) to DragonflyBSD, supporting
releases 2.2 and 2.3.  Updates for client support of recent versions
of FreeBSD 8.0 current and NetBSD 4.x and 5.x are in progress. --Matt



### Extended Callback Information

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

I am preparing a public release of the full extended callback
information draft implementation, including a reduced version of Tom
Keiser's libosi work.  (The xcb mechanism makes the callback interface
extensible, and provides atop this new notifications including range
invalidation on files and metadata change notifications.)  This will
be ready for review some time before the afsbpw. --Matt

### Rx OSD integration

Project Contacts:

- Hartmut Reuter <reuter@rzg.mpg.de>
- Felix Frank <Felix.Frank@Desy.de>
- Christof Hanke <hanke@rzg.mpg.de>

Felix Frank is working on integrating the Rx OSD changes back into the mainline
OpenAFS code.

Ref: https://lists.openafs.org/pipermail/openafs-devel/2009-May/016625.html

### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

Marcus Watts updated the pts\_interactive.pod, pts\_sleep.pod,
pts\_source.pod, and NoAuth.pod man pages in the rxk5 branch on May 3.
Jason clarified fake address support in netinfo.pod on April 27. Jason has
started working on the Admin Quickstart guide. The man pages still need
work, but Jason is tired of seeing new users set up OpenAFS with the
deprecated kaserver. Appendix A of the Unix Quickstart Guide has been
rewritten to show the use of configure and make to compile OpenAFS from
source.



## CVS statistics

    Month     Lines Added     Lines Removed  Net Lines Changed
    ====HEAD====
    2009/01   +    1289 	  -    1128 	      161
    2009/02   +    2274 	  -    2152 	      122
    2009/03   +    4276 	  -    4466 	     -190
    2009/04   +     394 	  -     361 	       33

    ====openafs-devel-1_5_x====
    2009/01   +    5794 	  -    7476 	    -1682
    2009/02   +  133623 	  -  128267 	     5356
    2009/03   +    8252 	  -    7838 	      414
    2009/04   +    1145 	  -     777 	      368

    ====openafs-stable-1_4_x====
    2009/01   +     389 	  -     251 	      138
    2009/02   +     869 	  -     612 	      257
    2009/03   +    1503 	  -     710 	      793
    2009/04   +     544 	  -     436 	      108

    ====openafs-windows-kdfs-ifs-branch====
    2009/01   +     247 	  -     177 	       70
    2009/02   +    1959 	  -    1135 	      824
    2009/03   +     316 	  -      74 	      242



    ====rxk5-devel-1_5_x====
    none in 2009 until May 2009
