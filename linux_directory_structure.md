# Linux Directory Structure

## 1. Introduction

Linux uses a hierarchical directory structure to organize files and folders.

Unlike Windows, where drives are represented using letters such as `C:` and `D:`, Linux starts its entire file system from a single root directory represented by:

```bash
/
```

Everything in Linux exists inside the root `/` directory.

---

## 2. Basic Linux Directory Structure

A typical Linux system contains directories such as:

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

The `/` directory is the top-level directory of the Linux file system.

All other directories and files are located inside the root directory.

### Example

```bash
cd /
ls
```

The `ls` command displays the directories and files inside `/`.

---

# 4. `/bin` – Essential User Commands

The `/bin` directory contains essential commands that are available to normal users.

Some common commands include:

```text
ls
cp
mv
rm
cat
mkdir
```

### Example

```bash
ls /bin
```

This displays commands stored in the `/bin` directory.

> On many modern Linux distributions, `/bin` is a symbolic link to `/usr/bin`.

---

# 5. `/boot` – Boot Files

The `/boot` directory contains files required to start the Linux operating system.

It may contain:

```text
Linux Kernel
GRUB bootloader files
Initial RAM filesystem
```

### Example

```bash
ls /boot
```

### Important

Do not delete or modify files in `/boot` unless you know exactly what you are doing.

---

# 6. `/dev` – Device Files

The `/dev` directory contains special files that represent hardware and other devices.

Examples include:

```text
/dev/sda
/dev/sdb
/dev/tty
/dev/null
```

For example:

```bash
ls /dev
```

Linux treats many hardware devices like files.

---

# 7. `/etc` – Configuration Files

The `/etc` directory contains system-wide configuration files.

Examples:

```text
/etc/hosts
/etc/passwd
/etc/hostname
/etc/fstab
```

### Example

```bash
cat /etc/hostname
```

This displays the hostname of the system.

Another example:

```bash
cat /etc/hosts
```

This displays the local hostname and IP address mappings.

---

# 8. `/home` – User Home Directories

The `/home` directory contains personal directories for normal users.

Example:

```text
/home
├── user1
├── user2
└── user3
```

If your username is `user1601`, your home directory may be:

```text
/home/user1601
```

You can go to your home directory using:

```bash
cd ~
```

or:

```bash
cd /home/user1601
```

The `~` symbol represents the current user's home directory.

---

# 9. `/lib` – Shared Libraries

The `/lib` directory contains important shared libraries required by system programs.

Libraries are files that provide functionality used by other programs.

Examples may include:

```text
/lib
/lib64
```

On modern Linux systems, `/lib` may also be linked to directories under `/usr`.

---

# 10. `/media` – Removable Media

The `/media` directory is commonly used for automatically mounted removable devices.

Examples:

```text
USB drive
CD/DVD
External storage
```

For example:

```text
/media/user/USB
```

When you connect a USB drive, Linux may automatically mount it under `/media`.

---

# 11. `/mnt` – Temporary Mount Point

The `/mnt` directory is commonly used for temporarily mounting file systems.

For example:

```bash
sudo mount /dev/sdb1 /mnt
```

This mounts a partition at `/mnt`.

---

# 12. `/opt` – Optional Software

The `/opt` directory is used for optional or additional software packages.

For example:

```text
/opt/application
/opt/software
```

Third-party software can sometimes be installed inside `/opt`.

---

# 13. `/proc` – Process Information

The `/proc` directory is a virtual file system that provides information about running processes and the Linux kernel.

For example:

```bash
ls /proc
```

You may see directories containing numbers such as:

```text
1234
1456
2001
```

These numbers generally represent process IDs (PIDs).

### Example

```bash
cat /proc/cpuinfo
```

This displays information about the CPU.

Another example:

```bash
cat /proc/meminfo
```

This displays information about system memory.

---

# 14. `/root` – Root User's Home Directory

The `/root` directory is the home directory of the root user.

It is different from the `/` root directory.

### Important Difference

```text
/       → Root of the entire file system
/root   → Home directory of the root user
```

---

# 15. `/run` – Runtime Data

The `/run` directory contains temporary runtime information created after the system starts.

It can contain information related to:

```text
Running processes
System services
User sessions
Sockets
PID files
```

