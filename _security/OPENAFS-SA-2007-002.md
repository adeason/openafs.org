---
id: 2007-002
title: OpenAFS for Windows clients denial of service vulnerability
issued: 19-Apr-2007
updated: 19-Apr-2007
severity: Medium
affected: OpenAFS 1.3.64-1.3.99, OpenAFS 1.4.0-1.4.4, OpenAFS 1.5.0-1.5.18
---

OpenAFS for Windows installs a Network Provider module, afslogon.dll,
which is loaded by the Windows Logon service, winlogon.exe. When MIT
Kerberos for Windows is installed, afslogon.dll will attempt to perform
operations that involve the Kerberos v5 libraries. Successful use of
Kerberos v5 requires the ability to establish a krb5\_context. Parsing
errors in the Kerberos v5 configuration profile, krb5.ini, will prevent
the successful creation of a krb5\_context. afslogon.dll attempts to
free a krb5\_context whether or not it was successfully established.
This produces a memory access error that in turn forces the Windows
Logon Service to terminate unexpectedly and causes Microsoft Windows to
halt.

There are no known publicly-available exploits for this vulnerability at
this time.


