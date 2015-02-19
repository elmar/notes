Some Notes on __locale__ settings
=================================

As of this writing (OS X Yosemite, 10.10.2) the default setting of a shell in
OS X includes the environment variable `LC=CTYPE=UTF-8`.  This in and of itself
is a good thing and should not be unset or changed without proper
consideration.

However, if you use a Mac to log into other computers via ssh you may note errors relating to locale settings and specifically to `LC_CTYPE`.  A typical error message may read

    -bash: warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory

This indicates that the remote system does not support this specific setting of
UTF-8.  Unfortunately, locale settings are evolving (which is a good thing) and
older systems do not know about newer conventions.  On top of that the
conventions are only gradually converging.  Specifically, there are systems
that support and expect `UTF-8` and others support `utf8`.  More recent setup
should support both as equivalent (one being treated as an alias to the other).

For the `ssh` connection in particular the problem arises that OS X by default sends all `LC_*` and the `LANG` settings as environment variables over to the remote host.  If the remote host happens not to support the given setting(s) of the local system it will complain.  There are two ways out of this dilemma.  You can either tell the local system not to send these environment variables or the remote one not to accept them.

On the local system find the file `ssh_config` (on OS X it is at
`/etc/ssh_config`, on typical Linux systems it is at `/etc/ssh/ssh_config`) and
disable the setting (e.g., by commenting it out)

    # SendEnv LANG LC_*

On the remote system find the file `sshd_config` (on OS X it is at
`/etc/sshd_config`, on typical Linux systems it is at `/etc/ssh/sshd_config`)
and disable the setting (e.g., by commenting it out)

    # AcceptEnv LANG LC_*

If you can choose it is preferable to disable only the `SendEnv` part and leave
the `AcceptEnv` part as is.  This way each user can choose which of the
environment variable they want to transfer in their own `${HOME}/.ssh/config`
file.  The user typically has no influence on the remote sshd nor can they
unset a global `SendEnv` setting on the local system.

By disabling the automatic transfer of the `LC_*` and `LANG` setting you will
loose the advantage of having your language preference automatically set even
for remote connections.  On the other hand this only makes sense when working
in a network of computers all supporting the same settings.  Typically, this is
only the case for homogenous networks with all computers on the same version of
the operating system.
