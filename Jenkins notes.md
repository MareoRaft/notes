The `sh` directive in Jenkins executes its contents in an sh-subshell.  Hence,

	sh "pwd"
	sh "cd .."
	sh "pwd"

will result in the SAME directory path being shown twice.
