## finger: Looking up a Person

The `finger` command is useful for finding out information about a person. The format of this command is:

```bash
finger [ username@hostname ]
```
The `finger` command lists the login name, full name, terminal name, idle time, login time and more included information for an individual user. If nore username is given, information about all the users working on the system is shown. 

The use of `finger` is a relic of the past. There was a time when one could check for ids on different servers. These types of services are generally not offered and have been replaced by tools that are run on a browser.

In fact there are odds it is not installed on your machine. You can install it with 

```bash
sudo apt -y install finger
```

Example usage:

```bash
finger
```
you will see output like this:

```bash
Login     Name          Tty      Idle  Login Time   Office     Office Phone
pulsys    Pul Systems   pts/0          Apr 21 18:38 (172.20.217.223)
```