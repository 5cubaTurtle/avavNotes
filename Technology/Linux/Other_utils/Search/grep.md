#search #linux 

`grep`, `egrep`, `fgrep`, `rgrep` - print lines that match patterns

Syntax: `grep <pattern> <file>`

Search all files for "patternA" or "patternB": `egrep 'patterA|patterB' *`
Search in a directory recursively: `grep -r <pattern> <directory>`

**Options**:
- `-n`   line number
- `-i`   ignore case
- `-r`   search recursively in subdirectories
- `-w`   match the whole word
- `-l`   gives the name of the file instead of the line
- `-e`   search a pattern
- `--color`   mark with red the found pattern
- `-v`   to reverse match (i.e. show unmatched lines)
- `-A NUM` Print  *NUM*  lines  of  trailing  context  after  matching  lines
- `-o`   print only the matched pattern
- `-c`   print only the total count of matched lines
- `-E`   Interpret PATTERNS as extended regular expressions. Same as `egrep`
- `-m5`  stop reading after 5 matching lines
- `-q`,`--quiet` do not write anything to standard output.  Exit immediately with zero status if any match is found, even if an error was detected.

Find lines with both patterns *patternA* followed by *patternB*:
	`grep "patternA.*patternB" file_name.txt`
Find multiple patterns:
	`grep 'patternA\|patternB'`
Find A but exclude B and C:
	`grep -wrne 'A' | grep -ve 'B' -e C`
Find a word which is followed by `\b` ("word boundary" i.e. a space or a coma):
	`grep inet\b`, will match lines with *inet* but not, say, *inet6*.
Print pattern that matches ip-address:
	`grep -oE '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b`
	The regular expression '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b' matches any string that looks like an IP address, i.e., four numbers separated by dots, with each number between 0 and 255.
Look inside archives:
	`zgrep` or `zegrep`
Look through only .h and .cpp files:  
	`grep -inr --include=\*.h --include=\*.cpp search_pattern` 
Show all lines and color the pattern:
```sh
grep --color 'pattern\|$' file
grep --color -E 'pattern|$' file
grep --color -E 'pattern|' file
```
Print 10 lines after the line with matched patter using the `-A` flag:
```sh
python3 -c 'import cv2; print(cv2.getBuildInformation())' | grep Video -A10
```

Check if string contains a substring: 
```sh
STR='GNU/Linux is an operating system'
SUB='Linux'

if grep -q "$SUB" <<< "$STR"; then
  echo "It's there"
fi
```

### Characters need escaping:
`-`,
For example to search for a pattern "- network" do: 
```sh
grep "\- network"
# or
grep -e "- network"
```
