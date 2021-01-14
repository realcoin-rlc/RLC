
Debian
====================
This directory contains files used to package realcoind/realcoin-qt
for Debian-based Linux systems. If you compile realcoind/realcoin-qt yourself, there are some useful files here.

## realcoin: URI support ##


realcoin-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install realcoin-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your realcoin-qt binary to `/usr/bin`
and the `../../share/pixmaps/realcoin128.png` to `/usr/share/pixmaps`

realcoin-qt.protocol (KDE)

