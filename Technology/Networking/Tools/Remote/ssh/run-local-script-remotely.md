#ssh
[guide](https://www.cyberciti.biz/faq/linux-unix-osx-bsd-ssh-run-command-on-remote-machine-server/)
Create a shell script as follows:
```shell
#!/bin/bash
# Name: test.sh 
# Purpose: Run multiple commands on a remote box 

uptime
date
whoami
```
Now run it as follows on host named server1.cyberciti.biz:  
`ssh vivek@server1.cyberciti.biz 'bash -s' < /path/to/test.sh`

could also use:
### TO-DO
add here the `<<< EOF` syntax explanation
