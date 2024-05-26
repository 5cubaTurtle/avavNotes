#linux 
remove sections from each line of files

extract from 5th to 15th character from  a line:   `cut -c 5-15`
extract from 5th character to the end of the line:   `cut -c5-`
extract up to the 5th character from the line:   `cut -c-5`
`-f, --fields=LIST`
	select only these fields;  also print any line that contains no delimiter character, unless the `-s` option is specified
`-s, --only-delimited` do not print lines not containing delimiters
`-d, --delimiter=DELIM`  use `DELIM` instead of TAB for field delimiter

get the second field delimited by ' ' (space):
`ifconfig | grep -oE '(inet |addr:)[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+' | cut -d' ' -f2`

