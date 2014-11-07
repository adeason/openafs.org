---
title: OpenAFS Newsletter, Issue 4, August 2009
layout: page
---

# OpenAFS Newsletter, Issue 4, August 2009

Welcome to the fourth issue of the OpenAFS newsletter. This newsletter
summarizes what is happening in the OpenAFS community.

As always, volunteers, patches, bug reports, or any other type of help is
greatly appreciated.

Feedback on this newsletter is welcome. The goal is to summarize the
various development efforts and news of OpenAFS for the community. Please
let Jason Edgecombe <jason@rampaginggeek.com> know what you would like to
see out of this newsletter. Any news about AFS-related projects is welcome
and may be submitted to Jason for inclusion in the next newsletter.

(On a personal note, I received thanks from the Elders and other folks for
my work on this newsletter. I would like to say "thanks for the
recognition, and I couldn't do it without the project leaders who put up
with me bugging them for monthly status updates. ;)" --Jason)

The current and past issues of this newsletter are available at
[http://www.openafs.org/newsletter/](http://www.openafs.org/newsletter/)

## General OpenAFS Progress

For people following the progress of OpenAFS development, you've no doubt
noticed a lot of changes. For those who haven't, the third great movement
forward is upon us (the first happened with the open-sourcing of AFS; the
second, when the Windows client was again adopted and development moved
forward). A number of small new features have become available, but more
importantly, thanks to a large number of fixes to compile-time warnings
throughout the codebase, a number of bugs, many longstanding, have been
uncovered and corrected.

We've also received contributions of code for GUI tools for MacOS, both an
installer plugin for client configuration, and a preferences pane; the
process of restructuring code to allow the Unix client cache manager to
manage data not served by traditional Rx fileservers has begun; Finally,
new supporting code for other planned enhancements, including the MCAS
library as needed for extended callback support, have been incorporated.

At the same time, effort has again begun to be expended in the direction
of creating a stable 1.6 release candidate. 1.5.61 was released on August
5\. Bug reports, especially bug reports for servers, are requested to help
us with this effort.

\--Derrick

## Events

### AFS Hackathon

The School of Informatics at the University of Edinburgh will be hosting
an AFS Hackathon 22-24 September (immediately before the European AFS
Conference). All OpenAFS developers are welcome to attend - please see the
email to openafs-announce for details, and RSVP to sxw@inf.ed.ac.uk

### European AFS Meeting

The University Roma Tre will host the 2009 European AFS Meeting from
September 28-30. The European workshop is mainly a platform for system
administrators to exchange their knowledge and report use cases. Topics of
interest include related technologies like Kerberos or LDAP and all
supported operating systems.

For more details, go to [http://www.dia.uniroma3.it/~afscon09/](http://www.dia.uniroma3.it/~afscon09/)

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

### Git & Gerrit

Project Contact:

- Simon Wilkinson <sxw@inf.ed.ac.uk>

People who were instrumental in the conversion to git include Michael
Meffie, Max Cohan, Simon Wilkinson, Derrick Brashear, and the git
developer community, especially Shawn Pearce and Johannes Schindlein. The
Git conversion is a major change.  Gerrit has been operational for
slightly over a week, and already 80 changes were submitted.  Most changes
are going in within a couple of days.  This is a clearing of backlog from
things that people already had in their personal repositories, but still,
it's clear that the new tools will make a huge difference.

The CVS repository for the openafs web site has been converted to git and
connected to Gerrit. Web site changes may be submitted to Gerrit and can
be approved just like source code contributions. A different
authentication group for web site approvals was created in Gerrit.

### Rx OSD integration & Raw Vicep Access in Clients

Project Contacts:

- Hartmut Reuter <reuter@rzg.mpg.de>
- Felix Frank <Felix.Frank@Desy.de>
- Christof Hanke <hanke@rzg.mpg.de>

The developers of the RxOSD branch have started to work on a protocol
draft for the OSD-extension. Their progress can be watched at
http://pfanne.rzg.mpg.de/trac/openAFS-OSD/wiki/SpecDraft. Any comments are
welcome. A series of patches has already been submitted to gerrit, and
some of the code is part of the OpenAFS development branch
already. --Christof

### \*BSD Support

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

New targets added for OpenBSD, all AMD64 subtargets up to 4.5.  FreeBSD
and NetBSD work in ongoing. I expect to send a more detailed status report
before next newsletter.

\--Matt

### Extended Callback Information

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>

I have begun submitting XCB code upstream.  The current status is that
Libosi and MCAS dependencies are submitted.  MCAS has 2 parts, the first
of which (base contribution) has been committed, and the second part I
would expect to be committed some time this week.  Libosi needs to be
broken up and re-sent to gerrit--this should happen by end-of-week.
Finally, the latest XCB implementation, implementing draft 10, should be
submitted for review by 8/10/2009.

\--Matt (Ed: received on August 2, 2009)

### Kerberos v5 and Multiple Encryption Types

Project Contacts:

- Matt Benjamin <matt@linuxbox.com>
- Marcus Watts <mwd@umich.edu>

Marcus is working on a protocol description for rxk5, to be published
fairly soon.



### Better Documentation

Project Contacts:

- Russ Allbery <rra@stanford.edu>
- Jason Edgecombe <jason@rampaginggeek.com>

There has not been major new documentation work since the last newsletter,
but we've been doing some work behind the scenes that should eventually
make it easier to manage and update the OpenAFS web site.  With the advent
of Gerrit, we will also be emphasizing updating the documentation at the
same time as the code for new user-visible features. --Russ

Simon Wilkinson has started a wiki page that documents the preferred code
style for new contributions. Previously, the coding style was documented
as a set of options to the GNU indent command. The new wiki page is
available at
[http://www.dementia.org/twiki/bin/view/AFSLore/CodingStyle](http://www.dementia.org/twiki/bin/view/AFSLore/CodingStyle)

### Google Summer of Code 2009

OpenAFS received four slots for the 2009 Google Summer of Code.

Go to [http://socghop.appspot.com/org/home/google/gsoc2009/openafs](http://socghop.appspot.com/org/home/google/gsoc2009/openafs) for more
information about the GSoC projects.

Three of the projects are still active. Unfortunately, one student had to
back out.

The following projects did not give a status update:

- Implementing OpenAFS Features into RedHat's kafs Kernel Module

#### OpenAFS Management Console on Windows

Student Developer: Brant Gurganus <brant@gurganus.name>

Mentor: Jeffrey Altman <jaltman@secure-endpoints.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2009-April/016591.html](https://lists.openafs.org/pipermail/openafs-devel/2009-April/016591.html)

There is now a 32-bit installer for people to try at
http://code.google.com/p/openafsclientmmc/downloads/list

#### OpenAFS Server Preference Based on Network Conditions

Student Developer: Jake Thebault-Spieker <summatusmentis@gmail.com>

Mentor: Derrick Brashear <shadow@gmail.com>

Self-intro:
[https://lists.openafs.org/pipermail/openafs-devel/2009-April/016590.html](https://lists.openafs.org/pipermail/openafs-devel/2009-April/016590.html)



### Projects with no progress or no update

- Disconnected AFS support
- Pthreaded Ubik

## Resolved Tickets

Since Gerrit is now the preferred method of accepting patches instead of
RT, it's likely that fewer RT tickets will be filed.

Here is a list of tickets that have been resolved since July 1, 2009:

    ticket # state     created       title
     124938: resolved  Jun 16, 2009  ubik "allbetter" log levels
     124976: resolved  Jun 23, 2009  fix for tests-generate-dirpath-in-makefile
     125001: resolved  Jun 26, 2009  Linux: conditionally compile search for key_type_keyring
     125020: resolved  Jun 29, 2009  Incorrect ubik_client reinitialization in CallPreamble
     125031: resolved  Jul 01, 2009  Parallel make fixes
     125064: resolved  Jul 07, 2009  vos doesn't display vnode accesses unless updateDate is set
     125079: resolved  Jul 09, 2009  OpenAFS 1.5.59 crash dump
     125089: resolved  Jul 12, 2009  Symbol find_task_by_vpid no longer available to modules as of Linux 2.6.31
     125093: resolved  Jul 13, 2009  afsd_servivce.exe at 45% cpu and explorer hangs.
     125111: resolved  Jul 16, 2009  vos listvol -format shows incorrect volume name when busy
     125152: resolved  Jul 23, 2009  deal with gerrit 175 for windows
