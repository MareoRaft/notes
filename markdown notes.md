I think this is
Markdown.pl 1.0.1
.


This is [an example](http://example.com/ "Hover Text") inline link.

[This link](http://example.net/) has no title attribute.

This is [an example][id] reference-style link.

[id]: http://www.google.com

[foo]: http://example.com/  "Optional Title Here"
[foo]: http://example.com/  (Optional Title Here)
[foo]: <http://example.com/>  "Optional Title Here"
[foo]: <http://example.com/>  (Optional Title Here)


h*ello*there  <-- italic  
h**ello**there  <-- bold  
h__ello__there  <-- underlined  
h\*ello\*there  <-- actual stars

inline code!:  This `is` great!  
inline code!:  This ``is`` great!  
inline code!:  This ```is``` great!  etc

|| Table title ||
Centered column | Right justified column | Left justified column | Default justified column
:-: | -: | :- | -
1 | 2 | 3 | 4
5 | 6 | 7 | 8
9 | 10 | 11 | 12

images:
![alternative text for ppl who can't see image](/path/to/img.jpg "Optional title")

![](/path/to/img.jpg)

[blah blah blah]:


[//]: # (single-line invisible comment)
[//]: # (another single-line invisible comment)

[
this
is a multi-line invisible comment.
hel\lo, there!!! ( )) ////
many    {
lines!
you can never use the end-bracket character in a multi-line comment because it will terminate the comment prematurely.
]:

visible

![](web+graphie://ka-perseus-graphie.s3.amazonaws.com/4d030c3e02fcd2d296bb74f472a1fbe442cda214)

![](web+graphie://ka-perseus-graphie.s3.amazonaws.com/805ee25cee3be5d0147b38421250970b8b87345c)

![](web+graphie://ka-perseus-graphie.s3.amazonaws.com/f20c7e22fd1ddd26a25f3bbcb5d2c0bc5c072859)
