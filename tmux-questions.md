tmux bind r source-file ~/.tmux.conf


"#[fg=Green]#(whoami)#[fg=white]::#[fg=blue] (hostname - s)#[fg=white]::##[fg=yellow]"



tmux Questions for Mo
==================================================


Is there a built-in ssh connecto feature so I don't get double tmux bars?  Is there a "right way" to connect to servers w/ tmux?  Where should the session belong?


How to move a window to a different session?
How to have the SAME window present in MULTIPLE sessions?

	dunno, i get the feeling that sessions are completely independent of each other. i could be wrong

How to have TWO people connected to the SAME session?

How to bind a GLOBAL keyboard shortcut to a tmux command (in particular, toggling windows)?

	/etc/tmux.conf

How to make the tmux config WORK?

How to force reload the config after an update?

	use an editor like vim and program it to auto-update tmux upon writing to a tmux.conf file :)

How to have tmux open zsh by default, not bash?

	http://superuser.com/questions/253786/how-can-i-make-tmux-use-my-default-shell

How can I put more spaces between the windows in the window list?  Can I change the * to parenthesis around the window name instead?

Is there a way to SAVE tmux sessions so that if tmux dies for some odd reason, you're ok?
see capture-pane