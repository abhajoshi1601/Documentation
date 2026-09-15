# Git Basic Commands Documentation

## 1. Introduction

Git is a **Distributed Version Control System (DVCS)** used to track changes in files and source code.

Git helps developers:

* Track changes in a project
* Save different versions of code
* Work on different features using branches
* Collaborate with other developers
* Upload projects to platforms such as GitHub
* Recover previous versions of files
* Manage project history

Git is commonly used in software development, web development, cybersecurity, data science, and many other technical fields.

---

# 2. Git vs GitHub

Git and GitHub are not the same thing.

### Git

Git is a version control system that runs on your computer.

It allows you to:

```text
Create repository
Track changes
Create commits
Create branches
Merge branches
View history
```

### GitHub

GitHub is an online platform that hosts Git repositories.

It allows you to:

```text
Store repositories online
Collaborate with developers
Share projects
Create pull requests
Manage issues
Review code
```

A simple way to understand it:

```text
Git     → Tool used to manage code versions
GitHub  → Online platform where Git repositories can be stored
```

---

# 3. Installing Git

## Ubuntu / Debian

Update the package list:

```bash
sudo apt update
```

Install Git:

```bash
sudo apt install git
```

Check the installation:

```bash
git --version
```

Example output:

```text
git version 2.x.x
```

---

## Windows

Git can be installed using Git for Windows.

After installation, open:

```text
Git Bash
```

Then check:

```bash
git --version
```

---

# 4. Git Configuration

Before using Git, configure your name and email.

## Set Username

```bash
git config --global user.name "Your Name"
```

Example:

```bash
git config --global user.name "Abha"
```

## Set Email

```bash
git config --global user.email "your-email@example.com"
```

Example:

```bash
git config --global user.email "abha@example.com"
```

The email should normally match the email associated with your GitHub account if you want your commits attributed to that account.

---

# 5. View Git Configuration

To see your Git configuration:

```bash
git config --list
```

To check your username:

```bash
git config user.name
```

To check your email:

```bash
git config user.email
```

---

# 6. Create a New Project Directory

Create a project folder:

```bash
mkdir my-project
```

Go inside the folder:

```bash
cd my-project
```

Check your current location:

```bash
pwd
```

---

# 7. Initialize a Git Repository

To convert a normal project folder into a Git repository:

```bash
git init
```

Example output:

```text
Initialized empty Git repository
```

Git creates a hidden directory:

```text
.git
```

The `.git` directory contains information required by Git to track your project.

---

# 8. Check Repository Status

The most commonly used Git command is:

```bash
git status
```

It shows:

* Modified files
* New files
* Deleted files
* Staged files
* Current branch

Example:

```bash
git status
```

Possible output:

```text
On branch main

Untracked files:
    index.html
    style.css
```

---

# 9. Git Working Areas

Git mainly works with three important areas:

```text
Working Directory
       ↓
Staging Area
       ↓
Git Repository
```

### Working Directory

This is where you create and modify files.

### Staging Area

Files selected for the next commit are placed here.

### Repository

Committed changes are stored in Git's repository history.

---

# 10. Create a File

Example:

```bash
touch README.md
```

Check the status:

```bash
git status
```

Git will show the file as untracked.

---

# 11. Add Files to the Staging Area

To stage one file:

```bash
git add README.md
```

To stage multiple files:

```bash
git add file1.txt file2.txt
```

To stage all changed files:

```bash
git add .
```

Another commonly used command:

```bash
git add -A
```

Check the status:

```bash
git status
```

The file should now appear under:

```text
Changes to be committed
```

---

# 12. Commit Changes

A commit saves a snapshot of your staged changes in Git history.

Syntax:

```bash
git commit -m "commit message"
```

Example:

```bash
git commit -m "Add README file"
```

A good commit message should clearly describe the change.

Good examples:

```text
Add login page
Fix password validation
Update homepage design
Add database connection
```

Avoid unclear messages such as:

```text
changes
update
done
test
```

---

# 13. First Commit

A basic first commit workflow is:

```bash
git init
git add .
git commit -m "Initial commit"
```

This is one of the most important Git workflows to remember.

---

# 14. View Commit History

To see previous commits:

```bash
git log
```

Example:

```text
commit abc123
Author: Abha
Date: ...

    Add login page
```

For a shorter history:

```bash
git log --oneline
```

Example:

```text
abc123 Add login page
def456 Add homepage
ghi789 Initial commit
```

