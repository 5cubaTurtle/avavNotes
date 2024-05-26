#linux 
To free up valuable [[RAM]], the OS may decide to swap-out pages of a process to storage. Usually to [[SSD]] (or [[hard-drive]] in older systems). When pages are saved to swapped memory they are marked as such in the [[virtual-memory-table]]. An attempt by the process to access the swapped page will trigger an exception at which point the OS will copy the swapped [[page]] back to [[RAM]].

setup swap file [guide](https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-20-04/)
```shell
sudo fallocate -l 2G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
Setting up swapspace version 1, size = 2 GiB (2147479552 bytes)
no label, UUID=877ccdc5-4d0a-49f3-89f4-7404659dc5e6
sudo swapon /swapfile
sudo nano /etc/fstab
sudo swapon --show
NAME      TYPE SIZE USED PRIO
/swapfile file   2G   0B   -2
sudo free -h
	   total       used        free     shared    buff/cache   available
Mem:   868Mi       302Mi       137Mi    10Mi       428Mi       468Mi
Swap:  2.0Gi          0B       2.0Gi
```

### Removing a Swap File

To deactivate and delete the swap file, follow these steps:
1.  First, deactivate the swap space:
```shell
sudo swapoff -v /swapfile
```
1.  Next, remove the swap file entry `/swapfile swap swap defaults 0 0` from the `/etc/fstab` file.
2.  Finally, remove the actual swapfile file using the [`rm`](https://linuxize.com/post/rm-command-in-linux/) command:
```shell
sudo rm /swapfile
```