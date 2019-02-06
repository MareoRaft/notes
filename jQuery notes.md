jquery cdn:
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>

jQuery!!!!!!!!
learn from codeacademy.com.

APPEAR/DISAPPEAR
/*all of these functions take in the SPEED as the first arg. The optional second arg is a FUNCTION which will be fired upon completion of animation!*/
.show(s,f) .hide(s,f) .toggle(s,f)
/* here is a list of ALL jQuery effects methods: http://www.w3schools.com/jquery/jquery_ref_effects.asp */
/*speed can be # of milliseconds, 'slow', or 'fast'*/
.fadeIn(s,f) .fadeOut(s,f) .fadeToggle(s,f)
.slideUp(s,f) .slideDown(s,f) .slideToggle(s,f)

.fadeTo(speed,opacity)
.empty() removes all content of an element
.remove() removes an element

ALL ABOUT QUEUES!
http://www.w3schools.com/jquery/tryit.asp?filename=tryjquery_eff_queue_all


CSS STUFF
.css('quotedproperty','quotedvalue')
.height(newheight) .width('40px') have specific function b/c they are so common
ADD/REMOVE CLASSES
.addClass(classname) .removeClass(classname) .toggleClass(classname)
ANIMATE
.animate({ width:'+=9px' },s,f)

EVENTS
.mouseenter .mouseleave .hover
/*Hover can take TWO input functions.  The first is for mouseenter, the second for mouseleave!*/
.click .dblclick

VARIABLES
var $sel = $('css-style-selection') stores a jQuery selector as a variable!
turns out you CAN use dollars in variable names, and we choose to do so for jQuery variables as a good convention.

ADDING ELEMENTS
var $newel = $('<p>I am a new HTML element.</p>')
$('e').append($newel) will add a $newel after every matched e selection!
.appendTo reverses the order of the inputs
.append puts $newel as the last child of the selection
.prepend puts it as first child
.before puts it BEFORE the selection element
.after puts AFTER the selection element

MODIFYING ELEMENTS / GETTING ELEMENT VALUES
.html(content) //css selection is set of matches. Take first match, then display all of its content.
.val(content) //same as html, shows the value of the VALUE attribute of the element. This only works on elements designed to have a value attribute (input, output, etc)
.text() //concatenates all text (no html tags) from the entire css set
.attr('attributename')

ELEMENTS AFTER DOM HAS LOADED
$(document).on('event', 'selector', function() {
    $(this).dostuffyay
})
selectors will not work on elements which were added AFTER the dom has loaded.  Therefore, we must use the $(document).on which will recheck the document.



great font!:  font-family: Vivaldi, Cursive;