---

# 15. View Detailed Commit Information

To see information about a particular commit:

```bash
git show COMMIT_ID
```

Example:

```bash
git show abc123
```

This shows details about what changed in that commit.

---

# 16. View Changes Before Committing

To see changes that have not been staged:

```bash
git diff
```

This compares your working directory with the staged version.

To see staged changes:

```bash
git diff --staged
```

---

# 17. Modify a File

Suppose you have:

```text
README.md
```

Edit the file:

```bash
nano README.md
```

Or open it using VS Code.

After making changes:

```bash
git status
```

Git will show the file as modified.

Then:

```bash
git add README.md
```

and:

```bash
git commit -m "Update README"
```

---

# 18. Remove a File

To remove a file from the project and stage the deletion:

```bash
git rm filename
```

Example:

```bash
git rm oldfile.txt
```

Then commit:

```bash
git commit -m "Remove old file"
```

---

# 19. Rename a File

Git provides a command for renaming files:

```bash
git mv oldname.txt newname.txt
```

Example:

```bash
git mv test.txt notes.txt
```

Then commit:

```bash
git commit -m "Rename test file"
```

---

# 20. Git Branches

A branch is an independent line of development.

Branches are useful when you want to work on a new feature without directly changing the main branch.

Example:

```text
main
 │
 ├── feature-login
 │
 └── feature-dashboard
```

---

# 21. View Branches

To see local branches:

```bash
git branch
```

Example:

```text
* main
  feature-login
```

The `*` indicates the currently active branch.

---

# 22. Create a Branch

Create a new branch:

```bash
git branch feature-login
```

Example:

```bash
git branch login
```

However, creating a branch does not automatically switch to it.

---

# 23. Switch to a Branch

Use:

```bash
git switch feature-login
```

Example:

```bash
git switch login
```

Older Git syntax is:

```bash
git checkout login
```

`git switch` is generally clearer for branch switching.

---

# 24. Create and Switch to a Branch

You can create and switch to a new branch in one command:

```bash
git switch -c feature-login
```

Example:

```bash
git switch -c login
```

---

# 25. Delete a Branch

After merging a branch, you can delete it:

```bash
git branch -d feature-login
```

Force delete:

```bash
git branch -D feature-login
```

Use `-D` carefully because it can delete a branch even when Git thinks it has unmerged changes.

---

# 26. Merge Branches

Suppose you have:

```text
main
feature-login
```

First switch to main:

```bash
git switch main
```

Then merge the feature branch:

```bash
git merge feature-login
```

Example:

```bash
git switch main
git merge login
```

After a successful merge, the changes from the feature branch become part of the main branch.

---

# 27. Merge Conflict

A merge conflict can occur when two branches modify the same part of a file differently.

Git may show:

```text
<<<<<<< HEAD
Code from main
=======
Code from feature branch
>>>>>>> feature-login
```

You must manually decide which code should remain.

After fixing the file:

```bash
git add filename
```

Then:

```bash
git commit -m "Resolve merge conflict"
```

---

# 28. Clone a Repository

`git clone` downloads an existing Git repository to your computer.

Syntax:

```bash
git clone repository-url
```

Example:

```bash
git clone https://github.com/username/project.git
```

Then enter the project directory:

```bash
cd project
```

---

# 29. Git Remote

A remote is a connection between your local Git repository and a repository hosted somewhere else, such as GitHub.

View remote repositories:

```bash
git remote -v
```

Example:

```text
origin  https://github.com/username/project.git (fetch)
origin  https://github.com/username/project.git (push)
```

---

# 30. Add a Remote Repository

If you created a local Git repository and want to connect it to GitHub:

```bash
git remote add origin https://github.com/username/project.git
```

Check it:

```bash
git remote -v
```

Here:

```text
origin
```

is the common name given to the remote repository.

---

# 31. Change Remote URL

To change the URL of an existing remote:

```bash
git remote set-url origin https://github.com/username/new-project.git
```

Check:

```bash
git remote -v
```

---

# 32. Push Changes to GitHub

After committing your changes:

```bash
git push origin main
```

This uploads your local commits to the `main` branch of the remote repository.

---

# 33. First Push

For a newly created repository, you may use:

```bash
git push -u origin main
```

The `-u` option sets the upstream branch.

After this, you can usually use:

```bash
git push
```

instead of specifying the remote and branch every time.

---

# 34. Pull Changes from Remote

To download and integrate changes from the remote repository:

