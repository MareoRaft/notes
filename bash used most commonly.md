What to learn in Bash
=====================
Basically, each line in this file is a bash command.  Know what each one does, what it's name is an abbreviation of, and how to use it.

You should go down the list in order.  And have fun!  Commands early on may serve as helpful tools to help you learn/do other things farther down the list.

This should be a hands-on experience.  You should be running these commands in a bash shell while learning.  The world is your oyster!

Final note and then I promise I'll stop talking so much.  Indented content after a command is additional stuff you have to know about that command.  In particular, something like "-s" is a flag to be used in conjunction with the command.



*means i added it after-the-fact

sh*
bash*

the basics
----------
man
  Use this one to help you learn about the other ones.  Especially useful for looking up flags.
pwd
cd
ls
  -l
  -a
sudo
touch*
mkdir*
rm
  Make sure you know what you are deleting before you pull the trigger!
  -r
  -f
cp
  Careful, if the destination path already exists, it will be overwritten.
  -r
  -p
mv



searching, viewing, editing
---------------------------
find
  -name
  Using glob "*" operator as wildcard in the name.
grep
  -r
  Know how to filter output of another command with grep (in particular, know ls -l -a | grep "stuff", which is so useful).
less
  Aside: You don't really need less once you learn emacs or vim, but what's nice about it is that it's so quick/convenient.
emacs or vim
  Choose ONE of these two text editors.  Know how to
  * create a new file
  * open an existing file
  * type things into the file of course!
  * jump to top/bottom of file
  * search for a word within the file (and iterate through all matches)
  * copy, delete, paste
  * save the file!
  Aside Again: I dare you to use emacs or vim instead of your regular text editor for the rest of this journey.
diff
  Using it on two files.
  Using it on two directories.



environment variables, configuring settings
-------------------------------------------
You sortof learn all the things in this section at the same time.
  * What is ~/.bash_profile ?
  * What is ~/.profile ?
  * How do you set a variable? (whitespace matters!)
  * How do you get a variable?
  * What is $PATH ?
echo
source
export
which
PROTIP:
  Configure a nice PS1 in your ~/.bash_profile that includes, among other things, your current working directory.  You'll pretty much never have to use pwd again, and you won't feel so lost all the time.
  


more things that i can't think of a good heading for
----------------------------------------------------
brew
  What are package managers?  Why are they better than installing software manually (BESIDES convenience)?  Do you like beer?
ln -s
ssh
scp



archiving & extracting, compressing & expanding
-----------------------------------------------
tar is important.  It's history is very interesting too.  You should know how to use it to both create and unravel archives.  All of the "zip" commands are straightforward and you don't need to spend much time on them.
tar
  x
  v
  f
zip
unzip
gzip
gunzip



far, and beyond!
----------------
screen or tmux
The following are not commands but shell constructs
$()
&& and ||
&

su*
chmod*
| (used in grep above)
>* (output to a file)
get color in terminal*
get color in git*



test for understanding
======================

What is <command>?
------------------
For each command and for each flag,
  1. What it stands for
  2. What it does
  3. An example
  4. What are the parameters and what do they default to?

How do you do <task>?
---------------------
  * How do you find all files that end in .js?
  * How do you find all files that contain the word "import"?
  * How do you move all the 

For next time
-------------
  1. Get colors in terminal and a PS1 w/ time and cwd

 