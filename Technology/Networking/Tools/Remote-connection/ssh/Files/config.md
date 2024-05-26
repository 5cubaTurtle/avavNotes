#ssh #network 

location: *~/.ssh/config*

To connect to a remote with a default user like this: `ssh remote_host`, the default user to needs to be defined in the [[Technology/Networking/Tools/Remote-connection/ssh/Files/config|config file]]: `$HOME/.ssh/config`. 

example file:
```ssh-file
Host rubin pleco2e2 PLC2-0-003 jordan static PLC2-0-static liat PLC2-0-004 PLC2-0-005 PLC2-0-006 PLC2-0-007 PLC2-0-008 PLC2-0-009 PLC-101 PLC-102 PLC-103 PLC-104 PLC-105 PLC-106 PLC-107 PLC-108 PLC2-0-RPI64
  IdentityFile ~/.ssh/br-dev-key
  User robot

Host blade
  IdentityFile ~/.ssh/br_servers.pub
  User blade-admin

Host bladecloud
  IdentityFile ~/.ssh/br_servers.pub
  User reprepro

```
