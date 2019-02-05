KNOW EVERYTHING ON www.myperlquiz.com

Core method $obj->isa('class') returns true if $obj is a subclass of class.  (I am using subset in the non strict sense).
Core method $obj->can('methodname') returns true iff there exists a defined method of that name.

my $v = sub { print 'hi' };  $v gets a reference to CODE.  That is, ref($v) eq 'CODE'.

Blocks include: BEGIN, END.  ENDs are executed in reverse order of definition.

the DESTROY function in a package will be automatically envoked when an object goes out of scope!
It is more the opposite of bless than the opposite of new.  This is because if an object gets re-blessed during its destruction, it will be destroyed again!

module >= core module >= core pragma
module >= pragma >= core pragma

specify module version that you want to use: use only MyModule => 0.30;
declare version in a module: our $VERSION = 1.9.3;

PIPE
http://www.tutorialspoint.com/perl/perl_pipe.htm
OPENING A PIPE FOR READING
http://docstore.mik.ua/orelly/perl3/prog/ch16_03.htm
SEPARATE SHELL:
I'm not sure if I fully understand your statement of the task, but in case it helps, here's a technique I've used to good effect when I want a perl script to run a series of commands in sequential order, and the script has to wait until all the commands are done before moving on:
#!/usr/bin/perl

use strict;
use warnings;

my @cmd_list = ( 'echo 1', 'echo 2', 'echo 3', 'echo 4' );

$|++;  # turn off buffering

my $shpid = open( my $shh, '|-', '/bin/bash' ) or die "Can't open a shell process: $!\n";

for my $cmd ( @cmd_list ) {
    print $shh "$cmd\n";
}
print $shh "exit\n";
close( $shh );
waitpid( $shpid, 0 );
print "Shell's all done.  Moving right along...\n";
________________________________________________________________




If you want more control, then consider these alternatives:
1) open
2) fork & exec
3) IPC::Open2 or IPC::Open3


#installing modules manually through terminal!!!:
cd into untarred gunzipped directory
perl Makefile.PL [LIB=/path/to/custom/lib/you/want]
make
make test
sudo make install

package S::Should::Be::Scoped::With::Curlies{
	#packages do NOT need to end with a 1.  Modules DO.  That is, the module FILE must end with a 1.
}

"use Module LIST" is EQUIVALENT to "BEGIN { require Module; import Module LIST; }".  Therefore "require..import" is a good choice when it's possible you won't need the module at all, and the module takes a long time to load. require can accept an EXPRESSION, so if you need more control, require!  "no" calls the "unimport" function.  i.e.  "no Moose;".
"use vars" and "use subs" are packagely (globally means packagely) scoped, while "no Module" is lexically scoped!
use vars qw($frob @mung %seen); is simply a way to predeclare package var names.  Perl prefers you use "our" declarations instead.  There is only one difference between "our" and "use vars".  "our" is lexically scoped, just like "my".  "use vars" crosses across all scope (but stays associated with the current package).

CPAN --> use "o conf init" in terminal to re-configure CPAN.

Perl Language Standards (CPAN):
ModuleNames use CapWords
function_names use snake_lowercase (snake_case)

#simplest example of exporting:
#port.pm:
package port;
use vars qw(@ISA @EXPORT);
use Exporter;
@ISA = ('Exporter');
@EXPORT = ('func');
sub func{
  print "func ran!\n";
} 1
#port.pl:
use port 'func'; #this gets 'func' but not 'port'. If you want both, do ':DEFAULT', 'func'
func();

#there may be some sort of autoexporter for advanced modules.  I can do "use POSIX; floor(4.5);" without importing 'floor' specifically.  Look also into autoload.


MOOSE EXAMPLE
package subclass;
use Moose; use namespace::autoclean;
extends 'vehicle';
has 'spoiler' => ( is=>'rw', reader=>'rspoil', writer=>'setSpoiler', trigger=>\&check_spoiler ); # allows you to rename the read and write functions.
sub check_spoiler{
	my( $subclass, $newspoiler, $oldspoiler ) = @_;
	#check stuff!
}
# reader and writer are optional, as the name 'spoiler' can be used to both read and write.
__PACKAGE__->meta->make_immutable;
1





use Tie::IxHash;

    # simple way to use (no need to use hash object itself)
    tie( my %hash, 'Tie::IxHash', a=>1, b=>2, c=>3 ); # from now on, it's all in order!!!
    %hash = (first => 1, second => 2, third => 3);
    $hash{fourth} = 4;
    @keys = keys %hash; print @keys;
    @values = values %hash; print @values;
    print("y") if exists $hash{third};

