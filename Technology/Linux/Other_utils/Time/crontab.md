#linux #time 
"Maintain crontab files for individual users"
#### Setting a startup process
Open the default _crontab_ editor.
`crontab -e`

A _crontab_ will be created for the user running the command and will be executed using the privileges of the user. If you need your program to run as the _root_ user, run `crontab -e` as the _root_ user itself.

Add a line starting with `@reboot` and followed by the command.
```shell
# m h  dom mon dow   command
@reboot /sbin/ip addr | grep inet\ | tail -n1 | awk '{ print $2 }' > /etc/issue && echo "" >> /etc/issue
```
- `@reboot` defines the job to be executed during system boot.
_Use full path for your programs when possible and write your commands in a single line._
Save the file to install it to the _crontab_.
The file is saved in _/var/spool/crontab/<username\>_
Check if _crontab_ is properly configured:  `crontab -l`