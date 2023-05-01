## tar: File-Archive Tool

`tar` was originally designed for archiving files to tape. It is still useful however in moving entire directory structures between systems.

The format of the `tar` command is:

```bash
tar options directory
```
Tar unlike most Unix commands does not require the `-` before the options. Here are some your instructor uses frequently.

* `c` : Create an archive
* `x` : Extract files from an archive
* `p` : Attempt to save file permission and ownership information
* `v` : Verbose mode
* `t` : Test the archive
* `f` : Use a tar file 
* `z` : compress the file using (gzip(1))

As an example let's create a tar file of everything under ~/Desktop.

```bash
cd ~
tar cvpf /tmp/command_line_curriculum.tar ~/command_line_curriculum/
```
This file can then be shared and untarred with

```bash
tar xvpf /tmp/command_line_curriculum.tar 
```
on another computer and have the same contents.
