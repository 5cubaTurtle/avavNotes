#bash #linux 

[linuxize guide](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/)

```txt
KEY=value
KEY="Some other value"
KEY=value1:value2
```

-   The names of the variables are case-sensitive. By convention, environment variables should have UPPER CASE names.
-   When assigning multiple values to the variable they must be separated by the colon `:` character.
-   There is no space around the equals `=` symbol.

Variables can be classified into two main categories, environment variables, and shell variables:
- **Environment variables** are variables that are available system-wide and are inherited by all spawned child processes and shells.
- **Shell variables** are variables that apply only to the current shell instance. Each shell such as `zsh` and `bash`, has its own set of internal shell variables.

There are several commands available that allow you to list and set environment variables in Linux:

-   `env` – The command allows you to run another program in a custom environment without modifying the current one. When used without an argument it will print a list of the current environment variables.
-   `printenv` – The command prints all or the specified environment variables.
-   `set` – The command sets or unsets *shell* variables. When used without an argument it will print a list of all variables including environment and shell variables, and shell functions.
-   `unset` – The command deletes shell and environment variables.
-   `export` – The command sets *environment* variables.

#### [[prompting]] variables
*PS3* - used for the [[select]] construct
*PS1* - is the prompt. Edit the prompt by editing this variable.
