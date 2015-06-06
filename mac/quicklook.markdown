Quick Look
==========

[Quick Look](https://support.apple.com/kb/PH18813) is the feature in OS X that
allows to quickly look at the contents of a file without opening a proper
application.  It is most prominently used within the finder by pressing the
space bar when a file is selected.

Under the hood the Quick Look renderings are done via plugins.  The name of
these plugins end in `.qlgenerator` and they can be found in many places.
The most prominent directories to find Quick Look plugins are:

```
/System/Library/QuickLook/
/Library/QuickLook/
~/Library/QuickLook/
```

Listing all Quick Look Plugins
------------------------------

To get a list of all Quick Look plugins that are currently known by the system use:

```text
$ qlmanage -m
server: living for 99s (0 requests handled) - instant off: yes - arch: X86_64 - user id: 501
memory used: 1 MB (1085008 bytes) - used descriptors: 21/256
plugins:
  org.openxmlformats.presentationml.slideshow -> /System/Library/QuickLook/Office.qlgenerator (32)
  com.adobe.pdf -> /System/Library/QuickLook/PDF.qlgenerator (675.42)
  com.apple.localized-pdf-bundle -> /System/Library/QuickLook/LocPDF.qlgenerator (675.42)
[...]
```

Installing a New Quick Look Plugin
----------------------------------

OS X already comes with a set of Quick Look plugins.  When you install some
applications they may add their own Quick Look plugins.  For some file types
there may not be a Quick Look plugin available but you may find some you can
install yourself.  Make sure you trust the developer of the plugin just like
with all software that you install.

To install copy the `*.qlgenerator` file into `/Library/QuickLook` if you want
it to be available for all users or `~/Library/QuickLook` if it should only
work for a single user.  Some Quick Look plugins may change the behaviour of
Quick Look significantly from the default given by the raw OS X that you may
want to restrict them to only those users who understand and appreciate the
change.

Suggestions for Additional Quick Look Plugins
---------------------------------------------

### EPUB ###

[EPUB Quick Look generator](https://github.com/jaketmp/ePub-quicklook) by
[jaketmp](https://github.com/jaketmp)

### Markdown ###

[QLMarkdown](https://github.com/toland/qlmarkdown/) by [Phillip Toland](https://github.com/toland)

### Plain Text without File Extensions ###

[QLStephen](http://whomwah.github.io/qlstephen/) by [Duncan Robertson](https://github.com/whomwah)

### Mail Messages ###

[DisableMail](http://www.heise.de/downloads/18/1/4/1/3/6/5/9/DisableMail_QuickLook-Plug-in.dmg)
Quick Look plugins disables rendering of mail by the default plugin.  This
prevents downloading remote contents from mail messages while quickly looking
at a mail (e.g. from a Spotlight search).  In conjunction with the QLStephen
plugin the plain text of the mail will still be shown.
