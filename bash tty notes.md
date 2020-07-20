Creating a new user on RHEL / fedora family
----------------------------------------------
sudo su root
useradd matt
passwd matt
(create a password)
visudo
(add the following line to the bottom of the file, and save)
matt  ALL=(ALL) NOPASSWD: ALL
su matt
(now we switch to the matt user because we want our ssh files to be owned by matt, not root)
cd /home/matt
mkdir .ssh
cd .ssh
vi authorized_keys
(add your public key and save the file)



BASH ON WINDOWS
---------------
There is a new product called Bash on Ubuntu on Windows.  According to some, it is easier to install and start using than Cygwin!
https://blogs.msdn.microsoft.com/commandline/2016/04/06/bash-on-ubuntu-on-windows-download-now-3/


# halt script on error
set -e 



# color escape codes / info
\[\033[    x;       y        m                 \]
ESC          SGR parameters          end an SGR code

Black	0;30
Blue (slightly purplish)	0;34
Green	0;32
Cyan	0;36
Red	0;31
Purple (looks pink)	0;35
Brown (looks yellow)	0;33
Blue	0;34
use 1 instead of 0 to get light or bold version

see color.pl and MohithMatthew/256colors2.pl
0 - regular
1 - bold
2 - faint/dark
3 - (italic)
4 - underline
5 - blink
6- (blinkrapid)
7 - reverse video on
8 - invisible



# PS1
PS1="\[\033[41m\]\[\033[30m\][\[\033[31m\]\u@\[\033[1;33m\]\h:\[\033[1;35m\]\W,\[\033[1;34m\] \@,\[\033[1;37m\]\d\[\033[30m\]]\[\033[0m\]>"

## PS1 common interpolation variables
\u is the User
\h is the computer
\W is directory
\@ is the time
\d is the date

## PS1 more interpolation variables
PS1="hostname--> \h hostname \H basenametermdevice \l shell \s username \u cwd \w cwdbase \W hist \! cmdnum \# effectUIDind \$ oct \nnn"


# hosts
127.0.0.1 is localhost

# ssh address
username@hostname
username@domain
username@ipaddress
username@ipaddress:path/relative/to/home/dir
username@ipaddress:/path/absolute

ssh -i /path/to/key/file.pem username@IPaddress
ssh punc5093@instructorium.com or ssh punc5093@50.63.101.1 (Godaddy) password is... (redacted)

perl mojo.pl daemon -l http://172.31.20.110:5432
(that's the private IP, the one the server sees itself)
type in browser: http://54.201.15.197:5432
(that's the public IP, allowing anyone to find the server. that address upon arrival is rerouted to the private IP)


# bash keybindings
Unfortunately, these may not work in tmux.
ctrl-k kill-->remove from cursor to end of line (like cut)
ctrl-y yank-->insert what was killed (like paste)
https://www.redpill-linpro.com/sysadvent/2015/12/09/shell-intro-tips.html

sudo -- super user do
su -- switch user
sg -- switch group
execute a command AS A GROUP:
`sg groupname -c 'command here!'`
sg for switch group, c for command, single quote the command to pass in as argument!

routing STDIN to a command which normally accepts a FILE:
source /dev/fd/0 <<<'echo hello'
/dev/fd/0 pretends to be a file, but it is really STDIN in disguise.  Heredocs route to STDIN.

PIPES THE EASY WAY!!!
http://www.linuxjournal.com/article/2156


PROCESS THINGS
ctrl-z stops (pauses) a process
jobs - lists all stopped (paused) processes.  gives them job#'s too. fg - foreground command which brings most recent job to fg
bg - background.  This means that you can do any commands while it is running!  But you still see it running if it prints things.  It doesn't really LOOK like it's in the bg.
ctrl-\ - quits a process
ps # lists running processes launched by user, including thier PID's
ps -e # lists all running processes - TRY ALSO:
ps aux
kill PID - kills the process.
kill %job# - same thing
killall - kills process AND all children
know what is: PID, PPID
pgrep



EXIT CODES
for exit codes, 0 signifies success.  1 means failure, and other error codes (ie 43) are very specific failures.  "true" makes us return 0, and "false" makes us return 1.
$? is the exit status.
perl -e 'exit 4;'; echo $? - gives exit status 4 (error code 4).
$? is the exit status (where exit status is $? >> 8) and $! is the error during execution if it failed. Same in perl, except true false flipped.



INPUTS AND OUTPUTS
Mo: file descriptors (fd) are integers that the unix OS keeps a record of per process
Mo: usually, in the beginning, file descriptor 0 points to the STDIN stream...
< is the same as 0< which is STDIN
> is the same as 1> which is STDOUT
2> is STDERR
&> is special shortcut for both STDOUT and STDERR
>> is the same as >, but in append mode.
<<DELIM is same as <, but in literal mode. We directly insert input. (can be multi-line)
<<"DE LIM" to allow spaces (multi-line)
<<< for single-line literal input.  These three are called HERE-DOCS.
HERE-DOCS are NOT like pipes.  You can only use it once, and the rightmost one would overwrite others. Use "" if you want a blank line to terminate the quote.
6<>file.txt opens the file for reading AND writing.  Assigns fd 6 to it.




Redirection
-----------
0 is STDIN
1 is STDOUT
2 is STDERR

`<` alone is short for `0<`
`>` alone is short for `1>`

A space *after* `<` or `>` is okay, but *before* is not.

Example:
```
cat 0<input.txt 1>output.txt
```
0< is now pulling from input.txt instead. 1> is now outputting to output.txt instead.  Inputs point left, outputs point right.

Example :
```
mycommand 2>/dev/null
```
The STDERR resulting from mycommand is now redirected to /dev/null.

1<&2 means that the 1's input is now pulling from 2's input instead.  
We cannot chain them 1>&2 2>&3 3>&4 4>file.txt like so.
We must chain them 4>file.txt 3>&4 2>&3 1>&2 like so.  
Read it like this: 4 goes to file.txt.  3 goes to what 4 is pointing to.  2 goes to what 3 is pointing to...
1<2 would be accepting input from a file named 2.
1<'&2' would be accepting input from a file named &2.

exec, you can only use a `fd` (file descriptor) for reading ONCE, close a fd like this: 3>&-, fifo (first in first out), pipes
http://www.catonmat.net/blog/bash-one-liners-explained-part-three/
currently on number 13




OTHER
-----
( allow me; to treat; multiple statements ) as a unit that run in a sub-shell.
{ allow me; to treat; multiple statements; } as a unit. Useful for i/o stuff.
& is the same as ;, but it means the command will be run in the bg.  When executed the terminal will tell you the [job#] PID of the command.
; means go to next statement.  && means statement && statement.  That is, the first must be true and then do the second.
'allows no interpolation nor escaping' must use 'i'"'"'m okay' for apostrophe.
$'allows ansi escaping, but no interpolation'
"allows ${variableinterpolation}s but no escaping except \". "
printf "allows escaping in it's input,\nso that you can do both."
When necessary, use concatenation by placing strings next to each other with NO WHITE SPACE between them.
!nonwhitespace (includes !" but not in single quotes) is a history grab even in a string!  Therefore to avoid errors with !, we often must "separate the "'!'
We can make any character be interpreted LITERALLY with \ (OUTSIDE of a string):
\', \ , \", etc. \n would give n.
<CR> (left) and <LF> (down).

calculations: use "bc" for integers. It uses ^ for pows.
Add "-l" for fractions and natural logarithms "l(x)".
example: echo "scale=40; l(10)"|bc -l

lambda calculus!

$PATH, .gz, gzip, gunzip, tar

octal (starts 0) and hex (starts 0x) representations of numbers in tty





COMMANDS
hexdump - displays textfile as aschii numbers written in hexadecimal.
mktemp thisnameXXX makes a unique file!
mktemp -d thisnameXXX makes a unique directory!
find /directory/to/look/in -name titleprefixtolookfor*
!fh... finds the first command that started with 'fh...' and executes it.

ls /tmp - lists temporary folders/places.  these might be usable by programs as a temp storage space!
ln -s points/to/path points/from/path - makes a symbolic link
echo $USER outputs Matthew
echo ${USER%??} outputs Matth
pwd, less, sudo, su, cat, tty, who, w, touch (does NOT open), open, mkdir, rm -R,

SUDO file:
sudo -E visudo
and
/etc/sudoers.d

sort - sort things alphabetically (ASCII or some other standard order listed)

grep -A 20 -B 4   .  Show 4 lines before each match, and 20 lines after each match.

URI commands are like applications
use "open tel:{query}" in terminal to execute

echo hello|sed s@find@replace@g
sed file.txt "s/find/repl/g"
# example of renaming files (remove any occurances of 'notesheet-section' from each file name):
for F1 in $(ls *.tex | grep ''); do
	F2=$(echo "$F1" | sed s@notesheet-section-@@g)
	mv "$F1" "$F2"
done

tput
	lines, cols, cup l c, clear, -S
cup means "cursor position"



CONTROL STATEMENTS - spacing is important in sh!  Pay attention to it!
for ...; do ...; done;
for i in $(seq 1 62); do mktemp -d X; done; # we use $( ) instead of ` ` because $( ) sets a clean slate for quoting.  ` ` requires escaping when in quotes var = "\`i'm ugly\`".

if []; then ... ; elif []; then ... ; elif []; then ... ; else ... ; fi;       # the "elif"s and the "else" are optional.
# [ -n ] returns true if the length of string is nonzero
if ["$DIRECTORY" = ""]; then...  #works too! #quotes VERY NECESSARY in all "if" cases
man [    !!! tells about if statements shell script



TERMINAL.APP
cmd-double click a url to go to the page in browser!
Ctrl-D  is EOF character
pbcopy and pbpaste (ex: pbpaste > file.txt )
SCROLLING
fn-up / fn-down     Terminal.app (and many other OSX applications!)
b / space           tty (in scrollable contexts only)
ctrl-b / ctrl-f     vim ("backwards" and "forwards")
ctrl-a then ESC then up/down arrow       screen


POSIX COMPLIANT SH SCRIPTS
use
checkbashisms
to get rid of bashisms in bash scripts, leaving only an posix-complient sh script


PROFILING
In chronological order:
all shells: /etc/profile   (i THINK all shells.  possibly just login shells)
login bash shells: ~/.bash_profile, ~/.bash_login
all login shells: ~/.profile
all non-login shells: ~/.bashrc (rc means run commands).

ctrl-r - reverse search through ~/.bash_history or ~/.zsh_history



SCREEN (SQUEALIN)
SESSIONS
screen -ls   lists all sessions
screen       new session
screen -d PID  detach session
screen -r PID reattach session
WINDOWS (within a session)
Ctrl-a w     window list
Ctrl-a c     create window
Ctrl-a 0     go to window 0 (for example)
Ctrl-d       drop window (if there is only 1 window, this will drop session too)
Ctrl-a Ctrl-d    detach session

Ctrl-a A     set the title of the current window!
Ctrl-a a     go to beginning of line!!


TMUX
reattach

VERIFYING A SHA-256 CHECKSUM
shasum -a 256 filepath
(or if you can't get shasum...use this python one:)
checksum --hash sha256 filepath

PERMISSIONS
stat, ctime, mtime, atime, index nodes.
user group everyone
uid/gid vs real uid / real gid - (a process that runs as a diff user)


SETTING DATE AND TIME
fedora:
"date" command
"timedatectl" command
see also: https://linuxconfig.org/how-to-change-a-timezone-on-rhel7-linux-server
other linux:
cp /usr/share/zoneinfo/America/New_York /etc/localtime
freebsd:
https://www.cyberciti.biz/faq/howto-set-date-and-time-timezone-in-freebsd/



TO LEARN
ncurses
http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/intro.html#WHERETOGETIT
killall



