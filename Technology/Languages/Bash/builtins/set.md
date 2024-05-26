#bash
Set or unset values of shell options and positional parameters
usage:   `set --help` or `help set`
[guide](https://linuxhint.com/set-command-bash/) of some flags:   `Cfxua`.
[docs](https://www.computerhope.com/unix/uset.htm)

At the start of the script file write `set -x` for easier debugging, or in command line:   `bash -x <script_file.sh>`
flags:
- `-v`   Print shell input lines as they are read
- `-x`   Print commands and their arguments as they are executed
- `-e`  Exit immediately if a command exits with a non-zero status.
- `-f`  Disable file name generation (globbing).
- `-a`  After setting this, any new variable will be exported to env.
- `-u`  Unset variables will produce error

Using `+` rather than `-` causes these flags to be turned off.  The
	flags can also be used upon invocation of the shell.  The current
	set of flags may be found in `$-`.
