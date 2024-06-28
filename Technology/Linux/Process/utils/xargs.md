Build and execute command lines from standard input

This is GNU version of xargs.  xargs reads items from the standard input, delimited by blanks (which can be protected with double or single quotes or a backslash) or newlines, and executes the command (default is [[echo|/bin/echo]]) one or more times with any initial-arguments followed by items read from standard input.  Blank  lines  on the standard input are ignored.
 
The  command line for command is built up until it reaches a system-defined limit (unless the `-n` and `-L` options are used). The specified command will be invoked as many times as necessary to use up the list of input items. In general, there will be many fewer invocations of command than there were items in the input. This will normally have significant performance benefits. Some commands can usefully be executed in parallel too; see the `-P` option.

To process filenames containing spaces, blanks or newlines, see usage of the `-0` option.

If  any  invocation of the command exits with a status of *255*, xargs will stop immediately without reading any further input.  An error message is issued on [[stderr]] when this happens.

#### Syntax
	`xargs [options] [command [initial-arguments]]`
#### Options:
`-0`, `--null`
	Input items are terminated by a null character instead of by whitespace, and the quotes and backslash are not special (every character is taken literally). Disables the end of file string, which is treated like any other argument. Useful when input items might contain white space, quote marks, or backslashes.  The GNU [[find]] `-print0` option produces input suitable for this mode.
`-p`, `--interactive`
	Prompt the user about whether to run each command line and read a line from the terminal.  Only run the command line if the response starts with *y* or *Y*.  Implies `-t`.
`-t`,` --verbose`
	Print the command line on the standard error output before executing it.

#### Usage:
Replace pattern in [[find]] output files using [[sed]]:
```bash
find /home/user/ -type f | xargs sed -i 's/lemon/apple/g'
```