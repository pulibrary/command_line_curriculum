## Variables

The *PATH* described at the end of the [Getting in and Out Session](login.md) stored as a process environment variable, exposed in a shell as a shell variable.

Shell variables have case-sensitive names made from sequence of alphanumeric
characters and underscores. It stores a value, usually a string or a number, and can have several attributes as shown here:

```bash
pulsys@sandbox-tw8766:~$ my_variable=42
pulsys@sandbox-tw8766:~$ echo $my_variable
42
```

**NOTE** Do not put spaces around the equals sign or it will result in an error.

## Environment Variables

Process environment variables (also env vars) are not the same as shell variables we just described. They are configuration variables that every process has in Unix-like operating systems. A shell session is a process that receives env vars from the system when it is run. The shell imports them at startup time as regular variables and marks them as exported.

Every variable marked as exported will be copied into the process environment of
all child processes started in the shell. This behavior makes it possible to pass
configuration and secrets to all programs we run.

To see all variables marked as exported (which will eventually become environment
variables of the child processes), use the command `export`.


```bash
pulsys@sandbox-tw8766:~$ export
declare -x HOME="/home/pulsys"
declare -x LANG="en_US.UTF-8"
declare -x LANGUAGE="en_US:"
declare -x LC_TERMINAL="iTerm2"
declare -x LC_TERMINAL_VERSION="3.4.16"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="pulsys"
declare -x LS_COLORS="rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:"
declare -x MOTD_SHOWN="pam"
declare -x OLDPWD
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
declare -x PWD="/home/pulsys"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_CLIENT="1.2.3.4 53599 22"
declare -x SSH_CONNECTION="1.2.3.4 53599 172.20.80.18 22"
declare -x SSH_TTY="/dev/pts/0"
declare -x TERM="xterm-256color"
declare -x USER="pulsys"
declare -x XDG_RUNTIME_DIR="/run/user/1000"
declare -x XDG_SESSION_CLASS="user"
declare -x XDG_SESSION_ID="16"
declare -x XDG_SESSION_TYPE="tty"
```
To promote a regular variable into an environment variable, we need to export it. A
variable can be exported and assigned at the same time:

```bash
VAR_42='the answer to life the universe and everything'
export VAR_42
```
The quotes above will save you even when variable substitution is not needed. The variable $VAR_42 is now available to programs in the same shell session. If you log out of your virtual machine the variable will no longer be available. (Later we will visit how to make these variables always available)

Let's create a directory where we will store our own clever scripts with:

```bash
mkdir ~/bin
```

We will make modifications to the PATH. It will make it possible to execute programs in the new directory by name without adding the full path to it:

```bash
export PATH="$HOME/bin:$PATH"
```

We set PATH to a new value, using variable substitution to use both the path to our
home directory and the previous value of PATH. We export it to make it available to
child processes as well. It is important to remember once again if you log out of this session your new PATH will cease to work.
