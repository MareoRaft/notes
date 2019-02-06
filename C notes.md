Both char* p and char *p make sense.  But in func( int* p ) vs func( int *p ), the former makes more sense.  Therefore I favor a left justified star!

%n.mf for formatted floats.  At least n digits wide (space fill if necessary), and exactly m decimal places.


C++11 STUFF
___________________________________________
an lvalue ref is NOT a ref, but rather an alias.
int x = 23;
int & l = x;
Now, l and x can be used interchangeably.  An lvalue ref can be created for any lvalue.  It may also be set equal to an rvalue expression, in which case memory is alloted for it:
const int & l = 73+9;
The "const" is necessary.
___________________________________________
an rvalue ref is an lvalue, but REFERS to an rvalue.
int && r = a+4;