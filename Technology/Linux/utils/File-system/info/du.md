#disk

estimate file space usage

file sizes:
	`du -sh -- *`  
disk usage of current dir:   `du . -hd1`
  - `-h` human readable form
  - `-s, --summarize`  display only total for each argument, like `-d0`
  - `dn`, where `n` is the number of depth to descend, i.e. descend to `n` sub-folders depth.

To calculate total size of all files of specific type (*.deb* here) pipe the output to [[awk]]:
```sh
du -s /path/to/directory/*.deb | awk '{ sum += $1 } END { print sum }'
```

A similar but more intuitive tool is [[dust]]:  `dust`
