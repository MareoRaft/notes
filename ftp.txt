FTP USAGE
==========


Resources:
---------
http://www.tldp.org/HOWTO/FTP-3.html

# there is a tool called gftp which sounds promising, but it seems like ppl don't normally use it on OS X.  It is capable of recursively copying down directories.  very cool, but i don't have the time to install it...
http://gftp.seul.org/


Commands:
----------
ftp # opens interactive mode

open domainname.com # connects to server. it then asks for the username, followed by the password.  # you can use cd to move around, and lcd to move around on your local machine

# you may optionally type "ascii" to switch to ascii transfer mode and "binary" to switch back

get path/to/file # will transfer back to your local machine, into the current directory, with the same name
# for every "get" command, there is an identical "put" command that goes the other direction

get path/to/file /path/to/destination # allows you to change the name and/or location

mget path/to/* # "multiple get" used with wildcards can download many files.
# or you can use a space delimited list of filenames
# use the "prompt" command to prevent ftp from prompting you before every single download

!ls # using ! before a command will run it on your local machine.  but don't use !cd, i guess...





