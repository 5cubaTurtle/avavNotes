#shell 
[[echo]](https://linuxize.com/post/echo-command-in-linux-with-examples/)
Builtin in Bash and most of the other popular shells like Zsh and Ksh. Its behavior is slightly different from shell to shell.

There is also a standalone `/usr/bin/echo` utility, but usually, the shell built-in version will take precedence.

```sh
echo [-neE] [ARGUMENTS]
```

- When the `-n` option is used, the trailing newline is suppressed.
- If the `-e` option is given, the following backslash-escaped characters will be interpreted:
    - `\\` - Displays a backslash character.
    - `\a` - Alert (BEL)
    - `\b` - Displays a backspace character.
    - `\c` - Suppress any further output
    - `\e` - Displays an escape character.
    - `\f` - Displays a form feed character.
    - `\n` - Displays a new line.
    - `\r` - Displays a carriage return.
    - `\t` - Displays a horizontal tab.
    - `\v` - Displays a vertical tab.
- The `-E` option disables the interpretation of the escape characters. This is the default.