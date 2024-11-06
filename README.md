# uln

Uln is a symbolic link creator (or file copier) controlled via config file.

Uln looks for a file named *.uln* in the current directory. This file defines a
root link/copy destination directory and a list of target source files. Link
targets may be dependent upon system hostname by appending it to target
filenames.

## Usage

    $ uln <command> [option...]

### Commands

`init`
: Create a new *.uln* file in current directory.

`link`
: Create symbolic links defined in *.uln* file.

`copy`
: Copy files defined in *.uln* file.

### Options

`-D, --dryrun`
: Perform trial run making no changes.

`-V, --verbose`
: Print existing links/copies.

`-c, --config <file>`
: Source alternative config file.

`-d, --dir <directory>`
: Set root destination directory.

`-s, --src <file>`
: Add to list of source files.

`-H, --help`
: Display help and exit.

## Config

*.uln* - yaml file containing the following keys:

*dest* or *dir*
: Link/copy destination directory. (required)

*srcs*
: List of source files. (optional)

## Hostname

Created links/copies may be dependent upon system hostname by appending an
underscore and the hostname to source filenames.

For example, if *file.txt* is listed in *srcs*, uln will create a link to
*file_<hostname>.txt*, if it exists, instead of *file.txt*.

## Example

Uln can be used to store one's dotfiles in a separate root folder for easy
version control, syncing with other machines, etc.

Consider a folder *.dotfiles/* in a user's home directory that contains a
number of subdirectories and files, mirroring the structure of the user's home
directory. *.dotfiles/* also contains a file named *.uln* with the following
content:

```yaml
    dest: ~
    srcs:
    - .bashrc
    - .config/feh/
    - .config/mpv/input.conf
    - .vim/
```

When the user runs `uln link` from within *.dotfiles/*, corresponding links are
created in the user's home directory to the files listed in *srcs*.

The user has several machines that share the contents of *.dotfiles/*. By
creating an additional file named *.bashrc_debian-pc* alongside the original
*.bashrc* in *.dotfiles/*, the user is able to manage and source a different
*.bashrc* file on their debian machine.

----
[Chris Magyar](https://mags.zone)\
[GPLv3](https://www.gnu.org/licenses/gpl-3.0)

<!--metadata:
author: Chris Magyar <c.magyar.ec@gmail.com>
description: Automated symbolic link creator.
keywords: uln, symbolic link, bash
-->
