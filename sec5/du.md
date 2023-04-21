## du: Disk usage

The `du` command tells us how much disk space is used by files. The format of the `du` command is:

```bash
du [options] directoryname
```
`du` without any options will show you the amount of space in each subdirectory and the total disk usage. This is useful when trying to locate unneccessary and large files in your directory. These results using pipes can be saved as a list of the largest files.

```bash
du --help
du -h ~/Desktop
du -sh ~ | sort -n > ~/diskusage
```

You can install a reimplementation of du on your VM with the following commands:

```bash
sudo deb-get install du-dust
```

The `dust` application can be used like this as shown on the [Github Repository](https://github.com/bootandy/dust):

```bash
Usage: dust
Usage: dust <dir>
Usage: dust <dir>  <another_dir> <and_more>
Usage: dust -p (full-path - Show fullpath of the subdirectories)
Usage: dust -s (apparent-size - shows the length of the file as opposed to the amount of disk space it uses)
Usage: dust -n 30  (Shows 30 directories instead of the default [default is terminal height])
Usage: dust -d 3  (Shows 3 levels of subdirectories)
Usage: dust -D (Show only directories (eg dust -D))
Usage: dust -F (Show only files - finds your largest files)
Usage: dust -r (reverse order of output)
Usage: dust -H (si print sizes in powers of 1000 instead of 1024)
Usage: dust -X ignore  (ignore all files and directories with the name 'ignore')
Usage: dust -x (Only show directories on the same filesystem)
Usage: dust -b (Do not show percentages or draw ASCII bars)
Usage: dust -i (Do not show hidden files)
Usage: dust -c (No colors [monochrome])
Usage: dust -f (Count files instead of diskspace)
Usage: dust -t (Group by filetype)
Usage: dust -z 10M (min-size, Only include files larger than 10M)
Usage: dust -e regex (Only include files matching this regex (eg dust -e "\.png$" would match png files))
Usage: dust -v regex (Exclude files matching this regex (eg dust -v "\.png$" would ignore png files))
Usage: dust -L (dereference-links - Treat sym links as directories and go into them)
Usage: dust -P (Disable the progress indicator)
Usage: dust -R (For screen readers. Removes bars/symbols. Adds new column: depth level. (May want to use -p for full path too))
Usage: dust --skip-total (No total row will be displayed)
Usage: dust -z 4000000 (Exclude files below size 4MB)
```