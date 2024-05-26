#bash 
The `source` command reads and executes commands from the file specified as its argument in the **current** shell environment
[guide](https://linuxize.com/post/bash-source-command/)
`source` and `.` (a period) are the same command.
[source vs executin](https://superuser.com/questions/176783/what-is-the-difference-between-executing-a-bash-script-vs-sourcing-it)

`exec myscript`
This will terminate the current shell and then execute myscript in place of the terminated shell. That means when myscript is done there no shell to return to. `exec` is powerful but rarely needed.