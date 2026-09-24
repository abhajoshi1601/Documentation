# Linux File Permissions

## 1. Introduction

Linux is a multi-user operating system. Many users can work on the same computer and access the same files and directories.

To protect files from unauthorized access, Linux provides a **file permission system**.

File permissions control:

* Who can read a file
* Who can modify a file
* Who can execute a file
* Who can access a directory

Understanding permissions is important for both **Linux administration** and **cybersecurity**.

---

# 2. What Are File Permissions?

File permissions define what different users are allowed to do with a file or directory.

For example:

```text
-rw-r--r--
```

This tells us:

* The file owner can read and write.
* Members of the file's group can only read.
* Other users can only read.

---

# 3. Checking File Permissions

Use the `ls -l` command:

```bash
ls -l
```

Example output:

```text
-rw-r--r-- 1 user user 1200 Sep 24 notes.txt
```

The first part:

```text
-rw-r--r--
```

represents the file type and permissions.

---

# 4. Understanding the Permission Structure

Consider:

```text
-rwxr-xr--
```

It can be divided into four parts:

```text
-   rwx   r-x   r--
│    │     │     │
│    │     │     └── Others
│    │     └──────── Group
│    └────────────── Owner
└─────────────────── File type
```

### Permission Structure

| Section | Meaning            |
| ------- | ------------------ |
| `-`     | File type          |
| `rwx`   | Owner permissions  |
| `r-x`   | Group permissions  |
| `r--`   | Others permissions |

---

# 5. File Types

The first character in the permission string represents the file type.

| Symbol | Meaning          |
| ------ | ---------------- |
| `-`    | Regular file     |
| `d`    | Directory        |
| `l`    | Symbolic link    |
| `c`    | Character device |
| `b`    | Block device     |
| `s`    | Socket           |
| `p`    | Named pipe       |

### Example

```text
-rw-r--r--
```

The first character is:

```text
-
```

So it is a regular file.

Another example:

```text
drwxr-xr-x
```

The first character is:

```text
d
```

So it is a directory.

---

# 6. Three Basic Permissions

Linux mainly uses three permissions:

| Symbol | Permission | Meaning               |
| ------ | ---------- | --------------------- |
| `r`    | Read       | View/read the content |
| `w`    | Write      | Modify the content    |
| `x`    | Execute    | Execute the file      |

These permissions are represented by:

```text
r = Read
w = Write
x = Execute
```

---

# 7. Read Permission

Read permission is represented by:

```text
r
```

For a file, read permission allows a user to view its contents.

Example:

```bash
cat notes.txt
```

If you do not have read permission, you may get:

```text
Permission denied
```

For a directory, read permission allows a user to see the names of files inside the directory.

---

# 8. Write Permission

Write permission is represented by:

```text
w
```

For a file, write permission allows the user to modify its contents.

Example:

```bash
nano notes.txt
```

For a directory, write permission allows the user to create, delete, or rename files inside the directory, subject to the directory's other permissions.

---

# 9. Execute Permission

Execute permission is represented by:

```text
x
```

For an executable program or script, execute permission allows the user to run it.

Example:

```bash
./script.sh
```

For a directory, execute permission allows a user to access/traverse the directory.

---

# 10. Owner, Group, and Others

Linux divides users into three permission categories:

```text
Owner
Group
Others
```

### Owner

The owner is the user who owns the file.

### Group

A group is a collection of users.

### Others

Others means all users who are neither the owner nor members of the relevant group.

---

# 11. Example Permission

Consider:

```text
-rwxr-xr--
```

Break it down:

```text
-   rwx   r-x   r--
    │      │     │
    │      │     └── Others
    │      └──────── Group
    └─────────────── Owner
```

### Owner

```text
rwx
```

The owner can:

* Read
* Write
* Execute

### Group

```text
r-x
```

The group can:

* Read
* Execute

The group cannot:

* Write

### Others

```text
r--
```

Others can:

* Read

Others cannot:

* Write
* Execute

---

# 12. Permission Values

Linux also represents permissions using numbers.

| Permission    | Value |
| ------------- | ----: |
| Read (`r`)    |     4 |
| Write (`w`)   |     2 |
| Execute (`x`) |     1 |
| No permission |     0 |

These values are added together.

### Examples

```text
r-- = 4
-w- = 2
--x = 1
```

For multiple permissions:

```text
rw- = 4 + 2 = 6
r-x = 4 + 1 = 5
rwx = 4 + 2 + 1 = 7
```

---

# 13. Numeric Permission System

A permission such as:

```text
755
```

has three digits:

```text
7   5   5
│   │   │
│   │   └── Others
│   └────── Group
└────────── Owner
```

