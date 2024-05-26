#linux 
from [wikiHow](https://www.wikihow.com/Format-a-USB-Flash-Drive-in-Ubuntu)
1. [[lsblk]] to list block devices:
```shell
mmcblk0     179:8    0  14.9G  0 disk 
├─mmcblk0p1 179:9    0   256M  0 part /media/ava/system-boot
└─mmcblk0p2 179:10   0  14.6G  0 part 
```
2. Identify your USB drive. Use the SIZE column to find your USB drive in the list.
3. [[umount|unmount]] the drive  `sudo umount /media/ava/system-boot` 
4. **Erase all of the data on the drive (optional).** You can delete everything on the drive by using the [[dd]] command.
	-   `sudo dd if=/dev/zero of=/dev/mmcblk0 bs=4k && sync`
	-   This will take a while to process and may appear frozen.
	-   On Ubuntu 16.04 and later: `sudo dd if=/dev/zero of=/dev/mmcblk0 bs=4k status=progress && sync`
5. use [[fdisk]] to create a partition table:`sudo fdisk /dev/mmcblk0`, this will enter interactive mode.
	1. press `o` to create an empty partition table
	2. Press `n` to create a new partition. Then `p` to set it as primary partition. Then enter the size of the partition that you want to create. Enter the full size of the drive if you are just creating a single partition.
	3. press `w` to write the table and exit. This may take a moment.
6. run [[lsblk]] again to view the new partition.
7. run [[mkfs]] command to format to ext4 format `sudo mkfs.ext4 /dev/mmcblk0p1`
8. Eject your drive when finished. Once the format is complete, you can safely eject your device: `sudo eject /dev/sdb`

[reference](https://askubuntu.com/questions/22381/how-to-format-a-usb-flash-drive)