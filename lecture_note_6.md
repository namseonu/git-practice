# Git Commands
- Open Source SW
- Lecture 6
- Git - 1

<br/>

## Table of Contents
1. [Version Control](#ⅰ-version-control)
2. [Git](#ⅱ-git)
3. [Git Commands](#ⅲ-git-commands)

<br/>

## Ⅰ. Version Control
### Ⅰ-1. Version Control and Collaboration
Associated with version control, basic solution is to make copies like below.

```plain text
project_v1.txt
project_v1_final.txt
project_v1_final_final.txt
project_v1_final_final_final.txt
...
```

This way is so complex and unintuitive.
At this point, the version control is required.

So, it's essential to use a **version control for software development and other documentation works.** We need a systematic management system for version control and collaboration.

<br/>

### Ⅰ-2. Changes vs. Snapshots
#### **Changes**: Storing data as changes to the base version  
![Changes](https://github.com/namseonu/namseonu/assets/77925666/3d9f3b4d-8de0-4c5c-b2de-ea96fbf99ad9)  
<span style="color: gray">*Source: Chacon and Straub, Pro Git (2nd edition)*</span>

#### **Snapshots**: Storing data as snapshots  
![Snapshots](https://github.com/namseonu/namseonu/assets/77925666/1513dee8-ec15-4bce-9149-d83889c74852)  
<span style="color: gray">*Source: Chacon and Straub, Pro Git (2nd edition)*</span>

<br/>

### Ⅰ-3 Local, Centralized, and Distributed Version Control
#### Local
- Version control only in local computer
- Difficult to collaborate with other

#### Centralized
- For collaboration
- There is a central VCS server.
- If needed, request to VCS server and then VCS server response to local.
- But when the VCS server is down, then the version control is not working well.
- E.g., SVN

#### Distributed
- For collaboration
- There is a server computer, but each local computer has all the versions(copies of server).
- So even if the server is down, the local computer can recover using version database in local.
- E.g., git

<br/>

![Version Control](https://github.com/namseonu/namseonu/assets/77925666/0120902f-b17d-421b-a34f-231e640667ed)  
<span style="color: gray">*Source: Chacon and Straub, Pro Git (2nd edition)*</span>

<br/>

## Ⅱ. Git
### Ⅱ-1. Three States in Git
#### Working Directory
- For project directory
- Common directory

#### Staging Area
- The middle step for committed
- Using git, files in working directory could be moved to staging area.

#### .git directory (Repository)
- When execute commit operation, then the commit log is created in repository.
- At this point, commit means snapshot.

<br/>

![Three States in Git](https://github.com/namseonu/namseonu/assets/77925666/eec44ddb-924f-41e4-a803-33ff0653b863)

<br/>

### Ⅱ-2. Installing Git
#### 1. Check pre-installed version
```sh
# Linux / Mac / Windows
$ git --version
git version 2.25.1
```

#### 2. If not installed, then install git
```sh
# Linux (install on a Debian-based distribution)
$ sudo apt install git-all

# Mac
# https://git-scm.com/download/mac

# Windows (after installing, open git bash)
# https://git-scm.com/download/win
```

#### 3. First-time setup

Git configuration are stored in three levels:  
Each level overrides values in the previous level: system -> global -> local

| Level | Option | Description | File |
| - | - | - | - |
| System level | `--system` option | Affects all uses and repositories on the system (administrative) | /etc/gitconfig |
| Global (user) level | `--global` option | Affects all repositories of a current user | ~/.config/git/config |
| Local level | `--local` option | Specific to the current repository | .git/gitconfig |

```sh
# show the config list
$ git config --list
$ git config --list --show-origin

# set the config (user.name and user.email) on global (user) level
$ git config --global user.name "namseonu"
$ git config --global user.email "ska2870ghk@naver.com"

# check the setup
$ git config user.name
$ git config user.email

# set the default branch name main (previous: master -> now: main)
$ git config --global init.defaultBranch main
```

Finished! then, you can use git with git commands.
For detail, reference to 'Ⅲ. Git Commands'.

<br/>

### Ⅱ-3. Ignoring a File
Note: If you don't know the git commands at this step, then go to the 'Ⅲ. Git Commands'.

#### 1. Create the .gitignore to root directory
```sh
# Linux Example 1.
$ nano .gitignore

# Linux Example 2.
$ vi .gitignore
```

#### 2. Write the contents(what you want to ignore) in .gitignore file (like below)
```plain text
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```

#### 3. Commit the .gitignore file
```sh
# Example
$ git add .gitignore
$ git status
$ git commit -m "Add gitignore"
```

#### 4. If the .gitignore not adapted, then remove cache
```sh
# remove all git caches
$ git rm -r --cached .

# Again step '3. Commit the .gitignore file'
```

<br/>

## Ⅲ. Git Commands

| Command | Description |
| - | - |
| `git config` | Setup git configuration |
| `git init` | Initialize a repository in an existing directory |
| `git status` | Check repository status |
| `git add {fileName}` | Add a new file to be staged (tracked) |
| `git add .` | Add all files to be staged (tracked) |
| `git rm --cached {fileName}` | Unstage a file |
| `git commit -m "{commit message"}` | Commit |
| `git log` | Show the log of commits
| `git branch` | Show the list of branches |
| `git branch -m {originalName} {newName}` | Change branch name |


<br/>