### 7

```text
4 + 2 + 1 = 7
```

Therefore:

```text
rwx
```

### 5

```text
4 + 1 = 5
```

Therefore:

```text
r-x
```

So:

```text
755
```

means:

```text
Owner  = rwx
Group  = r-x
Others = r-x
```

---

# 14. Common Permission Values

## 755

```text
755 = rwxr-xr-x
```

Owner:

```text
rwx
```

Group:

```text
r-x
```

Others:

```text
r-x
```

Commonly used for executable files and directories.

---

## 644

```text
644 = rw-r--r--
```

Owner:

```text
rw-
```

Group:

```text
r--
```

Others:

```text
r--
```

Commonly used for regular files.

---

## 700

```text
700 = rwx------
```

Only the owner has access.

Useful for private directories and files.

---

## 600

```text
600 = rw-------
```

Only the owner can read and write.

Useful for sensitive files.

---

## 777

```text
777 = rwxrwxrwx
```

Owner:

```text
rwx
```

Group:

```text
rwx
```

Others:

```text
rwx
```

Everyone has full permissions.

**Avoid using `777` unless there is a specific reason.** It can unnecessarily expose files to modification or execution by other users.

---

# 15. The `chmod` Command

`chmod` means:

```text
Change Mode
```

It is used to change file or directory permissions.

Basic syntax:

```bash
chmod permissions filename
```

Example:

```bash
chmod 644 notes.txt
```

This changes `notes.txt` to:

```text
rw-r--r--
```

---

# 16. Using `chmod` with Numbers

Example:

```bash
chmod 755 script.sh
```

This gives:

```text
Owner  = rwx
Group  = r-x
Others = r-x
```

Another example:

```bash
chmod 600 secret.txt
```

This gives:

```text
Owner  = rw-
Group  = ---
Others = ---
```

---

# 17. Symbolic Permissions

Permissions can also be changed using letters.

Linux uses:

```text
u = user/owner
g = group
o = others
a = all
```

Operators:

```text
+ = add permission
- = remove permission
= = set permission
```

### Add Execute Permission

```bash
chmod u+x script.sh
```

This gives the owner execute permission.

### Remove Write Permission

```bash
chmod g-w notes.txt
```

This removes write permission from the group.

### Give Read Permission to Others

```bash
chmod o+r notes.txt
```

### Give Execute Permission to Everyone

```bash
chmod a+x script.sh
```

---

# 18. Checking Permissions After `chmod`

Use:

```bash
ls -l
```

Example:

```bash
chmod 600 secret.txt
ls -l secret.txt
```

Output may look like:

```text
-rw------- 1 user user 500 Sep 24 secret.txt
```

The permission is:

```text
rw-------
```

Only the owner has read and write permissions.

---

# 19. Changing File Ownership

Linux also allows you to change the owner of a file.

The command is:

```bash
chown
```

`chown` means:

```text
Change Owner
```

Basic syntax:

```bash
sudo chown username filename
```

Example:

```bash
sudo chown abha notes.txt
```

This changes the owner of `notes.txt` to `abha`.

---

# 20. Changing Owner and Group

You can change both the owner and group:

```bash
sudo chown username:groupname filename
```

Example:

```bash
sudo chown abha:developers project.txt
```

Now:

```text
Owner = abha
Group = developers
```

---

# 21. Changing Group Ownership

The `chgrp` command changes the group associated with a file.

Syntax:

```bash
chgrp groupname filename
```

Example:

```bash
sudo chgrp developers project.txt
```

---

# 22. Using `sudo`

`sudo` means:

```text
SuperUser Do
```

It allows an authorized user to execute a command with elevated privileges.

Example:

```bash
sudo chown abha notes.txt
```

Some operations require administrator privileges.

Be careful when using:

```bash
sudo
```

because commands executed with elevated privileges can make important system changes.

---

# 23. File Permissions vs Directory Permissions

Permissions behave slightly differently for files and directories.

## File

| Permission | Meaning              |
| ---------- | -------------------- |
| `r`        | Read file contents   |
| `w`        | Modify file contents |
| `x`        | Execute the file     |

## Directory

| Permission | Meaning                       |
| ---------- | ----------------------------- |
| `r`        | List directory contents       |
| `w`        | Create/delete/rename entries  |
| `x`        | Access/traverse the directory |

Example:

```text
drwxr-xr-x
```

The `d` tells us that it is a directory.

---

# 24. Recursive Permissions

Sometimes you want to change permissions for a directory and everything inside it.

Use:

```bash
chmod -R 755 myfolder
```

Here:

```text
-R
```

means:

