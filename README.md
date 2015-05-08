Status
======
The development of this project has been put on hold due to show stopping issues with libspotify that I don't have the energy to try to work around.
I wrote a rant about it in a [blog post](https://jonaslundqvist.net/2015/05/06/do-not-use-libspotify/) with a follow-up [here](https://jonaslundqvist.net/2015/05/07/do-use-libspotify-later-this-year/).

As Spotify says they plan to release a new library sometime later this year and then I might resume development.

If someone still would like some feature or such please go ahead and create an issue and/or pull request here on GitHub and I'll see what I can do.

About
=====
This plugin adds support for playing spotify tracks in VLC media player.
The code should be seen as a prototype and I can't claim that it is "work in progress" since I don't really know if I will further develop it into something useful. Please fork! :)

Why?
====
I did this to play around with libspotify and VLC.

Prerequisites
=============
 * Spotify Preemium account
 * libspotify (https://developer.spotify.com/technologies/libspotify/)
 * libspotify application key (https://devaccount.spotify.com/my-account/keys/)
 * VLC headers and libraries

Installation
============
Get an appkey from spotify and copy it to *src/appkey.c*.
View and edit the Makefile in the *src/* directory if necessary.

For linux
---------
Type *make*.
Copy the *src/libspotify_plugin.so* to the vlc access plugins folder, possibly */usr/lib/vlc/plugins/access*

For win32
---------
The plugin is cross-compiled using mingw. Please note that the win32 version of VLC is needed and it will not work with the 64 bit version due to Spotify not providing a 64 bit library for Windows.

Unzip the libspotify zip file (from spotify) somewhere and set the *$LIBSPOTIFY_WIN32_DIR* to that base path.
Copy *extras/libspotify.def* to the same directory as the *libspotify.dll*, ie *$LIBSPOTIFY_WIN32_DIR/lib* and cd to that directory. Run *i686-w64-mingw32-dlltool -U -d libspotify.def -l libspotify.a*

Back in the *src/* directory run *make OS=win32*.
Copy the *libspotify_plugin.dll* to the windows systems *vlc/plugins/access/* folder

Usage
=====
Start VLC and find the spotify preferences and set the option(s) accordingly.

Start from gui:
File -> Open Network Stream -> spotify://spotify:track:6wNTqBF2Y69KG9EPyj9YJD -> Play

Or from command line:
vlc spotify://spotify:track:6wNTqBF2Y69KG9EPyj9YJD

vlc-spotify also supports https://open.spotify.com/ URLs.

License
=======
GNU LGPL 2.1. See the file *LICENSE*.
