#linux #stream 
stream editor for filtering and transforming text

syntax: `sed SCRIPT INPUTFILE`

## Usage
#### Basic
replace all occurrences of 'hello' to 'world' in the file 'input.txt':
```sh
sed 's/hello/world/' input.txt > output.txt
```

If you do not specify `INPUTFILE`, or if `INPUTFILE` is `-`, *sed*
filters the contents of the standard input.  The following commands are
equivalent:
```sh
     sed 's/hello/world/' input.txt > output.txt
     sed 's/hello/world/' < input.txt > output.txt
     cat input.txt | sed 's/hello/world/' - > output.txt
```

Default *sed* behavior to write to [[stdout]].
`-i` to edit files in-place instead of printing to standard output.  See also the 'W' and
's///w' commands for writing output to other files.
#### display file content
print a line 162 from a file:
```shell
sed -n 162p <filename>
```

print line range from a file:
```shell
sed -n '16224,16482p;16483q' filename
```
- the `16483q` is optional so the execution will stop on this line instead of running to the end of the file

#### replace pattern
Replace \<patternA\> with \<patternB\> in all files in current folder:  
```sh
sed -i 's/SEARCH_REGEX/REPLACEMENT/g' INPUTFILE
```
- `-i[SUFFIX], --in-place[=SUFFIX]`   edit files in place (makes backup if SUFFIX supplied (ex -i.bak))
- `g` - Global replacement flag. By default, `sed` reads the file line by line and changes only the first occurrence of the `SEARCH_REGEX` on a line. When the replacement flag is provided, all occurrences are replaced.
- `INPUTFILE` could be a list of files separated by spaces.

replace patternA with patternB in all .html files in current dir:
`sed 's/patternA/patternB/g' *.html`

Remove everything on the line which starts with the pattern `^.*\ to\ Root_RobotOK_FullyAutonomous` and 
```sh
sed -n 's/^.*\ to\ Root_RobotOK_FullyAutonomous//p' cleaning_algorithm-1.log
```

On all lines remove everything up-to the pattern `5 07:`:
```sh
sed 's/^.*5\ 07://g' cleaning_algorithm-1.log > woDate.log
```

Insert into line 79 of the file */dest/to/file* the text "big brown bear":
`sed -i "79i big brown bear" /dest/to/file`

Insert `#` to the beginning of the 10th line: `sed -i '10s/^/# /' example.txt`

Remove the pattern `</h3>` from the *end* of each line and save to new file: ```
```sh
sed 's/<\/h3>$//' headers_.txt > new_headers.txt
```
- `$` refers to the end of the line.

Extract lines after a pattern:   `sed -n -e 's/^.*pattern //p'`
-   `-n` means not to print anything by default.
-   `-e <sed-script>`, `-e` is followed by a sed command/script.
-   `s` is the pattern replacement command.
-   The regular expression `^.*pattern` matches the pattern you're looking for, plus any preceding text (`.*` meaning any text, with an initial `^` to say that the match begins at the beginning of the line). Note that if `pattern` occurs several times on the line, this will match the last occurrence.
-   The match, i.e. everything on the line up to `pattern` , is replaced by the empty string (i.e. deleted).
-   The final `p` means to print the transformed line.

#### delete line/s from file
- delete 4th line from *testfile.txt*: `sed '4d' testfile.txt`
- `$` is the *last* line as used by [[Search_and_replace|vim]] syntax. Delete the last line: `sed '$d' testfile.txt`
 - delete a *range* of lines (*3-5*): `sed '3,5d' testfile.txt`
 - delete all lines *except* the given range(*3-5*): `sed '3,5!d' testfile.txt`
 - delete *blank* lines (lines with 0 characters): `sed '/^$/d' testfile.txt`
 - delete lines with *only spaces*: `sed '/^[[:space:]]*$/d' testfile.txt`
 - delete a line that *starts* with a certain word: `sed '/^First/d' testfile.txt`
 - delete a line that *ends* with a certain word: `sed '/LINE$/d' testfile.txt`