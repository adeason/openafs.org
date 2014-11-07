---
title: OpenAFS Newsletter, Volume 4, Issue 2, May 2012
---

# OpenAFS Newsletter, Volume 4, Issue 2, May 2012

## Introduction

This edition of the OpenAFS newsletter is Part 1 of our Case Study on Windows Roaming Profiles in AFS. Part 1 is contributed by Lars Schimmer of the Graz University of Technology. Future newsletters will follow up with the next parts of our roaming profiles case study.

But first, a quick update on what's new in AFS-land, starting with what to expect for OpenAFS 1.6.2, contributed by Derrick Brashear.

## OpenAFS 1.6.2

• "No-offline" volume release mechanism
• Fixed partition statistics
• MacOS Preference Pane enhancements
• Solaris and Linux changes for current revisions
• vos convertROtoRW improvements
• Improved offline volume reporting from the fileserver

## OpenAFS Windows 1.7.14

1.7.14 fixes two major issues discovered in 1.7.13:

    * A kernel deadlock that is triggered by Sophos anti-virus
      products but can be triggered by other activity.

    * A crash of afsd_service.exe at startup if the previous
      shutdown of afsd_service.exe was not clean.

The significant changes since 1.7.12 are:

    * Fixes problems with Adobe Acrobat Reader

    * Fixes problems with Adobe Acrobat Pro X

    * Fixes problems with Windows Media Player

    * Corrects BSODs
      . interaction with Microsoft anti-virus product
      . kernel memory corruption due to race condition

    * Increased maximum path depth from 32 to 512 expanded components
      (symlinks, mount points, @sys substitutions)

## 2012 European AFS and Kerberos Conference

The 2012 European AFS and Kerberos Conference will take place in the University
of Edinburgh School of Informatics from Tuesday 16th to Thursday 18th October
2012.

Full details are available at: http://openafs2012.inf.ed.ac.uk/

## 2012 AFS and Kerberos Best Practices Workshop Cancelled

Unfortunately, the Best Practices Workshop will not take place this year. We look forward to returning in 2013.

## Case Study: Windows Roaming Profiles in OpenAFS

The Institute of Computer Graphics and Knowledge Visualization started as a new institute at TU Graz in 2005. Already, we had chosen OpenAFS as the main storage platform for all our data. We had three different locations, a CAVE(tm) setup, and mostly Windows users; and we needed to provide the same data and workspace to our users no matter their work location. So, we decided to use a Windows Active Directory domain with user profiles stored in OpenAFS. As a happy side effect, with all user data saved in the central OpenAFS filespace we also solved the issue of user data backup from client machines.

Over the past seven years, we have iterated both our hardware and software setups. Now, we have three OpenAFS database servers and three OpenAFS fileservers each offering 1 TeraByte partitions. The partitions themselves are not local to the fileservers but are iSCSI over gigabit network. While the OpenAFS servers are real (bare metal) servers for better performance, our two Windows AD servers are virtual servers. Services provided by these two Windows AD servers are Active Directory authentication to the Windows clients and Kerberos Domain Controller (KDC) servers for our Linux clients.

We tested Windows Folder Redirection into OpenAFS on Windows XP for the AppData folder and for the Documents folder. Our testing included a special user group in Windows Active Directory redirecting the AppData and Documents folders to subfolders of the user's OpenAFS home directory. But, at the time, the testing was not successful. In addition to more overhead on volume/ACL/quota creation/management, Windows Folder Redirection simply did not work as expected. Programs did not consistently store their data in the same place -- some programs would write to the redirected folders and some simply wrote into the usual profile space. Also, the redirected folders did not consistently work on login.

Another problem with Windows Folder Redirection was Windows XP folder synchronization. Instead of writing directly into OpenAFS (like a Linux client), Windows would write into its own folder sync cache. This was an additional cache in between programs and OpenAFS. Some programs, such as Skype and Adobe Acrobat, broke horribly with this extra cache. Windows XP would attempt to sync the folders on logoff and would often fail with errors like "could not write file" or file "still in use". While our setup itself may have been part of the problem, we simply could not get folder sync to work with Windows XP and Folder Redirection.

For us, Roaming Profiles worked faster and more reliably. We are, however, wondering if we should again try Folder Redirection with Windows 7 clients.

With our typical Roaming Profile setup, users obtain an OpenAFS token on login. User profile paths point to a directory in OpenAFS. If a user Roaming Profile actually exists, Windows will load the profile data on the local harddrive. Otherwise, the workstation creates a new user profile on the local harddrive from a profile skeleton stored on the local harddrive.

Using our Windows Active Directory servers as our KDCs, we have to allow the old, insecure Kerberos enctypes with a policy:
	

	"Network security: Configure encryption types allowed for Kerberos".

We also have to add a REG\_DWORD (32 bit) registry entry named "KdcUseRequestedEtypesForTickets" at "HKLM\\SYSTEM\\CurrentControlSet\\services\\kdc". Without this registry entry, the Windows KDC does not talk single DES with clients, as required by OpenAFS.

Storing Roaming Profiles in the OpenAFS filespace requires setting the following policy in Active Directory:

	"Do not check for user ownership of roaming profiles Folders" - "enabled"
	under Policies/Administrative/Templates/Sytem/Users Profiles.

Without this policy set, Windows will not allow users to access their OpenAFS stored profile data.

