---
title: "Git and GitHub Crash course: Get Started"
datePublished: Tue Jan 30 2024 15:45:21 GMT+0000 (Coordinated Universal Time)
cuid: cmd4xtcms000702ky6iyl311p
slug: git-and-github-crash-course-get-started-a338a31d2966

---

### 1\. What is a Version Control System?

Version control, or source control, is a system that manages changes to software code over time. It allows multiple developers to work on a project simultaneously, tracks changes, and provides mechanisms to merge those changes seamlessly.

#### Famous VCS:

*   Git: Most widely used distributed version control system.
*   Apache SubVersion: Centralized version control system.
*   Piper: Used by Google.

### 2\. Introduction to Git VCS

#### What is Git?

*   Git is a distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

#### Installation of Git CLI

*   Install Git on your local machine.

#### Basic Git Commands

*   Learn fundamental commands:
*   `git init`: Initializes a new Git repository.
*   `git clone <repository_url>`: Clones a repository from a URL.
*   `git add <file_path>`: Adds changes in a file to the staging area.
*   `git commit -m "message"`: Commits changes with a descriptive message.
*   `git status`: Displays the status of changes.
*   `git diff`: Shows changes between commits, branches, etc.

#### Setting up Git Global Configuration

*   Configure your name and email globally in Git.

### 3\. Version Controlling with Git

#### Initializing Git Project

*   Start a new Git project with `git init`.

#### Adding Files to VCS

*   Use `git add <file_path>` to add files to the version control system.
*   `git add .`: Adds all changes to the staging area.

#### Removing Files from VCS

*   `git rm <file_path>`: Removes a file from both the working directory and the staging area.

#### Introduction to Commits

*   Commits are snapshots of your project at a specific point in time.

#### Committing Files

*   `git commit -m "message"`: Commits changes with a descriptive message.

#### Staging Area

*   The staging area is where changes are prepared for a commit.

#### Logging Commit History

*   `git log`: Shows a detailed commit history.
*   `git log --oneline`: Displays a concise commit history.

#### Reverting Back

*   Undo changes with appropriate commands.

### 4\. Git VS GitHub

#### What are Git and GitServer

*   Git is the version control system.
*   GitServer is a term used to refer to the servers that host Git repositories.

#### Popular Git Servers

*   GitHub, GitLab, Bitbucket, etc.

#### GitHub

*   A web-based platform for hosting and collaborating on Git repositories.

#### Git Remotes

*   Remote repositories are versions of your project hosted on the internet or network.

#### Pushing and Pulling in Git

*   `git push`: Sends local changes to a remote repository.
*   `git pull`: Fetches changes from a remote repository and merges them into the local branch.

#### Self-Hosted Git Server

*   Setting up your Git server for more control.

### 5\. Branching in Git

#### Introduction to Branching Concept

*   Branching allows multiple lines of development to coexist.

#### Creating Branches

*   `git branch <branch_name>`: Creates a new branch.
*   `git checkout <branch_name>`: Switches to the specified branch.
*   `git checkout -b "branch_name"`: Creates and switches to a new branch in one step.

#### Branch Tags

*   Naming conventions like `feat/feat-name` for feature branches.

#### Merging Branches

*   Merge: Combining changes from different branches.
*   Rebase: Incorporating changes by moving or combining a sequence of commits.

#### Stashing

*   Temporary storage of changes that are not ready to be committed.