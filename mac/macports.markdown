MacPorts Hints
==============

Perl
----

Upgrade to a new perl version.

First list the available variants:

    port variants perl5

Then change to the version you want:

    port deactivate perl5
    port install perl5 +perl5_20

Package List
------------

When doing an OS X upgrade the
[MacPorts Migration Guide](https://trac.macports.org/wiki/Migration) recommends
wiping all pachages from the old installation and then just installing all
those packages again.  This is good advice and it can even be automated in most
cases.  However, it is also a good idea to go over the list of installed
packages and only selectively install the ones that are actually needed.
Unfortunately, MacPorts does not distinguish whether a packages was requested
to be installed directly or whether it came in via a dependency.  The one
pragmatic solution for now that I can think of is to keep such a list of
desired packages manually.

This is my personal list of MacPorts packages that I keep here for my
convenience.  If someone else can make use of it too, I'm happy to share.

Perl first: with a new OS X version the system provided version of Perl is
usually fairly modern and there would be no need to install a MacPorts version.
Due to dependencies a MacPorts-Perl version might creep in anyway.  Better make
sure it is at least a current one, so choose to install as recent a Perl
version as seems resonable to be prepared.

    port install perl5 + perl5_20

TODO: This needs to be fleshed out more (setting defaults etc.)
This might apply for other interpreters too.

Then just a bunch of useful programs

    for p in \
        jhead \
        mosh \
        ncdu \
        tree \
        wget \
        wireshark \
    ; do
        port install $p
    done

