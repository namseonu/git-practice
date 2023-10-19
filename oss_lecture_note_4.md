# Shell Commands
- Open Source SW
- Lecture 4
- Linux CLI(Command Line Interface) - 1

</br>

## Table of Contents
1. [Linux](#ⅰ-linux)
2. [CLI vs. GUI](#ⅱ-cli-vs-gui)
3. [Shell Commands](#ⅲ-shell-commands)

</br>

## Ⅰ. Linux
### Ⅰ-1. Linux
- Open source UNIX-like operating systems and kernels
- First released by Linus Torvalds in 1991
- Leading OS(Operating System) on servers
- Runs on embedded systems and mobile systems (e.g., Android)
- Most widely-used platform for open source software development
- Secure and stable
- Runs on CLI(Command Line Interface), but many distributions support GUIs as well

</br>

### Ⅰ-2. Kernel and Shell
#### ❖ Kernel
- Core of OS that controls and communicates with hardware resource

</br>

#### ❖ Shell
- Interface that allows users to communicate with kernel
- Users can run applications and give commands through shell
- E.g., bash (git bash), zsh, ...

</br>

![Kernel and Shell](https://github.com/namseonu/namseonu/assets/77925666/6d87f8b4-a623-4fda-a7b1-add2f74c2b70)

</br>

## Ⅱ. CLI vs. GUI

|  | CLI | GUI |
| - | - | - |
| Meaning | Command Line Interface | Graphical User Interface |
| Speed | Relatively fast | Relatively slow |
| For use | Keyboards mostly | Mouse mostly, Some keyboard shortcuts |
| Target user | Basic environment for developers | For daily users |
| Point | - Have to remember commands </br> - Scripts enable automation and records | - Easy to use and intuitive </br> - Manual labors required for repetitive tasks |
| Example | ![CLI](https://github.com/namseonu/namseonu/assets/77925666/8d019350-8d98-447b-bcce-46fdf6766f23) | ![GUI](https://github.com/namseonu/namseonu/assets/77925666/edeaa86d-2816-47ac-80e9-16a36f1518dc) |

</br>

## Ⅲ. Shell Commands
### Ⅲ-1. Shell Commands
| Command | Description |
| - | - |
| `$ pwd` | Show the current path in a hierarchical directory |
| `$ cd [directory name]` | Change directory |
| `$ ls` | Show list files and directories 
| `$ clear` | Clear the history of command on shell |
| `$ cp [original file] [new file]` | Copy files and directories |
| `$ mv [original file] [new file]` | Move files and directories or rename them |
| `$ rm [file]` | Delete files and directoreis permantely and irreversevely |
| `$ mkdir [new directory]` | Make a new directory |
| `$ help [command]` | Get information regarding a shell command |
| `$ map [command]` | Display the user manual of a shell command |
| `$ exit` | Exit from the shell script |

</br>

### Ⅲ-2. Detail Shell Commands
#### ❖ `cd` Command
##### Format
```sh
$ cd [directory name]
```

##### Example
```sh
# Root directory
$ cd /

# Current directory
$ cd .

# Upper-level directory
$ cd ..

# Home of current user
$ cd ~

# Absolute path
$ cd /home/ubuntu

# Relative path
$ cd ./home/ubuntu
$ cd ../home/ubuntu
```

##### Option/Argument
| Option/Argument | Description |
| - | - |
| / | Root directory |
| . | Current directory |
| .. | Upper-level directory |
| ~ | Home of current user |
| /[directory name] | Absolute path |
| ./[directory name] | Relative path |
| ../[directory name] | Relative path |

</br>

#### ❖ `ls` Command
- Show list the contents of a directory
- Probably the most commonly used Linux command
- Can be used in a number of different ways

##### Format
```sh
$ ls
```

##### Example
```sh
# List the files in the working directory
$ ls

# List the files in the /bin directory (or any other directory we care to specify)
$ ls /bin

# List the files in the working directory in long format
$ ls -l

# Same as above(`ls -l`), but size in units
$ ls -lh

# List the files in the /bin directory and the /etc directory in long format
$ ls -l /etc /bin

# List all fiels in the parent of the working directory in long format
$ ls -la ..
```

##### Option/Argument
| Option/Argument | Description |
| - | - |
| [directory name] | List the files in the directory |
| -l | Show detailed information (long format) |
| -l [directory name] | List the files in the directory |
| -lh | Show detailed information, but size in units
| -la | List all files (even ones with names beginning with a period character, which are normally hidden) in the parent of the working directory in long format |

</br>

#### ❖ `cp` Command
- Copy files and directories
- Make sure to backup your important contents when using this command.

##### Format
```sh
$ cp [original file] [new file]
```

##### Example
```sh
# Copies the contents of file1 into file2. If file2 does not exist, it is created; otherwise, file2 is silently overwritten with the contents of file1.
$ cp file1 file2

# Like above however, since the '-i' (interactive) option is specified, if file2 exists, the user is prompted before it is overwritten with the contents of file1.
$ cp -i file1 file2

# Copy the contents of file1 (into a file named file1) inside of directory dir1.
$ cp file1 dir1

# Copy the contents of the directory dir1. If directory dir2 does not exist, it is created. Otherwise, it creates a directory named dir1 within directory dir2.
$ cp -R dir1 dir2
```

##### Option/Argument
| Option/Argument | Description |
| - | - |
| [original file] | Original file that you want to copy |
| [new file] | New file that you want to create with `cp` command |
| -i | Means 'interactive', and prompted before it is overwritten with original file when the new file name is already exist. |
| -R | Using when copy the contents of the directory to directory. If directory that you want to create using original directory does not exist, it is created. |

</br>

#### ❖ `mv` Command
- Move files and directories or rename them.

##### Format
```sh
$ mv [original file] [new file]
```

##### Example
```sh
# If file2 does not exist, then file1 is renamed file2. If file2 exists, its contents are silently replaced with the contents of file1.
$ mv file1 file2

# Like above however, since the '-i (interactive) option is specified, if file2 exists, the user is prompted before it is overwritten with the contents of file1.
$ mv -i file1 file2

# The file file1 and file2 are moved to directory dir1. If dir1 does not exist, `mv` will exit with an error.
$ mv file1 file2 dir1

# If dir2 does not exist, then dir1 is renamed dir2. If dir2 exists, the directory dir1 is moved within directory dir2.
$ mv dir1 dir2
```

##### Option/Argument
| Option/Argument | Description |
| - | - |
| [file1] | Original file |
| [file2] | New file that you want to create with `mv` command |
| -i | Means 'interactive', and prompted before it is overwritten with original file when the new file name is already exist. |

</br>

#### ❖ `rm` Command
- Delete files and directories permantely and irreversevely.

##### Format
```sh
$ rm [file]
```

##### Example
```sh
# Delete file1 and file2.
$ rm file1 file2

# Like above however, since the '-i' (interactive) option is specified, the user is prompted before each file is deleted.
$ rm -i file1 file2

# Directories dir1 and dir2 are deleted along with all of their contents.
$ rm -r dir1 dir2
```

##### Option/Argument
| Option/Argument | Description |
| - | - |
| [file] | Original file that you want to delete |
| -i | Means 'interactive', and prompted before it is overwritten with original file when the new file name is already exist. |
| -r | Use when deleting directory (not file) |

</br>

### Ⅲ-3. Tips
#### ❖ Autocompletion
Press 'tab' key, then the command will be completed automatically.

</br>

#### ❖ Past Commands
If you want to show/know the past command, then press 'up/down arrow' key on the bash terminal.

</br>

#### ❖ Wildcards
Linux does note have an undelete command. Once you delete something with `rm`, It's gone. You can inflict terrific damage on your system with `rm` if you are not careful, particularly with wildcards.

Before you use `rm` with wildcards, try this helpful trick. Construct your command using `ls` instead. By doing this, you can see the effect of your wildcards before you delete files. After you have tested your command with `ls`, recall the command with the up-arrow key and then substitute `rm` for `ls` in the command.

| Pattern | Matches |
| - | - |
| * | All filenames |
| g* | All filenames that begin with the character 'g' |
| b*.txt | All filename that begin with the character 'b' and end with the characters '.txt' |
| Data??? | Any filename that begins with the characters 'Data' followed by exactly 3 more characters |

</br>
