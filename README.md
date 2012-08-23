libglibcurl
===========

Summary
-------
Open-source edition of the glibcurl library used by Open webOS.

Description
-----------
Glibcurl integrates the event loops of libcurl and glib. This means that a GTK+
program is able to wait for clicks, button presses etc. at the same time as 
waiting for data to arrive on the network sockets maintained by libcurl.

Dependencies
============

Below are the tools and libraries (and their minimum versions) required to build
glibcurl:

- cmake (version required by openwebos/cmake-modules-webos)
- g++ 4.6.3
- glib-2.0 2.32.1
- libcurl 7.22.0
- make (any version)
- openwebos/cmake-modules-webos 1.0.0 RC2
- pkg-config 0.26

How to Build on Linux
=====================

## Building

Once you have downloaded the source, enter the following to build it (after
changing into the directory under which it was downloaded):

    $ mkdir BUILD
    $ cd BUILD
    $ cmake ..
    $ make
    $ sudo make install

The directory under which the files are installed defaults to <tt>/usr/local/webos</tt>.
You can install them elsewhere by supplying a value for <tt>WEBOS\_INSTALL\_ROOT</tt>
when invoking <tt>cmake</tt>. For example:

    $ cmake -D WEBOS_INSTALL_ROOT:PATH=$HOME/projects/openwebos ..
    $ make
    $ make install

will install the files in subdirectories of <tt>$HOME/projects/openwebos</tt>.

Specifying <tt>WEBOS\_INSTALL\_ROOT</tt> also causes <tt>pkg-config</tt> to look
in that tree first before searching the standard locations. You can specify
additional directories to be searched prior to this one by setting the
<tt>PKG\_CONFIG\_PATH</tt> environment variable.

If not specified, <tt>WEBOS\_INSTALL\_ROOT</tt> defaults to <tt>/usr/local/webos</tt>.

To configure for a debug build, enter:

    $ cmake -D CMAKE_BUILD_TYPE:STRING=Debug ..

To see a list of the make targets that <tt>cmake</tt> has generated, enter:

    $ make help

## Uninstalling

From the directory where you originally ran <tt>make install<tt>, enter:

    $ [sudo] make uninstall

You will need to use <tt>sudo</tt> if you did not specify <tt>WEBOS\_INSTALL\_ROOT</tt>.

## Copyright and License Information

All content, including all source code files and documentation files in this repository are:

Copyright (C) 2004 Richard Atterer
Copyright (c) 2010-2012 Hewlett-Packard Development Company, L.P.

Permission to use, copy, modify, and distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT OF THIRD PARTY RIGHTS.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM,
DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE
USE OR OTHER DEALINGS IN THE SOFTWARE.

Except as contained in this notice, the name of a copyright holder shall
not be used in advertising or otherwise to promote the sale, use or other
dealings in this Software without prior written authorization of the
copyright holder.
