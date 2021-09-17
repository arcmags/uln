===
uln
===

This is an automated symbolic link creator and/or file copier controlled with a
basic config file.  The files linked/copied can be dependent upon the system
hostname.  I use this to link all my dotfiles to a single location that
contains the config files for every one of my systems.


Synopsis
========

``uln <COMMAND> [OPTIONS]``


Commands
========

``init``
    Create a new .uln file in current directory.

``link``
    Create symbolic links defined in .uln file.

``copy``
    Copy files defined in .uln file.


Options
=======

``-c, --config <FILE>``
    Read config from FILE instead of .uln default.

``-D, --dry-run``
    Perform trial run making no changes.

``-H, --help``
    Display help and exit.


Files
=====

*.uln*
    The ``init`` command creates a file named *.uln* in the current
    directory.  This file has two sections: [dir] and [targets].

    ``[dir]``
        This section defines the base directory to create symbolic links
        in or copy files to.  Only the first directory listed will be used.

    ``[targets]``
        This section is a list of target files.  Files are listed relative
        to the current directory.  Any link created or file copied is
        done so in a corresponding subdirectory.


Hostname
========

The file linked to/copied may be dependent upon the system hostname by
appending an underscore and the desired hostname to the file name.  For
example, if the ``[targets]`` section of *.uln* lists a file named *FILE.EXT*, a
link to/copy of a file named *FILE_HOSTNAME.EXT* will be created, if it
exists, instead of *FILE.EXT*.


Credits
=======

:Author:
    Chris Magyar

:License:
    GPL 3.0
