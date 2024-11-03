# uln

Uln is a symbolic link creator and/or file copier controlled via config file.

Uln reads a *.uln* file in the current directory. This file defines source
files for linking/coping and destination directory for these links/files.
Target files may be dependent upon hostname by appending it to their names.

## Usage

    $ uln <COMMAND> [OPTION...]

### Commands

`init`
: Create a new *.uln* file in current directory.

`link`
: Create symbolic links defined in *.uln* file.

`copy`
: Copy files defined in *.uln* file.

### Options

`-c, --config <FILE>`
: Read config from *FILE* instead of .uln default.

`-D, --dry-run`
: Perform dry run making no changes.

`-H, --help`
: Display help and exit.

## Config

*.uln* - yaml file containing following keys:

*dest*
: Links/copy destination directory. (required)

*srcs*
: List of source files. (required)

## Hostname

The file linked to/copied may be dependent upon system hostname by appending an
underscore and the desired hostname to the file name.

For example, if *FILE.EXT* is in *srcs* and a *FILE\_HOSTNAME.EXT* exists, uln
will link/copy that file instead of *FILE.EXT*.

----
[Chris Magyar](https://mags.zone)\
[GPLv3](https://www.gnu.org/licenses/gpl-3.0)

<!--metadata:
author: Chris Magyar <c.magyar.ec@gmail.com>
description: Automated symbolic link creator.
keywords: uln, link, symbolic link
-->
