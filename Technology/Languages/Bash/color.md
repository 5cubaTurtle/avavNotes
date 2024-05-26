#print
[guide](https://linuxhandbook.com/change-echo-output-color/) to [[echo]] in color
[ANSI color code generator](https://ansi.gabebanks.net/index.html)

#### codes
use these special escaped characters to colorize your terminal output:

|color|code|
|---|---|
|Default|00 or nothing
|Black  |30
|Red    |31
|Green  |32
|Yellow |33
|Blue   |34
|Purple |35
|Cyan   |36
|White  |37
|Bold|1
|Italic|3
|Underline|4
|Strikethrough|9

These are for foreground coloring, the same colors could be set for background instead using numbers 40-47.
To produce a lighter tint use the number + 60; for example for lighter red use 91.
You can use these escape codes with `'\033['` or `\e[`, followed by the ANSI escape code of the color of your choice followed by `'m'`. If coloring the [[prompting|prompt]], also finish with `\]`.

usage example:
```shell
#!/bin/bash

RED='\033[0;31m'
NOCOLOR='\033[0m'
echo -e "I ${RED}love${NOCOLOR} Linux"
```
when using with [[echo]] use the `-e` option
