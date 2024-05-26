#linux 
gawk - pattern scanning and processing language

### Syntax
awk parser ignores more than one whitespace.
- `BEGIN {...}` pre-loop operations
-  `END {...}` after loop operations
- `{...}` the loop
To print a string enclose it in quotation marks `"`: `{print "His name is " name}`

### Examples
print the 2nd word of the input: `awk '{print $2}'`
print the the whole line the input: `awk '{print $0}'`

calculate avarage from lines in file.txt:
1.23
3.45
5.46
6.23

`awk 'BEGIN{s=0;}{s+=$1;}END{print s/NR;}' file.txt`
4.0925

To calculate total size of all *.deb* files:
```sh
du -s /path/to/directory/*.deb | awk '{ sum += $1 } END { print sum }'
```

Start the sum from 100:
```sh
du *.deb|awk 'BEGIN{sum =100; print "started with " sum} {sum += $1}END{print sum}
```
