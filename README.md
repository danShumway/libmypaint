## libmypaint - MyPaint brush engine library

[![Translation Status](https://hosted.weblate.org/widgets/mypaint/libmypaint/svg-badge.svg)](https://hosted.weblate.org/engage/mypaint/?utm_source=widget)
[![Travis Build Status](https://travis-ci.org/mypaint/libmypaint.png?branch=master)](https://travis-ci.org/mypaint/libmypaint)
[![Appveyor Build Status](https://ci.appveyor.com/api/projects/status/vc6ejt4nba5ctd6r)](https://ci.appveyor.com/project/jonnor/libmypaint)

This is a self-contained C library that is isolated from MyPaint.
It allows other applications to make use of the MyPaint brush engine.

License: ISC, see [COPYING](./COPYING) for details

### Prerequisites

Build dependencies:

* [json-c](https://github.com/json-c/json-c/wiki) (>= 0.11)
* [GObjectIntrospection](https://live.gnome.org/GObjectIntrospection)

Optional dependencies:

* [Python](http://python.org/) (for builds from git)
* `autotools` and `intltool` (for builds from git)
* [GEGL + BABL](http://gegl.org/) (for --enable-gegl,
  note that GIMP does *not* require this option.)

### Building

#### Maintainer mode / from git

Now libmypaint uses autotools conventions,
so you have to kickstart the build environment with:

    $ ./autogen.sh

This script is for the hackers who want to generate the configure script
the first time from `configure.ac`.
Users won't have to deal with it
and will have the configure generated from the start.

The distribution release can be generated with:

    $ make dist

And it should be checked before public release with:

    $ make distcheck

#### Everyone else

Now run:

    $ ./configure

As usual, add any of the common GNU options, like --prefix, --host (for
cross-compilation), --enable-shared/static to build whatever you want,
--bindir/libdir/includedir/whateverdir for any hardcore user who like to
play with one's environment and so on.

Then the libmypaint specific options:
--enable-docs/debug/profiling/openmp/gperftools/i18n/introspection/gegl
and --with-glib.

You can get the full list with `./configure -h`.

Then run

    `make`

and

    `make install`

Afterwards, you can run all the unit tests with make check (works now with
both shared and static libs), update the po files from the source code
with cd po && make update-po. Common/practical GNU stuff. :-)

### Localization

List of language is maintained in po/LINGUAS (currently it has all the
lang, I left a comment on the top of the files with a command line to
get the full list of languages. But you can also disable languages by
removing them from the list if needed).

A list of files where localizable strings can be found is maintained
in `po/POTFILES.in`.

### Documentation

Further documentation can be found in the MyPaint wiki:
<https://github.com/mypaint/mypaint/wiki/Brushlib>.
