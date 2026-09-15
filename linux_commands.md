# Top 30 Basic Linux Commands

## Introduction

Linux commands are instructions that are entered into the Terminal to perform different tasks. They are used to manage files and folders, navigate through the system, check system information, manage processes, and perform many other operations.

This document covers 30 basic Linux commands that are useful for beginners.

---

## 1. `pwd`

### Use Case

`pwd` stands for **Print Working Directory**. It shows the current directory you are working in.

### Syntax

```bash
pwd
```

### Example

```bash
pwd
```

### Example Output

```text
/home/ubuntu
```

---

## 2. `ls`

### Use Case

`ls` is used to list files and directories in the current location.

### Syntax

```bash
ls
```

### Example

```bash
ls
```

To show detailed information:

```bash
ls -l
```

To show hidden files:

```bash
ls -la
```

---

## 3. `cd`

### Use Case

`cd` stands for **Change Directory**. It is used to move from one directory to another.

### Syntax

```bash
cd directory_name
```

### Example

```bash
cd Documents
```

Go back to the parent directory:

```bash
cd ..
```

Go to the home directory:

```bash
cd ~
```

---

## 4. `mkdir`

### Use Case

`mkdir` stands for **Make Directory**. It is used to create a new folder.

### Syntax

```bash
mkdir directory_name
```

### Example

```bash
mkdir projects
```

Create multiple directories:

```bash
mkdir project1 project2 project3
```

---

## 5. `rmdir`

### Use Case

`rmdir` is used to remove an empty directory.

### Syntax

```bash
rmdir directory_name
```

### Example

```bash
rmdir old_folder
```

> Note: `rmdir` works only when the directory is empty.

---

## 6. `touch`

### Use Case

`touch` is commonly used to create a new empty file.

### Syntax

```bash
touch filename
```

### Example

```bash
touch notes.txt
```

Create multiple files:

```bash
touch file1.txt file2.txt file3.txt
```

---

## 7. `cat`

### Use Case

`cat` is used to display the contents of a file.

### Syntax

```bash
cat filename
```

### Example

```bash
cat notes.txt
```

It can also be used to create a simple file:

```bash
cat > notes.txt
```

Type your text and press `Ctrl + D` to save.

---

## 8. `cp`

### Use Case

`cp` stands for **Copy**. It is used to copy files or directories.

### Syntax

```bash
cp source destination
```

### Example

```bash
cp notes.txt backup.txt
```

Copy a file into another directory:

```bash
cp notes.txt Documents/
```

---

## 9. `mv`

### Use Case

`mv` stands for **Move**. It is used to move or rename files and directories.

### Example: Move a file

```bash
mv notes.txt Documents/
```

### Example: Rename a file

```bash
mv old.txt new.txt
```

---

## 10. `rm`

### Use Case

`rm` is used to remove files or directories.

### Syntax

```bash
rm filename
```

### Example

```bash
rm oldfile.txt
```

Remove a directory and its contents:

```bash
rm -r old_folder
```

> Be careful with `rm` because deleted files may not go to the Trash.

---

## 11. `echo`

### Use Case

`echo` is used to display text or variable values in the terminal.

### Example

```bash
echo "Hello Linux"
```

Output:

```text
Hello Linux
```

It can also be used to write text into a file:

```bash
echo "Linux is easy" > notes.txt
```

---

## 12. `clear`

### Use Case

`clear` clears the terminal screen.

### Example

```bash
clear
```

This does not delete files or commands. It only clears the visible terminal screen.

---

## 13. `man`

### Use Case

`man` stands for **Manual**. It displays documentation for Linux commands.

### Syntax

```bash
man command
```

### Example

```bash
man ls
```

To exit the manual page, press:

```text
q
```

---

## 14. `sudo`

### Use Case

`sudo` allows a permitted user to run commands with administrator privileges.

### Syntax

```bash
sudo command
```

### Example

```bash
sudo apt update
```

Another example:

```bash
sudo systemctl restart ssh
```

> `sudo` should be used carefully because administrator commands can modify important system files.

---

## 15. `apt`

### Use Case

`apt` is the package management command commonly used on Ubuntu and other Debian-based Linux distributions.

### Update package information

```bash
sudo apt update
```

### Install a package

```bash
sudo apt install git
```

### Remove a package

```bash
sudo apt remove git
```

---

## 16. `whoami`

### Use Case

`whoami` displays the username of the currently logged-in user.

### Example

```bash
whoami
```

### Example Output

```text
ubuntu
```

---

## 17. `id`

### Use Case

`id` displays information about the current user, including user ID and group IDs.

### Example

```bash
id
```

### Example Output

```text
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),27(sudo)
```

---

## 18. `history`

### Use Case

`history` displays previously executed commands.

### Example

```bash
history
```

You may see:

```text
1  pwd
2  ls
3  cd Documents
4  mkdir project
```

You can run a previous command using its history number:

```bash
!3
```

---

## 19. `find`

### Use Case

`find` is used to search for files and directories.

### Syntax

```bash
find location -name "filename"
```

### Example

```bash
find . -name "notes.txt"
```

Here:

* `.` means the current directory.
* `-name` searches by filename.

---

## 20. `grep`

### Use Case

`grep` searches for specific text inside files or command output.

### Syntax

```bash
grep "text" filename
```

### Example

