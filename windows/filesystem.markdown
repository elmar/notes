Notes about Filesystems in Windows
==================================

Some characters like a colon are illegal in a file name under Windows.  To force a literal interpretation use `\\?\` to quota a file name.  E.g., to delete a file use

    del \\?\D:\foo:bar.txt

[via SuperUser](http://superuser.com/a/615067/389435) (a [StackExchange](http://stackexchange.com) site)
