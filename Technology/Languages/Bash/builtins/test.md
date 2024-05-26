In Bash, the `test` command takes one of the following syntax forms:

```sh
test EXPRESSION
[ EXPRESSION ]
[[ EXPRESSION ]]
```

To make the script portable, prefer using the old test `[` command, which is available on all POSIX shells. The new upgraded version of the `test` command `[[` (double brackets) is supported on most modern systems using Bash, Zsh, and Ksh as a default shell.

To negate the test expression, use the logical `NOT` (`!`) operator. When [comparing strings](https://linuxize.com/post/how-to-compare-strings-in-bash/) , always use single or double quotes to avoid word splitting and globbing issues.

Most commonly used operators:
-   `-n` `VAR` - True if the length of `VAR` is greater than zero.
-   `-z` `VAR` - True if the `VAR` is empty.
-   `STRING1 = STRING2` - True if `STRING1` and `STRING2` are equal.
-   `STRING1 != STRING2` - True if `STRING1` and `STRING2` are not equal.
-   `INTEGER1 -eq INTEGER2` - True if `INTEGER1` and `INTEGER2` are equal.
-   `INTEGER1 -ne INTEGER2` - True if `INTEGER1` and `INTEGER2` are not equal.
-   `INTEGER1 -gt INTEGER2` - True if `INTEGER1` is greater than `INTEGER2`.
-   `INTEGER1 -lt INTEGER2` - True if `INTEGER1` is less than `INTEGER2`.
-   `INTEGER1 -ge INTEGER2` - True if `INTEGER1` is equal or greater than `INTEGER2`.
-   `INTEGER1 -le INTEGER2` - True if `INTEGER1` is equal or less than `INTEGER2`.
-   `-h` `FILE` - True if the `FILE` exists and is a symbolic link.
-   `-r` `FILE` - True if the `FILE` exists and is readable.
-   `-w` `FILE` - True if the `FILE` exists and is writable.
-   `-x` `FILE` - True if the `FILE` exists and is executable.
-   `-d` `FILE` - True if the `FILE` exists and is a directory.
-   `-e` `FILE` - True if the `FILE` exists and is a file, regardless of type (node, directory, socket, etc.).
-   `-f` `FILE` - True [if the `FILE` exists](https://linuxize.com/post/bash-check-if-file-exists/) and is a regular file (not a directory or device).

#### "\[" vs "\[\[":
`[` is the original test command in BASH and is also known as `test` command. It uses positional parameters and evaluates the expression according to the POSIX standard.

`[[` is a newer,  it provides additional features and a more flexible syntax for evaluating conditions. Unlike `[`, `[[` is a shell keyword, rather than a standalone binary.

For example, `[[ $a -lt $b ]]` will return true if the value of `a` is less than the value of `b`. This is not possible with the `[` command, as it does not support the `-lt` operator.

In general, it is recommended to use `[[` over `[` for test conditions, as it provides more functionality and is more readable. However, for compatibility with POSIX shell scripts, it is important to continue to use `[` when necessary.
