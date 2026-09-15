# Linux Directory Structure

## 1. Introduction

Linux uses a hierarchical directory structure to organize files and folders.

Unlike Windows, Linux does not use drive letters such as `C:`, `D:`, or `E:` to organize the file system.

In Linux, everything starts from a single main directory called the **root directory**, represented by:

```text
/
```

All other directories and files exist under this root directory.

---

# 2. Basic Linux Directory Structure

A typical Linux system has a structure similar to this:

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

Each directory has a specific purpose.

---

# 3. Root Directory `/`

The `/` directory is called the **root directory**.

It is the top-level directory of the Linux file system.

All other directories are located inside `/`.

### Example

```bash
cd /
```

To see the directories inside `/`:

```bash
ls
```

You may see:

```text
bin
boot
dev
etc
home
lib
media
mnt
opt
proc
root
run
sbin
srv
sys
tmp
usr
var
```

### Simple Example

Think of `/` as the main building.

All other directories are rooms inside that building.

```text
/
├── home
├── etc
├── usr
└── var
```

---

# 4. `/bin` - Essential User Commands

`/bin` contains essential command-line programs used by users.

Examples include commands such as:

```text
ls
cp
mv
rm
cat
pwd
```

You can view the directory using:

```bash
ls /bin
```

### Use Case

When you execute:

```bash
ls
```

the `ls` program is available as part of the system's essential commands.

> On many modern Linux distributions, `/bin` may be a symbolic link to `/usr/bin`.

---

# 5. `/boot` - Boot Files

The `/boot` directory contains files required to start the Linux operating system.

It may contain:

```text
Linux kernel
GRUB bootloader files
Initial RAM filesystem
```

Check it using:

```bash
ls /boot
```

### Use Case

When your computer starts, the bootloader and kernel files in this area are involved in starting Linux.

> Do not modify files in `/boot` unless you understand what you are doing.

---

# 6. `/dev` - Device Files

`/dev` contains special files that represent hardware and devices.

Examples include:

```text
/dev/sda
/dev/sdb
/dev/tty
/dev/null
```

Check it using:

```bash
ls /dev
```

### Use Case

Linux treats many hardware devices as files.

For example:

```text
/dev/sda
```

may represent a storage device.

Another example:

```text
/dev/null
```

is a special device that discards data sent to it.

Example:

```bash
echo "Hello" > /dev/null
```

The text is discarded.

---

# 7. `/etc` - Configuration Files

`/etc` contains system-wide configuration files.

Examples include:

```text
/etc/hostname
/etc/hosts
/etc/passwd
/etc/ssh/
```

Check it using:

```bash
ls /etc
```

### Use Case

If you configure SSH, some configuration files are stored under:

```text
/etc/ssh/
```

For example:

```text
/etc/ssh/sshd_config
```

contains SSH server configuration.

---

# 8. `/home` - User Home Directories

`/home` contains the personal directories of normal users.

Example:

```text
/home/
├── alice/
├── bob/
└── ubuntu/
```

If your username is `ubuntu`, your home directory is usually:

```text
/home/ubuntu
```

You can check your home directory with:

```bash
pwd
```

or:

```bash
echo $HOME
```

Example output:

```text
/home/ubuntu
```

### What can be stored here?

Users can store:

```text
Documents
Downloads
Pictures
Videos
Projects
Personal files
```

---

# 9. `/lib` - System Libraries

`/lib` contains important libraries required by system programs and commands.

Libraries are files that provide functionality used by other programs.

For example:

```text
/lib
```

may contain shared libraries required for system operations.

> On modern distributions, `/lib` may be linked to a directory under `/usr`.

---

# 10. `/media` - Removable Devices

`/media` is commonly used for automatically mounted removable storage devices.

Examples:

```text
USB drive
External hard drive
CD/DVD
```

For example:

```text
/media/username/USB
```

### Use Case

When you connect a USB drive, your desktop environment may automatically mount it under `/media`.

You can check:

```bash
ls /media
```

---

# 11. `/mnt` - Temporary Mount Point

`/mnt` is traditionally used as a temporary location for mounting file systems.

For example:

```text
/mnt/mydrive
```

An administrator might mount a disk using:

```bash
sudo mount /dev/sdb1 /mnt/mydrive
```

Then the files on that disk can be accessed through:

```bash
cd /mnt/mydrive
```

---

# 12. `/opt` - Optional Software

`/opt` is used for optional or additional software packages.

For example:

```text
/opt/application
```

### Use Case

A third-party application that is not part of the normal Linux installation may be installed under:

```text
/opt
```

---

# 13. `/proc` - Process and Kernel Information

`/proc` is a virtual file system that provides information about running processes and the Linux kernel.

Examples:

