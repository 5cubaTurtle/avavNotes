#copy
usage [examples](https://opensource.com/article/18/7/how-use-dd-linux)
copies and converts files
`dd if=/dev/sda of=/dev/sdb bs=64k`
- `if` input file
- `of` output file
- `bs` number of bytes to copy in a time

copying through ssh and zipping along the way:
`ssh username@54.98.132.10 "dd if=/dev/sda | gzip -1 -" | dd of=backup.gz`

copy partition `mmcblk0` to file `rubin.img`:
```shell
dd if=/dev/mmcblk0 of=/media/img/rubin.img conv=sync,noerror bs=64k status=progress
```

`conv=CONVS`   convert the file as per the comma separated symbol list
	  - `sync`   pad every input block with NULs to ibs-size; when used with block or unblock, pad with spaces rather than NULs
	  - `noerror`  continue after read errors
