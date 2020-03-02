fetch function
---------------
fetch is builtin to javascript
https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch



you might not need jquery!
vanilla JS replacements of jQuery libraries!
http://youmightnotneedjquery.com/


nodejs
--------
how to create a standalone executable/binary file from a nodeJS script:
https://dev.to/jochemstoel/bundle-your-node-app-to-a-single-executable-for-windows-linux-and-osx-2c89


npm
------
npm install --no-package-lock
will install without modifying package-lock
npm install --production
will install based on package-lock instead of based on package (i THINK.  NOT verified)


SYNTAX CHECKING
-----------------------
npm install --global esprima
esvalidate path/to/file.js



HTM
------
  * uses template literals instead of jsx html snippets
  * like react but w no transpiling!!!
  * download the powerpoint on the gdg slack channel for more info
  * babel-plugin-htm
  * lit-htm



REACT
--------
  * uses jsx which is like javascript but w html snippets in it
  * has to be transpiled
  * could follow a functional approach



MATERIAL DESIGN
-----------------
  * a google UI thing
  * material.io
  * gallery.io
  * pocket cast
  * material plugin for Sketch.app allows you to choose colors and change around designs in a smart/efficient was and preview what the app would look liked!
  * from Sketch you can upload the gallery, so ppl can view your design
  * in Gallery, you can click on things and get design information: color, width, object type, documentation for that object
  * in the future, it might generate code for you
  * also download the powerpoint from slack and put it in this folder









TYPE CHECKING
-------------
www.npmjs.com/package/check-types


REQUIRE
-------
with comments for viewing:
http://requirejs.org/docs/release/2.1.16/comments/require.js
load script to use: // this is not really a CDN
http://requirejs.org/docs/release/2.1.16/minified/require.js


R.JS REQUIRE OPTIMIZER
----------------------
node
builder/r.js
-o
mainConfigFile=www/scripts/main.js
baseUrl=www/scripts/lib  # even though it takes in the config file, it stupidly doesn't know the baseUrl, so you need to tell it anyway
name=../main  # this is the path to the file you actually want to optimize, RELATIVE TO the baseURL and without the .js (how you would call it in require())
out=www/scripts/main-rified.js
optimize=none

for example, type this in terminal:

node builder/r.js -o mainConfigFile=www/scripts/main.js baseUrl=www/scripts/lib name=../main out=www/scripts/main-rified.js generateSourceMap=true preserveLicenseComments=false optimize=uglify2

Alternatively, you can put the options in an object in parenthesis ({ mainConfigFile: 'www/scripts/main.js', etc }) and save it as something like mybuild.js.  Then you can run node -o mybuild.js.  In this case, the paths are now relative to the location of mybuild.js, not the current directory of the terminal.

Apparently Google's "Clojure Compiler" removes unused JS code, which r.js does not do.
https://developers.google.com/closure/compiler/


SEMICOLON INSERTION
-------------------
http://inimino.org/~inimino/blog/javascript_semicolons

semicolons can appear at the end of (exhaustive list):
  1. do Statement while (Expression);
  2. var something;
  3. 4+4; f(); // Expressions
  4. continue;
  5. break;
  6. return stuff;
  7. throw 'custom error'; throw 500; // throw statements
  8. debugger; // a debugger pause point!
  9. ; // the empty statement, which maybe is an expression an need not be mentioned here
Finally, semicolons can appear in for( ; ; ) and inside 'strings;' and /regexpliterals;/


The rules of adding semicolons:
  1. When the program contains a token that is not allowed by the formal grammar, then a semicolon is inserted if (a) there is a line break at that point, or (b) the unexpected token was a closing brace.
  2. When the end of a file is reached, if the program cannot be parsed otherwise, then a semicolon is inserted.
  3. When a "restricted production" is encountered and contains a line terminator in a place where the grammar contains the annotation "[no LineTerminator here]", then a semicolon is inserted.
  4. Exceptions: semicolons never added in for loop.  Semicolons never added if they result in an empty statement.

restricted productions:


RECOMMENDED RESOURCES
---------------------
http://www.smashingmagazine.com/2009/02/08/50-extremely-useful-javascript-tools/
http://www.adequatelygood.com
http://www.javascriptkit.com
http://scripterlative.com

RECOMMENDED COURSES
-------------------
http://www.pluralsight.com/courses/javascript-fundamentals-es6
http://www.pluralsight.com/courses/javascript-jquery-advanced-techniques
http://www.pluralsight.com/courses/requirejs-javascript-dependency-injection

ES6 COURSE STUFF
----------------
http://plnkr.co --> write code in JS ES6!  Use traceur to convert to ES5 for use in real world. --> ppl now prefer 6to5 --> look at -->
	http://www.pluralsight.com/courses/discussion/javascript-fundamentals-es6 --> try searching for "Npm install gulp-6to5"
google "es6 compatibility table" --> very useful



setAttributeNS is setAttribute NAMESPACE and

setAttribute( this, that ) is just like
setAttributeNS( null, this, that ) except that the orig. setAtt had some flaw, so the second one is recommended, esp. for SVG stuff...

double quotes are necessary for attribute values. (no single)


evt:
http://www.javascriptkit.com/jsref/event.shtml



