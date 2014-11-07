---
title: OpenAFS Newsletter, Volume 4, Issue 3, August 2012
---

# OpenAFS Newsletter, Volume 4, Issue 3, August 2012

## Introduction

Welcome back to the OpenAFS Newsletter.

This edition features part 2 of our Windows Roaming Profiles Case Study. And, the debut of "Did You Know..." , which will feature lesser known hints,
tips, and tidbits in addition to more misunderstood pieces of OpenAFS.

If you have any suggestions for future topics or would like to contribute to the OpenAFS Newsletter, please contact Dave Botsch at newsletter (at)
openafs.org .

## Passing of RL "Bob" Morgan

OpenAFS recently learned of the passing of RL "Bob" Morgan.

Bob was most recently known for his considerable work on identity management,
but before his employment at the University of Washington worked at Stanford
and was involved in Kerberos and AFS during his time there. Bob was among the
people who externally pushed the cause of open sourcing AFS, and in a
conference call where it became clear that would actually happen, posed a
scenario which became a running joke for years when he suggested the
possibility of providing support for this open source AFS as "R L Bob's AFS
Company".  Bob will be sorely missed.

More can be read here: [https://spaces.internet2.edu/display/rlbob/Home](https://spaces.internet2.edu/display/rlbob/Home)

\-Derrick Brashear

## OpenAFS 1.6.1a for Mountain Lion

OpenAFS 1.6.1a is a set of patches to 1.6.1 to update the MacOS AFS client, including the preferences pane. Installers for Mac OS X Lion and SnowLeopard are also available.

[http://www.openafs.org/macos.html](http://www.openafs.org/macos.html) as always has links to all MacOS installers.

## OpenAFS for Windows 8 and Server 2012

On August 15th Microsoft made available the "Release to Manufacturing"
builds of Windows 8 and Server 2012 to members of the following programs:

\* MSDN Subscriptions

\* Microsoft Partner Network

\* TechNet Professional Subscriptions

\* Microsoft Volume Licensing/Software Assurance customers

The general public release for consumers and small businesses will take
place on October 26.  However, the above programs will permit just about
every organization that uses OpenAFS to deploy Windows 8 and Server 2012
in some capacity.  Therefore, it is critical that OpenAFS provide
support for the Windows 8 and Server 2012 platforms.

On August 16th OpenAFS.org announced the availability of Windows 8 and
Server 2012 support in the OpenAFS 1.7.17 release.  This support covers
the X86 and AMD64/X64 chipsets.

Windows 8 and Server 2012 are a major platform change for the Windows
ecosystem,  especially for file system vendors and file system filter
products such as Anti-malware, Backup, Encryption, and Content/Activity
monitors.  For the first time since the introduction of NTFS Microsoft
has introduced a new file system called ReFS which will eventually
provide functionality equivalent to Solaris' ZFS.  As a result of the
addition of ReFS, significant changes have taken place within the
installable file system (IFS) layer.  File Object IDs have grown from
64-bit to 128-bit values, Short (8.3 compatibility) names have been
discontinued, and extended attributes and alternate data streams among
other features have become optional.

Windows 8 and Server 2012 include significant security improvements as
well.  There is support for the new Kerberos Flexible Authentication
Secure Tunneling (FAST) protocol, Compound identities, Kerberos Proxy
support for obtaining Kerberos credentials when KDCs are not exposed to
the Internet, and compressed Privilege Attribute Certificate (PAC) data
in Kerberos tickets substantially reduce the chance of buffer overflow
failures during authentication with AFS, WebAuth and other systems.

The OpenAFS 1.7.17 client has undergone substantial testing with
forthcoming Windows 8 and Server 2012 products from a broad range of
vendors at two Microsoft sponsored interop events this year.

The biggest challenge for sites that wish to use OpenAFS on future
Windows devices is Microsoft's approach to locking down ARM devices.
At present there is no OpenAFS support for Windows 8 RT that will be
used in the forthcoming products such as the Microsoft Surface and
Lenovo Thinkpad Tablet 2 or in Windows Phone 8 devices from Nokia and
Samsung.  Microsoft will not allow third party file system device
drivers to be sold via the Windows 8 and Windows Phone 8 Marketplaces.
The only time an OpenAFS file system driver could appear on such a
device is if the hardware manufacturer chooses to bundle it.

While OpenAFS can never be distributed via the Marketplace for X86 and
AMD64/X64 Windows systems, there are no restrictions on the installation
of third party file systems on those platforms.

## Did You Know... About DKMS?

DKMS stands for Dynamic Kernel Module Support. Designed by Dell, DKMS allows
one to auto-build kernel modules. The auto build can take place when the system
boots a new kernel, when the new kernel version is installed, when the dynamic kernel module package itself is installed, or at any time by typing in a couple of very simple commands. No longer do you need to manually rebuild modules from source by hand. And no longer do you need to install new pre-packaged and pre-built kernel modules for every individual kernel version. After installing the DKMS version of a kernel module, you just reboot to the new kernel, and DKMS does the rest.

DKMS OpenAFS packages are available for Fedora and RedHat Enterprise Linux.
You will need to install compilers if not part of your standard install (these
are usually available as part of the linux distribution). You should install
the main DKMS RPM, available from various sources such as the EPEL (Extra
Packages for Enterprise Linux) repository. Then, in place of installing the
kmod-openafs RPMs matching your installed kernel versions, install the
dkms-openafs RPM. The install will take a bit longer than an usual RPM install
since DKMS is building an openafs kernel module for your running kernel.

And now, with each new kernel install, DKMS will ensure you have a matching OpenAFS kernel module.

Read more about DKMS in Linux Journal: [http://www.linuxjournal.com/article/6896](http://www.linuxjournal.com/article/6896)

## Case Study: Windows Roaming Profiles, Part 2

	Nathan Hatley
	Mosaic Technical Specialist-Windows Administration
	William States Lee College of Engineering
	The University of North Carolina at Charlotte

Our legacy and current computing environment is Windows XP. The XP environment consists of about 1100 XP desktops spread across several labs and hundereds of faculty/staff offices.

Roaming profiles with folder redirection allow all user data to easily and quickly roam to wherever the user is logging in. The user gets a seamless desktop experience. As all of the user's data is stored in AFS, the user's data is easily backed up. And in case of a hardware failure, this setup allows easy replacement of systems.

We are in process of testing our upgrade path from XP to Windows 7 and from Server 2003 to Server 2008 R2. We have created a brand new AD for our Windows 7 rollout so that any changes made can be guaranteed to not affect the current production environment. This also enables us to use Windows Server 2008 R2 from the start, rather than having to upgrade our production Server 2003 boxes.

The rest of this discussion targets the new Windows 7 environment. However, some also applies to the old XP environment because some settings have not changed between Windows releases.

Our environment utilizes three virtual MIT KDCs, three virtual VLDB servers, and seven bare-metal AFS fileservers offering 10TB each (2TB per vice partition).  The partitions reside on 12 1TB disks in a raid 6 array per server.  We have three virtual Windows Server 2008 R2 AD servers.  We have three server rooms in three separate buildings, so each KDC, VLDB, and AD server are split among the three server rooms.  We have two fileservers in two server rooms, and three in the last.

Currently, we have 35 Windows 7 test systems. Some of these Windows 7 test systems are virtual machines running on our several Hyper-V servers. Our workstations are running the 64-bit version of Windows 7 SP1 Enterprise.  We installed MIT Kerberos 3.2.2 64bit and 32bit, both provided by Secure-Endpoints. We also installed the new Network Identity Manager from Secure-Endpoints.  As of this writing, we are running OpenAFS 1.7.1600 64bit with the 32bit tools package also installed.

To get Roaming Profiles working, we first had to get AFS access on user login (known in AFS parlance as "integrated login") so that Windows can download the user's profile. We describe the necessary changes in appendix A1 and A2. Note that if your organization uses Windows AD as the KDC, a cross realm trust between Windows Active Directory and the MIT KDC Kerberos realm, as described in appendix A1, is unnecessary.

We store the Windows Roaming Profile in a folder under the user's AFS home directory. The Roaming Profile folder does not have to exist prior to the user's first logon as Windows will automatically create it (users have 'rlidwka' permissions for their AFS volume, so with tokens obtained at login Windows can create the folder). See appendix B1 for roaming profile configuration details. You can also choose to delete the workstation local caches of Roaming Profiles. If you do so, you must also save the contents of AppData\\Local and AppData\\LocalLow in the Roaming Profile. These are not stored with the roaming profile by default.  To store these folders with the roaming profile, see appendix B2.

Roaming Profiles have some Gotchas which need to be understood. Profile upload and download only occur at user logon / logoff. This means that if a user changes a preference, other machines that user is concurrently logged into will not see the change. Also, Roaming Profiles are subject to what we call "last write wins". In "last write wins" if a user is logged into multiple machines and logs out of one machine at a time, the Roaming Profile will only keep the configuration uploaded by the last logout. Any changes that were made on the other systems will be overwritten by the last logout and will be lost. Also, a user must have an AFS token before logging out. Otherwise, the profile upload will fail, and the user will lose any changed data. Of course, if you do not delete local Roaming Profile caches, any changed data will still reside in the Roaming Profile cache on the workstation.

In our organization, we do not limit profile size through Active Directory. Instead, we just use the user's AFS volume quota as the limiting factor.  Users must be mindful of their quotas and ensure enough space to store Roaming Profiles on logout. Otherwise the Roaming Profile upload/synchronization will fail. We have quota checks during our logon scripting that inform the user if running low on space. And if the user is at quota, we do not allow the user to login (via our pre-profile scripting mentioned below). This is to help prevent the issues resulting from not being able to store anything in AFS. Users can login to our web gateway from an unmanaged workstation to free up space in their AFS volumes.

Folder Redirection into AFS gets a little more complicated. Target folders for the redirection must exist prior to user login, or the redirection will fail.  There are two choices for a resolution to this problem.

Option one is that an organization could pre-create these folders during user AFS volume creation. The issue with this approach is that the user could accidentally delete those folders and break the profile.

Option two, our choice, is to run a script prior to user profile download. Unfortunately, Microsoft does not natively provide a means to run a script at the right time. We had to create a logon provider that would execute our script. Our implementation works but currently has a bug. This bug causes the script code to run during workstation unlock as well. Once we resolve this issue we will hopefully be able to release the code for others.

A second issue, common to both options, is that Folder Redirection configuration choices are relatively limited. This is especially true if all user volumes do not reside under a common folder. So, we chose to redirect all folders to a drive letter. And, we configured each user to map a drive letter on login. See appendix C for configuration details.

For use with Windows Folder Redirection, we have configured the OpenAFS cache size to 1GB. This larger cache size allows enough room in the  workstation OpenAFS cache for the user's Windows profile data (from Windows folder redirection into AFS) to reside in the cache.  We have also configured the chunk size for 2MB to increase network throughput for faster login / logout times for users.  See appendix D for configuration details.

Folder Redirection has some more Gotchas. The AppData\\Roaming folder stores user configuration information for most all programs a user runs. If the user's AFS token goes away, programs can no longer access this folder, which we redirect into AFS. Programs do not take kindly to their data store suddently disappearing and can start to behave oddly. Because of this potential problem, we have a monitor program, written in java, to warn the user if his or her token is about to expire. Our program then offers an AFS token renewal GUI to the user. Because the Network Identity Manager targets users who understand what AFS and what Kerberos are, we instead use our own simpler GUI. Our targeted user base is made up of university students who may or may not even know what a hard drive is!

Another gotcha is that while most applications obey Folder Redrection, some applications do
not. The end result is that a user may now have \*two\* AppData folders! When a
folder is redirected, various Microsoft functions/registry keys/environment
variables will return the path to the redirected folder instead of the default
path.  Programs that implement these standard routines will properly store
their data in the redirected folder.  Unfortunately, some programs do not
follow standard Microsoft practice and will instead store their data in a hard
coded location (more or less).  For example, the path to the roaming
application data folder can be accessed via the environment variable
"%APPDATA%".  By default, this resolves to
"C:\\Users\\<username>\\AppData\\Roaming".  But some programs instead take a
different tack and use "%USERPROFILE%\\AppData\\Roaming".  This is done
erroneously, but we cannot change the behavior of the individual program.
When the roaming application data folder is redirected, "%APPDATA%" properly
resolves to the redirected location, but "%USERPROFILE%\\AppData\\Roaming" still
resolves to a location in the regular user Roaming Profile. So, we have to
allow this 'hard coded' data to roam with the profile, even when the data
should instead be stored in the redirected folder.

Many applications will also not store files in the location pointed to by the %TEMPT% environment variable. %TEMP% by default resolves to C:\\Users\\<username>\\AppData\\Local\\Temp, on the local hard disk. Instead, the applications will store temporary files inside one of the two Appdata\\Roaming folders. If using the redirected to AFS Appdata\\Roaming folder, the application will experience a performance hit talking to AFS. This is an application specific configuration that must be attended to during application deployment.

And for another gotcha, some applications attempt to perform NTFS specific operations in redirected folders. These operations not only fail in AFS but can result in odd behavior. One example is an application attempting to store data in an alternate stream or attempting to hide a file. This will not work in AFS. So, the user may encounter the normally hidden desktop.ini files throughout the user profile. Another example is pinning a program to the taskbar. When Google Chrome is pinned to the taskbar, Windows attempts to store additional data with the shortcut so that jump lists function. Because this operation fails, Google Chrome creates an additional temporary icon that lasts as long as chrome continues running.

These issues are not show stoppers for us. And these issues will eventually be resolved. The incredible functionality brought about by combining OpenAFS with Windows Roaming Profiles and Windows Folder Redirection far exceeds any other competing solutions.

### Appendix A1.	Cross realm authentication:

Create a principal on the KDC with a strong password:

	krbtgt/<AD DOMAIN>@<KERBEROS DOMAIN>

NOTE: This principal MUST have RC4-HMAC-MD5 encryption enabled.



- 1.
AD: Active Directory Domains and Trusts
- Right-click on <domain name> properties
- Trusts
- New Trust
- next
- <KERBEROS DOMAIN>
- Realm Trust
- next
- nontransitive
- next
- One way: outgoing
- next
- Enter strong password used for principal
- next
- next
- finish.

Configure Kerberos name mapping for each user in AD:

- 1.
Active Directory users and computers
- view
- advanced features
- Right-click on a user
- Name Mappings
- Kerberos Names
- Add the Kerberos principal e.g. exampleuser@EXAMPLEDOMAIN.COM
- Assign a default domain for logon: enabled
- Set it to your Kerberos domain.
- On each workstation execute:

	ksetup /addkdc <KERBEROS DOMAIN> <Kerberos kdc server>

NOTE: execute for each kdc server you wish to add

### Appendix A2.	AFS Access on login:

- Network Security:

	Configure encryption types allowed for Kerberos:
	DES_CBC_CRC, RC4_HMAC_MD5, AES128_HMAC_SHA1, AES256_HMAC_SHA1
- \[HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\TransarcAFSDaemon\\NetworkProvider\]

	"LogonOptions"=dword:00000000
- \[HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\TransarcAFSDaemon\\NetworkProvider\\Domain\\uncc.edu\]

	"LogonOptions"=dword:00000001

### Appendix B1.	Roaming profile:

Configure roaming profile for each user in AD: Active Directory users and computers.

- 1.
Right-click on a user
- Properties
- Profile
- Under profile path

Input the path to a subfolder under the user's volume where you wish to store the profile.  This folder will have a .V2 appended to the end of it.

- Do not check for user ownership of Roaming Profile Folders: enabled
- Do not detect slow network connections: enabled
- Wait for remote user profile: enabled

### Appendix B2. Caching of Roaming Profiles

- Delete cached copies of roaming profiles: enabled

Each user must have the following registry key changed:

	HKCU\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\ExcludeProfileDirs

	AppData\Local\Temp; $Recycle.Bin; AppData\Local\Microsoft\Terminal Server Client\Cache; AppData\Local\Microsoft\Windows\Temporary Internet Files;

The default for the above key is "AppData\\Local;AppData\\LocalLow;$RecycleBin" . We change the key to "AppData\\Local\\Temp;$RecycleBin" so that the folders LocalLow and Local (except temp) will be stored with the profile.

However, "AppData\\Local" is not normally a roaming folder. So, Applications will tend to store cache data in "AppData\\Local". To control profile bloat, we exclude the "Temp" subfolder ("AppData\\Local\\Temp") from the Roaming Profile.

Any additional cache data subfolders created by programs should also be added to this exclude list to keep profile size small.

### Appendix C.	Folder redirection:

User Configuration > Policies > Windows Settings > Folder Redirection.

Configure all folders except Start Menu to redirect to a common drive letter of your choice (we selected H:).

Under the options tab, ensure the following is configured:

- Grant user exclusive rights to <folder name>: disabled.
- Move the contents of <folder name> to the new location: disabled.
- Also apply redirection policy to Windows 2000, Windows 200 server, Windows XP, and Windows Server 2003 operating systems: disabled.
- Policy removal behavior: leave contents.

Configure driver letter mapping for each user in AD:

- 1.
Active Directory users and computers.
- Right-click on a user
- Properties
- Profile
- Under Home folder, choose connect <drive letter> to:

Input the path to a subfolder under the user's volume where you wish to store the redirected folders.  This folder and all redirected subfolders must exist prior to user login.

- Intranet Sites:  Include all network paths (UNCs): enabled
- Site to Zone Assignment List: enabled, afs, \*.uncc.edu
- Allow or Disallow use of the Offline Files feature: disabled
- Turn off Windows Libraries features that rely on indexed file data: enabled
- Exclude directories in roaming profile: enabled

<input all redirected folders> ex: Desktop; Documents; Pictures; Music; Videos; Favorites; Contacts; Downloads; Links; Searches; Saved Games

NOTE:  Do NOT include AppData\\Roaming in this list, as some programs do not follow the redirected folder and will store important information here (e.g. Outlook.).

- Do not automatically make redirected folders available offline: enabled

### Appendix D.	OpenAFS Client Configuration

\[HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\AFD\\Parameters\]

- "FastSendDatagramThreshold"=dword:000005dc
- "FastCopyReceiveThreshold"=dword:000005dc

NOTE: The above values modify Microsoft's default UDP behavior.  See this message from the mailing lists for more detail: [http://lists.openafs.org/pipermail/openafs-info/2012-July/038350.html](http://lists.openafs.org/pipermail/openafs-info/2012-July/038350.html)

\[HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\TransarcAFSDaemon\\Parameters\]

- "SecurityLevel"=dword:00000000
- "FreelanceClient"=dword:00000001
- "UseDNS"=dword:00000001
- "RxMaxMTU"=dword:00000000
- "IsGateway"=dword:00000000
- "HideDotFiles"=dword:00000001
- "NoFindLanaByName"=dword:00000001
- "CacheSize"=dword:00100000
- "ChunkSize"=dword:00000015
