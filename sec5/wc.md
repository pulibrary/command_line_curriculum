## wc: List number of lines, words, and characters

The format for the `wc` command is

```bash
wc [ -lwc ] [ name ]
```
`wc` counts the number of lines, words, and characters in the named files, or in the standard input. The definition of "word" is a string of characters separated by spaces, tabs, or new lines.

Example usage:

```bash
cat ~/cli_workshop/data_files/names.txt
wc --help
wc ~/cli_workshop/data_files/names.txt
wc -cw ~/cli_workshop/data_files/names.txt
```
