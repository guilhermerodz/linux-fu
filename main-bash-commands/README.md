# Main Bash Commands

## pwd

- `pwd` means _Print Working Directory_.
- Everything in Linux is a file.
- The `/` (_root directory_) has many folders and files which you can store more folders and files.

```
/
| - bin
|   |-- file1
|   |-- file2
|-- etc
|   |-- file3
|   `-- directory1
|       |-- file4
|       `-- file5
|-- home
|   |-- guilhermerodz
|       |-- Documents
|-- var
```

### Example input & output:

```sh
$ pwd

/home/guilhermerodz/Documents
```

## cd

- `cd` means _Change Directory_.
- There are two **different ways** to specify a path:
  - **Absolute path**
    - The entire path from the root directory.
    - Path starts with `/`
    - Usage example: `cd /home/guilhermerodz/Documents`.
  - **Relative path**
    - The relative path from the current working directory. I mean, where you are currently in filesystem.
    - Path can't start with `/`
    - Usage example: `cd guilhermerodz/Documents` from `/home` dir.

### Example scenario:

```
/
| - bin
|-- etc
|   `-- directory1
|-- home <--- (current directory)
|   |-- guilhermerodz
|       |-- Documents
|-- var
```

### Example input & output:

```sh
$ cd guilhermerodz/Documents && pwd

/home/guilhermerodz/Documents
```

### Some shortcuts to help you out:

- . <--- Current working directory.
- .. <--- Parent directory.
- ~ <--- Home directory.
  - Defaults to your `$HOME` environment variable (e.g. `/home/guilhermerodz`).
- - <--- Previous directory.
  - This will take you to the previous directory you were at.

```sh
$ cd .
$ cd ..
$ cd ~
$ cd -
```

## ls

- `ls` means _List Directories_.
- Useful flags
  - `-a`
    - Includes hidden filenames in the command output.
    - Filenames that start with `.` are hidden.
  - `-l`
    - Shows a detailed list of files in a long format.
    - Detailed informations starting from the left: `file permissions`, `number of links`, `owner name`, `owner group`, `file size`, `timestamp of last modification` and `filename or directory name`.
- Like the other comands, you can combine flags (e.g. `ls -al` for `-a` and `-l`). The order matters, but will not represent any changes in the previous example.

### Example input & output:

In this example, we'll navigate to home (`~`), then run `ls -l`.

```sh
$ cd ~ && ls -l

drwxr-xr-x  2 guilhermerodz guilhermerodz 4096 jul 29 14:33 Desktop
drwxr-xr-x  5 guilhermerodz guilhermerodz 4096 ago 21 15:53 Documents
drwxr-xr-x 11 guilhermerodz guilhermerodz 4096 ago 21 17:44 Downloads
drwxr-xr-x  2 guilhermerodz guilhermerodz 4096 jul 29 14:33 Music
drwxr-xr-x  3 guilhermerodz guilhermerodz 4096 ago 22 21:16 Pictures
drwxr-xr-x  2 guilhermerodz guilhermerodz 4096 jul 29 14:33 Public
drwxr-xr-x  2 guilhermerodz guilhermerodz 4096 jul 29 14:33 Templates
drwxr-xr-x  3 guilhermerodz guilhermerodz 4096 jul 31 20:38 Videos
```

## touch

The `touch` command can be used for:

- Creating a new empty file.
- Updating the timestamp of a non-empty file.

There are many other ways to create files that involve other things like redirection and text editors.

### Example input & output:

```sh
$ touch my-empty-file.txt
```

And boom, new file!

<<<<<<< HEAD

## file

> In Linux, filenames aren’t required to represent the contents of the file. You can create a file called funny.gif that isn’t actually a GIF.

Use this command to find out what kind of file a file is. It will show you a description of the file's contents.

### Example input & output:

```sh
$ file .bashrc .zshrc

.bashrc: ASCII text
.zshrc:  UTF-8 Unicode text
```

## cat

The `cat` command (short for con**cat**enate) not only displays file contents but it can combine multiple files and show you the output of them.

### Example input & output:

```sh
$ echo "Hello World" > hellofile
$ echo "Foo Bar" > foofile
$ cat hellofile foofile

Hello World
Foo Bar
```

## less

> If you are viewing text files larger than a simple output, less is more.

- The text is displayed in a paged manner, so you can navigate through a text file page by page.
- Once you're in the `less` command, you can actually use other keyboard commands to navigate in the file.
  - `q` - Used to quit out of less and go back to your shell
  - `page up`, `page down`, `up` and `down` - Navigate using the arrow keys and page keys.
  - `g` - Moves to beginning of the text file.
  - `G` - Moves to the end of the text file.
  - `/search` - You can search for specific text inside the text document. Prefacing the words you want to search with /
  - `h` - If you need a little help about how to use less while you’re in less, use help.

### Example input & output:

```sh
$ echo "Hello World" > hellofile
$ echo "Foo Bar" > foofile
$ cat hellofile foofile

Hello World
Foo Bar
```

### Fun fact

`less` commands are based on `more` and `vi`.

Timeline:

```
vi 1976
 | \      more 1978
 |  \     /
 |   \   /
 |     v
 |   less 1983
 v
