#copy 
OpenSSH secure file transfer

example:
```shell
$ sftp user@192.168.1.10
Connected to 192.168.1.10.
sftp> dir
file1      file2  file3   
sftp> pwd
Remote working directory: /home/user
sftp> get file2
Fetching /home/user/file2 to file2
/home/user/file2                                                   100% 3740KB 747.9KB/s   00:05    
sftp> bye
```
- `-r` get a folder

run sftp command on local machine:   `!<command>`
to run a navigation command locally attach "l"(lowercase L) to it: `lls`, `lpwd` or `lcd`
to pull a file from the remote use get: `get -r <filename>`
- `-r` recursive. Use this flag to pull folders to local
to push a file to a remote use put: `get put <local-filname>`
- `-r` recursive. Use this flag to push folders to remote
- `-i <private_key>` Selects the file from which the identity (private key) for public key authentication is read.