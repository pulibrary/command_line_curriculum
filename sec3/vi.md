
## vi

The `vi` is a modal editor comes with two huge advantages.

1. You will find it in every Unix system
2. By default has a very small cpu, memory footprint to edit files. 

The format of the `vi` command is:

```bash
vi command
```
The `vi` editor has two common modes. They are *insert mode* where the characters you type are inserted into the file, and *command mode*, where the characters you type are commands for the `vi` editor to execute. `vi` starts up in command mode. To get into insert mode type `i`. The `ESC` key goes from insert mode to command mode.

### movement commands

The following commands allow movement when editing your file.

_Screen Movement_

* `cntl-U`: Scroll up
* `cntl-D`: Scroll down
* `cntl-F`: Scroll forward
* `cntl-B`: Scroll backward

_Line Movement_

* `j`: Move down one line
* `k`: Move up one line
* `H`: Move to the first line on the screen
* `M`: Move to the middle line on the screen
* `L`: Move to the last line on the screen
* `h`: Move left one character
* `l`: Move right one character
* `^`: Move to the beginning of a line
* `$`: Move to the end of a line
* `kG`: Go to like `k`
* `G`: Go to the end of the file
* `.`: Repeat the last edit (change, deletion) command

### deletion and insertion commands

_Deletion Commands_

* `ndd`: Delete next `n` lines
* `nx`: Delete next `n` characters
* `nX`: Delete previous `n` characters
* `D`: Delete from current position to end of line

Typing a `d` followed by any movement command deletes text in the area from the current position to the new position. For example, `dG` deletes to the end of the file. A `d$` deletes to the end of the line.
The last text you deleted is stored in a deleted text buffer. This deleted text can be inserted back into the document by using the `p` command.
To move text, delete the text that you want moved, move your cursor to where you want it placed, and type `p` to insert the text. To duplicate text, delete the text, type `p` to yank it back, move your cursor where you want the duplicate to appear and type a `p` a second time.

### saving and inserting files

The following commands are associated with saving edited information to a file. All of them except `ZZ` must be ended by typing the return key.

* `:w` : Write buffer back to file
* `:w examplefile` : Write buffer to examplefile
* `:w! examplefile` : Write buffer to examplefile even if it already exists
* `:q` : Quit window (more on this in [Neovim](neovim.md))
* `:q!` : Quit but discard changes
* `ZZ` : Save buffer and exit
* `:r newfile`: Insert file in the buffer
* `:e otherfile`: Edit a new file

### searching

These commands search for a string. The return key must be pressed after both these commands:

* `/string`: Forward search
* `?string`: Backward search

To continue searching:

* `n`: Searches for the next occurrence of the string
* `N`: Reverses the direction and searches for the next occurence

There's more to vi that would be a workshop in and of itself. This should allow a user to be able to create modify files.