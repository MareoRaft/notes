last reviewed: 7/28/14

PURE REGEX:

? optional {0,1}
+ is {1,}
* is {0,}
{n,} and {,m} allows too or just use {0,m}
??, +?, *? makes reluctant.  avoid if possible
(?:non marking)
(marking)
(?=regex) look ahead!
(?<=regex) look behind!
\a
\b word boundary
[\b] backspace. Yes, really!  In Perl too! Whenever in a character class, \b is backspace.
\t tab
\n
\r return?
\s whitespace
. any character, but not \n. can option it in with s
\w \W
[^]
|
[a-c][1-6] ranges
\\
\.

http://perldoc.perl.org/perlrebackslash.html