```bash
git pull
```

Example:

```bash
git pull origin main
```

A simple workflow is:

```text
Remote Repository
       ↓
    git pull
       ↓
Local Repository
```

---

# 35. Fetch Changes

`git fetch` downloads information about remote changes without automatically merging them into your current branch.

```bash
git fetch
```

You can then inspect the changes before merging.

Example:

```bash
git fetch origin
```

Difference:

```text
git fetch → Downloads remote information
git pull   → Fetches and integrates changes
```

---

# 36. Git Push vs Pull

### `git push`

Uploads local commits to the remote repository.

```bash
git push
```

### `git pull`

Downloads and integrates changes from the remote repository.

```bash
git pull
```

Simple diagram:

```text
Local Repository  ── git push ──>  Remote Repository

Local Repository  <── git pull ──  Remote Repository
```

---

# 37. `.gitignore`

`.gitignore` tells Git which files or directories should not be tracked.

Create a file:

```text
.gitignore
```

Example:

```text
__pycache__/
*.pyc
.env
node_modules/
.vscode/
```

For a Python project:

```text
__pycache__/
*.pyc
.env
venv/
```

For a Node.js project:

```text
node_modules/
.env
```

Then check:

```bash
git status
```

Ignored files should not appear as untracked files.

---

# 38. Unstage a File

If you accidentally staged a file:

```bash
git add notes.txt
```

You can remove it from the staging area using:

```bash
git restore --staged notes.txt
```

The file will remain in your working directory.

---

# 39. Discard Changes in a File

If you modified a file but want to restore it to the version from the latest commit:

```bash
git restore filename
```

Example:

```bash
git restore notes.txt
```

> Be careful. This discards your uncommitted changes to that file.

---

# 40. Restore a File from the Staging Area

If a file is staged and you want to restore the working copy to the staged version:

```bash
git restore filename
```

This is useful when you want to discard changes made after staging.

---

# 41. Amend the Last Commit

If you forgot something in your latest commit, you can update it.

First make the required changes:

```bash
git add .
```

Then:

```bash
git commit --amend
```

Or provide a new message:

```bash
git commit --amend -m "Updated project files"
```

Use this carefully if the previous commit has already been pushed to a shared repository.

---

# 42. Revert a Commit

`git revert` creates a new commit that reverses the changes introduced by an earlier commit.

Syntax:

```bash
git revert COMMIT_ID
```

Example:

```bash
git revert abc123
```

This is generally safer than rewriting shared history.

---

# 43. Reset

`git reset` can move the current branch pointer and can change what is staged or committed.

### Unstage changes

```bash
git reset HEAD filename
```

Modern equivalent:

```bash
git restore --staged filename
```

### Reset to a previous commit

```bash
git reset --hard COMMIT_ID
```

Example:

```bash
git reset --hard abc123
```

> Be very careful with `--hard` because it can permanently discard uncommitted changes.

---

# 44. Git Stash

`git stash` temporarily stores uncommitted changes.

Suppose you are working on a feature but need to switch branches.

Save your current changes:

```bash
git stash
```

Your working directory becomes clean.

List stashes:

```bash
git stash list
```

Restore the latest stash:

```bash
git stash pop
```

Apply a stash without removing it:

```bash
git stash apply
```

Delete a stash:

```bash
git stash drop
```

---

# 45. Git Tags

Tags are used to mark important points in the project history, such as releases.

Create a tag:

```bash
git tag v1.0
```

List tags:

```bash
git tag
```

Create an annotated tag:

```bash
git tag -a v1.0 -m "Version 1.0"
```

Push a tag:

```bash
git push origin v1.0
```

Push all tags:

```bash
git push origin --tags
```

---

# 46. Show Branch Information

To see branches and their latest commits:

```bash
git branch -v
```

To see both local and remote branches:

```bash
git branch -a
```

---

# 47. Check Remote Branches

Use:

```bash
git branch -r
```

This displays remote-tracking branches.

Example:

```text
origin/main
origin/develop
```

---

# 48. Rename a Branch

Rename the current branch:

```bash
git branch -m new-name
```

Example:

```bash
git branch -m main
```

---

# 49. Show Current Branch

You can use:

```bash
git branch --show-current
```

Example output:

```text
main
```

---

# 50. Git Help

If you do not understand a command, Git provides built-in help.

Example:

```bash
git help
```

Help for a specific command:

```bash
git help commit
```

A shorter form:

