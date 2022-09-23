## sed: non-interactive editor

`sed` is a **s**tream-oriented **ed**itor. It interprets a script and performs actions on the script. `sed` like many Unix programs, input flows through the program and is directed to standard output. `sed` commands have the general form:

```zsh
sed [options] `command` file(s)
sed [options] -f scriptfile files(s)
```
**Typical uses of `sed` include:**

* Editing one or more files automatically
* Simplifying repetitive edits to multiple files
* Writing conversion programs

Examples usage:

```zsh
sed --help
sed s/BSD// < ~/cli_workshop/data_files/operatingsystemlist
sed s/BSD//g < ~/cli_workshop/data_files/operatingsystemlist 
sed s/BSD//g < ~/cli_workshop/data_files/operatingsystemlist > nobsdlist
sed -n '/BSD/ p' ~/cli_workshop/data_files/operatingsystemlist
```