this takes a regular hash and cements its order!


use Module qw(:DEFAULT :constants);
instead of typing it twice!!!

mojolicious tutorial for non blocking web services!!!!! great website w/ lots of tips and best practices!
http://tempi.re/a-mojolicious-non-blocking-web-service-why-

challenges:
http://www.learning-perl.com/2012/04/learning-perl-challenge-tripwire/
http://en.wikipedia.org/wiki/Longest_common_subsequence_problem
For a more robust way, this module sounds great:
http://search.cpan.org/~bzajac/Proc-Background-1.10/lib/Proc/Background.pm

fork(), $$ = the current PID, getppid(), wait(), waitpid()
a process terminates.
wait() waits for ANY child to terminate and returns the pid of the deceased process. (naturally, exit status will be in $?)
waitpid() is what you'd expect, returning the same thing, or -1 if there is no such process.
waitpid(-1) is the same thing as wait()
but waitpid allows the following flag!!:
$kid = waitpid(-1, WNOHANG); # Wait NO HANG means
SIGINT is the signal (integer) sent to the process whenever you Ctrl-C, SIGSTP is from Ctrl-Z
when a child dies, it sends a SIGCHLD to the parent
signal handlers interrupt processes in what they are doing.  for some, it terminates process, for others, it stops process (pause).  for some, it creates core image, which is to dump the state of the program so it can be debugged later.
exec() executes a command in the current process!
exec never returns, except in rare case that input was not a shell command. use array input to avoid a grammar mistake, like confusing shell string syntax.
use exec { "this is" } "it" to run command "this is" with arg "it", as opposed to exec "this is", "it", which will run command "this" with args "is" and "it".
This can also be done with exec $command "and", "stuff".  Notice the ABSENCE of a comma after the command!  Just like how we differentiate in print!!!
 exec {'/bin/csh'} '-sh';  # pretend it's a login shell


.ep means embedded perl

$string = "this is a Foo case";
$string =~ s/(Foo)/preserve_case($1, "bar")/egi;
	# a s///g in scalar AND array context returns the number of substitutions.
	#a m// returns the match itself.
	#m//g in array context returns an array of all matches.
	#m//g in scalar context returns 1 for match, undef for none.
print "$string\n";

http://mojolicio.us/perldoc/Mojolicious/Controller

a // b. is equivalent to defined a? a: b;
a //= b is shorthand for a = a//b.

All of Perl's Special scalars special variables:
http://affy.blogspot.com/p5be/ch12.htm



if you put parenthesis when declaring a function, you are designating it as a no input function.
sub first() {
  my $x = 1;
};



http://mojolicio.us/perldoc/Mojolicious/Guides/Cookbook

  if (my @unrecognized_options = grep { not exists $$default_options{$_} } keys %$supplied_options) {

   local $" = ', '; array delimiter!!


@ISA "is a" list of parent classes of the class (class=package)

use vs require

$] is the running version of perl!

use experimental 'smartmatch';-->a cpan module which gets rid of the warnings.
el ~~ arrayorarrayref
key ~~ hashorhashref
arrayorref ~~ arrayorref
hashorhashref ~~ hashorhashref checks the keys
personal preference: when using references, DO retrieve the actual array or hash with @ or %.  This explicitness will make it clear in the code what it is you are comparing!



.cpan and .cpanm are in the ~ directory.

#!usr/bin/env perl uses your ENVIRONMENT perl

i created /usr/local/Library/Perl/5.16/Modules/Downloads for downloaded stuff and /usr/local/Library/Perl/5.16/Modules/MattCreated for my own stuff!

array of hashes.and loading more than one key of a hash at a time!!!
my @records;
my @cols = qw(surname firstname job);
while <DATA>{
	my %rec;
	@rec{@cols} = split /,/;
	push @records \%rec;
}
__DATA__
lancellotti, matthew, extraordinaire
muddasani, mohith, googler


our cannot jump out of a function! really!
you can only localize global variables (not lexical) really!

diff btw local and my is declaration!

use strict is good practice.
use warnings is good practice!
when you use strict, you must say "our" for globals.  Globals become part of the 'main' package.  our $var is the same as $main::var.
"our" makes it a package var.  If I was in a package Package, and used 'our', then that var would be global to the package, and it would be $Package::var.
Package var.s can be predeclared with "use vars" or "our".  Like so:
use vars qw($var @arr %has);
our ($var, @arr, %has);
"my" makes lexical var ("lexical" because scope purely defined by the "text"), which is for it's containing block.
"local" is WHAT HAPPENS IN THE BLOCK STAYS IN THE BLOCK.