```text
/proc/cpuinfo
/proc/meminfo
/proc/uptime
```

You can view CPU information:

```bash
cat /proc/cpuinfo
```

View memory information:

```bash
cat /proc/meminfo
```

### Important

`/proc` does not work like a normal directory containing files stored permanently on disk.

Its contents are generated by the Linux kernel.

---

# 14. `/root` - Root User's Home Directory

`/root` is the home directory of the **root user**.

It is different from:

```text
/
```

The difference is:

```text
/       → Root of the entire file system
/root   → Home directory of the root user
```

A normal user may not have permission to access `/root`.

Example:

```bash
sudo ls /root
```

---

# 15. `/run` - Runtime Information

`/run` contains temporary runtime information created after the system starts.

It may contain information about:

```text
Running services
Processes
Sockets
PID files
```

Example:

```bash
ls /run
```

The contents of `/run` are generally temporary and are recreated when the system boots.

---

# 16. `/sbin` - System Administration Commands

`/sbin` contains important system administration commands.

Examples may include commands related to:

```text
System management
Disk management
Networking
System startup
```

For example:

```bash
ls /sbin
```

> On many modern Linux distributions, `/sbin` may be a symbolic link to `/usr/sbin`.

---

# 17. `/srv` - Service Data

`/srv` is intended to contain data served by system services.

For example, a server application might store service-related data under:

```text
/srv
```

Possible examples:

```text
/srv/www
/srv/ftp
```

The exact usage depends on the server configuration.

---

# 18. `/sys` - Kernel and Hardware Information

`/sys` is another virtual file system provided by the Linux kernel.

It contains information about:

```text
Hardware devices
Kernel subsystems
Device drivers
```

Check it using:

```bash
ls /sys
```

For example:

```text
/sys/class
/sys/devices
/sys/block
```

Like `/proc`, `/sys` is not simply a collection of ordinary files stored on disk.

---

# 19. `/tmp` - Temporary Files

`/tmp` is used for temporary files created by applications and users.

Example:

```bash
cd /tmp
```

Create a temporary file:

```bash
touch test.txt
```

### Use Case

Applications can use `/tmp` when they need temporary storage.

> Files in `/tmp` may be removed automatically, especially during system startup or cleanup operations. Do not store important permanent files there.

---

# 20. `/usr` - User Programs and Data

`/usr` is one of the most important directories in Linux.

It contains many user-space programs, libraries, documentation, and other read-only/shareable data.

A simplified structure is:

```text
/usr
├── bin
├── lib
├── local
├── sbin
└── share
```

---

## `/usr/bin`

Contains many commonly used executable programs.

Examples:

```text
python
git
grep
vim
```

You can check:

```bash
ls /usr/bin
```

---

## `/usr/sbin`

Contains many system administration programs.

```bash
ls /usr/sbin
```

---

## `/usr/local`

Used for software installed locally by the system administrator rather than through the distribution's normal package management.

Example:

```text
/usr/local/bin
/usr/local/lib
```

---

## `/usr/share`

Contains architecture-independent shared data such as:

```text
Documentation
Manual pages
Icons
Application data
```

---

# 21. `/var` - Variable Data

`/var` contains data that changes frequently while the system is running.

Examples include:

```text
Logs
Caches
Spool files
Databases
Temporary application data
```

A common subdirectory is:

```text
/var/log
```

---

## `/var/log`

Contains system and application log files.

Example:

```bash
ls /var/log
```

You may find files related to:

```text
System logs
Authentication logs
Application logs
Kernel logs
```

### Use Case

Logs are useful for troubleshooting system problems.

For example:

```bash
sudo tail /var/log/syslog
```

---

# 22. Important Directory Comparison

| Directory | Purpose                                     |
| --------- | ------------------------------------------- |
| `/`       | Root of the entire Linux file system        |
| `/bin`    | Essential user commands                     |
| `/boot`   | Bootloader and kernel files                 |
| `/dev`    | Device files                                |
| `/etc`    | System configuration                        |
| `/home`   | Normal users' home directories              |
| `/lib`    | Essential system libraries                  |
| `/media`  | Removable media mount points                |
| `/mnt`    | Temporary mount points                      |
| `/opt`    | Optional/third-party software               |
| `/proc`   | Process and kernel information              |
| `/root`   | Root user's home directory                  |
| `/run`    | Runtime system information                  |
| `/sbin`   | System administration commands              |
| `/srv`    | Data for system services                    |
| `/sys`    | Kernel and hardware information             |
| `/tmp`    | Temporary files                             |
| `/usr`    | User programs and shared data               |
| `/var`    | Frequently changing system/application data |

---

# 23. Linux Directory Structure Diagram

A simplified Linux directory structure can be represented as:

