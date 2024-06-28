#ssh #mount #file-system 
Filesystem client based on ssh

Using this utility you can mount a remote machine via ssh.

Install *sshfs* on the client side then mount the server system:
```sh
sudo apt install sshfs
sshfs -o follow_symlinks <user>@<server_address>: ~/empty_mount_dir
```
This will mount `<user>`'s home directory to local `~/empty_mount_dir`.
>[!Note] Troubleshooting
> Drop `-o follow_symlinks` if it causes problems.

