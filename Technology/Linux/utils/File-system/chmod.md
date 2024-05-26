#access 

change file mode bits

|Symbol| Meaning|
|---|-----|
|u |user|
|g |group
|o |other
|a | all
|r |read
|w |write (and delete)
|x |execute (and access directory)
|+| add permission|
|-| take away permission|

changing recursively: use `-R` flag
changing all files to some type but directories to other mode use [[find]]:
Using the numeric method:
```shell
find /var/www/html -type d -exec chmod 755 {} \;
find /var/www/html -type f -exec chmod 644 {} \;
```
Using the symbolic method:
```shell
find /var/www/html -type d -exec chmod u=rwx,go=rx {} \;
find /var/www/html -type f -exec chmod u=rw,go=r {} \;
```
The find command searches for files or directories under /var/www/html and passes each found file or directory to the chmod command to set the permissions.

When using find with -exec, the chmod command is run for each found entry. Use the xargs command to speed up the operation by passing multiple entries at once:
```shell
find /var/www/html -type d -print0 | xargs -0 chmod 755 
find /var/www/html -type f -print0 | xargs -0 chmod 644
```
For `xargs` command the flag `-0` means, input  items  are  terminated by a null character instead of by whitespace. This ensured by `-print0` flag in `find` command.