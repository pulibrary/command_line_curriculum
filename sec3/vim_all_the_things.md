## Vim: keybindings

This guide provides a more complete list of vim keybindings that you can play around with in vim. It is not exhaustive, but does provide a useful and fairly large subset that will get you a long way.

### Vim configuration

If you're going to do much more than very occasional vim usage, you'll want at least a few configurations.

There is a useful small, basic config file at [https://github.com/pulibrary/princeton_ansible/blob/main/roles/common/files/vimrc.local](https://github.com/pulibrary/princeton_ansible/blob/main/roles/common/files/vimrc.local). Copy this into a file called `.vimrc` in your home directory as a starting point.

### Starting Vim

On many machines Vim can be started with either the `vi` command or the `vim`
command. To open a file for editing do:

```bash
vi [filename]
```

Vim opens in normal mode. If you are in any other mode you can return to
normal mode by pressing the `ESC` key or `ctrl+c`.


### Entering insert mode

Insert mode is the mode you use to type. There are so many good ways to enter insert mode.

* `i`: Enter insert mode with your cursor at its current position. Most commonly taught.
* `a`: Enter insert mode with your cursor directly after its current position.
* `o`: Enter insert mode on a new line below your current cursor position.
* `I`: Enter insert mode at the very beginning of the line your cursor is on.
* `A`: Enter insert mode at the very end of the line your cursor is on.
* `O`: Enter insert mode on a new line above your current cursor position. (This one is great for starting a commit message)

### Movement commands (aka vim motion)

The following commands allow movement when in normal mode.

Basic single-character motion:
* `h`: Move left one character
* `j`: Move down one line
* `k`: Move up one line
* `l`: Move right one character

Word-by-word:
* `w`: move to the next word boundary
* `b`: move to the previous word boundary

Within a line:
* `0`: Move to the beginning of a line
* `^`: Move to the first character on a line
* `$`: Move to the end of a line

Within a file:
* `gg`: Go to the beginning of the file
* `G`: Go to the end of the file
* `:n` or `nG`: Go to line n (substitute any number for n)
* `cntl-U`: Scroll up (half a page)
* `cntl-D`: Scroll down (half a page)
* `cntl-F`: Scroll forward (a full page)
* `cntl-B`: Scroll backward (a full page)

### Deletion commands

* `x`: Delete the character under the cursor
* `dd`: delete the current line
* `nx`: Delete next `n` characters
* `ndd`: Delete next `n` lines
* `D`: Delete from current position to end of line

Typing a `d` followed by any movement command deletes text in the area from the current position to the new position. For example, `dG` deletes to the end of the file. `d$` deletes to the end of the line.


### Paste, yank, undo, redo, repeat

* `p`: paste from the text buffer. The last text you deleted is stored in a text buffer. This deleted text can be inserted back into the document by using the `p` command.
* `y`: many deletion commands have corollary "yank" commands. To do these commands use `y` where you would have used `d`, for example `yy` to yank an entire line. Any text you yank is stored in the text buffer and you can paste it somewhere else.
* `u`: undo the last change you made. You can keep doing this to undo a series of changes.
* `ctrl-r`: redo a change you undid. You can keep doing this to redo a series or undos.
### 
* `.`: Repeat the last edit (change, deletion)

### saving and inserting files

The following commands are associated with saving edited information to a file. All of them except `ZZ` must be ended by typing the return key.

* `:w` : Write buffer back to file
* `:w examplefile` : Write buffer to examplefile
* `:w! examplefile` : Write buffer to examplefile even if it already exists (i.e. overwrite)
* `:q` : Quit window (more on this in [Neovim](neovim.md))
* `:q!` : Quit but discard changes
* `ZZ` : Save buffer and exit
* `:r newfile`: Insert file in the buffer
* `:e otherfile`: Edit a new file

### Indentation
* `>>`: Indent the line you're on
* `<<`: unindent the line you're on
* `ggVG=`: go to the top of the file, enter visual mode, go to the bottom of the file, and re-indent everything that's selected.

### searching

These commands search for a string. The return key must be pressed after both these commands. Searching is case-sensitive by default; the vim config file mentioned above gives you case-insensitive search.

* `/string`: Forward search
* `?string`: Backward search

To continue searching:

* `n`: Searches for the next occurrence of the string
* `N`: Reverses the direction and searches for the next occurence

There's more to vi that would be a workshop in and of itself. This should allow a user to be able to create modify files.

### Visual Mode

You'll start to want to delete or yank whole sections of text, like a multi-line function, or the irb prompt from the beginning of each line you just pasted into your file after you tried some stuff out in the console. Visual mode allows you to select multiple lines, either in their entirety or specific columns of each line, and then operate on those selections. It's probably outside the scope of this document, but good to know about as a thing you might want to learn about next.
