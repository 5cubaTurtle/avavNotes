#encryption

### PGP (Pretty good privacy):
Command for PGP batch file Encryption:  
command-line: `gpg -e -r $ENCRYPT_KEY  file_name`  
C: 
```C
sprintf(cmd,"gpg -e -r  %s  %s",encrptKey,fileStruct.SprintFileName);
```
•	Command for PGP batch file Decryption  
command-line: `gpg  --batch  --passphrase-fd  0  -o  Output_file -d  input_encrypted_file` (with ext as .PGP)  
C Example:
```C
sprintf(cmd,"echo %s | gpg --batch --passphrase-fd 0 -o %s  -d  %s",fileData.passphrase,input_file_with_path,new_full_fileName);
```

For more Details/Commands, refer below links.
- [GNU manual]( https://www.gnupg.org/gph/en/manual/x110.html)
- [hawaii.edu](http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/)
- [illinois.edu - GPG cheat sheet](https://guides.library.illinois.edu/data_encryption/gpgcheatsheet)
