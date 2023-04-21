## emacs

`emacs` (for the purposes of this introduction we will be using the lightweight [`mg`](http://homepage.boetes.org/software/mg/) micro version of emacs. To install the editor run the following commands:

```bash
sudo apt -y install mg
```

### emacs windows

Running `mg` creates a window on our screen containing:

* Text window showing the contents of the buffer
* A one-line mode line describing what is going on in the text window
* A minibuffer -- a special location to input commands

### escape and control keys

`mg` relies heavily on the escape key and the control key. Throughout this section, `<esc>` means to type the escape key and `<cntl>`. For example.

```bash
<esc> a

<cntl>-a
```

Means type the escape key and then the `a` key, which is sometimes referred to as an *escape sequence* and the second one is hold down the control key and then press the `a` key while holding the control key. This is known as a *control character*. If you don't do this the text is inserted into the buffer.

### Character Operations

The character operations are:

* `cntl-b` : Move back one character
* `cntl-f` : Move forward one character
* `cntl-p` : Move to the previous line
* `cntl-n` : Move to the next line
* `cntl-d` : Delete the character underneath the cursor
* `delete` : Delete the charater to the left of the cursor
* `cntl-t` : Transpose the two previous characters.

### file operations

The file operations are:

* `cntl-x cntl-v` : Visit a file -- putting the contents of a file into the buffer
* `cntl-x cntl-w` : Write the contents of the buffer to a file
* `cntl-x cntl-s` : Write the contents of the buffer to the file listed in the mode line

To exit `mg`, use the following control sequence:

```
`cntl-x cntl-c`
```

### line operations

Line operations work with an entire line of the buffer. The four line operations are:

* `cntl-a` : Move the cursor to the beginning of the line
* `cntl-e` : Move the cursor to the end of the line
* `cntl-o` : Insert a blank line into the buffer
* `cntl-k` : Kill a line of text

### word operations

Word operations work with an entire word of text at one time instead of just one character at a time.

* `<esc>b` : Move back one word
* `<esc>f` : Move forward one word
* `<esc><delete>` : Delete one word to the left
* `<esc>d` : Delete one word to the right
* `<esc>t` : Transpose the two words aroud the cursor
* `<ecs>c` : Capitalize a word. Must be at the beginning of a word for this to work consistently
* `<esc>u` : Convert a word to uppercase
* `<esc>l` : Convert a word to lowercase

This practice is a minimal introduction to how to use emacs. Using your preferred search engine explore the use of emacs if this has scratched a surface. How to get comfortable with emacs would be a workshop in itself.

 * I used this [Guide to emacs](http://www.jesshamrick.com/2012/09/10/absolute-beginners-guide-to-emacs/) to write this document 
 * A former colleague recommended [Mastering Emacs](https://www.masteringemacs.org/article/beginners-guide-to-emacs) as a good way to start with good habits