"state" variables are lexically scoped, but do NOT reset.  Almost like a lexically scoped global:
use feature 'state';
sub f{
	state $l; print $l++
}
f(); f();


lvalue
A left value is an expression which has at least a semi-permanent address in memory.  For example, $x is an lvalue.  A right value is an expression which is not a left value.
lvaluable
Able to serve as an lvalue.
An lvaluable function or expression is one to which a value may be assigned, as in pos($x) = 10 .
lvalue modifier
An adjectival pseudofunction that warps the meaning of an lvalue in some declarative fashion. Currently there are three lvalue modifiers: my, our, and local.

variables in perl are reference counted!  So you can take the reference of a temporary array, and then it has a ref count of 1, and therefore it will store it (no longer temporary)


for single quotes, qy...y, that y really means the end.  Any y's inside need escaping with \y.  So the \ means look ahead to next character.  If y, then great!  If \, then \!  That is, \\ means \.  So BOTH y's and \'s have escapes.  \ doesn't NEED to be escaped except when followed by a \ or y. (think about it)

Well, thing about this.  We can't LOOK AHEAD, so we HAVE to gobble up the next character, and then poop a result.  This is why if I wanted to get "\y", i would have to type \\\y, not \\y.


what is Filter.pm ? source filtering
need to learn:
I bet that $? contains the exit information (where exit status is $? >> 8) and $! contains the error during execution if it failed. I'm not sure where STDERR goes to.

If you want more control, then consider these alternatives:

1) open
2) fork & exec
3) IPC::Open2 or IPC::Open3

bash and perl have the SAME heredocs behavior!!!!
$referencestohashesandarrays->{'use'}->{'arrows'}.    This really depends on the reference naturedness of the ROOT.  After that, everything is a reference anyway.
$hashesandarrays{'donot'}{'usearrows'}
Is it a number? NaN and Infinity, std from C:
http://www.perl.com/doc/FMTEYEWTK/is_numeric.html
map {block with a list in it} indices not nec in paren;  this will take the list and push into an array, or hash, or anything accepting a list indices times.
ex: map { $_, $_ + @a } ( 0 .. $#a )
{ } is for hashes what [ ] is for arrays!
multilevel
5.10 and later you can use the associative array %+ to get the text matched by named capturing groups. For example, $+{name} holds the t
Getopt::Long!!
regular s/search/rep/g will find ALL matches, and THEN replace them.
while while (s/search/replace/) will repreate the s/search/replace/ from the beginning of the string each time, as expected.
For intuitive comprehension, it is easy to think of ( ) as a "capture", which does not include (?:).
split WILLNOT include the regex match, but it WILL include captures within the regex, each as there own element.  Captures within captures do not get singled out.
split will include empty fields at the beginning, but not at the end.  If you want at the end too, use split( /regex/, @array, -1 );

for the VERY IMPORTANT purpose of not having to look up the input of a function every time, we should by default always pass array references instead of arrays.
subarrays!  ---> use @array[0,2,4,whateverelementsyouneed!,9..20] #9..20 is a LIST shortcut called "range operator" so can be used in ANY list situation.
return (a,b,c) returns a literal array.  If taken in as a SCALAR, then you get the last element.
@l= (a,b,c); return @l returns an array.  If taken in as a SCALAR, you get the length, as expected.
if you write $arr[-1], it gives you the last element of the array.  That's right, IT CAN GO BACKWARDS (it doesn't cycle though)

