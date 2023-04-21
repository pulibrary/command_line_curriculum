## grep: Search for a keyword

All commands in the `grep` family search a file or files for a pattern. The format used by grep is:
```bash
grep [ option ] ... expression [ file ] ...
egrep [ option ] ... expression ] [ file ] ...
fgrep [ option ] ... [ strings ] [ file ] ...
```
Each line found that matches the pattern is sent to standard output. `grep` patterns are limited regular expressions. `egrep` also `grep -E` patterns are full regular expressions. `fgrep` also `grep -F` patterns are fixed strings. 

The options your instructor has used the most over the years are:

* `-c` : Only the number of matching lines is printed
* `-i` : not case sensitive.
* `-l` : Names of the files with matching lines are listed
* `-n` : Each line is preceded by the line number in the file
* `-x` : on `fgrep` only lines matched in their entirety are printed
* `-v` : All lines but those matching

Regular expressions are a class on their own. What follows are some of the symbols used in the `grep` group of tools:

* `x`		: Single character `x` matches on that character
* `\x` 	: Matches on single character `x` even if `x` is a special symbol
* `^`		: Matches beginning of the line
* `$`		: Matches the end of the line
* `.`		: Matches a single character
*  `[s]`	: Matches any character in the string `s`
*  `re*`	: Zero or more matches of the regular expression `re`
*  `re+`	: One or more matches of the regular expression `re`
*  `re?`	: Matches zero or one occurrence of the regular expression `re`
*  `(re)`	: Parentheses to enclose a regular expression

These special characters must be in quotes or the shell will interpret the special symbols instead of `grep`

`*`,`+`,`?`,`|`,`()`,`[]`,`$`,`\`,`^`

Example usage:

```bash
cd ~
cat cli_workshop/data_files/operatingsystemlist
```
you will get this output:

```bash
OpenBSD     BSD             2016-03
FreeBSD     BSD             2016-04
NetBSD      BSD             2015-09
Dyson       Illumos         2015-07
SmartOS     Illumos         2016-07
OpenIndiana Illumos         2016-04
Debian      Linux           2016-06
Centos      Linux           2016-02
Gentoo      Linux           2016-07
```

Show all lines that have BSD:

```bash
grep --help
```
From reading the help menu you will see the `-F` flag which we will use:

dritchie@cliwkshp:~$ grep -F BSD cli_workshop/data_files/operatingsystemlist
OpenBSD     BSD             2016-03
FreeBSD     BSD             2016-04
NetBSD      BSD             2015-09
```

Show all lines that do not have BSD:

```bash
grep -F -v BSD cli_workshop/data_files/operatingsystemlist
```
you will see the following results:

```bash
Dyson       Illumos         2015-07
SmartOS     Illumos         2016-07
OpenIndiana Illumos         2016-04
Debian      Linux           2016-06
Centos      Linux           2016-02
Gentoo      Linux           2016-07
```

Show all occurences of a single character, followed by an `e`, followed one or more occurences of an `n`:

```bash
grep -E '.en+' cli_workshop/data_files/operatingsystemlist
```
you will see the following results:

```bash
OpenBSD     BSD             2016-03
OpenIndiana Illumos         2016-04
Centos      Linux           2016-02
Gentoo      Linux           2016-07
```

Show all occurences of an `l` follow by zero or more `l's`

```bash
grep -E 'll*' cli_workshop/data_files/operatingsystemlist
```
you will see the following results:

```bash
Dyson       Illumos         2015-07
SmartOS     Illumos         2016-07
OpenIndiana Illumos         2016-04
```
Show all strings that have an `n` or an `o` in them.

```bash
grep -E '[no]' cli_workshop/data_files/operatingsystemlist
```
you will see the following results:

```bash
OpenBSD     BSD             2016-03
Dyson       Illumos         2015-07
SmartOS     Illumos         2016-07
OpenIndiana Illumos         2016-04
Debian      Linux           2016-06
Centos      Linux           2016-02
Gentoo      Linux           2016-07
```

[More on `grep`](http://www.thegeekstuff.com/2009/03/15-practical-unix-grep-command-examples/)