

Emacs Personal Command List
---
M-x rgrep --> search across files
C-h v user-emacs-directory --> see value of user-emacs-directory variable. Your init.el _should_ be in that dir if it exists.
C-x C-f --> find file / open file
C-g --> Quit command / bail on command / cancel / reverse

C-x C-f --> open file
C-s --> search within file
save C-x C-s
close C-x C-c

C-k --> kill line, kill the current line, delete current line
C-w --> kill selection

C-x 3 --> split window into two, side-by-side
C-x o --> go to other window
C-x 0 -> close INDIVIDUAL window
C-p --> close INDIVIDUAL window (personal alias)

C-x k --> close buffer


C-/ --> undo
C-g C-/ (C-/ one or more times) --> redo
M-g M-g --> go to line
M-x term --> open up a terminal within emacs (M-x shell --> dumb terminal) (M-x term or M-x terminal --> full term)
C-h m --> inspect key bindings
(key) C-h --> show all possible key completions for key prefix (key).
C-x C-f, RET RET, m per file, M-x dired-do-find-regexp-and-replace RET, <find_string> RET, <replace_string> RET, y per replacement (or ? for help) --> multi-fild find-and-replace
C-x TAB --> indent-rigidly. allows you to left/right shift all highlighted text (newlines) with left, right, S-left, S-right

M-x describe-key --> show what a certain keycut does

C-x C-f newfilename.txt RET C-x C-s --> Creates a new buffer and then saves it as a file.
