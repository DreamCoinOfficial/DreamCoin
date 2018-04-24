
Debian
====================
This directory contains files used to package dremd/drem-qt
for Debian-based Linux systems. If you compile dremd/drem-qt yourself, there are some useful files here.

## drem: URI support ##


drem-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install drem-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your dremqt binary to `/usr/bin`
and the `../../share/pixmaps/drem128.png` to `/usr/share/pixmaps`

drem-qt.protocol (KDE)

