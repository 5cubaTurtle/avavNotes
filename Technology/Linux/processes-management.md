#linux 

### Killing
killing all running processes of a specific <**user**> with some <**pattern**>:  
```shell
kill -9 $(ps -fu <user> | grep '<pattern>' | awk '{print $2}')
```
- _**kill -9** should only ever be used as a last resort as it will create ‘orphaned shared memory segments’ and is therefore best avoided if possible_
### Display
pstree - display a tree of processes
    `pstree`

`pgrep <pattern>`   shows pids of processes whose name match the <pattern\>
`pkill <pattern>`   sends **SIGTERM** to processes whose name match the <pattern\>
