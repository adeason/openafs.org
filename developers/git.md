---
title: OpenAFS Git information
redirect-from: /cvs.html
---

The OpenAFS source code is maintained using the [Git revision control
system](http://git-scm.com/) in conjunction with
[Gerrit](http://code.google.com/p/gerrit/) for code review. The Git
repository is publicly accessible, both via the Git protocol and over
the web.

To browse the source repository via the web, go to:
[http://git.openafs.org/](http://git.openafs.org/)

To clone the repository using Git, install a Git client if you have not
already (see the [Git download page](http://git-scm.com/download) to
find one for your platform) and then run:

          git clone git://git.openafs.org/openafs.git


This will download the full repository and leave a checked-out tree in a
subdirectory of the current directory named `openafs`. The repository
itself is in the `.git` subdirectory of that directory. WARNING: The
repository is approximately 78MiB currently and will only grow, so it
may take some time to download the first time over a slow network
connection.

The current development series is in the branch named `master`. This is
the code that forms the 1.7 release series. The current 1.6 code is in
the `openafs-stable-1_6_x` branch. If you are developing new code,
please start with the `master` branch.

If you are working from a checkout of the Git repository, you will need
to run `./regen.sh` in your working tree before you can run
`./configure` and build the code as normal. This requires Autoconf and
Automake be available on your system. So the summary of commands to get
started is:

          git clone git://git.openafs.org/openafs.git
          cd openafs
          sh ./regen.sh
          sh ./configure


For information about submitting patches and the Gerrit code review
system used by OpenAFS, see the [documentation in the
wiki](http://wiki.openafs.org/AFSLore/GitDevelopers).

* * * * *

\<webmaster@openafs.org\>

Last modified: \$Date\$
