Mac Power Management
====================

Hybernation
-----------

By default OS X saves its state to battery powered RAM and to hard disk.  This
will prevent data loss in case of power failures.  It will also take time to
close and open a MacBook.  Most of the time its more of a nuissance than a
help.  Here is how you can change the settings.

    $ sudo -i
    # pmset -g | grep hibernate
     hibernatefile        /var/vm/sleepimage
     hibernatemode        3
    # pmset -a hibernatemode 0

Settings other than 0 are possible.

After that you may want to reclaim the swapfile (of the size of you RAM!)

    # ls -l /var/vm/sleepimage
    -rw------T  1 root  wheel  4294967296 Nov 26 09:59 sleepimage
    # rm /var/vm/sleepimage
    # touch /var/vm/sleepimage
    # chflags uchg /var/vm/sleepimage

You need to make a 0 Byte immutable file in place of it.  Otherwise the system
will regenerate the file.  The other files in `/var/vm` are swap files that
start with every reboot and tend to grow.

Further Reading
---------------

The manual page for pmset will tell you more about the settings you can read and/or tweak for power management.  See

    $ man pmset