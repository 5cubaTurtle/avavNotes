Merge lines from multiple files side by side (horizontally) into a single output. It takes the corresponding lines from each input file and combines them using a specified delimiter. Here's the basic syntax:
```sh
paste [options] file1 file2 ...
```

By default, `paste` uses a tab character as the delimiter between columns. Here's an example to illustrate its usage:
```sh
$ cat file1.txt
apple
banana
orange

$ cat file2.txt
red
yellow
orange

$ paste file1.txt file2.txt
apple   red
banana  yellow
orange  orange
```
The `paste` command offers various options for customizing the output, such as specifying a different delimiter, controlling the behavior for handling lines of unequal lengths, and more.

merge 2 files: `paste -d <delimeter> file1.txt file2.txt`
- `-d <delimiter>` will set a delimiter other than the default (tab).
