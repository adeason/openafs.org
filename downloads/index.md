---
title: Downloads
layout: downloads
---

## Downloads ##

### Binaries ###

To download the latest stable release of OpenAFS, choose your platform:

<ul class="download-list-items">
  <li class="item"><a class="osicon windows" href="windows/">Windows</a></li>
  <li class="item"><a class="osicon mac" href="mac/">Mac OS X</a></li>
  <li class="item"><a class="osicon linux" href="linux/">Linux</a></li>
  <li class="item"><a class="osicon solaris" href="solaris/">Solaris</a></li>
  <Li class="item"><a class="osicon freebsd" href="freebsd/">FreeBSD</a></Li>
  <li class="item"><a class="osicon aix" href="aix/">AIX</a></li>
</ul>

[Older releases]({{ site.files.prefix }}) are also available.

If your platform is not listed here, you may need to build from source to
install OpenAFS.

### Source ###

Source code for the latest stable release is also available:

* Stable source for Windows: \[[.tar.gz][win-src-gz]\] \[[.tar.bz2][win-src-bz2]\]
* Stable documentation for Windows: \[[.tar.gz][win-doc-gz]\] \[[.tar.bz2][win-doc-bz2]\]
* Stable source for other platforms: \[[.tar.gz][unix-src-gz]\] \[[.tar.bz2][unix-src-bz2]\]
* Stable documentation for other platforms: \[[.tar.gz][unix-doc-gz]\] \[[.tar.bz2][unix-doc-bz2]\]
* [Source RPM][srpm]

For information about retrieving the source via git, building the source, or
other information, see [the Developers page]({{ site.baseurl }}/developers).

{% capture winprefix %}{{ site.files.prefix }}/{{ site.data.version.win }}{% endcapture %}
{% capture unixprefix %}{{ site.files.prefix }}/{{ site.data.version.unix }}{% endcapture %}

[win-src-gz]:  {{ winprefix }}/openafs-{{ site.data.version.win }}-src.tar.gz
[win-src-bz2]: {{ winprefix }}/openafs-{{ site.data.version.win }}-src.tar.bz2
[win-doc-gz]:  {{ winprefix }}/openafs-{{ site.data.version.win }}-doc.tar.gz
[win-doc-bz2]: {{ winprefix }}/openafs-{{ site.data.version.win }}-doc.tar.bz2

[unix-src-gz]:  {{ unixprefix }}/openafs-{{ site.data.version.unix }}-src.tar.gz
[unix-src-bz2]: {{ unixprefix }}/openafs-{{ site.data.version.unix }}-src.tar.bz2
[unix-doc-gz]:  {{ unixprefix }}/openafs-{{ site.data.version.unix }}-doc.tar.gz
[unix-doc-bz2]: {{ unixprefix }}/openafs-{{ site.data.version.unix }}-doc.tar.bz2

[srpm]: {{ unixprefix }}/{{ site.data.version.srpm }}
