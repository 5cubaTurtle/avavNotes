---
aliases:
  - pkill
  - pidwait
---
`pgrep`, `pkill`, `pidwait` - Look up or signal processes based on name and other attributes.

`pgrep` looks through the currently running processes and lists the process IDs which match the selection criteria to stdout.
`pkill` will send the specified signal (by default [[Signals#SIGTERM - terminate|SIGTERM]]) to each process.
`pidwait` will wait for each process.

`pgrep` is similar to [[pidof]].
### Usage:
Show PID of NetworkManager: `pgrep Network`

### Options:
- `-a`, `--list-full`
	List the full command line as well as the process ID.

### [Print PID of a started process](https://serverfault.com/a/903631)
```sh
sh -c 'echo $$; exec myCommand'
```