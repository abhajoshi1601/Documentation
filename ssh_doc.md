# SSH Setup on Local Ubuntu Machine

## 1. Introduction

SSH stands for Secure Shell. It is a secure protocol used to connect to another computer over a network.

In Ubuntu, SSH can be used to:

* Connect to another Linux machine
* Access a remote server
* Transfer files securely
* Authenticate using SSH keys
* Connect GitHub with SSH

This documentation explains how to create and configure the `.ssh` directory and SSH key on a local Ubuntu machine.

---

# 2. Requirements

Before starting, make sure you have:

* Ubuntu installed
* Terminal access
* Internet connection
* A user account with `sudo` permission

---

# 3. Check SSH Installation

First, open the Ubuntu Terminal.

Check whether SSH is installed:

```bash
ssh -V
```

Example output:

```text
OpenSSH_9.x
```

If SSH is installed, the version will be displayed.

---

# 4. Install OpenSSH

If SSH is not installed, update the Ubuntu package list:

```bash
sudo apt update
```

Then install OpenSSH:

```bash
sudo apt install openssh-client
```

If you want your Ubuntu machine to accept incoming SSH connections, also install the SSH server:

```bash
sudo apt install openssh-server
```

---

# 5. Check SSH Server Status

After installing the SSH server, check its status:

```bash
sudo systemctl status ssh
```

If everything is working correctly, you should see:

```text
Active: active (running)
```

If the service is not running, start it using:

```bash
sudo systemctl start ssh
```

To automatically start SSH when Ubuntu boots:

```bash
sudo systemctl enable ssh
```

---

# 6. Create the `.ssh` Directory

The `.ssh` directory is normally located inside the user's home directory.

Go to your home directory:

```bash
cd ~
```

Check whether the `.ssh` directory already exists:

```bash
ls -la
```

If `.ssh` does not exist, create it:

```bash
mkdir -p ~/.ssh
```

Check it:

```bash
ls -la ~/.ssh
```

---

# 7. Set `.ssh` Directory Permissions

For security, the `.ssh` directory should only be accessible by the current user.

Run:

```bash
chmod 700 ~/.ssh
```

Check the permissions:

```bash
ls -ld ~/.ssh
```

The permissions should look similar to:

```text
drwx------ ... .ssh
```

---

# 8. Generate an SSH Key

The recommended SSH key type is Ed25519.

Run:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Example:

```bash
ssh-keygen -t ed25519 -C "abha@example.com"
```

The terminal will ask:

```text
Enter file in which to save the key:
```

Press:

```text
Enter
```

This will use the default location:

```text
~/.ssh/id_ed25519
```

Next, it will ask for a passphrase:

```text
Enter passphrase:
```

You can enter a secure passphrase.

For a simple local setup, you can also press `Enter` to leave it empty.

---

# 9. SSH Key Files

After generating the key, two important files will be created:

```text
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
```

### Private Key

```text
id_ed25519
```

This is your private SSH key.

Never share this file with anyone.

### Public Key

```text
id_ed25519.pub
```

This is your public SSH key.

The public key can be added to services such as GitHub or to the `authorized_keys` file of another Linux machine.

---

# 10. Check the Generated Keys

Run:

```bash
ls -la ~/.ssh
```

You should see something similar to:

```text
id_ed25519
id_ed25519.pub
```

You may also see other SSH-related files if you have used SSH previously.

---

# 11. Start the SSH Agent

The SSH agent temporarily stores your private key so that you do not have to enter the passphrase repeatedly.

Start the SSH agent:

```bash
eval "$(ssh-agent -s)"
```

You should get output similar to:

```text
Agent pid 1234
```

---

# 12. Add the SSH Key to the Agent

Run:

```bash
ssh-add ~/.ssh/id_ed25519
```

If the key has a passphrase, Ubuntu will ask you to enter it.

---

# 13. Display the Public Key

To display your public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Example:

```text
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAA... abha@example.com
```

Copy the complete line if you need to add the key to GitHub or another server.

---

# 14. SSH Configuration File

The `.ssh` directory can also contain a configuration file named:

```text
~/.ssh/config
```

Create it using:

```bash
touch ~/.ssh/config
```

Set its permissions:

```bash
chmod 600 ~/.ssh/config
```

A basic SSH configuration can look like:

```text
Host myserver
    HostName 192.168.1.100
    User username
    IdentityFile ~/.ssh/id_ed25519
```

Now instead of typing:

```bash
ssh username@192.168.1.100
```

you can use:

```bash
ssh myserver
```

---

# 15. Connect to Another Ubuntu Machine

Suppose the remote Ubuntu machine has:

```text
IP Address: 192.168.1.100
Username: ubuntu
```

You can connect using:

```bash
ssh ubuntu@192.168.1.100
```

The first time you connect, you may see:

```text
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Type:

```text
yes
```

Then enter the remote user's password.

---

# 16. Passwordless SSH Login

To use SSH keys instead of entering the remote password every time, copy your public key to the remote Ubuntu machine.

Run:

```bash
ssh-copy-id username@192.168.1.100
```

Example:

```bash
ssh-copy-id ubuntu@192.168.1.100
```

After this, try:

```bash
ssh ubuntu@192.168.1.100
```

If the key is configured correctly, SSH will authenticate using your SSH key.

---

# 17. Understanding `authorized_keys`

On the remote Ubuntu machine, public SSH keys are normally stored in:

```text
~/.ssh/authorized_keys
```

For example:

```text
/home/ubuntu/.ssh/authorized_keys
```

The file can contain one or more public keys.

Check it using:

```bash
cat ~/.ssh/authorized_keys
```

---

# 18. Correct SSH Permissions

SSH permissions are important.

Use:

```bash
chmod 700 ~/.ssh
```

For the private key:

```bash
chmod 600 ~/.ssh/id_ed25519
```

For the public key:

```bash
chmod 644 ~/.ssh/id_ed25519.pub
```

For the SSH configuration:

```bash
chmod 600 ~/.ssh/config
```

For the authorized keys file:

```bash
chmod 600 ~/.ssh/authorized_keys
```

---

# 19. Test the SSH Connection

Use:

```bash
ssh username@IP_ADDRESS
```

Example:

```bash
ssh ubuntu@192.168.1.100
```

If the connection is successful, you will get a terminal session on the remote Ubuntu machine.

---

# 20. Find Ubuntu IP Address

To find the local Ubuntu machine's IP address:

```bash
hostname -I
```

Example:

```text
192.168.1.100
```

Another useful command is:

```bash
ip addr
```

Look for the IP address associated with your network interface.

---

# 21. Common `.ssh` Directory Structure

After completing the setup, the `.ssh` directory may look like:

```text
~/.ssh/
│
├── id_ed25519
├── id_ed25519.pub
├── config
├── known_hosts
└── authorized_keys
```

### File Description

| File              | Purpose                                               |
| ----------------- | ----------------------------------------------------- |
| `id_ed25519`      | Private SSH key                                       |
| `id_ed25519.pub`  | Public SSH key                                        |
| `config`          | SSH connection configuration                          |
| `known_hosts`     | Stores identities of previously connected SSH servers |
| `authorized_keys` | Public keys allowed to log into this machine          |

---

# 22. SSH Security Rules

Follow these basic security rules:

1. Never share your private key.
2. Do not upload `id_ed25519` to GitHub.
3. You can safely share your public key when required.
4. Use a strong passphrase for important systems.
5. Keep `.ssh` permissions restricted.
6. Do not put private keys inside a public project folder.

---

# 23. Useful SSH Commands

### Check SSH version

```bash
ssh -V
```

### Check SSH server

```bash
sudo systemctl status ssh
```

### Start SSH server

```bash
sudo systemctl start ssh
```

### Stop SSH server

```bash
sudo systemctl stop ssh
```

### Restart SSH server

```bash
sudo systemctl restart ssh
```

### Generate SSH key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

### List SSH keys

```bash
ls -la ~/.ssh
```

### Show public key

```bash
cat ~/.ssh/id_ed25519.pub
```

### Add key to SSH agent

```bash
ssh-add ~/.ssh/id_ed25519
```

### Connect to remote machine

```bash
ssh username@IP_ADDRESS
```

---

# 24. Troubleshooting

## Problem 1: `.ssh` directory does not exist

Create it:

```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```

---

## Problem 2: SSH service is not running

Run:

```bash
sudo systemctl start ssh
```

Then check:

```bash
sudo systemctl status ssh
```

---

## Problem 3: Permission denied

Check permissions:

```bash
ls -la ~/.ssh
```

Then apply:

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub
```

---

## Problem 4: SSH key is not found

Check:

```bash
ls -la ~/.ssh
```

Then add the key:

```bash
ssh-add ~/.ssh/id_ed25519
```

---

# 25. Complete Setup Commands

For a quick setup, the main commands are:

```bash
sudo apt update
sudo apt install openssh-client openssh-server

sudo systemctl enable ssh
sudo systemctl start ssh

mkdir -p ~/.ssh
chmod 700 ~/.ssh

ssh-keygen -t ed25519 -C "your_email@example.com"

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

cat ~/.ssh/id_ed25519.pub
```

---

# 26. Final SSH Setup

After completing the setup, your Ubuntu machine will have:

```text
Ubuntu Machine
      │
      └── ~/.ssh/
           │
           ├── id_ed25519
           │     └── Private Key
           │
           ├── id_ed25519.pub
           │     └── Public Key
           │
           ├── config
           │     └── SSH Configuration
           │
           └── known_hosts
                 └── Known SSH Servers
```

The `.ssh` directory provides the basic configuration and key storage required for secure SSH authentication.

---

# 27. Conclusion

SSH is an important tool for securely connecting to Linux systems. By creating the `.ssh` directory, generating an Ed25519 key pair, configuring permissions, and starting the SSH service, an Ubuntu machine can be prepared for secure SSH communication.

The same SSH key can also be used for services such as GitHub, allowing secure authentication without entering a GitHub password every time.