The contents of `/run` are generally temporary and are recreated when the system boots.

---

# 16. `/sbin` – System Administration Commands

The `/sbin` directory traditionally contains commands mainly used for system administration.

Examples include commands related to:

```text
System configuration
Disk management
Networking
System maintenance
```

On many modern distributions, `/sbin` is linked into `/usr/sbin`.

---

# 17. `/srv` – Service Data

The `/srv` directory is intended for data served by system services.

For example, a server application may store service-related data in:

```text
/srv
```

It is commonly associated with server systems.

---

# 18. `/sys` – Kernel and Hardware Information

The `/sys` directory is another virtual file system used by the Linux kernel.

It provides information about:

```text
Hardware devices
Kernel components
Device drivers
System devices
```

### Example

```bash
ls /sys
```

You may see directories such as:

```text
block
bus
class
devices
firmware
```

---

# 19. `/tmp` – Temporary Files

The `/tmp` directory is used for temporary files created by applications and users.

Example:

```bash
cd /tmp
```

You can create a temporary file:

```bash
touch test.txt
```

Then check it:

```bash
ls
```

Temporary files may be automatically deleted depending on the Linux distribution and its configuration.

---

# 20. `/usr` – User Programs and Data

The `/usr` directory contains a large portion of the operating system's user-space programs, libraries, documentation, and other shared data.

Important subdirectories include:

```text
/usr/bin
/usr/sbin
/usr/lib
/usr/share
/usr/local
```

### `/usr/bin`

Contains many user commands and applications.

Example:

```bash
ls /usr/bin
```

### `/usr/sbin`

Contains many system administration programs.

### `/usr/share`

Contains architecture-independent data such as:

```text
Documentation
Man pages
Icons
Application data
```

### `/usr/local`

Commonly used for software installed locally by the system administrator.

---

# 21. `/var` – Variable Data

The `/var` directory contains data that changes frequently while the system is running.

Examples include:

```text
Logs
Caches
Spool files
Databases
Application data
```

Important subdirectories include:

```text
/var/log
/var/cache
/var/tmp
```

---

## 22. `/var/log` – System Logs

The `/var/log` directory contains system and application log files.

Example:

```bash
ls /var/log
```

You may find files such as:

```text
syslog
auth.log
kern.log
```

Logs are useful for troubleshooting and security monitoring.

---

# 23. `/var/cache` – Cached Data

The `/var/cache` directory contains cached data created by applications and system services.

For example:

```text
Package manager cache
Application cache
```

Cache files are usually stored to improve performance.

---

# 24. `/var/tmp` – Temporary Data

`/var/tmp` is used for temporary files that may need to remain available for longer than files in `/tmp`.

Difference:

```text
/tmp      → Short-term temporary files
/var/tmp  → Temporary files that may persist longer
```

---

# 25. Important Directories at a Glance

| Directory | Purpose                         |
| --------- | ------------------------------- |
| `/`       | Root of the entire file system  |
| `/bin`    | Essential user commands         |
| `/boot`   | Boot and kernel files           |
| `/dev`    | Device files                    |
| `/etc`    | System configuration files      |
| `/home`   | Users' personal directories     |
| `/lib`    | Essential shared libraries      |
| `/media`  | Removable media mount points    |
| `/mnt`    | Temporary mount point           |
| `/opt`    | Optional/third-party software   |
| `/proc`   | Process and kernel information  |
| `/root`   | Root user's home directory      |
| `/run`    | Runtime system information      |
| `/sbin`   | System administration commands  |
| `/srv`    | Data for system services        |
| `/sys`    | Kernel and hardware information |
| `/tmp`    | Temporary files                 |
| `/usr`    | User programs and shared data   |
| `/var`    | Frequently changing data        |

---

# 26. Important Linux Path Concepts

## Absolute Path

An absolute path starts from the root directory `/`.

Example:

```bash
/home/user1601/Documents
```

It tells Linux the complete location of a file or directory.

---

## Relative Path

A relative path starts from the current directory.

Example:

```bash
Documents/project
```

If the current directory is:

```text
/home/user1601
```

then:

```text
Documents/project
```

means:

```text
/home/user1601/Documents/project
```

---

# 27. Special Directory Symbols

