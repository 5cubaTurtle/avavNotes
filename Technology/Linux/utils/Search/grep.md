#search #linux 

grep, egrep, fgrep, rgrep - print lines that match patterns

search all files for "patternA" or "patternB":  
`egrep 'patterA|patterB' * -n --color`
search all files in a directory for a search_word:
`grep -r <search_word> <dir_path>`
- `-n`   line number
- `-i` ignore case
- `-r`   search recursively in subdirectories
- `-w`   match the whole word
- `-l`   gives the name of the file instead of the line
- `-e`   is to search a pattern (like egrep)
- `--color`     mark with red the found pattern
- `-v` to reverse match (i.e. show unmatched lines)
- `-A NUM` Print  *NUM*  lines  of  trailing  context  after  matching  lines
- `-o` print only the matched pattern
- `-c` print only the total count of matched lines
- `-E` Interpret PATTERNS as extended regular expressions
- `-m5` stop reading after 5 matching lines

find lines with both patterns *patternA* followed by *patternB*:
	`grep "patternA.*patternB" file_name.txt`
find multiple patterns:
	`grep 'patternA\|patternB'`
find A but exclude B and C:
	`grep -wrne 'A' | grep -ve 'B' -e C`
find a word which is followed by `\b` ("word boundary" i.e. a space or a coma):
	`grep inet\b`, will match lines with *inet* but not, say, *inet6*.
print pattern that matches ip-address:
	`grep -oE '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b`
	The regular expression '\b([0-9]{1,3}\.){3}[0-9]{1,3}\b' matches any string that looks like an IP address, i.e., four numbers separated by dots, with each number between 0 and 255.
look inside archives:
	`zgrep` or `zegrep`
look through only .h and .cpp files:  
	`grep -inr --include=\*.h --include=\*.cpp search_pattern` 
show all lines and color the pattern:
```sh
grep --color 'pattern\|$' file
grep --color -E 'pattern|$' file
grep --color -E 'pattern|' file
```
print 10 lines after the line with matched patter using the `-A` flag:
```sh
python3 -c 'import cv2; print(cv2.getBuildInformation())' | grep Video -A10
```

check if string contains a substring: 
```sh
STR='GNU/Linux is an operating system'
SUB='Linux'

if grep -q "$SUB" <<< "$STR"; then
  echo "It's there"
fi
```