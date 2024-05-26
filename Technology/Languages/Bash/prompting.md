#shell #bash  
from man:

When  executing  interactively,  bash displays the primary prompt *PS1* when it is ready
 to read a command, and the secondary prompt *PS2* when it needs more input to 
 complete a command.  Bash displays *PS0* after it reads a command but before
 executing it.  Bash displays *PS4* as described above before tracing each command 
 when the `-x` option is enabled.
#### shell variables
*PROMPT_COMMAND*
	  If set, the value is executed as a command prior to issuing each primary prompt.
	   for example: `PROMPT_COMMAND='stitle $ROBOT'`, this will call the predefined function *stitle* with the parameter `$ROBOT` after every executed command.
*PROMPT_DIRTRIM*
	  If  set  to  a number greater than zero, the value is used as the number of trailing directory components to retain when expanding the `\w` and `\W` prompt string escapes (see
	  [[#customazation escaped special characters]]).  Characters removed are replaced with an ellipsis.
*PS0*    The value of this parameter is expanded (see PROMPTING below) and displayed by interactive shells after reading a command and before the command is executed.
*PS1*    The value of this parameter is expanded (see PROMPTING below) and used as the primary prompt string.  The default value is ``\s-\v\$ ''.
*PS2*    The value of this parameter is expanded as with PS1 and used as the secondary prompt string.  The default is ``> ''.
*PS3*    The value of this parameter is used as the prompt for the select command (see SHELL GRAMMAR above).
*PS4*    The value of this parameter is expanded as with PS1 and the value is printed before each command bash displays during an execution trace.  The first character of  the  expanded value of PS4 is replicated multiple times, as necessary, to indicate multiple levels of indirection.  The default is ``+ ''.

#### customazation escaped special characters
Bash allows these prompt strings to be customized by inserting a number of backslash-escaped special characters that are decoded as follows:
  
`\a`     an ASCII bell character (07)
`\d`     the date in "Weekday Month Date" format (e.g., "Tue May 26")
`\D{format}`
		 the format is passed to strftime(3) and the result is inserted into the prompt string; an empty format results in a locale-specific time representation.  The braces
		 are required
`\e`     an ASCII escape character (033)
`\h`     the hostname up to the first `.'
`\H`     the hostname
`\j`     the number of jobs currently managed by the shell
`\l`     the basename of the shell's terminal device name
`\n`     newline
`\r`     carriage return
`\s`     the name of the shell, the basename of $0 (the portion following the final slash)
`\t`     the current time in 24-hour HH:MM:SS format
`\T`     the current time in 12-hour HH:MM:SS format
`\@`     the current time in 12-hour am/pm format
`\A`     the current time in 24-hour HH:MM format
`\u`     the username of the current user
`\v`     the version of bash (e.g., 2.00)
`\V`     the release of bash, version + patch level (e.g., 2.00.0)
`\w`     the current working directory, with $HOME abbreviated with a tilde (uses the
		   value of the PROMPT_DIRTRIM variable)
`\W`     the basename of the current working directory, with $HOME abbreviated with a 
		  tilde
`\!`     the history number of this command
`\#`     the command number of this command
`\$`     if the effective UID is 0, a #, otherwise a $
`\nnn`   the character corresponding to the octal number nnn
`\\`     a backslash
`\[`     begin a sequence of non-printing characters, which could be used to embed a
			terminal control sequence into the prompt
`\]`     end a sequence of non-printing characters

The command number and the history number are usually different: the history number of a command is its position in the history list, which may include commands restored from the history file (see HISTORY below), while the command number is the position in the sequence of commands executed during the current shell session.  After the string is decoded, it is expanded via parameter expansion, command substitution, arithmetic expansion, and quote removal, subject to the value of the promptvars shell option (see  the  description  of the shopt command under SHELL BUILTIN COMMANDS).

[[color]] could also be added as described [here](https://tecadmin.net/how-to-customize-bash-prompt-ps1-in-linux/)
for example: `PS1="\u@\h \[\e[32m\]\w \[\e[91m\]\$(parse_git_branch)\[\e[00m\]$ "`
