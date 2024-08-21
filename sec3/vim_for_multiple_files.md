## vim: a Deeper Dive into vi/Vim

  * Ways to organize and open files
  * Useful motions to move around your code
  * How to create new keystrokes
  * Ways to repeat your keystrokes
  * Plugins
  
## Spatial Organization

If you’ve used an Intergrated Development Environment (IDE) before, you’re certainly used to managing your files with tabs. vim uses other ways to represent and organize open files. Indeed, there are four layers of abstraction you can use for that: the buffers, the windows, the tabs, and the argument list.

### Buffers

A buffer directly matches to an open file in memory. To make a comparison with a standard IDE, a buffer would be the content of a tab. The big difference is that when you close a tab in an IDE, you also close the open file in it. Not in vim; if you close a window containing a buffer, the buffer is still there but it’s hidden.
In fact, a buffer can have three different states:

 * active - The buffer is displayed in a window.
 * hidden - The buffer is not displayed, but it exists and the file is still open.
 * inactive - The buffer is not displayed and empty. It’s not linked to any file.

To see all opened buffers, we can look at the buffer list. You can use the commands `:buffers` or `:ls` to display it. Each line contains:

 1. The buffer unique ID.
 1. Indicators displaying different information (for example `a` for active, `h` for hidden, or  for inactive).
 1. The name of the buffer
 1. The line number where the cursor is 

To navigate through the buffer list you can use the following commands

 * `:buffer` <ID_or_name>- Move to the buffer using its ID or its name.
 * `:bnext` or `:bn` - Move to the next buffer.
 * `:bprevious` or `:bp` - Move to the previous buffer.
 * `:bfirst` or `:bf` - Move to the first buffer.
 * `:blast` or `:bl` - Move to the last buffer.

Try opening the following new files with

```bash
pulsys@sandbox-fkayiwa:~$ vim file1 file2 file3 file4
```

cycle through the buffers to get used to navigating through the files.

You can type `:help buffers` while in your editor for more information on buffers.

### Windows

A window in vim is a space (or a place) you can use to display the content of a buffer. Don’t forget: when you close the window, the buffer is still in the buffer list.

The simplest ways to create windows, use the command :new or one of these keystrokes:

 * CTRL+W s - Split the current window horizontally.
 * CTRL+W v - Split the current window vertically.
 * CTRL+W n - Split the current windows horizontally and edit a new file.

To move your cursor from one window to another, you can use:

 * CTRL-W j.
 * CTRL-W k.
 * CTRL-W h.
 * CTRL-W l.

To move from window to window use:

  * CTRL+W r - Rotate the windows.
  * CTRL+W x - Exchange the focused window with the next window.

To resize the windows:

  * CTRL+W - - Decrease window’s height.
  * CTRL+W + - Increase window’s height.
  * CTRL+W < - Decrease window’s width.
  * CTRL+W > - Increase window’s width.
  * CTRL+W = - Resize windows for them to fit on the screen with the same size.

Later we will use a plugin that simplifies this. 

If you want to quit windows you use:

 * `:q` - To quit the current window. Worth pointing out that `:q` doesn’t quit vim, but a window. Although, if there is only one window open, vim will close.
 * `:q!` - To quit the current window, even if there is only one window open with an unsaved buffer!.
 * `:qa` - To quit all the current windows. Add `!` if you don’t want to save your changes in unsaved buffers.

For now open vim and create now windows using the examples above.

### Tabs

We saw that a buffer is a document (often an open file), and a window is the container for an active buffer. We can see tabs as a container for a bunch of windows. As a result, vim’s tabs are different from the usual tabs you can find in many IDEs!

Here are the commands to create and delete tabs:

 * `:tabnew` or `:tabe` - Open a new tab.
 * `:tabclose` or `:tabc` - Close the current tab.
 * `:tabonly` or :`tabo` - Close every other tab except the current one.

To move from tab to tab, you can use these keystrokes:

 * `gt` - go to the next tab.
 * `gT` - go to the previous tab.

You can also add a count before the last two keystrokes. For example, 1gT goes to the first tab. Worth remembering that tabs are indexed from 1, not from 0.

