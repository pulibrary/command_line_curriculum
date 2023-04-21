## awk: Pattern scanning and processing

The `awk` command allows for complex pattern scanning and processing. `awk` is an entire programming language allowing complex interpreted programs. One of its most powerful features is the print function to reformat the output of other commands. This is the form we will focus on for this section. It uses the following format:

```bash
awk [ -Fcolumn_separator] '{print format_string}'
```
where column\_separator is the character separating columns in the input and format\_string is the new format of the output. By default, the column separator is a space or a tab character. The variables `$1`, `$2`, ... are output fields to put in the format string.

Example use:

```bash
date
```
which will have output like this:

```bash
Fri Apr 21 04:35:19 PM UTC 2023
```

```bash
date | awk '{print $2 $3}'
```
which will have output like this:

```bash
Apr21
```

```bash
date | awk '{ print $2" "$3}'
```
which will have output like this:

```bash
Jul 28
```

```bash
who
```
which will have output like this:

```bash
pulsys   pts/0        2023-04-21 16:35 (172.20.217.223)
```

```bash
who | awk '{print $1}'
```
which will have output like this:

```bash
pulsys
```