#cloud 
[wiki](https://en.wikipedia.org/wiki/JumpCloud)

### Uninstalling the local agent
Run the uninstall script: `sudo /opt/jc_user_ro/bin/uninstall-jumpcloud-remote-assist ` 
Also, search for any installed [[apt]] packages for *jc*. Run: `apt --installed|grep jc` you might find the *jcagent* or something like that. Then remove it: `sudo apt remove jcagent`.