```bash
git commit --help
```

You can also use:

```bash
git commit -h
```

---

# 51. Git Alias

Aliases allow you to create shorter commands.

Example:

```bash
git config --global alias.st status
```

Now:

```bash
git st
```

will work like:

```bash
git status
```

Another example:

```bash
git config --global alias.co checkout
```

---

# 52. Git Clean

`git clean` removes untracked files from the working directory.

First preview what would be removed:

```bash
git clean -n
```

To actually remove untracked files:

```bash
git clean -f
```

> Use this carefully because it can permanently delete untracked files.

---

# 53. Git Diff

Check changes in the working directory:

```bash
git diff
```

Check staged changes:

```bash
git diff --staged
```

Compare two commits:

```bash
git diff COMMIT1 COMMIT2
```

Example:

```bash
git diff abc123 def456
```

---

# 54. Git Log Options

Basic log:

```bash
git log
```

One-line log:

```bash
git log --oneline
```

Show branches:

```bash
git log --oneline --all
```

Show graphical history:

```bash
git log --oneline --graph --all
```

A useful command is:

```bash
git log --oneline --graph --decorate --all
```

---

# 55. Git Blame

`git blame` shows who last modified each line of a file.

Example:

```bash
git blame README.md
```

It can help identify when and by whom a particular line was changed.

---

# 56. Git Show

`git show` displays information about an object, commonly a commit.

Example:

```bash
git show HEAD
```

Show the previous commit:

```bash
git show HEAD~1
```

---

# 57. HEAD

`HEAD` represents the currently checked-out commit or branch reference.

For example:

```bash
git show HEAD
```

means:

```text
Show the current commit.
```

Previous commit:

```bash
git show HEAD~1
```

Two commits before:

```bash
git show HEAD~2
```

---

# 58. Check Git Repository Information

Check the repository status:

```bash
git status
```

Show the repository's top-level directory:

```bash
git rev-parse --show-toplevel
```

Show the current branch:

```bash
git branch --show-current
```

---

# 59. Git Remote Details

Show remote URLs:

```bash
git remote -v
```

Show detailed information about a remote:

```bash
git remote show origin
```

---

# 60. Complete Basic Git Workflow

A typical Git workflow looks like this:

```text
Create Project
      ↓
git init
      ↓
Create/Edit Files
      ↓
git status
      ↓
git add .
      ↓
git commit -m "message"
      ↓
git branch
      ↓
git push
```

---

# 61. Basic Local Git Example

Create a project:

```bash
mkdir my-project
cd my-project
```

Initialize Git:

```bash
git init
```

Create a file:

```bash
touch README.md
```

Check status:

```bash
git status
```

Stage the file:

```bash
git add README.md
```

Commit it:

```bash
git commit -m "Initial commit"
```

View history:

```bash
git log --oneline
```

---

# 62. Basic GitHub Workflow

After creating a repository on GitHub, a typical workflow is:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/username/project.git
git push -u origin main
```

After the first push, future changes can usually be uploaded using:

```bash
git add .
git commit -m "Update project"
git push
```

---

# 63. Working with a Team

A simple team workflow can look like:

```text
             GitHub
                ↑
                │
              push
                │
Developer A → Local Repository
                │
              pull
                ↓
