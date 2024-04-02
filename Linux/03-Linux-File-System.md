# LINUX FILE SYSTEM

The Linux file system is a hierarchical structure that organizes and stores data on a Linux-based operating system. It provides a unified way to manage files, directories, devices, and other resources.

### Filesystem Hierarchy Standard

The FHS standard categorizes each system directory in a couple of ways:

* A directory can be categorized as either shareable or not, referring to whether the directory can be shared on a network and used by multiple machines.
* The directory is put into a category of having either static files (file contents won't change) or variable files (file contents can change).

The FHS standard defines four hierarchies of directories used in organizing the files of the filesystem. The top-level or root hierarchy follows:

| Directory	| Contents |
|--------|--------|
| /	| The base of the structure, or root of the filesystem, this directory unifies all directories regardless of whether they are local partitions, removable devices, or network shares |
| /bin |	Essential binaries like the ls, cp, and rm commands, and be a part of the root filesystem |
| /boot |	Files necessary to boot the system, such as the Linux kernel and associated configuration files |
| /dev |	Files that represent hardware devices and other special files, such as the /dev/null and /dev/zero files |
| /etc |	Essential host configurations files such as the /etc/hosts or /etc/passwd files |
| /home |	User home directories |
| /lib |	Essential libraries to support the executable files in the /bin and /sbin directories |
| /lib64 |	Essential libraries built for a specific architecture. For example, the /lib64 directory for 64-bit AMD/Intel x86 compatible processors |
| /media |	Mount point for removable media mounted automatically |
| /mnt |	Mount point for temporarily mounting filesystems manually |
| /opt |	Optional third-party software installation location |
| /proc |	Virtual filesystem for the kernel to report process information, as well as other information |
| /root |	Home directory of the root user |
| /sbin |	Essential system binaries primarily used by the root user |
| /sys |	Virtual filesystem for information about hardware devices connected to the system |
| /srv |	Location where site-specific services may be hosted |
| /tmp |	Directory where all users are allowed to create temporary files and that is supposed to be cleared at boot time (but often is not) |
| /usr |	**Second hierarchy**. Non-essential files for multi-user use |
| /usr/local |	**Third hierarchy**. Files for software not originating from distribution |
| /var |	**Fourth hierarchy**. Files that change over time |
| /var/cache |	Files used for caching application data |
| /var/log |	Most log files |
| /var/lock |	Lock files for shared resources |
| /var/spool |	Spool files for printing and mail |
| /var/tmp |	Temporary files to be preserved between reboots |

The second and third hierarchies, located under the /usr and /usr/local directories, repeat the pattern of many of the key directories found under the first hierarchy or root filesystem. The fourth hierarchy, the /var directory, also repeats some of the top-level directories such as lib, opt and tmp.

While the root filesystem and its contents are considered essential or necessary to boot the system, the /var, /usr and /usr/local directories are deemed non-essential for the boot process. 

The /usr/local hierarchy is for installation of software that does not originate with the distribution. Often this directory is used for software that is compiled from the source code.


Software Application Directories

Unlike the Windows operating system, where applications may have all of their files installed in a single subdirectory under the C:\Program Files directory, applications in Linux may have their files in multiple directories spread out throughout the Linux filesystem. For Debian-derived distributions, you can execute the dpkg -L packagename command to get the list of file locations. In Red Hat-derived distributions, you can run the rpm -ql packagename command for the list of the locations of the files that belong to that application.

The executable program binary files may go in the /usr/bin directory if they are included with the operating system, or else they may go into the /usr/local/bin or /opt/application/bin directories if they came from a third party.

The data for the application may be stored in one of the following subdirectories:
* /usr/share
* /usr/lib
* /opt/application
* /var/lib
The file related to documentation may be stored in one of the following subdirectories:
* /usr/share/doc
* /usr/share/man
* /usr/share/info
The global configuration files for an application are most likely to be stored in a subdirectory under the /etc directory, while the personalized configuration files (specific for a user) for the application are probably in a hidden subdirectory of the user's home directory.


Library Directories

Libraries are files which contain code that is shared between multiple programs. Most library file names end in a file extension of .so, which means shared object.
The libraries that support the essential binary programs found in the /bin and /sbin directories are typically located in either /lib or /lib64.

To support the /usr/bin and /usr/sbin executables, the /usr/lib and /usr/lib64 library directories are typically used.
For supporting applications that are not distributed with the operating system, the /usr/local/lib and /opt/application/lib library directories are frequently used.