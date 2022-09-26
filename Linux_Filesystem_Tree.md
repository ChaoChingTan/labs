# The Linux Filesystem Tree

Many Linux distributions partially follow the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/). The FHS may help make more Unix/Linux file system trees conform better in the future.

To find information about the file system hierarchy, run the command:

> man hier

## Typical directories

* / - All Linux systems have a directory structure that starts at the root directory.
* /boot - The /boot directory contains all files needed to boot the computer.
* /bin - The /bin directory contains binaries for use by all users.
* /dev - Device files in /dev appear to be ordinary files, but are not actually located on the hard disk. The /dev directory is populated with files as the kernel is recognising hardware.
* /etc - All of the machine-specific configuration files should be located in /etc.
* /home - Users can store personal or project data under /home
* /lib - Binaries found in /bin and /sbin often use shared libraries located in /lib.
* /media - The /media directory serves as a mount point for removable media devices such as CDROM's, digital cameras, and various usb-attached devices.
* /mnt - The /mnt directory should be empty and should only be used for temporary mount points
(according to the FHS).
* /opt - The purpose of /opt is to store optional software. In many cases this is software from outside the distribution repository. You may find an empty /opt directory on many systems.
* /proc - /proc is another special directory, appearing to be ordinary files, but not taking up disk
space. It is actually a view of the kernel, or better, what the kernel manages, and is a means
to interact with it directly. /proc is a proc filesystem.
* /root - On many systems /root is the default location for personal data and profile of the root user.
* /sbin -   /sbin contains binaries to configure the operating system. Many of the system binaries
require root privilege to perform certain tasks.
* /sys - Since 2.6 kernel, Linux uses sysfs to support usb and IEEE 1394 (FireWire) hot plug devices. /sys directory contains kernel information about hardware.
* /tmp - Applications and users should use /tmp to store temporary data when needed. Data stored
in /tmp may use either disk space or RAM. Both of which are managed by the operating system. Never use /tmp to store data that is important or which you wish to archive.
* /usr - Although /usr is pronounced like user, it stands for Unix System Resources. The /usr hierarchy should contain shareable, read only data. Some people choose to mount /usr as read only.
* /var - Variable data. Files that are unpredictable in size, such as log, cache and spool files, should be located in /var.

## Lab

1. Determine the Sizes of the Default Linux Directories using du command
2. Examine the /proc Filesystem

## Reference

* [Linux Fundamentals Textbook](https://linux-training.be/linuxfun.pdf)
  * Chapter 11 - Linux file tree
