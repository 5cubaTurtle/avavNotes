#link

create a link:   `ln -s <path to file> name_of_link`
- `-s`  make symbolic links instead of hard links

### From chatGPT (doesn't work)
To see all links to a file in Linux, you can use the `ls` command with the `-i` option to show the inode number of the file. Then, you can use the `find` command to search for all files in the system that have the same inode number. Here is the command:
```sh
ls -i <file_path>
find / -inum <inode_number> 2>/dev/null
```
In this command, the ls -i command shows the inode number of the file specified by <file_path>. Then, the find command searches the entire system for files with the same inode number (<inode_number>). The `2>/dev/null` at the end of the find command redirects any error messages to the null device, so they are not displayed on the screen.

The output of the find command will list all the links to the file, along with their file paths. Note that the search may take some time to complete, especially if the system has a large number of files.
