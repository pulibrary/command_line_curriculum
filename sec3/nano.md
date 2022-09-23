## nano

`nano` is arguably the editor with the lowest learning curve. It is much younger than emacs and vi and was designed to replace `pico`. When you launch this editor with the command:

```bash
nano
```
if you get an error when you type that. Install the software by running

```zsh
sudo apt -y install nano
```
you will notice at the bottom a short list of common commands needed to edit documents. All of them are preceded by the `^` symbol which represents the `ctrl` key. 

* `ctrl-x` : Exits the editor. If you are editing a file the exit process will ask if you want to save your work
* `ctrl-r` : Read a file in your current working directory
* `ctrl-c` : Display the current cursor position
* `ctrl-k` : Cut text
* `ctrl-o` : Save file and continue working on it
* `ctrl-t` : Perfom spell check 
* `ctrl-w` : Search your text
* `ctrl-a` : Go to the beginning or your current working line
* `ctrl-e` : Go to the end of the current working line
* `ctrl-g` : Get additional help with `nano`

All the editors are powerful enough and I recommend familiarizing yourself with the one that makes the most sense to you. Finding out what works best for you will take a while and mastering it even longer if ever. 
