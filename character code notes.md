
Character Codes! (info from http://www.joelonsoftware.com/articles/Unicode.html)
================
*more reading: http://www.perlmonks.org/?node_id=862973


1. ASCII
--------

0-31 are ctrl characters, such as null character, end of file, escape, and carraige return.
    * the ctrl key subtracts 64 from the value of the key.  So since G is 71, ^G is 71-64 = 7, the BEL character.
32-126 are keyboard characters (anything you can type normally on your keyboard_
127 is DEL "Delete (rubout), cross-hatch box

The numbers to these characters can of course be called in octal and hexadecimal too.  128 = 2^7, so all this info is stored in 7 bits.  These are "7-bit characters".



2. OEM character sets
---------------------

There were still 2^8-2^7 = 128 bits left in a byte, and many companies created their own OEM character sets to use up the other 128 characters.  Different sets were used by different companies and countries, so this became a huge issue when transferring documents across borders.

For example, some PC's had 130 stand for é, but on computers sold in Israel, it standed for ג, so when ppl sent their résumés to Israel, the Israeli's got rגsumגs  :)

These are "8-bit characters", a superset of "7-bit characters".



3. ANSI Standard
----------------

This standard assigns a codepage number (e.g. CP 00874) to each of the OEM sets so that they are now distinguishible.  Lookup: http://www.i18nguy.com/unicode/codepages.html#msftdos



4. Unicode
----------

Attempted to create a SINGLE character set that contained all the characters. (oh my!)

A unicode letter bijects to a "code point".  For example, A <--> U+0041.  The number is hexadecimal.  Reference: http://www.unicode.org/charts/

There is no limit on the number of letters unicode can define.  Let's call these "unicode characters".



5. Encodings
------------

We have to store these code points into memory somehow!

U+0048 U+0065 U+006C U+006C U+006F

one way (high-endian UCS-2 because each char is 2 bytes, or UTF-16 because each char 16 bits)

00 48 00 6C 00 6C 00 6F

another way (low-endian UCS-2)

48 00 6C 00 6C 00 6F 00

another way (UTF-8 "Unicode Transformation Format 8")

UTF-8 stored each character (0-127) in a byte, and other characters in 2 bytes, or 3, or 6, depending on how high up it was.  This is backwards compatible with ASCII



