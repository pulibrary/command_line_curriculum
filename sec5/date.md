## date: Display or Set Current Date

The format for the `date` command is:

```bash
date [ -u ] [ yymmddhhmm [ .ss] ]
```
The comman `date` without any options displays the current date and time. As super user using `sudo` you can change the time using the `--set` flag.

Example usage:

```bash
date --help
date 
sudo date --set "4 AUGUST 2016 1:40 PM"
```