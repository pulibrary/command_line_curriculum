## gzip, gunzip, zcat: Compress and uncompress files

The `gzip`, `gunzip`, and `zcat` commands are used to compress files. One can use `tar` with the `-z` option to invoke `gzip`. `gzip` will compress a file, `gunzip` will uncompress it and `zcat` will allow you to review the contents of the `gzip`ped files.

We can compress the contents of our Desktop like we did with the tar command:

```bash
cd ~
gzip --help
```
From the `gzip` manual we will use the `-c` and `-r` flags below:

```bash
gzip -c -r ~/cli_workshop/data_files/ > /tmp/data_files.gz
```

You can compare the sizes of the `tar`red file and the `gzip`ped one using `ls`. 

Let's review the contents of the file using `zcat` by piping that into `less`

```bash
zcat /tmp/data_files.gz | less
```

Finally you can send this file much easier to another user who will open it using.

```bash
gunzip /tmp/data_files.gz
```

[More on gzip](https://www.rootusers.com/11-simple-gzip-examples/)