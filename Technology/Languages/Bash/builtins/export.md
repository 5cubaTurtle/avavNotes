#bash
`export [-fn] [name[=word]]` ...
`export -p`
	  The supplied names are marked for automatic export to the environment of subsequently executed commands.  If the -f option is given, the names refer to functions.   If  no
	  names  are  given, or if the -p option is supplied, a list of names of all exported variables is printed.  The -n option causes the export property to be removed from each
	  name.  If a variable name is followed by =word, the value of the variable is set to word.  export returns an exit status of 0 unless an invalid option is encountered,  one
	  of the names is not a valid shell variable name, or -f is supplied with a name that is not a function.

To export a variable to current shell: `export BR_DEBUG_BLD=1`
- to permanently export to **current** user add the `export` statement into *.bashrc* file
- to permanently export to **all** users add the `export` statement into */etc/environment* file

Set an environment variable
	`export GERMANY=/home/vit/Projects/GermanProject/sgwGerman/`
#### export vs definition of a variable
The difference between exporting a variable and simply defining it lies in the scope and availability of the variable to other processes.
1. Defining a Variable: When you define a variable in Bash without exporting it, the variable remains within the scope of the current shell session. It is accessible only within the current shell and any child processes created within that session. Other processes or subsequent shell sessions won't have access to this variable.
2. Exporting a Variable: Exporting a variable makes it available to other processes as an environment variable. When you export a variable in Bash using the `export` statement, its value becomes accessible to any child processes spawned from the current shell session, as well as any subsequent shell sessions. These child processes and subsequent shell sessions can read the value of the exported variable and use it as needed.