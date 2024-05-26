#process #memory 
Report memory map of a process

The `pmap` command reports the memory map of a process, which includes the address space and memory usage of the process: `pmap -x <pid>`
- `<pid>` is the process ID of the process you want to inspect.
- `-x` option displays detailed information about the memory usage of the process, including the amount of [[heap]] memory allocated to the process.

The output of the `pmap` command includes a section for the heap memory, which shows the total size of the heap, the amount of memory that is currently in use, and the amount of memory that is currently available. For example:

```
Address           Kbytes     RSS   Dirty Mode   Mapping
[...]
00007f13c1bf4000    1324     1320        0 rw---   [ heap ]
[...]`
```
Here, the heap memory starts at address `00007f13c1bf4000`, has a total size of `1324` KB, and `1320` KB are currently in use, leaving `4` KB available.

Note that the amount of heap memory available to a process can change dynamically as the process allocates and frees memory. Additionally, the available memory reported by `pmap` may not be entirely accurate, because some of the memory may be shared with other processes or the kernel. Therefore, it's important to use the `pmap` command as a tool for gaining insight into a process's memory usage, rather than as a definitive measure of available memory.