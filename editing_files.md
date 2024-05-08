## Editing Files

Most beginner and experienced developers and operations engineers use VSCode, the editor commonly recommended to beginners. VSCode is a desktop application with a graphical user interface, and is highly customizable via plugins. However, there are still good reasons to have some familiarity with a terminal-based editor. You may need to edit a configuration file on a machine you've accessed via ssh. And even on your local machine your shell will default to a terminal-based editor (likely vim) for certain activities, such as writing a git commit message. Many people use a terminal-based editor as their primary editor -- because you cannot rely on mouse usage at all, they can be a highly productive environment once you learn to use them.

In exploring text editors we will look at terminal-based text editors found on *NIX systems: `ed`, `vi` and `emacs`. The `ed` editor was the first of these three editors created. It is a line-oriented editor instead of a full-screen editor and will feel very primitive compared to `vi` and `emacs`. It is can be useful on the rare occasion when one is dealing with a console terminal. (I wish no one ever to have to suffer this) If you run:

```bash
pulsys@sandbox-fkayiwa:~$ man ed
```
you will see what is needed to use the editor. In this segment we will use `vi/Neovim`, `mg/emacs` and `micro/nano` text Editors to manipulate files. Familiarity with all of them I feel is worth it.

## Choose and editor not a side

A somewhat religious war has raged for decades in certain circles on the topic of which text editor is superior. The main armies on this battlefield are those that herald emacs and those that herald vim. I encourage the reader to maintain an attitude of radical acceptance. In the same way that personal choices in lifestyle should be respected unconditionally, so too should be the choice of text editor. While the selection of a text editor can powerfully affect one’s working efficiency and enjoyment while programming, the choice is neither permanent nor an indication of character.


# Exercises

1. In the editor you found most baffling create a new document named `lorem_ipsum.txt`. You will need to "copy and paste" the results of your favorite search engine the contents of your "lorem ipsum" into this document. Save it and then edit the contents in the editor that you found most compelling. 
