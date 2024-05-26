print real and effective user and group IDs

print all groups the current user is part of: `id`

if you don't see video in your group list add it using [[usermod]] command `sudo usermod -a -G video`
for Ubuntu users:(20.04)
`sudo usermod -a -G video $LOGNAME`
Logout and log back in to take affect.