## Files and Directories

File paths that start with a forward slash / are absolute, fully determining the location of a file or a folder. We can also use relative paths relative to the location of the working directory. Such paths start with one or two dots, pointing to the current or parent directory. The tilde expansion provides quick access to the home directories when the path starts with ~. See the table below:

| path| comment |
| --- | --- |
| */* | the root directory of the file system |
| . | the current working directory |
| .. | the parent directory of your current working directory |
| ~ | the home directory of the current user |
| ~username | the home directory of `username` |





### File commands

#### home directory ( ~ )

The shell starts your session from a special directory called your home directory.  The tilde (~) character can be used as a shortcut to your home directory. Thus, when you log in, you probably see the command prompt telling you you’re in your home directory:

```bash
pulsys@sandbox-tw8766 ~$ 
```
These prompts are not universal. Our prompt shows the username and the name of the computer as well but there are instances that look like this:

```bash
➜  ~
```

#### absolute pathnames

In Unix, all pathnames can be absolute of relative. Absolute means to start from the root directory. Absolute pathnames start with a beginning `/` such as `/usr/bin/who` With absolute filenames, the entire directory path is specified starting with the root directory.

#### relative pathnames

Relative pathnames start from the beginning of a directory that you are currently located. These pathnames do not begin with a `/` For example in the previous example if you were in the `/usr` directory, the relative path name to run the who command is `bin/who`
Specifying `../` within a filename goes up one directory. From the the `/usr/bin` directory the who command would be run with `../bin/who`.
The symbol `~` always refers to your home directory.

#### ls: Listing Files

The `ls` command lists the files in your directory. The format of this command is:

```bash
ls [options] filenames(s)
```

For each filename listed, if it is a file, information about that file is displayed. If the filename is a directory, information about all the files and subdirectories are displayed.

The `ls` command has many options associated with it. Take a look at some of them by typing:

```bash
pulsys@sandbox-tw8766 ~$ ls --help
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.
...
```
The `ls` (list) command is used to show directories and
files. It is similar to the DIR command in Windows Command Prompt.

```bash
pulsys@sandbox-fkayiwa:~/command_line_curriculum$ ls
environment.md  images  LICENSE  login.md  plan.md  README.md
```

To see a more detailed listing of the files and directories, you can use
the ls -l command, as shown below:

```bash
pulsys@sandbox-fkayiwa:~/command_line_curriculum$ ls -l
total 36
-rw-rw-r-- 1 pulsys pulsys 4903 Aug 19 12:12 environment.md
drwxrwxr-x 2 pulsys pulsys 4096 Aug 19 12:12 images
-rw-rw-r-- 1 pulsys pulsys 1536 Aug 19 12:12 LICENSE
-rw-rw-r-- 1 pulsys pulsys 8799 Aug 19 12:12 login.md
-rw-rw-r-- 1 pulsys pulsys 1366 Aug 19 12:12 plan.md
-rw-rw-r-- 1 pulsys pulsys 1349 Aug 19 12:12 README.md
```

From left to right, you see file permissions, owner, group, size, last
modified date, and finally the file or directory name. File permissions
are beyond the scope of this intro to the CLI, but as you continue your CLI Linux
education we will visit them. 

In Windows, a file is hidden by setting a file attribute (metadata) on
the file. In Linux, a file is hidden if its name starts with a period, or
dot. To show these dot files, you use the `ls -a` command shown below:

```bash
pulsys@sandbox-fkayiwa:~/command_line_curriculum$ ls -a
.  ..  environment.md  .git  .gitignore  images  LICENSE  login.md  plan.md  README.md
```

On the left you see . and .., which mean *current directory* and *parent directory*, respectively, just as in Windows. You also see
previously hidden files such as .gitignore and the .git directory

Finally, you can combine parameters. If you want to see a detailed
listing (-l) of all files (-a), recursively descending into every
child directory (-R), you simply combine them all (ls -alR), as
shown below:

```bash
pulsys@sandbox-fkayiwa:~/command_line_curriculum$ ls -alR
.:
total 52
drwxrwxr-x 4 pulsys pulsys 4096 Aug 19 12:12 .
drwxr-xr-x 7 pulsys pulsys 4096 Aug 19 12:12 ..
-rw-rw-r-- 1 pulsys pulsys 4903 Aug 19 12:12 environment.md
drwxrwxr-x 8 pulsys pulsys 4096 Aug 19 12:12 .git
-rw-rw-r-- 1 pulsys pulsys   26 Aug 19 12:12 .gitignore
drwxrwxr-x 2 pulsys pulsys 4096 Aug 19 12:12 images
-rw-rw-r-- 1 pulsys pulsys 1536 Aug 19 12:12 LICENSE
-rw-rw-r-- 1 pulsys pulsys 8799 Aug 19 12:12 login.md
-rw-rw-r-- 1 pulsys pulsys 1366 Aug 19 12:12 plan.md
-rw-rw-r-- 1 pulsys pulsys 1349 Aug 19 12:12 README.md

./.git:
total 52
drwxrwxr-x 8 pulsys pulsys 4096 Aug 19 12:12 .
drwxrwxr-x 4 pulsys pulsys 4096 Aug 19 12:12 ..
drwxrwxr-x 2 pulsys pulsys 4096 Aug 19 12:12 branches
-rw-rw-r-- 1 pulsys pulsys  277 Aug 19 12:12 config
-rw-rw-r-- 1 pulsys pulsys   73 Aug 19 12:12 description
...
...
```

Some of the most useful ones are:

* `-l`: Prints detailed information about each file. It shows the following information:
  1. File protection for each file (read, write and execute permissions for the owner of the file, people in the same group and the anyone else
  2. Number of files in the subdirectory (if it is a subdirectory)
  3. Owner of the file
  4. Size of the file in bytes
  5. Date the file was last modified
  6. Name of the file
* `-t`: Lists the files in the order of modification date
* `-g`: Shows what group owns the file (we will see `chmod` later for more details)
*  `-a`: Shows hidden files in addition to regular files.

Just like `bat` before there is a modern replacement for `ls` called `exa` which adds Extended attributes, git and tree (more below on this) support as it's features. It can be [installed](https://the.exa.website/) on our Ubuntu VM with 

```bash
sudo apt -y install exa
```


#### cat more or less: Show file contents

The `cat`, `more` and `less` commands can be used to show the contents of a file on your terminal screen. To show the contents of the `/etc/fstab` file you can do any one of the following:

```bash
pulsys@sandbox-tw8766 ~$ cat /etc/fstab
```
or

```bash
pulsys@sandbox-tw8766 ~$ more /etc/fstab
```
or

```bash
pulsys@sandbox-tw8766 ~$ less /etc/fstab
```
On files smaller than your screen `cat` and `more` work the same way; they differ on how they display files longer than the length of your terminal. 

A `cat command_line_curriculum/data_files/22631-0.txt` will display the entire contents of the file on your screen at once. `less` is modeled on `more` which is an earlier implementation. However, more has fewer features, and you probably shouldn’t bother with it. So, always remember: *less is more*.

There's a new implementation of `cat` (short for concatenate) written in the [Rust](https://www.rust-lang.org/) called `bat`. It adds the following possibly useful features of Syntax Highlighting, Git Integration, Automatic paging into `less` which would make the example of reading the `Gutenberg` more "manageable". It can be [installed using](https://github.com/sharkdp/bat) using your Operating System's package manager. In the case of our Ubuntu VM:

```bash
sudo apt -y install bat
```

#### cp: Copy Files

The `cp` command copies files. The Format of the `cp` command is:

```bash
cp [options] from-file(s) to-file
```
or

```bash
cp [options] from-file(s) to-directory
```

The first one copies files within the same directory while the second one copies files into another directory. Let's look at the manual for the `cp` command:

```bash
pulsys@sandbox-tw8766 ~$ man cp
```

These are the frequent based on the `history` of the creator of this repo is:

* `-r`: Recursive. Will recursively copy the files in all the subdirectories.
* `-i`: Interactive. If copying the file, it will overwrite an old version of a file. The `-i` option asks if you want to do the copy. Without the option, it would overwrite the file without asking.
* `-p`: Preserve the permission modes and modification times of the files.

Let's make a few copies of the document by launching our terminal.

```bash
pulsys@sandbox-tw8766 ~$ ls
command_line_curriculum
pulsys@sandbox-tw8766 ~$ cp command_line_curriculum/data_files/22631-0.txt .
pulsys@sandbox-tw8766 ~$ ls
22631-0.txt  command_line_curriculum
```
In order we:

1. `ls` listed contents of our directory
2. `cp` copied from a relative location to our current one. The `.` period represents our current directory
3. `ls` listed contents of our current directory to show the change

However, if the destination is in another directory, the named directory must already exist. Otherwise, the cp command will respond with an error:

```bash
pulsys@sandbox-tw8766 ~$ cp command_line_curriculum/data_files/22631-0.txt gutenberg_books/22631-0.txt
cp: cannot create regular file `gutenberg_books/22631-0.txt`: No such file or directory
```

#### mv: Move Files

To move a file instead of copying it, use the `mv` command. The `mv` command can do two things.

1. It can move a file or a directory to another directory
2. It can rename a file of a directory

`mv` uses the following format:

```bash
mv [options] filename to-directoryname
```
or

```bash
mv [options] directoryname to-directoryname
```
or

```bash
mv [options] filename newfilename
```
or

```bash
mv [options] directoryname to-newdirectoryname
```

The directory `to-directoryname` must exist to move the file or directory. If it does not, the `mv` command assumes that you are renaming the file or directory.

These are the frequent `mv` commands the instructor uses:

1. `-i`: Interactive. If moving the file will overwrite a file with the same name without the `-i` option. 
2. `-f`: Force. Overrides any file permissions mode restrictions if you are the owner of the file being overwritten.

Let's change the name of our file to something meaningful. And move it to the `training`

```bash
pulsys@sandbox-tw8766 ~$ mv 22631-0.txt timbuctoo.txt
pulsys@sandbox-tw8766 ~$ mv timbuctoo.txt /tmp/timbuctoo.txt
```

#### rm: Remove Files

Unix handles file removal with the `rm` command. There's no "Trash" stop when this command is run. Very important to remember this.

The format for `rm` is as follows:

```bash
rm [options] filenames(s)
```
Be careful when using the `-r` and `-f` options. 

* `-r`: Recursive. Recursively removes all the files and directories
* `-i`: Interactive. Will ask for each file before removing it
* `-f`: Force. Will override any file permissions mode restrictions if you are the owner of the file being removed.

Let's delete a file. Do the following:

```bash
touch /tmp/password.txt
```
Find out the synopsis of what touch is by:

```bash
man touch
```


```bash
pulsys@sandbox-tw8766 ~$ ls -l /tmp/
...
-rw-rw-r-- 1 pulsys pulsys    9 Jul 17 13:18 password.txt
pulsys@sandbox-tw8766 ~$ rm -i training/password.txt
```


### File Protection

You can specify the permission of a file or directory:

1. `r`: Read permission
2. `w`: Write permission
3. `x`: Execute permission

|  *Permission* |  *File* | *Directory*  |
|---|---|---|
| `r`  |  Read the file |  List files in Directory |
|  w |  Rewrite or remove file |  Remove any file in directory. Put a file in the directory. Remove the directory itself. |
|  x |  Run executable program |  Read, write or execute any files in the directory |

These permissions can be specified for each of the following categories:

1. `u`: The user - owner of the file
2. `g`: All members in the same group as the owner of the file
3. `o`: Other people
4. `a`: All of the above

The `ls -l` command shows these permissions in order by user, group and others:

```bash
pulsys@sandbox-tw8766 ~$ ls -l
total 928
-rw-rw-r-- 1 pulsys pulsys 927212 Jul 20 13:17 22631-0.txt
drwxrwxr-x 4 pulsys pulsys   4096 Jul 19 18:35 command_line_curriculum
drwx------ 2 pulsys pulsys   4096 Jul 17 17:38 training
```
The user `pulsys` has read, write on the `22631-0.txt` 

#### chmod: Change File Permissions Modes

The `chmod` command is used to change your file or directory permission mode. The format of the `chmod` command is:

```bash
chmod mode filename
```
The mode consists of:

```bash
Category + permission to add permission, or
Category - permission to remove permission
```

For example:

```bash
pulsys@sandbox-tw8766 ~$ chmod o+w 22631-0.txt
pulsys@sandbox-tw8766 ~$ chmod g-w 22631-0.txt
```
The first command adds write permissions to anyone `22631-0.txt` and the second one removes write permissions to the `pulsys` group.

Another form of the `chmod` command allows an octal number to be used for the mode. This number has the values:

|  *Value* |  *Meaning* |
|---|---|
|  4 |  Read permission allowed |
|  2 |  Write permission allowed |
|  1 |  Execute permission allowed |

A value of six (4+2) allows read and write permission. A value of five (4+1) allows read and execute permission. The numeric form for the mode of the `chmod` command has three digits for:

1. Permission for the owner of the file or directory
2. Group permission of the file or directory
3. Permission for anyone on the system

For example the command:

```bash
pulsys@sandbox-tw8766 ~$ chmod 700 22631-0.txt
```

changes the `22631-0.txt` to be executable by the user `pulsys` and no other user can do anything with the file.

#### chown: Setting Ownership

In multiuser systems it is often helpful to open file permissions up to other users on a filesystem. Suppose Pul Sys, wants to give all Princeton University Library access to read and write to the file, `22631-0.txt`. If those users are all part of a group called `pulibrary`, then he can give them those permissions by changing the group ownership of the file. He can handle this task with:

```bash
pulsys@sandbox-tw8766 ~$ chown :pulibrary  22631-0.txt
```


### Directory Commands

In order to logically organize under your home directory, Unix allows you to create subdirectories and put files in them. Let's look at the structure of your home directory.

```bash
pulsys@sandbox-tw8766 ~$ tree
```

The `tree` command will list contents of directories in a tree-like format. It is a recursive directory listing program that produces a depth indented listing of files. (If not available can be installed with the step below)

```bash
sudo apt -y install tree
```

#### cd: Change Directory

On login, you are usually in the home directory, which is represented
by ~. It is similar to the user directories under C:\Users on
Windows. Hence, you will probably need to go elsewhere. Here’s a list of
common directories on Linux systems that are of

`/etc` System configuration files (often pronounced slash-et-see
if someone is instructing you what to do over the phone)

`/var` Installed software generally writes here by default

`/var/log` Log files 

`/proc` Real-time system information -- similar to Windows Management Instrumentation (WMI) but easier ;-)

`/tmp` Temporary files that are wiped by a reboot

The `cd` command changes the current directory where you are located. It uses the format


```bash
cd directoryname
```

If no `directoryname` is specified your current directory becomes your home directory. The `directoryname` can be an absolute or relative path. A few examples are

```bash
pulsys@sandbox-tw8766 ~$ cd
pulsys@sandbox-tw8766 ~$ cd /usr/bin
pulsys@sandbox-tw8766 ~$ cd ~/bin
```

In order the first command takes us to your home directory, the second one takes us to the `/usr/bin` directory and the last one takes us to the `bin` directory under your home. It could also be written as `cd /home/pulsys/bin`

**Be Lazy** 

Most modern interactive shells like our zsh and even Windows Command Prompt allow for tab expansion and command history, at least for the current session of the
shell. This is a good thing in a crisis situation, because it saves you
typing, and thus, time.

Tab expansion is like autocomplete for the command prompt. Let’s say you
have some files in a directory, as shown below:

```bash
pulsys@sandbox-fkayiwa:~/command_line_curriculum$ cd /var/log
pulsys@sandbox-fkayiwa:/var/log$ ls
alternatives.log       dmesg          kern.log.4.gz  ubuntu-advantage.log             vmware-vgauthsvc.log.0
alternatives.log.1     dmesg.0        lastlog        ubuntu-advantage.log.1           vmware-vmsvc.1.log
alternatives.log.2.gz  dmesg.1.gz     mysql          ubuntu-advantage-timer.log       vmware-vmsvc.2.log
alternatives.log.3.gz  dmesg.2.gz     nginx          ubuntu-advantage-timer.log.1     vmware-vmsvc.3.log
apt                    dpkg.log       private        ubuntu-advantage-timer.log.2.gz  vmware-vmsvc.log
auth.log               dpkg.log.1     syslog         ubuntu-advantage-timer.log.3.gz  vmware-vmsvc-root.1.log
auth.log.1             dpkg.log.2.gz  syslog.1       ubuntu-advantage-timer.log.4.gz  vmware-vmsvc-root.2.log
auth.log.2.gz          dpkg.log.3.gz  syslog.2.gz    ubuntu-advantage-timer.log.5.gz  vmware-vmsvc-root.3.log
auth.log.3.gz          faillog        syslog.3.gz    unattended-upgrades              vmware-vmsvc-root.log
auth.log.4.gz          journal        syslog.4.gz    upgrade                          vmware-vmtoolsd-root.log
BESClient              kern.log       syslog.5.gz    vmware-network.1.log             wtmp
btmp                   kern.log.1     syslog.6.gz    vmware-network.2.log             wtmp.1
btmp.1                 kern.log.2.gz  syslog.7.gz    vmware-network.3.log
dist-upgrade           kern.log.3.gz  tallylog       vmware-network.log
```
Without tab expansion, typing out something like this is slow and error-prone:

do the following

`cd un`[TAB], where [Tab] represents hitting the Tab key, and because only one directory starts with un, tab expansion will fill in the rest of the directory name for you.

#### mkdir: Make Directories

The `mkdir` command is used to make directories. The format for this is 

```bash
mkdir directoryname
```

To make make a new `command_line_training` directory run the following command:

```bash
pulsys@sandbox-tw8766 ~$ mkdir ~/command_line_training
```

#### pwd: Print Working Directory

The `pwd` command prints out the full pathname of the directory you are currently located.

## Exercises

1. Specify three ways how `pulsys`may go from `/usr/bin` to his home directory. 
1. Using the cp command make a copy of the 22361-0.txt to the `/tmp` directory
1. Instead of using the rm command how can `pulsys` move the 22361-0.txt file to the `/tmp` directory
1. How can `pulsys` change the permission on the 22361-0.txt file so anyone can read it?
1. How can `pulsys` make his Desktop directory so no one except he can read it?

