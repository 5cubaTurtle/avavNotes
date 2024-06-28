Location: *~/.ssh/config*  

This file is the configuration file for the SSH client, which is used by users to connect to SSH servers. It allows users to specify various options for their SSH connections, such as which private key to use for a specific host, port numbers, and custom hostnames. Here are some common settings you might find or set in this file:
This a user-specific file.

- **Host**: Defines a section for a specific host or pattern of hosts. This can be used to set options that apply only to those hosts. Understands wildcards (`*`).
```
Host example.com
	HostName example.com
	User username
	Port 22
	IdentityFile ~/.ssh/id_rsa
```

- **HostName**: Specifies the real hostname to log into. This is useful for defining aliases.
 ```
Host myserver
    HostName 192.168.1.100
 ```
 
- **User**: Specifies the username to use when connecting to the host.
	`User username`
    
- **Port**: Specifies the port number to use for the connection.
	`Port 2222`
    
- **IdentityFile**: Specifies which private key file to use for authentication.
	`IdentityFile ~/.ssh/id_rsa`

Wildcard usage:
```
Host *.example.com
    User username
    IdentityFile ~/.ssh/id_rsa
```

### Example
In a config file in  we can set up connection to ssh servers without typing in the password. This what config looks like:
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