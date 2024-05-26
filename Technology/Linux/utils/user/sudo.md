#shell 

[debian.org](https://wiki.debian.org/sudo)
open a new shell with sudo privileges: `sudo -i`

[StkOvrfl](https://stackoverflow.com/a/43623102):
`-H`
The `-H` (HOME) option requests that the security policy set the HOME environment variable to the home directory of the target user (root by default) as specified by the password database. Depending on the policy, this may be the default behavior.

To run sudo command with current environment use the `-E` or `--preserve-env` option with `sudo`. Example:`sudo -E python3 your_script.py`

### env
setting an environemtn variable for a sudo execution:
```bash
sudo env "PYTHONPATH=$PYTHONPATH" python3 your_script.py
```
This command sets the `PYTHONPATH` environment variable explicitly for the `sudo` command. It takes the current value of `PYTHONPATH` from the current shell session and passes it to the `sudo` environment.

### troubleshoot
> Sorry, user ava is not allowed to execute '/usr/bin/apt-get update' as root on lt-avnera.

If a user has sudo privilages and this error occurs. Try running `visudo` from a sudoer account or looking at files in the folder */etc/sudoers.d*. For example, this issue was fixed once I edited the file */etc/sudoers.d/00-ava-jumpcloud* from:
```
ava    ALL=(ALL:ALL) !ALL
```
to:
```
ava    ALL=(ALL:ALL) ALL
```
