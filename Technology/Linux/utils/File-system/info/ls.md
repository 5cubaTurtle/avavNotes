#linux 
list directory contents

ignore a pattern:   `ls -Ipattern`
list only dirs: `ls /path/to/dir -d */`
list only [[ln|links]]: `ls -l | grep "^l"` or `ls -l |grep "\->"`
- `-r` revers the list