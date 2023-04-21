## sort: sort files

The `sort` command sorts infomation in files. We've already used it in the workshop but we will look at it in more detail as a filter. Until now we've used it generically but sort uses this format

```bash
sort [ - bdfnrtx ] [ +pos1 [ -pos2] ] [ -T directory ] [ name ]
```
By default, sort orders the entire lines starting in the first column. This is how we have used it until now. `sort` is used most frequently by your instructor in the following ways:

* `-b` : Ignore leading blanks
* `-d` : Only letters, digits and blanks are significant in comparisons.
* `-f` : Not case-sensitive
* `-n` : Sort in numeric order
* `-r` : Sort in descending order
* `-k` : Restrict a sort key that has the starting position field1, and optional ending position field2 of a key field.

Example Usage:
We have a an example of list with Operating Systems separated by tab characters.

```bash
cd ~
cat ~/cli_workshop/data_files/operatingsystemlist
```
you will see output like this:

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

Compare the output after we sort it with the following command:

```bash
sort -r -k2 ~/cli_workshop/data_files/operatingsystemlist
```
