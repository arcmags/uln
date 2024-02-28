# uln

Uln is a symbolic link creator and/or file copier controlled via config file.

Uln reads a *.uln* file in the current directory. This file defines source
files for linking/coping and destination directory for these links/files.
Target files may be dependent upon hostname by appending it to their names.

## Usage

    uln <COMMAND> [OPTIONS]

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

*.uln* - yaml file defining target files, contains the following keys:

*dest*
: Destination directory for links/copies. Required.

*srcs*
: List of target files relative to directory containing *.uln* file.

## Hostname

The files linked to/copied from may be dependent upon the system hostname by
appending an underscore and the desired hostname to the file name. For example,
if *FILE.EXT* is in *targets*, a link to *FILE\_HOSTNAME.EXT* will be created,
if it exists, instead of *FILE.EXT*.

## Requirements
- yq

----
[Chris Magyar](https://mags.zone)\
[GPL v3](https://www.gnu.org/licenses/gpl-3.0)

<!--metadata:
author: Chris Magyar <c.magyar.ec@gmail.com>
description: Automated
keywords: uln, link, symbolic link
css: ../css/main.css
-->
