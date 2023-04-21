## tee: add output to file

The `tee` command takes the format of:

```
tee [ -a ] [ File ]
```

The following command only displays output on the screen (stdout)

```bash
pwd
```

will display output like this: (matching your selected username)

```bash
/home/pulsys
```

The same command directs the output to a file

```bash
pwd > file
cat file
```
you will see output like this: (matching your selected username)

```bash
/home/pulsys
```
By using a pipe to `tee` we can display on stdout _AND_ direct to a file

```
pwd | tee file.txt
```
you will see output like this: (matching your selected username)

```bash
/home/pulsys
```