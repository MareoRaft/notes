COMMANDS
select v
select LINES V
cut d
copy y
paste p


VIM KEYWORDS
:syntax on
:set number
:set nonumber "follow same pattern to unset all things!
:set ignorecase "for matching!
:set smartcase
:set scrolloff=2


VIM COMMAND MODE
f finds next character you hit, F backwards
use NUMBERS with everything to repeat!
% goes to matching bracket.
next word under cursor *, previous #
insert in next line: o.  previous O.

v for VISUAL mode
shift v for VISUAL LINE mode
ctrl-v for VISUAL BLOCK mode: then I to prepend, or a to append  ".vimrc comments!
paste with p.  paste before cursor with P. "mark


when using REGEX: "all this!
:% s/regex/replace/options "the percent means wrap around the document!  Otherwise it only searches from cursor to end of document.
:% s&regex&replace&options supported!
PCRE regex: escape the repeaters: \+, \*, and \{n,m}
:/regex "then use n for next occurence, and N for previous occurance


OTHER
open file in terminal type "vim file.txt"