Developer B → Local Repository
```

Developers can use branches to work on separate features.

Example:

```text
main
│
├── login-feature
├── dashboard-feature
└── payment-feature
```

Each feature can be developed separately and later merged into `main`.

---

# 64. Git Branch Workflow Example

Create a feature branch:

```bash
git switch -c login-feature
```

Make changes to the project.

Stage the changes:

```bash
git add .
```

Commit:

```bash
git commit -m "Add login feature"
```

Push the branch:

```bash
git push -u origin login-feature
```

Switch back to main:

```bash
git switch main
```

Update main:

```bash
git pull
```

Merge the feature:

```bash
git merge login-feature
```

Push the merged changes:

```bash
git push
```

---

# 65. Common Git Commands Quick Reference

| Command           | Purpose                        |
| ----------------- | ------------------------------ |
| `git --version`   | Check Git version              |
| `git config`      | Configure Git                  |
| `git init`        | Create a repository            |
| `git status`      | Check repository status        |
| `git add`         | Stage changes                  |
| `git commit`      | Save staged changes            |
| `git log`         | View commit history            |
| `git show`        | Show commit details            |
| `git diff`        | View changes                   |
| `git branch`      | Manage branches                |
| `git switch`      | Switch branches                |
| `git merge`       | Merge branches                 |
| `git clone`       | Download a repository          |
| `git remote`      | Manage remote repositories     |
| `git push`        | Upload commits                 |
| `git pull`        | Download and integrate changes |
| `git fetch`       | Download remote information    |
| `git rm`          | Remove tracked files           |
| `git mv`          | Move or rename files           |
| `git restore`     | Restore files                  |
| `git revert`      | Reverse a commit               |
| `git reset`       | Reset repository state         |
| `git stash`       | Temporarily save changes       |
| `git tag`         | Create version tags            |
| `git blame`       | Show line authorship           |
| `git clean`       | Remove untracked files         |
| `git grep`        | Search tracked files           |
| `git reflog`      | View reference history         |
| `git cherry-pick` | Apply a specific commit        |
| `git remote -v`   | View remote URLs               |
| `git branch -a`   | View all branches              |

---

# 66. Important Git Concepts

Before using Git professionally, understand these terms:

### Repository

A project tracked by Git.

### Working Directory

The files you are currently working on.

### Staging Area

The area where changes are prepared before committing.

### Commit

A saved snapshot of changes.

### Branch

A separate line of development.

### Merge

Combines changes from different branches.

### Remote

A repository hosted somewhere else, such as GitHub.

### Clone

Creates a local copy of a remote repository.

### Push

Uploads local commits to a remote repository.

### Pull

Downloads and integrates changes from a remote repository.

### Fetch

Downloads remote information without automatically integrating it.

### HEAD

Represents the current checked-out commit/branch reference.

### Tag

A named reference used to mark an important point in history.

---

# 67. Git Workflow Diagram

The complete basic workflow can be remembered as:

```text
             Working Directory
                    │
                    │ git add
                    ↓
             Staging Area
                    │
                    │ git commit
                    ↓
             Local Repository
                    │
                    │ git push
                    ↓
             Remote Repository
                    │
                    │ git pull
                    ↓
             Working Directory
```

---

# 68. Most Important Commands for Beginners

If you are completely new to Git, learn these commands first:

```bash
git --version
git config
git init
git status
git add
git commit
git log
git branch
git switch
git merge
git clone
git remote
git push
git pull
git fetch
git diff
git restore
git stash
```

Once these commands are understood, learning advanced Git becomes much easier.

---

# 69. Recommended Beginner Practice

Create a practice project:

```bash
mkdir git-practice
cd git-practice
git init
```

Create a file:

```bash
touch notes.txt
```

Add some content:

```bash
echo "Learning Git" > notes.txt
```

Check status:

```bash
git status
```

Stage the file:

```bash
git add notes.txt
```

Commit:

```bash
git commit -m "Add notes file"
```

Modify the file:

```bash
echo "Git is a version control system" >> notes.txt
```

Check the difference:

```bash
git diff
```

Stage and commit again:

```bash
git add notes.txt
git commit -m "Update Git notes"
```

View the history:

```bash
git log --oneline
```

Create a branch:

```bash
git switch -c practice-branch
```

Make another change:

```bash
echo "Learning branches" >> notes.txt
```

Commit:

```bash
git add .
git commit -m "Practice Git branch"
```

Return to main:

```bash
git switch main
```

Merge the branch:

```bash
git merge practice-branch
```

---

# 70. Important Safety Rules

When using Git, remember:

1. Always check `git status` before performing important operations.
2. Write meaningful commit messages.
3. Do not commit passwords, API keys, or secret credentials.
4. Use `.gitignore` for sensitive or unnecessary files.
5. Be careful with `git reset --hard`.
6. Be careful with `git clean -f`.
7. Avoid rewriting shared history unless you understand the consequences.
8. Pull the latest changes before starting collaborative work.
9. Use branches for new features.
10. Review changes with `git diff` before committing.

---

# Conclusion

Git is an essential tool for managing and tracking changes in software projects. Beginners should first understand the basic workflow:

```text
Create/Edit
    ↓
git status
    ↓
git add
    ↓
git commit
    ↓
git push
```

For collaboration, the workflow expands to:

```text
Clone
  ↓
Create Branch
  ↓
Make Changes
  ↓
Add
  ↓
Commit
  ↓
Push
  ↓
Pull Request / Merge
```

Learning Git commands step by step will make it easier to work with GitHub, collaborate with developers, manage projects, and maintain a professional software development workflow.

