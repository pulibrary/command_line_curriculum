## rsync: Remote sync

`rsync` is a file transfer program capable of efficient remote update
via a fast differencing algorithm. The basic format of the `rsync` command is:

```bash
rsync [ options ] source destination
```
Some of the commonly used options by your instructor follow:

* `-a`: Archive mode, archive mode allows copying files recursively and it also preserves symbolic links, file permissions, user & group ownerships and timestamps 
* `-r`: Copy data recursively but doesn't preserve time and permissions 
* `-z`: Compress file data
* `-h`: human readable
* `-v`: Verbose.

Example usage:

```bash
cd ~
rsync --help
```
From the `rsync` manual we will use the `-a`, `-z`, `-v`, and `-h` flags:

```bash
rsync -azvh command_line_curriculum/ /tmp/backups/
```
This will synchronize the directory. If you run this command a second time nothing happens. Let's add a new file named `newfile.txt`

```bash
touch command_line_curriculum/newfile.txt /tmp/backups/
rsync -azvh command_line_curriculum/ /tmp/backups/
```
unlike a `cp` command the `rsync` will only send `newfile.txt` to the destination.

[More `rsync` examples](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps)
