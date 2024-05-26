In a config file in *~/.ssh/config* we can set up connection to ssh servers without typing in the password. This what config looks like:
```sh
Host mypi rubin pleco2e2 PLC2-0-003 PLC2-0-static liat PLC2-0-004 PLC2-0-005 PLC2-0-006 PLC2-0-007 PLC2-0-008 PLC-009 PLC-101 PLC-102 PLC-103 PLC-104 PLC-105 PLC-106 PLC-107 PLC-108 PLC-109 PLC-110 PLC-111 PLC-112 PLC-113 PLC-114 PLC-115 PLC-116 PLC-117 PLC-118 PLC-119 PLC-119 
  IdentityFile ~/.ssh/br-dev-key
  User robot

Host blade
  IdentityFile ~/.ssh/br_servers.pub
  User blade-admin

Host bladecloud
  IdentityFile ~/.ssh/br_servers.pub
  User reprepro
```
Each section contains *Host*, *IdentityFile* and *User*.
- *Host* is the server to which we connect. Its IP should be defined in [[/etc/hosts]] file.
- *IdentityFile* is the public key which is used to connect to the host. This is identification instead of  typing the password.
- *User* as whom the connections will be made.

### ssh environment vars
- `SSH_CLIENT` - address of the client which is currently connected.