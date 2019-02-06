Notes(SASS)


The SCSS (Sass CSS) formatting scheme is a superset of CSS3!!! Save as file.scss


MAIN SASS FEATURES:
variables, use #{$var} to insert into property names or selectors!
nesting
partials
import
mixins (...include)
extend (this is inheritance)
math operators (yay more supported math in CSS!!!)
define your own function!
built-in functions, there are a set of functions on colors, strings, numbers, more!!!! - http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html


COLOR FUNCTIONS:
lighten, darken, opacify, mix
alpha


OTHER STUFF:
!default is the opposite of !important
@for allows a C-style loop
@each allows a perl-style loop ( declare a list like so: "$list: 'this' 'that' 'andtheotherthing';" )