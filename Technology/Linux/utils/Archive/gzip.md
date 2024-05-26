#linux 
gzip, gunzip, zcat - compress or expand files

decompress and remove the .gz file:   `gzip -d file.gz` or `gunzip file.gz`
- `-k`   keep the original file
- `-c` or use `zcat` to extract to [[stdout]]. The original file untouched.

### zip
unzip a file:   `unzip <filename>`  
Combine several zips into one folder: `unzip *.zip -d <combind_dir>`
View zip's contents: `unzip -l <filename.zip>` or `zipinfo <filename.zip>` which is more detailed.
