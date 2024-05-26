#linux 
"mount a file-system"

mount the file system `/dev/sda1` to the folder `/media/img`:
`mount /dev/sda1 /media/img`

[setup NFS on Ubuntu guide](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04)

If the mounting is defined in [[fstab]] file as described in [[creating-NFS-mount]], we could simply mount the folder: `sudo mount /br`

mounting a shared folder to a local folder (`/home/vit/ForTransfer`). Shared folder on IP: *192.168.32.150*
	`sudo mount.cifs //192.168.32.150/data/For_Transfer /home/vit/ForTransfer -o user=Avner`

### command-line options
`-t`: The argument following the `-t` is used to indicate the [[filesystem-type]]. If  no  -t  option is given, or if the auto type is specified, mount will try to guess the desired type.
`-rw`: Mount the [[filesystem]] read/write. The read-write is kernel default.  A synonym is `-o rw`.