#linux 
manipulate disk partition table

`sudo fdisk /dev/mmcblk0`, this will enter interactive mode.
- use `m`  for help

create a partition table:
	1. press `o` to create an empty partition table
	2. Press `n` to create a new partition. Then `p` to set it as primary partition. Then enter the size of the partition that you want to create. Enter the full size of the drive if you are just creating a single partition.
	3. press `w` to write the table and exit. This may take a moment.


list partition tables: `sudo fdisk -l`