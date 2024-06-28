#linux 
Modify a user account

Set a user as a sudoer: `sudo usermod -aG sudo reprepro`. This will add *reprepro* to the group *sudo*.

To see all groups you are part of use the [[id]] command.
add current user to *video* group: `sudo usermod -a -G video`
- for Ubuntu users (20.04):`sudo usermod -a -G video $LOGNAME`

Logout and log back in to take affect.