```text
Recursive
```

It applies the change to the directory and its contents.

### Important

Be careful with:

```bash
chmod -R
```

because an incorrect recursive permission change can affect many files.

---

# 25. Checking Ownership

Use:

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 abha developers 1200 Sep 24 project.txt
```

Here:

```text
Owner = abha
Group = developers
```

---

# 26. Permission Denied Error

You may see:

```text
Permission denied
```

This usually means that your current user does not have the required permission.

Example:

```bash
./script.sh
```

Output:

```text
Permission denied
```

You may need to add execute permission:

```bash
chmod +x script.sh
```

Then:

```bash
./script.sh
```

---

# 27. Practical Example

Create a file:

```bash
touch test.txt
```

Check its permissions:

```bash
ls -l test.txt
```

Change permissions:

```bash
chmod 600 test.txt
```

Check again:

```bash
ls -l test.txt
```

You should see permissions similar to:

```text
-rw------- 
```

This means only the owner can read and write the file.

---

# 28. Practical Example with a Script

Create a script:

```bash
nano hello.sh
```

Add:

```bash
#!/bin/bash

echo "Hello Linux"
```

Initially, the script may not have execute permission.

Give execute permission:

```bash
chmod +x hello.sh
```

Run it:

```bash
./hello.sh
```

Output:

```text
Hello Linux
```

---

# 29. Useful Permission Commands

| Command  | Purpose                                    |
| -------- | ------------------------------------------ |
| `ls -l`  | View permissions                           |
| `chmod`  | Change permissions                         |
| `chown`  | Change owner                               |
| `chgrp`  | Change group                               |
| `sudo`   | Execute with elevated privileges           |
| `id`     | Display current user and group information |
| `whoami` | Display current username                   |

---

# 30. Important Permission Examples

| Numeric | Symbolic    | Meaning                         |
| ------: | ----------- | ------------------------------- |
|   `777` | `rwxrwxrwx` | Everyone has full permissions   |
|   `755` | `rwxr-xr-x` | Owner full, others read/execute |
|   `700` | `rwx------` | Only owner has full access      |
|   `644` | `rw-r--r--` | Owner read/write, others read   |
|   `600` | `rw-------` | Only owner read/write           |
|   `444` | `r--r--r--` | Everyone can only read          |
|   `400` | `r--------` | Only owner can read             |

---

# 31. File Permission Security

Correct permissions are important for system security.

### Good practices

* Give users only the permissions they need.
* Avoid unnecessary `777` permissions.
* Use `600` for highly private files when appropriate.
* Use `700` for private directories when appropriate.
* Check ownership of important files.
* Be careful with recursive permission changes.
* Avoid using `sudo` unnecessarily.
* Regularly check permissions on sensitive files.

---

# 32. Principle of Least Privilege

A major cybersecurity principle is:

> Give users only the permissions they actually need.

For example, if a user only needs to read a file, they should not automatically receive write and execute permissions.

Instead of:

```text
rwx
```

use:

```text
r--
```

when read-only access is sufficient.

This reduces the risk of accidental or unauthorized changes.

---

# 33. Quick Permission Calculation

Remember:

```text
Read    = 4
Write   = 2
Execute = 1
```

### Example 1

```text
rwx
```

Calculation:

```text
4 + 2 + 1 = 7
```

### Example 2

```text
rw-
```

Calculation:

```text
4 + 2 = 6
```

### Example 3

```text
r-x
```

Calculation:

```text
4 + 1 = 5
```

### Example 4

```text
r--
```

Calculation:

```text
4 = 4
```

Therefore:

```text
rwxr-xr--
```

becomes:

```text
754
```

---

# 34. Quick Revision

```text
r = Read    = 4
w = Write   = 2
x = Execute = 1
```

User categories:

```text
u = Owner
g = Group
o = Others
a = All
```

Common commands:

```bash
ls -l
chmod
chown
chgrp
sudo
```

Common permissions:

```text
755 = rwxr-xr-x
644 = rw-r--r--
700 = rwx------
600 = rw-------
```

---

# 35. Practice Questions

## Question 1

What does this mean?

```text
-rw-r--r--
```

### Answer

```text
Owner  = Read + Write
Group  = Read
Others = Read
```

Numeric form:

```text
644
```

---

## Question 2

What does `755` mean?

### Answer

```text
Owner  = rwx
Group  = r-x
Others = r-x
```

---

## Question 3

How do you make a script executable?

### Answer

```bash
chmod +x script.sh
```

---

## Question 4

How do you check permissions?

### Answer

```bash
ls -l
```

---

## Question 5

How do you change a file to permission `600`?

### Answer

```bash
```