```bash
grep "password" notes.txt
```

Search without considering uppercase/lowercase:

```bash
grep -i "password" notes.txt
```

---

## 21. `head`

### Use Case

`head` displays the beginning of a file.

### Example

```bash
head notes.txt
```

Display the first 5 lines:

```bash
head -n 5 notes.txt
```

---

## 22. `tail`

### Use Case

`tail` displays the last part of a file.

### Example

```bash
tail notes.txt
```

Display the last 5 lines:

```bash
tail -n 5 notes.txt
```

It is also useful for monitoring log files:

```bash
tail -f /var/log/syslog
```

Press `Ctrl + C` to stop monitoring.

---

## 23. `less`

### Use Case

`less` is used to view large files one screen at a time.

### Example

```bash
less largefile.txt
```

Useful keys:

```text
Space  → Next page
b      → Previous page
q      → Quit
```

---

## 24. `chmod`

### Use Case

`chmod` is used to change file and directory permissions.

### Syntax

```bash
chmod permissions filename
```

### Example

Make a script executable:

```bash
chmod +x script.sh
```

Now it can be executed using:

```bash
./script.sh
```

---

## 25. `chown`

### Use Case

`chown` is used to change the owner of a file or directory.

### Syntax

```bash
sudo chown user:group filename
```

### Example

```bash
sudo chown ubuntu:ubuntu notes.txt
```

This changes the owner and group of `notes.txt` to `ubuntu`.

---

## 26. `ps`

### Use Case

`ps` displays information about currently running processes.

### Example

```bash
ps
```

To see more detailed processes:

```bash
ps aux
```

This is useful for checking which programs are currently running.

---

## 27. `top`

### Use Case

`top` provides a real-time view of running processes and system resource usage.

### Example

```bash
top
```

It displays information such as:

* CPU usage
* Memory usage
* Running processes
* Process IDs

Press:

```text
q
```

to exit.

---

## 28. `df`

### Use Case

`df` displays information about available and used disk space.

### Example

```bash
df -h
```

The `-h` option displays the information in a human-readable format such as GB and MB.

Example:

```text
Filesystem      Size  Used Avail Use%
/dev/sda1        50G   20G   28G  42%
```

---

## 29. `du`

### Use Case

`du` shows how much disk space files and directories are using.

### Example

```bash
du -sh Documents
```

Example output:

```text
500M    Documents
```

Here, `-s` shows the total and `-h` makes the output human-readable.

---

## 30. `ip`

### Use Case

`ip` is used to view and manage network information in Linux.

### Example

To view IP addresses:

```bash
ip addr
```

A shorter command:

```bash
ip a
```

To view network interfaces:

```bash
ip link
```

---

# Quick Reference Table

| No. | Command   | Main Use                     |
| --: | --------- | ---------------------------- |
|   1 | `pwd`     | Show current directory       |
|   2 | `ls`      | List files and directories   |
|   3 | `cd`      | Change directory             |
|   4 | `mkdir`   | Create directory             |
|   5 | `rmdir`   | Remove empty directory       |
|   6 | `touch`   | Create a file                |
|   7 | `cat`     | Display file contents        |
|   8 | `cp`      | Copy files/directories       |
|   9 | `mv`      | Move or rename files         |
|  10 | `rm`      | Remove files/directories     |
|  11 | `echo`    | Display or write text        |
|  12 | `clear`   | Clear terminal               |
|  13 | `man`     | View command manual          |
|  14 | `sudo`    | Run command as administrator |
|  15 | `apt`     | Manage software packages     |
|  16 | `whoami`  | Show current username        |
|  17 | `id`      | Show user/group information  |
|  18 | `history` | Show previous commands       |
|  19 | `find`    | Search files/directories     |
|  20 | `grep`    | Search text                  |
|  21 | `head`    | Show beginning of file       |
|  22 | `tail`    | Show end of file             |
|  23 | `less`    | Read large files             |
|  24 | `chmod`   | Change permissions           |
|  25 | `chown`   | Change file ownership        |
|  26 | `ps`      | View processes               |
|  27 | `top`     | Monitor processes/resources  |
|  28 | `df`      | Check disk space             |
|  29 | `du`      | Check directory/file size    |
|  30 | `ip`      | Check network information    |

---

# Basic Linux Practice

The following commands can be practiced in order:

```bash
pwd
ls
mkdir linux-practice
cd linux-practice
touch notes.txt
echo "Linux is easy to learn" > notes.txt
cat notes.txt
cp notes.txt backup.txt
mv backup.txt backup_notes.txt
ls -l
grep "Linux" notes.txt
du -sh .
cd ..
rm -r linux-practice
```

---

# Important Safety Tips

Before running Linux commands, remember:

* Be careful when using `sudo`.
* Double-check paths before using `rm`.
* Avoid using `rm -rf` unless you completely understand what it will delete.
* Do not modify system files without understanding the command.
* Practice file operations inside a test directory first.
* Use `man command` whenever you are unsure about a command.

---

# Conclusion

Learning basic Linux commands is an important first step for working with Linux systems. These 30 commands cover common tasks such as navigating directories, creating and managing files, searching data, managing permissions, monitoring processes, checking disk space, and viewing network information.

Once these commands are comfortable to use, the next step is to learn Linux permissions, users and groups, SSH, networking commands, package management, and Bash scripting.

