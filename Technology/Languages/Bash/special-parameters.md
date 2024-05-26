#linux #bash

##### [Conditional Experessions](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Bash-Conditional-Expressions)
##### [Special Parameters](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Special-Parameters)
expanded as follows: `($*)`
- `*`   positional parameters, starting from one. `"$*"` is equivalent to `"$1 $2 …"`
- `@`   positional parameters, starting from one. `"$@"` is equivalent to `"$1" "$2" …`
- `#`   number of positional parameters in decimal
- `?`   exit status of the most recently executed foreground pipeline
- `-`   current option flags as specified upon invocation, by the `set` builtin command, or those set by the shell itself (such as the -i option)
- `$`   process ID of the shell. In a `()` subshell, it expands to the process ID of the invoking shell, not the subshell
- `!`   process ID of the job most recently placed into the background
- `0`   name of the shell or shell script


