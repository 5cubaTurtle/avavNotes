Location:  */etc/ssh/sshd_config*

This file is the configuration file for the SSH daemon (`sshd`), which is the server-side component of SSH. It defines the behavior of the SSH server, including what authentication methods are allowed, which users can connect, and various security settings. Some common configurations you might find or set in this file include:
This is a system-wide file.

- **Port**: Specifies the port number that the SSH server listens on. The default is 22.
	`Port 22`
- **PermitRootLogin**: Controls whether the root user is allowed to log in via SSH.
	`PermitRootLogin no`
- **PasswordAuthentication**: Determines whether password authentication is allowed.
	`PasswordAuthentication yes`
- **PubkeyAuthentication**: Enables or disables public key authentication.
	 `PubkeyAuthentication yes`
- **AuthorizedKeysFile**: Specifies the file that contains public keys for user authentication.
	`AuthorizedKeysFile .ssh/authorized_keys`
- **AllowUsers**: Specifies which users are allowed to connect.
	`AllowUsers user1 user2`
