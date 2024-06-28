A subshell happens when a shell fork()s a child process, and that child process **does not** exec anything.

The following commands create subshells:
```sh
(cmd)
cmd1 | cmd2
$(cmd) or `cmd`
cmd &
<(cmd) or >(cmd)
```

[guide](https://mywiki.wooledge.org/SubShell)
