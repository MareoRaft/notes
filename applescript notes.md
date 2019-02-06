return # Ends prematurely.  But this won't exit the script if you're inside a function.

delay 0.2 # this is like a pause, about 0.2 seconds

# functions:
on do_stuff(hi)
	display dialog hi
end

# function used with "to"
to plus_one(a)
	return a+1
end

# which you would then use with:
set theDigit to plus_one(37)

"this" & "that" # string concatenation

-- main
on run argv
	...print... item 1 of argv # grab arg's from command line!
end run

# key codes
tell application "System Events" to key code 31 using control down --down arrow
tell application "System Events" to key code 30 using control down --up arrow
tell application "System Events" to key code 29 using control down --right arrow
tell application "System Events" to key code 28 using control down --left arrow

in bean:
42 -- \
43 -- ,
45 -- n
46 -- m
47 -- .
48 -- tab
49 -- space
50 -- `
51 -- backspace
52 -- return

# key codes:
/System/Library/Frameworks/Carbon.framework/Versions/A/Frameworks/HIToolbox.framework/Versions/A/Headers/Events.h
(in hex)