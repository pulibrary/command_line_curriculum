## echo: print a line

The format of the `echo` command is:

```bash
echo [ -n ] [ arg ] ...
```

Echo writes its arguments separated by blanks and terminated by a newline on the standard output. If the `-n` flag is used, no newline is added to the output.

Example usage:

```bash
echo print this line of text to standard output
echo -n print this line with the flag
```

It is often used with redirects to create or modify files:

```bash
echo --help
echo -e "1,a\n2,b\n3,c" > file.csv
sudo echo "pulsys ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
```