vim 1991
```

### Vim

`vim`, by Bram Moolenaar, was also inspired by `vi`.

## history

> In your shell, there is a history of the commands that you previously entered, you can actually look through these commands.

- A `history` shortcut is `Ctrl + R`, this is the reverse search command.

### Usage:

```sh
$ history
```

Our terminal is getting a little cluttered no? Let's do a little cleanup.

```sh
$ clear
```

## cp

> Much like copy and pasting files in other operating systems, the shell gives us an even simpler way of doing that.

- `cp` means _Copy_.
- You can copy multiple files and directories as well as use wildcards. A wildcard is a character that can be substituted for a pattern based selection, giving you more flexibility with searches. You can use wildcards in every command for more flexibility.
  - `*` used to represent all single characters or any string.
  - `?` used to represent one character
  - `[]` used to represent any character within the brackets

### Example scenario:

```
/
| - bin
|-- etc
|   |-- directory1
|-- home
|   |-- guilhermerodz
|       |-- Pictures
|       |-- Downloads <--- (current directory)
|           |-- image1.jpg
|           |-- image2.jpg
|           |-- image3.jpg
|-- var
```

### Example input:

```sh
$ cp *.jpg ../Pictures
```

This will copy all files with the `.jpg` extension in your current directory to the `../Pictures` directory.

**Note: the `-r` flag will recursively copy the files and directories within a directory (_deep copy_).**
**Note: the `copy` command will overwrite files if needed. To avoid mistakes, you can use the `-i` (interactive) flag to prompt you before overwriting a file.**

## mv

Used for moving files and also renaming them. Similar to cp in terms of `flags` and `functionality`.

- `mv` means _Move_.

### Example inputs & outputs:

You can rename files like this:

```sh
$ mv oldfile newfile
```

Or you can actually move a file to a different directory:

```sh
$ mv file2 /home/pete/Documents
```

And move more than one file:

```sh
$ mv file_1 file_2 /somedirectory
```

You can rename directories as well:

```sh
$ mv directory1 directory2
```

Like `cp`, if you `mv` a file or directory it will overwrite anything in the same directory. So you can use the `-i` flag to prompt you before overwriting anything.

```sh
mv -i directory1 directory2
```

Let’s say you did want to `mv` a file to overwrite the previous one. You can also make a backup of that file and it will just rename the old version with a `~`.

```sh
$ mv -b directory1 directory2
```

## rm

Used to delete files and directories.

- `rm` means _Remove_.
- **Take caution when using `rm`, there is no magical trash can that you can fish out removed files. Once they are gone, they are gone for good, so be careful.**

### Example inputs & outputs:

If you don’t care about any of that, you can absolutely remove a bunch of files.

```sh
$ rm -f file1
```

`-f` or force option tells `rm` to remove all files, whether they are write protected or not, without prompting the user (as long as you have the appropriate permissions).

Adding the `-i` flag like many of the other commands, will give you a prompt on whether you want to actually remove the files or directories.

```sh
$ rm -i file
```

You can’t just `rm` a directory by default, you’ll need to add the `-r` flag (recursive) to remove all the files and any subdirectories it may have.

```sh
$ rm -r directory
```

You can remove a directory with the `rmdir` command.

```sh
$ rmdir directory
```

## find

Used for searching files in the specified directory.

### Example inputs & outputs:

If you don’t care about any of that, you can absolutely remove a bunch of files.

```sh
$ find /home -name puppies.jpg
```

With `find` you’ll have to specify the directory you’ll be searching it, what you’re searching for, in this case we are trying to find a file by the name of `puppies.jpg`.

You can specify what type of file you are trying to find:

```sh
$ find /home -type d -name MyFolder
```

You can see that I set the type of file I’m trying to find as `d` (directory) and I’m still searching by the name of `MyFolder`.

**Note: `find` doesn’t stop at the directory you are searching, it will look inside any subdirectories that directory may have as well.**

## help

Provides help for other bash commands.

### Example input:

```sh
$ help echo
```

Some commands don't offer a `help` flag by default, for example:

```sh
$ echo --help
```

## man

> Man pages are manuals that are by default built into most Linux operating systems. They provide documentation about commands and other aspects of the system.

You can see the manuals for a command with the `man` command.

### Example input:

```sh
$ man ls
```

This will run `less` in order to view the `ls` command manual.

## whatis

Provides a brief description of command line programs.

- The description gets sourced from the `manual` page of each command.

### Example input & output:

```sh
$ whatis cat

cat (1) - concatenate files and print on the standard output
```

## alias

> Sometimes typing commands can get really repetitive, or if you need to type a long command many times, it’s best to have an alias you can use for that.

### Example input:

```sh
$ alias foobar='ls -la'
```

Now instead of typing `ls -la`, you can type `foobar` and it will execute that command, pretty neat stuff.

**Note: Keep in mind that this command won't save your alias after reboot, so you'll need to add a permanent alias in: `~/.bashrc`**

You can remove aliases with the unalias command:

```sh
$ unalias foobar
```

## exit

To exit from the shell:

```sh
$ exit
```

Or the logout command:

```sh
$ logout
```

If you are working out of a terminal GUI, you can just close the terminal.
