#ssh 
[Using an already established SSH channel](https://unix.stackexchange.com/a/33581)
[Reusing ssh session for repeated rsync commands](https://unix.stackexchange.com/a/50515)

see the `ControlMaster` and `ControlPath` options in [man](https://www.freebsd.org/cgi/man.cgi?query=ssh_config&sektion=5).
Start the master connection:
```shell
mkdir ~/.ssh/ctl
ssh -nNf -o ControlMaster=yes -o ControlPath="$HOME/.ssh/ctl/%L-%r@%h:%p" user@host
```
And then use rsync with:
```shell
rsync -e "ssh -o 'ControlPath=$HOME/.ssh/ctl/%L-%r@%h:%p'" ...
```
Then, to terminate the master connection:
```shell
ssh -O exit -o ControlPath="$HOME/.ssh/ctl/%L-%r@%h:%p" user@host
```
- `-o ControlPersist=320`   persists the master-connection for 320 seconds and then closes it