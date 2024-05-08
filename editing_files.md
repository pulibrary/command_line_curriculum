## Editing Files

Most beginner and experienced developers and operations engineers use VSCode, the editor commonly recommended to beginners. VSCode is a desktop application with a graphical user interface, and is highly customizable via plugins. However, there are still good reasons to have some familiarity with a terminal-based editor. You may need to edit a configuration file on a machine you've accessed via ssh. And even on your local machine your shell will default to a terminal-based editor (likely vim) for certain activities, such as writing a git commit message. Many people use a terminal-based editor as their primary editor -- because you cannot rely on mouse usage at all, they can be a highly productive environment once you learn to use them.

## Choose and editor not a side

A somewhat religious war has raged for decades in certain circles on the topic of which text editor is superior. The main armies on this battlefield are those that herald emacs and those that herald vim. I encourage the reader to maintain an attitude of radical acceptance. In the same way that personal choices in lifestyle should be respected unconditionally, so too should be the choice of text editor. While the selection of a text editor can powerfully affect one’s working efficiency and enjoyment while programming, the choice is neither permanent nor an indication of character.

## Terminal-based editors

The first unix editor, `ed`, is a line-oriented editor that allows you to interact with one line at a time, rather than a full document all at once. It is almost never used now, so we don't cover it, but it was influential in the design of `vim`/`vim` and `sed`, both of which are covered in this material.

In this segment we will use `micro/nano`, `vi/vim/Neovim`, and `mg/emacs` text Editors to manipulate files. Familiarity with all of them I feel is worth it.
* [nano](sec3/nano.md)
* [emacs](sec3/emacs.md)
* [vi](sec3/vi.md)
* [Vim](sec3/vim.md)
* [sed](sec3/sed.md)


# Exercises

1. In the editor you found most baffling create a new document named `lorem_ipsum.txt`. You will need to "copy and paste" the results of your favorite search engine the contents of your "lorem ipsum" into this document. Save it and then edit the contents in the editor that you found most compelling. 
