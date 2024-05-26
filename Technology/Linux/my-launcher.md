*bitwarden*, an example of a launcher script:
```sh
#!/usr/bin/bash
cd $HOME/AppImages/
./Bitwarden-2023.5.1-x86_64.AppImage >> bitwarden.log 2>&1 &
```
This one is located in *~/.local/bin*.

running a process in background: `sleep 10 &`