### Argument List (arglist)

The argument list (also called arglist) is the fourth and last abstraction allowing you to organize your open files. It’s useful to see it as a `stable subset` of the buffer list. When we ran `vim file1 file2 file3 file4`

 1. Every file in the arguments above will be in the buffer list and the arglist
 2. Some files in the buffer list might not be in the arglist

The arglist can be useful to isolate some files from the buffer list to do some operations on them. Here are some commands you can use to manipulate the arglist:

  * `:args` - Display the arglist.
  * `:argadd` - Add file to the arglist.
  * `:argdo` - Execute a command on every file in the arglist.

To edit the files in the arglist, you can use these commands:

  * `:next` - Move to the next file in the arglist.
  * `:prev` - Move to the previous file in the arglist.
  * `:first` - Move to the first file in the arglist.

### Mapping Keystrokes

Mapping keystrokes eliminates toil from repetition. Create a file called `file_extraction.txt` with the following content: 

```txt
The quick brown fox jumps over the lazy dog
The quick brown fox jumps over the lazy dog
The quick brown fox jumps over the lazy dog
The quick brown fox jumps over the lazy dog
The quick brown fox jumps over the lazy dog
The quick brown fox jumps over the lazy dog
```

To work with this files we will demonstrate a simple example of remapped keys that mean less typing. For that one uses commands for all the vim modes:

  * `:nnoremap` - Create a new mapping for NORMAL mode (non recursive).
  * `:inoremap` - Create a new mapping for INSERT mode (non recursive).
  * `:vnoremap` - Create a new mapping for VISUAL mode (non recursive).

As an example let's map `s` to `dd` Keep in mind `s`ubstitute is already used in your default mapping of a vim installation. Use the following commands on the file you just created.

  1. Run the `ex` command `:noremap s dd`
  2. Try to hit the keystroke `dd`. It will delete a line. (hit `u` to undo the delete)
  3. Try to hit `s`. It deletes a line too.

If you close your vim this silly change will vanish. The lesson here is avoid making changes to the default vim's mappings. 

If you want to create new mappings, you should use a special key called the leader key. It’s a way to create namespaces for keystrokes: first you use your leader key, then you use your keystroke. Thanks to the leader key, your new keystroke will never conflict with the default vim keystrokes.
You need to set the variable mapleader to use the key you want as leader key. Here’s an example:

```bash
:let mapleader = "\<space>"
```

The mapping commands we saw above are often written in vim’s configuration file to set them automatically when you open vim. For example, you can write the following to the nvim configuration file:

```conf
let mapleader = "\<space>"

nnoremap <leader>bn :bn<cr> ;buffer next
nnoremap <leader>tn gt ;new tab
```

We define our leader key and other keystrokes. The keystrokes `SPACE bn` will move to the next buffer, and `SPACE tn` to the next tab. The `<CR>` is for the carriage return which represents the `ENTER` you would normally enter to execute this command.

### Jump motions

There are special motions in vim called jump-motions. These motions move your cursor several lines away, like the keystroke gg we saw earlier.

#### Jump List
Each time we use a jump motion, the position of the cursor before the jump is saved in the jump list. You can move through it with the following keystrokes:

  * `CTRL+o` - Go to the previous cursor positions.
  * `CTRL+i` - Go to the next cursor positions.

You can move from line to line and even from buffer to buffer with these commands.

#### Change List

I find the change list really useful. Each time you insert something (using INSERT mode), the position of your cursor is saved in the change list. You can navigate through it using these keystrokes:

  * `g;` - Jump to the next change.
  * `g,` - Jump to the previous change.

#### Method Jump

Being able to jump from method to method, if you’re programming with some OOP languages, is a nice feature to have. You can do that with the following keystrokes:

  * `[m` - Move to the start of a method.
  * `]m` - Move to the end of a method.

#### Repeating Keystrokes

Here’s an extremely effective way to use vim. The following steps will reduce your toil significantly:

  * `.` - Repeat the last change.
  * `@:` - Repeat the last command executed.


### Plugin Manager

TODO
