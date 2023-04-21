## sudo: Execute a command as another user

`sudo` allows a permitted user to execute a command as the superuser or another user, as specified in the sudoers file.  By default, sudo requires that users authenticate themselves with a password (NOTE: by default this is the user’s password, not the root password).

### /etc/sudoers

This file controls who can use the sudo command to gain elevated privileges. It is usually located at /etc/sudoers. The best and safest way to edit this file is by using the `visudo` command. This command will start the OS's default editor with elevated privileges so that you can edit the file and save it. It also will put a filelock on the sudoers file so that no one else can edit it. Once you're done editing it, it will parse the file for simple errors. 

On this VM your the user `pulsys` has all rights.

```bash
sudo --help
sudo -l
visudo
```