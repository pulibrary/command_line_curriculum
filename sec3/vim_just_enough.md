## Just Enough Vim

This guide focuses on giving you basic background information about Vim, and just enough Vim knowledge to write a git commit message.

### About Vim

Vim is a modal editor. This means that instead of holding down the control or
option key every time you want to issue a command, you instead enter **normal
mode** (aka command mode) and then issue as many commands as you like. Then when you want to type
again, you enter **insert mode**. Examples of commands include moving the cursor
around, or saving the file and exiting Vim. There are a couple other modes, but command mode and insert mode are the most important.

People who really like Vim find that once you grow proficient in its modes and
controls you can work very quickly.

For casual use Vim has two big advantages:

1. You will find it in every Unix system
2. By default has a very small cpu, memory footprint to edit files.

### Writing a commit message in Vim

This section is optional, and intended to give exposure to a very small set of extremely useful vim commands, using a git commit message as an example. If you're not using git in your current environment, move on to sec3/vim_all_the_things.md.

On many machines Vim is the default editor. If it's not the default editor on your machine, you can temporarily make it the default editor by typing `export EDITOR=vim`. This will make vim the default editor for a single shell session. Then if you use that shell session to create a git commit, vim will open so that you can create the message.

Vim opens in normal mode. If you are in any other mode you can return to
normal mode by pressing the `ESC` key or `ctrl+c`.

Here are some steps you can follow:
* `O`: When Vim opens to you to create your commit message, you'll want to enter insert mode. `O` will enter insert mode by opening a new line above the one you're currently on, which likely already has some text on it.
* Now you're in insert mode. Type your commit message!
* `ESC`: get out of insert mode.
* `/`, then someone's name, then `enter`: search for your co-author's name, and go to the result. Unless you've got a .vimrc that changes the default settings, search is case-sensitive.
* `0`: move the cursor to the beginning of the line
* `x`: delete the character to uncomment the `co-authored-by` line. hit `x` again to delete the leading space
* `:wq`: write (save) the file and quit
