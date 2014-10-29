Packaging Perl Software
=======================

[TIMTOWTDI](https://en.wikipedia.org/wiki/TIMTOWTDI): this is how I prefer
doing Perl software packaging currently.

The Simplest Package
--------------------

Create a directory with just one file called `dist.ini` as follows:

```ini
# dist.ini
name    = Foo-Bar
author  = Elmar S. Heeb <elmar@heebs.ch>
license = GPL_3
copyright_holder = Elmar S. Heeb
copyright_year   = 2014
version = 1
abstract = Bar the Foo
[@Basic]
```

This corresponds to a package with no actual contents but only infrastructurei.
Nevertheless, it is a perfect starting point.  What will be produced is called
a distribution in Perl (CPAN) nomenclature or a package in Debian.

The following `dzil` commands work and do what they should

```shell
dzil build
dzil test
dzil clean
```