.getAttribute()
.setAttribute()
.removeAttribute()

These methods can be used on any element that supports attributes.

.getAttribute()

GetAttribute() retrieves the corresponding value of an attribute. If the attribute does not exist, an empty string is returned. For example:

<img id="myimage" src="test.gif">

<script type="text/javascript">
//returns "test.gif"
var getvalue=document.getElementById("myimage").getAttribute("src")


FUNCTIONS
---------
  * (function(p){alert(p)})('k')  //alerts k.  The parenthesis are NECESSARY to make the function a valid expression before executing it.
  * (function(p){alert(p)}('k'))  //same as above.  Here, the executed function needs parenthesis to make it a valid expression.
  * closures are created WHEN THE FUNCTION IS RETURNED.  Therefore if you use a variable in a loop, you could end up with the wrong variable if you don't return until end of loop.
  * if something returns a function, postfix it with () to execute it!  i.e.  ireturnafunction()()


MISCELLANEOUS
-------------
  * javascript is pythonic in that everything is an object.  Semicolons too.
  * E6 has Class and import statements like Python
  * E6 expect(x).toBe(y) is for error checking!
  * E6 [x,y] = [2,8] the right side is an array literal, but the left side is "destructuring" syntax, so JS knows to assign. like Python. objects too:
fuction objlit(){
	return {
		a: "hi",
		b: "bye",
		c: { epsilon: 0.2, delta: 0.1 },
	}
}
let { a: x, b, c: { delta: t } } = objlit()
expect(x).toBe("hi")
expect(b).toBe("bye")
expect(t).toBe(0.1)
expect(reshths).toBeUndefined()
function foo( pop, { oats, barley } ){ // destructing used here!
	alert(oats)
}
  * E6 function( name="defaultval" ){ ... like Python! Only gives default when input is undefined! :)
  * E6 rest parameters are real arrays, meant to replace "arguments", which is an array-like object:
function( some, parameters, ...resty ){ // a rest parameter must be last, and takes the "rest" of the arguments.
  * E6 the spread operator, "...", is a flattener, not to be confused with rest parameter: let a = [ 2, 3 ]; let b = [ 1, ...a, 4 ]
  * E6 template literals are `strings with ${drop-in-expressions+"!"}`
  * tags are functions that take in template literals as array of strings followed by array of drop-ins


HOISTING
--------
Following is the order in which things are done within a scope:
function( formal, parameters ){
	// then all functions declared/defined in this scope are here declared/defined
	var this; //this variable cannot be overwritten.  "this" always refers to the Object which owns the function! :)
	var formal;
	var parameters;
	var arguments;
	// then all vars declared in this scope are here declared
	// finally, we run the actual code, leaving out what has already been done above
}


SCOPING
-------
Only FUNCTIONS create a new scope.  Block statements such as IF and FOR do not create a new scope!
(source: http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html )
(function () {
			var x = 2;
			// this is a workaround to make your own scope block
alert('ut')
}())
In E6, we can use "let" intead of "var" for block scoping.  "let" cannot be redeclared.  "const" is like "let", but errors reassignment


OBJECTS
-------
  * obj.key3 = "value3"; sets a key
  * obj["key3"] = "value3"; sets a key and ALLOW VARIABLE INPUT
  * if( "key" in obj )  // checks for key existance in an object (even if the value is undefined)
  * for( var key in obj ) //loops through the keys of an object, where our variable key is the keyname, and therefore obj[key] is the value.
  * delete obj.key //will delete or verify a key is not there, then return true
BUILT-IN OBJECT PROPERTIES
Arrays, strings, and numbers are objects too!  They inherit these properties too!
.toLocaleString(), .toString() - what we see when we alert a variable.
.valueOf() - valueOf is used by comperators.  Overload it if you want your objects compared a certain way!
.hasOwnProperty() - returns true if object has the property (does NOT check prototype chain (hasOWNproperty))
.isPrototypeOf()
.constructor - refers to the method which constructs the object.  You can build your own constructor with function ObjName(){...}
and many more!
  * ES6 instanceof - for example, if( myemployee instanceof Person ){...


ARRAYS
------
  * The native .map() method can be used on arrays.  It creates a COPY and does NOT modify the inputted array.
  * .indexOf() will take in a value and give you the index
The array prototype has the following methods:
.length,
.shift(), .pop()
.unshift(), .push() - DIFFERENT than Perl's push.  Input is list of 1 or more ELEMENTS - see .apply
.reverse(), .sort(), .reduce(), .join(), .slice()
and many more!


STRINGS
------
  * .indexOf() will take in a string to find within, and give you the index of the starting char (as if the string is an array of characters)
The string prototype has the following methods:
.length
.charAt(), .trim()
.concat()
.replace() - uses regex
.toUpperCase(), .toLowerCase(), .substring()
and many more!


NUMBER
------
The number prototype has the following methods:
.toFixed(), .toExponential(), .toPrecision()
and many more!


FUNCTIONS
---------
the function prototype has these methods:
.name
.bind(), .call(), .apply()
and many more!



RANDOM
------
http://stackoverflow.com/questions/10331305/what-is-define-used-for-in-javascript-aside-from-the-obvious
