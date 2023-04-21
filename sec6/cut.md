## cut: remove sections of a file

The format for the `cut` command is:

```bash
cut options directory
```

Example usage:

```bash
cat ~/cli_workshop/data_files/cut_example.txt
```
you will get output like this:

```bash
tr command for translations.
du command for disk usage
ls command is an interactive calculator
wc command lists number of lines
```


```bash
cat --help
```

```bash
cut -c4 ~/cli_workshop/data_files/cut_example.txt
```

you will get output like this:

```bash
c
c
c
c
```

this extracts only a desired column from a file using the `-c` option.

```bash
cut -c4-6 ~/cli_workshop/data_files/cut_example.txt
```
you will get output like this:

```bash
com
com
com
com
```