---
title: OpenAFS Newsletter, Issue 3, July 2009
layout: page
---

# OpenAFS Newsletter, Issue 3, July 2009

Welcome to the third issue of the OpenAFS newsletter. The newsletter
summarizes what is happening in the OpenAFS community. The main thing to
report in this issue is the conversion of CVS to git. Git is now ready for
use in development. I suspect that many people were very busy or on
vacation this month, because many of the subprojects did not reply to
requests for project updates.

As always, volunteers, patches, bug reports, or any other type of help is
greatly appreciated.

Feedback on this newsletter is welcome. The goal is to summarize the
various development efforts and news of OpenAFS for the community. Please
let Jason Edgecombe <jason@rampaginggeek.com> know what you would like to
see out of this newsletter.

The current and past issues of this newsletter are available at
[http://www.openafs.org/newsletter/](http://www.openafs.org/newsletter/)

## General OpenAFS Progress

Many thanks go to Simon Wilkinson for finishing the conversion from CVS to
git and setting up gerrit. Gerrit has only been up for a week and there
are already over 100 patches that have been merged!

1.4.11 has been released, and it includes major bugfixes for Linux clients
and fileservers. Some minor bugs were fixed on other platforms. The
release notes are available at
http://www.openafs.org/frameset/dl/openafs/1.4.11/RELNOTES-1.4.11

## Events

### AFS Hackathon

The School of Informatics at the University of Edinburgh will be hosting
an AFS Hackathon 22-24 September (immediately before the European AFS
Conference). All OpenAFS developers are welcome to attend - please see the
email to openafs-announce for details, and RSVP to sxw@inf.ed.ac.uk

### Annual Best Practices Workshop

Plans are already underway for the seventh Workshop, to be held May 24-28,
2010, at the University of Illinois at Urbana-Champaign.  We hope to see
you there.

## Projects

### Security Releases

Security Officer:

- Simon Wilkinson <sxw@inf.ed.ac.uk>

No security issues since 1.4.9, 1.4.10, and 1.5.59 were released in April
2009.

### Git

Project Contact:

- Simon Wilkinson <sxw@inf.ed.ac.uk>

During the week of 6th July, we completed our transition to the git
version control system. Git, and gerrit (our code review tool) are now
ready for use! See
http://www.dementia.org/twiki/bin/view/AFSLore/GitDevelopers for more
details.

### Pthreaded Ubik

Project Contact:

- Steven Jenkins <steven@endpoint.com>

The pthreaded ubik's initial code delivery to provide for use of POSIX
threads instead of LWPs was made in April 2008.  After some production
usage, some problems were found in initialization (on certain platforms)
and lack of locking, leading to data corruption in some cases for the
vlserver.  As part of the analysis of these problems, some differences
were identified between the private version of OpenAFS being used and the
version in OpenAFS HEAD, several other longstanding issues with vos,
vlclient, and the vlserver were identified, and some patches have been
submitted:

- RT \#124977 addresses mutex and condition variable initialization
- RT \#125035 fixes a longstanding logging bug
- RT \#125036 fixes a longstanding bug in vlclient command-line parsing

Current work involves cleaning up and testing a patch to fix improper
handling of multi-homed IP addresses in the VLDB.  The patches to fix the
logging are undergoing further testing and analysis (both code review and
automated testing with Helgrind), and we hope to have those submitted soon
as well.

\--Steven

### Rx OSD integration & Raw Vicep Access in Clients

Project Contacts:

- Hartmut Reuter <reuter@rzg.mpg.de>
- Felix Frank <Felix.Frank@Desy.de>
- Christof Hanke <hanke@rzg.mpg.de>

The RxOSD-integration is now documented at
http://pfanne.rzg.mpg.de/trac/openAFS-OSD.  This website offers technical
documentation as well as links to prebuilt rpm- packages for some
distributions (CentOS,Fedora, Mandriva, RHEL, openSUSE, and SLES). Anyone
willing to contribute is cordially intvited to drop a line to the
maintainers.  Patches are currently being prepared and targeted at the
1.4.x stable branch, they are published on
https://dvinfo.ifh.de/AfsOsd/Patches.  Patches for 1.5.x are coming up.



### Google Summer of Code 2009

OpenAFS received four slots for the 2009 Google Summer of Code.

Go to [http://socghop.appspot.com/org/home/google/gsoc2009/openafs](http://socghop.appspot.com/org/home/google/gsoc2009/openafs) for more
information about the GSoC projects.

Three of the projects are still active. Unfortunately, one student had to
back out.

The following projects did not give a status update:

- Implementing OpenAFS Features into RedHat's kafs Kernel Module
- OpenAFS Server Preference Based on Network Conditions

#### OpenAFS Management Console on Windows

Student Developer: Brant Gurganus <brant@gurganus.name>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2009-April/016591.html](https://lists.openafs.org/pipermail/openafs-devel/2009-April/016591.html)

The Google Summer of Code program is at its half way point. With that, the
management console has a complete user interface as well as deployment
packages. Project downloads and source will be available at
http://code.google.com/p/openafsclientmmc

### Projects with no progress or no update

- Binary Packaging
- Better Documentation - No significant updates.
- BSD support
- Disconnected AFS support
- Extended Callback Information
- Kerberos v5 and Multiple Encryption Types

## Resolved Tickets

Since Gerrit is now the preferred method of accepting patches instead of
RT, it's likely that fewer RT tickets will be filed.

Here is a list of tickets that have been resolved since June 1, 2009:

    ticket # state     created       title
       3210: resolved  Feb 03, 2004  multiprobealternateaddress doesn't remove bad interfaces for this uuid
      18596: resolved  May 06, 2005  [Patch] add module license macro to Linux kernel module
      60275: resolved  Apr 25, 2007  'make dest' fails to create man dir + manpages
     101309: resolved  Jun 02, 2008  DAFS: error creating volumes on 1.5.38 with demand attach
     124492: resolved  Mar 17, 2009  DAFS: new volumes always require salvaging
     124709: resolved  Apr 28, 2009  linux26 issue with pagsh.krb and Pag location in group list
     124763: resolved  May 11, 2009  Windows Vista 64 bit would not reboot cleanly after running 64-bit 1.5.59 installer
     124891: resolved  Jun 01, 2009  CellServDB parsing subject to buffer overflows
     124893: resolved  Jun 02, 2009  ptserver debug flag correction
     124894: resolved  Jun 02, 2009  ptprocs vicelog newlines and loglevels
     124898: resolved  Jun 03, 2009  src/aklog/klog.c uninitialized variable tofree
     124910: resolved  Jun 08, 2009  Windows: cm_cell_t lists not properly protected by cm_cellLock
     124923: resolved  Jun 12, 2009  opensolaris 'struct conn' conflict
     124924: resolved  Jun 12, 2009  Re: OpenAFS and OpenSolaris
     124933: resolved  Jun 15, 2009  Problems to access to the read only volume.
     124938: resolved  Jun 16, 2009  ubik "allbetter" log levels
     124939: resolved  Jun 16, 2009  src/config/Makefile.version missing in OpenAFS 1.4.11 RC1
     124942: resolved  Jun 16, 2009  Linux: cache files: use i_op->setattr if defined
     124946: resolved  Jun 17, 2009  call gethostbyname() from cellconfig.c afsconf_GetCellInfo()
     124952: resolved  Jun 18, 2009  2 small things to make 1.4.11pre1 build on FreeBSD 6.1
     124976: resolved  Jun 23, 2009  fix for tests-generate-dirpath-in-makefile
     124986: resolved  Jun 24, 2009  Linux: try to deal with unexported rcu_read_{un}lock
     124991: resolved  Jun 25, 2009  1.4.11pre2 on suse
     124996: resolved  Jun 26, 2009  Linux: fix rcu patch fallout for 1.5/head
     125001: resolved  Jun 26, 2009  Linux: conditionally compile search for key_type_keyring
     125015: resolved  Jun 29, 2009  What Are Pheromones? -- Let's Finnd Out
     125018: resolved  Jun 29, 2009  Windows: lost FetchData error codes in cm_GetBuffer?
     125020: resolved  Jun 29, 2009  Incorrect ubik_client reinitialization in CallPreamble
     125064: resolved  Jul 07, 2009  vos doesn't display vnode accesses unless updateDate is set
     125079: resolved  Jul 09, 2009  OpenAFS 1.5.59 crash dump
     125089: resolved  Jul 12, 2009  Symbol find_task_by_vpid no longer available to modules as of Linux 2.6.31
     125093: resolved  Jul 13, 2009  afsd_servivce.exe at 45% cpu and explorer hangs.
     125111: resolved  Jul 16, 2009  vos listvol -format shows incorrect volume name when busy
