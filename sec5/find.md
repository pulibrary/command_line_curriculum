## find: Locate a file in a directory tree

The `find` command is useful for searching for a file when you do not know where in the directory it is located. To search the format for the command is:

```bash
find directory-name commandlist
```
The most common but hardly exhaustive comandlist arguments that your instructor uses are:

* `-name filename` : Look for files with that name
* `-user username` : Look for files owned by that user
* `-perm permission` : Look for files with a certain permission
* `-atime days` : Look for files accessed within a certain number of days
* `-mtime days` : Look for files modified withing a certain number of days
* `-size blocks` : File size of 512 byte blocks
* `-a` : And two conditions
* `-o` : Or two conditions

Once the file is located one can either:

* `-print`: Print full pathname when the file is found
* `-exec command`: Execute a Unix command on that file. The end of the command is marked with a `";"` The brackets `"{ }"` are replaced by the name of the file. 

To list all files greater that 51200 bytes in the `data_files` directory:

```bash
find ~/cli_workshop/data_files/ -size +100 -print
```
We can run the same command but instead of printing execute `ls -lF` on all files:

```bash
find ~/cli_workshop/data_files/ -size +100 ls -lF "{}" ";"
```
Some symbols, such as `";"`, `"("`, `")"`, and `"*"`, are needed for `find`, and must be put in quotes. If they are not put in double quotes, the shell will interpret them instead of the `find` command. 

To remove all files in my home directory that have "core dumped"

```bash
find ~ -name core -exec rm "{ }" ";"
```
To use the `-o` and `-a` flags, the conditions must be in parenthesis. To remove all files in my home directory named a.out or core that haven't been accessed within 10 days:

```bash
find ~ "(" -name a.out -o -name core ")" -atime +10 exec rm "{ }" ";"
```
More examples:

```bash
find --help
find ~ -name "*.csv" -type f
find ~ -type f -not -name libraryfines.csv
find ~ -name "cli_workshop" type -d
```
Find uses up quite a bit of memory and CPU if you traverse outside your home directory. There's other tools that help with this which we will meet later.

A reimplementation of find is [fd-find](https://github.com/sharkdp/fd) which can be installed by doing this:

```bash
sudo apt install fd-find
```