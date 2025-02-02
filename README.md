XBOXDRV-NXT Modded Xbox/Xbox360 USB Gamepad Driver for Userspace by Liontek1985
=============================================

Basic-Code:	Retropie - xboxdrv</br>
Moded-Code:	Liontek1985</br>
Scrips:		Liontek1985</br>
License:	CC BY-NC-SA 4.0</br>

![pic001](https://github.com/microplay-hub/mpcore-library/raw/main/Imagebase/_Moduls/xboxdrvnxt-modul.png "Modul Picture")
![pic002](https://github.com/microplay-hub/mpcore-library/raw/main/Imagebase/_Moduls/xboxdrvnxt-modul-cf.png "Modul Picture")


Xbox/Xbox360 USB Gamepad Driver for Userspace
=============================================

Xboxdrv is a Xbox/Xbox360 gamepad driver for Linux that works in
userspace. It is an alternative to the xpad kernel driver and has
support for Xbox1 gamepads, Xbox360 USB gamepads and Xbox360 wireless
gamepads. The Xbox360 guitar and some Xbox1 dancemats might work too.
The Xbox 360 racing wheel is not supported, but shouldn't be to hard
to add if somebody is interested.

Some basic support for the Xbox360 Chatpad on USB controller is
provided, Chatpad on wireless ones is not supported. The headset is
not supported, but you can dump raw data from it.

This driver is only of interest if the xpad kernel driver doesn't work
for you or if you want more configurability. If the xpad kernel driver
works for you there is no need to try this driver.

Newest version of the driver can be found at:

 * http://pingus.seul.org/~grumbel/xboxdrv/

The development version can be optained via:

 * git clone http://pingus.seul.org/~grumbel/xboxdrv.git


Compilation
-----------

Required libraries and tools:

 * g++ - GNU C++ Compiler
 * libusb-1.0
 * pkg-config
 * libudev
 * boost
 * scons
 * uinput (userspace input kernel module)
 * git (only to download the development version)
 * X11
 * libdbus
 * glib

Once everything installed, you can compile by typing:

    scons

On Ubuntu 10.10 you can install all the required libraries via:

    sudo apt-get install \
     g++ \
     libboost1.42-dev \
     scons \
     pkg-config \
     libusb-1.0-0-dev \
     git-core \
     libx11-dev \
     libudev-dev \
     x11proto-core-dev \
     libdbus-glib-1-dev

To load the uinput kernel module automatically on boot add it
/etc/modules, to load it manually type:

    sudo modprobe uinput

On other distributions exact install instructions might be
slightly different.


Installation
------------

Once the compilation process is complete you can install xboxdrv with:

    make install

You can also change the install PREFIX and DESTDIR as usual with:

    make install PREFIX=/usr DESTDIR=/tmp

Note that there is no need to install xboxdrv, you can run it directly
from the source directory if you prefer.

If you want to run xboxdrv in daemon mode on boot, copy
`data/org.seul.Xboxdrv.conf` into `/etc/dbus-1/system.d/`, otherwise xboxdrv will complain with:

    [ERROR] XboxdrvDaemon::run(): fatal exception: failed to get unique dbus name: Connection ":1.135" is not allowed to own the service "org.seul.Xboxdrv" due to security policies in the configuration file


Running
-------

Extensive documentation on running xboxdrv can be found in the RUNNING
XBOXDRV section of the xboxdrv manpage. When you haven't installed
xboxdrv the man page can be found in doc/xboxdrv.1 and be read with:

    man -l doc/xboxdrv.1

Documentation on xboxdrv-daemon, a daemon that will automatically
launch xboxdrv when a pad is plugged in can be read via:

    man -l doc/xboxdrv-daemon.1
