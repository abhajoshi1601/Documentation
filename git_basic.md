# Git Basic Commands Documentation

## Introduction

Git is a tool used to track changes in a project. It helps developers save their work, maintain the history of changes, work with different branches, and upload their project to GitHub.

This documentation explains some commonly used Git commands in simple language.

---

# 1. `git add .`

## Command

```bash
git add .
```

## Meaning

The `git add .` command tells Git to prepare all the changed and new files for the next commit.

In simple words:

> **"Mere saare changes ko save karne ke liye ready karo."**

## Example

Suppose you changed these files:

```text
index.html
style.css
script.js
```

Run:

```bash
git add .
```

Now these changes are ready to be committed.

## Important Point

`git add .` does **not** upload files to GitHub.

It only moves the changes to the **staging area**.

## Real-Life Example

Think about sending a parcel:

```text
Files
  ↓
git add .
  ↓
Files are packed and ready
```

---

# 2. `git commit -m "message"`

## Command

```bash
git commit -m "message"
```

## Meaning

The `git commit` command saves the changes that were previously added using `git add`.

The message describes what changes were made.

## Example

```bash
git commit -m "Added portfolio website"
```

This means:

> The portfolio website changes have been saved in Git.

## More Examples

```bash
git commit -m "Added login page"
```

```bash
git commit -m "Fixed navbar issue"
```

```bash
git commit -m "Updated website design"
```

## Real-Life Example

```text
git add .
     ↓
Pack the changes

git commit
     ↓
Officially save/record the changes
```

---

# 3. `git push origin "branch_name"`

## Command

```bash
git push origin main
```

## Meaning

The `git push` command uploads your committed changes from your computer to the remote GitHub repository.

Here:

* `origin` = name of the remote GitHub repository
* `main` = branch name

Therefore:

```bash
git push origin main
```

means:

> Upload my local `main` branch changes to the GitHub `main` branch.

## Example with Another Branch

```bash
git push origin feature-login
```

This uploads the `feature-login` branch to GitHub.

## Real-Life Example

```text
Your Computer
      ↓
  git push
      ↓
    GitHub
```

So, you can remember:

> **Push = Send your changes to GitHub.**

---

# 4. `git checkout -b "branchname"`

## Command

```bash
git checkout -b feature-login
```

## Meaning

This command creates a **new branch** and immediately switches to that branch.

It performs two actions:

1. Creates a new branch.
2. Switches to the new branch.

## Example

Suppose you are currently working on:

```text
main
```

You run:

```bash
git checkout -b feature-login
```

Now a new branch called `feature-login` is created.

```text
main
  \
   feature-login
```

You are now working on the `feature-login` branch.

## Why Use a Branch?

Branches allow you to work on new features without directly changing the main project.

For example:

```text
main
 ├── feature-login
 ├── feature-navbar
 └── bug-fix
```

Each branch can be used for a different task.

---

# 5. `git checkout "branchname"`

## Command

```bash
git checkout main
```

## Meaning

The `git checkout` command is used to switch to an existing branch.

## Example

Suppose you are currently on:

```text
feature-login
```

and want to switch back to:

```text
main
```

Use:

```bash
git checkout main
```

Now you are working on the `main` branch.

## Difference Between Checkout Commands

### Create a new branch

```bash
git checkout -b feature-login
```

This:

```text
Creates branch + Switches to branch
```

### Switch to an existing branch

```bash
git checkout feature-login
```

This:

```text
Only switches to the existing branch
```

## Easy Trick

```text
-b       → New branch
No -b    → Existing branch
```

---

# 6. `git log`

## Command

```bash
git log
```

## Meaning

The `git log` command shows the history of commits in your Git repository.

It helps you see:

* Commit ID
* Author
* Date
* Commit message
* Previous changes

## Example

```text
commit 82abc12
Author: Abha
Date: ...

Added portfolio website

commit 91def34
Author: Abha
Date: ...

Added CSS styling

commit 72xyz45
Author: Abha
Date: ...

Initial project
```

## Traceability

Traceability means being able to track the history of changes.

For example, suppose you want to know:

> When was the login page added?

You can use:

```bash
git log
```

and check the commit history.

Therefore:

> **`git log` is useful for checking project history and traceability.**

---

# 7. `git pull`

## Command

```bash
git pull
```

## Meaning

The `git pull` command downloads the latest changes from the remote GitHub repository and updates your local project.

In simple words:

> **"GitHub par jo latest changes hain, unko mere computer mein le aao."**

## Example

Suppose another developer changes the project and pushes the changes to GitHub.

The flow will be:

```text
Other Developer
      ↓
    GitHub
      ↓
   git pull
      ↓
 Your Computer
```

After running:

```bash
git pull
```

your local project gets the latest changes.

## Real-Life Example

Imagine GitHub is a shared online folder.

If someone updates a file in that folder, `git pull` helps you get those latest updates on your computer.

---

# Git Basic Workflow

A common Git workflow looks like this:

```text
Make changes in project
        ↓
    git add .
        ↓
git commit -m "message"
        ↓
git push origin main
        ↓
      GitHub
```

---

# Complete Example

Suppose you are creating a portfolio website.

## Step 1: Create a New Branch

```bash
git checkout -b portfolio
```

This creates a new `portfolio` branch.

---

## Step 2: Make Changes

You modify your project files:

```text
index.html
style.css
script.js
```

---

## Step 3: Add Changes

```bash
git add .
```

This prepares all changed files for the commit.

---

## Step 4: Commit Changes

```bash
git commit -m "Added portfolio website"
```

This saves the changes in Git.

---

## Step 5: Push Changes

```bash
git push origin portfolio
```

This uploads the changes to the `portfolio` branch on GitHub.

---

## Step 6: Check Commit History

```bash
git log
```

This shows the previous commits and their details.

---

## Step 7: Get Latest Changes

If there are new changes on GitHub:

```bash
git pull
```

This brings the latest changes to your computer.

---

# Quick Revision Table

| Command                      | Simple Meaning                             |
| ---------------------------- | ------------------------------------------ |
| `git add .`                  | Changes ko ready karo                      |
| `git commit -m "message"`    | Changes ko Git mein save karo              |
| `git push origin main`       | Changes ko GitHub par upload karo          |
| `git checkout -b branchname` | New branch banao aur switch karo           |
| `git checkout branchname`    | Existing branch par switch karo            |
| `git log`                    | Commit history aur traceability check karo |
| `git pull`                   | GitHub se latest changes lao               |

---

# Easy Way to Remember

```text
ADD
↓
Changes ready karo

COMMIT
↓
Changes save karo

PUSH
↓
GitHub par bhejo

PULL
↓
GitHub se changes lao

CHECKOUT
↓
Branch change karo

LOG
↓
History check karo
```

---

# Most Common Git Workflow

```bash
git add .
git commit -m "Updated project"
git push origin main
```

The meaning is:

```text
Changes ready
     ↓
Changes save
     ↓
Changes upload to GitHub
```

To get changes from GitHub:

```bash
git pull
```

---

# Conclusion

These Git commands are enough to understand the basic Git workflow:

* `git add .` prepares changes.
* `git commit` saves changes in Git.
* `git push` uploads changes to GitHub.
* `git pull` gets the latest changes from GitHub.
* `git checkout -b` creates and switches to a new branch.
* `git checkout` switches to an existing branch.
* `git log` shows the history of changes.

Understanding these commands is a good starting point for working with Git and GitHub.
