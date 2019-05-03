
# 'main' function
on run argv
	...print... item 1 of argv # grab arg's from command line!
end run

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

# string concatenation
"this" & "that" 

# this is like a pause, about 0.2 seconds
delay 0.2

# comments can begin with a hash # (like most shell / scripting languages)
-- or they can begin with a double dash (originally to applescript)

# Ends prematurely.  But this won't exit the script if you're inside a function.
return 



# key codes
-- down arrow:
tell application "System Events" to key code 31 using control down
--up arrow:
tell application "System Events" to key code 30 using control down
--right arrow:
tell application "System Events" to key code 29 using control down
--left arrow:
tell application "System Events" to key code 28 using control down

## key codes in bean:
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

## key codes in hex:
/System/Library/Frameworks/Carbon.framework/Versions/A/Frameworks/HIToolbox.framework/Versions/A/Headers/Events.h
