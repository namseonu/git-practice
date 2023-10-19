# Shell Commands
- Open Source SW
- Lecture 5
- Linux CLI(Command Line Interface) - 2

</br>

## Table of Contents
1. [I/O Redirection](#ⅰ-io-redirection)
2. [Useful Commands](#ⅱ-useful-commands)
3. [Permissions](#ⅲ-permissions)
4. [Text Editors](#ⅳ-text-editors)
5. [Tips](#ⅴ-tips)

</br>

## Ⅰ. I/O Redirection
### Ⅰ-1. Standard Output
By default, standard output is screen.

| Command | Description |
| - | - |
| `>` | Redirect output using `>` after a command to create and save the output in a file |
| `>>` | Append output to an existing file (if it already exists), or create and write to a new file if it doesn't exist |
| `cat` | Display the content of a text file |

```sh
# Create and save the output of `ls -lh` in 'file_list.txt'
$ ls -lh > file_list.txt

# Append output to 'file_list.txt'
$ ls -lh >> file_list.txt

# Display the content of a 'file_list.txt'
$ cat file_list.txt
```

</br>

### Ⅰ-2. Standard Input
By default, standard input is from keyboard.

| Command | Description |
| - | - |
| `<` | Redirect input from a file |

```sh
# You can mix `<` and `>` together in a single line
# The sorted result is saved to 'sorted_words.txt'
$ sort < words.txt > sorted_words.txt
```

</br>

## Ⅱ. Useful Commands
### Ⅱ-1. Pipelines "|"
- Pipeline feeds output of previous command to input of next command.
- Format: `command1 | command2 | command3 | ...`
```sh
# Example 1. enter `ls -lh | less`, then you can exit the screen using 'q' key
# `ls`: display a list of files and directories in the current directory
# `-l`: stand for 'long format'
# `-h`: make file sizes human-readable, showing them in a format like 'K' for kilobytes or 'M' for megabytes
# `less`: a text viewer that displays the content of files or command outputs on the screen
$ ls -lh | less

# Example 2
# `wc`: stands for 'word count' and is a command used to count lines, words, and characters in text
# `-l`: instructs `wc` to count the number of lines in the input
$ ls | wc -l
```

</br>

### Ⅱ-2. Expansion
Special characters(*, ~, ...) expand its meaning when given to shell commands.

| Special character (Wildcard) | Description |
| - | - |
| * | match any character or characters |
| ~ | represent the home directory of the specified user |

```sh
# `echo`: display text or variable values on the screen

# Display all files and directories in the current directory
$ echo *

# Represent the home directory of the currently logged-in user
$ echo ~

# Represent the home directory of the specified user
$ echo ~username
```

</br>

## Ⅲ. Permissions
### Ⅲ-1. Permissions
- Linux is a multi-user system.
- Files and directories have a permission assigned differently owner / group / others.

```sh
# Example
$ ls -l /bin/bash
-r-xr-xr-x  1 root  wheel  1310224 Sep 16 22:28 /bin/bash
```

Above, the `-r-xr-xr-x` means permission. If the permission status is `-rwxrwxrwx` instead, then the description is like below.

| Part | Description |
| - | - |
| `-` | File type: indicates regular file/directory
| `rwx` (1st) | Read(r), write(w) and execute(x) permissions for the file owner |
| `rwx` (2nd) | Read(r), write(w) and execute(x) permissions for the group owner of the file |
| `rwx` (3rd) | Read(r), write(w) and execute(x) permissions for all other users |

</br>

### Ⅲ-2. Changing Permissions
- `chmod` changes permissions.
- Format: `chmod 600 some_file` (600 is just example, and more detail below.)

| Value | Meaning | Owner | Group | Others |
| - | - | - | - | - |
| 777 | `rwxrwxrwx` = 111 111 111 (binary) | Read, write, execute | Read, write, execute | Read, write, execute |
| 755 | `rwxr-xr-x` = 111 101 101 (binary) | Read, write, execute | Read, execute | Read, execute |
| 700 | `rwx------` = 111 000 000 (binray) | Read, write, execute | | |
| 666 | `rw-rw-rw-` = 110 110 110 (binary) | Read, write | Read, write | Read, write |
| 644 | `rw-r--r--` = 110 100 100 (binary) | Read, write | Read | Read |
| 600 | `rw-------` = 110 000 000 (binray) | Read, write | | |

Plus,
- '777' is generally not a desirable setting.
- '755' is common for programs that are used by all users.
- '700' is useful for programs that only the owner may use and must be kept private from others.
- '644' is a common setting for data files that everybody may read, but only the owner may change.
- '600' is a common setting for data files that owner wants to keep private.

```sh
# Example
# Change the permission of a file 'word.txt' that only the owner can read and write, but all the others (including others in the group) can only read it. And no execution is needed for all users.
$ chmod 644 words.txt
```

</br>

### Ⅲ-3. Superuser
- A superuser has all system administration authority.
- Some commands need superuser's privilleges.
- Put `sudo` before the command if you are a superuser.
- Format: `sudo some_command`

```sh
# Change the current user to superuser (e.g., ubuntu -> root)
$ sudo -i
```

</br>

## Ⅳ. Text Editors

 | Interface | Text Editor Name | Short description | Link |
 | - | - | - | - |
 | CLI | vi, vim | The granddaddy of Unix text editors | [vi, vim](https://www.vim.org/) |
 | CLI | Emacs | The true giant in the world of text editors | [Emacs](https://www.gnu.org/software/emacs/) |
 | CLI | nano | A free clone of the text editor | [nano](https://www.nano-editor.org/) |
 | GUI | gedit | Easy to use and contains enough features to be a good beginners-level editor by GNOME | [GNOME](https://www.gnome.org/) |
 | GUI | kwrite | Advanced editor by KDE | [KDE](https://kde.org/) |

 *CLI: Command Line Interface  
 *GUI: Graphical User Interface

</br>

## Ⅴ. Tips
### Ⅴ-1. Backslash
Backslash can be used
  - to ignore line change in command ("enter"),
  - to enter a long command in multiple lines

```sh
# `--reverse`: specify displaying the list in reverse order
# `--human-readable`: same as `-h` above
$ ls -l \
> --reverse \
> --human-readable
```

</br>

### Ⅴ-2. History
- Type `history` to see previous command history.

```sh
# Example
# See previous command history and save it to a text file
$ history > history_command.txt
```

</br>
