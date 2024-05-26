[Reference article](https://itsfoss.com/how-to-hack-ubuntu-password/)
1. Boot into recovery mode
	Enter the [[grub]] menu. Then chose the recovery mode from the advanced options.
![[Advanced_options.png]]
2. Drop to root shell prompt. Press `Enter` for maintenance.
3. You need to have write access to the root partition. By default, it has read-only access. Re[[mount]] the root with write access: `mount -rw -o remount /`
4. Then set a new password for any user using the [[passwd]] command: `passwd <username>`. To see the available users, check the */home* direcotry: `ls /home`.
5.  Then you can exit the root shell: `exit`, and then *resume* - resume normal boot.