Linux provides some special symbols for navigating directories.

| Symbol | Meaning                       |
| ------ | ----------------------------- |
| `/`    | Root directory                |
| `~`    | Current user's home directory |
| `.`    | Current directory             |
| `..`   | Parent directory              |

### Example

Go to home directory:

```bash
cd ~
```

Show current directory:

```bash
pwd
```

Go to parent directory:

```bash
cd ..
```

Go to current directory:

```bash
cd .
```

---

# 28. Useful Commands for Exploring Directories

## `pwd`

Shows the current working directory.

```bash
pwd
```

Example output:

```text
/home/user1601
```

---

## `ls`

Lists files and directories.

```bash
ls
```

Detailed listing:

```bash
ls -l
```

Show hidden files:

```bash
ls -a
```

---

## `cd`

Changes the current directory.

```bash
cd /home
```

Go back to the previous directory:

```bash
cd ..
```

---

## `mkdir`

Creates a new directory.

```bash
mkdir myfolder
```

---

## `rmdir`

Removes an empty directory.

```bash
rmdir myfolder
```

---

## `tree`

Displays directories in a tree-like structure.

If `tree` is installed:

```bash
tree
```

Example:

```text
.
├── Documents
│   ├── notes.txt
│   └── project
├── Downloads
└── Pictures
```

---

# 29. Linux Directory Structure Example

Consider the following structure:

```text
/
├── home
│   └── user1601
│       ├── Documents
│       ├── Downloads
│       ├── Pictures
│       └── Projects
│
├── etc
│   ├── hosts
│   └── hostname
│
├── var
│   └── log
│
├── usr
│   ├── bin
│   ├── lib
│   └── share
│
└── tmp
```

Here:

* `/home/user1601` contains the user's personal files.
* `/etc` contains configuration files.
* `/var/log` contains logs.
* `/usr` contains programs and shared data.
* `/tmp` contains temporary files.

---

# 30. Linux Directory Structure vs Windows

| Linux                         | Windows                                                                       |
| ----------------------------- | ----------------------------------------------------------------------------- |
| Uses `/` as the root          | Uses drive letters such as `C:`                                               |
| `/home` stores user files     | `C:\Users` stores user files                                                  |
| `/etc` stores configuration   | Configuration is commonly stored in the Registry and application/system files |
| `/tmp` stores temporary files | `%TEMP%` is commonly used                                                     |
| `/var/log` stores many logs   | Logs are commonly accessed through Event Viewer and log files                 |
| Uses `/` in paths             | Uses `\` in traditional Windows paths                                         |

---

# 31. Why Linux Directory Structure Is Important

Understanding the Linux directory structure helps you:

1. Navigate the Linux file system.
2. Find configuration files.
3. Locate system logs.
4. Manage user files.
5. Troubleshoot system problems.
6. Understand where applications store their files.
7. Work with Linux servers.
8. Manage permissions and system resources.
9. Understand cybersecurity environments.
10. Use the terminal more effectively.

---

# 32. Basic Practice Commands

You can practice the directory structure using these commands:

```bash
pwd
```

```bash
ls
```

```bash
cd /
```

```bash
ls
```

```bash
cd /home
```

```bash
ls
```

```bash
cd ~
```

```bash
pwd
```

```bash
cd ..
```

```bash
ls -la
```

---

# 33. Quick Revision

The most important directories to remember are:

```text
/       → Root
/boot   → Boot files
/dev    → Devices
/etc    → Configuration
/home   → User files
/lib    → Libraries
/media  → Removable media
/mnt    → Temporary mounts
/opt    → Optional software
/proc   → Process information
/root   → Root user's home
/run    → Runtime information
/sbin   → System administration commands
/srv    → Service data
/sys    → Kernel and hardware information
/tmp    → Temporary files
/usr    → User programs and data
/var    → Variable data and logs
```

---

# 34. Conclusion

The Linux directory structure provides an organized way to store system files, user files, configuration files, applications, logs, temporary files, and hardware-related information.

The most important directories for beginners are:

```text
/
├── /home
├── /etc
├── /usr
├── /var
├── /tmp
├── /boot
├── /dev
└── /root
```

Learning these directories is an important first step toward working comfortably with Linux, system administration, servers, networking, and cybersecurity.