```text
/
│
├── bin
│   └── Essential commands
│
├── boot
│   └── Boot files and kernel
│
├── dev
│   └── Device files
│
├── etc
│   └── Configuration files
│
├── home
│   ├── user1
│   └── user2
│
├── lib
│   └── System libraries
│
├── media
│   └── Removable devices
│
├── mnt
│   └── Temporary mount points
│
├── opt
│   └── Optional software
│
├── proc
│   └── Process information
│
├── root
│   └── Root user's home
│
├── run
│   └── Runtime information
│
├── sbin
│   └── System administration commands
│
├── srv
│   └── Service data
│
├── sys
│   └── Kernel and hardware information
│
├── tmp
│   └── Temporary files
│
├── usr
│   ├── bin
│   ├── lib
│   ├── local
│   ├── sbin
│   └── share
│
└── var
    ├── log
    ├── cache
    └── spool
```

---

# 24. Absolute Path vs Relative Path

Understanding paths is very important when working with the Linux directory structure.

## Absolute Path

An absolute path starts from the root directory `/`.

Example:

```text
/home/ubuntu/Documents/notes.txt
```

This tells Linux the complete location of the file.

You can access it using:

```bash
cat /home/ubuntu/Documents/notes.txt
```

---

## Relative Path

A relative path starts from your current directory.

For example, if you are currently in:

```text
/home/ubuntu
```

and the file is inside:

```text
/home/ubuntu/Documents/notes.txt
```

you can use:

```bash
cat Documents/notes.txt
```

---

# 25. Special Directory Symbols

Linux provides some special symbols for navigating directories.

| Symbol | Meaning                       |
| ------ | ----------------------------- |
| `/`    | Root directory                |
| `~`    | Current user's home directory |
| `.`    | Current directory             |
| `..`   | Parent directory              |

### Example

Go to your home directory:

```bash
cd ~
```

Go to the parent directory:

```bash
cd ..
```

Stay in the current directory:

```bash
cd .
```

Go to the root directory:

```bash
cd /
```

---

# 26. Example: Navigating the Linux File System

Suppose your directory structure is:

```text
/home/ubuntu/
├── Documents
│   └── notes.txt
├── Downloads
└── Projects
```

First go to your home directory:

```bash
cd ~
```

Check the contents:

```bash
ls
```

Go to Documents:

```bash
cd Documents
```

Check the file:

```bash
ls
```

Read the file:

```bash
cat notes.txt
```

Go back to the home directory:

```bash
cd ..
```

---

# 27. Important Commands for Directory Navigation

### Show current location

```bash
pwd
```

### List files

```bash
ls
```

### List hidden files

```bash
ls -la
```

### Go to a directory

```bash
cd Documents
```

### Go to parent directory

```bash
cd ..
```

### Go to home directory

```bash
cd ~
```

### Go to root directory

```bash
cd /
```

---

# 28. Hidden Files and Directories

Linux files and directories beginning with `.` are hidden by default.

For example:

```text
.bashrc
.profile
.ssh
```

To see hidden files:

```bash
ls -la
```

The `.ssh` directory is an example of a hidden directory.

It is usually located at:

```text
~/.ssh
```

For a user named `ubuntu`, this may be:

```text
/home/ubuntu/.ssh
```

---

# 29. Why Linux Uses This Structure

The Linux directory structure helps keep different types of files organized.

For example:

```text
Configuration files  → /etc
User files            → /home
Temporary files       → /tmp
System logs           → /var/log
Programs              → /usr/bin
Boot files            → /boot
Device information    → /dev
Kernel information    → /proc and /sys
```

This organization makes Linux easier to manage and maintain.

---

# 30. Beginner Summary

The most important directories to remember are:

```text
/          → Root of the file system
/home      → User files
/etc       → Configuration files
/var       → Logs and changing data
/usr       → Programs and shared data
/tmp       → Temporary files
/boot      → Boot files
/dev       → Device files
/proc      → Process/kernel information
/sys       → Hardware/kernel information
/root      → Root user's home
```

A simple way to remember them is:

```text
/       → Everything starts here
/home   → My files
/etc    → System settings
/usr    → Programs
/var    → Changing data and logs
/tmp    → Temporary files
/boot   → Starting Linux
/dev    → Devices
/proc   → Processes
/sys    → Hardware
/root   → Administrator's home
```

---

# Conclusion

The Linux directory structure is a hierarchical system where everything starts from the root directory `/`.

Each major directory has a specific purpose. Understanding directories such as `/home`, `/etc`, `/usr`, `/var`, `/tmp`, `/boot`, `/dev`, `/proc`, and `/sys` is essential for anyone learning Linux.

Once you understand this structure, commands such as `cd`, `ls`, `pwd`, `find`, `cat`, and `cp` become much easier to use because you understand where files and directories are located.