We limit the size of the user profile to 4 GigaBytes via AD Group Policy. We do not, however, set the option to delete the Roaming Profile from the Windows workstation hard drive at logoff. The advantage is that when the Roaming Profile does not properly sync back to the OpenAFS server, the user data remains on the Windows workstation. The disadvantage is that we must keep an eye on hard drive space. For example, 10 Roaming Profiles each of 4 GigaBytes could consume 40 GigaBytes of local hard drive space.

Each user has two home volumes - one for the user's Linux home and one for the user's Roaming Profile. For example, user "Meyer" has a volume named "home.meyer" for Linux and a volume named "win.meyer" for the Windows Roaming Profile. Windows 7 workstations look for the Roaming Profile in a directory named "winprofile.V2" while Windows XP workstations look for the Roaming Profile in a directory simply named "winprofile". So, the path of the Windows Roaming Profile is just set to the OpenAFS mountpoint (named winprofile or winprofile.V2) for the user's Windows profile volume. Each Roaming Profile OpenAFS volume has a 4 GigaByte quota, matching the Roaming Profile size limit.

For a user's Roaming Profile folder/volume in OpenAFS, we set the ACLs to "write" (rlidwk) for the user him or herself only. But, just to make sure the AD servers can access the users' profiles under all circumstances, the AD servers do, via IP ACLs, have "rl" rights on the full path. Of course, one must beware that with IP ACLs all users on that IP address have the same ACL.

After we completed the server-side setup - setting Group Policies, creating the OpenAFS volumes, mounting the OpenAFS volumes for the Roaming Profiles, setting quotas on the Roaming Profiles and OpenAFS volumes, and setting ACLs on the OpenAFS volumes - we moved on to setting up the workstations.

We began the workstation setup by installing the latest OpenAFS client. As the systems are 64-bit Windows systems, we installed the OpenAFS 64 bit MSI as well as the 32-bit OpenAFS tools MSI. As of this writing, the latest version is 1.7.12. And because we are using the 1.7.x series of OpenAFS for Windows, we use the new "native" IFS OpenAFS windows client instead of the old SMB redirector. We also install MIT krb5 3.2.2 which while old works flawlessly in our environment. On each workstation located on our internal network, we chose the OpenAFS client option "Obtain Token on Login" and we disabled AFS crypt security (we do, however, enable AFS crypt security for laptops and other computers which would leave our internal network). Because we do not have AFS DNS records, we disable the lookup of cells in DNS. The AFS cache size is set to at least 500MB with a chunk size of 1 MB. We have found the cache size and chunk size cache settings extremely important for speeding up transfers of Roaming Profiles to/from the OpenAFS servers. The larger cache and chunk sizes help to keep most Roaming Profile user data in the local OpenAFS client cache. With the typically large number of small files in a user's Roaming Profile, a complete reload of a 1 GigaByte profile can take a lot of time. 

Roaming Profiles have their own set of challenges which are not unique to storing the Roaming Profiles in OpenAFS. Unfortunately, the use of OpenAFS does not solve these challenges.

For example, profile data is only synced back to the OpenAFS filesystem during logout and shutdown. If the local user profile exceeds the profile quota, errors will occur, including the profile not being completely written into OpenAFS. Setting policy to remove the profile from the workstation would result in data loss. Also, on login, Windows checks the file alteration date and selects the newer version of a file to write to the local profile path. In other words, last write across multiple possibly not synced versions of a file wins.

Profile size problems worsen with programs not knowing anything about Roaming Profiles. For example, Microsoft Virtual Earth caches data in the user's profile path. But, Virtual Earth does not have an option to limit the cache size. Long and heavy use of Virtual Earth fills up the Roaming Profile with "useless" cache data. Another example, Geomagic Studio 12, writes a 12 GigaByte cache profile into the user Roaming Profile on startup. While Microsoft did divide the profile AppData folder into three sections, we sync the whole user profile into OpenAFS. This includes the AppData\\Local folder, which normally should be kept only on the workstation and not synced back into OpenAFS. We need to further research how to not sync the AppData\\Local folder and the side effects of not syncing this folder. For example, Microsoft Outlook unfortunately writes its data files into the AppData\\Local folder. Without its data file cache, Microsoft Outlook will reload all data from the mail server (if the data is still available on the mail server). This reload will take time, especially since some users have greater than 500 MegaByte size mailboxes. And for those users not storing mail on the server (eg POP3), email data would be lost. 

Even programs aware of Roaming Profiles can cause size problems. Thunderbird, for example, does write its data into the AppData\\Roaming folder. With a lot of mail, Thunderbird alone can easily fill up half or more of a user's Roaming Profile quota.

As mentioned earlier, a Roaming Profile can be slow to load, especially with
lots of small files. Users constantly reported slow and unreliable logins and
logoffs to Windows. But, moving to OpenAFS 1.7.12 with IFS and the
aforementioned cache size of at least 500 Megabytes with a 1 MegaByte chunk
size has significantly improved login/logoff times. Also, the use of SSD drives
for the OpenAFS cache has impressively increased data transfer speeds. We have typically seen speed rates of 10x faster.

As the biggest problem for us is silly applications filling up a user's profile quota, user awareness is extremely important. Even so, users still often hit the four GigaByte profile limit. 

That said, the biggest benefit for us is to have our user data readily accessible 24/7 on each workstation. OpenAFS is a big win for us.
