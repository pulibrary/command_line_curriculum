## bc: Calculator

The format for the `bc` command is:

```bash
bc [ file ]
```
`bc` is an interactive calculator with unlimited precision arithmetic. It is one of the instructor's favorite commands to "pass time with". For example one nice feature of `bc` is that you can set the parameter scale to indicate the desired precision. For example, if you set scale=100, all calculations will be carried out to 100 decimal places. It is one of the *to my knowledge* only unix tools with a Hilary Mason maintained [twitter account](https://twitter.com/bc_l)

Example usage:

```bash
bc --help
bc
bc 1.06.95
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'.
42 + 42
84
```
`cntl-d` will close it. 