?^ a fresh beginning (you can have a regex group with it's very OWN set of modifiers)
more regex:
http://perldoc.perl.org/perlre.html
you can also use quotemeta which makes everything literal by backslashing everything except for letter, numbers, and _
http://perldoc.perl.org/functions/quotemeta.html

the special \K option.
?(1)(?!") is a CONDITIONAL statement.  IF group 1, THEN lookahead for not ".  Whatever immediately follows the (1) is the THEN. stops at a pipe.
(?R) is recursive entire regex, and (?1) is recurse group 1 of regex, and so forth...
(?<NAME>...) is a named capture group, and (?&NAME) calls it again (can be used recursively), and $+{NAME} is the replacement variable with that capture.
tr counts things!  ex $count = $string ~= tr/p//; will tell you how many p's!
regex/e evaluates the replacement string as perl code. So the replacement is what the code returns.
regex/x extended. includes recursive regex!
regex/m multiline.
regex/s . matches newlines too.
regex/o compile only once. (for variables in a regex, if they change it won't update)
regex/p	When matching preserve a copy of the matched string so
        that ${^PREMATCH}, ${^MATCH}, ${^POSTMATCH} will be defined.
s/reg/r return the result of the substituted string AND LEAVE THE INPUT STRING ALONE
/adda${variable}into your regex!/
qr/isaregexflavorquote/ (?^isaregexflavorquote)
qr/isaregexflavorquote/i (?^i:isaregexflavorquote)
use POSIX; ceil and floor.
eval is a security risk why?
https://www.securecoding.cert.org/confluence/display/perl/IDS35-PL.+Do+not+invoke+the+eval+form+with+a+string+argument
overload operators!!!!!
http://perldoc.perl.org/overload.html
push, pop, shift, unshift.
splice spliced and dices.  It's only really usefulness is to "push" things into the middle of the array.  For everyting else, you could set the array equal to a subarray of itself. splice is NOT subarray[0,2,3] substr($str,begin,length) or substr($str,beginindex,-backwardsindex)

http://www.misc-perl-info.com/perl-array-functions.html
good resource!!!!
EVAL: can use SINGLE quotes to function properly.  we don't want the strings interpreted when eval is going to do that for us!
however, if you want a variable to be replaced with its contents, and then eval THAT, use double quotes.
But you mine as well use eval{ code here } over single quotes because that will trap errors, and you can see color syntax.
http://www.caveofprogramming.com/frontpage/articles/perl/perl-eval-using-eval-to-run-code-and-trap-errors-in-perl/
file tests, etc.
http://www.cs.cmu.edu/afs/cs/usr/rgs/mosaic/pl-exp-op.html
range operator .. when used on SCALARS is a special tool.
@a = (9..89)

x= for scalars.   x can be used for arrays too!   @eightyones = (1) x 80; wow!   @eightyfives = (5) x @eightyones (makes an array of 5's which takes the SCALAR(length) of @eightyones)  (1,2) x 6 yeilds (1,2,1,2,1,2,1,2,1,2,1,2,1,2,1,2) as expected.
something like \w+ (.*)thop can match an empty string in which case $1 eq ''.

defined is a function which tells you if it's defined
undef is "undefine", a function which undefines the variable (but it's still declared). Can be used on $s, @a, %h, &subroutine do NOT use paren because that is a subroutine call, whereas &subroutine is a subroutine name!, and *typeglob (meaning that $typeglob, @typeglob, %typeglob, and &typeglob all get undefined!)
use delete to get rid of a $hash{'key'}
if the EXPR is emitted from undef, you still get an undef value that you could pass or return.  Hence the other use of undef as a 'value'.

NOTDECLARED(not initialized):
DECLARED(initialized): $a; @a; use exists for subs (&this), hash keys ($hash{'key'}), and array elements ($array[3]) (deprecated for array elements)
DEFINED: $a=''; @a=(); but we don't use defined with arrays anymore.  defined $hash{'key'} will tell you if the VALUE is defined. (undef is not a defined value as expected)
NONEMPTY: $a='h'; @a=('h'); We use if(@a) and if(%h) which will be true if the size is not zero.

ref tells you what type of variable a reference points to! "if (ref($r) eq "HASH") {".  see http://perldoc.perl.org/functions/ref.html


join() is the complement of split()!
$/ is a special variable that tells < > where to read to.  By default, it's '\n'.  If you change it to another character, <FILE> will grab up until that character!
local $/ = undef means that <FILE> will get the whole file!
you CANNOT use length() to get the length of an array.  it's for STRINGS ONLY. Use scalar(@array) for that, or just understand that when you need a number, perl will automatically give you the scalar of the array.  scalar() is only needed in ambiguous situations.
ALWAYS USE , to concatenate in print statements, because you CANT concatenate an array.
$0 - is the program!
@ARGV contains the passed arguments!!!
rand() - randnum btw 0 and 1
if, elsif, else; all NEED {} because they are treated as a once executed BLOCK (loops use blocks)
open( my $fh, '<', "path/to/file.txt") or die "No file :( $!";#NO SLASH AT BEG OF PATH (auto adds ./), OR USE ABSOLUTE PATH
{ local $/ = undef;
$data = <$fh>;
}
old:
while( <FILE> ){
	chomp; #when no input, chops $_.
	print ("$_\n"); # $_ is the first line.
}

$_ is the default variable.  so this is while $_=<FILE>,chomp $_, print etc.....
close( FILE );	
=being comment
=end comment
=cut
`backticks` performs it in a separate shell (you don't see the output because it is in separate shell, but can use $?)
system("code"); #you can see output because the output is redirected from separate shell to the current terminal output!  (you can use $?, which it also returns)  $? is the terminal success (0) or failure (nonzero).
system(@a) where @a = ("command","arg1","arg2"); #is also acceptable 
 if ($? == -1) {
        print "failed to execute: $!\n";
    }
    elsif ($? & 127) {
        printf "child died with signal %d, %s coredump\n",
            ($? & 127),  ($? & 128) ? 'with' : 'without';
    }
    else {
        printf "child exited with value %d\n", $? >> 8;
    }
localtime and it's two formats
The operating system. i.e. 'MSWin32'****************************************************
use English;
print "$OSNAME\n";

use Config;
print "$Config{osname}\n";
print "$Config{archname}\n";

@-, $-[0], gives LOCATION not letter (1st character is 0)
@+, $+[0], give LOCATION of end of match
in terminal: cpanm Module::Name (to install)
print to file:
open( FILE, '>>output.txt');#appendmode, use > for fresh mode
print FILE "yo";
close( FILE );
all system commands are executed from the directory that the TERMINAL was in when the perl program was launched.  This is not necessarily the same directory that the perl program is in. For example, in ALFRED ITS RUN FROM WORKFLOW FOLDER.  and applescripts are executed from the root / unless you cd first.
open multiple files: 

"GLOBBING"
my @files = glob("*.h *.m"); # matches all files with a .h or .m extension  --> specifically for files/paths!
* anything, any length (doesn't go through slash)
? anything, one character
[ ] and [^ ] just like reg exp
** any combination of path components (DOES go through slash) --> may not work in bash.  globbing is what we use in the TERMINAL instead of regular expressions!  yay!
{this,or,this,or,that}


system("touch a.txt"); # linux command "touch a.txt" which opens or creates the file.
if alternatives, false: undef, 0, '', and "0". true: everything else.
comparing values, strings
die and warn-- for errors $! for the error string!.
a lot of times you can use commas instead of ;
continue, last(BREAK), next, redo
my declares var. to be local to enclosing block, file, or eval RECOMMEND USING IT FOR OBJ ORIENTEDNESS
shift, shift(@array)
%hash = @array;
split vs. splice
index($string,$char) index($string, $substring) returns first index, or -1 ***************************
null (\0).  \0 is rare, a special character.
hash --> see hash.pl **************
how to initialize and make objects!
importing / exporting constants: http://stackoverflow.com/questions/193020/how-do-i-use-constants-from-a-perl-module


What to learn next:
cmp string comparison, returning -1, 0, or 1
<=> numeric comparison, likewise
reading inputs from a webpage (URL) (PHP??)
make program that uses hash
make program that uses objects
sorting (see fundamentals website)
performing s/replace into a new variable without changing old one.
perform regex on as a function.
POSIX module
http://stackoverflow.com/questions/178539/how-do-you-round-a-floating-point-number-in-perl
printf printing.
binary(bitwise) shifting!!!!   1001 > ?         ^ means xor!!!!!! can use word "xor" too! For binary numbers, start w/ 0b. For octal, start with 0, for hexadecimal, start with 0x
arrays in arrays:
http://perldoc.perl.org/perlreftut.html#Who-Needs-Complicated-Data-Structures%3f

good resources:
mag-sol.com/talks/perlwhirl/idiomatic.pdf
http://www.tutorialspoint.com/perl/perl_hashes.htm
perlbrew.pl (a website)
http://perl-begin.org/learn/get-a-job/
challenges:
http://www.learning-perl.com/2013/04/learning-perl-challenge-remove-intermediate-directories/
examples:
http://www.misc-perl-info.com/perl-operators.html


about loading .pm's:
perl -V will print out various properties about your Perl installation, including the default @INC. You should notice a . in there: yes, the current working directory is searched for modules by default.

The @INC array is set when perl is compiled, but can be altered by the program, with the -I command-line switch, or by the PERL5LIB (lib for library!) environment variable.

  terminalcommand$ PERL5LIB=also perl -Ilib -E 'say for @INC'
  lib
  also
  /usr/local/lib/perl/5.10.0
  /usr/local/share/perl/5.10.0
  /usr/lib/perl5
  /usr/share/perl5
  /usr/lib/perl/5.10
  /usr/share/perl/5.10
  /usr/local/lib/site_perl
  .

Also, in a applescript use
do shell script "cd /Applications/bigperl.app/Contents/Resources/Scripts;
perl crisscross.pl"

instead of
do shell script "cd /Applications/bigperl.app/Contents/Resources/Scripts"
do shell script "perl crisscross.pl"

because the second one is two SEPARATE terminal sessions, each starting at the root

for future more complicated error checking...http://www.tutorialspoint.com/perl/perl_error_handeling.htm
