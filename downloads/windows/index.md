---
layout: downloads
title: Windows
---

{% assign version = site.data.version.win %}
{% capture prefix %}{{ site.files.prefix }}/{{ version }}{% endcapture %}

## Windows ##

Here you can find downloads for Windows for __OpenAFS {{ version }}__.

While you're downloading OpenAFS, feel free to look at the [Change
Log][changelog] or the [Release Notes][relnotes-html] \[[CHM][relnotes-chm]\]
\[[EPUB][relnotes-epub]\] \[[PDF][relnotes-pdf]\].

### Installers ###

* __[OpenAFS 32-bit installer][win32]__
* __[OpenAFS 64-bit installer][win64]__
* [Tools for 32-bit applications on 64-bit Windows][win32-tools]

### Debug Installers ###

Only use these if you are debugging an issue, or if you are directed to by a
developer.

* [OpenAFS 32-bit DEBUG installer][win32-debug]
* [OpenAFS 64-bit DEBUG installer][win64-debug]
* [Tools for 32-bit applications on 64-bit Windows][win32-tools-debug] (debug)

[win32]: {{ prefix }}/{{ site.data.version.msi.32bit }}
[win64]: {{ prefix }}/{{ site.data.version.msi.64bit }}

[win32-debug]: {{ prefix }}/{{ site.data.version.msi.32bit-debug }}
[win64-debug]: {{ prefix }}/{{ site.data.version.msi.64bit-debug }}

[win32-tools]: {{ prefix }}/{{ site.data.version.msi.tools }}
[win32-tools-debug]: {{ prefix }}/{{ site.data.version.msi.tools-debug }}

[changelog]: {{ prefix }}/winxp/afs-changes-since-1.2.txt
[relnotes-html]: {{ prefix }}/winxp/ReleaseNotes/html/index.html
[relnotes-chm]: {{ prefix }}/winxp/ReleaseNotes.chm
[relnotes-epub]: {{ prefix }}/winxp/ReleaseNotes.epub
[relnotes-pdf]: {{ prefix }}/winxp/ReleaseNotes.pdf
