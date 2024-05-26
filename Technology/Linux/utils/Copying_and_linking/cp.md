#copy 

copy several files:
```shell
cp /home/usr/dir/{file1,file2,file3,file4} /home/usr/destination/
```
If the all the files have the same prefix but different endings:
```shell
cp /home/usr/dir/file{1..4} ./
```
copy all .c and .h files from a directory:   `cp *.[c,h] <destination/folder>`