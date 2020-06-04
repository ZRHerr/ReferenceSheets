# Zach's Command Line Cheatsheet

- One stop shop of things I've gathered since my career as a software Engineer, use this as a reference when trying to accomplish tasks through the CLI.
- Feel free to add/update anything you see
- Currently using (Bash) - would be very beneficial if anyone uses others ie(unix, windows etc..) to add the equivalent.

## Table of Contents

- [BASH/Terminal](#work-with-bash)

  - [Bash Commands](#bash-commands)
  - [Bash Variables](#bash-variables)
  - [Directory Operations](#directory-operations)
  - [Search Files](#search-files)
  - [File Operations](#file-operations)
  - [File Permissions](#file-permission-numbers)

- [Working with Git](#working-with-git)
  - [Quick Start](#quick-start)
  - [Creating a project](#create-project)
  - [Branching & Merging](#branching-and-merging)
  - [Delete a project](#delete-project)
  - [Referring to revisions](#referring-to-revisions)

## Working with Bash

### Bash Commands

- `uname -a` Show sytem and kernel
- `head -n1 /etc/issue` Show distribution
- `mount` Show mounted filesystems
- `date` Show system date
- `uptime` Show uptime
- `whoami` Show your username (employeeId)
- `man command` Show manual for builtin command (Q - to quit)

### Bash Variables

- `env` Show enviro­nment variables
- `echo $NAME` Output value of \$NAME variable
- `export NAME=value` Set \$NAME to value
- `$PATH` Executable search path
- `$HOME` Home directory
- `$SHELL` Current shell

### Directory Operations

- `pwd` Show current Directory
- `mkdir dirName` Creates a directory "dirName"
- `cd dirName` Change directory to "dirName"
- `cd ..` Go up (1) directory
- `ls` List files
  - `-a` Show all (including hidden)
  - `-R` Recursive list
  - `-r` Reverse order
  - `-t` Sort by last modified
  - `-S` Sort by filesize
  - `-l` Long listing format
  - `-1` 1 file per line
  - `-m` Comma-separated output

### Search Files

- `grep -i` Case insens­itive search
- `grep -r` Recursive search
- `grep -v` Inverted search
- `grep -o` Show matched part of file only
- `find /dir/ -name name*` Find files starting with name in dir
- `find /dir/ -user name` Find files owned by name in dir
- `find /dir/ -mmin num` Find files modifed less than num minutes ago in dir
- `whereis command` Find binary / source / manual for command
- `locate file` Find file (quick search of system index)

### File Operations

- `touch file1` Create file1
- `cat file1 file2` Concat­enate files and output
- `less file1`View and paginate file1
- `file file1` Get type of file1
- `cp file1 file2` Copy file1 to file2
- `mv file1 file2` Move file1 to file2
- `rm file1` Delete file1
- `head file1` Show first 10 lines of file1
- `tail file1` Show last 10 lines of file1
- `tail -F file1` Output last lines of file1 as it changes

### File Permission Numbers

> **First digit** is owner permis­sion, **second** is group and **third** is everyone. Calculate permission digits by adding numbers below.
>
> - 4 = read (r)
> - 2 = write (w)
> - 1 = execute (x)

- `chmod 775 file` Change mode of file to 775
- `chmod -R 600 folder` Recurs­ively chmod folder to 600
- `chown user:group file` Change file owner to user and group to group

## Working with Git

### Quick Start

- `git clone <url>` Clone directory
- `git checkout -b <new-branch>` Create new local branch
- `git push -u origin <new-branch>` Sync local branch with remote
- `git checkout <branch>` Checkout branch
- `git push origin <branch>` Push branch to remote

- `git branch -d <branchname>` deletes local branch
- `git push origin :<branchname>` deletes remote branch

### Create Project

- `cd project/`
- `git init` initializes the repository
- `git add .` add those 'unknown' files
- `git commit` commit all changes, edit changelog entry
- `git rm --cached <file>...` ridiculously complicated command to undo, in case you forgot .gitignore

### Branching and Merging

- `git branch` show list of all branches (\* is active)
- `git checkout -b zachs-branch` create a new branch named "zachs-branch"
- `git commit -a` commit (all changes)
- `git checkout master` go back to master branch
- `git merge zachs-branch` merge changesets from zachs-branch (Git >= 1.5)
- `git pull . zachs-branch` merge changesets from zachs-branch (all Git versions)
- `git branch -m oldname newname` rename branch
- `git branch -m newname` rename current branch

### Delete Project

- `git branch -d <branchname>` deletes local branch
- `git push origin :<branchname>` deletes remote branch
- `git remote prune <branchname>` update local/remote sync

### Referring to Revisions

**by name**

- `git log v1.0.0` show history leading up to tag "v1.0.0"
- `git log master` show history of branch "master"

**relative to a name**

- `git show master^` show parent to last revision of master
- `git show master~2` show grand parent to tip of master
- `git show master~3` show great grand parent to tip of master (you get the idea)

**by output of "git describe"**

- `git show v1.4.4-g730996f` you get this string by calling "git describe"

**by hash (internally, all objects are identified by a hash)**

- `git show f665776185ad074b236c00751d666da7d1977dbe`
  - `git show f665776` a unique prefix is sufficient

**tag a revision**

- `git tag v1.0.0` make current HEAD known as "v1.0.0"
- `git tag interesting v1.4.4-g730996f` tag a specific revision (not HEAD)

**diff between two branches**

- `git diff origin..master` pipes a diff into PAGER
- `git diff origin..master > my.patch` pipes a diff into my.patch
- `git diff --stat HEAD` get diffstat of uncommitted work
