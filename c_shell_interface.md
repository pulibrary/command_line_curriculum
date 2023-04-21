# C Shell Interface

The C shell (csh) is the interface to the Unix system and is responsible for interpreting your keyboard input. When you log into a Unix system, the shell is started and runs until your log out of the system. The shell is a powerful program allowing:

1. Connection of the output of one command as input to a second command
1. The output of commands to be sent to files
1. Files as input to commands
1. Multiple command running at the same time
1. Aliasing the names of commands
1. Ease of running commands you have previously executed

## Pipes and File Redirection

### standard input, output and error

Every command has three "files" associated with it called **standard input, standard output**, and **standard error**. Input may read from standard input (keyboard), output may send to standard output (screen), and error messages get sent to standard error (logs, screen). These default devices may be changed using one of the following special shell symbols:

```bash
| | & < > >> >&
```

When you issue a command, the operating system creates what is called a **process** to execute that command. Each process is considered independently by the operating system, so it is possible to have more than one process executing at the same time. 

### file redirection

The C shell interprets the following symbols as the file redirection symbols:

* `<` : Use file as standard input
* `>` : Use file as standard output
* `>>` : Append standard output to the file
* `>&` : Write both standard error and standard output to the file

We can sort the contents of `library-visits.csv` and put the output into a file called `sorted.csv`

```bash
cd ~
sort < cli_workshop/data_files/library-visits.csv > sorted.csv
in2csv cli_workshop/data_files/Evidovane-knihovny.xls > converted_file.csv
```

### pipes

A unix pipe takes the standard output of one process and makes it the standard input of another process. Use of a pipe involves:

```bash
command1 | command2
```
For example in the file redirection section we talked about `sort` and `in2csv` without discussing what they are. Typing `sort --help` and `in2csv --help` for most screens will not be useful. We can solve this by "piping" this to the `less` command:

```bash
sort --help | less
in2csv --help | less
```
pipes are very useful if the standard output of any command produces more lines of output than the size of your terminal. The output can be piped to the `less` command. 

More than one pipe is allowed. To skip CSV header, get 1 column, sort names, get uniq names:

```bash
cd ~
sed '1d' cli_workshop/data_files/libraries-visits.csv | cut -d',' -f 1 | sort | uniq
```

### aliasing command names

The `alias` command redefines the names of Unix commands. The format of the `alias` command is:

```bash
alias newname='command statement'
```
For example instead of typing `ls -al && pwd` which would list all the files in our current working directory we can create an `alias` for that with:

```bash
alias whereami='ls al && pwd'
```
after that every time we type the command `whereami` it would display the same results of the two commands `ls -al` and `pwd`. `alias` is used on commands that a user uses frequently.

### c shell variables

Several variables are associated exclusively with the C shell. Use the `set` command to assign values to these variables. The format of the `set` command is:

```bash
set variable = value
```
Let's see what our current variables look like by running the

```bash
set | less
```
command in our terminal. Let's change our prompt to say `cliwkshp` instead using the following:

### history

Another variable I find useful to set is the `history` variable. The C shell remembers the previous commands you have executed. The `history` variable gives the number of previous commands to remember. We will adjust this to a larger number

```bash
set history = 2000
```

Let's see what commands we have run on the VM

```bash
history
```
### reexuciting commands

There is also the `!` (called the **bang** character) which refers to some previously executed command. Typing `!!` means to execute the previous command again.

Typing

```
!3
```

# Exercises

1. Get the file from `~/cli_workshop/names.txt` and after reading the manual. Sort those names alphabetically.
1. If a user logs into a Unix system and types the following input to the shell, list the commands executed by the shell for each of the history substitutions:

```bash
w
who
ls
!1
cd /tmp
!3
!c
!w
```