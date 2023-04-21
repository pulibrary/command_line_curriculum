## ssh: Log in to Another System

The command `ssh` allows you to log into another system. The format is

```bash
ssh [ options ] hostname
```
The ssh command comes with many features and options. Once this command is executed, it is equivalent to connecting to a computer via a terminal connection. The `ssh` session ends once the user disconnects. 

Some Example Use:

 1. `ssh -J pulsys@bastion-host pulsys@protected-internal-host`. # allows connection to a server behind a bastion location
 1. `ssh -L 8080:localhost:80 pulsys@tunneled-host` # allows one to open a tunnelled connection on port `8080` to on a remote host that has port `80` available