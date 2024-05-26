#linux 
an archiving utility

to extract a .tar.gz:  
```shell
sudo tar -xzf eclipse-cpp-2020-12-R-linux-gtk-x86_64.tar.gz -C /opt
```
  - `-x` extract
  - `-v` verbose
  - `-f file.tar.gz`  sets the name of the file to operate upon
  - `-z` Filter the archive through **gzip(1)**
  - `-j` Filter the archive through **bzip2(1)**
  - `--exclude` Exclude files matching PATTERN/DIR/FILENAME
  - `C`, `--directory`=DIR
    - Change to DIR before performing any operations.  This option is order-sensitive, i.e. it affects all options that follow.  

compress a file or a folder:
`tar -czvf /path/dest_filename.tar.gz src/folder_or_file_name src/another_file`  
  - `-c` create archive, or use `--create`
list files in archive:   `tar --list -f tar_file.tar`  
  - `-t` could be used instead of `--list`
tar and compress multiple directories file by running:  `tar -czvf file.tar.gz dir1 dir2 dir3`

extract specific folders to a destination folder:
  `mkdir /backup/tar_extracts`
  `tar -xvf etc.tar etc/issue etc/fuse.conf etc/mysql/ -C /backup/tar_extracts/`


#### Add a file to an .tar.gz archive
You cannot directly append or update files within an existing *.tar.gz* archive. There are two common alternatives: 
- Approach 1: Extract, Add, and Recompress
- Approach 2: Use `gzip` and `tar` Separately
1. **Decompress the Archive:**
   ```bash
   gzip -d your-archive.tar.gz
   ```
   This will leave you with an uncompressed `your-archive.tar` file.

2. **Add the New File:**
   ```bash
   tar --append --file=your-archive.tar file-to-add
   ```

3. **Recompress the Archive:**
   ```bash
   gzip your-archive.tar
   ```

Choose the approach that fits your needs best. Approach 1 is more straightforward, while Approach 2 can be useful in certain scripting scenarios.