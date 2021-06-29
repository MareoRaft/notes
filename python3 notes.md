pip downloads a source distribution (source code) for a package, and then builds it into a wheel. (like a .jar file).  
# example
uWSGI-2.0.18-cp38-cp38-<OS>_<ARCH>.whl  ->  for a specific OS and chip architecture
uWSGI-2.0.18-cp38-cp38-macosx_10_15_x86_64.whl  ->  for mac os only
uWSGI-2.0.18-cp38-cp38-none_x86_64.whl  ->  the OS is none.  could run on any OS, but only for x86_64 arch.
uWSGI-2.0.18-cp38-cp38-macosx_10_15_any.whl  ->  for mac OS, but ANY architecture.


conda has a yaml config file, where you can tell it to use pip to install things that are missing from the conda registry




http://coderbyte.com/CodingArea/GuestEditor.php?ct=Optimal%20Assignments&lan=Python

You can run a file by importing it at the interactive prompt, but this only works once per session; subsequent imports simply return the already-loaded module. To force Python to reload and rerun a file's code, call the reload(module) function instead. And while you're at it, be sure to use parentheses for reload, but not import.


http://stackoverflow.com/questions/356161/python-coding-standards-best-practices
http://www.onlamp.com/pub/a/python/2004/02/05/learn_python.html

REQUIREMENTS.txt
pip install pipreqs
pipreqs .
(see https://stackoverflow.com/questions/31684375/automatically-create-requirements-txt)


PACKAGES
python3.4, for example, stores packages here:
/usr/local/lib/python3.4/site-packages





LAMBDA FUNCTIONS
http://www.secnetix.de/olli/Python/lambda_functions.hawk






REGEX
import re
# by the way, r"string" and r'string' are RAW strings, that's what the r is for.
re.match( r'regexpattern', 'stringtomatch', options ) - matches from the BEGINNING OF THE STRING
re.search( " ) - matches regularly (like in perl)
options include:
re.M, re.I, re.S
re.L - uses the locale (language) to modify what \w \W \b \B match
re.U - uses unicode to modify "
re.X - extends regex with whitespace allowed. Use (?#comment) for comments.

Understanding the yield STATEMENT:
http://stackoverflow.com/questions/231767/what-does-the-yield-keyword-do-in-python

Understanding the yield EXPRESSION:
http://stackoverflow.com/questions/10695456/what-is-the-result-of-a-yield-expression-in-python

pip (Python Package Index) -- Dealing with multiple versions of Python:
http://stackoverflow.com/questions/2812520/pip-dealing-with-multiple-python-versions
To use "pip3", first re-install pip following
https://pip.pypa.io/en/stable/installing/
and using python3 get-pip.py if you want python3
then it should work.




VARIABLES
to use a global variable in a function, you must say "global":
x = 'this'
def hi():
	global x
	x = x + 'nthat'

print(x)




LIST OF THINGS I KNOW
locals()
globals()
__add__
__sub__
__mul__
__truediv__
__floordiv__
"positional" parameters vs "named, default value" parameters.  They can actually be used interchangeably!  The point is you can have default values.  intuitive.
functions and variables are the same thing
issubclass - all the regular things are subclass of `object`
http://simeonfranklin.com/blog/2012/jul/1/python-decorators-in-12-steps/ look at number 8. func_closure
