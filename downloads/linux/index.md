---
layout: downloads
title: Linux
---

{% assign version = site.data.version.unix %}
{% capture prefix %}{{ site.files.prefix }}/{{ version }}{% endcapture %}

## Linux ##

It is recommended to install OpenAFS using the package manager of your Linux
distribution, if an OpenAFS package is available. If packages for OpenAFS are
not included in your distribution, try finding prebuilt packages on this page.
If you cannot find any for your distribution on this page, you may need to
build OpenAFS from source.

### Fedora ###

Install the [openafs-release RPM][fedora-rpm] for OpenAFS {{ version }}, then:

`$ yum install openafs-client`

`$ yum install openafs-server`

Or you can download and install individual RPMs here:

* [Fedora 20][fedora20-rpms]
* [Fedora 19][fedora19-rpms]
* [Fedora 18][fedora18-rpms]

[fedora-rpm]: {{ prefix }}/{{ site.data.version.rpm.fedora }}
[fedora20-rpms]: {{ prefix }}/fedora-20/
[fedora19-rpms]: {{ prefix }}/fedora-19/
[fedora18-rpms]: {{ prefix }}/fedora-18/

### Red Hat Enterprise Linux ###

Install the [openafs-release RPM][rhel-rpm] for OpenAFS {{ version }}, then:

`$ yum install openafs-client`
`$ yum install openafs-server`

Or you can download and install individual RPMs here:

* [RHEL 6][rhel6-rpms]
* [RHEL 5][rhel5-rpms]

Note that OpenAFS does not currently provide RHEL7 RPMs, but some people are
trying to maintain OpenAFS packages for RHEL7 in the [CentOS storage
SIG](http://wiki.centos.org/SpecialInterestGroup/Storage). You can either find
packages elsewhere, or try to build from source.

[rhel-rpm]: {{ prefix }}/{{ site.data.version.rpm.rhel }}
[rhel6-rpms]: {{ prefix }}/rhel6/
[rhel5-rpms]: {{ prefix }}/rhel5/

### openSUSE ###

RPMs for OpenAFS {{ version }} are available for download here:

* [openSUSE 13.1]({{ prefix }}/openSUSE_13.1/)
* [openSUSE 12.3]({{ prefix }}/openSUSE_12.3/)
* [openSUSE 12.2]({{ prefix }}/openSUSE_12.2/)

### SLES ###

RPMs for OpenAFS {{ version }} are available for download here:

* [SLES 11 SP3]({{ prefix }}/SLE_11_SP3/)
* [SLES 11 SP2]({{ prefix }}/SLE_11_SP2/)
* [SLES 11 SP1]({{ prefix }}/SLE_11_SP1/)
* [SLES 11]({{ prefix }}/SLE_11/)

### Debian/Ubuntu ###

`$ apt-get install openafs-client openafs-fileserver openafs-dbserver`

### Arch Linux ###

`$ pacman -S openafs`

### Gentoo ###

Note that while an [ebuild does exist for OpenAFS in
portage](http://packages.gentoo.org/package/net-fs/openafs), it is currently a
bit out-of-date.

`$ emerge net-fs/openafs`

