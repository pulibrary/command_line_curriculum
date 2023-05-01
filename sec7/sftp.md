## sftp: Secure File Transport Protocol

`sftp` is the secure method for transferring files between computers. If security doesn't matter most of the commands used in this section can be used with `ftp`. The format of the `sftp` command is:

```bash
sftp hostname
```
Once connected to the remote machine, `sftp` prompts for a login name and password on the remote. Some of the possible functions are:

* `bye` : End session
* `cd remotedirectory`: Change the directory on the remote machine
* `get filename`: Copy a file from remote machine to local machine
* `help` : Print help
* `lcd localdirectory` : Change the directory on the local machine
* `ls`: List files on the remote machine
* `mget remotefiles` : Multiple get. 
* `mkdir remotedirectory` : Make a directory on the remote machine
* `mput localfiles` : Puts multiple files on the remote machine
* `put localfile`: Puts localfile on remote machine
* `pwd`: Print working directory on remote machine
* `quit`: Same as bye
