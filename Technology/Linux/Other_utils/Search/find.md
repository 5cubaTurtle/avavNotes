#linux #search

search for files in a directory hierarchy

Find all files excluding starting pattern "hbuild*" in name and path "*/bkup/*":
```shell
find -type f -not -name "hbuild*" -not -path "*/bkup/*"
```
 - `-not` flag could be replaced by `!`
 - `-name`  name of file
 - `-path`  path of file
 - `-type`  type of file

Find files newer than 2021-06-12:
```shell
find . -maxdepth 1 -newermt "2021-06-12" -ls
```
Delete files recursively (run w/o -delete at 1st):
```shell
find . -name "*.bak" -type f -delete
```
Touch .txt files recursively:
```shell
find . -type f -name "*.txt" -exec touch {} +
```
Print the total size in bytes of all files older than 8 days found in local dir and its subdirs:
```shell
find . -mtime +8 -ls|awk '{s += $7} END {print s}'
```
Zip files older than 20 days:
```shell
find /tmp/log/ -mtime +20 | xargs tar -czvPf /tmp/older_log_$(date +%F).tar.gz
```

listing largest 15 files in current path (with timestamp):
```shell
find . -type f | xargs ls -ls | sort -rn | awk '{size=$1/1024;name=$10;;Mon=$7;Year=$9; printf(" %sMb %s %s %s \n",size,Mon,Year,name);}' | head -15
```

files slightly less than 10Mb:  `find . -size 10M`
files larger than 10Mb:  `find . -size +10M`

create alias locate
To quickly find files: `locate <filename>`  

return error if find did not find anything (for scripting):   `find -name somefile |grep .`
